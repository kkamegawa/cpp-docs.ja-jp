---
title: コンパイラの警告 (レベル 2) C4156
ms.date: 11/04/2016
f1_keywords:
- C4156
helpviewer_keywords:
- C4156
ms.assetid: 9adf3acb-c0fe-42a8-a4db-5822b1493f77
ms.openlocfilehash: 95605aa29e1faba449e19dcf20e6895d31cc5874
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052146"
---
# <a name="compiler-warning-level-2-c4156"></a>コンパイラの警告 (レベル 2) C4156

' delete ' の配列形式を使用せずに配列式を削除しています。配列形式の置換

配列以外の形式の**delete**では、配列を削除できません。 コンパイラが**delete**を配列形式に変換しました。

この警告は、Microsoft 拡張機能 (/Ze) でのみ発生します。

## <a name="example"></a>例

```cpp
// C4156.cpp
// compile with: /W2
int main()
{
   int (*array)[ 10 ] = new int[ 5 ][ 10 ];
   delete array; // C4156, changed by compiler to "delete [] array;"
}
```