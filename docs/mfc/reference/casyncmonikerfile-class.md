---
title: CAsyncMonikerFile クラス
ms.date: 11/04/2016
f1_keywords:
- CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::CAsyncMonikerFile
- AFXOLE/CAsyncMonikerFile::Close
- AFXOLE/CAsyncMonikerFile::GetBinding
- AFXOLE/CAsyncMonikerFile::GetFormatEtc
- AFXOLE/CAsyncMonikerFile::Open
- AFXOLE/CAsyncMonikerFile::CreateBindStatusCallback
- AFXOLE/CAsyncMonikerFile::GetBindInfo
- AFXOLE/CAsyncMonikerFile::GetPriority
- AFXOLE/CAsyncMonikerFile::OnDataAvailable
- AFXOLE/CAsyncMonikerFile::OnLowResource
- AFXOLE/CAsyncMonikerFile::OnProgress
- AFXOLE/CAsyncMonikerFile::OnStartBinding
- AFXOLE/CAsyncMonikerFile::OnStopBinding
helpviewer_keywords:
- CAsyncMonikerFile [MFC], CAsyncMonikerFile
- CAsyncMonikerFile [MFC], Close
- CAsyncMonikerFile [MFC], GetBinding
- CAsyncMonikerFile [MFC], GetFormatEtc
- CAsyncMonikerFile [MFC], Open
- CAsyncMonikerFile [MFC], CreateBindStatusCallback
- CAsyncMonikerFile [MFC], GetBindInfo
- CAsyncMonikerFile [MFC], GetPriority
- CAsyncMonikerFile [MFC], OnDataAvailable
- CAsyncMonikerFile [MFC], OnLowResource
- CAsyncMonikerFile [MFC], OnProgress
- CAsyncMonikerFile [MFC], OnStartBinding
- CAsyncMonikerFile [MFC], OnStopBinding
ms.assetid: 17378b66-a49a-4b67-88e3-7756ad26a2fc
ms.openlocfilehash: cd399368e46e4e9a86b4c6260e07aee07b80defb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507501"
---
# <a name="casyncmonikerfile-class"></a>CAsyncMonikerFile クラス

ActiveX コントロール (以前の OLE コントロール) で非同期モニカーを使用するための機能が用意されています。

## <a name="syntax"></a>構文

