---
title: '&lt;hash_map&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::swap
- hash_map/std::swap (hash_map)
ms.assetid: 28748cd0-71f7-41b9-b068-579183645fba
ms.openlocfilehash: efaa960d91c69d2157896adb4612c5dd36f00cff
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448743"
---
# <a name="lthashmapgt-functions"></a>&lt;hash_map&gt; 関数

|||
|-|-|
|[swap](#swap)|[swap (hash_map)](#swap_hash_map)|

## <a name="swap_hash_map"></a>  swap (hash_map)

> [!NOTE]
> この API は、互換性のために残されています。 代わりに、[unordered_map クラス](../standard-library/unordered-map-class.md)を使用してください。

2 つの hash_map の要素を交換します。

```cpp
void swap(
    hash_map <Key, Type, Traits, Alloctor>& left,
    hash_map <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
要素が*左*のマップと交換される hash_map。

*左側*\
要素がマップ*右*の要素と交換される hash_map。

### <a name="remarks"></a>Remarks

テンプレート関数は、コンテナー クラス hash_map に特化したアルゴリズムであり、メンバー関数 `left.`[swap](../standard-library/basic-ios-class.md#swap) *(right*) を実行します。 これは、コンパイラによる関数テンプレートの部分的な順序付けのインスタンスです。 テンプレートと関数呼び出しの照合が一意にならないようにテンプレート関数がオーバーロードされた場合、コンパイラは、最も特化したバージョンのテンプレート関数を選択します。 テンプレート関数の一般的なバージョンであり、algorithm ヘッダー ファイルにある **template \<class T> void swap(T&, T&)** は、代入によって機能し、処理が低速です。 各コンテナー内の特化バージョンのほうが、コンテナー クラスの内部表現で使用できるため大幅に高速になります。

## <a name="swap"></a>  swap

> [!NOTE]
> この API は、互換性のために残されています。 代替が必要な場合は、[unordered_multimap クラス](../standard-library/unordered-multimap-class.md)をご使用ください。

2 つの hash_multimap の要素を交換します。

```cpp
void swap(
    hash_multimap <Key, Type, Traits, Alloctor>& left,
    hash_multimap <Key, Type, Traits, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
要素が*左*のマップと交換される hash_multimap。

*左側*\
要素がマップ*右*の要素と交換される hash_multimap。

### <a name="remarks"></a>Remarks

テンプレート関数は、コンテナー クラス hash_multimap に特化したアルゴリズムであり、メンバー関数 `left.`[swap](../standard-library/hash-multimap-class.md#swap) *(right*`)` を実行します。 これは、コンパイラによる関数テンプレートの部分的な順序付けのインスタンスです。 テンプレートと関数呼び出しの照合が一意にならないようにテンプレート関数がオーバーロードされた場合、コンパイラは、最も特化したバージョンのテンプレート関数を選択します。 テンプレート関数の一般的なバージョンであり、algorithm ヘッダー ファイルにある **template \<class T> void swap(T&, T&)** は、代入によって機能し、処理が低速です。 各コンテナー内の特化バージョンのほうが、コンテナー クラスの内部表現で使用できるため大幅に高速になります。

## <a name="see-also"></a>関連項目

[<hash_map>](../standard-library/hash-map.md)
