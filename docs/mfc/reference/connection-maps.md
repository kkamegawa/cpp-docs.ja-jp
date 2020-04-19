---
title: コネクション マップ
ms.date: 11/04/2016
helpviewer_keywords:
- connection maps
ms.assetid: 1f25a9bc-6d09-4614-99cf-dc38e8ddfa73
ms.openlocfilehash: a36c112de8c760f91afd5cf544b355f7cb8e1bed
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612278"
---
# <a name="connection-maps"></a>コネクション マップ

OLE コントロールは、他のアプリケーションへのインターフェイスを公開できます。 これらのインターフェイスは、そのコントロールにのみ、コンテナーからのアクセスを許可します。 OLE コントロールの他の OLE オブジェクトの外部インターフェイスにアクセスする場合、接続ポイントを確立する必要があります。 この接続ポイントでは、コントロールからイベント マップや通知関数などの外部のディスパッチ マップへのアクセスを許可します。

Microsoft Foundation Class ライブラリには、接続ポイントをサポートするプログラミング モデルが用意されています。 このモデルで「接続マップ」インターフェイスまたは OLE コントロールの接続ポイントを指定するために使用します。 コネクション マップには、各接続ポイントの 1 つのマクロが含まれます。 コネクション マップの詳細については、次を参照してください。、 [CConnectionPoint](../../mfc/reference/cconnectionpoint-class.md)クラス。

通常、コントロールが 2 つのコネクション ポイントをサポートします。 イベントとプロパティの通知のいずれかのいずれか。 これらは実装によって、`COleControl`基底クラスとコントロールの作成者によって追加の作業は必要ありません。 クラスで実装する任意の追加の接続ポイントを手動で追加する必要があります。 コネクション マップとポイントをサポートするには、MFC には、次のマクロが用意されています。

### <a name="connection-map-declaration-and-demarcation"></a>接続のマップの宣言と定義

