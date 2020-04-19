---
title: mktemp
ms.date: 12/16/2019
api_name:
- mktemp
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mktemp
helpviewer_keywords:
- mktemp function
ms.assetid: b58cba60-034f-4e63-b312-ccbcd489d0a7
ms.openlocfilehash: c9efd79111c000764561ba415db79a13a34c46fe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301016"
---
# <a name="mktemp"></a>mktemp

Microsoft 固有の関数名 `mktemp` は、 [_mktemp](mktemp-wmktemp.md)関数の非推奨のエイリアスです。 既定では、[コンパイラの警告 (レベル 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)が生成されます。 名前は、実装固有の名前の標準 C 規則に従っていないため、非推奨とされます。 ただし、関数は引き続きサポートされます。

代わりに、 [_mktemp](mktemp-wmktemp.md)またはセキュリティが強化された[_mktemp_s](mktemp-s-wmktemp-s.md)関数を使用することをお勧めします。 または、この関数名を引き続き使用して、警告を無効にすることもできます。 詳細については、「警告と[POSIX の関数名](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)を[無効にする](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)」を参照してください。
