---
title: コンパイラ エラー C3087
ms.date: 11/04/2016
f1_keywords:
- C3087
helpviewer_keywords:
- C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
ms.openlocfilehash: 6b9ae71ebfbcfcd5936a2fc3ca666aa51e59bfb5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74751418"
---
# <a name="compiler-error-c3087"></a>コンパイラ エラー C3087

'named_argument': 'attribute' の呼び出しは、既にこのメンバーを初期化しています

名前付き引数が、同じ値の名前なし引数と同じ属性ブロックに指定されました。 名前付引数か名前なし引数の、どちらか 1 つだけを指定します。

## <a name="example"></a>使用例

次の例では C3087 が生成されます。

```cpp
// C3087.cpp
// compile with: /c
[idl_quote("quote1", text="quote2")];   // C3087
[idl_quote(text="quote3")];   // OK
[idl_quote("quote4")];   // OK
```
