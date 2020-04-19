---
title: CPropExchange クラス
ms.date: 11/04/2016
f1_keywords:
- CPropExchange
- AFXCTL/CPropExchange
- AFXCTL/CPropExchange::ExchangeBlobProp
- AFXCTL/CPropExchange::ExchangeFontProp
- AFXCTL/CPropExchange::ExchangePersistentProp
- AFXCTL/CPropExchange::ExchangeProp
- AFXCTL/CPropExchange::ExchangeVersion
- AFXCTL/CPropExchange::GetVersion
- AFXCTL/CPropExchange::IsAsynchronous
- AFXCTL/CPropExchange::IsLoading
helpviewer_keywords:
- CPropExchange [MFC], ExchangeBlobProp
- CPropExchange [MFC], ExchangeFontProp
- CPropExchange [MFC], ExchangePersistentProp
- CPropExchange [MFC], ExchangeProp
- CPropExchange [MFC], ExchangeVersion
- CPropExchange [MFC], GetVersion
- CPropExchange [MFC], IsAsynchronous
- CPropExchange [MFC], IsLoading
ms.assetid: ed872180-e770-4942-892a-92139d501fab
ms.openlocfilehash: e9ad7c363f2580200af20baeb0acd7a93c1f603b
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78871772"
---
# <a name="cpropexchange-class"></a>CPropExchange クラス

OLE コントロールの永続性の実装をサポートします。

## <a name="syntax"></a>構文

```
class AFX_NOVTABLE CPropExchange
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|Description|
|----------|-----------------|
|[CPropExchange:: ExchangeBlobProp](#exchangeblobprop)|バイナリラージオブジェクト (BLOB) プロパティを交換します。|
|[CPropExchange::ExchangeFontProp](#exchangefontprop)|フォントプロパティを交換します。|
|[CPropExchange::ExchangePersistentProp](#exchangepersistentprop)|コントロールとファイルの間でプロパティを交換します。|
|[CPropExchange:: ExchangeProp](#exchangeprop)|任意の組み込み型のプロパティを交換します。|
|[CPropExchange:: ExchangeVersion](#exchangeversion)|OLE コントロールのバージョン番号を交換します。|
|[CPropExchange:: GetVersion](#getversion)|OLE コントロールのバージョン番号を取得します。|
|[CPropExchange:: IsAsynchronous](#isasynchronous)|プロパティ交換を非同期的に実行するかどうかを決定します。|
|[CPropExchange:: IsLoading](#isloading)|プロパティがコントロールに読み込まれるか、またはプロパティから保存されるかを示します。|

## <a name="remarks"></a>解説

`CPropExchange` には基底クラスがありません。

プロパティ交換のコンテキストと方向を確立します。

永続化とは、コントロール自体とメディアの間で、コントロールの状態情報を交換することです。通常は、プロパティによって表されます。

このフレームワークは、OLE コントロールのプロパティが永続ストレージから読み込まれるか、永続ストレージに格納されることが通知されるときに、`CPropExchange` から派生したオブジェクトを構築します。

フレームワークは、この `CPropExchange` オブジェクトへのポインターをコントロールの `DoPropExchange` 関数に渡します。 ウィザードを使用してコントロールのスターターファイルを作成した場合、コントロールの `DoPropExchange` 関数は `COleControl::DoPropExchange`を呼び出します。 基本クラスのバージョンは、コントロールのストックプロパティを交換します。派生クラスのバージョンを変更して、コントロールに追加したプロパティを交換します。

`CPropExchange` を使用すると、コントロールのプロパティをシリアル化したり、コントロールの読み込み時または作成時にコントロールのプロパティを初期化したりすることができます。 `CPropExchange` の `ExchangeProp` および `ExchangeFontProp` メンバー関数は、さまざまなメディアにプロパティを格納して読み込むことができます。

`CPropExchange`の使用方法の詳細については、「 [MFC ActiveX コントロール: プロパティページ](../../mfc/mfc-activex-controls-property-pages.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`CPropExchange`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxctl.h

##  <a name="exchangeblobprop"></a>CPropExchange:: ExchangeBlobProp

バイナリラージオブジェクト (BLOB) データを格納するプロパティをシリアル化します。

```
virtual BOOL ExchangeBlobProp(
    LPCTSTR pszPropName,
    HGLOBAL* phBlob,
    HGLOBAL hBlobDefault = NULL) = 0;
