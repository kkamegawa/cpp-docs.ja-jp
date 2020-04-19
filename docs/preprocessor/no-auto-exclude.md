---
title: no_auto_exclude import 属性
ms.date: 08/29/2019
f1_keywords:
- no_auto_exclude
helpviewer_keywords:
- no_auto_exclude attribute
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
ms.openlocfilehash: 530c2b2adf24e964cb0a512371f4430a61bf8b11
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216081"
---
# <a name="no_auto_exclude-import-attribute"></a>no_auto_exclude import 属性

**C++のみ**

自動除外を無効にします。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***no_auto_exclude**

## <a name="remarks"></a>Remarks

タイプ ライブラリは、システム ヘッダーまたはその他のタイプ ライブラリで定義された項目の定義を含むことがあります。 `#import` は、そのような項目を自動的に除外して多重定義エラーを回避します。 これにより、除外する項目ごとに[コンパイラの警告 (レベル 3) C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)が発行されます。 この属性を使用して、自動除外を無効にすることができます。

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
