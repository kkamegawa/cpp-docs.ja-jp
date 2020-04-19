---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 3ad740975cfff4f65f9e1c800a709cfaca3367db
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687821"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

クラステンプレート `numeric_limits` と、浮動小数点の表現と丸め処理に関する2つの列挙体を定義します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<limits>

**名前空間:** std

## <a name="remarks"></a>Remarks

@No__t_0 クラスの明示的な特殊化では、基本型の多くのプロパティが記述されています。**これには**、文字、整数、浮動小数点型、および、 C++言語. \<limits> に記述されたプロパティには、精度、表現の最小と最大サイズ、丸め処理、およびシグナリングに関するエラーが含まれます。

## <a name="members"></a>メンバー

### <a name="enumerations"></a>列挙

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|この列挙体では、小さすぎて、正規化された値としては表現できない非正規化された浮動小数点値を表現するために、実装で選択できるさまざまなメソッドを記述します。|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|この列挙体では、浮動小数点値を整数値に丸めるために、実装で選択できるさまざまなメソッドを記述します。|

### <a name="classes"></a>クラス

|||
|-|-|
|[numeric_limits クラス](../standard-library/numeric-limits-class.md)|クラステンプレートでは、組み込みの数値型の算術プロパティについて説明します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
