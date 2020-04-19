---
title: '&lt;atomic&gt;'
description: 標準C++ライブラリの atomic ヘッダーで使用できる型および関数について説明します。
ms.date: 12/06/2019
f1_keywords:
- <atomic>
- atomic/std::atomic_int_least32_t
- atomic/std::atomic_ullong
- atomic/std::atomic_ptrdiff_t
- atomic/std::atomic_char16_t
- atomic/std::atomic_schar
- atomic/std::atomic_ulong
- atomic/std::atomic_uint_fast32_t
- atomic/std::atomic_uint8_t
- atomic/std::atomic_int32_t
- atomic/std::atomic_uint_fast64_t
- atomic/std::atomic_uint32_t
- atomic/std::atomic_int16_t
- atomic/std::atomic_uintmax_t
- atomic/std::atomic_intmax_t
- atomic/std::atomic_long
- atomic/std::atomic_int
- atomic/std::atomic_uint_least8_t
- atomic/std::atomic_size_t
- atomic/std::atomic_uint_fast16_t
- atomic/std::atomic_wchar_t
- atomic/std::atomic_int_fast64_t
- atomic/std::atomic_uint_fast8_t
- atomic/std::atomic_int_fast8_t
- atomic/std::atomic_intptr_t
- atomic/std::atomic_uint
- atomic/std::atomic_uint16_t
- atomic/std::atomic_char32_t
- atomic/std::atomic_uint64_t
- atomic/std::atomic_ushort
- atomic/std::atomic_int_least16_t
- atomic/std::atomic_char
- atomic/std::atomic_uint_least32_t
- atomic/std::atomic_uintptr_t
- atomic/std::atomic_short
- atomic/std::atomic_llong
- atomic/std::atomic_uint_least16_t
- atomic/std::atomic_int_fast16_t
- atomic/std::atomic_int_least8_t
- atomic/std::atomic_int_least64_t
- atomic/std::atomic_int_fast32_t
- atomic/std::atomic_uchar
- atomic/std::atomic_int8_t
- atomic/std::atomic_int64_t
- atomic/std::atomic_uint_least64_t
ms.assetid: e79a6b9f-52ff-48da-9554-654c4e1999f6
ms.openlocfilehash: d11e8bf2067c1c8525725ae74e713ac834d89ec4
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991166"
---
# <a name="ltatomicgt"></a>&lt;atomic&gt;

アトミック操作をサポートする型を作成するために使用するクラスとクラステンプレートを定義します。

## <a name="syntax"></a>構文

```cpp
#include <atomic>
```

## <a name="remarks"></a>Remarks

> [!NOTE]
> [/Clr: pure](../build/reference/clr-common-language-runtime-compilation.md)を使用してコンパイルされたコードでは、このヘッダーはブロックされます。 **/Clr: pure**と **/clr: safe**はどちらも、Visual Studio 2017 以降のバージョンでは非推奨とされます。

アトミック操作には、ミューテックス ロックを使用せずに、複数のスレッドを使用してオブジェクトを正しく操作することに役立つ 2 つの主要なプロパティがあります。

- アトミック操作は分割不可能なので、別のスレッドからの同じオブジェクトに対する2番目のアトミック操作では、最初のアトミック操作の前または後にのみ、オブジェクトの状態を取得できます。

