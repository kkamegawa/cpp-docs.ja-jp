---
title: atomic 構造体
ms.date: 04/20/2018
f1_keywords:
- atomic/std::atomic
ms.assetid: 261628ed-7049-41ac-99b9-cfe49f696b44
ms.openlocfilehash: 1b3b60d71fcdf68fdf215820535c3bfb3d4dfb2b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456730"
---
# <a name="atomic-structure"></a>atomic 構造体

*Ty*型の格納された値に対してアトミック操作を実行するオブジェクトを記述します。

## <a name="syntax"></a>構文

```cpp
template <class Ty>
struct atomic;
```

## <a name="members"></a>メンバー

|メンバー|説明|
|----------|-----------------|
|**コンストラクター**||
|[atomic](#atomic)|アトミック オブジェクトを構築します。|
|**演算子**||
|[atomic:: operator Ty](#op_ty)|格納されている値を読み取って返します。 ([atomic:: load](#load))|
|[atomic::operator=](#op_eq)|格納されている値を置き換えるために指定された値を使用します。 ([atomic:: store](#store))|
|[atomic::operator++](#op_inc)|格納されている値をインクリメントします。 整数およびポインターの特殊化でのみ使用されます。|
|[atomic::operator+=](#op_add_eq)|指定した値を格納されている値に加算します。 整数およびポインターの特殊化でのみ使用されます。|
|[atomic::operator--](#op_dec)|格納されている値をデクリメントします。 整数およびポインターの特殊化でのみ使用されます。|
|[atomic::operator-=](#op_sub_eq)|指定した値を格納されている値から減算します。 整数およびポインターの特殊化でのみ使用されます。|
|[atomic::operator&=](#op_and_eq)|指定した値と格納されている値に対してビットごとの and を実行します。 整数の特殊化でのみ使用されます。|
|[atomic:: operator&#124;=](#op_or_eq)|指定した値と格納されている値に対してビットごとの or を実行します。 整数の特殊化でのみ使用されます。|
|[atomic::operator^=](#op_xor_eq)|指定した値と格納されている値に対してビットごとの排他的 or を実行します。 整数の特殊化でのみ使用されます。|
|**関数**||
|[compare_exchange_strong](#compare_exchange_strong)|**this**に対して*atomic_compare_and_exchange*操作を実行し、結果を返します。|
|[compare_exchange_weak](#compare_exchange_weak)|**this**に対して*weak_atomic_compare_and_exchange*操作を実行し、結果を返します。|
|[fetch_add](#fetch_add)|指定した値を格納されている値に加算します。|
|[fetch_and](#fetch_and)|指定した値と格納されている値に対してビットごとの and を実行します。|
|[fetch_or](#fetch_or)|指定した値と格納されている値に対してビットごとの or を実行します。|
|[fetch_sub](#fetch_sub)|指定した値を格納されている値から減算します。|
|[fetch_xor](#fetch_xor)|指定した値と格納されている値に対してビットごとの排他的 or を実行します。|
|[is_lock_free](#is_lock_free)|**this**に対するアトミック操作が*ロックを解放*するかどうかを指定します。 その型に対する分割不可能な操作においてロックが使用される場合、atomic 型は*ロック制御不要*になります。|
|[給紙](#load)|格納されている値を読み取って返します。|
|[store](#store)|格納されている値を置き換えるために指定された値を使用します。|

## <a name="remarks"></a>Remarks

型*Ty*は、*普通にコピー可能*である必要があります。 つまり、 [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)を使用してそのバイトをコピーするには、元のオブジェクトと等しい有効な*Ty*オブジェクトを生成する必要があります。 [Compare_exchange_weak](#compare_exchange_weak)および[compare_exchange_strong](#compare_exchange_strong)メンバー関数は、 [memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)を使用して2つの*Ty*値が等しいかどうかを判断します。 これらの関数は、 *Ty*定義`operator==`を使用しません。 の`atomic`メンバー関数は、 `memcpy` *Ty*型の値をコピーするために使用します。

部分的 **\<特殊化\*は、すべてのポインター型に存在します。 >** 特殊化により、マネージド ポインター値のオフセットの加算またはマネージド ポインター値からのオフセットの減算が可能になります。 算術演算は型`ptrdiff_t`の引数を受け取り、通常のアドレス演算との一貫性を確保するために、 *Ty*のサイズに従ってその引数を調整します。

**Bool**を除くすべての整数型に特殊化が存在します。 それぞれの特殊化には、分割不可能な算術演算および論理演算のための豊富な一連のメソッドが用意されています。

||||
|-|-|-|
|**atomic\<char >**|**アトミック\<署名された char >**|**atomic\<unsigned char >**|
|**atomic\<char16_t >**|**atomic\<char32_t >**|**アトミック\<wchar_t >**|
|**atomic\<short >**|**atomic\<unsigned short >**|**atomic\<int >**|
|**atomic\<unsigned int >**|**atomic\<long >**|**atomic\<unsigned long >**|
|**アトミック\<長 long >**|**atomic\<unsigned long long>**|

整数の特殊化は、対応する `atomic_integral` 型から派生します。 たとえば、 **atomic\<unsigned int >** はから`atomic_uint`派生します。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<アトミック >

**名前空間:** std

## <a name="atomic"></a>atomic:: atomic

アトミック オブジェクトを構築します。

```cpp
atomic();
atomic( const atomic& );
atomic( Ty Value ) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
初期化値。

### <a name="remarks"></a>Remarks

アトミック オブジェクトをコピーまたは移動することはできません。

アトミック\<*Ty*> のインスタンス化であるオブジェクトは、集約初期化を使用するのではなく、型*Ty*の引数を受け取るコンストラクターによってのみ初期化できます。 ただし、atomic_integral オブジェクトを初期化できるのは、集計の初期化を使用する場合だけです。

```cpp
atomic<int> ai0 = ATOMIC_VAR_INIT(0);
atomic<int> ai1(0);
```

## <a name="op_ty"></a>atomic:: operator *Ty*

テンプレートに対して指定された型の演算子\<、atomic*Ty*>。 **\*this**に格納されている値を取得します。

```cpp
atomic<Ty>::operator Ty() const volatile noexcept;
atomic<Ty>::operator Ty() const noexcept;
```

### <a name="remarks"></a>Remarks

この演算子は、 `memory_order_seq_cst` [memory_order](atomic-enums.md)を適用します。

## <a name="op_eq"></a>atomic:: operator =

指定された値を格納します。

```cpp
Ty operator=(
   Ty Value
) volatile noexcept;
Ty operator=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*オブジェクト。

### <a name="return-value"></a>戻り値

*値*を返します。

## <a name="op_inc"></a>atomic:: operator + +

格納されている値をインクリメントします。 整数およびポインターの特殊化でのみ使用されます。

```cpp
Ty atomic<Ty>::operator++(int) volatile noexcept;
Ty atomic<Ty>::operator++(int) noexcept;
Ty atomic<Ty>::operator++() volatile noexcept;
Ty atomic<Ty>::operator++() noexcept;
```

### <a name="return-value"></a>戻り値

最初の2つの演算子は、インクリメントされた値を返します。最後の2つの演算子は、インクリメントの前に値を返します。 演算子は[memory_order](atomic-enums.md)を`memory_order_seq_cst`使用します。

## <a name="op_add_eq"></a>atomic:: operator + =

指定した値を格納されている値に加算します。 整数およびポインターの特殊化でのみ使用されます。

```cpp
Ty atomic<Ty>::operator+=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator+=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
整数またはポインターの値。

### <a name="return-value"></a>戻り値

加算の結果を格納する*Ty*オブジェクト。

### <a name="remarks"></a>Remarks

この演算子は、 `memory_order_seq_cst` [memory_order](atomic-enums.md)を使用します。

## <a name="op_dec"></a>atomic:: operator--

格納されている値をデクリメントします。 整数およびポインターの特殊化でのみ使用されます。

```cpp
Ty atomic<Ty>::operator--(int) volatile noexcept;
Ty atomic<Ty>::operator--(int) noexcept;
Ty atomic<Ty>::operator--() volatile noexcept;
Ty atomic<Ty>::operator--() noexcept;
```

### <a name="return-value"></a>戻り値

最初の2つの演算子は、デクリメントされた値を返します。最後の2つの演算子は、デクリメントの前に値を返します。 演算子は[memory_order](atomic-enums.md)を`memory_order_seq_cst`使用します。

## <a name="op_sub_eq"></a>atomic:: operator-=

指定した値を格納されている値から減算します。 整数およびポインターの特殊化でのみ使用されます。

```cpp
Ty atomic<Ty>::operator-=(
   Ty Value
) volatile noexcept;
Ty atomic<Ty>::operator-=(
   Ty Value
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
整数またはポインターの値。

### <a name="return-value"></a>戻り値

減算の結果を格納している*Ty*オブジェクト。

### <a name="remarks"></a>Remarks

この演算子は、 `memory_order_seq_cst` [memory_order](atomic-enums.md)を使用します。

## <a name="op_and_eq"></a>atomic:: operator & =

指定した値と、 **\*this**の格納された値に対してビットごとの and を実行します。 整数の特殊化でのみ使用されます。

```cpp
atomic<Ty>::operator&= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator&= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*型の値。

### <a name="return-value"></a>戻り値

ビットごとの and の結果。

### <a name="remarks"></a>Remarks

この演算子は、読み取り/書き込み操作を実行し、  **\*this**の格納された値を、*値*のビットごとの and と、 **\*this**に格納されている現在の値に置き換えます`memory_order_seq_cst`。 [memory_order](atomic-enums.md)。

## <a name="op_or_eq"></a>atomic:: operator&#124;=

指定した値と、 **\*this**の格納された値に対してビットごとの or を実行します。 整数の特殊化でのみ使用されます。

```cpp
atomic<Ty>::operator|= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator|= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*型の値。

### <a name="return-value"></a>戻り値

ビットごとの or の結果。

### <a name="remarks"></a>Remarks

この演算子は、読み取り/書き込み操作を実行して、  **\***  **\*** `memory_order_seq_cst`このの格納されている値を、次の制約内で、値のビットごとのor値と、このに格納されている現在の値に置き換えます。 [memory_order](atomic-enums.md)の制約。

## <a name="op_xor_eq"></a>atomic:: operator ^ =

指定した値と、 **\*this**の格納された値に対してビットごとの排他的 or を実行します。 整数の特殊化でのみ使用されます。

```cpp
atomic<Ty>::operator^= (
   Ty Value
) volatile noexcept;
atomic<Ty>::operator^= (
   Ty Value
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*型の値。

### <a name="return-value"></a>戻り値

ビットごとの排他的 or の結果。

### <a name="remarks"></a>Remarks

この演算子は、読み取り/書き込み操作を実行して、 **\*this** **\*に格納**されている値をビットごとの排他的 or*値*に置き換えます。また、[memory_order](atomic-enums.md) の制約。`memory_order_seq_cst`

## <a name="compare_exchange_strong"></a>atomic:: compare_exchange_strong

**\*this**に対してアトミックの比較および交換操作を実行します。

```cpp
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_strong(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>パラメーター

*期限*\
*Ty*型の値。

*数値*\
*Ty*型の値。

*Order1*\
1 `memory_order`番目の引数。

*Order2*\
2 番目の `memory_order` 引数。

### <a name="return-value"></a>戻り値

値の比較の結果を示す**ブール**値。

### <a name="remarks"></a>Remarks

このアトミックの比較および交換操作では、 **\*this**に格納されている値と*Exp*を比較します。値が等しい場合、操作は、 **\*this**に格納されている値を、読み取り/書き込み操作を使用し、 *Order1*で指定されたメモリ順序制約を適用して、*値*に置き換えます。 値が等しくない場合、この操作は、 **\*this**に格納されている値を使用して*Exp*を置き換え、 *Order2*で指定されているメモリ順序制約を適用します。

2番目`memory_order`のを持たないオーバーロードでは、 *Order1*の値に基づく暗黙的な*Order2*が使用されます。 *Order1* `memory_order_acq_rel`がの場合、 *Order2*は`memory_order_acquire`です。 *Order1* `memory_order_release`がの場合、 *Order2*は`memory_order_relaxed`です。 それ以外の場合は、 *Order2*は*Order1*と等しくなります。

2 `memory_order`つのパラメーターを受け取るオーバーロードで`memory_order_release`は、 *Order2*の値をまた`memory_order_acq_rel`はにすることはできません。また、 *Order1*の値よりも強い値を指定することはできません。

## <a name="compare_exchange_weak"></a>atomic:: compare_exchange_weak

**\*this**に対して弱いアトミック比較と交換操作を実行します。

```cpp
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1,
   memory_order Order2
) noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) volatile noexcept;
bool compare_exchange_weak(
   Ty& Exp,
   Ty Value,
   memory_order Order1 = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>パラメーター

*期限*\
*Ty*型の値。

*数値*\
*Ty*型の値。

*Order1*\
1 `memory_order`番目の引数。

*Order2*\
2 番目の `memory_order` 引数。

### <a name="return-value"></a>戻り値

値の比較の結果を示す**ブール**値。

### <a name="remarks"></a>Remarks

このアトミックの比較および交換操作では、 **\*this**に格納されている値と*Exp*を比較します。値が等しい場合、操作は、 **\*this**に格納されている値を、読み取り/書き込み操作を使用し、 *Order1*で指定されたメモリ順序制約を適用して、*値*に置き換えます。 値が等しくない場合、この操作は、 **\*this**に格納されている値を使用して*Exp*を置き換え、 *Order2*で指定されているメモリ順序制約を適用します。

比較対象の値が等しい場合、弱いアトミックの比較および交換操作によって exchange が実行されます。 値が同じでない場合、操作による交換の実行は保証されません。

2番目`memory_order`のを持たないオーバーロードでは、 *Order1*の値に基づく暗黙的な*Order2*が使用されます。 *Order1* `memory_order_acq_rel`がの場合、 *Order2*は`memory_order_acquire`です。 *Order1* `memory_order_release`がの場合、 *Order2*は`memory_order_relaxed`です。 それ以外の場合は、 *Order2*は*Order1*と等しくなります。

2 `memory_order`つのパラメーターを受け取るオーバーロードで`memory_order_release`は、 *Order2*の値をまた`memory_order_acq_rel`はにすることはできません。また、 *Order1*の値よりも強い値を指定することはできません。

## <a name="exchange"></a>atomic:: exchange

指定した値を使用して、 **\*this**の格納されている値を置き換えます。

```cpp
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::exchange(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*型の値。

*順序*\
`memory_order`。

### <a name="return-value"></a>戻り値

Exchange の前に格納されていた **\*this**の値。

### <a name="remarks"></a>Remarks

この操作では、*値*を使用して、 *Order*によって指定されたメモリ制約内で、 **\*this**に格納されている値を置き換える読み取り/書き込み操作を実行します。

## <a name="fetch_add"></a>atomic:: fetch_add

**\*this**に格納されている値をフェッチし、格納されている値に指定した値を加算します。

```cpp
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_add (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*型の値。

*順序*\
`memory_order`。

### <a name="return-value"></a>戻り値

加算の前に、 **\*this**に格納されている値を格納している*Ty*オブジェクト。

### <a name="remarks"></a>Remarks

メソッド`fetch_add`は、読み取り/書き込み操作を実行して、 **\*this**の格納された値に*値*をアトミックに追加し、 *Order*によって指定されたメモリ制約を適用します。

## <a name="fetch_and"></a>atomic:: fetch_and

値と、 **\*this**に格納されている既存の値に対してビットごとの and を実行します。

```cpp
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_and (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*型の値。

*順序*\
`memory_order`。

### <a name="return-value"></a>戻り値

ビットごとの and の結果を含む*Ty*オブジェクト。

### <a name="remarks"></a>Remarks

メソッド`fetch_and`は、読み取り/書き込み操作を実行して、 **\*this**の格納された値を、メモリ内の*値*のビットごとの and と、 **\*this**に格納されている現在の値に置き換えます。*順序*によって指定される制約。

## <a name="fetch_or"></a>atomic:: fetch_or

値と、 **\*this**に格納されている既存の値に対してビットごとの or を実行します。

```cpp
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_or (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*型の値。

*順序*\
`memory_order`。

### <a name="return-value"></a>戻り値

ビットごとの or の結果を格納する*Ty*オブジェクト。

### <a name="remarks"></a>Remarks

メソッド`fetch_or`は、読み取り/書き込み操作を実行して、 **\*this**の格納された値を、メモリ内の値のビットごとの or*値*と、 **\*this**に格納されている現在の値に置き換えます。*順序*によって指定される制約。

## <a name="fetch_sub"></a>atomic:: fetch_sub

指定した値を格納されている値から減算します。

```cpp
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_sub (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*型の値。

*順序*\
`memory_order`。

### <a name="return-value"></a>戻り値

減算の結果を格納している*Ty*オブジェクト。

### <a name="remarks"></a>Remarks

メソッド`fetch_sub`は、*順序*によって指定されたメモリの制約内で、 **\*this**の格納されている値から*値*をアトミックに減算するために、読み取り/書き込み操作を実行します。

## <a name="fetch_xor"></a>atomic:: fetch_xor

値と、 **\*this**に格納されている既存の値に対してビットごとの排他的 or を実行します。

```cpp
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
Ty atomic<Ty>::fetch_xor (
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*型の値。

*順序*\
`memory_order`。

### <a name="return-value"></a>戻り値

ビットごとの排他的 or の結果を格納する*Ty*オブジェクト。

### <a name="remarks"></a>Remarks

メソッド`fetch_xor`は、読み取り/書き込み操作を実行して、 **\*this**の格納されている値をビットごとの排他的 or*値*に置き換え、  **\*それに格納**されている現在の値を適用します。*順序*によって指定されるメモリの制約。

## <a name="is_lock_free"></a>atomic:: is_lock_free

**\*this**に対するアトミック操作がロックを解放するかどうかを指定します。

```cpp
bool is_lock_free() const volatile noexcept;
```

### <a name="return-value"></a>戻り値

**\*this**に対するアトミック操作がロックを解放している場合は true、それ以外の場合は false。

### <a name="remarks"></a>Remarks

その型に対するアトミック操作でロックが使用されていない場合、atomic 型はロックを解放します。

## <a name="load"></a>atomic:: load

指定されたメモリ制約内で、 **\*this**内の格納されている値を取得します。

```cpp
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const volatile noexcept;
Ty atomic::load(
   memory_order Order = memory_order_seq_cst
) const noexcept;
```

### <a name="parameters"></a>パラメーター

*順序*\
`memory_order`。 *順序*を`memory_order_release`または`memory_order_acq_rel`にすることはできません。

### <a name="return-value"></a>戻り値

**\*this**に格納されている取得値。

## <a name="store"></a>atomic:: store

指定された値を格納します。

```cpp
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) volatile noexcept;
void atomic<Ty>::store(
   Ty Value,
   memory_order Order = memory_order_seq_cst
) noexcept;
```

### <a name="parameters"></a>パラメーター

*数値*\
*Ty*オブジェクト。

*順序*\
`memory_order`制約です。

### <a name="remarks"></a>Remarks

このメンバー関数は、 *Order*に`*this`よって指定されたメモリ制約内で、に*値*をアトミックに格納します。

## <a name="see-also"></a>関連項目

[\<atomic>](../standard-library/atomic.md)\
[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
