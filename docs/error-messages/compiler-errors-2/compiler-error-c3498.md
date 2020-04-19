---
title: コンパイラ エラー C3498
ms.date: 11/04/2016
f1_keywords:
- C3498
helpviewer_keywords:
- C3498
ms.assetid: 0a5a7817-0872-4119-83bf-980a19113374
ms.openlocfilehash: 771e8c72ab4386bb45a11983318f412e784f5bc9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738103"
---
# <a name="compiler-error-c3498"></a>コンパイラ エラー C3498

' var ': マネージまたは WinRTtype の変数をキャプチャすることはできません

ラムダで、マネージド型または Windows ランタイム型を持つ変数をキャプチャすることはできません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- マネージド変数または Windows ランタイム変数をラムダ式のパラメーター リストに渡します。

## <a name="example"></a>使用例

次の例では、マネージド型を持つ変数がラムダ式のキャプチャ リストに表示されるため、C3498 が生成されます。

```cpp
// C3498a.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [&s](String ^ r)
      { return String::Concat(s, r); } (", World!"); // C3498
}
```

## <a name="example"></a>使用例

次の例では、マネージド型の変数 `s` をラムダ式のパラメーター リストに渡すことにより、C3498 を解決します。

```cpp
// C3498b.cpp
// compile with: /clr
using namespace System;

int main()
{
   String ^ s = "Hello";
   [](String ^ s, String ^ r)
      { return String::Concat(s, r); } (s, ", World!");
}
```

## <a name="see-also"></a>参照

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
