---
title: CMFCRibbonStatusBar クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddDynamicElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::AddSeparator
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::Create
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::CreateEx
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindByID
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::FindElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExCount
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetExtendedArea
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::GetSpace
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsBottomFrame
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsExtendedElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::IsInformationMode
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RecalcLayout
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveAll
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::RemoveElement
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::SetInformation
- AFXRIBBONSTATUSBAR/CMFCRibbonStatusBar::OnDrawInformation
helpviewer_keywords:
- CMFCRibbonStatusBar [MFC], AddDynamicElement
- CMFCRibbonStatusBar [MFC], AddElement
- CMFCRibbonStatusBar [MFC], AddExtendedElement
- CMFCRibbonStatusBar [MFC], AddSeparator
- CMFCRibbonStatusBar [MFC], Create
- CMFCRibbonStatusBar [MFC], CreateEx
- CMFCRibbonStatusBar [MFC], FindByID
- CMFCRibbonStatusBar [MFC], FindElement
- CMFCRibbonStatusBar [MFC], GetCount
- CMFCRibbonStatusBar [MFC], GetElement
- CMFCRibbonStatusBar [MFC], GetExCount
- CMFCRibbonStatusBar [MFC], GetExElement
- CMFCRibbonStatusBar [MFC], GetExtendedArea
- CMFCRibbonStatusBar [MFC], GetSpace
- CMFCRibbonStatusBar [MFC], IsBottomFrame
- CMFCRibbonStatusBar [MFC], IsExtendedElement
- CMFCRibbonStatusBar [MFC], IsInformationMode
- CMFCRibbonStatusBar [MFC], RecalcLayout
- CMFCRibbonStatusBar [MFC], RemoveAll
- CMFCRibbonStatusBar [MFC], RemoveElement
- CMFCRibbonStatusBar [MFC], SetInformation
- CMFCRibbonStatusBar [MFC], OnDrawInformation
ms.assetid: 921eb57f-3b40-49fa-a38c-3f2fb6dc2893
ms.openlocfilehash: b927012f241c30b1beec23ff7e0bbc9e8302d8da
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296606"
---
# <a name="cmfcribbonstatusbar-class"></a>CMFCRibbonStatusBar クラス

`CMFCRibbonStatusBar`クラスは、リボン要素を表示できるステータス バー コントロールを実装します。

## <a name="syntax"></a>構文

