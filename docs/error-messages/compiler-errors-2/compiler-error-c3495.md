---
title: コンパイラ エラー C3495
ms.date: 11/04/2016
f1_keywords:
- C3495
helpviewer_keywords:
- C3495
ms.assetid: 1fd40cb8-8373-403d-b8a8-f08424a50807
ms.openlocfilehash: 1a61d4f2472ef6da8aedcf8a8ef90b70de47d8af
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738272"
---
# <a name="compiler-error-c3495"></a>コンパイラ エラー C3495

'var': ラムダ キャプチャには自動ストレージ存続期間が指定されている必要があります

`static` または `extern`とマークされている変数など、自動ストレージ存続期間がない変数をキャプチャすることはできません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- `static` または `extern` 変数をラムダ式のキャプチャ リストに渡さないでください。

## <a name="example"></a>使用例

次の例では、 `static` 変数 `n` がラムダ式のキャプチャ リストにあるため、C3495 が生成されます。

```cpp
// C3495.cpp

int main()
{
   static int n = 66;
   [&n]() { return n; }(); // C3495
}
```

## <a name="see-also"></a>参照

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)

