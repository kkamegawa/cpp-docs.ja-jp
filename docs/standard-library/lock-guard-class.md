---
title: lock_guard クラス
ms.date: 11/04/2016
f1_keywords:
- mutex/std::lock_guard
- mutex/std::lock_guard::lock_guard
ms.assetid: 57121f0d-9c50-481c-b971-54e64df864e0
ms.openlocfilehash: f59860c3aaa9ef7458fe5e30b85b119dede52c72
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453853"
---
# <a name="lockguard-class"></a>lock_guard クラス

オブジェクトを作成し、そのデストラクタ―が `mutex` のロックを解除するためにインスタンス化できるテンプレートを表します。

## <a name="syntax"></a>構文

```cpp
template <class Mutex>
class lock_guard;
```

## <a name="remarks"></a>Remarks

テンプレート引数 `Mutex` には *mutex 型*を指定する必要があります。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|`lock_guard::mutex_type`|テンプレート引数 `Mutex` のシノニム。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[lock_guard](#lock_guard)|`lock_guard` オブジェクトを構築します。|
|[lock_guard::~lock_guard デストラクター](#dtorlock_guard_destructor)|コンストラクターに渡された `mutex` をロック解除します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<ミューテックス >

**名前空間:** std

## <a name="lock_guard"></a>  lock_guard::lock_guard コンストラクター

`lock_guard` オブジェクトを構築します。

```cpp
explicit lock_guard(mutex_type& Mtx);

lock_guard(mutex_type& Mtx, adopt_lock_t);
```

### <a name="parameters"></a>パラメーター

*Mtx.exe*\
*mutex 型*オブジェクト。

### <a name="remarks"></a>Remarks

1つ目のコンストラクターは、型`lock_guard`のオブジェクトを構築し、 *mtx.exe*をロックします。 *Mtx.exe*が再帰的なミューテックスでない場合は、このコンストラクターが呼び出されるときにロックを解除する必要があります。

2番目のコンストラクターは、 *mtx.exe*をロックしません。 このコンストラクターが呼び出されたときに、 *mtx.exe*をロックする必要があります。 このコンストラクターでは例外はスローされません。

## <a name="dtorlock_guard_destructor"></a>  lock_guard::~lock_guard デストラクター

コンストラクターに渡された `mutex` をロック解除します。

```cpp
~lock_guard() noexcept;
```

### <a name="remarks"></a>Remarks

デストラクターの実行時に `mutex` が存在しない場合の動作は未定義です。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
