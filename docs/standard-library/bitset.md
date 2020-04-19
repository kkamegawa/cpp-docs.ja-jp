---
title: '&lt;bitset&gt;'
ms.date: 11/04/2016
f1_keywords:
- <bitset>
helpviewer_keywords:
- <bitset> header
- bitset header
ms.assetid: af30a9b9-489e-46e3-9d29-5f3ea07ae6dc
ms.openlocfilehash: e017cad251f57cb477b0bf711cdd6243d7fd9893
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689925"
---
# <a name="ltbitsetgt"></a>&lt;bitset&gt;

クラステンプレートのビットセットと、固定サイズのビットシーケンスを表現および操作するための2つのサポートテンプレート関数を定義します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<bitset>

**名前空間:** std

## <a name="members"></a>メンバー

### <a name="operators"></a>演算子

|||
|-|-|
|[operator&](../standard-library/bitset-operators.md#op_amp)|次の 2 つのビットセット間でビットごとの AND を実行します。|
|[operator<\<](../standard-library/bitset-operators.md#op_lt_lt)|ビット シーケンスのテキスト表現を標準出力ストリームに挿入します。|
|[operator>>](../standard-library/bitset-operators.md#op_gt_gt)|ビット シーケンスのテキスト表現を標準入力ストリームに挿入します。|
|[operator^](../standard-library/bitset-operators.md#op_xor)|次の 2 つのビットセット間でビットごとの EXCLUSIVE-OR を実行します。|
|[operator&#124;](../standard-library/bitset-operators.md#op_or)|次の 2 つのビットセット間でビットごとの OR を実行します。|

### <a name="classes"></a>クラス

|||
|-|-|
|[bitset](../standard-library/bitset-class.md)|クラステンプレートは、固定数のビットで構成されるシーケンスを格納するオブジェクトの型を記述します。これにより、一連の項目または条件のフラグを保持するコンパクトな方法が提供されます。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
