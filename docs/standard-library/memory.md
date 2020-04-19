---
title: '&lt;memory&gt;'
ms.date: 08/04/2019
f1_keywords:
- memory/std::<memory>
- <memory>
- std::<memory>
helpviewer_keywords:
- memory header
ms.openlocfilehash: 4a6383ee94d021373b984122926a5bb73e18f953
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689363"
---
# <a name="ltmemorygt"></a>&lt;memory&gt;

メモリの割り当てとオブジェクトの解放を支援するクラス、演算子、および各種テンプレートを定義します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<memory>

**名前空間:** std

## <a name="members"></a>メンバー

### <a name="functions"></a>関数

|||
|-|-|
|[addressof](../standard-library/memory-functions.md#addressof)|オブジェクトの実際のアドレスを取得します。|
|[align](../standard-library/memory-functions.md#align)|指定されたアラインメントと開始アドレスに基づいて特定のサイズの範囲へのポインターを返します。|
|[allocate_shared](../standard-library/memory-functions.md#allocate_shared)|指定されたアロケーターを使用し、特定の型に割り当てられ構築されたオブジェクトに対して `shared_ptr` を作成します。|
|[atomic_compare_exchange_strong](../standard-library/memory-functions.md#atomic_compare_exchange_strong)||
|[atomic_compare_exchange_weak](../standard-library/memory-functions.md#atomic_compare_exchange_weak)||
|[atomic_compare_exchange_strong_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_strong_explicit)||
|[atomic_compare_exchange_weak_explicit](../standard-library/memory-functions.md#atomic_compare_exchange_weak_explicit)||
|[atomic_exchange](../standard-library/memory-functions.md#atomic_exchange)||
|[atomic_exchange_explicit](../standard-library/memory-functions.md#atomic_exchange_explicit)||
|[atomic_is_lock_free](../standard-library/memory-functions.md#atomic_is_lock_free)||
|[atomic_load](../standard-library/memory-functions.md#atomic_load)||
|[atomic_load_explicit](../standard-library/memory-functions.md#atomic_load_explicit)||
|[atomic_store](../standard-library/memory-functions.md#atomic_store)||
|[atomic_store_explicit](../standard-library/memory-functions.md#atomic_store_explicit)||
|[const_pointer_cast](../standard-library/memory-functions.md#const_pointer_cast)|`shared_ptr` への定数キャストを行います。|
|[declare_no_pointers](../standard-library/memory-functions.md#declare_no_pointers)|指定されたアドレスを先頭とする指定されたブロック サイズの範囲内にある文字が、追跡可能なポインターを含まないことをガベージ コレクターに通知します。|
|[declare_reachable](../standard-library/memory-functions.md#declare_reachable)|指定されたアドレスが、割り当てられたストレージのアドレスであり、そのストレージに到達可能であることをガベージ コレクションに通知します。|
|[default_delete](../standard-library/memory-functions.md#default_delete)|`operator new` を使用して割り当てられたオブジェクトを削除します。 `unique_ptr` での使用に適しています。|
|[destroy_at](../standard-library/memory-functions.md#destroy_at)|短縮形 `destroy` メソッド。|
|[destroy](../standard-library/memory-functions.md#destroy)|短縮形 `destroy` メソッド。|
|[destroy_n](../standard-library/memory-functions.md#destroy_n)|短縮形 `destroy` メソッド。|
|[dynamic_pointer_cast](../standard-library/memory-functions.md#dynamic_pointer_cast)|`shared_ptr` への動的キャストを行います。|
|[get_deleter](../standard-library/memory-functions.md#get_deleter)|`shared_ptr` から削除子を取得します。|
|[get_pointer_safety](../standard-library/memory-functions.md#get_pointer_safety)|ガベージ コレクターが想定するポインターの安全性の種類を返します。|
|[get_temporary_buffer](../standard-library/memory-functions.md#get_temporary_buffer)|指定した要素数を上限とする要素シーケンスに対し、一時的なストレージを割り当てます。|
|[make_shared](../standard-library/memory-functions.md#make_shared)|既定のアロケーターを使用してゼロ以上の引数から構築された割り当て済みオブジェクトを指し示す `shared_ptr` を作成し、返します。|
|[make_unique](../standard-library/memory-functions.md#make_unique)|0 以上の引数から構築された割り当て済みオブジェクトを指し示す [unique_ptr](../standard-library/unique-ptr-class.md) を作成し、返します。|
|[pointer_safety](../standard-library/memory-enums.md#pointer_safety)|`get_pointer_safety` のすべての可能な戻り値の列挙体です。|
|[return_temporary_buffer](../standard-library/memory-functions.md#return_temporary_buffer)|`get_temporary_buffer` テンプレート関数を使用して割り当てられた一時メモリを解放します。|
|[static_pointer_cast](../standard-library/memory-functions.md#static_pointer_cast)|`shared_ptr` への静的キャストを行います。|
|[swap](../standard-library/memory-functions.md#swap)|2 つの `shared_ptr` または `weak_ptr` オブジェクトを交換します。|
|[undeclare_no_pointers](../standard-library/memory-functions.md#undeclare_no_pointers)|ベース アドレス ポインターとブロック サイズで定義されたメモリ ブロック内の文字が、追跡可能なポインターを含む可能性があることをガベージ コレクターに通知します。|
|[undeclare_reachable](../standard-library/memory-functions.md#undeclare_reachable)|指定されたメモリ位置に到達できないことを `garbage_collector` に通知します。|
|[uninitialized_copy](../standard-library/memory-functions.md#uninitialized_copy)|指定された入力範囲にあるオブジェクトを、初期化されていないコピー先の範囲にコピーします。|
|[uninitialized_copy_n](../standard-library/memory-functions.md#uninitialized_copy_n)|入力反復子から、指定した数の要素のコピーを作成します。 コピーは前方反復子に格納されます。|
|[uninitialized_default_construct](../standard-library/memory-functions.md#uninitialized_default_construct)|短縮形 `uninitialized_default_construct` メソッド。|
|[uninitialized_default_construct_n](../standard-library/memory-functions.md#uninitialized_default_construct_n)|短縮形 `uninitialized_construct` メソッド。|
|[uninitialized_fill](../standard-library/memory-functions.md#uninitialized_fill)|指定された値のオブジェクトを、初期化されていないコピー先の範囲にコピーします。|
|[uninitialized_fill_n](../standard-library/memory-functions.md#uninitialized_fill_n)|指定された値のオブジェクトを、初期化されていないコピー先の範囲にある指定された数の要素にコピーします。|
|[uninitialized_move](../standard-library/memory-functions.md#uninitialized_move)|短縮形 `uninitialized_move` メソッド。|
|[uninitialized_move_n](../standard-library/memory-functions.md#uninitialized_move_n)|短縮形 `uninitialized_move` メソッド。|
|[uninitialized_value_construct](../standard-library/memory-functions.md#uninitialized_value_construct)|短縮形 `uninitialized_value_construct` メソッド。|
|[uninitialized_value_construct_n](../standard-library/memory-functions.md#uninitialized_value_construct_n)|短縮形 `uninitialized_value_construct` メソッド。|
|[uses_allocator_v](../standard-library/memory-functions.md#uses_allocator_v)||

### <a name="operators"></a>演算子

|||
|-|-|
|[operator!=](../standard-library/memory-operators.md#op_neq)|指定したクラスのアロケーター オブジェクト間の非等値をテストします。|
|[operator==](../standard-library/memory-operators.md#op_eq_eq)|指定したクラスのアロケーター オブジェクト間の等値をテストします。|
|[operator>=](../standard-library/memory-operators.md#op_gt_eq)|指定したクラスの 1 つ目のアロケーター オブジェクトが 2 つ目のアロケーター オブジェクト以上であるかどうかをテストします。|
|[operator<](../standard-library/memory-operators.md#op_lt)|指定したクラスの 1 つ目のオブジェクトが 2 つ目のオブジェクト未満であるかどうかをテストします。|
|[operator\<=](../standard-library/memory-operators.md#op_gt_eq)|指定したクラスの 1 つ目のオブジェクトが 2 つ目のオブジェクト以下であるかどうかをテストします。|
|[operator>](../standard-library/memory-operators.md#op_gt)|指定したクラスの 1 つ目のオブジェクトが 2 つ目のオブジェクトを超えるかどうかをテストします。|
|[operator<<](../standard-library/memory-operators.md#op_lt_lt)|`shared_ptr` の挿入演算子です。|

### <a name="classes"></a>クラス

|||
|-|-|
|[allocator](../standard-library/allocator-class.md)|クラステンプレートは **、型の**オブジェクトの配列に対して、ストレージの割り当てと解放を管理するオブジェクトを記述します。|
|[allocator_traits](../standard-library/allocator-traits-class.md)|アロケーター対応のコンテナーが必要とするすべての情報を指定したオブジェクトを記述します。|
|[auto_ptr](../standard-library/auto-ptr-class.md)|クラステンプレートは<strong>\*</strong> **型の**割り当てられたオブジェクトへのポインターを格納するオブジェクトを記述します。このオブジェクトは、それを囲む auto_ptr が破棄されるときに、そのオブジェクトが確実に削除されるようにします。|
|[bad_weak_ptr](../standard-library/bad-weak-ptr-class.md)|weak_ptr が無効であることを示す例外を報告します。|
|[enabled_shared_from_this](../standard-library/enable-shared-from-this-class.md)|`shared_ptr` の生成を支援します。|
|[pointer_traits](../standard-library/pointer-traits-struct.md)|ポインター型 `Ptr` を持つアロケーターを記述するために `allocator_traits` 型のオブジェクトに必要な情報を提供します。|
|[raw_storage_iterator](../standard-library/raw-storage-iterator-class.md)|アルゴリズムの結果を初期化されていないメモリに格納するために用意されたアダプター クラスです。|
|[shared_ptr](../standard-library/shared-ptr-class.md)|参照カウント スマート ポインターを、動的に割り当てられたオブジェクトにラップします。|
|[unique_ptr](../standard-library/unique-ptr-class.md)|所有されているオブジェクトへのポインターを格納します。 このポインターは、この `unique_ptr` によってのみ所有されます。 `unique_ptr` は所有者が破棄されたときに破棄されます。|
|[weak_ptr](../standard-library/weak-ptr-class.md)|関連付けの弱いポインターをラップします。|

### <a name="structures"></a>構造体

|||
|-|-|
|[allocator_arg_t](../standard-library/allocator-class.md#allocator_arg_t)||
|[default_delete](../standard-library/default-delete-struct.md)||
|hash|@No__t_0 および `shared_ptr` に特化したオーバーロードを提供します。|
|[owner_less](../standard-library/memory-functions.md#owner_less)|共有ポインターとウィーク ポインターの所有権ベースの混合型比較を実行します。|
|[uses_allocator](../standard-library/allocator-class.md#uses_allocator)||

### <a name="specializations"></a>特殊化

|||
|-|-|
|[allocator\<void>](../standard-library/allocator-void-class.md)|**Void**型へのクラステンプレートアロケーターの特殊化で、この特殊なコンテキストで意味を持つメンバー型のみを定義しています。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
