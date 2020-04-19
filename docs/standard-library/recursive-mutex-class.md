---
title: recursive_mutex クラス
ms.date: 11/04/2016
f1_keywords:
- mutex/std::recursive_mutex
- mutex/std::recursive_mutex::recursive_mutex
- mutex/std::recursive_mutex::lock
- mutex/std::recursive_mutex::try_lock
- mutex/std::recursive_mutex::unlock
ms.assetid: eb5ffd1b-7e78-4559-8391-bb220ead42fc
helpviewer_keywords:
- std::recursive_mutex [C++]
- std::recursive_mutex [C++], recursive_mutex
- std::recursive_mutex [C++], lock
- std::recursive_mutex [C++], try_lock
- std::recursive_mutex [C++], unlock
ms.openlocfilehash: 448b4d03e4d38dc45621cddab7d8f5d03b805968
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451684"
---
# <a name="recursivemutex-class"></a>recursive_mutex クラス

*mutex 型*を表します。 [mutex](../standard-library/mutex-class-stl.md) とは異なり、既にロックされているオブジェクトのロック メソッドを呼び出す動作は詳細に定義されています。

## <a name="syntax"></a>構文

```cpp
class recursive_mutex;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[recursive_mutex](#recursive_mutex)|`recursive_mutex` オブジェクトを構築します。|
|[~recursive_mutex デストラクター](#dtorrecursive_mutex_destructor)|`recursive_mutex` オブジェクトによって使用されているすべてのリソースを解放します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[lock](#lock)|呼び出しスレッドがミューテックスの所有権を取得するまでそのスレッドをブロックします。|
|[try_lock](#try_lock)|ブロックせずにミューテックスの所有権を取得しようとします。|
|[unlock](#unlock)|ミューテックスの所有権を解放します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<ミューテックス >

**名前空間:** std

## <a name="lock"></a>  lock

呼び出しスレッドが `mutex` の所有権を取得するまでそのスレッドをブロックします。

```cpp
void lock();
```

### <a name="remarks"></a>Remarks

呼び出しスレッドが既に `mutex` を所有している場合、メソッドが直ちに返され、以前のロックは有効のままになります。

## <a name="recursive_mutex"></a>  recursive_mutex

ロックされていない `recursive_mutex` オブジェクトを構築します。

```cpp
recursive_mutex();
```

## <a name="dtorrecursive_mutex_destructor"></a>  ~recursive_mutex

オブジェクトによって使用されるすべてのリソースを解放します。

```cpp
~recursive_mutex();
```

### <a name="remarks"></a>Remarks

デストラクターの実行時にオブジェクトがロックされる場合の動作は未定義です。

## <a name="try_lock"></a>  try_lock

ブロックせずに `mutex` の所有権を取得しようとします。

```cpp
bool try_lock() noexcept;
```

### <a name="return-value"></a>戻り値

メソッドがの所有権`mutex`を正常に取得した場合は true。呼び出し元`mutex**; otherwise, **false`のスレッドがを既に所有している場合は。

### <a name="remarks"></a>Remarks

呼び出し元のスレッドが既に`mutex`を所有している場合、関数はすぐに**true**を返し、前のロックは有効のままになります。

## <a name="unlock"></a>  unlock

ミューテックスの所有権を解放します。

```cpp
void unlock();
```

### <a name="remarks"></a>Remarks

このメソッドが `mutex` の所有権を開放するのは、[lock](#lock) および [try_lock](#try_lock) が `recursive_mutex` オブジェクト上で正常に呼び出されたのと同じ回数だけ呼び出された後のみです。

呼び出しスレッドが `mutex` を所有していない場合の動作は未定義です。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
