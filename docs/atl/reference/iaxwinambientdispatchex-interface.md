---
title: IAxWinAmbientDispatchEx インターフェイス
ms.date: 11/04/2016
f1_keywords:
- IAxWinAmbientDispatchEx
- ATLIFACE/ATL::IAxWinAmbientDispatchEx
- ATLIFACE/ATL::SetAmbientDispatch
helpviewer_keywords:
- IAxWinAmbientDispatchEx interface
ms.assetid: 2c25e079-6128-4278-bc72-b2c6195ba7ef
ms.openlocfilehash: 638152d8c49bd20742a586bc665efcdb662b6f3a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62276095"
---
# <a name="iaxwinambientdispatchex-interface"></a>IAxWinAmbientDispatchEx インターフェイス

このインターフェイスは、ホストされるコントロールの補足のアンビエント プロパティを実装します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
MIDL_INTERFACE("B2D0778B - AC99 - 4c58 - A5C8 - E7724E5316B5") IAxWinAmbientDispatchEx : public IAxWinAmbientDispatch
```

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[SetAmbientDispatch](#setambientdispatch)|このメソッドはユーザー定義のインターフェイスを持つ既定のアンビエント プロパティのインターフェイスを補完します。|

## <a name="remarks"></a>Remarks

ATL アプリケーションの ATL と ActiveX コントロール、特にアンビエント プロパティを持つ ActiveX コントロールのホストに静的にリンクされている、このインターフェイスがあります。 このインターフェイスを含まない、このアサーションが生成されます。「を忘れました:term に LIBID を渡す」

このインターフェイスは、オブジェクトのホスト、ATL の ActiveX コントロールによって公開されます。 派生した[IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md)、`IAxWinAmbientDispatchEx`を独自のいずれかで、ATL によって提供されるアンビエント プロパティのインターフェイスを補うことができるメソッドを追加します。

<xref:System.Windows.Forms.AxHost> に関する型情報を読み込んでみます`IAxWinAmbientDispatch`と`IAxWinAmbientDispatchEx`コードを含むタイプ ライブラリから。

ATL90.dll にリンクしている場合**AXHost**は DLL 内のタイプ ライブラリから型情報を読み込みます。

参照してください[ActiveX コントロール ATL を使用しての AXHost をホストしている](../../atl/hosting-activex-controls-using-atl-axhost.md)の詳細。

## <a name="requirements"></a>必要条件

このインターフェイスの定義は、次の表に示すようにさまざまな形式で使用できます。

|定義の種類|ファイル|
|---------------------|----------|
|IDL|atliface.idl|
|タイプ ライブラリ|ATL.dll|
|C++|atliface.h (ATLBase.h にも含まれています)|

##  <a name="setambientdispatch"></a>  IAxWinAmbientDispatchEx::SetAmbientDispatch

このメソッドはユーザー定義のインターフェイスを持つ既定のアンビエント プロパティのインターフェイスを補完します。

```
virtual HRESULT STDMETHODCALLTYPE SetAmbientDispatch(IDispatch* pDispatch) = 0;
```

### <a name="parameters"></a>パラメーター

*pDispatch*<br/>
新しいインターフェイスへのポインター。

### <a name="return-value"></a>戻り値

成功した場合、S_OK または失敗時にエラーの hresult 値を返します。

### <a name="remarks"></a>Remarks

ときに`SetAmbientDispatch`呼びますプロパティやメソッドでこれらのプロパティが既に提供されていない場合、ホストされるコントロールでのよく寄せられるすべての呼び出しに、この新しいインターフェイスを使用と新しいインターフェイスへのポインター、 [IAxWinAmbientDispatch](../../atl/reference/iaxwinambientdispatch-interface.md).

## <a name="see-also"></a>関連項目

[IAxWinAmbientDispatch インターフェイス](../../atl/reference/iaxwinambientdispatch-interface.md)
