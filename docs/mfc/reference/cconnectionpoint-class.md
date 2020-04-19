---
title: CConnectionPoint クラス
ms.date: 11/04/2016
f1_keywords:
- CConnectionPoint
- AFXDISP/CConnectionPoint
- AFXDISP/CConnectionPoint::CConnectionPoint
- AFXDISP/CConnectionPoint::GetConnections
- AFXDISP/CConnectionPoint::GetContainer
- AFXDISP/CConnectionPoint::GetIID
- AFXDISP/CConnectionPoint::GetMaxConnections
- AFXDISP/CConnectionPoint::GetNextConnection
- AFXDISP/CConnectionPoint::GetStartPosition
- AFXDISP/CConnectionPoint::OnAdvise
- AFXDISP/CConnectionPoint::QuerySinkInterface
helpviewer_keywords:
- CConnectionPoint [MFC], CConnectionPoint
- CConnectionPoint [MFC], GetConnections
- CConnectionPoint [MFC], GetContainer
- CConnectionPoint [MFC], GetIID
- CConnectionPoint [MFC], GetMaxConnections
- CConnectionPoint [MFC], GetNextConnection
- CConnectionPoint [MFC], GetStartPosition
- CConnectionPoint [MFC], OnAdvise
- CConnectionPoint [MFC], QuerySinkInterface
ms.assetid: f0f23a1e-5e8c-41a9-aa6c-1a4793b28e8f
ms.openlocfilehash: a75ce23cf55f26505c2584c3a021b654602a6a2b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182281"
---
# <a name="cconnectionpoint-class"></a>CConnectionPoint クラス

他の OLE オブジェクトと通信するために使われる "コネクション ポイント" と呼ばれる特別な型のインターフェイスを定義します。

## <a name="syntax"></a>構文

```
class CConnectionPoint : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CConnectionPoint::CConnectionPoint](#cconnectionpoint)|`CConnectionPoint` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CConnectionPoint::GetConnections](#getconnections)|コネクション マップ内のすべての接続ポイントを取得します。|
|[CConnectionPoint::GetContainer](#getcontainer)|コネクション マップを所有するコントロールのコンテナーを取得します。|
|[CConnectionPoint::GetIID](#getiid)|接続ポイントのインターフェイス ID を取得します。|
|[CConnectionPoint::GetMaxConnections](#getmaxconnections)|コントロールによってサポートされている接続ポイントの最大数を取得します。|
|[CConnectionPoint::GetNextConnection](#getnextconnection)|接続要素へのポインターを取得します。 *pos*します。|
|[CConnectionPoint::GetStartPosition](#getstartposition)|渡すことができる位置の値を返すことによって、マップの反復処理を開始、`GetNextConnection`呼び出します。|
|[CConnectionPoint::OnAdvise](#onadvise)|確立されるかの接続を解除するときにフレームワークによって呼び出されます。|
|[CConnectionPoint::QuerySinkInterface](#querysinkinterface)|要求されたシンク インターフェイスへのポインターを取得します。|

## <a name="remarks"></a>Remarks

標準の OLE インターフェイスを実装し、OLE コントロールの機能を公開に使用されるとは異なりは、接続ポイントは、イベントを発生させるなどの他のオブジェクトに対するアクションを開始して、変更通知が送信インターフェイスを実装します。

接続は、2 つの部分で構成されています:"source"と、インターフェイスを実装するオブジェクトと呼ばれるインターフェイスを呼び出すオブジェクトには、「シンク」が呼び出されます。 接続ポイントを公開するでは、ソースは、シンク自体への接続の確立を許可します。 コネクション ポイントでは、ソース オブジェクトは、シンクの一連のメンバー関数へのポインターを取得します。 たとえば、シンクによって実装されるイベントを発生させるには、ソースは、シンクの実装の適切なメソッドを呼び出すことができます。

既定で、 `COleControl`-2 つのコネクション ポイントを実装する派生クラス: イベントのいずれかとプロパティのいずれかの変更通知します。 これらの接続が使用される、それぞれ、シンク (たとえば、コントロールのコンテナー) を通知するときに、イベントの発生からのプロパティ値が変更されました。 サポートは、追加の接続ポイントを実装する OLE コントロールのも提供されます。 各追加の接続ポイントが、コントロール クラスで実装された、接続ポイントを実装する「接続部分」を宣言する必要があります。 1 つまたは複数の接続ポイントを実装する場合は、1 つのコントロール クラスの「接続マップ」を宣言する必要があります。

次の例は、単純な接続のマップとの 1 つの接続ポイントを`Sample`OLE コントロール、コードの 2 つのフラグメントで構成される: 最初の部分宣言接続マップとポイントは、2 つ目は、このマップとポイントを実装します。 最初のフラグメントが、コントロール クラスの宣言に挿入された、**保護**セクション。

[!code-cpp[NVC_MFCConnectionPoints#7](../../mfc/codesnippet/cpp/cconnectionpoint-class_1.h)]

BEGIN_CONNECTION_PART と END_CONNECTION_PART マクロ、埋め込みのクラスを宣言する`XSampleConnPt`(から派生した`CConnectionPoint`) この特定の接続ポイントを実装します。 オーバーライドする場合`CConnectionPoint`メンバー関数、または独自のメンバー関数を追加、これら 2 つのマクロの間、それらを宣言します。 CONNECTION_IID マクロのオーバーライドなど、`CConnectionPoint::GetIID`これら 2 つのマクロの間に配置した場合、メンバー関数。

2 つ目のコード フラグメントは、実装ファイルに挿入されます (します。CPP) のコントロール クラス。 このコードは、追加の接続ポイントが含まれた接続マップを実装する`SampleConnPt`:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/cconnectionpoint-class_2.cpp)]

以下のコード片が挿入されると、サンプル OLE コントロールがのコネクション ポイントを公開、`ISampleSink`インターフェイス。

通常、接続ポイントはサポート「マルチキャスト」は、同じインターフェイスに接続されている複数のシンクにブロードキャストすることが可能です。 次のコード フラグメントでは、各シンク接続ポイントを反復処理するマルチキャストを実行する方法を示します。

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

この例では、接続の現在のセットを取得、`SampleConnPt`接続ポイントへの呼び出しが`CConnectionPoint::GetConnections`します。 接続および呼び出しで反復処理し、`ISampleSink::SinkFunc`アクティブな接続ごとにします。

使用しての詳細については`CConnectionPoint`、記事をご覧ください[コネクション ポイント](../../mfc/connection-points.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CConnectionPoint`

