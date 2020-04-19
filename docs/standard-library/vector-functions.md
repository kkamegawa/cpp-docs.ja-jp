---
title: '&lt;vector&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- vector/std::swap
ms.assetid: 6cdcf043-eef6-4330-83f0-4596fb9f968a
helpviewer_keywords:
- std::swap [vector]
ms.openlocfilehash: cdf67b3cb34546f5d0dfcd9a4f3bd96500c18af9
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68241034"
---
# <a name="ltvectorgt-functions"></a>&lt;vector&gt; 関数

## <a name="swap"></a> スワップ

2 つのベクターの要素を交換します。

```cpp
template <class Type, class Allocator>
void swap(vector<Type, Allocator>& left, vector<Type, Allocator>& right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
交換する要素を提供するベクター、または要素のベクターと交換するベクター*左*します。

*左*\
要素のベクターと交換するベクター*右*します。

### <a name="remarks"></a>Remarks

テンプレート関数はメンバー関数の実行に、コンテナー クラス ベクターに特化したアルゴリズム`left`します。 [vector::swap](../standard-library/vector-class.md) *(右*)。 これらは、コンパイラによる関数テンプレートの部分的な順序付けのインスタンスです。 テンプレートと関数呼び出しの照合が一意にならないようにテンプレート関数がオーバーロードされた場合、コンパイラは、最も特化したバージョンのテンプレート関数を選択します。 テンプレート関数の一般的なバージョンであり、algorithm クラスにある **template** \< **class T**> **void swap**(**T&** , **T&** ) は、代入によって機能し、処理が低速です。 各コンテナー内の特化バージョンのほうが、コンテナー クラスの内部表現で使用できるため大幅に高速になります。

### <a name="example"></a>例

テンプレート バージョンの `swap` の使用例については、メンバー関数 [vector::swap](../standard-library/vector-class.md) のコード例をご覧ください。
