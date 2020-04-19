---
title: コンカレンシー名前空間関数 (AMP)
ms.date: 11/04/2016
f1_keywords:
- amp/Concurrency::all_memory_fence
- amp/Concurrency::atomic_compare_exchange
- amp/Concurrency::atomic_fetch_dec
- amp/Concurrency::atomic_fetch_max
- amp/Concurrency::atomic_fetch_min
- amp/Concurrency::copy
- amp/Concurrency::direct3d_abort
- amp/Concurrency::direct3d_printf
- amp/Concurrency::global_memory_fence
- amp/Concurrency::tile_static_memory_fence
ms.assetid: 2bef0985-cb90-4ece-90b9-66529aec73c9
ms.openlocfilehash: 90a23ce111f7307610de3f0ad4bcec05d8de27df
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126901"
---
# <a name="concurrency-namespace-functions-amp"></a>コンカレンシー名前空間関数 (AMP)

||||
|-|-|-|
|[all_memory_fence](#all_memory_fence)|[amp_uninitialize](#amp_uninitialize)|[atomic_compare_exchange](#atomic_compare_exchange)|
|[atomic_exchange 関数 (C++ AMP)](#atomic_exchange)|[atomic_fetch_add 関数 (C++ AMP)](#atomic_fetch_add)|[atomic_fetch_and 関数 (C++ AMP)](#atomic_fetch_and)|
|[atomic_fetch_dec](#atomic_fetch_dec)|[atomic_fetch_inc](#atomic_fetch_inc)|[atomic_fetch_max](#atomic_fetch_max)|
|[atomic_fetch_min](#atomic_fetch_min)|[atomic_fetch_or 関数 (C++ AMP)](#atomic_fetch_or)|[atomic_fetch_sub 関数 (C++ AMP)](#atomic_fetch_sub)|
|[atomic_fetch_xor 関数 (C++ AMP)](#atomic_fetch_xor)|[copy](#copy)|[copy_async](#copy_async)|
|[direct3d_abort](#direct3d_abort)|[direct3d_errorf](#direct3d_errorf)|[direct3d_printf](#direct3d_printf)|
|[global_memory_fence](#global_memory_fence)|[parallel_for_each 関数 (C++ AMP)](#parallel_for_each)|[tile_static_memory_fence](#tile_static_memory_fence)|

## <a name="all_memory_fence"></a>all_memory_fence

すべてのメモリ アクセスが完了するまでタイルのすべてのスレッドの実行をブロックします。 これによって、すべてのメモリ アクセスがスレッド タイルの他のスレッドから参照でき、プログラムの順序で実行されます。

```cpp
inline void all_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Barrier*<br/>
`tile_barrier` オブジェクトです。

## <a name="amp_uninitialize"></a>amp_uninitialize

C++ AMP ランタイムを初期化前の状態に戻します。 アプリケーションの有効期間中にこの関数を複数回呼び出すことは有効です。 この関数C++を呼び出した後に amp API を呼びC++出すと、amp ランタイムが再初期化されます。 この関数の複数の呼び出しにまたがって C++ AMP オブジェクトを使用することは無効であり、それにより未定義の動作が発生することに注意してください。 また、この関数と他の AMP API を同時に呼び出すことは無効であり、未定義の動作が発生します。

```cpp
void __cdecl amp_uninitialize();
```

## <a name="atomic_compare_exchange"></a>atomic_compare_exchange

1 番目の引数で指定されたメモリ位置に格納されている値を 2 番目に指定された引数の値と等しいかどうかアトミックに比較し、値が同じ場合、メモリ位置の値は 3 番目に指定された引数の値に変更されます。

```cpp
inline bool atomic_compare_exchange(
    _Inout_ int* _Dest,
    _Inout_ int* _Expected_value,
    int value
    ) restrict(amp)

inline bool atomic_compare_exchange(
    _Inout_ unsigned int* _Dest,
    _Inout_ unsigned int* _Expected_value,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
比較される値の 1 つが読み取られ、新しい値 (ある場合) が格納される位置。

*_Expected_value*<br/>
比較される 2 番目の値が読み取られる位置。

*value*<br/>
`_Dest` が `_Dest` と等しい場合、`_Expected_value` によって指定したメモリ位置に格納される値。

### <a name="return-value"></a>戻り値

操作が成功した場合は**true** 。それ以外の場合は**false**。

## <a name="atomic_exchange"></a>atomic_exchange 関数 (C++ AMP)

コピー先の場所の値を分割不可能な操作として設定します。

```cpp
inline int atomic_exchange(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_exchange(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)

inline float atomic_exchange(
    _Inout_ float* _Dest,
    float value
    ) restrict(amp)
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
移動先の場所へのポインター。

*value*<br/>
新しい値です。

### <a name="return-value"></a>戻り値

コピー先の場所の元の値。

## <a name="atomic_fetch_add"></a>atomic_fetch_add 関数 (C++ AMP)

メモリ位置の値に値をアトミックに追加します。

```cpp
inline int atomic_fetch_add(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_add(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
メモリ位置へのポインター。

*value*<br/>
追加する値。

### <a name="return-value"></a>戻り値

メモリ位置の元の値。

## <a name="atomic_fetch_and"></a>atomic_fetch_and 関数 (C++ AMP)

値とメモリ位置の値のビットごとの AND 演算をアトミックに実行します。

```cpp
inline int atomic_fetch_and(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_and(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
メモリ位置へのポインター。

*value*<br/>
ビットごとの AND 演算で使用する値。

### <a name="return-value"></a>戻り値

メモリ位置の元の値。

## <a name="atomic_fetch_dec"></a>atomic_fetch_dec

指定したメモリ位置に格納されている値をアトミックにデクリメントします。

```cpp
inline int atomic_fetch_dec(_Inout_ int* _Dest
    ) restrict(amp)

inline unsigned int atomic_fetch_dec(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
デクリメントされる値のメモリ内での位置。

### <a name="return-value"></a>戻り値

メモリ位置に格納されている元の値。

## <a name="atomic_fetch_inc"></a>atomic_fetch_inc

指定されたメモリ位置に格納されている値をアトミックにインクリメントします。

```cpp
inline int atomic_fetch_inc(_Inout_ int* _Dest) restrict(amp);

inline unsigned int atomic_fetch_inc(_Inout_ unsigned int* _Dest) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
インクリメントされる値のメモリでの位置。

### <a name="return-value"></a>戻り値

メモリ位置に格納されている元の値。

## <a name="atomic_fetch_max"></a>atomic_fetch_max

最初の引数で指定されたメモリ位置に格納されている値と 2 番目の引数で指定された値の間での最大値をアトミックに計算し、同じメモリ位置に格納します。

```cpp
inline int atomic_fetch_max(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_max(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
比較される値の 1 つが読み取られ、2 つの値の最大値が格納される位置。

*value*<br/>
指定した位置の値と比較する値。

### <a name="return-value"></a>戻り値

指定した位置に格納される元の値。

## <a name="atomic_fetch_min"></a>atomic_fetch_min

最初の引数で指定されたメモリ位置に格納されている値と 2 番目の引数で指定された値の間での最小値をアトミックに計算し、同じメモリ位置に格納します。

```cpp
inline int atomic_fetch_min(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_min(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
比較される値の 1 つが読み取られ、2 つの値の最小値が格納される位置。

*value*<br/>
指定した位置の値と比較する値。

### <a name="return-value"></a>戻り値

指定した位置に格納される元の値。

## <a name="atomic_fetch_or"></a>atomic_fetch_or 関数 (C++ AMP)

値とメモリ位置の値を使用して、ビットごとの OR 演算をアトミックに実行します。

```cpp
inline int atomic_fetch_or(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_or(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
メモリ位置へのポインター。

*value*<br/>
ビットごとの OR 演算で使用する値。

### <a name="return-value"></a>戻り値

メモリ位置の元の値。

## <a name="atomic_fetch_sub"></a>atomic_fetch_sub 関数 (C++ AMP)

メモリ位置から値をアトミックに減算します。

```cpp
inline int atomic_fetch_sub(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_sub(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
移動先の場所へのポインター。

*value*<br/>
減算される値。

### <a name="return-value"></a>戻り値

メモリ位置の元の値。

## <a name="atomic_fetch_xor"></a>atomic_fetch_xor 関数 (C++ AMP)

値とメモリ位置のビットごとの XOR 演算をアトミックに実行します。

```cpp
inline int atomic_fetch_xor(
    _Inout_ int* _Dest,
    int value
    ) restrict(amp)

inline unsigned int atomic_fetch_xor(
    _Inout_ unsigned int* _Dest,
    unsigned int value
    ) restrict(amp)
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
メモリ位置へのポインター。

*value*<br/>
XOR 計算で使用する値。

### <a name="return-value"></a>戻り値

メモリ位置の元の値。

## <a name="copy"></a>  copy

C++ AMP オブジェクトをコピーします。 すべての同期データ転送の要件が満たされます。 アクセラレータでコードを実行しているときにデータをコピーすることはできません。 この関数の一般的な形式は `copy(src, dest)` です。

```cpp
template <typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    array<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
   OutputIterator _DestIter);

template <typename value_type, int _Rank>
void copy(
    const array<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<const value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<const value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    InputIterator _SrcLast,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
void copy(
    InputIterator _SrcFirst,
    array_view<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
void copy(
    const array_view<value_type, _Rank>& _Src,
    OutputIterator _DestIter);
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
コピー先のオブジェクト。

*_DestIter*<br/>
コピー先での開始位置の出力反復子。

*InputIterator*<br/>
入力反復子の型。

*OutputIterator*<br/>
出力反復子の型。

*_Rank*<br/>
コピー元のオブジェクトまたはコピー先のオブジェクトのランク。

*_Src*<br/>
コピーするオブジェクト。

*_SrcFirst*<br/>
ソース コンテナーへの先頭の反復子。

*_SrcLast*<br/>
ソース コンテナーへの終了の反復子。

*value_type*<br/>
コピーされた要素のデータ型。

## <a name="copy_async"></a>copy_async

AMP オブジェクトC++をコピーし、待機できる[completion_future](completion-future-class.md)オブジェクトを返します。 アクセラレータでコードを実行しているときにデータをコピーすることはできません。  この関数の一般的な形式は `copy(src, dest)` です。

```cpp
template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,
    array<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst,
    array<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src, OutputIterator _DestIter);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,
    array<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<const value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst, InputIterator _SrcLast,
    array_view<value_type, _Rank>& _Dest);

template <typename InputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(InputIterator _SrcFirst,
    array_view<value_type, _Rank>& _Dest);

template <typename OutputIterator, typename value_type, int _Rank>
concurrency::completion_future copy_async(
    const array_view<value_type, _Rank>& _Src, OutputIterator _DestIter);
```

### <a name="parameters"></a>パラメーター

*_Dest*<br/>
コピー先のオブジェクト。

*_DestIter*<br/>
コピー先での開始位置の出力反復子。

*InputIterator*<br/>
入力反復子の型。

*OutputIterator*<br/>
出力反復子の型。

*_Rank*<br/>
コピー元のオブジェクトまたはコピー先のオブジェクトのランク。

*_Src*<br/>
コピーするオブジェクト。

*_SrcFirst*<br/>
ソース コンテナーへの先頭の反復子。

*_SrcLast*<br/>
ソース コンテナーへの終了の反復子。

*value_type*<br/>
コピーされた要素のデータ型。

### <a name="return-value"></a>戻り値

待機できる `future<void>`。

## <a name="direct3d_abort"></a>direct3d_abort

制限句 `restrict(amp)` を使用して関数の実行を中止します。 AMP ランタイムが呼び出しを検出すると、 [runtime_exception](runtime-exception-class.md) 例外が発生し、"リファレンス ラスタライザー: シェーダー中止命令が発行" というエラー メッセージが返されます。

```cpp
void direct3d_abort() restrict(amp);
```

## <a name="direct3d_errorf"></a>direct3d_errorf

Visual Studio の出力ウィンドウに書式指定文字列を出力します。 これは制限句 `restrict(amp)` を使用して関数から呼び出されます。 AMP ランタイムが呼び出しを検出すると、同じ書式指定文字列を使用して[runtime_exception](runtime-exception-class.md)例外を発生させます。

```cpp
void direct3d_errorf(
    const char *,
...) restrict(amp);
```

## <a name="direct3d_printf"></a>direct3d_printf

Visual Studio の出力ウィンドウに書式指定文字列を出力します。 これは制限句 `restrict(amp)` を使用して関数から呼び出されます。

```cpp
void direct3d_printf(
    const char *,
...) restrict(amp);
```

## <a name="global_memory_fence"></a>global_memory_fence

すべてのグローバル メモリ アクセスが完了するまでタイルのすべてのスレッドの実行をブロックします。 これによって、グローバル メモリのアクセスがスレッド タイルの他のスレッドから参照でき、プログラムの順序で実行されます。

```cpp
inline void global_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Barrier*<br/>
tile_barrier オブジェクト

## <a name="parallel_for_each"></a>parallel_for_each 関数 (C++ AMP)

計算ドメインを越えて関数を実行します。 詳細については、「 [ C++ AMP の概要](../../../parallel/amp/cpp-amp-overview.md)」を参照してください。

```cpp
template <int _Rank, typename _Kernel_type>
void parallel_for_each(
    const extent<_Rank>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
   const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, typename _Kernel_type>
void parallel_for_each(
    const tiled_extent<_Dim0>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Rank, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const extent<_Rank>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, int _Dim2, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0, _Dim1, _Dim2>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, int _Dim1, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0, _Dim1>& _Compute_domain,
    const _Kernel_type& _Kernel);

template <int _Dim0, typename _Kernel_type>
void parallel_for_each(
    const accelerator_view& _Accl_view,
    const tiled_extent<_Dim0>& _Compute_domain,
    const _Kernel_type& _Kernel);
```

### <a name="parameters"></a>パラメーター

*_Accl_view*<br/>
並列計算を実行する `accelerator_view` オブジェクト。

*_Compute_domain*<br/>
計算用のデータを含む `extent` オブジェクト。

*_Dim0*<br/>
`tiled_extent` オブジェクトの次元。

*_Dim1*<br/>
`tiled_extent` オブジェクトの次元。

*_Dim2*<br/>
`tiled_extent` オブジェクトの次元。

*_Kernel*<br/>
型 "index\<_Rank >" の引数を受け取り、並列計算を実行するラムダまたは関数オブジェクト。

*_Kernel_type*<br/>
ラムダまたはファンクタ。

*_Rank*<br/>
範囲のランク。

## <a name="tile_static_memory_fence"></a>tile_static_memory_fence

すべての未処理の `tile_static` メモリ アクセスが完了するまで、タイルのすべてのスレッドの実行をブロックします。 これによって、`tile_static` メモリ アクセスがスレッド タイルのその他のスレッドに表示され、アクセスをプログラムの順序で実行することができます。

```cpp
inline void tile_static_memory_fence(const tile_barrier& _Barrier) restrict(amp);
```

### <a name="parameters"></a>パラメーター

*_Barrier*<br/>
tile_barrier オブジェクト。

## <a name="see-also"></a>参照

[コンカレンシー名前空間 (C++ AMP)](concurrency-namespace-cpp-amp.md)
