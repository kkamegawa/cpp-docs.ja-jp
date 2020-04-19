---
title: AFX_EXT_CLASS を使ったエクスポート/インポート
ms.date: 11/04/2016
f1_keywords:
- afx_ext_class
helpviewer_keywords:
- AFX_EXT_CLASS macro
- exporting classes [C++]
- importing DLLs [C++]
- extension DLLs [C++], exporting classes
- executable files [C++], importing classes
- exporting DLLs [C++], AFX_EXT_CLASS macro
ms.assetid: 6b72cb2b-e92e-4ecd-bcab-c335e1d1cfde
ms.openlocfilehash: bcfdc94e8db80daec227d77c20ecec6b14d5af11
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195330"
---
# <a name="exporting-and-importing-using-afxextclass"></a>AFX_EXT_CLASS を使ったエクスポート/インポート

[MFC 拡張 Dll](extension-dlls-overview.md)マクロを使用して**AFX_EXT_CLASS**クラスをエクスポートするには、MFC 拡張 DLL にリンクする実行可能ファイルは、クラスをインポートするマクロを使用します。 **AFX_EXT_CLASS**マクロ、同じヘッダー ファイル、DLL、DLL にリンクする実行可能ファイルで使用できる MFC の拡張機能を構築するために使用します。

DLL のヘッダー ファイルで追加、 **AFX_EXT_CLASS**キーワードを次のように、クラスの宣言に。

```cpp
class AFX_EXT_CLASS CMyClass : public CDocument
{
// <body of class>
};
```

としての MFC でこのマクロが定義されている`__declspec(dllexport)`とプリプロセッサ シンボル`_AFXDLL`と`_AFXEXT`定義されます。 としてマクロが定義されているが、`__declspec(dllimport)`とき`_AFXDLL`が定義されていると`_AFXEXT`が定義されていません。 プリプロセッサ シンボルの定義と`_AFXDLL`MFC の共有バージョンがターゲット実行可能ファイル (DLL またはアプリケーション) によって使用されていることを示します。 ときに両方`_AFXDLL`と`_AFXEXT`は実行可能ファイルのターゲットが MFC 拡張 DLL であるは定義されている場合、これを示します。

`AFX_EXT_CLASS`として定義されます`__declspec(dllexport)`MFC 拡張 DLL からエクスポートするときは、.def ファイル内のすべてにそのクラスのシンボルの装飾名をかけることがなくクラス全体をエクスポートすることができます。

.Def ファイルとすべてのクラスの修飾名をこのメソッドを使用して作成を避けることができます、.def ファイルの作成がより効率的ですので名前を序数でエクスポートできます。 エクスポートの .def ファイル メソッドを使用するには、ヘッダー ファイルの末尾、先頭にある次のコードを配置します。

```cpp
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

> [!CAUTION]
>  バージョン間の競合の可能性があるために、インライン関数をエクスポートするときに注意が必要ですが。 インライン関数は、アプリケーション コードに展開されます。そのため、後で、関数を書き直して場合に、も更新されないアプリケーション自体が再コンパイルしない限り、します。 通常、DLL 関数は、それらを使用するアプリケーションをリビルドせずに更新できます。

## <a name="exporting-individual-members-in-a-class"></a>クラスで個々 のメンバーをエクスポートします。

場合によってクラスの個々 のメンバーをエクスポートする可能性があります。 エクスポートする場合など、 `CDialog`-派生クラスでコンス トラクターをエクスポートする必要がありますのみ、`DoModal`を呼び出します。 使用することができます`AFX_EXT_CLASS`で個々 のメンバーをエクスポートする必要があります。

例えば:

```cpp
class CExampleDialog : public CDialog
{
public:
   AFX_EXT_CLASS CExampleDialog();
   AFX_EXT_CLASS int DoModal();
   ...
   // rest of class definition
   ...
};
```

クラスのすべてのメンバーをエクスポートしないため、実行すると、その他の問題に方法が原因 MFC マクロの動作。 MFC のヘルパー マクロのいくつか実際に宣言またはデータ メンバーを定義します。 そのため、これらのデータ メンバーは、また DLL からエクスポートする必要があります。

たとえば、 `DECLARE_DYNAMIC` MFC 拡張 DLL を作成するときに、マクロが次のように定義されます。

```cpp
#define DECLARE_DYNAMIC(class_name) \
protected: \
   static CRuntimeClass* PASCAL _GetBaseClass(); \
public: \
   static AFX_DATA CRuntimeClass class##class_name; \
   virtual CRuntimeClass* GetRuntimeClass() const; \
```

静的で始まる行`AFX_DATA`クラスの内部静的オブジェクトを宣言しています。 でこのクラスを正しくエクスポートして、クライアントの実行可能ファイルの実行時情報にアクセスするには、この静的オブジェクトをエクスポートする必要があります。 静的オブジェクトは、修飾子で宣言されているため`AFX_DATA`、のみを定義する必要があります`AFX_DATA`する`__declspec(dllexport)`、DLL のビルド時として定義し、`__declspec(dllimport)`クライアント実行可能ファイルを作成するときにします。 `AFX_EXT_CLASS`は既に定義されて、この方法でだけを再定義する`AFX_DATA`と同じである`AFX_EXT_CLASS`クラス定義をします。

例えば:

```cpp
#undef  AFX_DATA
#define AFX_DATA AFX_EXT_CLASS

class CExampleView : public CView
{
   DECLARE_DYNAMIC()
   // ... class definition ...
};

#undef  AFX_DATA
#define AFX_DATA
```

MFC は常に使用されるため、`AFX_DATA`このようなシナリオの場合は、この方法は、マクロ、内で定義するデータ項目のシンボルです。 動作など、`DECLARE_MESSAGE_MAP`します。

> [!NOTE]
>  クラスの選択したメンバーではなく、クラス全体をエクスポートする場合は、静的データ メンバーが自動的にエクスポートします。

### <a name="what-do-you-want-to-do"></a>実行する操作

- [.Def ファイルを使った DLL からエクスポートします。](exporting-from-a-dll-using-def-files.md)

- [関数を使った DLL からエクスポートします。](exporting-from-a-dll-using-declspec-dllexport.md)

- [C 言語の実行可能ファイルで使用するための C++ 関数をエクスポートします。](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C または C++ 言語の実行可能ファイルで使用するための C 関数をエクスポートします。](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [エクスポート方式の使用](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport) を使用してアプリケーションにインポートする](importing-into-an-application-using-declspec-dllimport.md)

- [DLL を初期化します。](run-time-library-behavior.md#initializing-a-dll)

### <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [装飾名](reference/decorated-names.md)

- [インライン関数のインポートとエクスポート](importing-and-exporting-inline-functions.md)

- [相互インポート](mutual-imports.md)

## <a name="see-also"></a>関連項目

[DLL からのエクスポート](exporting-from-a-dll.md)
