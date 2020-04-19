---
title: CDocObjectServer クラス
ms.date: 09/12/2018
f1_keywords:
- CDocObjectServer
- AFXDOCOB/CDocObjectServer
- AFXDOCOB/CDocObjectServer::CDocObjectServer
- AFXDOCOB/CDocObjectServer::ActivateDocObject
- AFXDOCOB/CDocObjectServer::OnActivateView
- AFXDOCOB/CDocObjectServer::OnApplyViewState
- AFXDOCOB/CDocObjectServer::OnSaveViewState
helpviewer_keywords:
- CDocObjectServer [MFC], CDocObjectServer
- CDocObjectServer [MFC], ActivateDocObject
- CDocObjectServer [MFC], OnActivateView
- CDocObjectServer [MFC], OnApplyViewState
- CDocObjectServer [MFC], OnSaveViewState
ms.assetid: 18cd0dff-0616-4472-b8d9-66c081bc383a
ms.openlocfilehash: f4b1a352a9fa62dfcb46d1c1cb0784661e66e5b4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391137"
---
# <a name="cdocobjectserver-class"></a>CDocObjectServer クラス

標準の `COleDocument` サーバーを完全な DocObject サーバーにするために必要な、 `IOleDocument`、 `IOleDocumentView`、 `IOleCommandTarget`、 `IPrint`などの追加 OLE インターフェイスを実装します。

## <a name="syntax"></a>構文

```
class CDocObjectServer : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDocObjectServer::CDocObjectServer](#cdocobjectserver)|`CDocObjectServer` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDocObjectServer::ActivateDocObject](#activatedocobject)|オブジェクトのドキュメントのサーバーをアクティブ化が表示されません。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CDocObjectServer::OnActivateView](#onactivateview)|DocObject ビューを表示します。|
|[CDocObjectServer::OnApplyViewState](#onapplyviewstate)|DocObject ビューの状態を復元します。|
|[CDocObjectServer::OnSaveViewState](#onsaveviewstate)|DocObject ビューの状態を保存します。|

## <a name="remarks"></a>Remarks

`CDocObjectServer` 派生`CCmdTarget`と密接に連携および`COleServerDoc`インターフェイスを公開します。

DocObject サーバーのドキュメントに含めることができます[CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md) DocObject 項目をサーバーのインターフェイスを表すオブジェクト。

DocObject サーバーをカスタマイズする、独自のクラスから派生させる`CDocObjectServer`そのビューのセットアップ関数をオーバーライドして[OnActivateView](#onactivateview)、 [OnApplyViewState](#onapplyviewstate)、および[OnSaveViewState](#onsaveviewstate). フレームワークの呼び出しに応答クラスの新しいインスタンスを提供する必要があります。

DocObjects については、次を参照してください。 [CDocObjectServerItem](../../mfc/reference/cdocobjectserveritem-class.md)と[COleCmdUI](../../mfc/reference/colecmdui-class.md)で、 *MFC リファレンス*します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocObjectServer`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdocob.h

##  <a name="activatedocobject"></a>  CDocObjectServer::ActivateDocObject

この関数は、ドキュメント オブジェクトのサーバーをアクティブ化 (は表示されません) を呼び出します。

```
void ActivateDocObject();
```

### <a name="remarks"></a>Remarks

`ActivateDocObject` 呼び出し`IOleDocumentSite`の`ActivateMe`メソッドを設定およびへの呼び出しで指定されたビューを表示する方法についての特定の待機しているため、ビューは表示されませんが、 [CDocObjectServer::OnActivateView](#onactivateview)します。

同時に、`ActivateDocObject`と`OnActivateView`アクティブ化し、DocObject ビューを表示します。 DocObject アクティブ化は、OLE インプレース アクティブ化の他の種類によって異なります。 DocObject のアクティブ化がか所の陰影の枠線とサイズ変更ハンドル) などのオブジェクトの表示要素を省略し、オブジェクトの拡張機能、および (通常のように、その四角形の外側に描画するのではなく、ビューの四角形内のスクロール バーを描画します埋めこみ先編集)。

##  <a name="cdocobjectserver"></a>  CDocObjectServer::CDocObjectServer

`CDocObjectServer` オブジェクトを構築して初期化します。

