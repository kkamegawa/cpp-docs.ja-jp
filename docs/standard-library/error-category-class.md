---
title: error_category クラス
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_category
- system_error/std::error_category::value_type
- system_error/std::error_category::default_error_condition
- system_error/std::error_category::equivalent
- system_error/std::error_category::message
- system_error/std::error_category::name
helpviewer_keywords:
- std::error_category
- std::error_category::value_type
- std::error_category::default_error_condition
- std::error_category::equivalent
- std::error_category::message
- std::error_category::name
ms.assetid: e0a71e14-852d-4905-acd6-5f8ed426706d
ms.openlocfilehash: 308fa1a2309ddfda1a02fe6a687360185c1e7c6e
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245855"
---
# <a name="errorcategory-class"></a>error_category クラス

エラー コードのカテゴリを表すオブジェクトの抽象的な共通基底を表します。

## <a name="syntax"></a>構文

```cpp
class error_category;

constexpr error_category() noexcept;
virtual ~error_category();
error_category(const error_category&) = delete
```

## <a name="remarks"></a>Remarks

定義済みの 2 つのオブジェクト [generic_category](../standard-library/system-error-functions.md#generic_category) および [system_category](../standard-library/system-error-functions.md#system_category) によって `error_category` が実装されます。

## <a name="members"></a>メンバー

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[value_type](#value_type)|格納されたエラー コード値を表す型。|

### <a name="functions"></a>関数

|||
|-|-|
|[default_error_condition](#default_error_condition)|エラー条件オブジェクトのエラー コード値を格納します。|
|[equivalent](#equivalent)|エラー オブジェクトが同等であるかどうかを示す値を返します。|
|[generic_category](#generic)||
|[message](#message)|指定したエラー コードの名前を返します。|
|[name](#name)|カテゴリの名前を返します。|
|[system_category](#system)||

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#op_as)||
|[operator==](#op_eq_eq)|`error_category` オブジェクト間の同等性をテストします。|
|[operator!=](#op_neq)|`error_category` オブジェクト間の不等性をテストします。|
|[operator<](#op_lt)|[error_category](../standard-library/error-category-class.md) オブジェクトが比較のために渡される `error_category` オブジェクトより小さいかどうかをテストします。|

## <a name="default_error_condition"></a> default_error_condition

エラー条件オブジェクトのエラー コード値を格納します。

```cpp
virtual error_condition default_error_condition(int _Errval) const;
```

### <a name="parameters"></a>パラメーター

*_Errval*\
[error_condition](../standard-library/error-condition-class.md) オブジェクトに格納するエラー コード値。

### <a name="return-value"></a>戻り値

`error_condition(_Errval, *this)` を返します。

### <a name="remarks"></a>Remarks

### <a name="equivalent"></a> 等価

エラー オブジェクトが同等であるかどうかを示す値を返します。

```cpp
virtual bool equivalent(value_type _Errval,
    const error_condition& _Cond) const;

virtual bool equivalent(const error_code& _Code,
    value_type _Errval) const;
```

#### <a name="parameters"></a>パラメーター

*_Errval*\
比較するエラー コード値。

*_Cond*\
比較する [error_condition](../standard-library/error-condition-class.md) オブジェクト。

*(_C)* \
比較する [error_code](../standard-library/error-code-class.md) オブジェクト。

#### <a name="return-value"></a>戻り値

**true**カテゴリと値が、それ以外の場合は**false**します。

#### <a name="remarks"></a>Remarks

最初のメンバー関数は `*this == _Cond.category() && _Cond.value() == _Errval` を返します。

2 番目のメンバー関数は `*this == _Code.category() && _Code.value() == _Errval` を返します。

### <a name="generic"></a> generic_category

```cpp
const error_category& generic_category();
```

### <a name="message"></a> メッセージ

指定したエラー コードの名前を返します。

```cpp
virtual string message(error_code::value_type val) const = 0;
```

#### <a name="parameters"></a>パラメーター

*val*\
記述するエラー コード値。

#### <a name="return-value"></a>戻り値

エラー コードのわかりやすい名前を返します*val*のカテゴリ。

#### <a name="remarks"></a>Remarks

### <a name="name"></a> 名

カテゴリの名前を返します。

```cpp
virtual const char *name() const = 0;
```

#### <a name="return-value"></a>戻り値

カテゴリの名前を、null 終端バイト文字列として返します。

### <a name="op_as"></a> 演算子 =

```cpp
error_category& operator=(const error_category&) = delete;
```


### <a name="op_eq_eq"></a> 演算子 = =

`error_category` オブジェクト間の同等性をテストします。

```cpp
bool operator==(const error_category& right) const;
```

#### <a name="parameters"></a>パラメーター

*そうです*\
等しいかどうかをテストするオブジェクト。

#### <a name="return-value"></a>戻り値

オブジェクトが等しい場合は **true**、オブジェクトが等しくない場合は **false**。

#### <a name="remarks"></a>Remarks

このメンバー演算子は、`this == &right` を返します。

### <a name="op_neq"></a> operator!=

`error_category` オブジェクト間の不等性をテストします。

```cpp
bool operator!=(const error_category& right) const;
```

#### <a name="parameters"></a>パラメーター

*そうです*\
不等性をテストするオブジェクト。

#### <a name="return-value"></a>戻り値

**true**場合、`error_category`オブジェクトが等しく、`error_category`で渡されるオブジェクト*右*。 そうしないと**false**します。

#### <a name="remarks"></a>Remarks

このメンバー演算子は、 `(!*this == right)`を返します。

### <a name="op_lt"></a> 演算子&lt;

[error_category](../standard-library/error-category-class.md) オブジェクトが比較のために渡される `error_category` オブジェクトより小さいかどうかをテストします。

```cpp
bool operator<(const error_category& right) const;
```

#### <a name="parameters"></a>パラメーター

*そうです*\
比較される `error_category` オブジェクト。

#### <a name="return-value"></a>戻り値

`error_category` オブジェクトが、比較対象として渡された `error_category` より小さい場合は **true**。それ以外の場合は **false**。

#### <a name="remarks"></a>Remarks

このメンバー演算子は、 `this < &right`を返します。

### <a name="system"></a> system_category

```cpp
const error_category& system_category();
```

### <a name="value_type"></a> value_type

格納されたエラー コード値を表す型。

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Remarks

この型定義のシノニムは、 **int**します。