## <a name="requirements"></a>必要条件

**ヘッダー :** afxdisp.h

##  <a name="cconnectionpoint"></a>  CConnectionPoint::CConnectionPoint

`CConnectionPoint` オブジェクトを構築します。

```
CConnectionPoint();
```

##  <a name="getconnections"></a>  CConnectionPoint::GetConnections

接続ポイントのすべてのアクティブな接続を取得するには、この関数を呼び出します。

```
const CPtrArray* GetConnections();
```

### <a name="return-value"></a>戻り値

アクティブな接続 (シンク) の配列へのポインター。 NULL ポインター、配列内のいくつかの可能性があります。 この配列内の各非 NULL ポインターは、キャスト演算子を使用して、シンク インターフェイスへのポインターに安全に変換できます。

##  <a name="getcontainer"></a>  CConnectionPoint::GetContainer

取得するためにフレームワークによって呼び出される、`IConnectionPointContainer`接続ポイント。

```
virtual LPCONNECTIONPOINTCONTAINER GetContainer();
```

### <a name="return-value"></a>戻り値

成功した場合、コンテナーへのポインターそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

この関数は通常、BEGIN_CONNECTION_PART マクロによって実装されます。

##  <a name="getiid"></a>  CConnectionPoint::GetIID

接続ポイントのインターフェイス ID を取得するためにフレームワークによって呼び出されます。

```
virtual REFIID GetIID() = 0;
```

### <a name="return-value"></a>戻り値

接続ポイントのインターフェイス ID への参照

### <a name="remarks"></a>Remarks

このコネクション ポイントのインターフェイス ID を返すには、この関数をオーバーライドします。

##  <a name="getmaxconnections"></a>  CConnectionPoint::GetMaxConnections

接続ポイントでサポートされている接続の最大数を取得するためにフレームワークによって呼び出されます。

```
virtual int GetMaxConnections();
```

### <a name="return-value"></a>戻り値

制限なしの場合は、コントロール、または-1 でサポートされている接続の最大数。

### <a name="remarks"></a>Remarks

既定の実装では、制限がないことを示します。-1 を返します。

コントロールに接続できるシンクの数を制限する場合は、この関数をオーバーライドします。

##  <a name="getnextconnection"></a>  CConnectionPoint::GetNextConnection

接続要素へのポインターを取得します。 *pos*します。

```
LPUNKNOWN GetNextConnection(POSITION& pos) const;
```

### <a name="parameters"></a>パラメーター

*pos*<br/>
によって以前返される位置の値への参照を指定します`GetNextConnection`または[中](#getstartposition)呼び出します。

### <a name="return-value"></a>戻り値

指定された接続の要素へのポインター *pos*、または NULL。

### <a name="remarks"></a>Remarks

この関数は、最も接続マップ内のすべての要素を反復処理する場合に適しています。 を反復処理するときは、この関数から返された Null はすべてをスキップします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCConnectionPoints#4](../../mfc/codesnippet/cpp/cconnectionpoint-class_3.cpp)]

##  <a name="getstartposition"></a>  CConnectionPoint::GetStartPosition

渡すことができる位置の値を返すことによって、マップの反復処理を開始、[順次アクセス](#getnextconnection)呼び出します。

```
POSITION GetStartPosition() const;
```

### <a name="return-value"></a>戻り値

マップを反復処理するための開始位置を示す位置値または、マップが空の場合は NULL です。

### <a name="remarks"></a>Remarks

反復シーケンスが予測可能です。そのため、マップの最初の要素""では、特別な意味はありません。

### <a name="example"></a>例

  例をご覧ください[CConnectionPoint::GetNextConnection](#getnextconnection)します。

##  <a name="onadvise"></a>  CConnectionPoint::OnAdvise

接続時にフレームワークによって呼び出されますが、確立または切断されています。

```
virtual void OnAdvise(BOOL bAdvise);
```

### <a name="parameters"></a>パラメーター

*bAdvise*<br/>
接続が確立される場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

既定の実装では、何も行われません。

通知をシンクに接続するか、接続ポイントから切断するときに使用する場合は、この関数をオーバーライドします。

##  <a name="querysinkinterface"></a>  CConnectionPoint::QuerySinkInterface

要求されたシンク インターフェイスへのポインターを取得します。

```
virtual HRESULT QuerySinkInterface(
    LPUNKNOWN pUnkSink,
    void** ppInterface);
```

### <a name="parameters"></a>パラメーター

*pUnkSink*<br/>
要求されているシンク インターフェイスの識別子。

*ppInterface*<br/>
によって識別されるインターフェイス ポインターへのポインター *pUnkSink*します。 オブジェクトは、このインターフェイスをサポートしていない場合\* *ppInterface* NULL に設定されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

## <a name="see-also"></a>関連項目

[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
