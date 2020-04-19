---
title: コンパイラ エラー C2348
ms.date: 11/04/2016
f1_keywords:
- C2348
helpviewer_keywords:
- C2348
ms.assetid: 4c4d701f-ccf1-46fe-9ddb-3f341684f269
ms.openlocfilehash: 7bded618c481e59f60c5528510c757dec7226acc
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759998"
---
# <a name="compiler-error-c2348"></a>コンパイラ エラー C2348

' type name ': は C スタイルの集計ではありません。埋め込み IDL 内でエクスポートできません

[Export](../../windows/export.md)属性を使用して .idl ファイルに `struct` を配置するには、`struct` にデータのみを含める必要があります。

次の例では、C2348 が生成されます。

```cpp
// C2348.cpp
// C2348 error expected
[ module(name="SimpleMidlTest") ];

[export]
struct Point {
   // Delete the following two lines to resolve.
   Point() : m_i(0), m_j(0) {}
   Point(int i, int j) : m_i(i), m_j(j) {}

   int m_i;
   int m_j;
};
```