```
class CMFCRibbonStatusBar : public CMFCRibbonBar
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonStatusBar::AddDynamicElement](#adddynamicelement)|リボン ステータス バーには、動的な要素を追加します。|
|[CMFCRibbonStatusBar::AddElement](#addelement)|リボン ステータス バーに新しいリボン要素を追加します。|
|[CMFCRibbonStatusBar::AddExtendedElement](#addextendedelement)|リボン ステータス バーの拡張領域には、リボン要素を追加します。|
|[CMFCRibbonStatusBar::AddSeparator](#addseparator)|リボン ステータス バーに、区切り記号を追加します。|
|[CMFCRibbonStatusBar::Create](#create)|リボン ステータス バーを作成します。|
|[CMFCRibbonStatusBar::CreateEx](#createex)|拡張スタイルを持つリボン ステータス バーを作成します。|
|[CMFCRibbonStatusBar::FindByID](#findbyid)||
|[CMFCRibbonStatusBar::FindElement](#findelement)|指定したコマンド ID を持つ要素へのポインターを返します|
|[CMFCRibbonStatusBar::GetCount](#getcount)|リボン ステータス バーの主な領域に配置されている要素の数を返します。|
|[CMFCRibbonStatusBar::GetElement](#getelement)|指定したインデックス位置にある要素へのポインターを返します。|
|[CMFCRibbonStatusBar::GetExCount](#getexcount)|リボン ステータス バーの拡張領域内にある要素の数を返します。|
|[CMFCRibbonStatusBar::GetExElement](#getexelement)|リボン ステータス バーの拡張領域内の指定されたインデックスにある要素へのポインターを返します。|
|[CMFCRibbonStatusBar::GetExtendedArea](#getextendedarea)||
|[CMFCRibbonStatusBar::GetSpace](#getspace)||
|[CMFCRibbonStatusBar::IsBottomFrame](#isbottomframe)||
|[CMFCRibbonStatusBar::IsExtendedElement](#isextendedelement)||
|[CMFCRibbonStatusBar::IsInformationMode](#isinformationmode)|リボン ステータス バーの情報のモードが有効になっているかどうかを判断します。|
|[CMFCRibbonStatusBar::RecalcLayout](#recalclayout)|(上書き[CMFCRibbonBar::RecalcLayout](../../mfc/reference/cmfcribbonbar-class.md#recalclayout))。|
|[CMFCRibbonStatusBar::RemoveAll](#removeall)|リボン ステータス バーからすべての要素を削除します。|
|[CMFCRibbonStatusBar::RemoveElement](#removeelement)|リボン ステータス バーから、指定したコマンド ID を持つ要素を削除します。|
|[CMFCRibbonStatusBar::SetInformation](#setinformation)|有効またはリボン ステータス バーの情報モードを無効にします。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonStatusBar::OnDrawInformation](#ondrawinformation)|リボン ステータス バー情報モードが有効な場合に表示される情報の文字列が表示されます。|

## <a name="remarks"></a>Remarks

ユーザーは、リボン ステータス バーの組み込みのコンテキスト メニューを使用して、リボン ステータス バーにあるリボン要素の可視性を変更できます。 追加したり、動的に要素を削除することができます。

リボン ステータス バーが 2 つの領域。 主要な領域と拡張領域。 拡張領域は、リボン ステータス バーの右側に表示され、主な領域よりも、異なる色で表示されます。

通常、ステータス バーの主な領域には、状態の通知が表示されます。 し、拡張領域がビュー コントロールを表示します。 拡張領域は、表示可能な限り、ユーザーがリボン ステータス バーをサイズ変更時にします。

## <a name="example"></a>例

`CMFCRibbonStatusBar` クラスのさまざまなメソッドの使用方法を次の例に示します。 、区切り記号を追加する例では、リボン ステータス バーに新しいリボン要素を追加、リボン ステータス バーの拡張領域にリボン要素を追加する方法を示していて、リボン ステータス バーの通常モードを有効にします。

[!code-cpp[NVC_MFC_RibbonApp#15](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_1.cpp)]
[!code-cpp[NVC_MFC_RibbonApp#16](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCRibbonBar](../../mfc/reference/cmfcribbonbar-class.md)

[CMFCRibbonStatusBar](../../mfc/reference/cmfcribbonstatusbar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribbonstatusbar.h

##  <a name="adddynamicelement"></a>  CMFCRibbonStatusBar::AddDynamicElement

リボン ステータス バーには、動的な要素を追加します。

```
void AddDynamicElement(CMFCRibbonBaseElement* pElement);
```

### <a name="parameters"></a>パラメーター

*pElement*<br/>
[in]動的な要素へのポインター。

### <a name="remarks"></a>Remarks

正規表現の要素とは異なり、動的な要素はカスタマイズできず、ステータス バーの [カスタマイズ] メニューは表示されません。

##  <a name="addelement"></a>  CMFCRibbonStatusBar::AddElement

リボン ステータス バーに新しいリボン要素を追加します。

```
void AddElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>パラメーター

*pElement*<br/>
[in]追加された要素へのポインター。

*lpszLabel*<br/>
[in]要素のテキスト ラベル。

*bIsVisible*<br/>
[in]非表示として、要素を追加する場合に表示、として要素を FALSE 追加する場合は TRUE。

##  <a name="addextendedelement"></a>  CMFCRibbonStatusBar::AddExtendedElement

リボン ステータス バーの拡張領域には、リボン要素を追加します。

```
void AddExtendedElement(
    CMFCRibbonBaseElement* pElement,
    LPCTSTR lpszLabel,
    BOOL bIsVisible=TRUE);
```

### <a name="parameters"></a>パラメーター

*pElement*<br/>
[in]追加された要素へのポインター。