```

### <a name="parameters"></a>パラメーター

*pszPropName*<br/>
交換されるプロパティの名前。

*phBlob*<br/>
プロパティが格納されている場所を指す変数へのポインター (変数は、通常、クラスのメンバーです)。

*hBlobDefault*<br/>
プロパティの既定値。

### <a name="return-value"></a>戻り値

交換が成功した場合は0以外の。失敗した場合は0。

### <a name="remarks"></a>解説

プロパティの値は、 *Phblob*によって参照される変数と同じように読み取りまたは書き込みを行います。 *Hblobdefault*が指定されている場合は、プロパティの既定値として使用されます。 この値は、何らかの理由でコントロールのシリアル化が失敗した場合に使用されます。

関数 `CArchivePropExchange::ExchangeBlobProp`、`CResetPropExchange::ExchangeBlobProp`、および `CPropsetPropExchange::ExchangeBlobProp` は、この純粋仮想関数をオーバーライドします。

##  <a name="exchangefontprop"></a>CPropExchange::ExchangeFontProp

ストレージメディアとコントロールの間でフォントプロパティを交換します。

```
virtual BOOL ExchangeFontProp(
    LPCTSTR pszPropName,
    CFontHolder& font,
    const FONTDESC* pFontDesc,
    LPFONTDISP pFontDispAmbient) = 0;
```

### <a name="parameters"></a>パラメーター

*pszPropName*<br/>
交換されるプロパティの名前。

*font*<br/>
Font プロパティを含む[CFontHolder](../../mfc/reference/cfontholder-class.md)オブジェクトへの参照です。

*pFontDesc*<br/>
*Pfontdispambient*が NULL の場合にフォントプロパティの既定の状態を初期化するための値を格納している、 [fontdesc](/windows/win32/api/olectl/ns-olectl-fontdesc)構造体へのポインター。

*pFontDispAmbient*<br/>
フォントプロパティの既定の状態を初期化するために使用されるフォントの `IFontDisp` インターフェイスへのポインター。

### <a name="return-value"></a>戻り値

交換が成功した場合は0以外の。失敗した場合は0。

### <a name="remarks"></a>解説

フォントプロパティをメディアからコントロールに読み込んでいる場合は、フォントの特性がメディアから取得され、*フォント*によって参照される `CFontHolder` オブジェクトが初期化されます。 フォントプロパティが格納されている場合は、フォントオブジェクトの特性がメディアに書き込まれます。

関数 `CArchivePropExchange::ExchangeFontProp`、`CResetPropExchange::ExchangeFontProp`、および `CPropsetPropExchange::ExchangeFontProp` は、この純粋仮想関数をオーバーライドします。

##  <a name="exchangepersistentprop"></a>CPropExchange::ExchangePersistentProp

コントロールとファイルの間でプロパティを交換します。

```
virtual BOOL ExchangePersistentProp(
    LPCTSTR pszPropName,
    LPUNKNOWN* ppUnk,
    REFIID iid,
    LPUNKNOWN pUnkDefault) = 0;
