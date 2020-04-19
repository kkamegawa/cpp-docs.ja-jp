---
title: CMFCMenuButton クラス
ms.date: 07/15/2019
f1_keywords:
- CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::CMFCMenuButton
- AFXMENUBUTTON/CMFCMenuButton::PreTranslateMessage
- AFXMENUBUTTON/CMFCMenuButton::SizeToContent
- AFXMENUBUTTON/CMFCMenuButton::m_bOSMenu
- AFXMENUBUTTON/CMFCMenuButton::m_bRightArrow
- AFXMENUBUTTON/CMFCMenuButton::m_bStayPressed
- AFXMENUBUTTON/CMFCMenuButton::m_hMenu
- AFXMENUBUTTON/CMFCMenuButton::m_nMenuResult
- AFXMENUBUTTON/CMFCMenuButton::m_bDefaultClick
helpviewer_keywords:
- CMFCMenuButton [MFC], CMFCMenuButton
- CMFCMenuButton [MFC], PreTranslateMessage
- CMFCMenuButton [MFC], SizeToContent
- CMFCMenuButton [MFC], m_bOSMenu
- CMFCMenuButton [MFC], m_bRightArrow
- CMFCMenuButton [MFC], m_bStayPressed
- CMFCMenuButton [MFC], m_hMenu
- CMFCMenuButton [MFC], m_nMenuResult
- CMFCMenuButton [MFC], m_bDefaultClick
ms.assetid: 53d3d459-1e5a-47c5-8b7f-2e61f6af5187
ms.openlocfilehash: d7c23cbda0a5af4dc3fa6b2d9f59497acc9bf5ff
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505208"
---
# <a name="cmfcmenubutton-class"></a>CMFCMenuButton クラス

ポップアップ メニューを表示してユーザーのメニュー選択を報告するボタンです。

## <a name="syntax"></a>構文

