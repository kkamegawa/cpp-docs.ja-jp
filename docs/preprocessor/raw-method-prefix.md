---
title: raw_method_prefix
ms.date: 08/29/2019
f1_keywords:
- raw_method_prefix
helpviewer_keywords:
- raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
ms.openlocfilehash: b1bc536507716e5c117718ec825bf7fe76c84b61
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216148"
---
# <a name="raw_method_prefix"></a>raw_method_prefix

**C++のみ**

名前の衝突を避けるために異なるプレフィックスを指定します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***raw_method_prefix (** "*prefix*" **)**

### <a name="parameters"></a>パラメーター

*外線*\
使用されるプレフィックス。

## <a name="remarks"></a>Remarks

低レベルのプロパティとメソッドは、 **raw_** の既定のプレフィックスを使用して、という名前のメンバー関数によって公開されます。これにより、上位レベルのエラー処理メンバー関数との名前の競合を回避できます。

> [!NOTE]
> **Raw_method_prefix**属性の効果は、 [raw_interfaces_only](raw-interfaces-only.md)属性が存在することによって変更されていません。 プレフィックスを指定する場合、 `raw_interfaces_only` raw_method_prefix は常により優先されます。 両方の属性が同じ`#import`ステートメントで使用されている場合は、 **raw_method_prefix**属性で指定されたプレフィックスが使用されます。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
