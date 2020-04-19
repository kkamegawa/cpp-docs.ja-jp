---
title: SafeInt 関数
ms.date: 10/22/2018
ms.topic: reference
f1_keywords:
- SafeInt functions
- SafeAdd
- SafeCast
- SafeDivide
- SafeEquals
- SafeGreaterThan
- SafeGreaterThanEquals
- SafeLessThan
- SafeLessThanEquals
- SafeModulus
- SafeMultiply
- SafeNotEquals
- SafeSubtract
helpviewer_keywords:
- functions, SafeInt
- SafeAdd function
- SafeCast function
- SafeDivide function
- SafeEquals function
- SafeGreaterThan function
- SafeGreaterThanEquals function
- SafeLessThan function
- SafeLessThanEquals function
- SafeModulus function
- SafeMultiply function
- SafeNotEquals function
- SafeSubtract function
ms.assetid: fdc208e5-5d8a-41a9-8271-567fd438958d
ms.openlocfilehash: e31cf35c903a0e7572ce7d47ada21c4603119cb2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515577"
---
# <a name="safeint-functions"></a>SafeInt 関数

SafeInt ライブラリには、[SafeInt クラス](../safeint/safeint-class.md)のインスタンスを作成せずに使える関数がいくつか用意されています。 1 つの数値演算を整数のオーバーフローから保護したい場合、これらの関数を使えます。 複数の数値演算を保護したい場合は、`SafeInt` オブジェクトを作成する必要があります。 これらの関数を複数回使うよりも、`SafeInt` オブジェクトを作成する方が効率的です。

これらの関数を使うと、2 つの異なる型のパラメーターを比較したり、それらで数値演算を実行したりできます。最初に同じ型に変換する必要はありません。

これらの各関数は、2 つのテンプレート型 `T` と `U` を持っています。 これらの型にはそれぞれ、ブール値、文字、または整数型を指定できます。 整数型は、符号付きまたは符号なしで、8 ビットから 64 ビットの任意のサイズにすることができます。

