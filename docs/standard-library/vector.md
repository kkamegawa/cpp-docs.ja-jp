---
title: '&lt;vector&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 19068de41cfdcb17ae624858c137bf624851479f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72684064"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

コンテナークラステンプレートベクターといくつかのサポートテンプレートを定義します。

`vector` 指定された型の要素を直線上のシーケンスに編成するコンテナーです。 このシーケンスでは、任意の要素を高速にランダム アクセスしたり、動的に追加および削除したりできます。 `vector` は、ランダム アクセスのパフォーマンスを重視するシーケンスに適したコンテナーです。

> [!NOTE]
> @No__t_0vector > ライブラリでは、`#include <initializer_list>` ステートメントも使用します。

クラス `vector` の詳細については、「[vector クラス](../standard-library/vector-class.md)」をご覧ください。 特殊化 `vector<bool>` の詳細については、「[vector\<bool> クラス](../standard-library/vector-bool-class.md)」をご覧ください。

## <a name="syntax"></a>構文

```cpp
namespace std {
template <class Type, class Allocator>
class vector;
template <class Allocator>
class vector<bool>;

template <class Allocator>
struct hash<vector<bool, Allocator>>;

// TEMPLATE FUNCTIONS
template <class Type, class Allocator>
bool operator== (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator!= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<(
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator> (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator>= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
void swap (
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>パラメーター

*型*\
ベクター内に格納されるデータ型に対するテンプレート パラメーター。

*アロケーター* \
メモリの割り当てと解放を担当する格納されたアロケーター オブジェクトのテンプレート パラメーター。

*左*\
比較演算の最初の (左辺の) ベクター

*右*\
比較演算の 2 つ目の (右辺の) ベクター。

## <a name="members"></a>メンバー

### <a name="operators"></a>演算子

|||
|-|-|
|[operator! =](../standard-library/vector-operators.md#op_neq)|演算子の左辺のベクター オブジェクトが右辺のベクター オブジェクトと等しくないかどうかを調べます。|
|[operator<](../standard-library/vector-operators.md#op_lt)|演算子の左辺のベクター オブジェクトが右辺のベクター オブジェクトより小さいかどうかを調べます。|
|[operator\<=](../standard-library/vector-operators.md#op_gt_eq)|演算子の左辺のベクター オブジェクトが右辺のベクター オブジェクト以下かどうかを調べます。|
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|演算子の左辺のベクター オブジェクトが右辺のベクター オブジェクトと等しいかどうかを調べます。|
|[operator>](../standard-library/vector-operators.md#op_gt)|演算子の左辺のベクター オブジェクトが右辺のベクター オブジェクトより大きいかどうかを調べます。|
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|演算子の左辺のベクター オブジェクトが右辺のベクター オブジェクト以上かどうかを調べます。|

### <a name="classes"></a>クラス

|||
|-|-|
|[vector クラス](../standard-library/vector-class.md)|指定された型の要素を直線上に配置し、任意の要素に対する高速なランダム アクセスを可能にするシーケンス コンテナーのクラス テンプレートです。|

### <a name="specializations"></a>特殊化

|||
|-|-|
|hash|ベクターのハッシュを返します。|
|[vector\<bool> クラス](../standard-library/vector-bool-class.md)|特殊化で使用される基になる型のアロケーターを持つ `bool` 型の要素に対するクラステンプレートベクターの完全特殊化。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<vector>

**名前空間:** std

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
