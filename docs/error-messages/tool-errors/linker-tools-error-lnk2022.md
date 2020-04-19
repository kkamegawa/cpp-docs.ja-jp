---
title: リンカ ツール エラー LNK2022
ms.date: 11/04/2016
f1_keywords:
- LNK2022
helpviewer_keywords:
- LNK2022
ms.assetid: d2128c73-dde3-4b8e-a9b2-0a153acefb3b
ms.openlocfilehash: e55202274c5ec3982f784ad6cdf074a5a99e922f
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345333"
---
# <a name="linker-tools-error-lnk2022"></a>リンカ ツール エラー LNK2022

> メタデータ操作に失敗しました (*HRESULT*): *error_message*

リンカーでは、メタデータのマージ中にエラーが検出されました。 正常にリンクするメタデータのエラーを解決する必要があります。

この問題を診断する方法の 1 つは、実行することです。 **ildasm-トークン**トークンに記載のある種類を検索するオブジェクト ファイル`error_message`、しの相違点を探します。  メタデータ、LayoutType の属性が異なる場合でも同じ名前の 2 つのさまざまな種類が有効でありません。

LNK2022 (構造体) などの型が、同じ名前が競合する定義は、複数のコンパイル単位に存在する場合と指定してコンパイルしたときに理由の 1 つ[/clr](../../build/reference/clr-common-language-runtime-compilation.md)します。  この場合、型が、すべてのコンパイル単位で同一の定義を持つことを確認します。  型名が表示されて`error_message`します。

LNK2022 のもう 1 つの考えられる原因は、リンカーがコンパイラに指定された以外に、別の場所にメタデータ ファイルを検出したとき (で[#using](../../preprocessor/hash-using-directive-cpp.md) )。 コンパイラに渡された時と、リンカーに渡されるときに、同じ場所にメタデータ ファイル (.dll または .netmodule) は、ことを確認します。

マクロの使用、ATL アプリケーションのビルド時に`_ATL_MIXED`で少なくとも 1 つ使用されている場合は、すべてのコンパイル単位が必要です。

## <a name="example"></a>例

次の例では、空の型を定義します。

```cpp
// LNK2022_a.cpp
// compile with: /clr /c
public ref class Test {};
```

## <a name="example"></a>例

このサンプルでは、名前が同じで別の定義の型が含まれる 2 つのソース コード ファイルをリンクすることはできませんを示します。

次の例では、LNK2022 が生成されます。

```cpp
// LNK2022_b.cpp
// compile with: LNK2022_a.cpp /clr /LD
// LNK2022 expected
public ref class Test {
   void func() {}
   int var;
};
```