> [!NOTE]
> このライブラリの最新バージョンは [https://github.com/dcleblanc/SafeInt](https://github.com/dcleblanc/SafeInt) にあります。

## <a name="in-this-section"></a>このセクションの内容

関数                      | 説明
----------------------------- | --------------------------------------------------------------
[SafeAdd](#safeadd)           | 2 つの数値を加算し、オーバーフローから保護します。
[SafeCast](#safecast)         | ある型のパラメーターを別の型にキャストします。
[SafeDivide](#safedivide)     | 2 つの数値を除算し、ゼロ除算から保護します。
[SafeEquals](#safeequals)、[SafeGreaterThan](#safegreaterthan)、[SafeGreaterThanEquals](#safegreaterthanequals)、[SafeLessThan](#safelessthan)、[SafeLessThanEquals](#safelessthanequals)、[SafeNotEquals](#safenotequals) | 2 つの数値を比較します。 これらの関数を使うと、異なる型の 2 つの数値を、その型を変更することなく比較できます。
[SafeModulus](#safemodulus)   | 2 つの数値に対して剰余演算を実行します。
[SafeMultiply](#safemultiply) | 2 つの数値を乗算し、オーバーフローから保護します。
[SafeSubtract](#safesubtract) | 2 つの数値を減算し、オーバーフローから保護します。

## <a name="related-sections"></a>関連項目

セクション                                                  | 説明
-------------------------------------------------------- | ----------------------------------------------------
[SafeInt](../safeint/safeint-class.md)                   | `SafeInt` クラス
[SafeIntException](../safeint/safeintexception-class.md) | SafeInt ライブラリに固有の例外クラスです。

## <a name="safeadd"></a>SafeAdd

オーバーフローから保護される方法で 2 つの数値を加算します。

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 加算する最初の数値。 これは T 型である必要があります。

*u*<br/>
[入力] 加算する 2 番目の数値。 これは U 型である必要があります。

*result*<br/>
[出力] `SafeAdd` の結果が格納されるパラメーター。

### <a name="return-value"></a>戻り値

エラーが発生しなかった場合は **true**。エラーが発生した場合は **false**。

## <a name="safecast"></a>SafeCast

ある型の数値を別の型にキャストします。

```cpp
template<typename T, typename U>
inline bool SafeCast (
   const T From,
   U& To
);
```

### <a name="parameters"></a>パラメーター

*From*<br/>
[入力] 変換元の数値。 これは `T` 型である必要があります。

*目的*<br/>
[出力] 新しい数値型への参照。 これは `U` 型である必要があります。

### <a name="return-value"></a>戻り値

エラーが発生しなかった場合は **true**。エラーが発生した場合は **false**。

## <a name="safedivide"></a>SafeDivide

ゼロ除算から保護される方法で 2 つの数値を除算します。

```cpp
template<typename T, typename U>
inline bool SafeDivide (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 除数。 これは T 型である必要があります。

*u*<br/>
[入力] 被除数。 これは U 型である必要があります。

*result*<br/>
[出力] `SafeDivide` の結果が格納されるパラメーター。

### <a name="return-value"></a>戻り値

エラーが発生しなかった場合は **true**。エラーが発生した場合は **false**。

## <a name="safeequals"></a>SafeEquals

2 つの数値を比較し、それらが等しいかどうかを判定します。

```cpp
template<typename T, typename U>
inline bool SafeEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 比較する最初の数値。 これは T 型である必要があります。

*u*<br/>
[入力] 比較する 2 番目の数値。 これは U 型である必要があります。

### <a name="return-value"></a>戻り値

*t* と *u* が等しい場合は **true**。それ以外の場合は **false**。

### <a name="remarks"></a>解説

このメソッドでは `==` が強化されます。`SafeEquals` を使うと、2 つの異なる型の数値を比較できるためです。

## <a name="safegreaterthan"></a>SafeGreaterThan

2 つの数値を比較します。

```cpp
template<typename T, typename U>
inline bool SafeGreaterThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 比較する最初の数値。 これは `T` 型である必要があります。

*u*<br/>
[入力] 比較する 2 番目の数値。 これは `U` 型である必要があります。

### <a name="return-value"></a>戻り値

*t* が *u* よりも大きい場合は **true**。それ以外の場合は **false**。

### <a name="remarks"></a>解説

`SafeGreaterThan` では通常の比較演算子が拡張され、2 つの異なる型の数値を比較できます。

## <a name="safegreaterthanequals"></a>SafeGreaterThanEquals

2 つの数値を比較します。

```cpp
template <typename T, typename U>
inline bool SafeGreaterThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 比較する最初の数値。 これは `T` 型である必要があります。

*u*<br/>
[入力] 比較する 2 番目の数値。 これは `U` 型である必要があります。

### <a name="return-value"></a>戻り値

*t* が *u* よりも大きいか等しい場合は **true**。それ以外の場合は **false**。

### <a name="remarks"></a>解説

`SafeGreaterThanEquals` では標準の比較演算子が強化され、2 つの異なる型の数値を比較できます。

## <a name="safelessthan"></a>SafeLessThan

一方の数値がもう一方の数値よりも小さいかどうかを判定します。

```cpp
template<typename T, typename U>
inline bool SafeLessThan (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 最初の数値。 これは `T` 型である必要があります。

*u*<br/>
[入力] 2 番目の数値。 これは `U` 型である必要があります。

### <a name="return-value"></a>戻り値

*t* が *u* よりも小さい場合は **true**。それ以外の場合は **false**。

### <a name="remarks"></a>解説

このメソッドでは標準の比較演算子が強化されます。`SafeLessThan` を使うと、2 つの異なる型の数値を比較できるためです。

## <a name="safelessthanequals"></a>SafeLessThanEquals

2 つの数値を比較します。

```cpp
template <typename T, typename U>
inline bool SafeLessThanEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 比較する最初の数値。 これは `T` 型である必要があります。

*u*<br/>
[入力] 比較する 2 番目の数値。 これは `U` 型である必要があります。

### <a name="return-value"></a>戻り値

*t* が *u* よりも小さいか等しい場合は **true**。それ以外の場合は **false**。

### <a name="remarks"></a>解説

`SafeLessThanEquals` では通常の比較演算子が拡張され、2 つの異なる型の数値を比較できます。

## <a name="safemodulus"></a>SafeModulus

2 つの数値に対して剰余演算を実行します。

```cpp
template<typename T, typename U>
inline bool SafeModulus (
   const T t,
   const U u,
   T& result
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 除数。 これは `T` 型である必要があります。

*u*<br/>
[入力] 被除数。 これは `U` 型である必要があります。

*result*<br/>
[出力] `SafeModulus` の結果が格納されるパラメーター。

### <a name="return-value"></a>戻り値

エラーが発生しなかった場合は **true**。エラーが発生した場合は **false**。

## <a name="safemultiply"></a>SafeMultiply

オーバーフローから保護される方法で 2 つの数値を乗算します。

```cpp
template<typename T, typename U>
inline bool SafeMultiply (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 乗算する最初の数値。 これは `T` 型である必要があります。

*u*<br/>
[入力] 乗算する 2 番目の数値。 これは `U` 型である必要があります。

*result*<br/>
[出力] `SafeMultiply` の結果が格納されるパラメーター。

### <a name="return-value"></a>戻り値

エラーが発生しなかった場合は `true`。エラーが発生した場合は `false`。

## <a name="safenotequals"></a>SafeNotEquals

2 つの数値が等しくないかどうかを判定します。

```cpp
template<typename T, typename U>
inline bool SafeNotEquals (
   const T t,
   const U u
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 比較する最初の数値。 これは `T` 型である必要があります。

*u*<br/>
[入力] 比較する 2 番目の数値。 これは `U` 型である必要があります。

### <a name="return-value"></a>戻り値

*t* と *u* が等しくない場合は **true**。それ以外の場合は **false**。

### <a name="remarks"></a>解説

このメソッドでは `!=` が強化されます。`SafeNotEquals` を使うと、2 つの異なる型の数値を比較できるためです。

## <a name="safesubtract"></a>SafeSubtract

オーバーフローから保護される方法で 2 つの数値を減算します。

```cpp
template<typename T, typename U>
inline bool SafeSubtract (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>パラメーター

*t*<br/>
[入力] 減算の最初の数値。 これは `T` 型である必要があります。

*u*<br/>
[入力] *t* から減算する数値。 これは `U` 型である必要があります。

*result*<br/>
[出力] `SafeSubtract` の結果が格納されるパラメーター。

### <a name="return-value"></a>戻り値

エラーが発生しなかった場合は **true**。エラーが発生した場合は **false**。