```

### <a name="parameters"></a>パラメーター

*pszPropName*<br/>
交換されるプロパティの名前。

*ppUnk*<br/>
プロパティの `IUnknown` インターフェイスへのポインターを格納している変数へのポインター (この変数は、通常はクラスのメンバー)。

*iid*<br/>
コントロールが使用するプロパティのインターフェイスのインターフェイス ID。

*pUnkDefault*<br/>
プロパティの既定値。

### <a name="return-value"></a>戻り値

交換が成功した場合は0以外の。失敗した場合は0。

### <a name="remarks"></a>解説

プロパティがファイルからコントロールに読み込まれている場合、プロパティが作成され、ファイルから初期化されます。 プロパティが格納されている場合、その値はファイルに書き込まれます。

関数 `CArchivePropExchange::ExchangePersistentProp`、`CResetPropExchange::ExchangePersistentProp`、および `CPropsetPropExchange::ExchangePersistentProp` は、この純粋仮想関数をオーバーライドします。

##  <a name="exchangeprop"></a>CPropExchange:: ExchangeProp

ストレージメディアとコントロールの間でプロパティを交換します。

```
virtual BOOL ExchangeProp(
    LPCTSTR pszPropName,
    VARTYPE vtProp,
    void* pvProp,
    const void* pvDefault = NULL) = 0 ;
```

### <a name="parameters"></a>パラメーター

*pszPropName*<br/>
交換されるプロパティの名前。

*vtProp*<br/>
交換されるプロパティの型を指定するシンボル。 次のいずれかの値になります。

|Symbol|プロパティの型|
|------------|-------------------|
|VT_I2|**short**|
|VT_I4|**long**|
|VT_BOOL|**BOOL**|
|VT_BSTR|`CString`|
|VT_CY|**暦年**|
|VT_R4|**float**|
|VT_R8|**double**|

*pvProp*<br/>
プロパティの値へのポインター。

*pvDefault*<br/>
プロパティの既定値へのポインター。

### <a name="return-value"></a>戻り値

交換が成功した場合は0以外の。失敗した場合は0。

### <a name="remarks"></a>解説

プロパティをメディアからコントロールに読み込んでいる場合は、プロパティの値が中から取得され、 *Pvprop*が指すオブジェクトに格納されます。 プロパティがメディアに格納されている場合は、 *Pvprop*が指すオブジェクトの値がメディアに書き込まれます。

関数 `CArchivePropExchange::ExchangeProp`、`CResetPropExchange::ExchangeProp`、および `CPropsetPropExchange::ExchangeProp` は、この純粋仮想関数をオーバーライドします。

##  <a name="exchangeversion"></a>CPropExchange:: ExchangeVersion

バージョン番号の永続化を処理するためにフレームワークによって呼び出されます。

```
virtual BOOL ExchangeVersion(
    DWORD& dwVersionLoaded,
    DWORD dwVersionDefault,
    BOOL bConvert);
```

### <a name="parameters"></a>パラメーター

*dwVersionLoaded*<br/>
読み込まれる永続データのバージョン番号が格納される変数への参照。

*dwVersionDefault*<br/>
コントロールの現在のバージョン番号。

*bConvert*<br/>
永続データを現在のバージョンに変換するか、または読み込まれたのと同じバージョンに保持するかを示します。

### <a name="return-value"></a>戻り値

関数が成功した場合は0以外の場合は。それ以外の場合は0。

##  <a name="getversion"></a>CPropExchange:: GetVersion

コントロールのバージョン番号を取得するには、この関数を呼び出します。

```
DWORD GetVersion();
```

### <a name="return-value"></a>戻り値

コントロールのバージョン番号。

##  <a name="isasynchronous"></a>CPropExchange:: IsAsynchronous

プロパティ交換を非同期的に実行するかどうかを決定します。

```
BOOL IsAsynchronous();
```

### <a name="return-value"></a>戻り値

プロパティが非同期に交換される場合は TRUE、それ以外の場合は FALSE を返します。

##  <a name="isloading"></a>CPropExchange:: IsLoading

この関数を呼び出して、プロパティがコントロールに読み込まれているか、またはプロパティから保存されているかどうかを確認します。

```
BOOL IsLoading();
```

### <a name="return-value"></a>戻り値

プロパティが読み込まれている場合は0以外。それ以外の場合は0です。

## <a name="see-also"></a>参照

[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleControl::D oPropExchange](../../mfc/reference/colecontrol-class.md#dopropexchange)
