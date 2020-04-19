---
title: CBindStatusCallback クラス
ms.date: 11/04/2016
f1_keywords:
- CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::CBindStatusCallback
- ATLCTL/ATL::CBindStatusCallback::Download
- ATLCTL/ATL::CBindStatusCallback::GetBindInfo
- ATLCTL/ATL::CBindStatusCallback::GetPriority
- ATLCTL/ATL::CBindStatusCallback::OnDataAvailable
- ATLCTL/ATL::CBindStatusCallback::OnLowResource
- ATLCTL/ATL::CBindStatusCallback::OnObjectAvailable
- ATLCTL/ATL::CBindStatusCallback::OnProgress
- ATLCTL/ATL::CBindStatusCallback::OnStartBinding
- ATLCTL/ATL::CBindStatusCallback::OnStopBinding
- ATLCTL/ATL::CBindStatusCallback::StartAsyncDownload
- ATLCTL/ATL::CBindStatusCallback::m_dwAvailableToRead
- ATLCTL/ATL::CBindStatusCallback::m_dwTotalRead
- ATLCTL/ATL::CBindStatusCallback::m_pFunc
- ATLCTL/ATL::CBindStatusCallback::m_pT
- ATLCTL/ATL::CBindStatusCallback::m_spBindCtx
- ATLCTL/ATL::CBindStatusCallback::m_spBinding
- ATLCTL/ATL::CBindStatusCallback::m_spMoniker
- ATLCTL/ATL::CBindStatusCallback::m_spStream
helpviewer_keywords:
- asynchronous data transfer [C++]
- data transfer [C++]
- data transfer [C++], asynchronous
- CBindStatusCallback class
ms.assetid: 0f5da276-6031-4418-b2a9-a4750ef29e77
ms.openlocfilehash: 89c65ff034cf7471c379b28116a741b62269a00c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497601"
---
# <a name="cbindstatuscallback-class"></a>CBindStatusCallback クラス

このクラスは、 `IBindStatusCallback` インターフェイスを実装します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T,
    int nBindFlags = BINDF_ASYNCHRONOUS | BINDF_ASYNCSTORAGE | BINDF_GETNEWESTVERSION | BINDF_NOWRITECACHE>
class ATL_NO_VTABLE CBindStatusCallback : public CComObjectRootEx <T ::_ThreadModel::ThreadModelNoCS>,
    public IBindStatusCallbackImpl<T>
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
データの受信時に呼び出される関数を含むクラス。

