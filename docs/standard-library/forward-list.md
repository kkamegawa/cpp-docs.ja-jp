---
title: '&lt;forward_list&gt;'
ms.date: 11/04/2016
f1_keywords:
- <forward_list>
helpviewer_keywords:
- <forward_list>
ms.assetid: 8b4ab09e-1475-434a-b4e0-fdbc07a08b5b
ms.openlocfilehash: 708e16cb4b8a1640f4978b806bc52beed24decd4
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688059"
---
# <a name="ltforward_listgt"></a>&lt;forward_list&gt;

コンテナークラステンプレート forward_list といくつかのサポートテンプレートを定義します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<forward_list>

**名前空間:** std

> [!NOTE]
> @No__t_0forward_list > ライブラリでは、`#include <initializer_list>` ステートメントも使用します。

## <a name="members"></a>メンバー

### <a name="operators"></a>演算子

|||
|-|-|
|[operator==](../standard-library/forward-list-operators.md#op_eq_eq)|演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクトと等しいかどうかを調べます。|
|[operator!=](../standard-library/forward-list-operators.md#op_neq)|演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクトと等しくないかどうかを調べます。|
|[operator<](../standard-library/forward-list-operators.md#op_lt)|演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクトより小さいかどうかを調べます。|
|[operator<=](../standard-library/forward-list-operators.md#op_lt_eq)|演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクト以下であるかどうかを調べます。|
|[operator>](../standard-library/forward-list-operators.md#op_gt)|演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクトより大きいかどうかを調べます。|
|[operator>=](../standard-library/forward-list-operators.md#op_lt_eq)|演算子の左辺の前方リスト オブジェクトが右辺の前方リスト オブジェクト以上であるかどうかを調べます。|

### <a name="functions"></a>関数

|||
|-|-|
|[swap](../standard-library/forward-list-functions.md#swap)|2 つの前方リストの要素を交換します。|

### <a name="classes"></a>クラス

|||
|-|-|
|[forward_list](../standard-library/forward-list-class.md)|要素の可変長シーケンスを制御するオブジェクトを表します。 シーケンスは要素のシングル リンク リストとして格納され、それぞれに `Type` 型のメンバーが含まれます。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
