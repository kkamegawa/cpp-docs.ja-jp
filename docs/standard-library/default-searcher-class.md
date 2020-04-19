---
title: default_searcher クラス
ms.date: 08/03/2019
f1_keywords:
- functional/std::default_searcher
helpviewer_keywords:
- std::default_searcher [C++]
ms.openlocfilehash: f2b1fe83b5223bbb60e9e32149c101e6379f93c3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "68268824"
---
# <a name="default_searcher-class"></a>default_searcher クラス

`default_searcher`は、オブジェクトのコンストラクターで指定されたシーケンスを検索する操作の関数オブジェクト型です。 検索は、オブジェクトの関数呼び出し演算子に渡された別のシーケンス内で実行されます。 は`default_searcher` 、 [std:: search](algorithm-functions.md#search)を呼び出して検索を実行します。

## <a name="syntax"></a>構文

```cpp
template <class ForwardIterator, class BinaryPredicate = equal_to<>>
class default_searcher
{
    default_searcher(
        ForwardIterator pat_first,
        ForwardIterator pat_last,
        BinaryPredicate pred = BinaryPredicate());

    template <class ForwardIterator2>
    pair<ForwardIterator2, ForwardIterator2> operator()(
        ForwardIterator2 first,
        ForwardIterator2 last) const;
};
```

## <a name="members"></a>メンバー

| | |
| - | - |
| **コンストラクター** | |
| [default_searcher](#default-searcher-constructor) | |
| **演算子** | |
| [演算子 ()](#operator-call) | |

## <a name="default-searcher-constructor"></a>default_searcher コンストラクター

検索する`default_searcher`シーケンスと等値述語を使用して、関数オブジェクトを構築します。

```cpp
default_searcher(                   // C++17
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());

constexpr default_searcher(         // C++20
    ForwardIterator pat_first,
    ForwardIterator pat_last,
    BinaryPredicate pred = BinaryPredicate());
```

### <a name="parameters"></a>パラメーター

*pat_first*\
検索するシーケンスの最初の要素。

*pat_last*\
検索するシーケンスの末尾。

*pred*\
Sequence 要素のオプションの等値比較述語。 等値比較型が指定されていない`std::equal_to`場合、既定値はになります。

### <a name="remarks"></a>Remarks

*Binarypredicate*型または*ForwardIterator*型のコピーコンストラクターによってスローされた例外をスローします。

このクラスは、C++ 17 で新しく追加されたものです。 C++ 20 によって`constexpr`コンストラクターが作成されました。

## <a name="operator-call"></a>operator ()

関数演算子の呼び出し演算子。 引数シーケンス`[first, last)`内で、コンストラクターに指定されたシーケンスを検索します。

```cpp
template <class ForwardIterator2>   // C++17
pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;

template <class ForwardIterator2>   // C++20
constexpr pair<ForwardIterator2, ForwardIterator2> operator()(
    ForwardIterator2 first,
    ForwardIterator2 last) const;
```

### <a name="parameters"></a>パラメーター

*まずは*\
検索するシーケンスの最初の要素。

*前の*\
検索するシーケンスの末尾。

### <a name="remarks"></a>Remarks

反復子のペアを返します。 最初の反復子*i*は、次のような結果になります。

`std::search( first, last, pat_first, pat_last, pred )`。

ペアの2番目の反復子は、 *i** が*last*の場合は*last*です。 それ以外の場合は、次のような結果になります。

`std::next( i, std::distance( pat_first, pat_last ))`。

このクラスは、C++ 17 で新しく追加されたものです。 C++ 20 は呼び出し演算子`constexpr`を作成しました。

## <a name="see-also"></a>関連項目

[\<functional>](functional.md)\
[アルゴリズム関数](algorithm-functions.md)\
[std:: search](algorithm-functions.md#search)
