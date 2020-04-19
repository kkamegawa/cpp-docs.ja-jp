---
title: CDynamicChain クラス
ms.date: 11/04/2016
f1_keywords:
- CDynamicChain
- ATLWIN/ATL::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CDynamicChain
- ATLWIN/ATL::CDynamicChain::CallChain
- ATLWIN/ATL::CDynamicChain::RemoveChainEntry
- ATLWIN/ATL::CDynamicChain::SetChainEntry
helpviewer_keywords:
- message maps, chaining
- chaining message maps
- CDynamicChain class
ms.assetid: f084b2be-0e77-4836-973d-ae278a1e9da8
ms.openlocfilehash: 4b68198c17d7bd030b88bc78ad4de1367c914703
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259002"
---
# <a name="cdynamicchain-class"></a>CDynamicChain クラス

このクラスは、メッセージ マップの動的な組み合わせをサポートするメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CDynamicChain
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDynamicChain::CDynamicChain](#cdynamicchain)|コンストラクターです。|
|[CDynamicChain:: ~ CDynamicChain](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDynamicChain::CallChain](#callchain)|別のオブジェクトのメッセージ マップに Windows メッセージを送信します。|
|[CDynamicChain::RemoveChainEntry](#removechainentry)|メッセージ マップ エントリをコレクションから削除します。|
|[CDynamicChain::SetChainEntry](#setchainentry)|メッセージ マップ エントリをコレクションに追加または既存のエントリを変更します。|

## <a name="remarks"></a>Remarks

`CDynamicChain` Windows メッセージを別のオブジェクトのメッセージ マップの実行時に、送信を有効にすると、メッセージ マップのコレクションを管理します。

メッセージ マップの動的な組み合わせのサポートを追加するには、次の操作を行います。

- クラスを派生`CDynamicChain`します。 メッセージ マップで指定、[場合](message-map-macros-atl.md#chain_msg_map_dynamic)マクロを別のオブジェクトの既定のメッセージ マップにチェーンします。

- チェーンするすべてのクラスを派生[CMessageMap](../../atl/reference/cmessagemap-class.md)します。 `CMessageMap` 他のオブジェクトへのメッセージ マップを公開するオブジェクトを許可します。

- 呼び出す`CDynamicChain::SetChainEntry`にチェーンするオブジェクトとどのようなメッセージをマップするを特定します。

たとえば、クラスが次のように定義されているとします。

[!code-cpp[NVC_ATL_Windowing#88](../../atl/codesnippet/cpp/cdynamicchain-class_1.h)]

クライアントは、 `CMyWindow::SetChainEntry`:

[!code-cpp[NVC_ATL_Windowing#89](../../atl/codesnippet/cpp/cdynamicchain-class_2.cpp)]

場所`chainedObj`チェーン オブジェクトから派生したクラスのインスタンスである`CMessageMap`します。 次に場合、`myCtl`によって処理されていないメッセージを受信`OnPaint`または`OnSetFocus`、ウィンドウ プロシージャにメッセージを送信する`chainedObj`の既定のメッセージ マップです。

メッセージ マップの組み合わせの詳細については、次を参照してください[メッセージ マップ](../../atl/message-maps-atl.md)"ATL ウィンドウ クラス"の記事。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlwin.h

##  <a name="callchain"></a>  CDynamicChain::CallChain

別のオブジェクトのメッセージ マップに Windows メッセージを送信します。

```
BOOL CallChain(
    DWORD dwChainID,
    HWND hWnd,
    UINT uMsg,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT& lResult);
```

### <a name="parameters"></a>パラメーター

*dwChainID*<br/>
[in]チェーンされたオブジェクトとそのメッセージ マップに関連付けられている一意の識別子。

*hWnd*<br/>
[in]メッセージを受信するウィンドウ ハンドル。

*uMsg*<br/>
[in]ウィンドウに送信されるメッセージ。

*wParam*<br/>
[in]追加のメッセージに固有の情報。

*lParam*<br/>
[in]追加のメッセージに固有の情報。

*lResult*<br/>
[out]メッセージの処理の結果。

### <a name="return-value"></a>戻り値

TRUE の場合は、メッセージが完全に処理します。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

ウィンドウ プロシージャを呼び出す`CallChain`を指定する必要があります、[場合](message-map-macros-atl.md#chain_msg_map_dynamic)メッセージ マップ マクロ。 例については、次を参照してください。、 [CDynamicChain](../../atl/reference/cdynamicchain-class.md)の概要。

`CallChain` 以前の呼び出しが必要です[SetChainEntry](#setchainentry)に関連付ける、 *dwChainID*値、オブジェクトと、メッセージ マップを使用します。

##  <a name="cdynamicchain"></a>  CDynamicChain::CDynamicChain

コンストラクターです。

```
CDynamicChain();
```

##  <a name="dtor"></a>  CDynamicChain:: ~ CDynamicChain

デストラクターです。

```
~CDynamicChain();
```

### <a name="remarks"></a>Remarks

割り当てられているすべてのリソースを解放します。

##  <a name="removechainentry"></a>  CDynamicChain::RemoveChainEntry

指定したメッセージ マップをコレクションから削除します。

```
BOOL RemoveChainEntry(DWORD dwChainID);
```

### <a name="parameters"></a>パラメーター

*dwChainID*<br/>
[in]チェーンされたオブジェクトとそのメッセージ マップに関連付けられている一意の識別子。 最初の呼び出しによってこの値を定義する[SetChainEntry](#setchainentry)します。

### <a name="return-value"></a>戻り値

メッセージ マップがコレクションから正常に削除する場合は TRUE。 それ以外の場合、FALSE です。

##  <a name="setchainentry"></a>  CDynamicChain::SetChainEntry

指定したメッセージ マップをコレクションに追加します。

```
BOOL SetChainEntry(
    DWORD dwChainID,
    CMessageMap* pObject,
    DWORD dwMsgMapID = 0);
```

### <a name="parameters"></a>パラメーター

*dwChainID*<br/>
[in]チェーンされたオブジェクトとそのメッセージ マップに関連付けられている一意の識別子。

*pObject*<br/>
[in]メッセージ マップを宣言するチェーン オブジェクトへのポインター。 このオブジェクトはから派生する必要があります[CMessageMap](../../atl/reference/cmessagemap-class.md)します。

*dwMsgMapID*<br/>
[in]チェーンされたオブジェクトでメッセージ マップの識別子。 既定値は 0 で、既定のメッセージ マップを使用して宣言を識別する[送るに](message-map-macros-atl.md#begin_msg_map)します。 宣言された、代替メッセージ マップを指定する[ALT_MSG_MAP(msgMapID)](message-map-macros-atl.md#alt_msg_map)、渡す`msgMapID`します。

### <a name="return-value"></a>戻り値

TRUE の場合、メッセージ マップがコレクションに追加されました。 それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

場合、 *dwChainID*値は、コレクションに既に存在、その関連付けられたオブジェクトとメッセージ マップに置き換えられます*pObject*と*dwMsgMapID*、それぞれします。 それ以外の場合、新しいエントリが追加されます。

## <a name="see-also"></a>関連項目

[CWindowImpl クラス](../../atl/reference/cwindowimpl-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
