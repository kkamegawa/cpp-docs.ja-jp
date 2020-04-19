---
title: コンパイラエラー C3154
ms.date: 11/04/2016
f1_keywords:
- C3154
helpviewer_keywords:
- C3154
ms.assetid: 78005c74-eaaf-4ac2-88ae-6c25d01a302a
ms.openlocfilehash: e40b0c2a56c36b92465fb3bb3451a48c88b5822e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745929"
---
# <a name="compiler-error-c3154"></a>コンパイラエラー C3154

省略記号の前に ', ' が必要です。 パラメーター配列関数では、非コンマ区切りの省略記号がサポートされていません。

可変個引数関数が正しく宣言されていませんでした。

詳細については、「[可変個引数リスト (..C++.) (/cli)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3154 が生成されます。

```cpp
// C3154.cpp
// compile with: /clr
ref struct R {
   void Func(int ... array<int> ^);   // C3154
   void Func2(int i, ... array<int> ^){}   // OK
   void Func3(array<int> ^){}   // OK
   void Func4(... array<int> ^){}   // OK
};

int main() {
   R ^ r = gcnew R;
   r->Func4(1,2,3);
}
```