- アトミック操作はその [memory_order](../standard-library/atomic-enums.md#memory_order_enum) 引数に基づいて、同一スレッド内の他のアトミック操作の効果の可視性に対して順序要件を確立します。 そのため、順序要件に違反するコンパイラの最適化を抑制します。

一部のプラットフォームでは、`mutex` を使用しないと、一部の型にアトミック操作を効率的に実装できない場合があります。 その型に対するアトミック操作においてロックが使用される場合、アトミック型は*ロック制御不要*になります。

**C++ 11**: シグナルハンドラーでは、`obj.is_lock_free()` または `atomic_is_lock_free(x)` が true の場合に、オブジェクトに対してアトミック操作を実行でき `obj`。

クラス[atomic_flag](../standard-library/atomic-flag-structure.md)は、**ブール**フラグを保持する最小のアトミック型を提供します。 その操作は常にロック制御不要です。

クラステンプレート `atomic<T>` は、その引数の `T` 型のオブジェクトを格納し、その格納されている値へのアトミックアクセスを提供します。 これは、[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md) を使用してコピーでき、[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md) を使用して等価性をテストできる任意の型を使用してインスタンス化することができます。 具体的には、これらの要件を満たすユーザー定義の型と、多くの場合、浮動小数点型で使用できます。

テンプレートには、整数型の一連の特殊化およびポインターの部分的特殊化もあります。 これらの特殊化は、プライマリテンプレートでは利用できない追加の操作を提供します。

## <a name="pointer-specializations"></a>ポインターの特殊化

`atomic<T *>` の部分的特殊化は、すべてのポインター型に適用されます。 これらはポインター演算のメソッドを提供します。

## <a name="integral-specializations"></a>整数の特殊化

`atomic<integral>` の特殊化は、すべての整数型に適用されます。 プライマリテンプレートでは利用できない追加の操作を提供します。

各 `atomic<integral>` 型には、`if directive` でコンパイル時にその型に対する操作がロック制御不要かどうかを判断するために使用できる対応するマクロがあります。 マクロの値が0の場合、型に対する操作はロックされません。 値が 1 の場合は、操作がロック制御不要の可能性があり、ランタイム チェックが必要です。 値が 2 の場合は、操作はロック制御不要です。 関数 `atomic_is_lock_free` を使用して、実行時にその型での操作がロック制御不要かどうかを判断することができます。

各整数型には、その整数型のオブジェクトを管理する、対応する名前付きアトミック型があります。 各 `atomic_integral` 型には、`atomic<T>` の対応するインスタンス化と同じメンバー関数のセットがあり、任意の非メンバーのアトミック関数に渡すことができます。

|`atomic_integral` の型|整数型|`atomic_is_lock_free` マクロ|
|----------------------------|-------------------|---------------------------------|
|`atomic_char`|**char**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_schar`|**signed char**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_uchar`|**unsigned char**|ATOMIC_CHAR_LOCK_FREE|
|`atomic_char16_t`|`char16_t`|ATOMIC_CHAR16_T_LOCK_FREE|
|`atomic_char32_t`|`char32_t`|ATOMIC_CHAR32_T_LOCK_FREE|
|`atomic_wchar_t`|**wchar_t**|ATOMIC_WCHAR_T_LOCK_FREE|
|`atomic_short`|**short**|ATOMIC_SHORT_LOCK_FREE|
|`atomic_ushort`|**unsigned short**|ATOMIC_SHORT_LOCK_FREE|
|`atomic_int`|**int**|ATOMIC_INT_LOCK_FREE|
|`atomic_uint`|**unsigned int**|ATOMIC_INT_LOCK_FREE|
|`atomic_long`|**long**|ATOMIC_LONG_LOCK_FREE|
|`atomic_ulong`|**unsigned long**|ATOMIC_LONG_LOCK_FREE|
|`atomic_llong`|**long long**|ATOMIC_LLONG_LOCK_FREE|
|`atomic_ullong`|**unsigned long long**|ATOMIC_LLONG_LOCK_FREE|

Typedef 名は、ヘッダー \<inttypes.h> で定義されている一部の型のアトミック テンプレートの特殊化のために存在します。

|アトミック型|Typedef 名|
|-----------------|------------------|
|`atomic_int8_t`|`atomic<int8_t>`|
|`atomic_uint8_t`|`atomic<uint8_t>`|
|`atomic_int16_t`|`atomic<int16_t>`|
|`atomic_uint16_t`|`atomic<uint16_t>`|
|`atomic_int32_t`|`atomic<int32_t>`|
|`atomic_uint32_t`|`atomic<uint32_t>`|
|`atomic_int64_t`|`atomic<int64_t>`|
|`atomic_uint64_t`|`atomic<uint64_t>`|
|`atomic_int_least8_t`|`atomic<int_least8_t>`|
|`atomic_uint_least8_t`|`atomic<uint_least8_t>`|
|`atomic_int_least16_t`|`atomic<int_least16_t>`|
|`atomic_uint_least16_t`|`atomic<uint_least16_t>`|
|`atomic_int_least32_t`|`atomic<int_least32_t>`|
|`atomic_uint_least32_t`|`atomic<uint_least32_t>`|
|`atomic_int_least64_t`|`atomic<int_least64_t>`|
|`atomic_uint_least64_t`|`atomic<uint_least64_t>`|
|`atomic_int_fast8_t`|`atomic<int_fast8_t>`|
|`atomic_uint_fast8_t`|`atomic<uint_fast8_t>`|
|`atomic_int_fast16_t`|`atomic<int_fast16_t>`|
|`atomic_uint_fast16_`|`atomic<uint_fast16_t>`|
|`atomic_int_fast32_t`|`atomic<int_fast32_t>`|
|`atomic_uint_fast32_t`|`atomic<uint_fast32_t>`|
|`atomic_int_fast64_t`|`atomic<int_fast64_t>`|
|`atomic_uint_fast64_t`|`atomic<uint_fast64_t>`|
|`atomic_intptr_t`|`atomic<intptr_t>`|
|`atomic_uintptr_t`|`atomic<uintptr_t>`|
|`atomic_size_t`|`atomic<size_t>`|
|`atomic_ptrdiff_t`|`atomic<ptrdiff_t>`|
|`atomic_intmax_t`|`atomic<intmax_t>`|
|`atomic_uintmax_t`|`atomic<uintmax_t>`|

## <a name="structs"></a>構造体

|[名前]|説明|
|----------|-----------------|
|[atomic 構造体](../standard-library/atomic-structure.md)|格納された値に対してアトミック操作を実行するオブジェクトについて記述します。|
|[atomic_flag 構造体](../standard-library/atomic-flag-structure.md)|**ブール**型のフラグをアトミックに設定およびクリアするオブジェクトを記述します。|

## <a name="enums"></a>列挙体

|[名前]|説明|
|----------|-----------------|
|[memory_order 列挙型](../standard-library/atomic-enums.md#memory_order_enum)|メモリ位置に対する同期操作のシンボル名を提供します。 これらの操作は、1 つのスレッドの割り当てが別のスレッドにおいて表示される方法に影響します。|

## <a name="functions"></a>関数

次の一覧では、`_explicit` で終了しない関数は、対応する `_explicit`のセマンティクスを持っていますが、`memory_order_seq_cst`の暗黙の[memory_order](../standard-library/atomic-enums.md#memory_order_enum)引数を持っている点が異なります。

|[名前]|説明|
|----------|-----------------|
|[atomic_compare_exchange_strong](../standard-library/atomic-functions.md#atomic_compare_exchange_strong)|*アトミックの比較および交換*の操作を実行します。|
|[atomic_compare_exchange_strong_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_strong_explicit)|*アトミックの比較および交換*の操作を実行します。|
|[atomic_compare_exchange_weak](../standard-library/atomic-functions.md#atomic_compare_exchange_weak)|*弱いアトミックの比較および交換*の操作を実行します。|
|[atomic_compare_exchange_weak_explicit](../standard-library/atomic-functions.md#atomic_compare_exchange_weak_explicit)|*弱いアトミックの比較および交換*の操作を実行します。|
|[atomic_exchange](../standard-library/atomic-functions.md#atomic_exchange)|格納されている値を置き換えます。|
|[atomic_exchange_explicit](../standard-library/atomic-functions.md#atomic_exchange_explicit)|格納されている値を置き換えます。|
|[atomic_fetch_add](../standard-library/atomic-functions.md#atomic_fetch_add)|指定した値を格納されている既存の値に加算します。|
|[atomic_fetch_add_explicit](../standard-library/atomic-functions.md#atomic_fetch_add_explicit)|指定した値を格納されている既存の値に加算します。|
|[atomic_fetch_and](../standard-library/atomic-functions.md#atomic_fetch_and)|指定されている値と格納されている既存の値でビットごとの `and` を実行します。|
|[atomic_fetch_and_explicit](../standard-library/atomic-functions.md#atomic_fetch_and_explicit)|指定されている値と格納されている既存の値でビットごとの `and` を実行します。|
|[atomic_fetch_or](../standard-library/atomic-functions.md#atomic_fetch_or)|指定されている値と格納されている既存の値でビットごとの `or` を実行します。|
|[atomic_fetch_or_explicit](../standard-library/atomic-functions.md#atomic_fetch_or_explicit)|指定されている値と格納されている既存の値でビットごとの `or` を実行します。|
|[atomic_fetch_sub](../standard-library/atomic-functions.md#atomic_fetch_sub)|指定した値を格納されている既存の値から減算します。|
|[atomic_fetch_sub_explicit](../standard-library/atomic-functions.md#atomic_fetch_sub_explicit)|指定した値を格納されている既存の値から減算します。|
|[atomic_fetch_xor](../standard-library/atomic-functions.md#atomic_fetch_xor)|指定されている値と格納されている既存の値でビットごとの `exclusive or` を実行します。|
|[atomic_fetch_xor_explicit](../standard-library/atomic-functions.md#atomic_fetch_xor_explicit)|指定されている値と格納されている既存の値でビットごとの `exclusive or` を実行します。|
|[atomic_flag_clear](../standard-library/atomic-functions.md#atomic_flag_clear)|`atomic_flag` オブジェクトのフラグを**false**に設定します。|
|[atomic_flag_clear_explicit](../standard-library/atomic-functions.md#atomic_flag_clear_explicit)|`atomic_flag` オブジェクトのフラグを**false**に設定します。|
|[atomic_flag_test_and_set](../standard-library/atomic-functions.md#atomic_flag_test_and_set)|`atomic_flag` オブジェクトのフラグを**true**に設定します。|
|[atomic_flag_test_and_set_explicit](../standard-library/atomic-functions.md#atomic_flag_test_and_set_explicit)|`atomic_flag` オブジェクトのフラグを**true**に設定します。|
|[atomic_init](../standard-library/atomic-functions.md#atomic_init)|`atomic` オブジェクトに格納されている値を設定します。|
|[atomic_is_lock_free](../standard-library/atomic-functions.md#atomic_is_lock_free)|指定されたオブジェクトに対するアトミック操作がロック制御不要かどうかを指定します。|
|[atomic_load](../standard-library/atomic-functions.md#atomic_load)|アトミックに値を取得します。|
|[atomic_load_explicit](../standard-library/atomic-functions.md#atomic_load_explicit)|アトミックに値を取得します。|
|[atomic_signal_fence](../standard-library/atomic-functions.md#atomic_signal_fence)|同じスレッドで実行される通知ハンドラーを持つスレッドの呼び出しで、フェンス間のメモリ オーダリング要件を確立する*フェンス*として機能します。|
|[atomic_store](../standard-library/atomic-functions.md#atomic_store)|アトミックに値を格納します。|
|[atomic_store_explicit](../standard-library/atomic-functions.md#atomic_store_explicit)|アトミックに値を格納します。|
|[atomic_thread_fence](../standard-library/atomic-functions.md#atomic_thread_fence)|他のフェンスに関するメモリ オーダリングの要件を確立する*フェンス*として機能します。|
|[kill_dependency](../standard-library/atomic-functions.md#kill_dependency)|可能な依存関係チェーンを切断します。|

## <a name="see-also"></a>参照

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
