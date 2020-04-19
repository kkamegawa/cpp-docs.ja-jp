---
title: CommandHandler
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CommandHandler function
ms.assetid: 662bc7bf-4a10-42b3-986d-d8bae4f63551
ms.openlocfilehash: 99a95228f6036e5f391395be367cdef39ca3dc3b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492457"
---
# <a name="commandhandler"></a>CommandHandler

`CommandHandler`は、メッセージマップ内の COMMAND_HANDLER マクロの3番目のパラメーターで識別される関数です。

## <a name="syntax"></a>構文

```cpp
LRESULT CommandHandler(
    WORD wNotifyCode,
    WORD wID,
    HWND hWndCtl,
    BOOL& bHandled);
```

#### <a name="parameters"></a>パラメーター

*wNotifyCode*<br/>
通知コード。

*wID*<br/>
メニュー項目、コントロール、またはアクセラレータの識別子。

*hWndCtl*<br/>
ウィンドウコントロールを指定するハンドル。

*bHandled*<br/>
が呼び出される前に`CommandHandler` 、メッセージマップによって*bhandled*が TRUE に設定されます。 が`CommandHandler`メッセージを完全に処理しない場合は、 *bhandled*を FALSE に設定して、メッセージにさらに処理が必要であることを示す必要があります。

## <a name="return-value"></a>戻り値

メッセージ処理の結果。 成功した場合は0。

## <a name="remarks"></a>Remarks

メッセージマップでこのメッセージハンドラーを使用する例については、「 [COMMAND_HANDLER](reference/message-map-macros-atl.md#command_handler)」を参照してください。

## <a name="see-also"></a>関連項目

[ウィンドウの実装](../atl/implementing-a-window.md)<br/>
[メッセージ マップ](../atl/message-maps-atl.md)<br/>
[WM_NOTIFY](/windows/win32/controls/wm-notify)
