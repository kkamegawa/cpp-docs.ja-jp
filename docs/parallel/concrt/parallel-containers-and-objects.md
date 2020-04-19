---
title: 並列コンテナーと並列オブジェクト
ms.date: 03/27/2019
helpviewer_keywords:
- parallel objects
- parallel containers
- concurrent containers
ms.assetid: 90ab715c-29cd-48eb-8e76-528619aab466
ms.openlocfilehash: 04b38fdc66a5c37a1780deaae4ae165f63238d93
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142900"
---
# <a name="parallel-containers-and-objects"></a>並列コンテナーと並列オブジェクト

並列パターンライブラリ (PPL) には、要素へのスレッドセーフなアクセスを提供するいくつかのコンテナーとオブジェクトが含まれています。

*同時実行コンテナー*は、最も重要な操作への同時実行セーフアクセスを提供します。 ここでは、同時実行セーフとは、ポインターまたは反復子が常に有効であることを意味します。 これは、要素の初期化、または特定のトラバーサルの順序の保証ではありません。 これらのコンテナーの機能は、 C++標準ライブラリに用意されているものと似ています。 たとえば、 [concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)クラスは[std:: vector](../../standard-library/vector-class.md)クラスに似ていますが、`concurrent_vector` クラスを使用すると、要素を並行して追加することができます。 同時実行コンテナーは、同じコンテナーに対する読み取りと書き込みの両方のアクセスを必要とする並列コードがある場合に使用します。

*同時実行オブジェクト*は、コンポーネント間で同時に共有されます。 同時実行オブジェクトの状態を並行して計算するプロセスでは、同じ状態を直列に計算する別のプロセスと同じ結果が生成されます。 [Concurrency:: 組み合わせ](../../parallel/concrt/reference/combinable-class.md)可能クラスは、同時実行オブジェクト型の一例です。 `combinable` クラスを使用すると、計算を並列に実行し、その計算を最終結果に結合できます。 ミューテックスなどの同期メカニズムを使用して共有変数またはリソースへのアクセスを同期する場合は、同時実行オブジェクトを使用します。

## <a name="top"></a> セクション

このトピックでは、次の並列コンテナーとオブジェクトについて詳しく説明します。

同時実行コンテナー:

