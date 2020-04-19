---
title: '&lt;deque&gt;'
ms.date: 11/04/2016
f1_keywords:
- <deque>
helpviewer_keywords:
- deque header
ms.assetid: 4521fe92-5a91-4853-9e9f-59600bf9e46f
ms.openlocfilehash: a5fea8f4a1bc1612a35db71cc515ba4799e95da6
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689727"
---
# <a name="ltdequegt"></a>&lt;deque&gt;

コンテナークラステンプレート deque といくつかのサポートテンプレートを定義します。

## <a name="requirements"></a>［要件］

**ヘッダー**: \<deque>

> [!NOTE]
> @No__t_0deque > ライブラリでは、`#include <initializer_list>` ステートメントも使用します。

## <a name="members"></a>メンバー

### <a name="operators"></a>演算子

|||
|-|-|
|[operator!=](../standard-library/deque-operators.md#op_neq)|演算子の左側の deque オブジェクトが右側の deque オブジェクトと等しくないかどうかを調べます。|
|[operator<](../standard-library/deque-operators.md#op_lt)|演算子の左側の deque オブジェクトが右側の deque オブジェクトより小さいかどうかを調べます。|
|[operator\<=](../standard-library/deque-operators.md#op_gt_eq)|演算子の左側の deque オブジェクトが右側の deque オブジェクト以下かどうかを調べます。|
|[operator==](../standard-library/deque-operators.md#op_eq_eq)|演算子の左側の deque オブジェクトが右側の deque オブジェクトと等しいかどうかを調べます。|
|[operator>](../standard-library/deque-operators.md#op_gt)|演算子の左側の deque オブジェクトが右側の deque オブジェクトより大きいかどうかを調べます。|
|[operator>=](../standard-library/deque-operators.md#op_gt_eq)|演算子の左側の deque オブジェクトが右側の deque オブジェクト以上かどうかを調べます。|

### <a name="functions"></a>関数

|||
|-|-|
|[swap](../standard-library/deque-functions.md#swap)|2 つの deque の要素を交換します。|

### <a name="classes"></a>クラス

|||
|-|-|
|[deque クラス](../standard-library/deque-class.md)|指定された型の要素を線形の配置に配置し、ベクターと同様に、任意の要素への高速なランダムアクセスを可能にし、コンテナーの後ろでの効率的な挿入と削除を可能にする、シーケンスコンテナーのクラステンプレート。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
