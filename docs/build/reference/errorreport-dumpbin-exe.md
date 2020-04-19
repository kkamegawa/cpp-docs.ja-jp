---
title: /ERRORREPORT (dumpbin.exe)
description: Microsoft DUMPBIN ユーティリティ/ERRORREPORT コマンドラインオプションのリファレンスです。
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT dumpbin option
- ERRORREPORT dumpbin option
- /ERRORREPORT dumpbin option
ms.assetid: 51178c43-4f95-4fda-8f97-50a257d1c948
ms.openlocfilehash: 665b4b1e7c01de4a1fcd848a9e6b36ddbf2944c9
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257677"
---
# <a name="errorreport-dumpbinexe"></a>/ERRORREPORT (dumpbin.exe)

> [!NOTE]
> /ERRORREPORT オプションは非推奨とされます。 Windows Vista 以降では、エラー報告は[Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。

## <a name="syntax"></a>構文

> **/Errorreport**\[**NONE** \| **PROMPT** \| **QUEUE** \| **SEND** ]

## <a name="remarks"></a>コメント

**/Errorreport**引数は、Windows エラー報告サービスの設定によってオーバーライドされます。 レポートが Windows エラー報告によって有効になっている場合、DUMPBIN によって内部エラーのレポートが Microsoft に自動的に送信されます。 Windows エラー報告で無効になっている場合、レポートは送信されません。

## <a name="see-also"></a>参照

[DUMPBIN オプション](dumpbin-options.md)
