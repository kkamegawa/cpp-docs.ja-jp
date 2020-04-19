---
title: 相互インポート
ms.date: 11/04/2016
helpviewer_keywords:
- mutual DLL imports [C++]
- AFX_DATA
- importing DLLs [C++], mutual imports
- mutually importing executable files [C++]
- AFX_EXT_CLASS macro
- circular imports
- _AFXEXT preprocessor symbol
- DLLs [C++], importing
- executable files [C++], importing
- extension DLLs [C++], mutual imports
- exporting DLLs [C++], mutual imports
ms.assetid: 2cc29537-92ee-4d92-af39-8b8b3afd808f
ms.openlocfilehash: f01e69138a6ca1744645a1c2fa8525b7088e260d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295686"
---
# <a name="mutual-imports"></a>相互インポート

エクスポートまたは別の実行可能ファイルをインポートするインポートが相互 (または循環) 場合に複雑な問題を表示します。 たとえば、2 つの Dll は、その他の相互再帰関数のようなシンボルをインポートします。

相互インポートを実行可能ファイル (通常は Dll) 問題では、その他の最初の構築しなくてもビルドできないことです。 各ビルド プロセスには、その他のビルド プロセスによって生成されるインポート ライブラリが、入力として必要です。

ソリューションでは、実行可能ファイルを構築しなくても、インポート ライブラリを生成する/DEF オプションを使用して、LIB ユーティリティを使用します。 このユーティリティを使用して、必要なすべてのインポート ライブラリをビルドできる Dll の数に関係なく関連または依存関係の複雑さは。

相互インポートを処理するための一般的なソリューションです。

1. さらに各 DLL を実行します。 (任意の順序は、いくつかの注文がより最適な実行不可能な)。すべての必要なインポート ライブラリが存在しは現在、ビルド、実行可能ファイル (DLL) へのリンクを実行します。 場合、 これには、インポート ライブラリが生成されます。 それ以外の場合、インポート ライブラリを生成するために LIB を実行します。

   /DEF オプションを使用しての LIB の実行で追加のファイルが生成されます、します。EXP の拡張機能。 します。EXP ファイルは、実行可能ファイルの構築に後で使用する必要があります。

1. リンクまたは LIB のいずれかを使用して、すべてのインポート ライブラリの構築、後に戻り、ビルド前の手順でビルドされていないすべての実行可能ファイルへのリンクを実行します。 リンク行に対応する .exp ファイルを指定する必要がありますに注意してください。

   DLL1 用インポート ライブラリを作成する前に、LIB ユーティリティを実行した場合 LIB が生成 DLL1.exp ファイルにもします。 DLL1.dlll を構築するときに、リンクへの入力として DLL1.exp を使用する必要があります。

次の図は、相互にインポートする 2 つの Dll や DLL1 DLL2 ソリューションを示します。 手順 1 では、DLL1 で/DEF オプションを設定すると、LIB を実行します。 手順 1 では、DLL1.lib、インポート ライブラリ、および DLL1.exp が生成されます。手順 2 では、インポート ライブラリは DLL2 生成 DLL2 のシンボルのインポート ライブラリをビルドに使用されます。 手順 3 では、入力として DLL1.exp と DLL2.lib を使用して DLL1 を構築します。 LIB DLL2 のインポート ライブラリをビルドに使用しなかったためには、DLL2 の .exp ファイルが必要ないことに注意してください。

![相互インポートを使用して 2 つの Dll をリンクする](media/vc37yj1.gif "相互インポートを使用して 2 つの Dll をリンクするには")<br/>
相互インポートを使った 2 つの DLL のリンク

## <a name="limitations-of-afxext"></a>_AFXEXT の制限事項

使用することができます、 `_AFXEXT` MFC 拡張 Dll が MFC 拡張 Dll の複数の層があるない限りのプリプロセッサ シンボル。 MFC 拡張 Dll を呼び出すか、独自の MFC 拡張 Dll で、MFC クラスから派生し、クラスから派生した場合は、あいまいさを回避するために独自のプリプロセッサ シンボルを使用する必要があります。