*lpszLabel*<br/>
[in]要素のテキスト ラベル。

*bIsVisible*<br/>
[in]非表示として、要素を追加する場合に表示、として要素を FALSE 追加する場合は TRUE。

### <a name="remarks"></a>Remarks

拡張領域は、ステータス バー コントロールの右側にあります。

##  <a name="addseparator"></a>  CMFCRibbonStatusBar::AddSeparator

リボン ステータス バーに、区切り記号を追加します。

```
void AddSeparator();
```

### <a name="remarks"></a>Remarks

フレームワークでは、区切り記号を追加、メソッドの後[CMFCRibbonStatusBar::AddElement](#addelement)します。 最後の要素を挿入します。

##  <a name="create"></a>  CMFCRibbonStatusBar::Create

リボン ステータス バーを作成します。

```
BOOL Create(
    CWnd* pParentWnd,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
[in]親ウィンドウへのポインター。

*dwStyle*<br/>
[in]コントロールのスタイルの論理 OR の組み合わせ。

*nID*<br/>
[in]ステータス バーのコントロール ID。

### <a name="return-value"></a>戻り値

TRUE の場合、ステータス バーが正常に作成、FALSE それ以外の場合。

##  <a name="createex"></a>  CMFCRibbonStatusBar::CreateEx

拡張スタイルを含むリボン ステータス バーを作成します。

```
BOOL CreateEx(
    CWnd* pParentWnd,
    DWORD dwCtrlStyle=0,
    DWORD dwStyle=WS_CHILD|WS_VISIBLE|CBRS_BOTTOM,
    UINT nID=AFX_IDW_STATUS_BAR);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
親ウィンドウへのポインター。

*dwCtrlStyle*<br/>
ステータス バーのオブジェクトを作成するための追加のスタイルの論理 OR の組み合わせ。

*dwStyle*<br/>
ステータス バーのコントロールのスタイル。

*nID*<br/>
ステータス バーのコントロール ID。

### <a name="return-value"></a>戻り値

TRUE の場合、ステータス バーが正常に作成、FALSE それ以外の場合。

##  <a name="findbyid"></a>  CMFCRibbonStatusBar::FindByID

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
CMFCRibbonBaseElement* FindByID(UINT uiCmdID, BOOL = TRUE);
```

### <a name="parameters"></a>パラメーター

[in] *uiCmdID*<br/>
[in]*BOOL*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="findelement"></a>  CMFCRibbonStatusBar::FindElement

指定したコマンド ID を持つ要素へのポインターを返します

```
CMFCRibbonBaseElement* FindElement(UINT uiID);
```

### <a name="parameters"></a>パラメーター

*uiID*<br/>
[in]要素の ID。

### <a name="return-value"></a>戻り値

指定したコマンド ID を持つ要素へのポインター このような要素が存在しない場合は NULL です。

##  <a name="getcount"></a>  CMFCRibbonStatusBar::GetCount

リボン ステータス バーの主な領域に配置されている要素の数を返します。

```
int GetCount() const;
```

### <a name="return-value"></a>戻り値

リボン ステータス バーの主な領域に配置されている要素の数。

##  <a name="getelement"></a>  CMFCRibbonStatusBar::GetElement

指定したインデックス位置にある要素へのポインターを返します。

```
CMFCRibbonBaseElement* GetElement(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]ステータス バー コントロールのメイン領域に配置されている要素の 0 から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

指定したインデックス位置にある要素へのポインター。 インデックスが負の値またはステータス バー内の要素の数を超える場合は NULL です。

### <a name="remarks"></a>Remarks

##  <a name="getexcount"></a>  CMFCRibbonStatusBar::GetExCount

リボン ステータス バーの拡張領域内にある要素の数を返します。

```
int GetExCount() const;
```

### <a name="return-value"></a>戻り値

リボン ステータス バーの拡張領域内にある要素の数。

##  <a name="getexelement"></a>  CMFCRibbonStatusBar::GetExElement

リボン ステータス バーの拡張領域内の指定されたインデックスにある要素へのポインターを返します。 拡張領域は、ステータス バー コントロールの右側にあります。

```
CMFCRibbonBaseElement* GetExElement(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[in]ステータス バー コントロールの拡張領域に配置されている要素の 0 から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

リボン ステータス バーの拡張領域内の指定されたインデックスにある要素へのポインター。 場合は NULL *nIndex*が負の値またはリボン ステータス バーの拡張領域内の要素の数を超えています。

### <a name="remarks"></a>Remarks

##  <a name="getextendedarea"></a>  CMFCRibbonStatusBar::GetExtendedArea

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
virtual BOOL GetExtendedArea(CRect& rect) const;
```

### <a name="parameters"></a>パラメーター

[in]*rect*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getspace"></a>  CMFCRibbonStatusBar::GetSpace

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
int GetSpace() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isbottomframe"></a>  CMFCRibbonStatusBar::IsBottomFrame

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
BOOL IsBottomFrame() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isextendedelement"></a>  CMFCRibbonStatusBar::IsExtendedElement

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
BOOL IsExtendedElement(CMFCRibbonBaseElement* pElement) const;
```

### <a name="parameters"></a>パラメーター

[in]*pElement*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isinformationmode"></a>  CMFCRibbonStatusBar::IsInformationMode

リボン ステータス バーの情報のモードが有効になっているかどうかを判断します。

```
BOOL IsInformationMode() const;
```

### <a name="return-value"></a>戻り値

ステータス バーは、情報モードで動作できる場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

情報モードでは、ステータス バーは、正規表現のすべてのペインを非表示にし、メッセージ文字列を表示します。

##  <a name="ondrawinformation"></a>  CMFCRibbonStatusBar::OnDrawInformation

リボン ステータス バー情報モードが有効な場合に表示される文字列を表示します。

```
virtual void OnDrawInformation(
    CDC* pDC,
    CString& strInfo,
    CRect rectInfo);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

*strInfo*<br/>
[in]情報の文字列。

*rectInfo*<br/>
[in]外接する四角形。

### <a name="remarks"></a>Remarks

ステータス バー情報の文字列の外観をカスタマイズする場合は、派生クラスでこのメソッドをオーバーライドします。 使用して、 [CMFCRibbonStatusBar::SetInformation](#setinformation)情報モードで、ステータス バーを配置するメソッド。 このモードで、ステータス バーはすべてのペインを非表示にしで指定された情報文字列を表示します*strInfo*します。

##  <a name="recalclayout"></a>  CMFCRibbonStatusBar::RecalcLayout

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Remarks

##  <a name="removeall"></a>  CMFCRibbonStatusBar::RemoveAll

リボン ステータス バーからすべての要素を削除します。

```
void RemoveAll();
```

##  <a name="removeelement"></a>  CMFCRibbonStatusBar::RemoveElement

リボン ステータス バーから、指定したコマンド ID を持つ要素を削除します。

```
BOOL RemoveElement(UINT uiID);
```

### <a name="parameters"></a>パラメーター

*uiID*<br/>
[in]ステータス バーから削除する要素の ID。

### <a name="return-value"></a>戻り値

TRUE の場合、指定した要素*uiID*が削除されます。 FALSE それ以外の場合。

##  <a name="setinformation"></a>  CMFCRibbonStatusBar::SetInformation

有効またはリボン ステータス バーの情報モードを無効にします。

```
void SetInformation(LPCTSTR lpszInfo);
```

### <a name="parameters"></a>パラメーター

*lpszInfo*<br/>
[in]情報の文字列。

### <a name="remarks"></a>Remarks

情報のモードで、ステータス バーを配置するのにには、このメソッドを使用します。 このモードで、ステータス バーはすべてのペインを非表示にしで指定された情報文字列を表示します*lpszInfo*します。

LpszInfo が NULL の場合、ステータス バーは通常モードに戻ります。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBar クラス](../../mfc/reference/cmfcribbonbar-class.md)<br/>
[CMFCRibbonBaseElement クラス](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar クラス](../../mfc/reference/cmfcribbonbar-class.md)
