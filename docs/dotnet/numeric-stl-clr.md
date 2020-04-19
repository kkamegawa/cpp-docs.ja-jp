---
title: 数値 (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/numeric>
- cliext::accumulate
- cliext::adjacent_difference
- cliext::inner_product
- cliext::partial_sum
helpviewer_keywords:
- numeric functions [STL/CLR]
- <cliext/numeric> header [STL/CLR]
- <numeric> header [STL/CLR]
- accumulate function [STL/CLR]
- adjacent_difference function [STL/CLR]
- inner_product function [STL/CLR]
- partial_sum function [STL/CLR]
ms.assetid: 1dc4d9a3-e734-459c-9678-5d9be0ef4c79
ms.openlocfilehash: 0311b36ec1190631e053eeade443939703e69103
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384804"
---
# <a name="numeric-stlclr"></a>数値 (STL/CLR)

数値処理のために用意されているアルゴリズムを実行するコンテナーのテンプレート関数を定義します。

## <a name="syntax"></a>構文

```
#include <cliext/numeric>
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<cliext/数値 >

**Namespace:** cliext

## <a name="declarations"></a>宣言

|関数|説明|
|--------------|-----------------|
|[accumulate (STL/CLR)](#accumulate)|連続する部分和を計算することで、いくつかの初期値を含め、指定された範囲のすべての要素の合計を計算します。または、指定された二項演算を使用して取得した、合計以外の連続する部分的な結果を計算します。|
|[adjacent_difference (STL/CLR)](#adjacent_difference)|入力範囲内の各要素とその先行要素との連続する差分を計算し、結果をターゲット範囲に出力するか、または差分演算が指定された別の二項演算に置き換えられた汎用化されたプロシージャの結果を計算します。|
|[inner_product (STL/CLR)](#inner_product)|2 つの範囲の要素ごとの積の合計を計算し、それを指定された初期値に加算するか、または和や積の二項演算が指定された別の二項演算に置き換えられた汎用化されたプロシージャの結果を計算します。|
|[partial_sum (STL/CLR)](#partial_sum)|一連の合計が、最初の要素からの入力の範囲の計算、`i`番目の要素でこのような各合計の結果を格納および`i`番目の要素をターゲット範囲のまたは汎用化されたプロシージャの結果を計算します、合計演算指定した別の二項演算に置き換えられます。|

## <a name="members"></a>メンバー

## <a name="accumulate"></a> 累積 (STL/CLR)

連続する部分和を計算することで、いくつかの初期値を含め、指定された範囲のすべての要素の合計を計算します。または、指定された二項演算を使用して取得した、合計以外の連続する部分的な結果を計算します。

### <a name="syntax"></a>構文

```cpp
template<class _InIt, class _Ty> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val);
template<class _InIt, class _Ty, class _Fn2> inline
    _Ty accumulate(_InIt _First, _InIt _Last, _Ty _Val, _Fn2 _Func);
```

### <a name="remarks"></a>Remarks

この関数が C++ 標準ライブラリ数値関数と同様に動作`accumulate`します。 詳細については、次を参照してください。[蓄積](../standard-library/numeric-functions.md#accumulate)します。

## <a name="adjacent_difference"></a> adjacent_difference (STL/CLR)

入力範囲内の各要素とその先行要素との連続する差分を計算し、結果をターゲット範囲に出力するか、または差分演算が指定された別の二項演算に置き換えられた汎用化されたプロシージャの結果を計算します。

### <a name="syntax"></a>構文

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt adjacent_difference(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Remarks

この関数が C++ 標準ライブラリ数値関数と同様に動作`adjacent_difference`します。 詳細については、次を参照してください。 [adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)します。

## <a name="inner_product"></a> inner_product (STL/CLR)

2 つの範囲の要素ごとの積の合計を計算し、それを指定された初期値に加算するか、または和や積の二項演算が指定された別の二項演算に置き換えられた汎用化されたプロシージャの結果を計算します。

### <a name="syntax"></a>構文

```cpp
template<class _InIt1, class _InIt2, class _Ty> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val);
template<class _InIt1, class _InIt2, class _Ty, class _Fn21,
       class _Fn22> inline
    _Ty inner_product(_InIt1 _First1, _InIt1 _Last1, _InIt2 _First2,
        _Ty _Val, _Fn21 _Func1, _Fn22 _Func2);
```

### <a name="remarks"></a>Remarks

この関数が C++ 標準ライブラリ数値関数と同様に動作`inner_product`します。 詳細については、次を参照してください。 [inner_product](../standard-library/numeric-functions.md#inner_product)します。

## <a name="partial_sum"></a> partial_sum (STL/CLR)

一連の合計が、最初の要素からの入力の範囲の計算、`i`番目の要素でこのような各合計の結果を格納および`i`番目の要素をターゲット範囲のまたは汎用化されたプロシージャの結果を計算します、合計演算指定した別の二項演算に置き換えられます。

### <a name="syntax"></a>構文

```cpp
template<class _InIt, class _OutIt> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last, _OutIt _Dest);
template<class _InIt, class _OutIt, class _Fn2> inline
    _OutIt partial_sum(_InIt _First, _InIt _Last,
        _OutIt _Dest, _Fn2 _Func);
```

### <a name="remarks"></a>Remarks

この関数が C++ 標準ライブラリ数値関数と同様に動作`partial_sum`します。 詳細については、次を参照してください。 [partial_sum](../standard-library/numeric-functions.md#partial_sum)します。