- [concurrent_vector クラス](#vector)

   - [Concurrent_vector と vector の違い](#vector-differences)

   - [同時実行セーフな操作](#vector-safety)

   - [例外の安全性](#vector-exceptions)

- [concurrent_queue クラス](#queue)

   - [Concurrent_queue とキューの違い](#queue-differences)

   - [同時実行セーフな操作](#queue-safety)

   - [反復子のサポート](#queue-iterators)

- [concurrent_unordered_map クラス](#unordered_map)

   - [Concurrent_unordered_map と unordered_map の違い](#map-differences)

   - [同時実行セーフな操作](#map-safety)

- [concurrent_unordered_multimap クラス](#unordered_multimap)

- [concurrent_unordered_set クラス](#unordered_set)

- [concurrent_unordered_multiset クラス](#unordered_multiset)

同時実行オブジェクト:

- [combinable クラス](#combinable)

   - [メソッドと機能](#combinable-features)

   - [使用例](#combinable-examples)

## <a name="vector"></a>concurrent_vector クラス

[Concurrency:: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md)クラスは、 [std:: vector](../../standard-library/vector-class.md)クラスと同様に、要素にランダムにアクセスできるようにするシーケンスコンテナークラスです。 `concurrent_vector` クラスを使用すると、同時実行セーフな append および element アクセス操作が可能になります。 追加操作によって、既存のポインターまたは反復子が無効になることはありません。 反復子アクセスおよび走査操作も同時実行セーフです。 ここでは、同時実行セーフとは、ポインターまたは反復子が常に有効であることを意味します。 これは、要素の初期化、または特定のトラバーサルの順序の保証ではありません。

### <a name="vector-differences"></a>Concurrent_vector と vector の違い

`concurrent_vector` クラスは、`vector` クラスによく似ています。 `concurrent_vector` オブジェクトに対する追加、要素アクセス、反復子アクセス操作の複雑さは、`vector` オブジェクトの場合と同じです。 次の点は、`vector`と `concurrent_vector` が異なる場所を示しています。

- `concurrent_vector` オブジェクトに対する追加、要素アクセス、反復子アクセス、および反復子の走査操作は、同時実行セーフです。

- 要素を追加できるのは、`concurrent_vector` オブジェクトの末尾だけです。 `concurrent_vector` クラスでは、`insert` メソッドは提供されません。

- `concurrent_vector` オブジェクトは、にを追加するときに[移動セマンティクス](../../cpp/rvalue-reference-declarator-amp-amp.md)を使用しません。

- `concurrent_vector` クラスは、`erase` または `pop_back` メソッドを提供しません。 `vector`と同様に、 [clear](reference/concurrent-vector-class.md#clear)メソッドを使用して、`concurrent_vector` オブジェクトからすべての要素を削除します。

- `concurrent_vector` クラスは、その要素をメモリ内に連続して格納しません。 したがって、配列を使用するすべての方法で `concurrent_vector` クラスを使用することはできません。 たとえば、`concurrent_vector`型の `v` という名前の変数の場合、式 `&v[0]+2` によって未定義の動作が生成されます。

- `concurrent_vector` クラスは、 [grow_by](reference/concurrent-vector-class.md#grow_by)メソッドと[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)メソッドを定義します。 これらのメソッドは、同時実行セーフである点を除いて、 [resize](reference/concurrent-vector-class.md#resize)メソッドに似ています。

- `concurrent_vector` オブジェクトは、追加時またはサイズ変更時に要素を再配置しません。 これにより、既存のポインターと反復子を同時操作中に有効なままにすることができます。

- ランタイムは、型 `bool`に対して特殊化されたバージョンの `concurrent_vector` を定義していません。

### <a name="vector-safety"></a>同時実行セーフな操作

`concurrent_vector` オブジェクトのサイズを追加または拡大するメソッド、または `concurrent_vector` オブジェクト内の要素にアクセスするすべてのメソッドは、同時実行セーフです。 ここでは、同時実行セーフとは、ポインターまたは反復子が常に有効であることを意味します。 これは、要素の初期化、または特定のトラバーサルの順序の保証ではありません。 この規則の例外は、`resize` メソッドです。

次の表は、同時実行セーフである一般的な `concurrent_vector` メソッドと演算子を示しています。

||||
|-|-|-|
|[at](reference/concurrent-vector-class.md#at)|[end](reference/concurrent-vector-class.md#end)|[operator&#91;&#93;](reference/concurrent-vector-class.md#operator_at)|
|[begin](reference/concurrent-vector-class.md#begin)|[front](reference/concurrent-vector-class.md#front)|[push_back](reference/concurrent-vector-class.md#push_back)|
|[back](reference/concurrent-vector-class.md#back)|[grow_by](reference/concurrent-vector-class.md#grow_by)|[rbegin](reference/concurrent-vector-class.md#rbegin)|
|[capacity](reference/concurrent-vector-class.md#capacity)|[grow_to_at_least](reference/concurrent-vector-class.md#grow_to_at_least)|[rend](reference/concurrent-vector-class.md#rend)|
|[empty](reference/concurrent-vector-class.md#empty)|[max_size](reference/concurrent-vector-class.md#max_size)|[size](reference/concurrent-vector-class.md#size)|

C++標準ライブラリとの互換性のためにランタイムによって提供される操作 (`reserve`など) は、同時実行セーフではありません。 次の表は、同時実行セーフではない共通のメソッドと演算子を示しています。

|||
|-|-|
|[assign](reference/concurrent-vector-class.md#assign)|[reserve](reference/concurrent-vector-class.md#reserve)|
|[オフ](reference/concurrent-vector-class.md#clear)|[resize](reference/concurrent-vector-class.md#resize)|
|[operator=](reference/concurrent-vector-class.md#operator_eq)|[shrink_to_fit](reference/concurrent-vector-class.md#shrink_to_fit)|

既存の要素の値を変更する操作は、同時実行セーフではありません。 [Reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)オブジェクトなどの同期オブジェクトを使用して、同時実行の読み取り操作と書き込み操作を同じデータ要素に同期します。 同期オブジェクトの詳細については、「[同期データ構造](../../parallel/concrt/synchronization-data-structures.md)」を参照してください。

`vector` を使用する既存のコードを変換して `concurrent_vector`を使用すると、同時実行操作によってアプリケーションの動作が変更される可能性があります。 たとえば、`concurrent_vector` オブジェクトに対して2つのタスクを同時に実行する次のプログラムについて考えてみます。 最初のタスクは、`concurrent_vector` オブジェクトに要素を追加します。 2番目のタスクは、同じオブジェクト内のすべての要素の合計を計算します。

[!code-cpp[concrt-vector-safety#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_1.cpp)]

`end` メソッドは同時実行セーフですが、 [push_back](reference/concurrent-vector-class.md#push_back)メソッドを同時に呼び出すと、`end` によって返される値が変更されます。 反復子が走査する要素の数は不確定です。 このため、このプログラムを実行するたびに、異なる結果が生成される可能性があります。 要素の型が重要でない場合、`push_back` と `end` の呼び出しの間に競合状態が存在する可能性があります。 `end` メソッドは、割り当てられているが完全には初期化されていない要素を返す場合があります。

### <a name="vector-exceptions"></a>例外の安全性

拡張操作または割り当て操作によって例外がスローされた場合、`concurrent_vector` オブジェクトの状態は無効になります。 無効な状態にある `concurrent_vector` オブジェクトの動作は、特に明記されていない限り、定義されていません。 ただし、デストラクターは、オブジェクトが無効な状態にある場合でも、オブジェクトが割り当てたメモリを常に解放します。

Vector 要素のデータ型 `T`は、次の要件を満たしている必要があります。 それ以外の場合、`concurrent_vector` クラスの動作は定義されていません。

- デストラクターは、をスローすることはできません。

- 既定のコンストラクターまたはコピーコンストラクターがをスローした場合、デストラクターは `virtual` キーワードを使用して宣言する必要がなく、ゼロ初期化されたメモリで正しく動作する必要があります。

[[トップ](#top)]

## <a name="queue"></a>concurrent_queue クラス

[Concurrency:: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md)クラスは、 [std:: queue](../../standard-library/queue-class.md)クラスと同様に、front 要素と back 要素にアクセスすることができます。 `concurrent_queue` クラスは、同時実行セーフなエンキュー操作とデキュー操作を可能にします。 ここでは、同時実行セーフとは、ポインターまたは反復子が常に有効であることを意味します。 これは、要素の初期化、または特定のトラバーサルの順序の保証ではありません。 `concurrent_queue` クラスでは、同時実行セーフではない反復子のサポートも提供されます。

### <a name="queue-differences"></a>Concurrent_queue とキューの違い

`concurrent_queue` クラスは、`queue` クラスによく似ています。 次の点は、`queue`と `concurrent_queue` が異なる場所を示しています。

- `concurrent_queue` オブジェクトでのエンキュー操作とデキュー操作は、同時実行セーフです。

- `concurrent_queue` クラスは、同時実行セーフではない反復子のサポートを提供します。

- `concurrent_queue` クラスは、`front` または `pop` メソッドを提供しません。 `concurrent_queue` クラスは、 [try_pop](reference/concurrent-queue-class.md#try_pop)メソッドを定義することで、これらのメソッドを置き換えます。

- `concurrent_queue` クラスでは、`back` メソッドは提供されません。 したがって、キューの末尾を参照することはできません。

- `concurrent_queue` クラスは、`size` メソッドではなく、 [unsafe_size](reference/concurrent-queue-class.md#unsafe_size)メソッドを提供します。 `unsafe_size` メソッドは同時実行セーフではありません。

### <a name="queue-safety"></a>同時実行セーフな操作

`concurrent_queue` オブジェクトに対してエンキューまたはデキューを行うすべてのメソッドは、同時実行セーフです。 ここでは、同時実行セーフとは、ポインターまたは反復子が常に有効であることを意味します。 これは、要素の初期化、または特定のトラバーサルの順序の保証ではありません。

次の表は、同時実行セーフである一般的な `concurrent_queue` メソッドと演算子を示しています。

|||
|-|-|
|[empty](reference/concurrent-queue-class.md#empty)|[push](reference/concurrent-queue-class.md#push)|
|[get_allocator](reference/concurrent-queue-class.md#get_allocator)|[try_pop](reference/concurrent-queue-class.md#try_pop)|

`empty` メソッドは同時実行セーフですが、同時実行操作によって、`empty` メソッドから制御が戻る前にキューが拡大または縮小される場合があります。

次の表は、同時実行セーフではない共通のメソッドと演算子を示しています。

|||
|-|-|
|[オフ](reference/concurrent-queue-class.md#clear)|[unsafe_end](reference/concurrent-queue-class.md#unsafe_end)|
|[unsafe_begin](reference/concurrent-queue-class.md#unsafe_begin)|[unsafe_size](reference/concurrent-queue-class.md#unsafe_size)|

### <a name="queue-iterators"></a>反復子のサポート

`concurrent_queue` は、同時実行セーフではない反復子を提供します。 これらの反復子は、デバッグのためにのみ使用することをお勧めします。

`concurrent_queue` 反復子は、前方方向にのみ要素をトラバースします。 次の表は、各反復子がサポートする演算子を示しています。

|演算子|説明|
|--------------|-----------------|
|`operator++`|キューの次の項目に進みます。 この演算子は、前置インクリメントと後置の両方のセマンティクスを提供するためにオーバーロードされています。|
|`operator*`|現在の項目への参照を取得します。|
|`operator->`|現在の項目へのポインターを取得します。|

[[トップ](#top)]

## <a name="unordered_map"></a>concurrent_unordered_map クラス

[Concurrency:: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)クラスは、 [std:: unordered_map](../../standard-library/unordered-map-class.md)クラスと同様に、 [std::p Air\<const キー、Ty >](../../standard-library/pair-structure.md)型の要素の可変長シーケンスを制御する連想コンテナークラスです。 順序なしのマップは、キーと値のペアを追加したり、キーで値を参照したりできるディクショナリと考えることができます。 このクラスは、共有コンテナーに同時にアクセスしたり、それに挿入したり、更新したりする必要がある複数のスレッドまたはタスクがある場合に便利です。

次の例は、`concurrent_unordered_map`を使用するための基本的な構造を示しています。 この例では、[' a ', ' i '] の範囲内に文字キーを挿入します。 操作の順序は不明であるため、各キーの最終的な値も不定になります。 ただし、挿入を並列で実行するのは安全です。

[!code-cpp[concrt-unordered-map-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_2.cpp)]

`concurrent_unordered_map` を使用して map および reduce 操作を並列で実行する例については、「[方法: マップ操作と縮小操作を並列実行](../../parallel/concrt/how-to-perform-map-and-reduce-operations-in-parallel.md)する」を参照してください。

### <a name="map-differences"></a>Concurrent_unordered_map と unordered_map の違い

`concurrent_unordered_map` クラスは、`unordered_map` クラスによく似ています。 次の点は、`unordered_map`と `concurrent_unordered_map` が異なる場所を示しています。

- `erase`、`bucket`、`bucket_count`、および `bucket_size` の各メソッドには、それぞれ `unsafe_erase`、`unsafe_bucket`、`unsafe_bucket_count`、および `unsafe_bucket_size`という名前が付けられています。 `unsafe_` 名前付け規則は、これらのメソッドが同時実行セーフでないことを示します。 同時実行の安全性の詳細については、「[同時実行セーフの操作](#map-safety)」を参照してください。

- 挿入操作では、既存のポインターまたは反復子を無効にしたり、マップ内に既に存在する項目の順序を変更したりすることはできません。 挿入操作と走査操作は同時に実行できます。

- `concurrent_unordered_map` は、転送イテレーションのみをサポートしています。

- 挿入は、`equal_range`によって返される反復子を無効にしたり、更新したりすることはありません。 挿入では、範囲の末尾に不等の項目を追加できます。 Begin 反復子が等しい項目を指しています。

デッドロックを回避するために、メモリアロケーター、ハッシュ関数、またはその他のユーザー定義コードを呼び出すときに、`concurrent_unordered_map` のメソッドがロックを保持することはありません。 また、ハッシュ関数が同じ値に対して同じキーを常に評価する必要があります。 最適なハッシュ関数は、ハッシュコード空間全体でキーを均等に分散します。

### <a name="map-safety"></a>同時実行セーフな操作

`concurrent_unordered_map` クラスを使用すると、同時実行セーフな挿入操作と要素アクセス操作が可能になります。 挿入操作では、既存のポインターまたは反復子は無効になりません。 反復子アクセスおよび走査操作も同時実行セーフです。 ここでは、同時実行セーフとは、ポインターまたは反復子が常に有効であることを意味します。 これは、要素の初期化、または特定のトラバーサルの順序の保証ではありません。 次の表は、同時実行セーフである `concurrent_unordered_map` のメソッドと演算子を示しています。

|||||
|-|-|-|-|
|[at](reference/concurrent-unordered-map-class.md#at)|`count`|`find`|[key_eq](reference/concurrent-unordered-map-class.md#key_eq)|
|`begin`|`empty`|`get_allocator`|`max_size`|
|`cbegin`|`end`|`hash_function`|[operator&#91;&#93;](reference/concurrent-unordered-map-class.md#operator_at)|
|`cend`|`equal_range`|[insert](reference/concurrent-unordered-map-class.md#insert)|`size`|

`count` メソッドは同時に実行されるスレッドから安全に呼び出すことができますが、新しい値が同時にコンテナーに挿入されると、異なるスレッドが異なる結果を受け取ることがあります。

次の表は、同時実行セーフではない一般的に使用されるメソッドと演算子を示しています。

||||
|-|-|-|
|`clear`|`max_load_factor`|`rehash`|
|`load_factor`|[operator=](reference/concurrent-unordered-map-class.md#operator_eq)

これらのメソッドに加えて、`unsafe_` で始まるメソッドも同時実行セーフではありません。

[[トップ](#top)]

## <a name="unordered_multimap"></a>concurrent_unordered_multimap クラス

[Concurrency:: concurrent_unordered_multimap](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)クラスは、複数の値が同じキーにマップされることを除いて、`concurrent_unordered_map` クラスに似ています。 また、`concurrent_unordered_map` と次の点で異なります。

- [Concurrent_unordered_multimap:: insert](reference/concurrent-unordered-multimap-class.md#insert)メソッドは、`std::pair<iterator, bool>`ではなく反復子を返します。

- `concurrent_unordered_multimap` クラスは `operator[]` と `at` メソッドを提供しません。

次の例は、`concurrent_unordered_multimap`を使用するための基本的な構造を示しています。 この例では、[' a ', ' i '] の範囲内に文字キーを挿入します。 `concurrent_unordered_multimap` を使用すると、キーに複数の値を設定できます。

[!code-cpp[concrt-unordered-multimap-structure#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_3.cpp)]

[[トップ](#top)]

## <a name="unordered_set"></a>concurrent_unordered_set クラス

[Concurrency:: concurrent_unordered_set](../../parallel/concrt/reference/concurrent-unordered-set-class.md)クラスは `concurrent_unordered_map` クラスによく似ていますが、キーと値のペアの代わりに値を管理する点が異なります。 `concurrent_unordered_set` クラスは `operator[]` と `at` メソッドを提供しません。

次の例は、`concurrent_unordered_set`を使用するための基本的な構造を示しています。 この例では、[' a ', ' i '] の範囲内に文字値を挿入します。 挿入は並行して実行するのが安全です。

[!code-cpp[concrt-unordered-set#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_4.cpp)]

[[トップ](#top)]

## <a name="unordered_multiset"></a>concurrent_unordered_multiset クラス

[Concurrency:: concurrent_unordered_multiset](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)クラスは `concurrent_unordered_set` クラスに似ていますが、重複する値が許可されている点が異なります。 また、`concurrent_unordered_set` と次の点で異なります。

- [Concurrent_unordered_multiset:: insert](reference/concurrent-unordered-multiset-class.md#insert)メソッドは、`std::pair<iterator, bool>`ではなく反復子を返します。

- `concurrent_unordered_multiset` クラスは `operator[]` と `at` メソッドを提供しません。

次の例は、`concurrent_unordered_multiset`を使用するための基本的な構造を示しています。 この例では、[' a ', ' i '] の範囲内に文字値を挿入します。 `concurrent_unordered_multiset` を使用すると、値を複数回実行できます。

[!code-cpp[concrt-unordered-multiset#1](../../parallel/concrt/codesnippet/cpp/parallel-containers-and-objects_5.cpp)]

[[トップ](#top)]

## <a name="combinable"></a>組み合わせ可能クラス

[Concurrency:: 組み合わせ](../../parallel/concrt/reference/combinable-class.md)可能クラスは、再利用可能なスレッドローカルストレージを提供します。これにより、きめ細かな計算を実行し、その計算を最終結果にマージできます。 `combinable` オブジェクトは減少変数と考えることができます。

`combinable` クラスは、複数のスレッドまたはタスク間で共有されるリソースがある場合に便利です。 `combinable` クラスは、ロックを使用しない方法で共有リソースへのアクセスを提供することで、共有状態を排除するのに役立ちます。 したがって、このクラスは、複数のスレッドからの共有データへのアクセスを同期するために、ミューテックスなどの同期機構を使用する代わりに使用できます。

### <a name="combinable-features"></a>メソッドと機能

次の表は、`combinable` クラスの重要なメソッドの一部を示しています。 `combinable` クラスのすべてのメソッドの詳細については、「組み合わせ可能な[クラス](../../parallel/concrt/reference/combinable-class.md)」を参照してください。

|方法|説明|
|------------|-----------------|
|[local](reference/combinable-class.md#local)|現在のスレッドコンテキストに関連付けられているローカル変数への参照を取得します。|
|[オフ](reference/combinable-class.md#clear)|`combinable` オブジェクトからすべてのスレッドローカル変数を削除します。|
|[combine](reference/combinable-class.md#combine)<br /><br /> [combine_each](reference/combinable-class.md#combine_each)|指定された結合関数を使用して、すべてのスレッドローカル計算のセットから最終的な値を生成します。|

`combinable` クラスは、最終的にマージされた結果に対してパラメーター化されるテンプレートクラスです。 既定のコンストラクターを呼び出す場合、`T` テンプレートパラメーター型には、既定のコンストラクターとコピーコンストラクターが必要です。 `T` テンプレートパラメーターの型に既定のコンストラクターがない場合は、初期化関数をパラメーターとして受け取るコンストラクターのオーバーロードされたバージョンを呼び出します。

[結合](reference/combinable-class.md#combine)メソッドまたは[combine_each](reference/combinable-class.md#combine_each)メソッドを呼び出した後、`combinable` オブジェクトに追加のデータを格納できます。 `combine` と `combine_each` メソッドを複数回呼び出すこともできます。 `combinable` オブジェクトのローカル値が変更されていない場合、`combine` メソッドと `combine_each` メソッドは、呼び出されるたびに同じ結果を生成します。

### <a name="combinable-examples"></a> 例

`combinable` クラスの使用方法の例については、次のトピックを参照してください。

- [方法: combinable を使用してパフォーマンスを向上させる](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)

- [方法: combinable を使用して集合を結合する](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)

[[トップ](#top)]

## <a name="related-topics"></a>関連トピック

[方法: 並列コンテナーを使用して効率を向上させる](../../parallel/concrt/how-to-use-parallel-containers-to-increase-efficiency.md)<br/>
並列コンテナーを使用してデータを並列に効率的に格納およびアクセスする方法を示します。

[方法: combinable を使用してパフォーマンスを向上させる](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md)<br/>
`combinable` クラスを使用して共有状態を排除し、パフォーマンスを向上させる方法について説明します。

[方法: combinable を使用して集合を結合する](../../parallel/concrt/how-to-use-combinable-to-combine-sets.md)<br/>
`combine` 関数を使用して、スレッドローカルデータのセットをマージする方法について説明します。

[並列パターン ライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
PPL について説明します。これは、同時実行アプリケーションを開発するためのスケーラビリティと使いやすさを促進する命令型プログラミングモデルを提供します。

## <a name="reference"></a>辞書／辞典／その他

[concurrent_vector クラス](../../parallel/concrt/reference/concurrent-vector-class.md)

[concurrent_queue クラス](../../parallel/concrt/reference/concurrent-queue-class.md)

[concurrent_unordered_map クラス](../../parallel/concrt/reference/concurrent-unordered-map-class.md)

[concurrent_unordered_multimap クラス](../../parallel/concrt/reference/concurrent-unordered-multimap-class.md)

[concurrent_unordered_set クラス](../../parallel/concrt/reference/concurrent-unordered-set-class.md)

[concurrent_unordered_multiset クラス](../../parallel/concrt/reference/concurrent-unordered-multiset-class.md)

[combinable クラス](../../parallel/concrt/reference/combinable-class.md)
