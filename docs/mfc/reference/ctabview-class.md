---
title: CTabView クラス
ms.date: 11/04/2016
f1_keywords:
- CTabView
- AFXTABVIEW/CTabView
- AFXTABVIEW/CTabView::AddView
- AFXTABVIEW/CTabView::FindTab
- AFXTABVIEW/CTabView::GetActiveView
- AFXTABVIEW/CTabView::GetTabControl
- AFXTABVIEW/CTabView::RemoveView
- AFXTABVIEW/CTabView::SetActiveView
- AFXTABVIEW/CTabView::IsScrollBar
- AFXTABVIEW/CTabView::OnActivateView
helpviewer_keywords:
- CTabView [MFC], AddView
- CTabView [MFC], FindTab
- CTabView [MFC], GetActiveView
- CTabView [MFC], GetTabControl
- CTabView [MFC], RemoveView
- CTabView [MFC], SetActiveView
- CTabView [MFC], IsScrollBar
- CTabView [MFC], OnActivateView
ms.assetid: 8e6ecd9d-d28d-432b-8ec8-0446f0204d52
ms.openlocfilehash: 56640edbd0d2e74a1cc00dad5441350ad3d35725
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64346252"
---
# <a name="ctabview-class"></a>CTabView クラス

`CTabView`クラスは、タブ コントロール クラスの使用を簡略化 ( [CMFCTabCtrl](../../mfc/reference/ctabview-class.md)) MFC のドキュメント/ビュー アーキテクチャを使用するアプリケーションでします。

## <a name="syntax"></a>構文

```
class CTabbedView : public CView
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CTabView::AddView](#addview)|タブ コントロールに新しいビューを追加します。|
|[CTabView::FindTab](#findtab)|タブ コントロールで、指定されたビューのインデックスを返します。|
|[CTabView::GetActiveView](#getactiveview)|現在アクティブなビューへのポインターを返します|
|[CTabView::GetTabControl](#gettabcontrol)|ビューに関連付けられているタブ コントロールへの参照を返します。|
|[CTabView::RemoveView](#removeview)|タブ コントロールから、ビューを削除します。|
|[CTabView::SetActiveView](#setactiveview)|ビューをアクティブになります。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CTabView::IsScrollBar](#isscrollbar)|タブのビューが共有の水平スクロール バーを持つかどうかを判断するタブのビューを作成するときに、フレームワークによって呼び出されます。|
|[CTabView::OnActivateView](#onactivateview)|アクティブまたは非アクティブなタブの表示が行われたときに、フレームワークによって呼び出されます。|

## <a name="remarks"></a>Remarks

このクラスは、簡単にドキュメント/ビュー アプリケーションに、タブ付きビューを追加します。 `CTabView` `CView`-埋め込みを含むクラスを派生`CMFCTabCtrl`オブジェクト。 `CTabView` サポートに必要なすべてのメッセージ処理、`CMFCTabCtrl`オブジェクト。 クラスを単純に派生`CTabView`を追加し、アプリケーションに組み込む`CView`-を使用して派生クラス、`AddView`メソッド。 タブ コントロールのタブとしてこれらのビューが表示されます。

たとえば、さまざまな方法で表すことができるドキュメントがあります: スプレッドシート、グラフ、編集可能なフォーム、およびなどとして。 挿入に、必要に応じて、データを描画する個々 のビューを作成できます、 `CTabView`-オブジェクトを派生し、コードを追加せずにタブ付きもらいます。

[TabbedView サンプル:タブ付きビューのアプリケーションの MFC](../../overview/visual-cpp-samples.md)の使用法を示します`CTabView`します。

## <a name="example"></a>例

次の例はどのように`CTabView`TabbedView サンプルで使用します。

[!code-cpp[NVC_MFC_TabbedView#1](../../mfc/reference/codesnippet/cpp/ctabview-class_1.h)]

## <a name="requirements"></a>必要条件

**ヘッダー:** afxTabView.h

##  <a name="addview"></a>  CTabView::AddView

タブ コントロールにビューを追加します。

```
int AddView(
    CRuntimeClass* pViewClass,
    const CString& strViewLabel,
    int iIndex=-1,
    CCreateContext* pContext=NULL);
