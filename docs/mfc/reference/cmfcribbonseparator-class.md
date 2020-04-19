---
title: CMFCRibbonSeparator クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CMFCRibbonSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::AddToListBox
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::CopyFrom
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::GetRegularSize
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsSeparator
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::IsTabStop
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDraw
- AFXBASERIBBONELEMENT/CMFCRibbonSeparator::OnDrawOnList
helpviewer_keywords:
- CMFCRibbonSeparator [MFC], CMFCRibbonSeparator
- CMFCRibbonSeparator [MFC], AddToListBox
- CMFCRibbonSeparator [MFC], CopyFrom
- CMFCRibbonSeparator [MFC], GetRegularSize
- CMFCRibbonSeparator [MFC], IsSeparator
- CMFCRibbonSeparator [MFC], IsTabStop
- CMFCRibbonSeparator [MFC], OnDraw
- CMFCRibbonSeparator [MFC], OnDrawOnList
ms.assetid: bedb1a53-cb07-4c3c-be12-698c5409e7cf
ms.openlocfilehash: 4806582a226590459a104f64499ab6ae541570e7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380235"
---
# <a name="cmfcribbonseparator-class"></a>CMFCRibbonSeparator クラス

リボンの区切り記号を実装します。

## <a name="syntax"></a>構文

```
class CMFCRibbonSeparator : public CMFCRibbonBaseElement
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|||
|-|-|
|名前|説明|
|[CMFCRibbonSeparator::CMFCRibbonSeparator](#cmfcribbonseparator)|`CMFCRibbonSeparator` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|名前|説明|
|[CMFCRibbonSeparator::AddToListBox](#addtolistbox)|区切り文字を追加、**コマンド**の一覧で、**カスタマイズ** ダイアログ ボックス。 (上書き[CMFCRibbonBaseElement::AddToListBox](../../mfc/reference/cmfcribbonbaseelement-class.md#addtolistbox))。|
|`CMFCRibbonSeparator::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|`CMFCRibbonSeparator::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|

### <a name="protected-methods"></a>プロテクト メソッド

|||
|-|-|
|名前|説明|
|[CMFCRibbonSeparator::CopyFrom](#copyfrom)|コピー メソッドを別のオブジェクトから区切り記号のメンバー変数を設定します。|
|[CMFCRibbonSeparator::GetRegularSize](#getregularsize)|区切り記号のサイズを返します。|
|[CMFCRibbonSeparator::IsSeparator](#isseparator)|これは、区切り記号であるかどうかを示します。|
|[CMFCRibbonSeparator::IsTabStop](#istabstop)|これは、タブ ストップであるかどうかを示します。|
|[CMFCRibbonSeparator::OnDraw](#ondraw)|リボンまたはクイック アクセス ツールバーに区分線を描画するために、システムによって呼び出されます。|
|[CMFCRibbonSeparator::OnDrawOnList](#ondrawonlist)|区切り文字を描画するためにシステムによって呼び出されます、**コマンド**一覧。|

## <a name="remarks"></a>Remarks

垂直または水平方向の行を論理的に分離リボン要素がリボン区切り記号です。 区切り記号は、リボン コントロール、アプリケーションのメイン メニューのリボン ステータス バー、およびクイック アクセス ツールバーを描画できます。

区切り記号を使用して、アプリケーションで、新しいオブジェクトを構築し、次に示すように、アプリケーションのメイン メニューに追加。

```
CMFCRibbonMainPanel* pMainPanel = m_wndRibbonBar.AddMainCategory(_T("Main Menu"),
    IDB_FILESMALL,
    IDB_FILELARGE);

...
pMainPanel->Add(new CMFCRibbonSeparator(TRUE));
```
呼び出す[CMFCRibbonPanel::AddSeparator](../../mfc/reference/cmfcribbonpanel-class.md#addseparator)リボン パネルに区切り記号を追加します。 区切り記号が割り当てられ、内部で追加、`AddSeparator`メソッド。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSeparator](../../mfc/reference/cmfcribbonseparator-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxbaseribbonelement.h

##  <a name="addtolistbox"></a>  CMFCRibbonSeparator::AddToListBox

区切り文字を追加、**コマンド**の一覧で、**カスタマイズ** ダイアログ ボックス。

```
virtual int AddToListBox(
    CMFCRibbonCommandsListBox* pWndListBox,
    BOOL bDeep);
```

### <a name="parameters"></a>パラメーター

*pWndListBox*<br/>
[in]ポインター、**コマンド**リスト区切り記号が追加されます。

*パラメーター bDeep*<br/>
[in]無視されます。

### <a name="return-value"></a>戻り値

0 から始まるインデックスで指定されたリスト ボックス内の文字列に*pWndListBox*します。

##  <a name="cmfcribbonseparator"></a>  CMFCRibbonSeparator::CMFCRibbonSeparator

`CMFCRibbonSeparator` オブジェクトを構築します。

```
CMFCRibbonSeparator(BOOL bIsHoriz = FALSE);
```

### <a name="parameters"></a>パラメーター

*bIsHoriz*<br/>
[in]TRUE の場合、区切り記号は水平方向です。FALSE の場合、区切り記号は垂直方向です。

### <a name="remarks"></a>Remarks

水平方向の区切り記号は、アプリケーションのメニューで使用されます。 ツールバーの縦の区切り記号が使用されます。

### <a name="example"></a>例

次の例のオブジェクトを構築する方法、`CMFCRibbonSeparator`クラス。

[!code-cpp[NVC_MFC_RibbonApp#19](../../mfc/reference/codesnippet/cpp/cmfcribbonseparator-class_1.cpp)]

##  <a name="copyfrom"></a>  CMFCRibbonSeparator::CopyFrom

コピー メソッドを別のオブジェクトから区切り記号のメンバー変数を設定します。

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
[in]コピー元ソース リボン要素。

##  <a name="getregularsize"></a>  CMFCRibbonSeparator::GetRegularSize

区切り記号のサイズを返します。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイスのコンテンツへのポインター。

### <a name="return-value"></a>戻り値

指定されたデバイス コンテキストで区切り記号のサイズ。

##  <a name="isseparator"></a>  CMFCRibbonSeparator::IsSeparator

これは、区切り記号であるかどうかを示します。

```
virtual BOOL IsSeparator() const;
```

### <a name="return-value"></a>戻り値

このクラスは常に TRUE です。

##  <a name="istabstop"></a>  CMFCRibbonSeparator::IsTabStop

これは、タブ ストップであるかどうかを示します。

```
virtual BOOL IsTabStop() const;
```

### <a name="return-value"></a>戻り値

このクラスは常に FALSE です。

### <a name="remarks"></a>Remarks

リボンの区切り記号はタブではありません。

##  <a name="ondraw"></a>  CMFCRibbonSeparator::OnDraw

リボンまたはクイック アクセス ツールバーに区分線を描画するために、システムによって呼び出されます。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

##  <a name="ondrawonlist"></a>  CMFCRibbonSeparator::OnDrawOnList

区切り文字を描画するためにシステムによって呼び出されます、**コマンド**一覧。

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pDC*|[in]デバイス コンテキストへのポインター。|
|*strText*|[in]一覧に表示されるテキスト。|
|*nTextOffset*|[in]テキストおよび外接する四角形の左側にある間の間隔。|
|*rect*|[in]外接する四角形を指定します。|
|*bIsSelected*|[in]無視されます。|
|*bHighlighted*|[in]無視されます。|

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