問題は、そので Win32、として任意のデータを明示的に宣言する必要があります**方式**、DLL からエクスポートする場合と **_declspec** DLL からインポートする場合。 定義するときに`_AFXEXT`、MFC ヘッダーことを確認します**AFX_EXT_CLASS**が正しく定義されています。

場合などがある複数のレイヤー、1 つの記号**AFX_EXT_CLASS** MFC 拡張 DLL 可能性がある新しいクラスをエクスポートするだけでなく他の MFC 拡張 DLL から他のクラスをインポートするために十分ではありません。 この問題を解決するには、DLL を使うと、DLL 自体を作成することを示す特殊なプリプロセッサ シンボルを使用します。 たとえば、2 つの MFC 拡張 Dll、A.dll と B.dll です。 それらの各ファイルはエクスポート A.h と B.h、一部のクラスです。 B.dll は、A.dll からクラスを使用します。 ヘッダー ファイルは次のようになります。

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A   __declspec(dllexport)
#else
   #define CLASS_DECL_A   __declspec(dllimport)
#endif

class CLASS_DECL_A CExampleA : public CObject
{ ... class definition ... };

// B.H
#ifdef B_IMPL
   #define CLASS_DECL_B   __declspec(dllexport)
#else
   #define CLASS_DECL_B   __declspec(dllimport)
#endif

class CLASS_DECL_B CExampleB : public CExampleA
{ ... class definition ... };
...
```

A.dll をビルドするときに構築されて`/D A_IMPL`B.dll をビルドするときに構築されて、`/D B_IMPL`します。 DLL ごとに個別のシンボルを使用して、`CExampleB`はエクスポートと`CExampleA`B.dll を構築するときにインポートされます。 `CExampleA` A.dll を構築するときにエクスポートし、B.dll (または他のクライアント) で使用するときにインポートします。

組み込みを使用する場合、この種類の階層化を行うことはできません**AFX_EXT_CLASS**と`_AFXEXT`プリプロセッサ シンボル。 上記で説明した手法では、その Active テクノロジ、データベース、およびネットワークの MFC 拡張 Dll を構築する際に MFC 自体のメカニズムを使用するいないとは異なりの方法でこの問題は解決します。

## <a name="not-exporting-the-entire-class"></a>クラス全体をエクスポートしません。

クラス全体をエクスポートしていない場合は、MFC マクロによって作成されたために必要なデータ項目が正常にエクスポートすることを確認する必要があります。 再定義できます`AFX_DATA`特定クラスのマクロにします。 これはクラス全体をエクスポートしない場合はいつ実行する必要があります。

例:

```
/* A.H */
#ifdef A_IMPL
   #define CLASS_DECL_A  _declspec(dllexport)
#else
   #define CLASS_DECL_A  _declspec(dllimport)
#endif

#undef  AFX_DATA
#define AFX_DATA CLASS_DECL_A

class CExampleA : public CObject
{
   DECLARE_DYNAMIC()
   CLASS_DECL_A int SomeFunction();
   //... class definition ...
};

#undef AFX_DATA
#define AFX_DATA
```

### <a name="what-do-you-want-to-do"></a>実行する操作

- [DLL からのエクスポートします。](exporting-from-a-dll.md)

- [使用して、DLL からエクスポートします。DEF ファイル](exporting-from-a-dll-using-def-files.md)

- [関数を使った DLL からエクスポートします。](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS を使ったエクスポート/インポート](exporting-and-importing-using-afx-ext-class.md)

- [C 言語の実行可能ファイルで使用するための C++ 関数をエクスポートします。](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [エクスポート方式の使用](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport) を使用してアプリケーションにインポートする](importing-into-an-application-using-declspec-dllimport.md)

### <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [LIB のユーティリティと/DEF オプション](reference/lib-reference.md)

## <a name="see-also"></a>関連項目

[インポートとエクスポート](importing-and-exporting.md)