```

### <a name="parameters"></a>パラメーター

*pViewClass*<br/>
[in]挿入されたビューのランタイム クラスへのポインター。

*strViewLabel*<br/>
[in]タブのテキストを指定します。

*iIndex*<br/>
[in]ビューを挿入する位置の 0 から始まる位置を指定します。 位置が-1 の場合は、新しいタブが最後に挿入されます。

*pContext*<br/>
[in]ポインター、`CCreateContext`のビュー。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合、ビューのインデックス。 それ以外の場合、-1 を返します。

### <a name="remarks"></a>Remarks

フレームに埋め込まれたタブ コントロールにビューを追加するには、この関数を呼び出します。

##  <a name="findtab"></a>  CTabView::FindTab

タブ コントロールで、指定されたビューのインデックスを返します。

```
int FindTab(HWND hWndView) const;
```

### <a name="parameters"></a>パラメーター

*hWndView*<br/>
[in]ビューのハンドル。

### <a name="return-value"></a>戻り値

見つかった場合、ビューのインデックスそれ以外の場合、-1 を返します。

### <a name="remarks"></a>Remarks

指定したハンドルを持つビューのインデックスを取得するには、この関数を呼び出します。

##  <a name="getactiveview"></a>  CTabView::GetActiveView

現在アクティブなビューへのポインターを返します。

```
CView* GetActiveView() const;
```

### <a name="return-value"></a>戻り値

アクティブなビュー、またはアクティブなビューがない場合は NULL に有効なポインター。

### <a name="remarks"></a>Remarks

##  <a name="gettabcontrol"></a>  CTabView::GetTabControl

ビューに関連付けられているタブ コントロールへの参照を返します。

```
DECLARE_DYNCREATE CMFCTabCtrl& GetTabControl();
```

### <a name="return-value"></a>戻り値

ビューに関連付けられたタブ コントロールへの参照。

##  <a name="isscrollbar"></a>  CTabView::IsScrollBar

タブのビューが共有の水平スクロール バーを持つかどうかを判断するタブのビューを作成するときに、フレームワークによって呼び出されます。

```
virtual BOOL IsScrollBar() const;
```

### <a name="return-value"></a>戻り値

TRUE の場合、共有のスクロール バーとタブのビューを作成する必要があります。 それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

フレームワークは、このメソッドを呼び出すときに、 *CTabView*オブジェクトが作成されます。

上書き、 *IsScrollBar*メソッドで、 *CTabView*-クラスを派生し、共有の水平スクロール バーのあるビューを作成する場合に TRUE を返します。

##  <a name="onactivateview"></a>  CTabView::OnActivateView

アクティブまたは非アクティブなタブの表示が行われたときに、フレームワークによって呼び出されます。

```
virtual void OnActivateView(CView* view);
```

### <a name="parameters"></a>パラメーター

*ビュー*<br/>
[in]ビューへのポインター。

### <a name="remarks"></a>Remarks

既定の実装では、何も行われません。 このメソッドをオーバーライドする`CTabView`-この通知を処理するクラスを派生します。

##  <a name="removeview"></a>  CTabView::RemoveView

タブ コントロールから、ビューを削除します。

```
BOOL RemoveView(int iTabNum);
```

### <a name="parameters"></a>パラメーター

*iTabNum*<br/>
[in]削除するビューのインデックス。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合、削除されたビューのインデックス。 それ以外の場合は-1。

### <a name="remarks"></a>Remarks

##  <a name="setactiveview"></a>  CTabView::SetActiveView

ビューをアクティブになります。

```
BOOL SetActiveView(int iTabNum);
```

### <a name="parameters"></a>パラメーター

*iTabNum*<br/>
[in]タブのビューの 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

TRUE の場合は、指定されたビューがアクティブにされた、false の場合、ビューのインデックスが有効でない場合。

### <a name="remarks"></a>Remarks

詳細については、次を参照してください。 [CMFCTabCtrl::SetActiveTab](../../mfc/reference/cmfctabctrl-class.md#setactivetab)します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCTabCtrl](../../mfc/reference/ctabview-class.md)<br/>
[CView クラス](../../mfc/reference/cview-class.md)
