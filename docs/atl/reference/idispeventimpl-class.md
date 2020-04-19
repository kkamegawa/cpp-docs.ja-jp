---
title: IDispEventImpl クラス
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: e82a397b6d2abb66f773908c72a287c979e5ae1d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495932"
---
# <a name="idispeventimpl-class"></a>IDispEventImpl クラス

このクラスは、 `IDispatch`メソッドの実装を提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>パラメーター

*nID*<br/>
ソースオブジェクトの一意の識別子。 が`IDispEventImpl`複合コントロールの基底クラスである場合は、このパラメーターに対して目的のコントロールのリソース ID を使用します。 それ以外の場合は、任意の正の整数を使用します。

*T*<br/>
から`IDispEventImpl`派生したユーザーのクラス。

*pdiid*<br/>
このクラスによって実装されるイベントディスパッチインターフェイスの IID へのポインター。 このインターフェイスは、 *plibid*、 *wmajor*、および*wmajor*で表されるタイプライブラリで定義されている必要があります。

*plibid*<br/>
*Pdiid*が指すディスパッチインターフェイスを定義するタイプライブラリへのポインター。 **GUID_NULL を &** すると、イベントの発生元のオブジェクトからタイプライブラリが読み込まれます。

*wMajor*<br/>
タイプ ライブラリのメジャー バージョンです。 既定値は 0 です。

*wMinor*<br/>
タイプ ライブラリのマイナー バージョンです。 既定値は 0 です。

