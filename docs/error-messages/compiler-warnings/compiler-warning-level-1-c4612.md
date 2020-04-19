---
title: コンパイラの警告 (レベル 1) C4612
ms.date: 08/27/2018
f1_keywords:
- C4612
helpviewer_keywords:
- C4612
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
ms.openlocfilehash: ed5458fc52c1c9c9f12187095e4658204613d1a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406367"
---
# <a name="compiler-warning-level-1-c4612"></a>コンパイラの警告 (レベル 1) C4612

> インクルード ファイル名にエラーがあります

## <a name="remarks"></a>Remarks

この警告は、ファイル名が正しくないか、不足している場合に、 **#pragma include_alias** で発生します。

引数、 **#pragma include_alias**ステートメントは、引用符形式を使用できます ("*filename*") または山かっこ形式 (\<*ファイル名*>)、どちらもする必要がありますが、同じフォームを使用します。

## <a name="example"></a>例

```cpp
// C4612.cpp
// compile with: /W1 /LD
#pragma include_alias("StandardIO", <stdio.h>) // C4612
```