*nBindFlags*<br/>
[Getbindinfo](#getbindinfo)によって返されるバインドフラグを指定します。 既定の実装は、バインディングを非同期に設定し、データ/オブジェクトの最新バージョンを取得し、取得したデータをディスクキャッシュに格納しません。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CBindStatusCallback::CBindStatusCallback](#cbindstatuscallback)|コンストラクターです。|
|[CBindStatusCallback:: ~ CBindStatusCallback](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CBindStatusCallback::D o)](#download)|ダウンロードプロセスを開始し、 `CBindStatusCallback`オブジェクトを作成し、を呼び出す`StartAsyncDownload`静的メソッド。|
|[CBindStatusCallback::GetBindInfo](#getbindinfo)|作成されるバインドの種類に関する情報を要求するために、非同期モニカーによって呼び出されます。|
|[CBindStatusCallback:: GetPriority](#getpriority)|バインド操作の優先順位を取得するために、非同期モニカーによって呼び出されます。 ATL の実装は`E_NOTIMPL`を返します。|
|[CBindStatusCallback::OnDataAvailable](#ondataavailable)|使用可能になったときにアプリケーションにデータを提供するために呼び出されます。 データを読み取り、そのデータを使用するために渡された関数を呼び出します。|
|[CBindStatusCallback::OnLowResource](#onlowresource)|リソースが不足しているときに呼び出されます。 ATL 実装は S_OK を返します。|
|[CBindStatusCallback::OnObjectAvailable](#onobjectavailable)|オブジェクトインターフェイスポインターをアプリケーションに渡すために、非同期モニカーによって呼び出されます。 ATL 実装は S_OK を返します。|
|[CBindStatusCallback::OnProgress](#onprogress)|データダウンロードプロセスの進行状況を示すために呼び出されます。 ATL 実装は S_OK を返します。|
|[CBindStatusCallback:: OnStartBinding](#onstartbinding)|バインディングの開始時に呼び出されます。|
|[CBindStatusCallback:: OnStopBinding](#onstopbinding)|非同期データ転送が停止したときに呼び出されます。|
|[CBindStatusCallback::StartAsyncDownload](#startasyncdownload)|使用可能なバイト数と読み取りバイト数をゼロに初期化し、URL からプッシュ型ストリームオブジェクトを作成`OnDataAvailable`し、データが使用可能になるたびにを呼び出します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CBindStatusCallback::m_dwAvailableToRead](#m_dwavailabletoread)|読み取り可能なバイト数。|
|[CBindStatusCallback::m_dwTotalRead](#m_dwtotalread)|読み取った合計バイト数。|
|[CBindStatusCallback::m_pFunc](#m_pfunc)|データが使用可能な場合に呼び出される関数へのポインター。|
|[CBindStatusCallback::m_pT](#m_pt)|非同期データ転送を要求しているオブジェクトへのポインター。|
|[CBindStatusCallback::m_spBindCtx](#m_spbindctx)|現在のバインド操作の[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)インターフェイスへのポインター。|
|[CBindStatusCallback::m_spBinding](#m_spbinding)|現在のバインド`IBinding`操作のインターフェイスへのポインター。|
|[CBindStatusCallback::m_spMoniker](#m_spmoniker)|使用する URL の[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)インターフェイスへのポインター。|
|[CBindStatusCallback::m_spStream](#m_spstream)|データ転送用の[IStream](/windows/win32/api/objidl/nn-objidl-istream)インターフェイスへのポインター。|

## <a name="remarks"></a>Remarks

`CBindStatusCallback` クラスは、`IBindStatusCallback` インターフェイスを実装します。 `IBindStatusCallback`は、非同期データ転送から通知を受信できるように、アプリケーションによって実装される必要があります。 システムによって提供される非同期`IBindStatusCallback`モニカーは、メソッドを使用して、オブジェクトとの間の非同期データ転送に関する情報を送受信します。

通常、 `CBindStatusCallback`オブジェクトは特定のバインド操作に関連付けられています。 たとえば、 [ASYNC](../../overview/visual-cpp-samples.md)サンプルでは、URL プロパティを設定すると、へ`CBindStatusCallback` `Download`の呼び出しにオブジェクトが作成されます。

[!code-cpp[NVC_ATL_Windowing#86](../../atl/codesnippet/cpp/cbindstatuscallback-class_1.h)]

非同期モニカーは、データがある`OnData`場合に、コールバック関数を使用してアプリケーションを呼び出します。 非同期モニカーは、システムによって提供されます。

## <a name="inheritance-hierarchy"></a>継承階層

`CComObjectRootBase`

`IBindStatusCallback`

[CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md)

`CBindStatusCallback`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlctl. h

##  <a name="cbindstatuscallback"></a>CBindStatusCallback::CBindStatusCallback

コンストラクターです。

```
CBindStatusCallback();
```

### <a name="remarks"></a>Remarks

非同期データ転送に関する通知を受信するオブジェクトを作成します。 通常、バインド操作ごとに1つのオブジェクトが作成されます。

また、コンストラクターは、 [m_pT](#m_pt)と[m_pFunc](#m_pfunc)を NULL に初期化します。

##  <a name="dtor"></a>CBindStatusCallback:: ~ CBindStatusCallback

デストラクターです。

```
~CBindStatusCallback();
```

### <a name="remarks"></a>Remarks

割り当てられたすべてのリソースを解放します。

##  <a name="download"></a>CBindStatusCallback::D o)

オブジェクトを`CBindStatusCallback`作成し、 `StartAsyncDownload`を呼び出して、指定した URL からデータの非同期ダウンロードを開始します。

```
static HRESULT Download(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
から非同期データ転送を要求しているオブジェクトへのポインター。 オブジェクト`CBindStatusCallback`は、このオブジェクトのクラスでテンプレート化されています。

*pFunc*<br/>
から読み取られるデータを受け取る関数へのポインター。 関数は、オブジェクトの型`T`のクラスのメンバーです。 構文と例については、「 [StartAsyncDownload](#startasyncdownload) 」を参照してください。

*bstrURL*<br/>
からデータの取得元の URL。 には、任意の有効な URL またはファイル名を指定できます。 Nll は指定できません。 例:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
からコンテナー `IUnknown`の。 既定では NULL です。

*bRelative*<br/>
からURL が相対パスか絶対パスかを示すフラグ。 既定では FALSE です。つまり、URL は absolute です。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

データが使用可能になるたびに、によって`OnDataAvailable`オブジェクトに送信されます。 `OnDataAvailable`データを読み取り、 *Pfunc*が指す関数を呼び出します (たとえば、データを格納したり画面に出力したりする場合)。

##  <a name="getbindinfo"></a>  CBindStatusCallback::GetBindInfo

モニカーにバインドする方法を指示するために呼び出されます。

```
STDMETHOD(GetBindInfo)(
    DWORD* pgrfBSCF,
    BINDINFO* pbindinfo);
```

### <a name="parameters"></a>パラメーター

*pgrfBSCF*<br/>
入出力バインド操作の実行方法を示す BINDF 列挙値へのポインター。 既定では、には次の列挙値が設定されます。

BINDF_ASYNCHRONOUS 非同期ダウンロード。

BINDF_ASYNCSTORAGE `OnDataAvailable`は、データが使用可能になるまでブロックするのではなく、データがまだ使用できない場合に E_PENDING を返します。

BINDF_GETNEWESTVERSION バインド操作は、最新バージョンのデータを取得する必要があります。

BINDF_NOWRITECACHE バインド操作では、取得したデータをディスクキャッシュに格納することはできません。

*pbindinfo*<br/>
[入力、出力]オブジェクトがどのよう`BINDINFO`にバインドを必要とするかについての詳細情報を提供する構造体へのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

既定の実装は、バインディングを非同期に設定し、データプッシュモデルを使用します。 データプッシュモデルでは、モニカーによって非同期バインド操作が実行され、新しいデータが利用可能になると常にクライアントに通知されます。

##  <a name="getpriority"></a>  CBindStatusCallback::GetPriority

バインド操作の優先順位を取得するために、非同期モニカーによって呼び出されます。

```
STDMETHOD(GetPriority)(LONG* pnPriority);
```

### <a name="parameters"></a>パラメーター

*pnPriority*<br/>
入出力成功時に優先順位を受け取る**LONG**変数のアドレス。

### <a name="return-value"></a>戻り値

E_NOTIMPL を返します。

##  <a name="m_dwavailabletoread"></a>CBindStatusCallback::m_dwAvailableToRead

読み取り可能なバイト数を格納するために使用できます。

```
DWORD m_dwAvailableToRead;
```

### <a name="remarks"></a>Remarks

で`StartAsyncDownload`0 に初期化されます。

##  <a name="m_dwtotalread"></a>  CBindStatusCallback::m_dwTotalRead

非同期データ転送で読み取られたバイトの累積合計。

```
DWORD m_dwTotalRead;
```

### <a name="remarks"></a>Remarks

`OnDataAvailable`が実際に読み取られたバイト数によって呼び出されるたびにインクリメントされます。 で`StartAsyncDownload`0 に初期化されます。

##  <a name="m_pfunc"></a>CBindStatusCallback::m_pFunc

によっ`m_pFunc`てポイントされる関数は`OnDataAvailable` 、使用可能なデータを読み取る (たとえば、データを格納したり画面に出力したりする) と、によって呼び出されます。

```
ATL_PDATAAVAILABLE m_pFunc;
```

### <a name="remarks"></a>Remarks

`m_pFunc`が指す関数は、オブジェクトのクラスのメンバーであり、次の構文を使用します。

```
void Function_Name(
   CBindStatusCallback<T>* pbsc,
   BYTE* pBytes,
   DWORD dwSize
   );
```

##  <a name="m_pt"></a>  CBindStatusCallback::m_pT

非同期データ転送を要求しているオブジェクトへのポインター。

```
T* m_pT;
```

### <a name="remarks"></a>Remarks

オブジェクト`CBindStatusCallback`は、このオブジェクトのクラスでテンプレート化されています。

##  <a name="m_spbindctx"></a>  CBindStatusCallback::m_spBindCtx

バインドコンテキスト (特定のモニカーバインディング操作に関する情報を格納するオブジェクト) へのアクセスを提供する[IBindCtx](/windows/win32/api/objidl/nn-objidl-ibindctx)インターフェイスへのポインター。

```
CComPtr<IBindCtx> m_spBindCtx;
```

### <a name="remarks"></a>Remarks

で`StartAsyncDownload`初期化されます。

##  <a name="m_spbinding"></a>  CBindStatusCallback::m_spBinding

現在のバインド操作`IBinding`のインターフェイスへのポインター。

```
CComPtr<IBinding> m_spBinding;
```

### <a name="remarks"></a>Remarks

で初期化され`OnStopBinding` 、で解放されました。`OnStartBinding`

##  <a name="m_spmoniker"></a>CBindStatusCallback::m_spMoniker

使用する URL の[IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)インターフェイスへのポインター。

```
CComPtr<IMoniker> m_spMoniker;
```

### <a name="remarks"></a>Remarks

で`StartAsyncDownload`初期化されます。

##  <a name="m_spstream"></a>  CBindStatusCallback::m_spStream

現在のバインド操作の[IStream](/windows/win32/api/objidl/nn-objidl-istream)インターフェイスへのポインター。

```
CComPtr<IStream> m_spStream;
```

### <a name="remarks"></a>Remarks

Bcsf `OnDataAvailable`フラグが`STGMEDIUM` BCSF_FIRSTDATANOTIFICATION で、bcsf フラグが BCSF_LASTDATANOTIFICATION のときに解放されたときに、構造体からで初期化されます。

##  <a name="ondataavailable"></a>  CBindStatusCallback::OnDataAvailable

システム提供の非同期モニカーは、 `OnDataAvailable`使用可能になったときにオブジェクトにデータを提供するためにを呼び出します。

```
STDMETHOD(
    OnDataAvailable)(DWORD grfBSCF,
    DWORD dwSize,
    FORMATETC* /* pformatetc */,
    STGMEDIUM* pstgmed);
```

### <a name="parameters"></a>パラメーター

*grfBSCF*<br/>
からBSCF 列挙値。 次の1つまたは複数を実行します。BSCF_FIRSTDATANOTIFICATION、BSCF_INTERMEDIARYDATANOTIFICATION、または BSCF_LASTDATANOTIFICATION。

*dwSize*<br/>
からバインドの開始以降に使用できるデータの累積量 (バイト単位)。 0を指定すると、データの量が関連していないこと、または特定の量が使用できなくなったことが示されます。

*pformatetc*<br/>
から使用可能なデータの形式を格納している[FORMATETC](/windows/win32/com/the-formatetc-structure)構造体へのポインター。 形式がない場合は、を CF_NULL にすることができます。

*pstgmed*<br/>
から使用できるようになった実際のデータを保持する[STGMEDIUM](/windows/win32/com/the-stgmedium-structure)構造体へのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

`OnDataAvailable`データを読み取り、オブジェクトのクラスのメソッドを呼び出します (たとえば、データを格納したり画面に出力したりする場合)。 詳細については、「 [CBindStatusCallback:: StartAsyncDownload](#startasyncdownload) 」を参照してください。

##  <a name="onlowresource"></a>  CBindStatusCallback::OnLowResource

リソースが不足しているときに呼び出されます。

```
STDMETHOD(OnLowResource)(DWORD /* dwReserved */);
```

### <a name="parameters"></a>パラメーター

*dwReserved*<br/>
予約済み。

### <a name="return-value"></a>戻り値

S_OK を返します。

##  <a name="onobjectavailable"></a>CBindStatusCallback::OnObjectAvailable

オブジェクトインターフェイスポインターをアプリケーションに渡すために、非同期モニカーによって呼び出されます。

```
STDMETHOD(OnObjectAvailable)(REFID /* riid */, IUnknown* /* punk */);
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
要求されたインターフェイスのインターフェイス識別子。 使用されません。

*パンク*<br/>
IUnknown インターフェイスのアドレス。 使用されません。

### <a name="return-value"></a>戻り値

S_OK を返します。

##  <a name="onprogress"></a>  CBindStatusCallback::OnProgress

データダウンロードプロセスの進行状況を示すために呼び出されます。

```
STDMETHOD(OnProgress)(
    ULONG /* ulProgress */,
    ULONG /* ulProgressMax */,
    ULONG /* ulStatusCode */,
    LPCWSTRONG /* szStatusText */);
```

### <a name="parameters"></a>パラメーター

*ulProgress*<br/>
符号なし長整数。 使用されません。

*ulProgressMax*<br/>
符号なし長整数値は使用されません。

*ulStatusCode*<br/>
符号なし長整数。 使用されません。

*szStatusText*<br/>
文字列値のアドレス。 使用されません。

### <a name="return-value"></a>戻り値

S_OK を返します。

##  <a name="onstartbinding"></a>  CBindStatusCallback::OnStartBinding

データメンバー [m_spBinding](#m_spbinding)を*pbinding*の`IBinding`ポインターに設定します。

```
STDMETHOD(OnStartBinding)(DWORD /* dwReserved */, IBinding* pBinding);
```

### <a name="parameters"></a>パラメーター

*dwReserved*<br/>
将来使用するために予約されています。

*pBinding*<br/>
から現在のバインド操作の IBinding インターフェイスのアドレス。 NULL にすることはできません。 クライアントは、このポインターで AddRef を呼び出して、バインドオブジェクトへの参照を保持する必要があります。

##  <a name="onstopbinding"></a>CBindStatusCallback:: OnStopBinding

データメンバー `IBinding` [m_spBinding](#m_spbinding)内のポインターを解放します。

```
STDMETHOD(OnStopBinding)(HRESULT hresult, LPCWSTR /* szError */);
```

### <a name="parameters"></a>パラメーター

*hresult*<br/>
バインド操作から返されたステータスコード。

*szError*<br/>
文字列値のアドレス。 使用されません。

### <a name="remarks"></a>Remarks

バインド操作の終了を示すために、システムによって提供される非同期モニカーによって呼び出されます。

##  <a name="startasyncdownload"></a>CBindStatusCallback::StartAsyncDownload

指定された URL からデータの非同期ダウンロードを開始します。

```
HRESULT StartAsyncDownload(
    T* pT,
    ATL_PDATAAVAILABLE pFunc,
    BSTR bstrURL,
    IUnknown* pUnkContainer = NULL,
    BOOL bRelative = FALSE);
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
から非同期データ転送を要求しているオブジェクトへのポインター。 オブジェクト`CBindStatusCallback`は、このオブジェクトのクラスでテンプレート化されています。

*pFunc*<br/>
から読み取るデータを受け取る関数へのポインター。 関数は、オブジェクトの型`T`のクラスのメンバーです。 構文と例については、「**解説**」を参照してください。

*bstrURL*<br/>
からデータの取得元の URL。 には、任意の有効な URL またはファイル名を指定できます。 Nll は指定できません。 例:

`CComBSTR mybstr =_T("http://somesite/data.htm")`

*pUnkContainer*<br/>
からコンテナー `IUnknown`の。 既定では NULL です。

*bRelative*<br/>
からURL が相対パスか絶対パスかを示すフラグ。 既定では FALSE です。つまり、URL は absolute です。

### <a name="return-value"></a>戻り値

標準の HRESULT 値の1つ。

### <a name="remarks"></a>Remarks

データが使用可能になるたびに、によって`OnDataAvailable`オブジェクトに送信されます。 `OnDataAvailable`データを読み取り、 *Pfunc*が指す関数を呼び出します (たとえば、データを格納したり画面に出力したりする場合)。

*Pfunc*が指す関数は、オブジェクトのクラスのメンバーであり、次の構文を使用します。

```
void Function_Name(
    CBindStatusCallback<T>* pbsc,
    BYTE* pBytes,
    DWORD dwSize);
```

( [ASYNC](../../overview/visual-cpp-samples.md)サンプルから取得した) 次の例では、 `OnData`関数は受信したデータをテキストボックスに書き込みます。

### <a name="example"></a>例

[!code-cpp[NVC_ATL_Windowing#87](../../atl/codesnippet/cpp/cbindstatuscallback-class_2.h)]

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