```
class CAsyncMonikerFile : public CMonikerFile
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAsyncMonikerFile::CAsyncMonikerFile](#casyncmonikerfile)|`CAsyncMonikerFile` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAsyncMonikerFile:: Close](#close)|すべてのリソースを閉じて解放します。|
|[CAsyncMonikerFile:: GetBinding](#getbinding)|非同期転送バインディングへのポインターを取得します。|
|[CAsyncMonikerFile::GetFormatEtc](#getformatetc)|ストリーム内のデータの形式を取得します。|
|[CAsyncMonikerFile:: Open](#open)|ファイルを非同期的に開きます。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAsyncMonikerFile::CreateBindStatusCallback](#createbindstatuscallback)|を実装`IBindStatusCallback`する COM オブジェクトを作成します。|
|[CAsyncMonikerFile:: GetBindInfo](#getbindinfo)|作成されるバインドの種類に関する情報を要求するために、OLE システムライブラリによって呼び出されます。|
|[CAsyncMonikerFile:: GetPriority](#getpriority)|バインディングの優先順位を取得するために、OLE システムライブラリによって呼び出されます。|
|[CAsyncMonikerFile::OnDataAvailable](#ondataavailable)|非同期バインド操作中にクライアントが使用できるようになると、データを提供するために呼び出されます。|
|[CAsyncMonikerFile:: OnLowResource](#onlowresource)|リソースが不足しているときに呼び出されます。|
|[CAsyncMonikerFile:: OnProgress](#onprogress)|データのダウンロードプロセスの進行状況を示すために呼び出されます。|
|[CAsyncMonikerFile::OnStartBinding](#onstartbinding)|バインディングの開始時に呼び出されます。|
|[CAsyncMonikerFile:: OnStopBinding](#onstopbinding)|非同期転送が停止したときに呼び出されます。|

## <a name="remarks"></a>Remarks

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)から派生し、 [COleStreamFile](../../mfc/reference/colestreamfile-class.md)から派生し、 `CAsyncMonikerFile` [IMoniker](/windows/win32/api/objidl/nn-objidl-imoniker)インターフェイスを使用して任意のデータストリームに非同期にアクセスします。これには、URL からのファイルの非同期読み込みも含まれます。 ファイルは、ActiveX コントロールのデータパスプロパティにすることができます。

非同期モニカーは、ファイル転送中に応答性の高いユーザーインターフェイスを提供するために、主にインターネット対応アプリケーションおよび ActiveX コントロールで使用されます。 この例では、 [CDataPathProperty](../../mfc/reference/cdatapathproperty-class.md)を使用して、ActiveX コントロールの非同期プロパティを提供しています。 オブジェクト`CDataPathProperty`は、長いプロパティ交換プロセス中に新しいデータが使用可能であることを示すコールバックを繰り返し取得します。

インターネットアプリケーションで非同期モニカーと ActiveX コントロールを使用する方法の詳細については、次の記事を参照してください。

- [インターネットの最初の手順:非同期モニカー](../../mfc/asynchronous-monikers-on-the-internet.md)

- [インターネットの最初の手順:ActiveX コントロール](../../mfc/activex-controls-on-the-internet.md)

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[COleStreamFile](../../mfc/reference/colestreamfile-class.md)

[CMonikerFile](../../mfc/reference/cmonikerfile-class.md)

`CAsyncMonikerFile`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxole

##  <a name="casyncmonikerfile"></a>CAsyncMonikerFile::CAsyncMonikerFile

`CAsyncMonikerFile` オブジェクトを構築します。

```
CAsyncMonikerFile();
```

### <a name="remarks"></a>Remarks

インターフェイスは`IBindHost`作成されません。 `IBindHost`は、 `Open`メンバー関数に指定した場合にのみ使用されます。

`IBindHost`インターフェイスの説明については、Windows SDK を参照してください。

##  <a name="close"></a>  CAsyncMonikerFile::Close

すべてのリソースを閉じて解放するには、この関数を呼び出します。

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

未開封または既に閉じられているファイルに対してを呼び出すことができます。

##  <a name="createbindstatuscallback"></a>CAsyncMonikerFile::CreateBindStatusCallback

を実装`IBindStatusCallback`する COM オブジェクトを作成します。

```
virtual IUnknown* CreateBindStatusCallback(IUnknown* pUnkControlling);
```

### <a name="parameters"></a>パラメーター

*pUnkControlling*<br/>
不明な制御 (外側`IUnknown`) または NULL (集計が使用されていない場合) へのポインター。

### <a name="return-value"></a>戻り値

*PUnkControlling*が NULL でない場合、関数は、をサポート`IUnknown` `IBindStatusCallback`する新しい COM オブジェクト上の内部へのポインターを返します。 が`pUnkControlling` NULL の場合、関数は`IUnknown`をサポート`IBindStatusCallback`する新しい COM オブジェクトのへのポインターを返します。

### <a name="remarks"></a>Remarks

`CAsyncMonikerFile`には、を実装`IBindStatusCallback`する COM オブジェクトが必要です。 MFC は、このようなオブジェクトを実装し、集計可能にします。 をオーバーライド`CreateBindStatusCallback`して、独自の COM オブジェクトを返すことができます。 Com オブジェクトは、com オブジェクトの不明な制御`CreateBindStatusCallback`を使用してを呼び出すことで、MFC の実装を集約できます。 `CCmdTarget` Com サポートを使用して実装された com オブジェクトは`CCmdTarget::GetControllingUnknown`、を使用して、不明な制御を取得できます。

または、を呼び出し`CreateBindStatusCallback( NULL )`て、COM オブジェクトを MFC の実装に委任することもできます。

[CAsyncMonikerFile:: Open](#open)呼び出し`CreateBindStatusCallback`。

非同期モニカーと非同期バインディングの詳細については、「 [IBindStatusCallback](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/ms775060\(v=vs.85\))インターフェイス」と「[非同期バインディングとストレージ](/windows/win32/Stg/how-asynchronous-binding-and-storage-work)のしくみ」を参照してください。 集計の詳細については、「[集計](/windows/win32/com/aggregation)」を参照してください。 この3つのトピックはすべて Windows SDK に含まれています。

##  <a name="getbindinfo"></a>  CAsyncMonikerFile::GetBindInfo

非同期モニカーをバインドする方法を非同期モニカーに通知するために、非同期モニカーのクライアントから呼び出されます。

```
virtual DWORD GetBindInfo() const;
```

### <a name="return-value"></a>戻り値

の`IBindStatusCallBack`設定を取得します。 `IBindStatusCallback`インターフェイスの説明については、Windows SDK を参照してください。

### <a name="remarks"></a>Remarks

既定の実装では、バインディングを非同期に設定し、ストレージメディア (ストリーム) を使用して、データプッシュモデルを使用します。 バインディングの動作を変更する場合は、この関数をオーバーライドします。

これを行う理由の1つは、データプッシュモデルではなく、データプルモデルを使用してバインドすることです。 データプルモデルでは、クライアントはバインド操作を行い、モニカーは読み取り時にのみクライアントにデータを提供します。 データプッシュモデルでは、モニカーによって非同期バインド操作が実行され、新しいデータが利用可能になると常にクライアントに通知されます。

##  <a name="getbinding"></a>  CAsyncMonikerFile::GetBinding

非同期転送バインドへのポインターを取得するには、この関数を呼び出します。

```
IBinding* GetBinding() const;
```

### <a name="return-value"></a>戻り値

非同期転送の開始`IBinding`時に提供されるインターフェイスへのポインター。 何らかの理由で転送を非同期的に行うことができない場合は NULL を返します。

### <a name="remarks"></a>Remarks

これにより`IBinding` 、、 `IBinding::Pause` 、など`IBinding::Abort`を使用して、インターフェイスを介してデータ転送プロセスを制御できます。`IBinding::Resume`

`IBinding`インターフェイスの説明については、Windows SDK を参照してください。

##  <a name="getformatetc"></a>  CAsyncMonikerFile::GetFormatEtc

ストリーム内のデータの形式を取得するには、この関数を呼び出します。

```
FORMATETC* GetFormatEtc() const;
```

### <a name="return-value"></a>戻り値

現在開かれているストリームの Windows 構造体[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)へのポインター。 モニカーがバインドされていない場合、非同期でない場合、または非同期操作が開始されていない場合は、NULL を返します。

##  <a name="getpriority"></a>CAsyncMonikerFile:: GetPriority

バインディング処理で、バインディング操作のスレッドに与えられた優先順位の受信が開始されるときに、非同期モニカーのクライアントから呼び出されます。

```
virtual LONG GetPriority() const;
```

### <a name="return-value"></a>戻り値

非同期転送が行われる優先度。 標準スレッド優先度フラグの1つ。THREAD_PRIORITY_ABOVE_NORMAL、THREAD_PRIORITY_BELOW_NORMAL、THREAD_PRIORITY_HIGHEST、THREAD_PRIORITY_IDLE、THREAD_PRIORITY_LOWEST、THREAD_PRIORITY_NORMAL、および THREAD_PRIORITY_TIME_CRITICAL。 これらの値の詳細については、「Windows 関数の[Setthreadpriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 」を参照してください。

### <a name="remarks"></a>Remarks

`GetPriority`を直接呼び出すことはできません。 THREAD_PRIORITY_NORMAL は、既定の実装によって返されます。

##  <a name="ondataavailable"></a>  CAsyncMonikerFile::OnDataAvailable

非同期モニカーは、 `OnDataAvailable`非同期のバインド操作中に、使用可能になったときにクライアントにデータを提供するためにを呼び出します。

```
virtual void OnDataAvailable(DWORD dwSize, DWORD bscfFlag);
```

### <a name="parameters"></a>パラメーター

*dwSize*<br/>
バインドの開始以降に使用できるデータの累積量 (バイト単位)。 0にすると、データ量が操作に関連していないこと、または特定の量が使用できなくなったことが示されます。

*bscfFlag*<br/>
BSCF 列挙値。 次の値の1つまたは複数を指定できます。

- BSCF_FIRSTDATANOTIFICATION は、特定`OnDataAvailable`のバインド操作について、の最初の呼び出しを識別します。

- BSCF_INTERMEDIATEDATANOTIFICATION は、バインド操作の`OnDataAvailable`ための中間呼び出しを識別します。

- BSCF_LASTDATANOTIFICATION は、バインド操作`OnDataAvailable`の最後の呼び出しを識別します。

### <a name="remarks"></a>Remarks

この関数の既定の実装は、何も行いません。 実装の例については、次の例を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWinInet#5](../../mfc/codesnippet/cpp/casyncmonikerfile-class_1.cpp)]

##  <a name="onlowresource"></a>  CAsyncMonikerFile::OnLowResource

リソースが不足しているときにモニカーによって呼び出されます。

```
virtual void OnLowResource();
```

### <a name="remarks"></a>Remarks

既定の実装で`GetBinding( )-> Abort( )`は、が呼び出されます。

##  <a name="onprogress"></a>  CAsyncMonikerFile::OnProgress

このバインド操作の現在の進行状況を示すために、モニカーによって繰り返し呼び出されます。通常は、時間のかかる操作中に妥当な間隔になります。

```
virtual void OnProgress(
    ULONG ulProgress,
    ULONG ulProgressMax,
    ULONG ulStatusCode,
    LPCTSTR szStatusText);
