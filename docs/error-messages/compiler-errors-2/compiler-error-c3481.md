---
title: コンパイラ エラー C3481
ms.date: 11/04/2016
f1_keywords:
- C3481
helpviewer_keywords:
- C3481
ms.assetid: 5d09375a-5ed3-4b61-86ed-45e91fd734c7
ms.openlocfilehash: 1719e9f1d3328be083f745498e6f4ad772b0b52a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755240"
---
# <a name="compiler-error-c3481"></a>コンパイラ エラー C3481

'var': ラムダ キャプチャ変数が見つかりません

コンパイラはラムダ式のキャプチャ リストに渡された変数の定義を見つけられませんでした。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- ラムダ式のキャプチャ リストから変数を削除します。

## <a name="example"></a>使用例

次の例では、変数 `n` が定義されていないため、C3481 が生成されます。

```cpp
// C3481.cpp

int main()
{
   [n] {}(); // C3481
}
```

## <a name="see-also"></a>参照

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