```
explicit CDocObjectServer(
    COleServerDoc* pOwner,
    LPOLEDOCUMENTSITE pDocSite = NULL);
```

### <a name="parameters"></a>パラメーター

*pOwner*<br/>
DocObject サーバー用のクライアントは、クライアント サイトのドキュメントへのポインター。

*pDocSite*<br/>
ポインター、`IOleDocumentSite`コンテナーによって実装されるインターフェイス。

### <a name="remarks"></a>Remarks

DocObject がアクティブの場合、クライアント サイトの OLE インターフェイス ( `IOleDocumentSite`) に DocObject サーバーは、そのクライアント (コンテナー) と通信できます。 DocObject サーバーがアクティブになることはまず、コンテナーを実装する、`IOleDocumentSite`インターフェイス。 そうである場合[COleServerDoc::GetDocObjectServer](../../mfc/reference/coleserverdoc-class.md#getdocobjectserver)がコンテナーに DocObjects でサポートされているかどうかに呼び出されます。 既定では、 `GetDocObjectServer` NULL を返します。 オーバーライドする必要があります`COleServerDoc::GetDocObjectServer`新しいを作成する`CDocObjectServer`オブジェクトまたは派生オブジェクトへのポインターは、使用、独自の`COleServerDoc`コンテナーとその`IOleDocumentSite`コンス トラクターに引数としてインターフェイス。

##  <a name="onactivateview"></a>  CDocObjectServer::OnActivateView

DocObject ビューを表示するには、この関数を呼び出します。

```
virtual HRESULT OnActivateView();
```

### <a name="return-value"></a>戻り値

エラーまたは警告の値を返します。 既定では、NOERROR を返します成功した場合。それ以外の場合、E_FAIL します。

### <a name="remarks"></a>Remarks

この関数で埋め込み先フレーム ウィンドウを作成するには、ビュー内でスクロール バーの描画、サーバー コンテナーが共有、フレーム コントロールが追加されます、作業中のオブジェクトを設定し、最後にで埋め込み先フレーム ウィンドウを示していますおよびフォーカスを設定メニューのセットアップします。

##  <a name="onapplyviewstate"></a>  CDocObjectServer::OnApplyViewState

DocObject ビューの状態を復元するには、この関数をオーバーライドします。

```
virtual void OnApplyViewState(CArchive& ar);
```

### <a name="parameters"></a>パラメーター

*ar*<br/>
A`CArchive`ビューステートをシリアル化するオブジェクト。

### <a name="remarks"></a>Remarks

インスタンス化後に最初に、ビューが表示されるときに、この関数が呼び出されます。 `OnApplyViewState` ビューのデータに基づいて自体を再初期化するように指示します、`CArchive`オブジェクトで以前に保存[OnSaveViewState](#onsaveviewstate)します。 ビューのデータを検証する必要があります、`CArchive`オブジェクトをコンテナーは任意の方法で、ビュー ステートのデータを解釈しようとはしません。

使用することができます`OnSaveViewState`ビューの状態を特定の永続的な情報を格納します。 オーバーライドする場合は`OnSaveViewState`情報を格納するには、無効にするは`OnApplyViewState`情報を読み取るし、新しくアクティブになったときに、ビューに適用します。

##  <a name="onsaveviewstate"></a>  CDocObjectServer::OnSaveViewState

DocObject ビューについての特別な状態情報を保存するには、この関数をオーバーライドします。

```
virtual void OnSaveViewState(CArchive& ar);
```

### <a name="parameters"></a>パラメーター

*ar*<br/>
A`CArchive`ビュー ステートがシリアル化するオブジェクトします。

### <a name="remarks"></a>Remarks

状態には、ビューの種類、ズームの倍率、カーソルと選択のポイントなどのプロパティが含まれます。 コンテナーは、通常、ビューを非アクティブ化する前にこの関数を呼び出します。 保存された状態は、利用後で復元できます[OnApplyViewState](#onapplyviewstate)します。

使用することができます`OnSaveViewState`ビューの状態を特定の永続的な情報を格納します。 オーバーライドする場合は`OnSaveViewState`情報を格納するには、無効にするは`OnApplyViewState`情報を読み取るし、新しくアクティブになったときに、ビューに適用します。

## <a name="see-also"></a>関連項目

[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDocObjectServerItem クラス](../../mfc/reference/cdocobjectserveritem-class.md)
