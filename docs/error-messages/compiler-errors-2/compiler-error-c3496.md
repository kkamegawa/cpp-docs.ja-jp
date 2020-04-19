---
title: コンパイラ エラー C3496
ms.date: 11/04/2016
f1_keywords:
- C3496
helpviewer_keywords:
- C3496
ms.assetid: e19885f2-677f-4c1e-bc69-e35852262dc3
ms.openlocfilehash: b9542f1904c6797a77c88c88a37aff9348364268
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738181"
---
# <a name="compiler-error-c3496"></a>コンパイラ エラー C3496

'this' は常に値によってキャプチャされます。'&' は無視されました

参照で `this` ポインターをキャプチャすることはできません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- 値で `this` ポインターをキャプチャします。

## <a name="example"></a>使用例

次の例では、 `this` ポインターへの参照がラムダ式のキャプチャ リストにあるため、C3496 が生成されます。

```cpp
// C3496.cpp
// compile with: /c

class C
{
   void f()
   {
      [&this] {}(); // C3496
   }
};
```

## <a name="see-also"></a>参照

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
