---
title: DEF ファイルを使った DLL からのエクスポート
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 92a140c6491e9e3f0d356509862dee39ebe3fae6
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220785"
---
# <a name="exporting-from-a-dll-using-def-files"></a>DEF ファイルを使った DLL からのエクスポート

モジュール定義または定義ファイル (*.def) は、DLL のさまざまな属性を記述する 1 つまたは複数のモジュールのステートメントを含むテキスト ファイルです。 使用していない場合、**方式**キーワード DLL の関数をエクスポートする DLL には、DEF ファイルが必要です。

DEF ファイルを最小限に抑えるには、次のモジュール定義ステートメントを含める必要があります。

- ファイルの先頭には、必ず LIBRARY 文を記述します。 このステートメントでは、DLL に属するものとして DEF ファイルを識別します。 LIBRARY 文の引数には、DLL の名前を指定します。 リンカーは、この名前を DLL のインポート ライブラリに配置します。

- EXPORTS 文には、DLL のエクスポート関数の名前と、オプションで序数値を指定します。 序数値を関数に割り当てるには、アット マーク (@) と数字の後に関数名を記述します。 序数値の場合は、1 から N の範囲で指定する必要があります。N は DLL のエクスポート関数の数字です。 関数を序数でエクスポートする場合は、「[関数名ではなく序数による DLL のエクスポート](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)」もいます。

たとえば、バイナリ検索ツリーを実装するコードを含む DLL は、以下のようになります。

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

使用する場合、 [MFC DLL ウィザード](../mfc/reference/mfc-dll-wizard.md)MFC DLL を作成するウィザードはスケルトン DEF ファイルを作成して、自動的にそれをプロジェクトに追加します。 エクスポートされる関数の名前は、このファイルに追加します。 非 MFC Dll の場合は、自分で DEF ファイルを作成し、プロジェクトに追加します。 移動し、**プロジェクト** > **プロパティ** > **リンカー** > **入力** > **モジュール定義ファイル**DEF ファイルの名前を入力します。 構成およびプラットフォームごとにこの手順を繰り返し表示するかを選択して一度にすべて行う**構成のすべての構成を =** と**プラットフォーム = すべてのプラットフォーム**します。

C++ ファイルで関数をエクスポートする場合は、装飾名を DEF ファイルに配置するか、extern"C"を使用して、標準の C リンケージを持つエクスポート関数を定義する必要があります。 使用して取得できます、DEF ファイルに装飾名を格納する必要がある場合、 [DUMPBIN](../build/reference/dumpbin-reference.md)ツールまたはリンカーを使用して[/map](../build/reference/map-generate-mapfile.md)オプション。 コンパイラが作成した装飾名は、コンパイラ独自のものであることに注意してください。 Microsoft によって生成された装飾名を配置するかどうかはC++DEF ファイルに、コンパイラ (MSVC) アプリケーション、DLL にリンクしている必要がありますも構築する呼び出し元のアプリケーション内の装飾名のエクスポート名が一致するように、MSVC の同じバージョンを使用します。DLL の DEF ファイルです。 

> [!NOTE]
> Visual Studio 2015 でビルドされた DLL は、Visual Studio 2017 または Visual Studio 2019 でビルドされたアプリケーションで使用できます。

構築している場合、[拡張 DLL](../build/extension-dlls-overview.md)、エクスポートされたクラスを含むヘッダー ファイルの末尾、先頭にある次のコードを配置、DEF ファイルを使用したエクスポートします。

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

これらの行が、内部的に使用される、クラスに追加される MFC 変数エクスポート (またはインポート)、MFC 拡張 DLL から。 たとえば、`DECLARE_DYNAMIC` を使って派生クラスを作成する場合、このマクロが展開して、`CRuntimeClass` メンバー関数をクラスに追加します。 上の 4 行をコードに追加しないと、DLL の不正なコンパイルまたはリンクが行われたり、クライアント アプリケーションが DLL とリンクするときにエラーが発生することになります。

DLL をビルドする場合、リンカーは、DEF ファイルをエクスポート (.exp) ファイルを作成し、インポート ライブラリ (.lib) ファイルを使用します。 次にリンカーはエクスポート ファイルを使って、.DLL ファイルを作成します。 DLL と暗黙的にリンクする実行形式は、ビルド時にインポート ライブラリと DLL をリンクします。

MFC 自体が DEF ファイルを使用して mfcx0.dll の関数とクラスをエクスポートすることに注意してください。

## <a name="what-do-you-want-to-do"></a>実行する操作

- [関数を使った DLL からエクスポートします。](exporting-from-a-dll-using-declspec-dllexport.md)

- [AFX_EXT_CLASS を使ったエクスポート/インポート](exporting-and-importing-using-afx-ext-class.md)

- [C 言語の実行可能ファイルで使用するための C++ 関数をエクスポートします。](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [C または C++ 言語の実行可能ファイルで使用するための C 関数をエクスポートします。](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [エクスポート方式の使用](determining-which-exporting-method-to-use.md)

- [__declspec(dllimport) を使用してアプリケーションにインポートする](importing-into-an-application-using-declspec-dllimport.md)

- [DLL を初期化します。](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>さらに詳しくは次のトピックをクリックしてください

- [.def ファイル](reference/module-definition-dot-def-files.md)

- [モジュール定義ステートメントに関する規則](reference/rules-for-module-definition-statements.md)

- [装飾名](reference/decorated-names.md)

- [インライン関数のインポートとエクスポート](importing-and-exporting-inline-functions.md)

- [相互インポート](mutual-imports.md)

## <a name="see-also"></a>関連項目

[DLL からのエクスポート](exporting-from-a-dll.md)