```
class CMFCMenuButton : public CMFCButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCMenuButton:: CMFCMenuButton](#cmfcmenubutton)|`CMFCMenuButton` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCMenuButton::P reTranslateMessage](#pretranslatemessage)|ディスパッチされる前にウィンドウメッセージを変換するために、フレームワークによって呼び出されます。 ( `CMFCButton::PreTranslateMessage`をオーバーライドします)。|
|[CMFCMenuButton:: SizeToContent](#sizetocontent)|テキストとイメージのサイズに応じて、ボタンのサイズを変更します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCMenuButton:: m_bOSMenu](#m_bosmenu)|既定のシステムポップアップメニューを表示するか、 [CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)を使用するかを指定します。|
|[CMFCMenuButton:: m_bRightArrow](#m_brightarrow)|ポップアップメニューをボタンの下または右に表示するかどうかを指定します。|
|[CMFCMenuButton:: m_bStayPressed](#m_bstaypressed)|ユーザーがボタンを離した後にメニューボタンの状態を変更するかどうかを指定します。|
|[CMFCMenuButton:: m_hMenu](#m_hmenu)|アタッチされた Windows メニューへのハンドル。|
|[CMFCMenuButton:: m_nMenuResult](#m_nmenuresult)|ポップアップメニューからユーザーが選択した項目を示す識別子。|
|[CMFCMenuButton:: m_bDefaultClick](#m_bdefaultclick)| 既定の (ボタンテキスト/イメージの) 処理を許可します。|

## <a name="remarks"></a>Remarks

クラスは、 [CButton クラス](../../mfc/reference/cbutton-class.md)から派生する[cmfcbutton クラス](../../mfc/reference/cmfcbutton-class.md)から派生します。 `CMFCMenuButton` そのため、を使用`CMFCMenuButton` `CButton`する場合と同じ方法でをコード内で使用できます。

を作成`CMFCMenuButton`する場合は、関連するポップアップメニューへのハンドルを渡す必要があります。 次に、関数`CMFCMenuButton::SizeToContent`を呼び出します。 `CMFCMenuButton::SizeToContent`ボタンのサイズが、ポップアップウィンドウが表示される場所を指す矢印を含めるために十分であることを確認します。これは、ボタンの下または右に表示されます。

## <a name="example"></a>例

次の例では、ボタンに関連付けられているメニューのハンドルを設定する方法、テキストとイメージのサイズに応じてボタンのサイズを変更する方法、およびフレームワークによって表示されるポップアップメニューを設定する方法を示します。 このコードスニペットは、[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_NewControls#38](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#39](../../mfc/reference/codesnippet/cpp/cmfcmenubutton-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCButton](../../mfc/reference/cmfcbutton-class.md)

[CMFCMenuButton](../../mfc/reference/cmfcmenubutton-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxmenubutton

##  <a name="cmfcmenubutton"></a>CMFCMenuButton:: CMFCMenuButton

新しい[Cmfcmenubutton](../../mfc/reference/cmfcmenubutton-class.md)オブジェクトを構築します。

```
CMFCMenuButton();
```

##  <a name="m_bosmenu"></a>  CMFCMenuButton::m_bOSMenu

フレームワークに表示されるポップアップメニューを示すブール型メンバー変数。

```
BOOL m_bOSMenu;
```

### <a name="remarks"></a>Remarks

が`m_bOSMenu` TRUE の場合、フレームワークはこのオブジェクト`TrackPopupMenu`の継承されたメソッドを呼び出します。 それ以外の場合、フレームワークは[CContextMenuManager:: TrackPopupMenu](../../mfc/reference/ccontextmenumanager-class.md#trackpopupmenu)を呼び出します。

##  <a name="m_brightarrow"></a>CMFCMenuButton:: m_bRightArrow

ポップアップメニューの場所を示すブール型メンバー変数。

```
BOOL m_bRightArrow;
```

### <a name="remarks"></a>Remarks

ユーザーがメニューボタンを押すと、アプリケーションにポップアップメニューが表示されます。 フレームワークによって、ボタンの下または右にポップアップメニューが表示されます。 このボタンには、ポップアップメニューが表示される場所を示す小さな矢印もあります。 が`m_bRightArrow` TRUE の場合、フレームワークはボタンの右側にポップアップメニューを表示します。 それ以外の場合は、ボタンの下にポップアップメニューが表示されます。

##  <a name="m_bstaypressed"></a>CMFCMenuButton:: m_bStayPressed

ユーザーがポップアップメニューから選択したときにメニューボタンが押されたかどうかを示すブール型メンバー変数。

```
BOOL m_bStayPressed;
```

### <a name="remarks"></a>Remarks

`m_bStayPressed`メンバーが FALSE の場合、[使用] ボタンをクリックしたときにメニューボタンが押されなくなります。 この場合、フレームワークにはポップアップメニューのみが表示されます。

`m_bStayPressed`メンバーが TRUE の場合、ユーザーがボタンをクリックすると、メニューボタンが押された状態になります。 ユーザーがポップアップメニューを閉じるか、選択を行うかキャンセルするかを選択するまで、押された状態のままになります。

##  <a name="m_hmenu"></a>CMFCMenuButton:: m_hMenu

添付メニューへのハンドル。

```
HMENU m_hMenu;
```

### <a name="remarks"></a>Remarks

フレームワークでは、ユーザーがメニューボタンをクリックしたときに、このメンバー変数によって示されるメニューが表示されます。

##  <a name="m_nmenuresult"></a>CMFCMenuButton:: m_nMenuResult

ポップアップメニューからユーザーが選択した項目を示す整数。

```
int m_nMenuResult;
```

### <a name="remarks"></a>Remarks

このメンバー変数の値は、ユーザーが選択を行わずにメニューをキャンセルした場合、またはエラーが発生した場合は0になります。

##  <a name="m_bdefaultclick"></a>CMFCMenuButton:: m_bDefaultClick

ボタン上のテキストまたはイメージの既定の処理を許可します。

```
BOOL  m_bDefaultClick;
```

### <a name="remarks"></a>Remarks

M_bDefaultClick を false に設定すると、ボタンの任意の場所をクリックすると、ボタンがメニューを表示します。

##  <a name="m_nmenuresult"></a>CMFCMenuButton:: m_nMenuResult

ポップアップメニューからユーザーが選択した項目を示す整数。

```
int m_nMenuResult;
```

### <a name="remarks"></a>Remarks

##  <a name="pretranslatemessage"></a>  CMFCMenuButton::PreTranslateMessage

ディスパッチされる前にウィンドウメッセージを変換するために、フレームワークによって呼び出されます。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>パラメーター

*pMsg*<br/>
から処理するメッセージを含む[MSG](/windows/win32/api/winuser/ns-winuser-msg)構造体を指します。

### <a name="return-value"></a>戻り値

メッセージが変換され、ディスパッチされない場合は0以外の。メッセージが変換されず、ディスパッチする必要がある場合は0。

### <a name="remarks"></a>Remarks

##  <a name="sizetocontent"></a>CMFCMenuButton:: SizeToContent

テキストのサイズとイメージのサイズに応じて、ボタンのサイズを変更します。

```
virtual CSize SizeToContent(BOOL bCalcOnly = FALSE);
```

### <a name="parameters"></a>パラメーター

*bCalcOnly*<br/>
からこのメソッドがボタンのサイズを変更するかどうかを示すブール型パラメーター。

### <a name="return-value"></a>戻り値

ボタンの新しいサイズを指定する[CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクト。

### <a name="remarks"></a>Remarks

この関数を呼び出し、 *bcalconly* TRUE の場合、 `SizeToContent`はボタンの新しいサイズのみを計算します。

ボタンの新しいサイズは、ボタンのテキスト、イメージ、および矢印に応じて計算されます。 また、フレームワークは、水平エッジに対して10ピクセル、垂直エッジに5ピクセルの定義済みの余白を追加します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCButton クラス](../../mfc/reference/cmfcbutton-class.md)
