---
title: unlink
ms.date: 12/16/2019
api_name:
- unlink
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
- unlink
helpviewer_keywords:
- unlink function
ms.assetid: 2cd82055-5770-48be-88ee-4b2c70541c46
ms.openlocfilehash: 5d8251c77a3c4d16ec6328c1c8e6d73d935db139
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301042"
---
# <a name="unlink"></a>unlink

Microsoft 実装の POSIX 関数名 `unlink` は、 [_unlink](unlink-wunlink.md)関数の非推奨のエイリアスです。 既定では、[コンパイラの警告 (レベル 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)が生成されます。 名前は、実装固有の名前の標準 C 規則に従っていないため、非推奨とされます。 ただし、関数は引き続きサポートされます。

代わりに[_unlink](unlink-wunlink.md)を使用することをお勧めします。 または、この関数名を引き続き使用して、警告を無効にすることもできます。 詳細については、「警告と[POSIX の関数名](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)を[無効にする](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)」を参照してください。
