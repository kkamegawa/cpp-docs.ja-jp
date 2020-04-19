---
title: once_flag 構造体
ms.date: 09/17/2018
f1_keywords:
- mutex/std::once_flag
ms.assetid: 71bfb88d-ca8c-4082-a6e1-ff52151e8629
ms.openlocfilehash: fb85bd48f9b1ac10ec2fefbc6738aae777f67bcf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455207"
---
# <a name="onceflag-structure"></a>once_flag 構造体

実行の複数のスレッドが存在する場合でも、初期化コードが1回だけ呼び出されるようにするために、テンプレート関数[call_once](../standard-library/mutex-functions.md#call_once)と共に使用される**構造体**を表します。

## <a name="syntax"></a>構文

struct once_flag { constexpr once_flag() noexcept; };

## <a name="remarks"></a>Remarks

構造体には、既定のコンストラクターのみがあります。  `once_flag`

`once_flag` 型のオブジェクトは、作成することはできますがコピーはできません。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<ミューテックス >

**名前空間:** std

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<mutex>](../standard-library/mutex.md)
