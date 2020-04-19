---
title: '&lt;system_error&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- system_error/std::operator!=
- system_error/std::operator==
ms.assetid: c14edefb-bd8a-4e90-88d3-c59c98e6f73c
ms.openlocfilehash: 5cf6a455beb5654ef65f7411db4783a32c71d625
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246212"
---
# <a name="ltsystemerrorgt-operators"></a>&lt;system_error&gt; 演算子

## <a name="op_eq_eq"></a> 演算子 = =

演算子の左側のオブジェクトが右側のオブジェクトと等しいかどうかを調べます。

```cpp
bool operator==(const error_code& left,
    const error_condition& right);

bool operator==(const error_condition& left,
    const error_code& right);

bool operator==(const error_condition& left,
    const error_condition& right);
```

### <a name="parameters"></a>パラメーター

*左*\
等しいかどうかをテストするオブジェクト。

*そうです*\
等しいかどうかをテストするオブジェクト。

### <a name="return-value"></a>戻り値

オブジェクトが等しい場合は **true**、オブジェクトが等しくない場合は **false**。

### <a name="remarks"></a>Remarks

この関数は `left.category() == right.category() && left.value() == right.value()` を返します。

## <a name="op_neq"></a> operator!=

演算子の左側のオブジェクトが右側のオブジェクトと等しくないかどうかを調べます。

```cpp
bool operator!=(const error_code& left, const error_condition& right);
bool operator!=(const error_condition& left, const error_code& right);
bool operator!=(const error_code& left, const error_code& right);
bool operator!=(const error_condition& left, const error_condition& right);
```

### <a name="parameters"></a>パラメーター

*左*\
不等性をテストするオブジェクト。

*そうです*\
不等性をテストするオブジェクト。

### <a name="return-value"></a>戻り値

**true**オブジェクトが渡された場合*左*が渡されたオブジェクトと等しく*右*。 そうしないと**false**します。

### <a name="remarks"></a>Remarks

この関数は `!(left == right)` を返します。

## <a name="op_lt"></a> 演算子&lt;

オブジェクトが比較のために渡されるオブジェクトより小さいかどうかをテストします。

```cpp
template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_code_enum<_Enum>::value,
    const error_code&>::type left, _Enum right);

template <class _Enum>
inline bool operator<(
    _Enum left,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type right);

template <class _Enum>
inline bool operator<(
    typename enable_if<is_error_condition_enum<_Enum>::value,
    const error_condition&>::type left, _Enum right);
```

### <a name="parameters"></a>パラメーター

*左*\
比較されるオブジェクト。

*そうです*\
比較されるオブジェクト。

### <a name="return-value"></a>戻り値

**true**オブジェクトが渡された場合*左*で渡されるオブジェクトより小さい*右*;それ以外の場合、 **false**します。

### <a name="remarks"></a>Remarks

この関数はエラー順序をテストします。

## <a name="op_ostream"></a> 演算子&lt;&lt;

```cpp
template <class charT, class traits> 
    basic_ostream<charT, traits>& operator<<(basic_ostream<charT, traits>& os, const error_code& ec);
```
