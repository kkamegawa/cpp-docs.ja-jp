---
title: Concurrency 名前空間 (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- AMP/Concurrency
helpviewer_keywords:
- Concurrency namespace
ms.assetid: b5aab265-3bac-42c5-8ead-f92ce05ef267
ms.openlocfilehash: 34c3c10fa6bec2737ba78a71c282f90f284a28c2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139365"
---
# <a name="concurrency-namespace-c-amp"></a>Concurrency 名前空間 (C++ AMP)

データ並列ハードウェアでの C++ コードの実行を高速化するクラスと関数を提供します。 詳細については、「AMP の概要」を参照してください。 [ C++](../cpp-amp-overview.md)

## <a name="syntax"></a>構文

```cpp
namespace Concurrency;
```

## <a name="members"></a>メンバー

### <a name="namespaces"></a>名前空間

|Name|説明|
|----------|-----------------|
|[Concurrency::direct3d 名前空間](concurrency-direct3d-namespace.md)|D3D の相互運用性をサポートする関数を提供します。 AMP コードでの計算に D3D のリソースをシームレスに使用できるようになり、AMP で作成したリソースを D3D コードで使用することができ、冗長な中間コピーを作成する必要がありません。 C++ AMP を使用して、DirectX アプリケーションの計算中心のセクションの処理をインクリメントに加速し、AMP の計算から生成されるデータに対して D3D API を使用することができます。|
|[Concurrency::fast_math 名前空間](concurrency-fast-math-namespace.md)|`fast_math` 名前空間の関数は C99 に準拠していません。 各関数の各単精度のバージョンのみが用意されています。 これらの関数は DirectX 組み込み関数を使用します。これは、`precise_math` 名前空間の対応する関数よりも高速で、アクセラレータでの倍精度の拡張サポートを必要としませんが、正確さに欠けます。 C99 コードとのソース レベルの互換性のための各関数には 2 つのバージョンがあります。どちらのバージョンも単精度の値を受け取り、返します。|
|[Concurrency::graphics 名前空間](concurrency-graphics-namespace.md)|グラフィックス プログラミング用に設計された型と関数を提供します。|
|[Concurrency::precise_math 名前空間](concurrency-precise-math-namespace.md)|`precise_math` 名前空間の関数は C99 に準拠しています。 各関数の単精度バージョンと倍精度のバージョンの両方が含まれます。 単精度関数を含む、これらの関数ではアクセラレータでの倍精度の拡張サポートが必要です。|

### <a name="classes"></a>クラス

|Name|説明|
|----------|-----------------|
|[accelerator クラス](accelerator-class.md)|物理的に DP に最適化されたコンピューティング ノードの抽象化を表します。|
|[accelerator_view クラス](accelerator-view-class.md)|C ++. AMP のデータ並列アクセラレータでの仮想デバイスの抽象化を表します。|
|[accelerator_view_removed クラス](accelerator-view-removed-class.md)|基になる DirectX の呼び出しが Windows のタイムアウト検出と回復機構が原因で失敗した場合にスローされる例外。|
|[array クラス](array-class.md)|グリッド ドメインの `accelerator_view` のデータ集合体。 これは、グリッド ドメインの各要素に対して 1 つずつの変数のコレクションです。 各変数はいずれかの C++ 型に対応する値を保持します。|
|[array_view クラス](array-view-class.md)|T、N >\<配列内のデータのビューを表します。|
|[completion_future クラス](completion-future-class.md)|C++ AMP 非同期操作に対応する予定を表します。|
|[extent クラス](extent-class.md)|原点が 0 である N 次元空間の境界を指定する N 個の整数値のベクターを表します。 座標ベクターの値は最上位から最下位へ順に並べ替えられます。 たとえば、デカルトの 3 次元空間では、範囲ベクター (7,5,3) は、z 座標の範囲が 0 ～ 7、y 座標の範囲が 0 ～ 5、x 座標の範囲が 0 ～ 3 である空間を表します。|
|[index クラス](index-class.md)|N 次元のインデックス位置を定義します。|
|[invalid_compute_domain クラス](invalid-compute-domain-class.md)|ランタイムが、`parallel_for_each` 呼び出しサイトで指定された計算ドメインを使用してカーネルを起動できない場合にスローされる例外。|
|[out_of_memory クラス](out-of-memory-class.md)|システムまたはデバイスのメモリ不足のためにメソッドが失敗した場合にスローされる例外。|
|[runtime_exception クラス](runtime-exception-class.md)|C++ AMP ライブラリの例外の基本型。|
|[tile_barrier クラス](tile-barrier-class.md)|システムによってのみ作成できる機能クラスであり、`parallel_for_each` パラメーターの一部として、タイルの `tiled_index` ラムダに渡されます。 これは 1 つのメソッド、`wait()` を提供します。その目的は、スレッド グループ (タイル) で実行されるスレッドの実行を同期することです。|
|[tiled_extent クラス](tiled-extent-class.md)|`tiled_extent` オブジェクトは 3 つの次元のいずれかの `extent` オブジェクトであり、範囲空間を 1、2、または 3 次元のタイルに再分割します。|
|[tiled_index クラス](tiled-index-class.md)|`tiled_grid` オブジェクトにインデックスを提供します。 このクラスには、ローカル タイルの原点およびグローバル原点を基準として要素にアクセスするためのプロパティがあります。|
|[uninitialized_object クラス](uninitialized-object-class.md)|初期化されていないオブジェクトが使用される場合にスローされる例外です。|
|[unsupported_feature クラス](unsupported-feature-class.md)|サポートされていない機能が使用される場合にスローされる例外です。|

### <a name="enumerations"></a>列挙体

|Name|説明|
|----------|-----------------|
|[access_type 列挙型](concurrency-namespace-enums-amp.md#access_type)|データ アクセスの種類を指定します。|
|[queuing_mode 列挙型](concurrency-namespace-enums-amp.md#queuing_mode)|アクセラレータでサポートされているキュー モードを指定します。|

### <a name="operators"></a>オペレーター

|演算子|説明|
|--------------|-----------------|
|[operator = = 演算子 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_eq_eq)|指定したデータ構造が等しいかどうかを判断します。|
|[operator! = 演算子 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_neq)|指定したデータ構造が等しくないかどうかを判断します。|
|[operator + 演算子 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_add)|指定された引数の要素ごとの合計を計算します。|
|[operator-演算子 (C++ AMP)](concurrency-namespace-operators-amp.md#operator-)|指定された引数の要素ごとの差を計算します。|
|[operator * 演算子 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_star)|指定された引数の要素ごとの積を計算します。|
|[operator/演算子 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_div)|指定された引数のコンポーネントごとの商を計算します。|
|[operator% 演算子 (C++ AMP)](concurrency-namespace-operators-amp.md#operator_mod)|2 番目の指定された引数による 1 番目の指定された引数の剰余を計算します。|

### <a name="functions"></a>関数

|Name|説明|
|----------|-----------------|
|[all_memory_fence](concurrency-namespace-functions-amp.md#all_memory_fence)|すべてのメモリ アクセスが完了するまでタイルのすべてのスレッドの実行をブロックします。|
|[amp_uninitialize](concurrency-namespace-functions-amp.md#amp_uninitialize)|C++ AMP ランタイムを初期化前の状態に戻します。|
|[atomic_compare_exchange](concurrency-namespace-functions-amp.md#atomic_compare_exchange)|オーバーロードされます。 指定した位置に格納されている値が 1 番目の指定された値と同じ場合、2 番目の指定された値は分割不可能な操作として同じ位置に格納されます。|
|[atomic_exchange](concurrency-namespace-functions-amp.md#atomic_exchange)|オーバーロードされます。 指定した位置に格納された値を分割不可能な操作として指定された値に設定します。|
|[atomic_fetch_add](concurrency-namespace-functions-amp.md#atomic_fetch_add)|オーバーロードされます。 指定した位置に格納された値をその値および分割不可能な操作として指定された値の合計に設定します。|
|[atomic_fetch_and](concurrency-namespace-functions-amp.md#atomic_fetch_and)|オーバーロードされます。 指定された位置に格納されている値をその値と分割不可能な操作として指定された値のビットごとの `and` に設定します。|
|[atomic_fetch_dec](concurrency-namespace-functions-amp.md#atomic_fetch_dec)|オーバーロードされます。 指定した位置に格納されている値をデクリメントし、分割不可能な操作としてしてその結果を同じ位置に格納します。|
|[atomic_fetch_inc](concurrency-namespace-functions-amp.md#atomic_fetch_inc)|オーバーロードされます。 指定した位置に格納されている値をインクリメントし、分割不可能な操作としてその結果を同じ位置に格納します。|
|[atomic_fetch_max](concurrency-namespace-functions-amp.md#atomic_fetch_max)|オーバーロードされます。 指定された位置に格納された値を、その値および分割不可能な操作として指定された値の大きい方の値に設定します。|
|[atomic_fetch_min](concurrency-namespace-functions-amp.md#atomic_fetch_min)|オーバーロードされます。 指定された位置に格納された値をその値および分割不可能な操作として指定された値の小さい方の値に設定します。|
|[atomic_fetch_or](concurrency-namespace-functions-amp.md#atomic_fetch_or)|オーバーロードされます。 指定された位置に格納されている値をその値と分割不可能な操作として指定された値のビットごとの `or` に設定します。|
|[atomic_fetch_sub](concurrency-namespace-functions-amp.md#atomic_fetch_sub)|オーバーロードされます。 指定された位置に格納された値を、その値と分割不可能な操作として指定された値の差に設定します。|
|[atomic_fetch_xor](concurrency-namespace-functions-amp.md#atomic_fetch_xor)|オーバーロードされます。 指定された位置に格納されている値をその値と分割不可能な操作として指定された値のビットごとの `xor` に設定します。|
|[copy](concurrency-namespace-functions-amp.md#copy)|C++ AMP オブジェクトをコピーします。 すべての同期データ転送の要件が満たされます。 アクセラレータでコードを実行しているときにデータをコピーすることはできません。 この関数の一般的な形式は `copy(src, dest)` です。|
|[copy_async](concurrency-namespace-functions-amp.md#copy_async)|AMP オブジェクトC++をコピーし、待機できる[completion_future](completion-future-class.md)を返します。 アクセラレータでコードを実行しているときにデータはコピーできません。 この関数の一般的な形式は `copy(src, dest)` です。|
|[direct3d_abort](concurrency-namespace-functions-amp.md#direct3d_abort)|制限句 `restrict(amp)` がある関数の実行を中止します。|
|[direct3d_errorf](concurrency-namespace-functions-amp.md#direct3d_errorf)|書式設定された文字列を Visual Studio の**出力**ウィンドウに出力し、同じ書式指定文字列を持つ[runtime_exception](runtime-exception-class.md)の例外を発生させます。|
|[direct3d_printf](concurrency-namespace-functions-amp.md#direct3d_printf)|Visual Studio の**出力**ウィンドウに書式設定された文字列を出力します。 これは制限句 `restrict(amp)` がある関数から呼び出されます。|
|[global_memory_fence](concurrency-namespace-functions-amp.md#global_memory_fence)|すべてのグローバル メモリ アクセスが完了するまでタイルのすべてのスレッドの実行をブロックします。|
|[parallel_for_each 関数 (C++ AMP)](concurrency-namespace-functions-amp.md#parallel_for_each)|計算ドメインを越えて関数を実行します。|
|[tile_static_memory_fence](concurrency-namespace-functions-amp.md#tile_static_memory_fence)|`tile_static` メモリ アクセスが完了するまでタイルのすべてのスレッドの実行をブロックします。|

## <a name="constants"></a>定数

|Name|説明|
|----------|-----------------|
|[HLSL_MAX_NUM_BUFFERS 定数](concurrency-namespace-constants-amp.md#hlsl_max_num_buffers)|DirectX で許容される最大バッファー数。|
|[MODULENAME_MAX_LENGTH 定数](concurrency-namespace-constants-amp.md#modulename_max_length)|モジュール名の最大長を格納します。 この値は、コンパイラとランタイムで同じにする必要があります。|

## <a name="requirements"></a>［要件］

**ヘッダー:** amp.h

## <a name="see-also"></a>参照

[リファレンス (C++ AMP)](reference-cpp-amp.md)
