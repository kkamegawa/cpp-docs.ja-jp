---
title: コンパイラの警告 (レベル 2) C4396
ms.date: 11/04/2016
f1_keywords:
- C4396
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
ms.openlocfilehash: e874e00d44eef29240cca55541837facfcf64495
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052039"
---
# <a name="compiler-warning-level-2-c4396"></a>コンパイラの警告 (レベル 2) C4396

"name": フレンド宣言が関数の特殊化を参照している場合、テンプレートのインライン指定子を使用できません

関数テンプレートの特殊化では、いずれの [インライン](../../cpp/inline-functions-cpp.md) 指定子も指定できません。 コンパイラは、警告 C4396 を発行し、インライン指定子を無視します。

### <a name="to-correct-this-error"></a>このエラーを解決するには

- フレンド関数の宣言から `inline`、 `__inline`、 `__forceinline` の指定子を削除します。

## <a name="example"></a>例

次のコード例では、 `inline` 指定子のある無効なフレンド関数の宣言を示します。

```cpp
// C4396.cpp
// compile with: /W2 /c

class X;
template<class T> void Func(T t, int i);

class X {
    friend inline void Func<char>(char t, int i);  //C4396
// try the following line instead
//    friend void Func<char>(char t, int i);
    int i;
};
```