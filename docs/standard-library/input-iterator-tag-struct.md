---
title: input_iterator_tag 構造体
ms.date: 11/04/2016
f1_keywords:
- xutility/std::input_iterator_tag
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
ms.openlocfilehash: 47e0d08f79cfa41c414ac4fcd570ce8fdfbd0b35
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455313"
---
# <a name="input_iterator_tag-struct"></a>input_iterator_tag 構造体

入力反復子を表す関数の`iterator_category`戻り値の型を提供するクラス。

## <a name="syntax"></a>構文

struct input_iterator_tag {};

## <a name="remarks"></a>Remarks

カテゴリ タグ クラスはアルゴリズムの選択にコンパイル タグとして使用されます。 テンプレート関数は、コンパイル時に最も効率的なアルゴリズムを利用できるように、その反復子引数の最も具体的なカテゴリを見つける必要があります。 `Iterator` 型の反復子ごとに、反復子の動作を表す最も具体的なカテゴリ タグとして `iterator_traits`< `Iterator`>  **::iterator_category** を定義する必要があります。

型は、が入力反復子として使用できる`Iter`オブジェクトを表す場合に、**反復子**\< **Iter**>  **:: iterator_category**と同じです。

## <a name="example"></a>例

の使用`iterator_tag`方法の例については、「[iterator_traits](../standard-library/iterator-traits-struct.md) or [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) 」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<iterator>

**名前空間:** std

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
