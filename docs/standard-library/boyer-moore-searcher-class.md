---
title: boyer_moore_searcher クラス
ms.date: 08/03/2019
f1_keywords:
- functional/std::boyer_moore_searcher
helpviewer_keywords:
- std::boyer_moore_searcher [C++]
ms.openlocfilehash: 3a6741a8ee9988a9842dea691a4ef01254872ed1
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957144"
---
# <a name="boyer_moore_searcher-class"></a>boyer_moore_searcher クラス

`boyer_moore_searcher`クラスは、オブジェクトのコンストラクターで指定されたシーケンスを検索するためにボイヤー-真人アルゴリズムを使用する関数オブジェクト型です。 検索は、オブジェクトの関数呼び出し演算子に渡された別のシーケンス内で実行されます。 このクラスは、 [std:: search](algorithm-functions.md#search)のオーバーロードのいずれかにパラメーターとして渡されます。

## <a name="syntax"></a>構文

```cpp
template <
    class RandomAccessIterator1,
    class Hash = hash<typename iterator_traits<RandomAccessIterator1>::value_type>,
    class BinaryPredicate = equal_to<>>
class boyer_moore_searcher
{
    boyer_moore_searcher(
        RandomAccessIterator1 pat_first,
        RandomAccessIterator1 pat_last,
        Hash hf = Hash(),
        BinaryPredicate pred = BinaryPredicate());

    template <class RandomAccessIterator2>
    pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
        RandomAccessIterator2 first,
        RandomAccessIterator2 last) const;
};
```

## <a name="members"></a>メンバー

| | |
| - | - |
| **コンストラクター** | |
|[boyer_moore_searcher](#boyer-moore-searcher-constructor)||
| **演算子** | |
| [演算子 ()](#operator-call) | |

## <a name="boyer-moore-searcher-constructor"></a>boyer_moore_searcher コンストラクター

検索する`boyer_moore_searcher`シーケンス、ハッシュ関数オブジェクト、および等値述語を使用して、関数オブジェクトを構築します。

```cpp
boyer_moore_searcher(
    RandomAccessIterator pat_first,
    RandomAccessIterator pat_last,
    Hash hf = Hash(),
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>パラメーター

*pat_first*\
検索するシーケンスの最初の要素。

*pat_last*\
検索するシーケンスの末尾。

*hf*\
シーケンスの要素をハッシュするために使用される呼び出し可能オブジェクト。

*pred*\
Sequence 要素のオプションの等値比較述語。 等値比較型が指定されていない`std::equal_to`場合、既定値はになります。

### <a name="remarks"></a>Remarks

*Binarypredicate*、 *Hash*、または*RandomAccessIterator*型のコピーコンストラクター、または*Binarypredicate*または*Hash*の call 演算子によってスローされた例外をスローします。

このクラスは、C++ 17 で新しく追加されたものです。

## <a name="operator-call"></a>operator ()

関数オブジェクトの呼び出し演算子。 引数シーケンス`[first, last)`内で、コンストラクターに指定されたシーケンスを検索します。

```cpp
template <class ForwardIterator2>
pair<RandomAccessIterator2, RandomAccessIterator2> operator()(
    RandomAccessIterator2 first,
    RandomAccessIterator2 last) const;
```

### <a name="parameters"></a>パラメーター

*まずは*\
検索するシーケンスの最初の要素。

*前の*\
検索するシーケンスの末尾。

### <a name="remarks"></a>Remarks

検索パターン`[pat_first, pat_last)`が空の場合、は`make_pair(first, first)`を返します。 検索パターンが見つからない場合は、 `make_pair(last, last)`を返します。 それ以外の場合は、述語`[first, last)` *pred*に`[pat_first, pat_last)`従って、に等しいシーケンスの先頭と末尾に反復子のペアを返します。

このクラスは、C++ 17 で新しく追加されたものです。

## <a name="see-also"></a>関連項目

[\<functional>](functional.md)\
[アルゴリズム関数](algorithm-functions.md)\
[boyer_moore_horspool_searcher クラス](boyer-moore-horspool-searcher-class.md)\
[std:: search](algorithm-functions.md#search)
