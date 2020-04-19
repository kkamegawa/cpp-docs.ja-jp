---
title: IDocHostUIHandlerDispatch インターフェイス
ms.date: 07/02/2019
f1_keywords:
- IDocHostUIHandlerDispatch
- atlbase/ATL::IDocHostUIHandlerDispatch
helpviewer_keywords:
- IDocHostUIHandlerDispatch interface
ms.assetid: 6963a301-601a-4ac3-8bef-f7b252ea2fc6
ms.openlocfilehash: a9e672144160528e6a2fbfe4cb702c4d211ef720
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495920"
---
# <a name="idochostuihandlerdispatch-interface"></a>IDocHostUIHandlerDispatch インターフェイス

Microsoft HTML 解析およびレンダリングエンジンへのインターフェイスです。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
interface IDocHostUIHandlerDispatch : IDispatch
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

> [!NOTE]
>  次の表のリンクは、 [IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))インターフェイスのメンバーに関する INet SDK のリファレンストピックです。 `IDocHostUIHandlerDispatch`はと`IDocUIHostHandler`同じ機能を持ちますが、その`IDocHostUIHandlerDispatch`違いはディスパッチ`IDocUIHostHandler`インターフェイスであり、はカスタムインターフェイスです。

|||
|-|-|
|[EnableModeless](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753253\(v=vs.85\))|[IOleInPlaceActiveObject:: EnableModeless](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-enablemodeless)の MSHTML 実装から呼び出されます。 MSHTML がモーダル UI を表示するときにも呼び出されます。|
|[FilterDataObject](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753254\(v=vs.85\))|ホストが MSHTML のデータオブジェクトを置き換えることができるようにするために、ホスト上で MSHTML によって呼び出されます。|
|[GetDropTarget](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753255\(v=vs.85\))|ドロップターゲットとして使用されているときに MSHTML によって呼び出され、ホストが代替の[IDropTarget](/windows/win32/api/oleidl/nn-oleidl-idroptarget)を提供できるようにします。|
|[GetExternal](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753256\(v=vs.85\))|ホストの IDispatch インターフェイスを取得するために、MSHTML によって呼び出されます。|
|[GetHostInfo](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753257\(v=vs.85\))|MSHTML ホストの UI 機能を取得します。|
|[GetOptionKeyPath](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753258\(v=vs.85\))|MSHTML がユーザー設定を格納するレジストリキーを返します。|
|[HideUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753259\(v=vs.85\))|MSHTML がメニューとツールバーを削除するときに呼び出されます。|
|[OnDocWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753261\(v=vs.85\))|[IOleInPlaceActiveObject:: OnDocWindowActivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-ondocwindowactivate)の MSHTML 実装から呼び出されます。|
|[OnFrameWindowActivate](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753262\(v=vs.85\))|[IOleInPlaceActiveObject:: Onフレーム Windowactivate](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-onframewindowactivate)の MSHTML 実装から呼び出されます。|
|[ResizeBorder](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753263\(v=vs.85\))|[IOleInPlaceActiveObject:: ResizeBorder](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-resizeborder)の MSHTML 実装から呼び出されます。|
|[ShowContextMenu](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753264\(v=vs.85\))|コンテキストメニューを表示するために、MSHTML から呼び出されます。|
|[ShowUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753265\(v=vs.85\))|ホストが MSHTML メニューとツールバーを置き換えることを許可します。|
|[TranslateAccelerator](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753266\(v=vs.85\))|[IOleInPlaceActiveObject:: TranslateAccelerator](/windows/win32/api/oleidl/nf-oleidl-ioleinplaceactiveobject-translateaccelerator)または[IOleControlSite:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-iolecontrolsite-translateaccelerator)が呼び出されたときに、MSHTML によって呼び出されます。|
|[TranslateUrl](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753267\(v=vs.85\))|読み込まれる URL をホストが変更できるようにするために、MSHTML によって呼び出されます。|
|[UpdateUI](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753268\(v=vs.85\))|コマンドの状態が変化したことをホストに通知します。|

## <a name="remarks"></a>Remarks

ホストは、このインターフェイスを実装することによって、Microsoft HTML 解析およびレンダリングエンジン (MSHTML) で使用されるメニュー、ツールバー、およびコンテキストメニューを置き換えることができます。

## <a name="requirements"></a>必要条件

このインターフェイスの定義は、次に示すようC++に IDL またはとして使用できます。

|定義の種類|File|
|---------------------|----------|
|IDL|ATLIFace|
|C++|ATLIFace (ATLBase. h にも含まれる)|

## <a name="see-also"></a>関連項目

[IDocUIHostHandler](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa753260\(v=vs.85\))
