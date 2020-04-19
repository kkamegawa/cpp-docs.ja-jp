---
title: Windows メッセージに関するマクロ
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::WM_FORWARDMSG
ms.assetid: 63abd22c-372d-4148-bb04-c605950ae64f
ms.openlocfilehash: 7bb5e2fa265c3a5dcabcc16d8343d5b86a4aaf42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275926"
---
# <a name="windows-messages-macros"></a>Windows メッセージに関するマクロ

このマクロは、ウィンドウ メッセージを転送します。

|||
|-|-|
|[WM_FORWARDMSG](#wm_forwardmsg)|処理するための別のウィンドウのウィンドウで受信メッセージの転送を使用します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase.h

##  <a name="wm_forwardmsg"></a>  WM_FORWARDMSG

このマクロは、処理のための別のウィンドウのウィンドウで受信したメッセージを転送します。

```
WM_FORWARDMSG
```

### <a name="return-value"></a>戻り値

0 以外の場合、メッセージが処理された場合しない場合は 0。

### <a name="remarks"></a>Remarks

処理のための別のウィンドウのウィンドウで受信したメッセージを転送するのに WM_FORWARDMSG を使用します。 LPARAM および WPARAM パラメーターは、次のように使用されます。

|パラメーター|使用法|
|---------------|-----------|
|WPARAM|ユーザーによって定義されたデータ|
|LPARAM|ポインターを`MSG`メッセージに関する情報を含む構造体|

### <a name="example"></a>例

次の例では、`m_hWndOther`このメッセージを受信する他のウィンドウを表します。

[!code-cpp[NVC_ATL_Windowing#137](../../atl/codesnippet/cpp/windows-messages-macros_1.cpp)]

## <a name="see-also"></a>関連項目

[[マクロ]](../../atl/reference/atl-macros.md)