*tihclass*<br/>
*T*の型情報の管理に使用されるクラス。既定値は型`CComTypeInfoHolder`のクラスです。ただし、以外`CComTypeInfoHolder`の型のクラスを指定することで、このテンプレートパラメーターをオーバーライドできます。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[IDispEventImpl:: tihclass](../../atl/reference/idispeventimpl-class.md)|型情報の管理に使用されるクラス。 既定では`CComTypeInfoHolder`、です。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[IDispEventImpl:: IDispEventImpl](#idispeventimpl)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[IDispEventImpl:: Getファンク Infofromid](#getfuncinfofromid)|指定されたディスパッチ識別子の関数インデックスを検索します。|
|[IDispEventImpl:: Idispatch.getidsofnames](#getidsofnames)|1つのメンバーと省略可能な引数名のセットを、対応する一連の整数 Dispid にマップします。|
|[IDispEventImpl:: GetTypeInfo](#gettypeinfo)|オブジェクトの型情報を取得します。|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|型情報インターフェイスの数を取得します。|
|[IDispEventImpl:: Getuserの種類](#getuserdefinedtype)|ユーザー定義型の基本型を取得します。|

## <a name="remarks"></a>Remarks

`IDispEventImpl`インターフェイスのすべてのメソッド/イベントに対して実装コードを指定することなく、イベントディスパッチインターフェイスを実装する方法を提供します。 `IDispEventImpl``IDispatch`メソッドの実装を提供します。 必要なのは、処理するイベントの実装を指定することだけです。

`IDispEventImpl`は、クラスのイベントシンクマップと連携して、適切なハンドラー関数にイベントをルーティングします。 このクラスを使用するには:

処理する各オブジェクトのイベントごとに、イベントシンクマップに[SINK_ENTRY](composite-control-macros.md#sink_entry)マクロまたは[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)マクロを追加します。 複合コントロール`IDispEventImpl`の基底クラスとしてを使用する場合は、 [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap)を呼び出して、イベントシンクマップ内のすべてのエントリのイベントソースとの接続を確立し、破棄することができます。 それ以外の場合、またはより詳細な制御を行うには、 [Dispeventadvise](idispeventsimpleimpl-class.md#dispeventadvise)を呼び出して、ソースオブジェクトと基本クラスの間の接続を確立します。 [Dispeventunadvise](idispeventsimpleimpl-class.md#dispeventunadvise)を呼び出して、接続を切断します。

イベントを処理する`IDispEventImpl`必要があるオブジェクトごとに、( *nID*に一意の値を使用して) から派生する必要があります。 1つのソースオブジェクトに対して unadvising で基底クラスを再利用し、別のソースオブジェクトに対してアドバイズすることができますが、一度に1つのオブジェクトによって処理できるソース`IDispEventImpl`オブジェクトの最大数は、基本クラスの数によって制限されます。

`IDispEventImpl`は[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)と同じ機能を提供しますが、 [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)構造体へのポインターとして指定するのではなく、タイプライブラリからインターフェイスに関する型情報を取得する点が異なります。 イベント`IDispEventSimpleImpl`インターフェイスを記述するタイプライブラリがない場合、またはタイプライブラリの使用に関連するオーバーヘッドを回避する場合は、を使用します。

> [!NOTE]
> `IDispEventImpl`と`IDispEventSimpleImpl`は、各`IUnknown::QueryInterface` `IDispEventImpl` と`IDispEventSimpleImpl`基本クラスが個別の com id として機能できるようにするための独自の実装を提供し、メイン com オブジェクトのクラスメンバーに直接アクセスできるようにします。

CE ATL の ActiveX イベントシンクの実装では、イベントハンドラーメソッドから HRESULT 型または void 型の戻り値のみがサポートされます。その他の戻り値はサポートされておらず、その動作は未定義です。

詳細については、「 [IDispEventImpl のサポート](../../atl/supporting-idispeventimpl.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlcom. h

##  <a name="getfuncinfofromid"></a>  IDispEventImpl::GetFuncInfoFromId

指定されたディスパッチ識別子の関数インデックスを検索します。

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>パラメーター

*iid*<br/>
から関数の ID への参照。

*dispidMember*<br/>
から関数のディスパッチ ID。

*lcid*<br/>
から関数 ID のロケールコンテキスト。

*インフォメーション*<br/>
から関数の呼び出し方法を示す構造体。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

##  <a name="getidsofnames"></a>IDispEventImpl:: Idispatch.getidsofnames

1つのメンバーと省略可能な引数名のセットを、それ以降の[IDispatch:: Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke)への呼び出しで使用できる、対応する整数の dispid のセットにマップします。

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IDispatch:: idispatch.getidsofnames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) 」を参照してください。

##  <a name="gettypeinfo"></a>  IDispEventImpl::GetTypeInfo

オブジェクトの型情報を取得します。この型情報を使用して、インターフェイスの型情報を取得できます。

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Remarks

##  <a name="gettypeinfocount"></a>  IDispEventImpl::GetTypeInfoCount

オブジェクトが提供する型情報インターフェイスの数 (0 または 1) を取得します。

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Remarks

Windows SDK の「 [IDispatch:: GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) 」を参照してください。

##  <a name="getuserdefinedtype"></a>IDispEventImpl:: Getuserの種類

ユーザー定義型の基本型を取得します。

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>パラメーター

*pTI*<br/>
からユーザー定義型を格納している[ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo)インターフェイスへのポインター。

*hrt*<br/>
から取得する型の説明を指定するハンドル。

### <a name="return-value"></a>戻り値

バリアントの型。

### <a name="remarks"></a>Remarks

「 [ITypeInfo:: GetRefTypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo)」を参照してください。

##  <a name="idispeventimpl"></a>  IDispEventImpl::IDispEventImpl

コンストラクターです。 クラステンプレートパラメーター *plibid*、 *pdiid*、 *Wmajor*、および*wmajor*の値を格納します。

```
IDispEventImpl();
```

##  <a name="tihclass"></a>  IDispEventImpl::tihclass

この typedef は、クラステンプレートパラメーター *tihclass*のインスタンスです。

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Remarks

既定では、クラスは`CComTypeInfoHolder`です。 `CComTypeInfoHolder`クラスの型情報を管理します。

## <a name="see-also"></a>関連項目

[_ATL_FUNC_INFO 構造体](../../atl/reference/atl-func-info-structure.md)<br/>
[IDispatchImpl クラス](../../atl/reference/idispatchimpl-class.md)<br/>
[IDispEventSimpleImpl クラス](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
