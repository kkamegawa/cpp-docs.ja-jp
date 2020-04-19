---
title: コンパイラの警告 (レベル 4) C4201
ms.date: 11/04/2016
f1_keywords:
- C4201
helpviewer_keywords:
- C4201
ms.assetid: 6156f508-9393-4d77-9e73-1ec3e1c32d0d
ms.openlocfilehash: 4bbbc8987c3ae4157d5f8133978a46a004988bce
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991618"
---
# <a name="compiler-warning-level-4-c4201"></a>コンパイラの警告 (レベル 4) C4201

非標準の拡張機能が使用されています: 無名の構造体/共用体

[Microsoft extensions (/Ze)] では、宣言子が別の構造体または共用体のメンバーとして指定されていない構造体を指定できます。 これらの構造体は、ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) でエラーを生成します。

## <a name="example"></a>使用例

```cpp
// C4201.cpp
// compile with: /W4
struct S
{
   float y;
   struct
   {
      int a, b, c;  // C4201
   };
} *p_s;

int main()
{
}
```
