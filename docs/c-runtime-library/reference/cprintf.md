---
title: cprintf
ms.date: 12/16/2019
api_name:
- cprintf
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
- cprintf
helpviewer_keywords:
- cprintf function
ms.assetid: 573e6634-d7e5-4856-8c01-627dcfbd5fc8
ms.openlocfilehash: 1f61043b1cf59ad31107bcfc333338a7493767cf
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299898"
---
# <a name="cprintf"></a>cprintf

Microsoft 固有の関数名 `cprintf` は、 [_cprintf](cprintf-cprintf-l-cwprintf-cwprintf-l.md)関数の非推奨のエイリアスです。 既定では、[コンパイラの警告 (レベル 3) C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)が生成されます。 名前は、実装固有の名前の標準 C 規則に従っていないため、非推奨とされます。 ただし、関数は引き続きサポートされます。

代わりに、 [_cprintf](cprintf-cprintf-l-cwprintf-cwprintf-l.md)またはセキュリティが強化された[_cprintf_s](cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)関数を使用することをお勧めします。 または、この関数名を引き続き使用して、警告を無効にすることもできます。 詳細については、「警告と[POSIX の関数名](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)を[無効にする](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#turn-off-the-warning)」を参照してください。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。
