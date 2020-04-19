---
title: コンパイラ エラー C3483
ms.date: 11/04/2016
f1_keywords:
- C3483
helpviewer_keywords:
- C3483
ms.assetid: 18b3a2c5-dfc9-4661-9653-08a5798474cf
ms.openlocfilehash: 0d6c1467575e7fae7d5e4862f36e733a68210f8e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743095"
---
# <a name="compiler-error-c3483"></a>コンパイラ エラー C3483

'var' は既にラムダ キャプチャ リストに含まれています

ラムダ式のキャプチャ リストに同じ変数を複数回渡しました。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- キャプチャ リストから変数のすべての追加インスタンスを削除します。

## <a name="example"></a>使用例

次の例では、変数 `n` がラムダ式のキャプチャ リストに複数回出現するため、C3483 が生成されます。

```cpp
// C3483.cpp

int main()
{
   int m = 6, n = 5;
   [m,n,n] { return n + m; }(); // C3483
}
```

## <a name="see-also"></a>参照

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
