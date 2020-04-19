---
title: no_dual_interfaces import 属性
ms.date: 08/29/2019
f1_keywords:
- no_dual_interfaces
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
ms.openlocfilehash: 6270888f0d31e4fbe18fb3364995be8c73426b83
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220764"
---
# <a name="no_dual_interfaces-import-attribute"></a>no_dual_interfaces import 属性

**C++のみ**

コンパイラがデュアル インターフェイス メソッドのラッパー関数を生成する方法を変更します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***no_dual_interfaces**

## <a name="remarks"></a>Remarks

通常、ラッパーは、インターフェイスの仮想関数テーブルを通じてメソッドを呼び出します。 **No_dual_interfaces**では、ラッパーはを`IDispatch::Invoke`呼び出して、メソッドを呼び出します。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
