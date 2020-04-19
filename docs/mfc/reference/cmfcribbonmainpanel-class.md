---
title: CMFCRibbonMainPanel クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::Add
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddRecentFilesList
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToBottom
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::AddToRight
- AFXRIBBONMAINPANEL/CMFCRibbonMainPanel::GetCommandsFrame
helpviewer_keywords:
- CMFCRibbonMainPanel [MFC], Add
- CMFCRibbonMainPanel [MFC], AddRecentFilesList
- CMFCRibbonMainPanel [MFC], AddToBottom
- CMFCRibbonMainPanel [MFC], AddToRight
- CMFCRibbonMainPanel [MFC], GetCommandsFrame
ms.assetid: 1af78798-5e75-4365-9c81-a54aa5679602
ms.openlocfilehash: e4bd1ab8cffc87d5079518cf9a1d6e430ca40fd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403595"
---
# <a name="cmfcribbonmainpanel-class"></a>CMFCRibbonMainPanel クラス

クリックしたときに表示されるリボン パネルを実装、 [CMFCRibbonApplicationButton](../../mfc/reference/cmfcribbonapplicationbutton-class.md)します。

## <a name="syntax"></a>構文

```
class CMFCRibbonMainPanel : public CMFCRibbonPanel
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCRibbonMainPanel::CMFCRibbonMainPanel`|既定のコンストラクターです。|
|`CMFCRibbonMainPanel::~CMFCRibbonMainPanel`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonMainPanel::Add](#add)|アプリケーション ボタン パネルの左側のウィンドウにリボン要素を追加します。 (上書き[cmfcribbonpanel::add](../../mfc/reference/cmfcribbonpanel-class.md#add))。|
|[CMFCRibbonMainPanel::AddRecentFilesList](#addrecentfileslist)|最近使ったファイル リスト メニューには、テキスト文字列を追加します。|
|[CMFCRibbonMainPanel::AddToBottom](#addtobottom)|アプリケーションのリボン パネル の下のペインには、リボン要素を追加します。|
|[CMFCRibbonMainPanel::AddToRight](#addtoright)|アプリケーション ボタン パネルの右側のウィンドウにリボン要素を追加します。|
|`CMFCRibbonMainPanel::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCRibbonMainPanel::GetCommandsFrame](#getcommandsframe)|リボンのメイン パネルの領域を表す四角形を返します。|
|`CMFCRibbonMainPanel::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|

## <a name="remarks"></a>Remarks

フレームワークが表示されます、`CMFCRibbonMainPanel`アプリケーション パネルを開くとします。 3 つのペインが含まれています。

- 左側のウィンドウにはなど、ファイルに関連付けられたコマンドが含まれています**オープン**、**保存**、**印刷**、および**閉じる**します。 このペインには、コマンドを追加するには、呼び出す[CMFCRibbonMainPanel::Add](#add)します。

- 右側のウィンドウには、左側のウィンドウでをクリックするコマンドを変更するオプションが含まれています。 たとえばをクリックする**付けて**左側のウィンドウから、右側のウィンドウが使用可能なファイルの種類を表示できます。 このペインにアイテムを追加するには、呼び出す[CMFCRibbonMainPanel::AddToRight](#addtoright)します。

- 下のペインには、アプリケーションの設定を変更して、プログラムを終了できるようにするボタンが含まれています。 このペインにアイテムを追加するには、呼び出す[CMFCRibbonMainPanel::AddToBottom](#addtobottom)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonPanel](../../mfc/reference/cmfcribbonpanel-class.md)

[CMFCRibbonMainPanel](../../mfc/reference/cmfcribbonmainpanel-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxRibbonMainPanel.h

##  <a name="add"></a>  CMFCRibbonMainPanel::Add

アプリケーション ボタン パネルの左側のウィンドウにリボン要素を追加します。

```
virtual void Add(CMFCRibbonBaseElement* pElem);
```

### <a name="parameters"></a>パラメーター

*pElem*<br/>
[入力、出力]メイン パネルに追加するリボン要素へのポインター。

### <a name="remarks"></a>Remarks

パネルには、リボン要素を追加します。 このメソッドを使用して追加された要素は、メイン パネルの左の列に格納されます。

##  <a name="addrecentfileslist"></a>  CMFCRibbonMainPanel::AddRecentFilesList

最近使ったファイル リスト メニューには、テキスト文字列を追加します。

```
void AddRecentFilesList(
    LPCTSTR lpszLabel,
    int nWidth = 300);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
最近使ったファイル リストに追加する文字列を指定します。

*nWidth*<br/>
最近使ったファイルの一覧 パネルのピクセル単位の幅を指定します。

### <a name="remarks"></a>Remarks

##  <a name="addtobottom"></a>  CMFCRibbonMainPanel::AddToBottom

アプリケーションのリボン パネル の下のペインには、リボン要素を追加します。

```
void AddToBottom(CMFCRibbonMainPanelButton* pElem);
```

### <a name="parameters"></a>パラメーター

*pElem*<br/>
[入力、出力]メイン パネルの下部に追加するリボン要素へのポインター。

### <a name="remarks"></a>Remarks

##  <a name="addtoright"></a>  CMFCRibbonMainPanel::AddToRight

アプリケーション ボタン パネルの右側のウィンドウにリボン要素を追加します。

```
void AddToRight(
    CMFCRibbonBaseElement* pElem,
    int nWidth = 300);
```

### <a name="parameters"></a>パラメーター

*pElem*<br/>
メイン パネルの右側に追加するリボン要素へのポインター。

*nWidth*<br/>
右側のパネルのピクセル単位の幅を指定します。

### <a name="remarks"></a>Remarks

右側のパネルにリボン要素を追加するのにには、この関数を使用します。 右側のパネルには、最近使ったファイル リストで、通常が表示されますが、リボンの要素を追加することができます。

##  <a name="getcommandsframe"></a>  CMFCRibbonMainPanel::GetCommandsFrame

リボンのメイン パネルの領域を表す四角形を返します。

```
CRect GetCommandsFrame() const;
```

### <a name="return-value"></a>戻り値

リボンのメイン パネルの領域を表す四角形。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel クラス](../../mfc/reference/cmfcribbonpanel-class.md)