```

### <a name="parameters"></a>パラメーター

*ulProgress*<br/>
*Ulprogress max*に示されている予想最大値に対するバインド操作の現在の進行状況を示します。

*ulProgressMax*<br/>
この操作のへ`OnProgress`の呼び出しの間に、 *ulprogress*の予期される最大値を示します。

*ulStatusCode*<br/>
バインド操作の進行状況に関する追加情報を提供します。 有効な値は、 `BINDSTATUS`列挙体から取得されます。 有効値については、「解説」を参照してください。

*szStatusText*<br/>
*Ulstatuscode*の値に応じて、現在の進行状況に関する情報を指定します。 有効値については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

*Ulstatuscode* (および各値の*szStatusText* ) に指定できる値は次のとおりです。

|||
|-|-|
|BINDSTATUS_FINDINGRESOURCE  |バインド操作は、バインドされているオブジェクトまたはストレージを保持しているリソースを検索しています。 *SzStatusText*は、検索対象のリソースの表示名を提供します (たとえば、"www.microsoft.com")。  |
|BINDSTATUS_CONNECTING  |バインド操作は、バインドされているオブジェクトまたはストレージを保持しているリソースに接続しています。 *SzStatusText*は、接続されているリソース (IP アドレスなど) の表示名を提供します。  |
|BINDSTATUS_SENDINGREQUEST|バインド操作で、バインド先のオブジェクトまたはストレージが要求されています。 *SzStatusText*は、オブジェクトの表示名 (たとえば、ファイル名) を提供します。|
|BINDSTATUS_REDIRECTING  |バインド操作が別のデータの場所にリダイレクトされました。 *SzStatusText*は、新しいデータの場所の表示名を提供します。  |
|BINDSTATUS_USINGCACHEDCOPY  |バインド操作で、要求されたオブジェクトまたはストレージがキャッシュされたコピーから取得されています。 *SzStatusText*が NULL です。  |
|BINDSTATUS_BEGINDOWNLOADDATA  |バインド操作は、バインドされているオブジェクトまたはストレージの受信を開始しました。 *SzStatusText*は、データの場所の表示名を提供します。|
|BINDSTATUS_DOWNLOADINGDATA  |バインド操作は、バインドされているオブジェクトまたはストレージを引き続き受信します。 *SzStatusText*は、データの場所の表示名を提供します。  |
|BINDSTATUS_ENDDOWNLOADDATA  |バインド操作は、バインドされているオブジェクトまたはストレージの受信を完了しました。 *SzStatusText*は、データの場所の表示名を提供します。  |
|BINDSTATUS_CLASSIDAVAILABLE  |バインドされているオブジェクトのインスタンスが作成されようとしています。 *SzStatusText*は、新しいオブジェクトの CLSID を文字列形式で提供します。これにより、必要に応じて、クライアントはバインド操作を取り消すことができます。  |

##  <a name="onstartbinding"></a>  CAsyncMonikerFile::OnStartBinding

バインドの開始時にアクションを実行するには、派生クラスでこの関数をオーバーライドします。

```
virtual void OnStartBinding();
```

### <a name="remarks"></a>Remarks

この関数は、モニカーによってコールバックされます。 既定の実装では、何も行われません。

##  <a name="onstopbinding"></a>  CAsyncMonikerFile::OnStopBinding

バインド操作の終了時にモニカーによって呼び出されます。

```
virtual void OnStopBinding(HRESULT hresult, LPCTSTR szError);
```

### <a name="parameters"></a>パラメーター

*hresult*<br/>
エラーまたは警告の値である HRESULT。

*szErrort*<br/>
エラーを説明する文字列。

### <a name="remarks"></a>Remarks

転送が停止したときにアクションを実行するには、この関数をオーバーライドします。 既定では、関数は`IBinding`を解放します。

`IBinding`インターフェイスの説明については、Windows SDK を参照してください。

##  <a name="open"></a>  CAsyncMonikerFile::Open

ファイルを非同期的に開くには、このメンバー関数を呼び出します。

```
virtual BOOL Open(
    LPCTSTR lpszURL,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IBindHost* pBindHost,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IServiceProvider* pServiceProvider,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszURL,
    IUnknown* pUnknown,
    CFileException* pError = NULL);

