---
title: コンパイラの警告 (レベル 4) C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 46418063625e16385497740a4f7e3d837e923156
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401554"
---
# <a name="compiler-warning-level-4-c4800"></a>コンパイラの警告 (レベル 4) C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 以降:
> 暗黙的な変換 '*型*' bool にします。 可能な情報の損失
::: moniker-end

Visual Studio 2015 以前のバージョンで、レベル 3 の警告 C4800 に示します。
> '*型*': 値を強制的にブール値は 'true' または 'false' (パフォーマンスの警告)

値が型に暗黙的に変換するときにこの警告は生成`bool`します。 通常、このメッセージは割り当てることで発生`int`変数`bool`変数を`int`変数には値のみが含まれています**true**と**false**、可能性があります型として再宣言`bool`します。 型を使用する式を書き直すことができない場合`bool`、追加することができますし、"`!=0`"式の型を式に示す`bool`します。 式の型にキャスト`bool`デザインでは、警告を無効にしません。

::: moniker range=">= vs-2017"
この警告は、Visual Studio 2017 では発生しません。
::: moniker-end

::: moniker range=">= vs-2019"
この警告は以降では、Visual Studio 2019 既定で無効にします。 使用 __/w__*n*__4800__レベルとして C4800 を有効にする*n*警告、または[/wall](../../build/reference/compiler-option-warning-level.md)すべての警告を有効にします。既定で無効にします。 詳細については、次を参照してください。[コンパイラの警告を、既定でオフ](../../preprocessor/compiler-warnings-that-are-off-by-default.md)します。
::: moniker-end

## <a name="example"></a>例

次の例では、C4800 を生成し、その修正方法を示しています。

```cpp
// C4800.cpp
// compile with: /W4 /w44800
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```