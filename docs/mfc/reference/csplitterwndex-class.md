---
title: CSplitterWndEx クラス
ms.date: 11/04/2016
f1_keywords:
- CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx
- AFXSPLITTERWNDEX/CSplitterWndEx::OnDrawSplitter
helpviewer_keywords:
- CSplitterWndEx [MFC], OnDrawSplitter
ms.assetid: 33e5eef3-05e1-4a07-a968-bf9207ce8598
ms.openlocfilehash: 8dedad4e99a37b13dc618859c8e6d8a83a65ea76
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64339603"
---
# <a name="csplitterwndex-class"></a>CSplitterWndEx クラス

カスタマイズされた分割ウィンドウを表します。

## <a name="syntax"></a>構文

```
class CSplitterWndEx : public CSplitterWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CSplitterWndEx::CSplitterWndEx`|既定のコンストラクターです。|
|`CSplitterWndEx::~CSplitterWndEx`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSplitterWndEx::OnDrawSplitter](#ondrawsplitter)|分割ウィンドウを描画するためにフレームワークによって呼び出されます。 (上書き[CSplitterWnd::OnDrawSplitter](csplitterwnd-class.md#ondrawsplitter))。|

## <a name="remarks"></a>Remarks

上書き、`OnDrawSplitter`スプリッター ウィンドウのグラフィック要素の外観をカスタマイズするメソッド。

`CSplitterWndEx`と同時にクラスを使用、 [OnDrawSplitterBorder](cmfcvisualmanager-class.md#ondrawsplitterborder)、 [OnDrawSplitterBox](cmfcvisualmanager-class.md#ondrawsplitterbox)、および[OnFillSplitterBackground](cmfcvisualmanager-class.md#onfillsplitterbackground)メソッドビジュアル マネージャーによって実装されます。 アプリケーション内のスプリッター ウィンドウを描画するためには、ビジュアル マネージャーの宣言を置き換える、`CSplitterWnd`クラス、`CSplitterWndEx`クラス。 フレーム ウィンドウのアプリケーションでは、スプリッター ウィンドウのクラスは、mainfrm.h に配置されている CMainFrame クラスで宣言されます。 例については、次を参照してください。、`OutlookDemo`サンプル、サンプル ディレクトリにします。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](cobject-class.md)

[CCmdTarget](ccmdtarget-class.md)

[CWnd](cwnd-class.md)

[CSplitterWnd](csplitterwnd-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxsplitterwndex.h

##  <a name="ondrawsplitter"></a>  CSplitterWndEx::OnDrawSplitter

分割ウィンドウを描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawSplitter(
   CDC* pDC,
   ESplitType nType,
   const CRect& rect
);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。 このパラメーターが NULL の場合、フレームワークには、アクティブなウィンドウが再描画します。

*nType*<br/>
[in]1 つ、`CSplitterWnd::ESplitType`描画するためにスプリッター ウィンドウの要素を指定する列挙値。 正しい値は `splitBox`、`splitBar`、`splitIntersection`、`splitBorder` です。

*rect*<br/>
[in]ディメンションと、指定された分割ウィンドウの要素を描画する場所を指定する外接する四角形。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../hierarchy-chart.md)<br/>
[クラス](mfc-classes.md)<br/>
[CSplitterWnd クラス](csplitterwnd-class.md)<br/>
[CMFCVisualManager クラス](cmfcvisualmanager-class.md)