|||
|-|-|
|[BEGIN_CONNECTION_PART](#begin_connection_part)|埋め込み (クラス宣言で使用する必要があります)、追加の接続ポイントを実装するクラスを宣言します。|
|[END_CONNECTION_PART](#end_connection_part)|接続ポイント (クラス宣言で使用する必要があります) の宣言を終了します。|
|[CONNECTION_IID](#connection_iid)|コントロールの接続ポイントのインターフェイス ID を指定します。|
|[DECLARE_CONNECTION_MAP](#declare_connection_map)|コネクション マップがクラス (クラス宣言で使用する必要があります) で使用されることを宣言します。|
|[BEGIN_CONNECTION_MAP](#begin_connection_map)|コネクション マップ (クラスの実装で使用する必要があります) の定義を開始します。|
|[END_CONNECTION_MAP](#end_connection_map)|コネクション マップ (クラスの実装で使用する必要があります) の定義を終了します。|
|[CONNECTION_PART](#connection_part)|コントロールの接続マップでは、接続ポイントを指定します。|

確立および接続ポイントを使用して接続を切断のシンクを補助する、次の関数。

### <a name="initializationtermination-of-connection-points"></a>コネクション ポイントの初期化/終了

|||
|-|-|
|[AfxConnectionAdvise](#afxconnectionadvise)|ソースとシンクの間の接続を確立します。|
|[AfxConnectionUnadvise](#afxconnectionunadvise)|ソースとシンクの間の接続を切断します。|

##  <a name="begin_connection_part"></a>  BEGIN_CONNECTION_PART

BEGIN_CONNECTION_PART マクロを使用して、イベントおよびプロパティの通知接続ポイントを超えた追加の接続ポイントの定義を開始します。

```
BEGIN_CONNECTION_PART(theClass, localClass)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
コネクション ポイントを持つコントロール クラスの名前を指定します。

*マクロ*<br/>
ローカル接続ポイントを実装するクラスの名前を指定します。

### <a name="remarks"></a>Remarks

クラスのメンバー関数を定義する宣言 (.h) ファイル、BEGIN_CONNECTION_PART マクロでは、接続ポイントを起動し、CONNECTION_IID マクロおよびを実装するその他のメンバー関数を追加して、接続を完了END_CONNECTION_PART マクロを含むマップをポイントします。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="end_connection_part"></a>  END_CONNECTION_PART

コネクション ポイントの宣言を終了します。

```
END_CONNECTION_PART(localClass)
```

### <a name="parameters"></a>パラメーター

*マクロ*<br/>
ローカル接続ポイントを実装するクラスの名前を指定します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="connection_iid"></a>  CONNECTION_IID

OLE コントロールでサポートされる接続ポイントのインターフェイス ID を定義するのにマクロを BEGIN_CONNECTION_PART と END_CONNECTION_PART 間で使用します。

```
CONNECTION_IID(iid)
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
接続ポイントによると呼ばれるインターフェイスのインターフェイス ID。

### <a name="remarks"></a>Remarks

*Iid*引数は、ID が接続されているシンクでは、接続ポイントを呼び出すインターフェイスを識別するために使用されるインターフェイス。 例えば:

[!code-cpp[NVC_MFCConnectionPoints#10](../../mfc/codesnippet/cpp/connection-maps_1.h)]

呼び出す接続ポイントを指定します、`ISinkInterface`インターフェイス。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="declare_connection_map"></a>  DECLARE_CONNECTION_MAP

各`COleControl`-プログラム内の派生クラスは、コントロールをサポートする追加の接続ポイントを指定する接続マップを提供できます。

```
DECLARE_CONNECTION_MAP()
```

### <a name="remarks"></a>Remarks

コントロールは、追加の点をサポートする場合は、クラスの宣言の最後に DECLARE_CONNECTION_MAP マクロを使用します。 次に、クラスのメンバー関数を定義する .cpp ファイル、BEGIN_CONNECTION_MAP マクロ、CONNECTION_PART マクロの各コントロールの接続ポイント、および使用 END_CONNECTION_MAP マクロ接続マップの最後を宣言します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="begin_connection_map"></a>  BEGIN_CONNECTION_MAP

各`COleControl`-プログラム内の派生クラスは、コントロールがサポートする接続ポイントを指定する接続マップを提供できます。

```
BEGIN_CONNECTION_MAP(theClass, theBase)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
コネクション マップ コントロール クラスの名前を指定します。

*基底*<br/>
基本クラスの名前を示す*クラス*します。

### <a name="remarks"></a>Remarks

実装 (します。メンバーを定義する CPP) ファイルは、クラスの関数、BEGIN_CONNECTION_MAP マクロでは、接続のマップを開始しを使用して、接続ポイントの各マクロのエントリを追加、 [CONNECTION_PART](#connection_part)マクロ。 接続マップを最後に、完了、 [END_CONNECTION_MAP](#end_connection_map)マクロ。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="end_connection_map"></a>  END_CONNECTION_MAP

コネクション マップの定義を終了します。

```
END_CONNECTION_MAP()
```

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="connection_part"></a>  CONNECTION_PART

OLE コントロールに対するコネクション ポイントを特定のインターフェイス ID にマップします。

```
CONNECTION_PART(theClass, iid, localClass)
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
コネクション ポイントを持つコントロール クラスの名前を指定します。

*iid*<br/>
接続ポイントによると呼ばれるインターフェイスのインターフェイス ID。

*マクロ*<br/>
ローカル接続ポイントを実装するクラスの名前を指定します。

### <a name="remarks"></a>Remarks

例:

[!code-cpp[NVC_MFCConnectionPoints#2](../../mfc/codesnippet/cpp/connection-maps_2.cpp)]

呼び出す接続ポイントとの接続マップを実装、`IID_ISinkInterface`インターフェイス。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdisp.h

##  <a name="afxconnectionadvise"></a>  AfxConnectionAdvise

指定された、ソースとの間の接続を確立するには、この関数を呼び出す*pUnkSrc*とで指定されたシンク*pUnkSink*します。

```
BOOL AFXAPI AfxConnectionAdvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD FAR* pdwCookie);
```

### <a name="parameters"></a>パラメーター

*pUnkSrc*<br/>
インターフェイスを呼び出し、オブジェクトへのポインター。

*pUnkSink*<br/>
インターフェイスを実装するオブジェクトへのポインター。

*iid*<br/>
接続のインターフェイス ID です。

*bRefCount*<br/>
接続を作成する必要がありますの参照カウントすると true *pUnkSink*インクリメントされます。 FALSE は、参照カウントをインクリメントしないことを示します。

*pdwCookie*<br/>
接続 id が返される位置 DWORD へのポインター。 としてこの値を渡す必要があります、 *dwCookie*パラメーターを`AfxConnectionUnadvise`とき、接続を切断します。

### <a name="return-value"></a>戻り値

0 以外の場合、接続が確立されました。それ以外の場合 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCConnectionPoints#8](../../mfc/codesnippet/cpp/connection-maps_3.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afxctl.h

##  <a name="afxconnectionunadvise"></a>  AfxConnectionUnadvise

指定された、ソースとの間の接続を切断するには、この関数を呼び出す*pUnkSrc*とで指定されたシンク*pUnkSink*します。

```
BOOL AFXAPI AfxConnectionUnadvise(
    LPUNKNOWN pUnkSrc,
    REFIID iid,
    LPUNKNOWN pUnkSink,
    BOOL bRefCount,
    DWORD dwCookie);
```

### <a name="parameters"></a>パラメーター

*pUnkSrc*<br/>
インターフェイスを呼び出し、オブジェクトへのポインター。

*pUnkSink*<br/>
インターフェイスを実装するオブジェクトへのポインター。

*iid*<br/>
接続ポイントのインターフェイスのインターフェイス ID です。

*bRefCount*<br/>
True に設定して、接続の切断する必要がありますの参照カウントすると*pUnkSink*デクリメントされます。 FALSE は、参照カウントがデクリメントされていない必要がありますを示します。

*dwCookie*<br/>
によって返される接続識別子`AfxConnectionAdvise`します。

### <a name="return-value"></a>戻り値

0 以外の場合、接続が切断されました。それ以外の場合 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCConnectionPoints#9](../../mfc/codesnippet/cpp/connection-maps_4.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afxctl.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
