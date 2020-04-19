---
title: コンパイラ エラー C3482
ms.date: 11/04/2016
f1_keywords:
- C3482
helpviewer_keywords:
- C3482
ms.assetid: bf99558e-bef4-421c-bb16-dcd9c54c1011
ms.openlocfilehash: 1d775551d0f4955dc4eda9b0d418ea31e065714f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743134"
---
# <a name="compiler-error-c3482"></a>コンパイラ エラー C3482

'this' は非静的メンバー関数内でのラムダ キャプチャとしてのみ使用できます

静的メソッドまたはグローバル関数で宣言されているラムダ式のキャプチャ リストに `this` を渡すことはできません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- 外側の関数を静的でないメソッドに変換します。または、

- ラムダ式のキャプチャ リストから `this` ポインターを削除します。

## <a name="example"></a>使用例

次の例では、C3482 が生成されます。

```cpp
// C3482.cpp
// compile with: /c

class C
{
public:
   static void staticMethod()
   {
      [this] {}(); // C3482
   }
};
```

## <a name="see-also"></a>参照

[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)
