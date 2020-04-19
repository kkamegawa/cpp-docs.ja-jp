---
title: duration クラス
ms.date: 03/27/2016
f1_keywords:
- chrono/std::chrono::duration
- chrono/std::chrono::duration::duration
- chrono/std::chrono::duration::count
- chrono/std::chrono::duration::max
- chrono/std::chrono::duration::min
- chrono/std::chrono::duration::zero
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
helpviewer_keywords:
- std::chrono [C++], duration
ms.openlocfilehash: 4c537b7dfdd23ba641438e0caf6306cf5549b2d7
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454307"
---
# <a name="duration-class"></a>duration クラス

2 つの時点の間における経過時間である *time interval* を保持する型を表します。

## <a name="syntax"></a>構文

```cpp
template <class Rep, class Period = ratio<1>>
class duration;
template <class Rep, class Period>
class duration;
template <class Rep, class Period1, class Period2>
class duration <duration<Rep, Period1>, Period2>;
```

## <a name="remarks"></a>Remarks

テンプレート引数 `Rep` では、間隔内でのクロック ティック数を保持するために使用する型を記述します。 テンプレート引数 `Period` は、各ティックが表す間隔のサイズを記述する [ratio](../standard-library/ratio.md) のインスタンス化です。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|duration::period Typedef|テンプレート パラメーター `Period` のシノニムを表します。|
|duration::rep Typedef|テンプレート パラメーター `Rep` のシノニムを表します。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[duration](#duration)|`duration` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[count](#count)|時間間隔内でのクロック ティック数を返します。|
|[max](#max)|静的。 テンプレート パラメーター `Ref` の最大許容値を返します。|
|[分](#min)|静的。 テンプレート パラメーター `Ref` の最小許容値を返します。|
|[zero](#zero)|静的。 実際には、`Rep`(0) を返します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[duration::operator-](#operator-)|無効にされたティック カウントと共に、`duration` オブジェクトのコピーを返します。|
|[duration::operator--](#operator--)|格納されたティック カウントをデクリメントします。|
|[duration::operator=](#op_eq)|格納されたティック カウントを指定された値だけ少なくします。|
|[duration::operator*=](#op_star_eq)|格納されたティック カウントを指定した値で乗算します。|
|[duration::operator/=](#op_div_eq)|格納されたティック カウントを、指定した `duration` オブジェクトのティック カウントで除算します。|
|[duration::operator+](#op_add)|`*this` を返します。|
|[duration::operator++](#op_add_add)|格納されたティック カウントをインクリメントします。|
|[duration::operator+=](#op_add_eq)|指定した `duration` オブジェクトのティック カウントを、格納されたティック カウントに加算します。|
|[duration::operator-=](#operator-_eq)|指定した `duration` オブジェクトのティック カウントを、格納されたティック カウントから減算します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<chrono >

**名前空間:** std::chrono

## <a name="count"></a>  duration::count

時間間隔内でのクロック ティック数を取得します。

```cpp
constexpr Rep count() const;
```

### <a name="return-value"></a>戻り値

時間間隔内でのクロック ティック数。

## <a name="duration"></a>  duration::duration コンストラクター

`duration` オブジェクトを構築します。

```cpp
constexpr duration() = default;

template <class Rep2>
constexpr explicit duration(const Rep2& R);

template <class Rep2, class Period2>
constexpr duration(const duration<Rep2, Period2>& Dur);
```

### <a name="parameters"></a>パラメーター

*Rep2*\
ティック数を表す演算型。

*Period2*\
秒単位でティック期間を表すための `std::ratio` テンプレートの特殊化。

*R*\
既定の期間のティック数。

*期間*\
*Period2*によって指定された期間のタイマー刻みの数。

### <a name="remarks"></a>Remarks

既定のコンストラクターは、初期化されていないオブジェクトを作成します。 空のかっこを使う値の初期化は、ゼロ クロック ティックの時間間隔を表すオブジェクトを初期化します。

2つ目のテンプレート引数コンストラクターは、既定の`std::ratio<1>`期間を使用して、 *R*クロックティックの時間間隔を表すオブジェクトを構築します。 ティックカウントが丸められないようにするには、が浮動小数点型として処理できない場合`duration::rep`に、浮動小数点型として扱うことができる表現型 Rep2 から duration オブジェクトを構築するとエラーになります。

3番目の2つのテンプレート引数コンストラクターは、長さが*期間*によって指定された時間間隔である時間間隔を表すオブジェクトを構築します。 ティック カウントが切り捨てられないようにするため、対象の型と*通約可能*な型を持つ duration オブジェクトから duration オブジェクトを作成するとエラーになります。

`D2` を浮動小数点型として処理できず、[ratio_divide\<D1::period, D2::period>::type::den](../standard-library/ratio.md) が 1 ではない場合、duration 型の `D1` は、別の duration 型の `D2` と*通約可能*になります。

*Rep2*が暗黙的に`rep`に変換可能であり、true `treat_as_floating_point<Rep2>`を*保持*して`treat_as_floating_point<rep>`いるか false を*保持*している場合を除き、2番目のコンストラクターはオーバーロードの解決に関与しません。 詳細については、「[<type_traits>](../standard-library/type-traits.md)」を参照してください。

変換でオーバーフローが発生して `treat_as_floating_point<rep>` が *true を保持*していない場合、または両方の `ratio_divide<Period2, period>::den` が 1 ではなく `treat_as_floating_point<Rep2>` が *false を保持*していない場合、3 番目のコンストラクターはオーバーロードの解決に関与しません。 詳しくは、「[<type_traits>](../standard-library/type-traits.md)」をご覧ください。

## <a name="max"></a>  duration::max

`Ref` テンプレート パラメーター型の値の上限の境界を返す静的メソッドです。

```cpp
static constexpr duration max();
```

### <a name="return-value"></a>戻り値

実際には、`duration(duration_values<rep>::max())` を返します。

## <a name="min"></a>  duration::min

`Ref` テンプレート パラメーター型の値の下限の境界を返す静的メソッドです。

```cpp
static constexpr duration min();
```

### <a name="return-value"></a>戻り値

実際には、`duration(duration_values<rep>::min())` を返します。

## <a name="operator-"></a>  duration::operator-

無効にされたティック カウントと共に、`duration` オブジェクトのコピーを返します。

```cpp
constexpr duration operator-() const;
```

## <a name="operator--"></a>  duration::operator--

格納されたティック カウントをデクリメントします。

```cpp
duration& operator--();

duration operator--(int);
```

### <a name="return-value"></a>戻り値

最初のメソッドは `*this` を返します。

2 番目のメソッドは、デクリメントの前に作成される `*this` のコピーを返します。

## <a name="op_eq"></a>  duration::operator=

格納されたティック カウントを指定された値だけ少なくします。

```cpp
duration& operator%=(const rep& Div);

duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>パラメーター

*Div*\
最初のメソッドでは、 *Div*はティックカウントを表します。 2番目のメソッドの*Div*は`duration` 、ティックカウントを含むオブジェクトです。

### <a name="return-value"></a>戻り値

モジュロ演算が実行された後の `duration` オブジェクト。

## <a name="op_star_eq"></a>  duration::operator*=

格納されたティック カウントを指定した値で乗算します。

```cpp
duration& operator*=(const rep& Mult);
```

### <a name="parameters"></a>パラメーター

*Mult*\
`duration::rep` によって指定される型の値。

### <a name="return-value"></a>戻り値

乗算が実行された後の `duration` オブジェクト。

## <a name="op_div_eq"></a>  duration::operator/=

指定された値で格納されているティック数を分割します。

```cpp
duration& operator/=(const rep& Div);
```

### <a name="parameters"></a>パラメーター

*Div*\
`duration::rep` によって指定される型の値。

### <a name="return-value"></a>戻り値

分割後の `duration` オブジェクト。

## <a name="op_add"></a>  duration::operator+

`*this` を返します。

```cpp
constexpr duration operator+() const;
```

## <a name="op_add_add"></a>  duration::operator++

格納されたティック カウントをインクリメントします。

```cpp
duration& operator++();

duration operator++(int);
```

### <a name="return-value"></a>戻り値

最初のメソッドは `*this` を返します。

2 番目のメソッドは、インクリメントの前に作成される `*this` のコピーを返します。

## <a name="op_add_eq"></a>  duration::operator+=

指定した `duration` オブジェクトのティック カウントを、格納されたティック カウントに加算します。

```cpp
duration& operator+=(const duration& Dur);
```

### <a name="parameters"></a>パラメーター

*期間*\
`duration` オブジェクト。

### <a name="return-value"></a>戻り値

加算が実行された後の `duration` オブジェクト。

## <a name="operator-_eq"></a>  duration::operator-=

指定した `duration` オブジェクトのティック カウントを、格納されたティック カウントから減算します。

```cpp
duration& operator-=(const duration& Dur);
```

### <a name="parameters"></a>パラメーター

*期間*\
`duration` オブジェクト。

### <a name="return-value"></a>戻り値

減算が実行された後の `duration` オブジェクト。

## <a name="zero"></a>  duration::zero

`duration(duration_values<rep>::zero())` を返します。

```cpp
static constexpr duration zero();
```

## <a name="op_mod_eq"></a>  duration::operator mod=

格納されたティック カウント剰余の Div または Div.count() を減算します。

```cpp
duration& operator%=(const rep& Div);duration& operator%=(const duration& Div);
```

### <a name="parameters"></a>パラメーター

*Div*\
除数。duration オブジェクトまたはティック カウントを表す値のいずれかです。

### <a name="remarks"></a>Remarks

最初のメンバー関数では、格納されたティック カウント剰余の Div を減算し、*this を返します。 最初のメンバー関数では、格納されたティック カウント剰余の Div.count() を減算し、\*this を返します。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)\
[duration_values 構造体](../standard-library/duration-values-structure.md)
