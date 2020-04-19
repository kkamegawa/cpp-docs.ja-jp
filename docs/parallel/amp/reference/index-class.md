---
title: index クラス
ms.date: 03/27/2019
f1_keywords:
- AMP/index
- AMP/Concurrency::index::index
- AMP/Concurrency::index::rank
helpviewer_keywords:
- index structure
ms.assetid: cbe79b08-0ba7-474c-9828-f1a71da39eb3
ms.openlocfilehash: 06a5fa9a2d7e645c46b90ace957d31251baed81c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127804"
---
# <a name="index-class"></a>index クラス

*N*次元のインデックスベクターを定義します。

## <a name="syntax"></a>構文

```cpp
template <int _Rank>
class index;
```

### <a name="parameters"></a>パラメーター

*_Rank*<br/>
ランク (次元数)。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[インデックスコンストラクター](#index_ctor)|`index` クラスの新しいインスタンスを初期化します。|

### <a name="public-operators"></a>パブリック演算子

|Name|説明|
|----------|-----------------|
|[operator--](#operator--)|`index` オブジェクトの各要素をデクリメントします。|
|[operator%=](#operator_mod_eq)|その要素がある数で除算された場合、`index` オブジェクトの各要素の剰余を計算します。|
|[operator*=](#operator_star_eq)|`index` オブジェクトの各要素をある数で乗算します。|
|[operator/=](#operator_div_eq)|`index` オブジェクトの各要素をある数で除算します。|
|[index:: operator\[\]](#operator_at)|指定したインデックス位置にある要素を返します。|
|[operator++](#operator_add_add)|`index` オブジェクトの各要素をインクリメントします。|
|[operator+=](#operator_add_eq)|指定した数を `index` オブジェクトの各要素に加算します。|
|[operator=](#operator_eq)|指定された `index` オブジェクトの内容をこのオブジェクトにコピーします。|
|[operator-=](#operator_-_eq)|指定した数を `index` オブジェクトの各要素から減算します。|

### <a name="public-constants"></a>パブリック定数

|Name|説明|
|----------|-----------------|
|[rank 定数](#rank)|`index` オブジェクトのランクを格納します。|

## <a name="inheritance-hierarchy"></a>継承階層

`index`

## <a name="remarks"></a>解説

`index` 構造体は、 *n*次元空間内の一意の位置を指定する*n 個*の整数の座標ベクトルを表します。 ベクターの値は最上位から最下位へ順に並べ替えられます。 [Operator =](#operator_eq)を使用して、コンポーネントの値を取得できます。

## <a name="requirements"></a>［要件］

**ヘッダー:** amp.h

**名前空間:** Concurrency

## <a name="index_ctor"></a>インデックスコンストラクター

index クラスの新しいインスタンスを初期化します。

```cpp
index() restrict(amp,cpu);

index(
   const index<_Rank>& _Other
) restrict(amp,cpu);

explicit index(
   int _I
) restrict(amp,cpu);

index(
   int _I0,
   int _I1
) restrict(amp,cpu);

index(
   int _I0,
   int _I1,
   int _I2
) restrict(amp,cpu);

explicit index(
   const int _Array[_Rank]
) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Array*<br/>
ランク値を持つ 1 次元配列。

*_I*<br/>
1 次元インデックスのインデックス位置。

*_I0*<br/>
最上位の次元の長さ。

*_I1*<br/>
最上位の次の次元の長さ。

*_I2*<br/>
最下位の次元の長さ。

*_Other*<br/>
新しいインデックスオブジェクトの基になる index オブジェクト。

## <a name="operator--"></a>operator--

index オブジェクトの各要素をデクリメントします。

```cpp
index<_Rank>& operator--() restrict(amp,cpu);

index operator--(
   int
) restrict(amp,cpu);
```

### <a name="return-values"></a>戻り値

前置演算子の場合は、index オブジェクト (* this) です。 サフィックス演算子の場合は、新しいインデックスオブジェクト。

## <a name="operator_mod_eq"></a>% = 演算子

要素が指定した数値で除算されたときに、インデックスオブジェクト内の各要素の剰余 (剰余) を計算します。

```cpp
index<_Rank>& operator%=(
   int _Rhs
) restrict(cpu, amp);
```

### <a name="parameters"></a>パラメーター

*_Rhs*<br/>
剰余を求めるために除算する数値。

## <a name="return-value"></a>戻り値

インデックスオブジェクトです。

## <a name="operator_star_eq"></a>operator * =

index オブジェクトの各要素を指定した数で乗算します。

```cpp
index<_Rank>& operator*=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Rhs*<br/>
乗算対象の数です。

## <a name="operator_div_eq"></a>operator/=

指定された数で index オブジェクトの各要素を除算します。

```cpp
index<_Rank>& operator/=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Rhs*<br/>
除数。

## <a name="operator_at"></a>  演算子\[\]

指定した位置にあるインデックスのコンポーネントを返します。

```cpp
int operator[] (
   unsigned _Index
) const restrict(amp,cpu);

int& operator[] (
   unsigned _Index
) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Index*<br/>
0 からランク - 1 までの整数。

### <a name="return-value"></a>戻り値

指定したインデックス位置にある要素。

### <a name="remarks"></a>解説

次の例では、インデックスのコンポーネント値を表示します。

```cpp
// Prints 1 2 3.
concurrency::index<3> idx(1, 2, 3);
std::cout << idx[0] << "\n";
std::cout << idx[1] << "\n";
std::cout << idx[2] << "\n";
```

## <a name="operator_add_add"></a>+ + 演算子

index オブジェクトの各要素をインクリメントします。

```cpp
index<_Rank>& operator++() restrict(amp,cpu);

index<_Rank> operator++(
   int
) restrict(amp,cpu);
```

### <a name="return-value"></a>戻り値

前置演算子の場合は、index オブジェクト (* this) です。 サフィックス演算子の場合は、新しいインデックスオブジェクト。

## <a name="operator_add_eq"></a>演算子 + =

指定した数を index オブジェクトの各要素に加算します。

```cpp
index<_Rank>& operator+=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator+=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Rhs*<br/>
加算する数。

### <a name="return-value"></a>戻り値

インデックスオブジェクトです。

## <a name="operator_eq"></a>  operator=

指定された index オブジェクトの内容をこのオブジェクトにコピーします。

```cpp
index<_Rank>& operator=(
   const index<_Rank>& _Other
) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Other*<br/>
コピー元のインデックスオブジェクト。

### <a name="return-value"></a>戻り値

このインデックスオブジェクトへの参照。

## <a name="operator_-_eq"></a>operator-=

指定した数を index オブジェクトの各要素から減算します。

```cpp
index<_Rank>& operator-=(
   const index<_Rank>& _Rhs
) restrict(amp,cpu);

index<_Rank>& operator-=(
   int _Rhs
) restrict(amp,cpu);
```

### <a name="parameters"></a>パラメーター

*_Rhs*<br/>
減算する数。

### <a name="return-value"></a>戻り値

インデックスオブジェクトです。

## <a name="rank"></a>ランク

インデックスオブジェクトのランクを取得します。

```cpp
static const int rank = _Rank;
```

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
