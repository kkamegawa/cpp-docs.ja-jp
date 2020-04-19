---
title: mutex クラス (C++ 標準ライブラリ)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- mutex/std::mutex
- mutex/std::mutex::mutex
- mutex/std::mutex::lock
- mutex/std::mutex::native_handle
- mutex/std::mutex::try_lock
- mutex/std::mutex::unlock
ms.assetid: 7999d055-f74f-4303-810f-8d3c9cde2f69
helpviewer_keywords:
- std::mutex [C++]
- std::mutex [C++], mutex
- std::mutex [C++], lock
- std::mutex [C++], native_handle
- std::mutex [C++], try_lock
- std::mutex [C++], unlock
ms.openlocfilehash: 099cf17db7b99f9cd1d953a603db70f75c33358e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457064"
---
# <a name="mutex-class-c-standard-library"></a>mutex クラス (C++ 標準ライブラリ)

*mutex 型*を表します。 この型のオブジェクトを使用して、プログラム内で相互排他を適用できます。

## <a name="syntax"></a>構文

```cpp
class mutex;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[mutex](#mutex)|`mutex` オブジェクトを構築します。|
|[mutex::~mutex デストラクター](#dtormutex_destructor)|`mutex` オブジェクトで使用されたすべてのリソースを解放します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[lock](#lock)|呼び出しスレッドが `mutex` の所有権を取得するまでそのスレッドをブロックします。|
|[native_handle](#native_handle)|ミューテックス ハンドルを表す実装固有の型を返します。|
|[try_lock](#try_lock)|ブロックせずに `mutex` の所有権を取得しようとします。|
|[unlock](#unlock)|`mutex` の所有権を解放します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<ミューテックス >

**名前空間:** std

## <a name="lock"></a>  mutex::lock

呼び出しスレッドが `mutex` の所有権を取得するまでそのスレッドをブロックします。

```cpp
void lock();
```

### <a name="remarks"></a>Remarks

呼び出しスレッドが既に `mutex` を所有している場合の動作は未定義です。

## <a name="mutex"></a>  mutex::mutex コンストラクター

ロックされていない `mutex` オブジェクトを構築します。

```cpp
constexpr mutex() noexcept;
```

## <a name="dtormutex_destructor"></a>  mutex::~mutex デストラクター

`mutex` オブジェクトによって使用されているすべてのリソースを解放します。

```cpp
~mutex();
```

### <a name="remarks"></a>Remarks

デストラクターの実行時にオブジェクトがロックされる場合の動作は未定義です。

## <a name="native_handle"></a>  mutex::native_handle

ミューテックス ハンドルを表す実装固有の型を返します。 ミューテックス ハンドルは、実装固有の方法で使用できます。

```cpp
native_handle_type native_handle();
```

### <a name="return-value"></a>戻り値

`native_handle_type` は、`void *` としてキャストされる `Concurrency::critical_section *` と定義されます。

## <a name="try_lock"></a>  mutex::try_lock

ブロックせずに `mutex` の所有権を取得しようとします。

```cpp
bool try_lock();
```

### <a name="return-value"></a>戻り値

メソッドがの所有権`mutex`を正常に取得した場合は true。それ以外の場合は**false**。

### <a name="remarks"></a>Remarks

呼び出しスレッドが既に `mutex` を所有している場合の動作は未定義です。

## <a name="unlock"></a>  mutex::unlock

`mutex` の所有権を解放します。

```cpp
void unlock();
```

### <a name="remarks"></a>Remarks

呼び出しスレッドが `mutex` を所有していない場合の動作は未定義です。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
