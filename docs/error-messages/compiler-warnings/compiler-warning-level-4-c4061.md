---
title: コンパイラの警告 (レベル 4) C4061
ms.date: 04/05/2019
f1_keywords:
- C4061
helpviewer_keywords:
- C4061
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
ms.openlocfilehash: 073e3e9cb1cb5bb6b0f66157c986072227960212
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401424"
---
# <a name="compiler-warning-level-4-c4061"></a>コンパイラの警告 (レベル 4) C4061

> 列挙子 '*識別子*'列挙型のスイッチは' in*列挙*' case ラベルによって明示的に処理されません。

指定された列挙子*識別子*で関連付けられたハンドラーを持たず、`switch`がステートメント、`default`ケース。 不足している場合は、不注意にあるか、問題ができない可能性があります。 かどうかに既定のケースで列挙子が処理されるかどうかに依存して可能性があります。 使用されていない列挙子に関連する警告の`switch`されていないステートメント`default`場合は、「」を参照[C4062](compiler-warning-level-4-c4062.md)します。

既定では、この警告はオフに設定されています。 既定で無効になっている警告を有効にする方法の詳細については、次を参照してください。[コンパイラの警告を Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)します。

## <a name="example"></a>例

次の例には、C4061; が生成されます。修正に不足している列挙子の case を追加します。

```cpp
// C4061.cpp
// compile with: /W4
#pragma warning(default : 4061)

enum E { a, b, c };
void func ( E e )
{
   switch(e)
   {
      case a:
      case b:
      default:
         break;
   }   // C4061 c' not handled
}

int main()
{
}
```

## <a name="see-also"></a>関連項目

[コンパイラの警告 (レベル 4) C4062](compiler-warning-level-4-c4062.md)
