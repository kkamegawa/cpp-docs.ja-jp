---
title: error_condition クラス
ms.date: 11/04/2016
f1_keywords:
- system_error/std::error_condition
- system_error/std::error_condition::value_type
- system_error/std::error_condition::assign
- system_error/std::error_condition::category
- system_error/std::error_condition::clear
- system_error/std::error_condition::message
- system_error/std::error_condition::operator bool
helpviewer_keywords:
- std::error_condition
- std::error_condition::value_type
- std::error_condition::assign
- std::error_condition::category
- std::error_condition::clear
- std::error_condition::message
ms.assetid: 6690f481-97c9-4554-a0ff-851dc96b7a06
ms.openlocfilehash: cbadf6a22871cc9a23d37c095a398490c8a4c72c
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245800"
---
# <a name="errorcondition-class"></a>error_condition クラス

ユーザー定義のエラー コードを表します。

## <a name="syntax"></a>構文

```cpp
class error_condition;
```

## <a name="remarks"></a>Remarks

`error_condition` 型のオブジェクトは、エラー コード値を格納するほか、レポートされたユーザー定義のエラーに使用されるエラー コードの[カテゴリ](../standard-library/error-category-class.md)を表すオブジェクトを指すポインターも格納します。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[error_condition](#error_condition)|`error_condition` 型のオブジェクトを構築します。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[value_type](#value_type)|格納されたエラー コード値を表す型。|

### <a name="functions"></a>関数

|||
|-|-|
|[assign](#assign)|エラー コード値とカテゴリをエラー条件に割り当てます。|
|[category](#category)|エラー カテゴリを返します。|
|[clear](#clear)|エラー コード値とカテゴリをクリアします。|
|[message](#message)|エラー コードの名前を返します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator==](#op_eq_eq)|`error_condition` オブジェクト間の同等性をテストします。|
|[operator!=](#op_neq)|`error_condition` オブジェクト間の不等性をテストします。|
|[operator<](#op_lt)|`error_condition` オブジェクトが比較のために渡される `error_code` オブジェクトより小さいかどうかをテストします。|
|[operator=](#op_eq)|`error_condition` オブジェクトに新しい列挙値を代入します。|
|[operator bool](#op_bool)|`error_condition` 型の変数をキャストします。|

### <a name="assign"></a> 割り当てる

エラー コード値とカテゴリをエラー条件に割り当てます。

```cpp
void assign(value_type val, const error_category& _Cat);
```

#### <a name="parameters"></a>パラメーター

*val*\
`error_code` に格納するエラー コード値。

*_Cat*\
`error_code` に格納するエラー カテゴリ。

#### <a name="remarks"></a>Remarks

メンバー関数のストア*val*エラー コード値とへのポインターとして *_Cat*します。

### <a name="category"></a> カテゴリ

エラー カテゴリを返します。

```cpp
const error_category& category() const;
```

#### <a name="return-value"></a>戻り値

格納されたエラー カテゴリへの参照

#### <a name="remarks"></a>Remarks

### <a name="clear"></a> オフ

エラー コード値とカテゴリをクリアします。

```cpp
clear();
```

#### <a name="remarks"></a>Remarks

このメンバー関数はゼロ エラー コード値と [generic_category](../standard-library/system-error-functions.md#generic_category) を指すポインターを格納します。

### <a name="error_condition"></a> error_condition

`error_condition` 型のオブジェクトを構築します。

```cpp
error_condition();

error_condition(value_type val, const error_category& _Cat);

template <class _Enum>
error_condition(_Enum _Errcode,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_code>::type* = 0);
```

#### <a name="parameters"></a>パラメーター

*val*\
`error_condition` に格納するエラー コード値。

*_Cat*\
`error_condition` に格納するエラー カテゴリ。

*_Errcode*\
`error_condition` に格納する列挙値。

#### <a name="remarks"></a>Remarks

最初のコンストラクターはゼロ エラー コード値と [generic_category](../standard-library/system-error-functions.md#generic_category) を指すポインターを格納します。

2 番目のコンス トラクター ストア*val*エラー コード値とへのポインターとして[error_category](../standard-library/error-category-class.md)します。

3 番目のコンストラクターは、エラー コード値としての `(value_type)_Errcode` と [generic_category](../standard-library/system-error-functions.md#generic_category) を指すポインターを格納します。

### <a name="message"></a> メッセージ

エラー コードの名前を返します。

```cpp
string message() const;
```

#### <a name="return-value"></a>戻り値

エラー コードの名前を表す `string`。

#### <a name="remarks"></a>Remarks

このメンバー関数は `category().message(value())` を返します。

### <a name="op_eq_eq"></a> 演算子 = =

`error_condition` オブジェクト間の同等性をテストします。

```cpp
bool operator==(const error_condition& right) const;
```

#### <a name="parameters"></a>パラメーター

*そうです*\
等しいかどうかをテストするオブジェクト。

#### <a name="return-value"></a>戻り値

オブジェクトが等しい場合は **true**、オブジェクトが等しくない場合は **false**。

#### <a name="remarks"></a>Remarks

このメンバー演算子は、 `category() == right.category() && value == right.value()`を返します。

### <a name="op_neq"></a> operator!=

`error_condition` オブジェクト間の不等性をテストします。

```cpp
bool operator!=(const error_condition& right) const;
```

#### <a name="parameters"></a>パラメーター

*そうです*\
不等性をテストするオブジェクト。

#### <a name="return-value"></a>戻り値

**true**場合、`error_condition`オブジェクトが等しく、`error_condition`で渡されるオブジェクト*右*。 そうしないと**false**します。

#### <a name="remarks"></a>Remarks

このメンバー演算子は、 `!(*this == right)`を返します。

### <a name="op_lt"></a> 演算子&lt;

`error_condition` オブジェクトが比較のために渡される `error_code` オブジェクトより小さいかどうかをテストします。

```cpp
bool operator<(const error_condition& right) const;
```

#### <a name="parameters"></a>パラメーター

*そうです*\
比較される `error_condition` オブジェクト。

#### <a name="return-value"></a>戻り値

`error_condition` オブジェクトが、比較対象として渡された `error_condition` より小さい場合は **true**。それ以外の場合は **false**。

#### <a name="remarks"></a>Remarks

このメンバー演算子は、 `category() < right.category() || category() == right.category() && value < right.value()`を返します。

### <a name="op_eq"></a> 演算子 =

`error_condition` オブジェクトに新しい列挙値を代入します。

```cpp
template <class _Enum>
error_condition(_Enum error,
    typename enable_if<is_error_condition_enum<_Enum>::value,
    error_condition>::type&
    operator=(Enum _Errcode);
```

#### <a name="parameters"></a>パラメーター

*_Errcode*\
`error_condition` オブジェクトに代入する列挙値。

#### <a name="return-value"></a>戻り値

メンバー関数によって新しい列挙値が代入される `error_condition` オブジェクトへの参照。

#### <a name="remarks"></a>Remarks

このメンバー演算子は、エラー コード値としての `(value_type)error` と [generic_category](../standard-library/system-error-functions.md#generic_category) を指すポインターを格納します。 `*this` を返します。

### <a name="op_bool"></a> operator bool

`error_condition` 型の変数をキャストします。

```cpp
explicit operator bool() const;
```

#### <a name="return-value"></a>戻り値

`error_condition` オブジェクトのブール値。

#### <a name="remarks"></a>Remarks

演算子に変換できる値を返します**true**場合にのみ[値](#value)0 と等しくないです。 戻り値の型にのみ変換可能**bool**ではなく、`void *`またはその他の既知のスカラー型。

### <a name="value"></a> 値

格納されたエラー コード値を返します。

```cpp
value_type value() const;
```

#### <a name="return-value"></a>戻り値

[value_type](#value_type) 型の格納されたエラー コード値。

#### <a name="remarks"></a>Remarks

### <a name="value_type"></a> value_type

格納されたエラー コード値を表す型。

```cpp
typedef int value_type;
```

#### <a name="remarks"></a>Remarks

型の定義がのシノニム**int**します。
