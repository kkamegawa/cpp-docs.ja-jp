---
title: '&lt;allocators&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- allocators/std::operator!=
- allocators/std::operator==
ms.assetid: b55d67cb-3c69-46bf-ad40-e845fb096c4e
ms.openlocfilehash: b7429e298cdf14d727fc481db6c4a3bf8574b5e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377895"
---
# <a name="ltallocatorsgt-operators"></a>&lt;allocators&gt; 演算子

これらは、グローバル テンプレートの演算子関数で定義されている&lt;アロケーター&gt;します。 クラスのメンバー演算子関数は、クラスのドキュメントを参照してください。

|||
|-|-|
|[operator!=](#op_neq)|[operator==](#op_eq_eq)|

## <a name="op_neq"></a>  operator!=

指定したクラスのアロケーター オブジェクト間の非等値をテストします。

```cpp
template <class Type, class Sync>
bool operator!=(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*left*|不等性をテストする一方のアロケーター オブジェクト。|
|*right*|不等性をテストする一方のアロケーター オブジェクト。|

### <a name="return-value"></a>戻り値

アロケーター オブジェクトが等しくない場合は **true**、アロケーター オブジェクトが等しい場合は **false**。

### <a name="remarks"></a>Remarks

テンプレート演算子は `!(left == right)` を返します。

## <a name="op_eq_eq"></a>  operator==

指定したクラスのアロケーター オブジェクト間の等値をテストします。

```cpp
template <class Type, class Sync>
bool operator==(
    const allocator_base<Type, Sync>& left,
    const allocator_base<Type, Sync>& right);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*left*|等しいかどうかをテストする一方のアロケーター オブジェクト。|
|*right*|等しいかどうかをテストする一方のアロケーター オブジェクト。|

### <a name="return-value"></a>戻り値

アロケーター オブジェクトが等しい場合は **true**、アロケーター オブジェクトが等しくない場合は **false**。

### <a name="remarks"></a>Remarks

このテンプレート演算子は `left.equals(right)` を返します。

## <a name="see-also"></a>関連項目

[\<allocators>](../standard-library/allocators-header.md)
