---
title: COleCmdUI クラス
ms.date: 09/12/2018
f1_keywords:
- COleCmdUI
- AFXDOCOBJ/COleCmdUI
- AFXDOCOBJ/COleCmdUI::COleCmdUI
- AFXDOCOBJ/COleCmdUI::Enable
- AFXDOCOBJ/COleCmdUI::SetCheck
- AFXDOCOBJ/COleCmdUI::SetText
helpviewer_keywords:
- COleCmdUI [MFC], COleCmdUI
- COleCmdUI [MFC], Enable
- COleCmdUI [MFC], SetCheck
- COleCmdUI [MFC], SetText
ms.assetid: a2d5ce08-6657-45d3-8673-2a9f32d50eec
ms.openlocfilehash: 5dc4e9504805146a9eff0f5ab937868226e4516e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148511"
---
# <a name="colecmdui-class"></a>COleCmdUI クラス

アプリケーションの `IOleCommandTarget`ドリブンの機能に関連するユーザー インターフェイス オブジェクトの状態を更新するメソッドを MFC に提供します。

## <a name="syntax"></a>構文

```
class COleCmdUI : public CCmdUI
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleCmdUI::COleCmdUI](#colecmdui)|`COleCmdUI` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleCmdUI::Enable](#enable)|設定または有効にするコマンドのフラグをクリアします。|
|[COleCmdUI::SetCheck](#setcheck)|設定のオン/オフ切り替えの状態コマンド。|
|[COleCmdUI::SetText](#settext)|コマンドのテキスト名またはステータス文字列を返します。|

## <a name="remarks"></a>Remarks

アプリケーションではない有効になっている DocObjects、MFC アプリケーションでメニューをユーザーのビューが UPDATE_COMMAND_UI 通知を処理するときに。 各通知、 [CCmdUI](../../mfc/reference/ccmdui-class.md)特定のコマンドの状態を反映するように操作できるオブジェクト。 ただし、DocObjects で、アプリケーションが有効な場合に MFC UPDATE_OLE_COMMAND_UI 通知を処理し、割り当てます`COleCmdUI`オブジェクト。

`COleCmdUI` コマンド (という名前、開く、印刷、具合) などのコンテナーのユーザー インターフェイスを受信する DocObject でき DocObject のユーザー インターフェイスで発生するコマンドを受信するためのコンテナーを使用します。 `IDispatch`同じコマンドをディスパッチするされる可能性があります`IOleCommandTarget`クエリし、引数を指定せず、通常は、コマンドの標準セットに依存し、型情報は必要ありませんので、実行する簡単な方法を提供します。 `COleCmdUI` 有効にする、更新、および DocObject ユーザー インターフェイスのコマンドの他のプロパティを設定するために使用します。 コマンドを実行するときに呼び出す[COleServerDoc::OnExecOleCmd](../../mfc/reference/coleserverdoc-class.md#onexecolecmd)します。

DocObjects については、次を参照してください。 [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)と[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CCmdUI](../../mfc/reference/ccmdui-class.md)

`COleCmdUI`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdocobj.h

##  <a name="colecmdui"></a>  COleCmdUI::COleCmdUI

構築、`COleCmdUI`オブジェクトに関連付けられた特定のユーザー インターフェイス コマンド。

```
COleCmdUI(
    OLECMD* rgCmds,
    ULONG cCmds,
    const GUID* m_pGroup);
```

### <a name="parameters"></a>パラメーター

*rgCmds*<br/>
指定された GUID に関連付けられている、サポートされているコマンドの一覧。 `OLECMD`構造体は、コマンド フラグをコマンドを関連付けます。

*cCmds*<br/>
コマンド数*rgCmds*します。

*pGroup*<br/>
コマンドのセットを識別する GUID へのポインター。

### <a name="remarks"></a>Remarks

`COleCmdUI`オブジェクトは、メニュー項目やコントロール バーのボタンなどの DocObject ユーザー インターフェイス オブジェクトを更新するためのプログラム インターフェイスを提供します。 ユーザー インターフェイス オブジェクトを有効になっている、無効になっている、オンになっている、クリア、`COleCmdUI`オブジェクト。

##  <a name="enable"></a>  COleCmdUI::Enable

コマンド フラグを設定するには、この関数を呼び出して、 `COleCmdUI` OLECOMDF_ENABLED、コマンドが有効になって使用可能なインターフェイスに伝える、またはコマンド フラグをクリアするオブジェクトします。

```
virtual void Enable(BOOL bOn);
```

### <a name="parameters"></a>パラメーター

*bOn*<br/>
コマンドが関連付けられているかどうかを示す、`COleCmdUI`オブジェクトを有効または無効にする必要があります。 このコマンドをにより、0 以外0 には、コマンドが無効にします。

##  <a name="setcheck"></a>  COleCmdUI::SetCheck

オン/オフ切り替えの状態を設定するには、この関数を呼び出すコマンド。

```
virtual void SetCheck(int nCheck);
```

### <a name="parameters"></a>パラメーター

*確認してください。*<br/>
オン/オフ切り替えを設定する状態を決定する値コマンド。 値は次のとおりです。

|[値]|説明|
|-----------|-----------------|
|**1**|コマンドを on に設定します。|
|**2**|不確定コマンドを設定します。このコマンドの属性は、上と関連する選択項目の状態をオフの両方では、状態を特定できないことはできません。|
|その他の値|コマンドをオフに設定します。|

##  <a name="settext"></a>  COleCmdUI::SetText

この関数では、コマンドのテキスト名またはステータス文字列を返します。

```
virtual void SetText(LPCTSTR lpszText);
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
コマンドで使用するテキストへのポインター。

## <a name="see-also"></a>関連項目

[CCmdUI クラス](../../mfc/reference/ccmdui-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
