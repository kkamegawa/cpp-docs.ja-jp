---
title: コンパイラエラー C2467
ms.date: 11/04/2016
f1_keywords:
- C2467
helpviewer_keywords:
- C2467
ms.assetid: f9ead270-5d0b-41cc-bdcd-586a647c67a7
ms.openlocfilehash: da17a3f78c8cab8144cb66b9a672dc59190b50f9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301146"
---
# <a name="compiler-error-c2467"></a>コンパイラエラー C2467

匿名の ' ユーザー定義型 ' の宣言が無効です。

入れ子になったユーザー定義型が宣言されました。 これは、ANSI 互換オプション ([/za](../../build/reference/za-ze-disable-language-extensions.md)) が有効になっている C ソースコードをコンパイルするときにエラーになります。

次の例では、C2467 が生成されます。

```c
//C2467.c
// compile with: /Za
int main() {
   struct X {
      union { int i; };   // C2467, nested declaration
   };
}
```
