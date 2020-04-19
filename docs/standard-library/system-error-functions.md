---
title: '&lt;system_error&gt; 関数'
ms.date: 03/15/2019
f1_keywords:
- system_error/std::generic_category
- system_error/std::make_error_code
- system_error/std::make_error_condition
- system_error/std::system_category
ms.assetid: 57d6f15f-f0b7-4e2f-80fe-31d3c320ee33
helpviewer_keywords:
- std::generic_category
- std::make_error_code
- std::make_error_condition
- std::system_category
ms.openlocfilehash: ab4d0d1ee810df8f719bba762262eb03bf899408
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245113"
---
# <a name="ltsystemerrorgt-functions"></a>&lt;system_error&gt; 関数

## <a name="generic_category"></a> generic_category

一般的なエラーのカテゴリを表します。

```cpp
const error_category& generic_category() noexcept;
```

### <a name="remarks"></a>Remarks

`generic_category`オブジェクトの実装は、 [error_category](../standard-library/error-category-class.md)します。

## <a name="is_error_code_enum_v"></a> is_error_code_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_code_enum_v = is_error_code_enum<T>::value;
```

## <a name="is_error_condition_enum_v"></a> is_error_condition_enum_v

```cpp
template <class T> 
    inline constexpr bool is_error_condition_enum_v = is_error_condition_enum<T>::value;
```

## <a name="make_error_code"></a> make_error_code

エラー コード オブジェクトを作成します。

```cpp
error_code make_error_code(std::errc error) noexcept;
```

### <a name="parameters"></a>パラメーター

*エラー*\
`std::errc`エラー コード オブジェクトに格納する列挙値。

### <a name="return-value"></a>戻り値

エラー コード オブジェクト。

### <a name="remarks"></a>Remarks

## <a name="make_error_condition"></a> make_error_condition

エラー条件オブジェクトを作成します。

```cpp
error_condition make_error_condition(std::errc error) noexcept;
```

### <a name="parameters"></a>パラメーター

*エラー*\
`std::errc`エラー コード オブジェクトに格納する列挙値。

### <a name="return-value"></a>戻り値

エラー条件オブジェクト。

### <a name="remarks"></a>Remarks

## <a name="system_category"></a> system_category

低レベル システム オーバーフローによって発生したエラーのカテゴリを表します。

```cpp
const error_category& system_category() noexcept;
```

### <a name="remarks"></a>Remarks

`system_category`オブジェクトの実装は、 [error_category](../standard-library/error-category-class.md)します。
