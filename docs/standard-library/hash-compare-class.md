---
title: hash_compare クラス
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_compare
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
ms.openlocfilehash: 4fb44a371630a66275f6ef59a0bf66b4cb73a71f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689557"
---
# <a name="hash_compare-class"></a>hash_compare クラス

クラステンプレートは、ハッシュ連想コンテナー (hash_map、hash_multimap、hash_set、または hash_multiset) のいずれかで使用できるオブジェクトを表します。このオブジェクトには、含まれる要素の順序付けとハッシュを行う既定の**特徴**パラメーターオブジェクトとして使用できます。

## <a name="syntax"></a>構文

class hash_compare { Traits comp; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare(Traits pred); size_t operator()(const Key& key) const; bool operator()( const Key& key1, const Key& key2) const; };

## <a name="remarks"></a>Remarks

各ハッシュ連想コンテナーには、`Traits` 型のハッシュ特性オブジェクト (テンプレートパラメーター) が格納されます。 特定の関数とオブジェクトを選択的にオーバーライドするために hash_compare を特殊化してクラスを派生させるか、特定の最小要件を満たしているこのクラスの独自のバージョンを使用することができます。 具体的には、`hash_compare<Key, Traits>` 型のオブジェクト hash_comp の場合、上記のコンテナーでは次の動作が必要です。

- @No__t_1 型の `key` すべての値について、call **hash_comp**(`key`) はハッシュ関数として機能し、`size_t` 型の値の分布を生成します。 hash_compare によって提供される関数は `key` を返します。

- シーケンス内の `key2` の前にあり、同じハッシュ値 (ハッシュ関数によって返される値) を持つ `Key` 型の値 `key1` の場合、 **hash_comp**(`key2`、`key1`) は false になります。 関数は `Key` 型の値の合計の順序を強制する必要があります。 Hash_compare によって提供される関数は、 *comp*(`key2`, `key1`) `,` を返します。ここで、 *comp*は、オブジェクト hash_comp を構築するときに指定できる `Traits` 型の格納されたオブジェクトです。 既定の `Traits` パラメーターの型 `less<Key>` では、並べ替えキーの値が減少することはありません。

- コンテナーが超えないようにする必要がある "バケット" (ハッシュテーブルのエントリ) ごとの要素の平均数を指定する整数の定数 `bucket_size`。 0 より大きくなければなりません。 hash_compare によって提供される値は 4 です。

- ハッシュテーブルで保持するバケットの最小数を指定する整数定数 `min_buckets`。 2 の累乗で、0 より大きくなければなりません。 hash_compare によって提供される値は 8 です。

## <a name="example"></a>例

hash_compare の宣言方法や使用方法の例については、[hash_map::hash_map](../standard-library/hash-map-class.md#hash_map)[hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap)[hash_set::hash_set](../standard-library/hash-set-class.md#hash_set)および [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset) の例をご覧ください。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<hash_map>

**名前空間:** stdext

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
