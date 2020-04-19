---
title: '&lt;stack&gt;'
ms.date: 11/04/2016
f1_keywords:
- <stack>
helpviewer_keywords:
- stack, stack header
- stack header
ms.assetid: 89d8999e-c773-46f2-86c1-4b3b5aedb1c1
ms.openlocfilehash: e8c468da35ae23e5a37c2dfc5ac3fbdf47408c71
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686080"
---
# <a name="ltstackgt"></a>&lt;stack&gt;

クラステンプレートスタックと2つのサポートテンプレートを定義します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<stack>

**名前空間:** std

> [!NOTE]
> @No__t_0stack > ライブラリでは、`#include <initializer_list>` ステートメントも使用します。

## <a name="members"></a>メンバー

### <a name="operators"></a>演算子

|||
|-|-|
|[operator!=](../standard-library/stack-operators.md#op_neq)|演算子の左辺のスタック オブジェクトが右辺のスタック オブジェクトと等しくないかどうかを調べます。|
|[operator<](../standard-library/stack-operators.md#op_lt)|演算子の左辺のスタック オブジェクトが右辺のスタック オブジェクトより小さいかどうかを調べます。|
|[operator\<=](../standard-library/stack-operators.md#op_lt_eq)|演算子の左辺のスタック オブジェクトが右辺のスタック オブジェクト以下かどうかを調べます。|
|[operator==](../standard-library/stack-operators.md#op_eq_eq)|演算子の左辺のスタック オブジェクトが右辺のスタック オブジェクトと等しいかどうかを調べます。|
|[operator>](../standard-library/stack-operators.md#op_gt)|演算子の左辺のスタック オブジェクトが右辺のスタック オブジェクトより大きいかどうかを調べます。|
|[operator>=](../standard-library/stack-operators.md#op_gt_eq)|演算子の左辺のスタック オブジェクトが右辺のスタック オブジェクト以上かどうかを調べます。|

### <a name="classes"></a>クラス

|||
|-|-|
|[stack クラス](../standard-library/stack-class.md)|基になるコンテナー型に最も新しく追加された要素へのアクセスを制限することにより、機能の制限を提供するテンプレート コンテナーのアダプター クラスです。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
