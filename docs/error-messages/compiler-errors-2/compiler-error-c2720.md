---
title: コンパイラ エラー C2720
ms.date: 11/04/2016
f1_keywords:
- C2720
helpviewer_keywords:
- C2720
ms.assetid: 9ee3aab7-711b-4f5a-b2f1-cb62b130f1ce
ms.openlocfilehash: c6499fd3f279099ea7c5b31860e70bdaa285e3f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383049"
---
# <a name="compiler-error-c2720"></a>コンパイラ エラー C2720

> '*識別子*':'*指定子*' ストレージ クラス指定子のメンバーが無効です

ストレージ クラスは、宣言の外側のクラス メンバーに対して使用することはできません。 このエラーを修正するには、不要な削除[ストレージ クラス](../../cpp/storage-classes-cpp.md)クラス宣言の外側にあるメンバーの定義からの指定子。

## <a name="example"></a>例

次の例では、C2720 を生成し、その修正方法を示しています。

```cpp
// C2720.cpp
struct S {
   static int i;
};
static S::i;   // C2720 - remove the unneeded 'static' to fix it
```