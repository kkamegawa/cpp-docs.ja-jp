---
title: nested_exception クラス
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: 5741b3aa255f915500f5fe79ab5374c8c86f8814
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460184"
---
# <a name="nestedexception-class"></a>nested_exception クラス

クラスは、多重継承で使用する例外を記述します。 現在処理されている例外をキャプチャし、後で使用できるように格納します。

## <a name="syntax"></a>構文

```cpp
class nested_exception {
    public:
        nested_exception();
        nested_exception(const nested_exception&) = default;
        virtual ~nested_exception() = default; // access functions
};
```

## <a name="members"></a>メンバー

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](#op_as)||

### <a name="functions"></a>関数

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|格納されている例外をスローします。|
|[nested_ptr](#nested_ptr)|格納されている例外を返します。|

### <a name="op_as"></a>operator =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a>nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>戻り値

この`nested_exception`オブジェクトによってキャプチャされた格納された例外。

### <a name="rethrow_nested"></a>rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>Remarks

が`nested_ptr()` null ポインターを返す場合、関数は`std::terminate()`を呼び出します。 それ以外の場合は、によって`*this`キャプチャされた格納済みの例外をスローします。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<exception>

**名前空間:** std

## <a name="see-also"></a>関連項目

[exception クラス](../standard-library/exception-class.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
