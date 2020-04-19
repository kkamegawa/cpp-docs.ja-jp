---
title: コンパイラ エラー C3484
ms.date: 11/04/2016
f1_keywords:
- C3484
helpviewer_keywords:
- C3484
ms.assetid: 2fe847fa-f6ee-4978-bc1d-b6dc6ae906ac
ms.openlocfilehash: c9895a3e5a8ae7e941fccde2da85fedfb3d2c6dd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743121"
---
# <a name="compiler-error-c3484"></a>コンパイラ エラー C3484

戻り値の型の前に '->' が必要です

ラムダ式の戻り値の型の前に `->` を指定する必要があります。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- 戻り値の型の前に `->` を指定します。

## <a name="example"></a>使用例

次の例では C3484 が生成されます。

```cpp
// C3484a.cpp

int main()
{
   return []() . int { return 42; }(); // C3484
}
```

## <a name="example"></a>使用例

次の例では、ラムダ式の戻り値の型の前に `->` を指定して C3484 を解決します。

```cpp
// C3484b.cpp

int main()
{
   return []() -> int { return 42; }();
}
```

## <a name="see-also"></a>参照

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
