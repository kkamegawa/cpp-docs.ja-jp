---
title: shared_future クラス
ms.date: 11/04/2016
f1_keywords:
- future/std::shared_future
- future/std::shared_future::shared_future
- future/std::shared_future::get
- future/std::shared_future::valid
- future/std::shared_future::wait
- future/std::shared_future::wait_for
- future/std::shared_future::wait_until
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
helpviewer_keywords:
- std::shared_future [C++]
- std::shared_future [C++], shared_future
- std::shared_future [C++], get
- std::shared_future [C++], valid
- std::shared_future [C++], wait
- std::shared_future [C++], wait_for
- std::shared_future [C++], wait_until
ms.openlocfilehash: 3b08a1341ed450dd5d5cee93cdfcbab57f8d6760
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450495"
---
# <a name="sharedfuture-class"></a>shared_future クラス

*非同期のリターン オブジェクト*を記述します。 [future](../standard-library/future-class.md) オブジェクトとは異なり、*非同期プロバイダー*を任意の数の `shared_future` オブジェクトに関連付けることができます。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
class shared_future;
```

## <a name="remarks"></a>Remarks

`valid`、`operator=` のメソッド、および*空の* `shared_future` オブジェクト上のデストラクター以外は呼び出しません。

`shared_future` オブジェクトは同期されません。 同じオブジェクト上で複数のスレッドからメソッドを呼び出すことは、結果が予測不可能なデータ競合をもたらします。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[shared_future](#shared_future)|`shared_future` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[get](#get)|*関連付けられた非同期状態*に格納されている結果を取得します。|
|[valid](#valid)|オブジェクトが空でないかどうかを指定します。|
|[wait](#wait)|関連付けられた非同期状態が準備できるまで、現在のスレッドをブロックします。|
|[wait_for](#wait_for)|関連付けられた非同期状態が準備できるまで、または指定した時間が経過するまでブロックします。|
|[wait_until](#wait_until)|関連付けられた非同期状態が準備できるまで、または指定した時点までブロックします。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[shared_future::operator=](#op_eq)|新しい関連付けられた非同期状態を割り当てます。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<今後の >

**名前空間:** std

## <a name="get"></a>  shared_future::get

*関連付けられた非同期状態*に格納されている結果を取得します。

```cpp
const Ty& get() const;

Ty& get() const;

void get() const;
```

### <a name="remarks"></a>Remarks

結果が例外の場合は、そのメソッドが再スローします。 それ以外の場合、結果が返されます。

結果を取得する前に、このメソッドは、関連付けられた非同期状態が準備できるまで、現在のスレッドをブロックします。

部分的特殊化 `shared_future<Ty&>` では、格納されている値は、実質的には*非同期プロバイダー*に戻り値として渡されたオブジェクトへの参照です。

特殊化`shared_future<void>`には格納されている値が存在しないため、メソッドは**void**を返します。

## <a name="op_eq"></a>  shared_future::operator=

指定したオブジェクトから、*関連付けられた非同期状態*を転送します。

```cpp
shared_future& operator=(shared_future&& Right) noexcept;
shared_future& operator=(const shared_future& Right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
`shared_future` オブジェクト。

### <a name="return-value"></a>戻り値

`*this`

### <a name="remarks"></a>Remarks

最初の演算子では、操作の後に、 *Right*に関連付けられた非同期状態がありません。

2番目のメソッドでは、 *Right*は関連付けられた非同期状態を保持します。

## <a name="shared_future"></a>  shared_future::shared_future コンストラクター

`shared_future` オブジェクトを構築します。

```cpp
shared_future() noexcept;
shared_future(future<Ty>&& Right) noexcept;
shared_future(shared_future&& Right) noexcept;
shared_future(const shared_future& Right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
[future](../standard-library/future-class.md) または `shared_future` オブジェクト。

### <a name="remarks"></a>Remarks

1 つ目のコンストラクターは、*関連付けられた非同期状態*がない `shared_future` オブジェクトを構築します。

2番目と3番目`shared_future`のコンストラクターは、オブジェクトを構築し、関連付けられている非同期状態を*右*から転送します。 *Right*には、関連付けられた非同期状態がありません。

4番目のコンストラクター `shared_future`は *、と同じ*関連付けられた非同期状態を持つオブジェクトを構築します。

## <a name="valid"></a>  shared_future::valid

オブジェクトが*関連付けられた非同期状態*であるかどうかを指定します。

```cpp
bool valid() noexcept;
```

### <a name="return-value"></a>戻り値

オブジェクトに関連付けられた非同期状態がある場合は**true** 。それ以外の場合は**false**。

## <a name="wait"></a>  shared_future::wait

*関連付けられた非同期状態*が *ready* になるまで、現在のスレッドをブロックします。

```cpp
void wait() const;
```

### <a name="remarks"></a>Remarks

関連付けられている非同期状態は、非同期プロバイダーが戻り値を格納した場合か例外を格納した場合のみ、準備完了になります。

## <a name="wait_for"></a>  shared_future::wait_for

関連付けられた非同期状態が *ready* になるまで、または指定した時間が経過するまで、現在のスレッドをブロックします。

```cpp
template <class Rep, class Period>
future_status wait_for(
    const chrono::duration<Rep, Period>& Rel_time) const;
```

### <a name="parameters"></a>パラメーター

*Rel_time*\
スレッドがブロックする最大の時間間隔を指定する [chrono::duration](../standard-library/duration-class.md) オブジェクト。

### <a name="return-value"></a>戻り値

呼び出し側に戻る理由を示す [future_status](../standard-library/future-enums.md#future_status)。

### <a name="remarks"></a>Remarks

関連付けられている非同期状態は、非同期プロバイダーが戻り値を格納した場合か例外を格納した場合のみ *ready* になります。

## <a name="wait_until"></a>  shared_future::wait_until

関連付けられた非同期状態が *ready* になるまで、または指定した時点後まで現在のスレッドをブロックします。

```cpp
template <class Clock, class Duration>
future_status wait_until(
    const chrono::time_point<Clock, Duration>& Abs_time) const;
```

### <a name="parameters"></a>パラメーター

*Abs_time*\
スレッドがブロックを解除できる時間を指定する [chrono::time_point](../standard-library/time-point-class.md) オブジェクト。

### <a name="return-value"></a>戻り値

呼び出し側に戻る理由を示す [future_status](../standard-library/future-enums.md#future_status)。

### <a name="remarks"></a>Remarks

関連付けられている非同期状態は、非同期プロバイダーが戻り値を格納した場合か例外を格納した場合のみ、準備完了になります。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<future>](../standard-library/future.md)