virtual BOOL Open(
    IMoniker* pMoniker,
    IUnknown* pUnknown,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszURL*<br/>
非同期的に開かれるファイルへのポインター。 このファイルには、任意の有効な URL またはファイル名を指定できます。

*pError*<br/>
ファイル例外へのポインター。 エラーが発生した場合は、その原因がに設定されます。

*pMoniker*<br/>
非同期モニカーインターフェイス`IMoniker`へのポインター。これは、を使用して`IOleClientSite::GetMoniker(OLEWHICHMK_CONTAINER)`取得できるドキュメント独自のモニカーとパス名から作成されたモニカーの組み合わせである正確なモニカーです。 コントロールはこのモニカーを使用してバインドできますが、これはコントロールが保存する必要があるモニカーではありません。

*pBindHost*<br/>
可能性のある相対`IBindHost`パス名からモニカーを作成するために使用されるインターフェイスへのポインター。 バインドホストが無効であるか、またはモニカーが指定されてい`Open(lpszFileName,pError)`ない場合、呼び出しは既定でになります。 `IBindHost`インターフェイスの説明については、Windows SDK を参照してください。

*pServiceProvider*<br/>
`IServiceProvider` インターフェイスへのポインター。 サービスプロバイダーが無効であるか、サービスの`IBindHost`提供に失敗した場合、呼び出しは既定でに`Open(lpszFileName,pError)`設定されます。

*pUnknown*<br/>
`IUnknown` インターフェイスへのポインター。 が`IServiceProvider`見つかった場合、関数はを`IBindHost`照会します。 サービスプロバイダーが無効であるか、サービスの`IBindHost`提供に失敗した場合、呼び出しは既定でに`Open(lpszFileName,pError)`設定されます。

### <a name="return-value"></a>戻り値

ファイルが正常に開かれた場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

この呼び出しにより、バインドプロセスが開始されます。

*Lpszurl*パラメーターには、url またはファイル名を使用できます。 例:

[!code-cpp[NVC_MFCWinInet#6](../../mfc/codesnippet/cpp/casyncmonikerfile-class_2.cpp)]

\- または -

[!code-cpp[NVC_MFCWinInet#7](../../mfc/codesnippet/cpp/casyncmonikerfile-class_3.cpp)]

## <a name="see-also"></a>関連項目

[CMonikerFile クラス](../../mfc/reference/cmonikerfile-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CMonikerFile クラス](../../mfc/reference/cmonikerfile-class.md)<br/>
[CDataPathProperty クラス](../../mfc/reference/cdatapathproperty-class.md)
