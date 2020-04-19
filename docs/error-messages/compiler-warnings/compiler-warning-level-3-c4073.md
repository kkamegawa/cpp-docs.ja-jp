---
title: コンパイラの警告 (レベル 3) C4073
ms.date: 11/04/2016
f1_keywords:
- C4073
helpviewer_keywords:
- C4073
ms.assetid: 50081a6e-6acd-45ff-8484-9b1ea926cc5c
ms.openlocfilehash: af9f8fc7323fab8c737e7a63cea20809c9182ad9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051915"
---
# <a name="compiler-warning-level-3-c4073"></a>コンパイラの警告 (レベル 3) C4073

初期化子がライブラリ初期化領域に配置される

サードパーティのライブラリの開発者のみが、 [#pragma init_seg](../../preprocessor/init-seg.md)で指定されたライブラリ初期化領域を使用する必要があります。 次の例では、C4073 が生成されます。

```cpp
// C4073.cpp
// compile with: /W3
#pragma init_seg(lib)   // C4073

// try this line to resolve the warning
// #pragma init_seg(user)

int main() {
}
```