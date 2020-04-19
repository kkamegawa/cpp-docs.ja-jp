---
title: /ERRORREPORT (editbin.exe)
description: Microsoft EDITBIN ユーティリティ/ERRORREPORT コマンドラインオプションのリファレンスです。
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
helpviewer_keywords:
- -ERRORREPORT editbin option
- ERRORREPORT editbin option
- /ERRORREPORT editbin option
ms.assetid: eca66ac3-b754-4bd7-9dd4-e04fc79a71b6
ms.openlocfilehash: 6c2ec8b6cda7b794114ed38cfb72b885bf2e38a1
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257596"
---
# <a name="errorreport-editbinexe"></a>/ERRORREPORT (editbin.exe)

> [!NOTE]
> /ERRORREPORT オプションは非推奨とされます。 Windows Vista 以降では、エラー報告は[Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。

## <a name="syntax"></a>構文

> **/Errorreport** \[ **NONE** \| **PROMPT** \| **QUEUE** \| **SEND** ]

## <a name="remarks"></a>コメント

**/Errorreport**引数は、Windows エラー報告サービスの設定によってオーバーライドされます。 EDITBIN では、レポートが Windows エラー報告によって有効になっている場合、内部エラーのレポートが Microsoft に自動的に送信されます。 Windows エラー報告で無効になっている場合、レポートは送信されません。

## <a name="see-also"></a>参照

[EDITBIN オプション](editbin-options.md)
