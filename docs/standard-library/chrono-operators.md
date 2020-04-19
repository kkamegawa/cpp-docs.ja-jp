---
title: '&lt;chrono&gt; 演算子'
ms.date: 11/04/2016
f1_keywords:
- chrono/std::operator modulo
ms.assetid: c5a19267-4684-40c1-b7a9-cc1012b058f3
ms.openlocfilehash: 398e2429c38cffb454c7b510aa5ab44fbe4cfef6
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244882"
---
# <a name="ltchronogt-operators"></a>&lt;chrono&gt; 演算子

## <a name="operator-"></a> 演算子-

[duration](../standard-library/duration-class.md) および [time_point](../standard-library/time-point-class.md) オブジェクトの減算または否定の演算子。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator-(
       const duration<Rep1, Period1>& Left,
       cconst duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type
   operator-(
       const time_point<Clock, Duration1>& Time,
       const duration<Rep2, Period2>& Dur);

template <class Clock, class Duration1, class Duration2>
constexpr typename common_type<Duration1, Duration2>::type
   operator-(
       const time_point<Clock, Duration1>& Left,
       const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>パラメーター

*左*\
左側の `duration` オブジェクトまたは `time_point` オブジェクト。

*そうです*\
右側の `duration` オブジェクトまたは `time_point` オブジェクト。

*時間*\
`time_point` オブジェクト。

*期間*\
`duration` オブジェクト。

### <a name="return-value"></a>戻り値

最初の関数は、間隔の長さが 2 つの引数の期間の違いである `duration` オブジェクトを返します。

2 番目の関数を返します、`time_point`オブジェクトで表される時間間隔の符号を反転によって、転置される時点を表す*期間*、によって指定された時間内のポイントから*時間*.

3 番目の関数を返します、`duration`間の時間間隔を表すオブジェクトを*左*と*右*します。

## <a name="op_neq"></a> operator!=

[duration](../standard-library/duration-class.md) または [time_point](../standard-library/time-point-class.md) オブジェクトの非等値演算子。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator!=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator!=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>パラメーター

*左*\
左側の `duration` オブジェクトまたは `time_point` オブジェクト。

*そうです*\
右側の `duration` オブジェクトまたは `time_point` オブジェクト。

### <a name="return-value"></a>戻り値

各関数から返される値は `!(Left == Right)` です。

## <a name="op_star"></a> 演算子 *

[duration](../standard-library/chrono-operators.md#op_star) オブジェクトの乗算演算子。

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator*(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Mult);

template <class Rep1, class Rep2, class Period2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period2>
   operator*(
       const Rep1& Mult,
       const duration<Rep2,
       Period2>& Dur);
```

### <a name="parameters"></a>パラメーター

*期間*\
`duration` オブジェクト。

*Mult*\
整数値。

### <a name="return-value"></a>戻り値

各関数を返します、`duration`間隔の長さがオブジェクト*Mult*の長さで乗算*期間*します。

`is_convertible<Rep2, common_type<Rep1, Rep2>>` が *true* にならない限り、最初の関数はオーバーロードの解決に関与しません。 詳細については、「[<type_traits>](../standard-library/type-traits.md)」を参照してください。

`is_convertible<Rep1, common_type<Rep1, Rep2>>` が *true* にならない限り、2 番目の関数はオーバーロードの解決に関与しません。 詳しくは、「[<type_traits>](../standard-library/type-traits.md)」をご覧ください。

## <a name="op_div"></a> 演算子/

[duration](../standard-library/chrono-operators.md#op_star) オブジェクトの除算演算子。

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<typename common_type<Rep1, Rep2>::type, Period1>
   operator/(
     const duration<Rep1, Period1>& Dur,
     const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<Rep1, Rep2>::type
   operator/(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>パラメーター

*期間*\
`duration` オブジェクト。

*div*\
整数値。

*左*\
左側の `duration` オブジェクト。

*そうです*\
右側の `duration` オブジェクト。

### <a name="return-value"></a>戻り値

1 つ目の演算子は間隔の duration オブジェクトを返しますの長さ*期間*値で除算*Div*します。

2 番目の演算子は、の間隔の長さの比率を返します*左*と*右*します。

`is_convertible<Rep2, common_type<Rep1, Rep2>>` が *true を保持*せず、かつ `Rep2` が `duration` のインスタンス化ではない限り、最初の演算子はオーバーロードの解決に関与しません。 詳しくは、「[<type_traits>](../standard-library/type-traits.md)」をご覧ください。

## <a name="op_add"></a> operator +

[duration](../standard-library/duration-class.md) および [time_point](../standard-library/time-point-class.md) オブジェクトを追加します。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, Period1>, duration<Rep2, Period2>>::type
   operator+(
      const duration<Rep1, Period1>& Left,
      const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Rep2, class Period2>
constexpr time_point<Clock, typename common_type<Duration1, duration<Rep2, Period2>>::type>
   operator+(
      const time_point<Clock, Duration1>& Time,
      const duration<Rep2, Period2>& Dur);

template <class Rep1, class Period1, class Clock, class Duration2>
time_point<Clock, constexpr typename common_type<duration<Rep1, Period1>, Duration2>::type>
   operator+(
      const duration<Rep1, Period1>& Dur,
      const time_point<Clock, Duration2>& Time);
```

### <a name="parameters"></a>パラメーター

*左*\
左側の `duration` オブジェクトまたは `time_point` オブジェクト。

*そうです*\
右側の `duration` オブジェクトまたは `time_point` オブジェクト。

*時間*\
`time_point` オブジェクト。

*期間*\
`duration` オブジェクト。

### <a name="return-value"></a>戻り値

最初の関数を返します、`duration`の間隔の合計に等しい時間間隔を含むオブジェクト*左*と*右*します。

2 番目と 3 番目の関数が返す、`time_point`間隔によって、転置される時点を表すオブジェクト*期間*、特定の時点から*時間*します。

## <a name="op_lt"></a> 演算子&lt;

一方の [duration](../standard-library/duration-class.md) または [time_point](../standard-library/time-point-class.md) オブジェクトが、もう一方の `duration` または `time_point` オブジェクト未満かどうかを判断します。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>パラメーター

*左*\
左側の `duration` オブジェクトまたは `time_point` オブジェクト。

*そうです*\
右側の `duration` オブジェクトまたは `time_point` オブジェクト。

### <a name="return-value"></a>戻り値

最初の関数を返します**true**場合の間隔の長さ*左*の間隔の長さより小さい*右*します。 関数を返しますそれ以外の場合、 **false**します。

2 番目の関数を返します**true**場合*左*前*右*します。 関数を返しますそれ以外の場合、 **false**します。

## <a name="op_lt_eq"></a> 演算子&lt;=

一方の [duration](../standard-library/duration-class.md) または [time_point](../standard-library/time-point-class.md) オブジェクトの値がもう一方の `duration` または `time_point` オブジェクトの値未満かどうかを判断します。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator<=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator<=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>パラメーター

*左*\
左側の `duration` オブジェクトまたは `time_point` オブジェクト。

*そうです*\
右側の `duration` オブジェクトまたは `time_point` オブジェクト。

### <a name="return-value"></a>戻り値

各関数から返される値は `!(Right < Left)` です。

## <a name="op_eq_eq"></a> 演算子 = =

2 つの `duration` オブジェクトが同じ長さの時間間隔を表しているかどうか、または 2 つの `time_point` オブジェクトが同じ時点を表しているかどうかを判断します。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator==(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator==(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>パラメーター

*左*\
左側の `duration` オブジェクトまたは `time_point` オブジェクト。

*そうです*\
右側の `duration` オブジェクトまたは `time_point` オブジェクト。

### <a name="return-value"></a>戻り値

最初の関数を返します**true**場合*左*と*右*同じ長さである時間間隔を表します。 関数を返しますそれ以外の場合、 **false**します。

2 番目の関数を返します**true**場合*左*と*右*の同じ時点を表しています。 関数を返しますそれ以外の場合、 **false**します。

## <a name="op_gt"></a> 演算子&gt;

1 つの [duration](../standard-library/duration-class.md) オブジェクトまたは [time_point](../standard-library/time-point-class.md) オブジェクトが、別の `duration` オブジェクトまたは `time_point` オブジェクトより大きいかどうかを判断します。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>パラメーター

*左*\
左側の `duration` オブジェクトまたは `time_point` オブジェクト。

*そうです*\
右側の `duration` オブジェクトまたは `time_point` オブジェクト。

### <a name="return-value"></a>戻り値

各関数から返される値は `Right < Left` です。

## <a name="op_gt_eq"></a> 演算子&gt;=

一方の [duration](../standard-library/duration-class.md) または [time_point](../standard-library/time-point-class.md) オブジェクトの値がもう一方の `duration` または `time_point` オブジェクトの値以上かどうかを判断します。

```cpp
template <class Rep1, class Period1, class Rep2, class Period2>
constexpr bool operator>=(
    const duration<Rep1, Period1>& Left,
    const duration<Rep2, Period2>& Right);

template <class Clock, class Duration1, class Duration2>
constexpr bool operator>=(
    const time_point<Clock, Duration1>& Left,
    const time_point<Clock, Duration2>& Right);
```

### <a name="parameters"></a>パラメーター

*左*\
左側の `duration` オブジェクトまたは `time_point` オブジェクト。

*そうです*\
右側の `duration` オブジェクトまたは `time_point` オブジェクト。

### <a name="return-value"></a>戻り値

各関数から返される値は `!(Left < Right)` です。

## <a name="op_modulo"></a> modulo 演算子

[duration](../standard-library/duration-class.md) オブジェクトに対する剰余演算の演算子。

```cpp
template <class Rep1, class Period1, class Rep2>
constexpr duration<Rep1, Period1, Rep2>::type
   operator%(
      const duration<Rep1, Period1>& Dur,
      const Rep2& Div);

template <class Rep1, class Period1, class Rep2, class Period2>
constexpr typename common_type<duration<Rep1, _Period1>, duration<Rep2, Period2>>::type
   operator%(
     const duration<Rep1, Period1>& Left,
     const duration<Rep2, Period2>& Right);
```

### <a name="parameters"></a>パラメーター

*期間*\
`duration` オブジェクト。

*div*\
整数値。

*左*\
左側の `duration` オブジェクト。

*そうです*\
右側の `duration` オブジェクト。

### <a name="return-value"></a>戻り値

最初の関数を返します、`duration`間隔の長さがオブジェクト*期間*剰余*Div*します。

2 番目の関数が表す値を返します*左*剰余*右*します。
