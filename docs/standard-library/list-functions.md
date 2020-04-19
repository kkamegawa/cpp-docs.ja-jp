---
title: '&lt;リスト&gt;関数 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- list/std::swap
ms.openlocfilehash: 04f00a9274018432cd03917ae5485f2d395649e4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269024"
---
# <a name="ltlistgt-functions"></a>&lt;リスト&gt;関数

## <a name="swap"></a> スワップ

2 つのリストの要素を交換します。

```cpp
template <class T, class Allocator>
    void swap(list<T, Allocator>& left, list<T, Allocator>& right)
```

### <a name="parameters"></a>パラメーター

*左*\
`list` 型のオブジェクト。

*そうです*\
`list` 型のオブジェクト。

### <a name="remarks"></a>Remarks

このテンプレート関数は、`left.swap(right)` を実行します。
