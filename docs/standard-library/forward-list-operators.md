---
title: '&lt;forward_list&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::operator!=
- forward_list/std::operator==
- forward_list/std::operatoroperator&gt;
- forward_list/std::operatoroperator&gt=;
- forward_list/std::operatoroperator&lt;
- forward_list/std::operatoroperator&lt;=
ms.assetid: 57492e09-3836-4dbc-9ae5-78ecf506c190
helpviewer_keywords:
- std::operator!= (forward_list)
- std::operator== (forward_list)
- std::operatoroperator&gt; (forward_list)
- std::operatoroperator&gt=; (forward_list)
- std::operatoroperator&lt; (forward_list)
- std::operatoroperator&lt;= (forward_list)
ms.openlocfilehash: 1ddfb56c7ff68ec10c7bb56af3495e4042acb83c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689684"
---
# <a name="ltforward_listgt-operators"></a>&lt;forward_list&gt; 演算子

## <a name="op_eq_eq"></a>operator = =

演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクトと等しいかどうかを調べます。

```cpp
bool operator==(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`forward_list` 型のオブジェクト。

*右*\
`forward_list` 型のオブジェクト。

### <a name="remarks"></a>Remarks

このテンプレート関数は、`operator==` をオーバーロードして、クラステンプレート `forward_list` の2つのオブジェクトを比較します。 `distance(left.begin(), end()) == distance(right.begin(),right.end()) && equal(left. begin(),left. end(),right.begin())`が返されます。

## <a name="op_neq"></a>operator! =

演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクトと等しくないかどうかを調べます。

```cpp
bool operator!=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`forward_list` 型のオブジェクト。

*右*\
`forward_list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

リストが等しくない場合は **true**、リストが等しい場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は `!(left == right)` を返します。

## <a name="op_lt"></a> 演算子&lt;

演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクトより小さいかどうかを調べます。

```cpp
bool operator<(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`forward_list` 型のオブジェクト。

*右*\
`forward_list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の list が演算子の右辺の list 未満である場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は、`operator<` をオーバーロードして、クラステンプレート `forward_list` の2つのオブジェクトを比較します。 `lexicographical_compare(lhs. begin(), lhs. end(), rhs.begin(), rhs.end())`が返されます。

## <a name="op_lt_eq"></a>演算子 &lt; =

演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクト以下であるかどうかを調べます。

```cpp
bool operator<=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`forward_list` 型のオブジェクト。

*右*\
`forward_list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の list が演算子の右辺の list 以下である場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は `!(right < left)` を返します。

## <a name="op_gt"></a> 演算子&gt;

演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクトより大きいかどうかを調べます。

```cpp
bool operator>(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`forward_list` 型のオブジェクト。

*右*\
`forward_list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の list が演算子の右辺の list より大きい場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は `right < left` を返します。

## <a name="op_gt_eq"></a>演算子 &gt; =

演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクト以上であるかどうかを調べます。

```cpp
bool operator>=(
    const forward_list <Type, Allocator>& left,
    const forward_list <Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*左*\
`forward_list` 型のオブジェクト。

*右*\
`forward_list` 型のオブジェクト。

### <a name="return-value"></a>戻り値

演算子の左辺の前方リストが演算子の右辺の前方リスト以上である場合は**true**を指定します。それ以外の場合は**false**。

### <a name="remarks"></a>Remarks

このテンプレート関数は `!(left < right)` を返します。
