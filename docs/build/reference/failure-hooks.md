---
title: エラー フック
ms.date: 11/04/2016
helpviewer_keywords:
- delayed loading of DLLs, failure hooks
ms.assetid: 12bb303b-ffe6-4471-bffe-9ef4f8bb2d30
ms.openlocfilehash: 2fc22ae77d729868adbf8c37d40e450e35a8e866
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292849"
---
# <a name="failure-hooks"></a>エラー フック

エラー フックと同じ方法で有効になっている、[通知フック](notification-hooks.md)します。 (HINSTANCE または FARPROC) を行うフックの日常的なニーズを処理するために適切な値を返すまたは 0 に、例外をスローする必要があります。

ユーザー定義関数を参照するポインター変数は次のとおりです。

```
// This is the failure hook, dliNotify = {dliFailLoadLib|dliFailGetProc}
ExternC
PfnDliHook   __pfnDliFailureHook2;
```

**DelayLoadInfo**構造体にはから値を含むエラーの正確なレポートに必要な関連データが含まれています`GetLastError`します。

通知が場合**dliFailLoadLib**、フック関数が返すことができます。

- エラーを処理できない場合は 0。

- HMODULE は、エラー フックは、問題が解決され、ライブラリ自体を読み込まれた場合。

通知が場合**dliFailGetProc**、フック関数が返すことができます。

- エラーを処理できない場合は 0。

- 有効なプロシージャのアドレス (インポート関数アドレス)、障害をフックする場合は、アドレス自体を取得に成功しました。

## <a name="see-also"></a>関連項目

[エラー処理と通知](error-handling-and-notification.md)
