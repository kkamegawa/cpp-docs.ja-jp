---
title: MessageHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- MessageHandler function
ms.assetid: 8a0acf97-1b0d-4226-91b9-75446634a03c
ms.openlocfilehash: aa044ef88ba3c872c2652cd774ac50024e52c68c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492318"
---
# <a name="messagehandler"></a>MessageHandler

`MessageHandler`メッセージマップ内の MESSAGE_HANDLER マクロの2番目のパラメーターで識別される関数の名前を指定します。

## <a name="syntax"></a>構文

```
LRESULT MessageHandler(
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    BOOL& bHandled);
```

### <a name="parameters"></a>パラメーター

*uMsg*<br/>
メッセージを指定します。

*wParam*<br/>
メッセージ固有の追加情報。

*lParam*<br/>
メッセージ固有の追加情報。

*bHandled*<br/>
が呼び出される前に`MessageHandler` 、メッセージマップによって*bhandled*が TRUE に設定されます。 が`MessageHandler`メッセージを完全に処理しない場合は、 *bhandled*を FALSE に設定して、メッセージにさらに処理が必要であることを示す必要があります。

## <a name="return-value"></a>戻り値

メッセージ処理の結果。 成功した場合は0。

## <a name="remarks"></a>Remarks

メッセージマップでこのメッセージハンドラーを使用する例については、「 [MESSAGE_HANDLER](reference/message-map-macros-atl.md#message_handler)」を参照してください。

## <a name="see-also"></a>関連項目

[ウィンドウの実装](../atl/implementing-a-window.md)<br/>
[メッセージ マップ](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
