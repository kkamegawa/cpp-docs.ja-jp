---
title: CComPtrBase クラス
ms.date: 11/04/2016
f1_keywords:
- CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase
- ATLCOMCLI/ATL::CComPtrBase::Advise
- ATLCOMCLI/ATL::CComPtrBase::Attach
- ATLCOMCLI/ATL::CComPtrBase::CoCreateInstance
- ATLCOMCLI/ATL::CComPtrBase::CopyTo
- ATLCOMCLI/ATL::CComPtrBase::Detach
- ATLCOMCLI/ATL::CComPtrBase::IsEqualObject
- ATLCOMCLI/ATL::CComPtrBase::QueryInterface
- ATLCOMCLI/ATL::CComPtrBase::Release
- ATLCOMCLI/ATL::CComPtrBase::SetSite
- ATLCOMCLI/ATL::CComPtrBase::p
helpviewer_keywords:
- CComPtrBase class
ms.assetid: 6dbe9543-dee8-4a97-b02f-dd3a25f4a1a0
ms.openlocfilehash: 740920225fc513a869b4a92344f87004831e4768
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298613"
---
# <a name="ccomptrbase-class"></a>CComPtrBase クラス

このクラスは、COM ベースのメモリルーチンを使用するスマートポインタークラスの基礎となります。

## <a name="syntax"></a>構文

```
template <class T>
class CComPtrBase
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
スマートポインターによって参照されるオブジェクトの種類。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|[名前]|説明|
|----------|-----------------|
|[CComPtrBase:: ~ CComPtrBase](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|[名前]|説明|
|----------|-----------------|
|[CComPtrBase:: Advise](#advise)|`CComPtrBase`のコネクションポイントとクライアントのシンクとの間の接続を作成するには、このメソッドを呼び出します。|
|[CComPtrBase:: Attach](#attach)|既存のポインターの所有権を取得するには、このメソッドを呼び出します。|
|[CComPtrBase:: CoCreateInstance](#cocreateinstance)|指定したクラス ID またはプログラム ID に関連付けられているクラスのオブジェクトを作成するには、このメソッドを呼び出します。|
|[CComPtrBase:: CopyTo](#copyto)|`CComPtrBase` ポインターを別のポインター変数にコピーするには、このメソッドを呼び出します。|
|[CComPtrBase::D etach](#detach)|ポインターの所有権を解放するには、このメソッドを呼び出します。|
|[CComPtrBase::IsEqualObject](#isequalobject)|このメソッドを呼び出して、指定した `IUnknown` が `CComPtrBase` オブジェクトに関連付けられている同じオブジェクトを指しているかどうかを確認します。|
|[CComPtrBase::QueryInterface](#queryinterface)|指定したインターフェイスへのポインターを返すには、このメソッドを呼び出します。|
|[CComPtrBase:: Release](#release)|インターフェイスを解放するには、このメソッドを呼び出します。|
|[CComPtrBase:: SetSite](#setsite)|`CComPtrBase` オブジェクトのサイトを親オブジェクトの `IUnknown` に設定するには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|[名前]|説明|
|----------|-----------------|
|[CComPtrBase:: operator T *](#operator_t_star)|キャスト演算子。|
|[CComPtrBase:: operator!](#operator_not)|NOT 演算子。|
|[CComPtrBase:: operator &](#operator_amp)|&amp; 演算子。|
|[CComPtrBase:: operator *](#operator_star)|\* 演算子。|
|[CComPtrBase:: operator <](#ccomptrbase__operator lt)|"未満" 演算子。|
|[CComPtrBase:: operator = =](#operator_eq_eq)|等値演算子。|
|[CComPtrBase:: operator->](#operator_ptr)|メンバーへのポインター演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|[名前]|説明|
|----------|-----------------|
|[CComPtrBase::p](#p)|ポインターデータメンバー変数。|

## <a name="remarks"></a>コメント

このクラスは、 [CComQIPtr](../../atl/reference/ccomqiptr-class.md)や[CCOMPTR](../../atl/reference/ccomptr-class.md)などの COM メモリ管理ルーチンを使用する他のスマートポインターの基礎となります。 派生クラスは、独自のコンストラクターと演算子を追加しますが、`CComPtrBase`によって提供されるメソッドに依存します。

## <a name="requirements"></a>要件

**ヘッダー:** atlcomcli. h

##  <a name="advise"></a>  CComPtrBase::Advise

`CComPtrBase`のコネクションポイントとクライアントのシンクとの間の接続を作成するには、このメソッドを呼び出します。

```
HRESULT Advise(
    IUnknown* pUnk,
    const IID& iid,
    LPDWORD pdw) throw();
```

### <a name="parameters"></a>パラメーター

*pUnk*<br/>
クライアントの `IUnknown`へのポインター。

*iid*<br/>
コネクションポイントの GUID。 通常、これは接続ポイントによって管理される送信インターフェイスと同じです。

*ウィザード*<br/>
接続を一意に識別するクッキーへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>コメント

詳細については、「 [AtlAdvise](connection-point-global-functions.md#atladvise) 」を参照してください。

##  <a name="attach"></a>CComPtrBase:: Attach

既存のポインターの所有権を取得するには、このメソッドを呼び出します。

```
void Attach(T* p2) throw();
```

### <a name="parameters"></a>パラメーター

*p2*<br/>
`CComPtrBase` オブジェクトは、このポインターの所有権を取得します。

### <a name="remarks"></a>コメント

`Attach` は、既存の[CComPtrBase::p](#p)メンバー変数に対して[CComPtrBase:: Release](#release)を呼び出し、`CComPtrBase::p`に*p2*を割り当てます。 `CComPtrBase` オブジェクトがポインターの所有権を取得すると、オブジェクトの参照カウントが0になった場合にポインターと割り当てられたデータを削除するポインターの `Release` が自動的に呼び出されます。

##  <a name="dtor"></a>CComPtrBase:: ~ CComPtrBase

デストラクターです。

```
~CComPtrBase() throw();
```

### <a name="remarks"></a>コメント

`CComPtrBase`が指すインターフェイスを解放します。

##  <a name="cocreateinstance"></a>CComPtrBase:: CoCreateInstance

指定したクラス ID またはプログラム ID に関連付けられているクラスのオブジェクトを作成するには、このメソッドを呼び出します。

```
HRESULT CoCreateInstance(
    LPCOLESTR szProgID,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();

HRESULT CoCreateInstance(
    REFCLSID rclsid,
    LPUNKNOWN pUnkOuter = NULL,
    DWORD dwClsContext = CLSCTX_ALL) throw();
```

### <a name="parameters"></a>パラメーター

*szProgID*<br/>
CLSID を回復するために使用される ProgID へのポインター。

*pUnkOuter*<br/>
NULL の場合、オブジェクトが集計の一部として作成されていないことを示します。 NULL 以外の場合、は集計オブジェクトの `IUnknown` インターフェイス (制御 `IUnknown`) へのポインターです。

*dwClsContext*<br/>
新しく作成されたオブジェクトを管理するコードが実行されるコンテキスト。

*rclsid*<br/>
オブジェクトの作成に使用されるデータとコードに関連付けられている CLSID。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、失敗した場合は REGDB_E_CLASSNOTREG、CLASS_E_NOAGGREGATION、CO_E_CLASSSTRING または E_NOINTERFACE を返します。 これらのエラーの説明については、「 [CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance) And [Clsidfromprogid](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid) 」を参照してください。

### <a name="remarks"></a>コメント

メソッドの最初の形式が呼び出された場合、CLSID を復旧するために[Clsidfromprogid](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromprogid)が使用されます。 どちらのフォームも[CoCreateClassInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance)を呼び出します。

デバッグビルドでは、 [CComPtrBase::p](#p)が NULL と等しくない場合にアサーションエラーが発生します。

##  <a name="copyto"></a>  CComPtrBase::CopyTo

`CComPtrBase` ポインターを別のポインター変数にコピーするには、このメソッドを呼び出します。

```
HRESULT CopyTo(T** ppT) throw();
```

### <a name="parameters"></a>パラメーター

*ppT*<br/>
`CComPtrBase` ポインターを受け取る変数のアドレス。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合は E_POINTER を返します。

### <a name="remarks"></a>コメント

`CComPtrBase` ポインターを*ppT*にコピーします。 [CComPtrBase::p](#p)メンバー変数の参照カウントがインクリメントされます。

*PpT*が NULL の場合は、エラー HRESULT が返されます。 デバッグビルドでは、 *ppT*が NULL に等しい場合にアサーションエラーが発生します。

##  <a name="detach"></a>CComPtrBase::D etach

ポインターの所有権を解放するには、このメソッドを呼び出します。

```
T* Detach() throw();
```

### <a name="return-value"></a>戻り値

ポインターのコピーを返します。

### <a name="remarks"></a>コメント

ポインターの所有権を解放し、 [CComPtrBase::p](#p)データメンバー変数を NULL に設定して、ポインターのコピーを返します。

##  <a name="isequalobject"></a>CComPtrBase::IsEqualObject

このメソッドを呼び出して、指定した `IUnknown` が `CComPtrBase` オブジェクトに関連付けられている同じオブジェクトを指しているかどうかを確認します。

```
bool IsEqualObject(IUnknown* pOther) throw();
```

### <a name="parameters"></a>パラメーター

*その他*<br/>
比較対象の `IUnknown *`。

### <a name="return-value"></a>戻り値

オブジェクトが同一の場合は true、それ以外の場合は false を返します。

##  <a name="operator_not"></a>CComPtrBase:: operator!

NOT 演算子。

```
bool operator!() const throw();
```

### <a name="return-value"></a>戻り値

`CComHeapPtr` ポインターが NULL の場合は true、それ以外の場合は false を返します。

##  <a name="operator_amp"></a>CComPtrBase:: operator &amp;

&amp; 演算子。

```
T** operator&() throw();
```

### <a name="return-value"></a>戻り値

`CComPtrBase` オブジェクトが指すオブジェクトのアドレスを返します。

##  <a name="operator_star"></a>CComPtrBase:: operator \*

\* 演算子。

```
T& operator*() const throw();
```

### <a name="return-value"></a>戻り値

[CComPtrBase::p](#p)の値を返します。つまり、`CComPtrBase` オブジェクトによって参照されるオブジェクトへのポインターです。

デバッグビルドの場合、 [CComPtrBase::p](#p)が NULL と等しくない場合、アサーションエラーが発生します。

##  <a name="operator_eq_eq"></a>CComPtrBase:: operator = =

等値演算子。

```
bool operator== (T* pT) const throw();
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

`CComPtrBase` と*pT*が同じオブジェクトを指している場合は true、それ以外の場合は false を返します。

##  <a name="operator_ptr"></a>CComPtrBase:: operator-&gt;

メンバーへのポインター演算子。

```
_NoAddRefReleaseOnCComPtr<T>* operator->() const throw();
```

### <a name="return-value"></a>戻り値

[CComPtrBase::p](#p)データメンバー変数の値を返します。

### <a name="remarks"></a>コメント

この演算子を使用すると、`CComPtrBase` オブジェクトが指すクラスのメソッドを呼び出すことができます。 デバッグビルドでは、`CComPtrBase` データメンバーが NULL を指している場合、アサーションエラーが発生します。

##  <a name="operator_lt"></a>CComPtrBase:: operator &lt;

"未満" 演算子。

```
bool operator<(T* pT) const throw();
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

現在のオブジェクトによって管理されているポインターが、比較対象のポインターより小さい場合に true を返します。

##  <a name="operator_t_star"></a>CComPtrBase:: operator T\*

キャスト演算子。

```
operator T*() const throw();
```

### <a name="remarks"></a>コメント

クラステンプレートで定義されているオブジェクトデータ型へのポインターを返します。

##  <a name="p"></a>CComPtrBase::p

ポインターデータメンバー変数。

```
T* p;
```

### <a name="remarks"></a>コメント

このメンバー変数は、ポインター情報を保持します。

##  <a name="queryinterface"></a>  CComPtrBase::QueryInterface

指定したインターフェイスへのポインターを返すには、このメソッドを呼び出します。

```
template <class Q> HRESULT QueryInterface(Q
** pp) const throw();
```

### <a name="parameters"></a>パラメーター

*Q*<br/>
インターフェイスポインターが必要なオブジェクト型。

*ページ*<br/>
要求されたインターフェイスポインターを受け取る出力変数のアドレス。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合は E_NOINTERFACE を返します。

### <a name="remarks"></a>コメント

このメソッド[は、IUnknown:: QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q))を呼び出します。

デバッグビルドでは、 *pp*が NULL と等しくない場合にアサーションエラーが発生します。

##  <a name="release"></a>  CComPtrBase::Release

インターフェイスを解放するには、このメソッドを呼び出します。

```
void Release() throw();
```

### <a name="remarks"></a>コメント

インターフェイスが解放され、 [CComPtrBase::p](#p)が NULL に設定されます。

##  <a name="setsite"></a>CComPtrBase:: SetSite

`CComPtrBase` オブジェクトのサイトを親オブジェクトの `IUnknown` に設定するには、このメソッドを呼び出します。

```
HRESULT SetSite(IUnknown* punkParent) throw();
```

### <a name="parameters"></a>パラメーター

*punkParent*<br/>
親の `IUnknown` インターフェイスへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返し、失敗した場合はエラー HRESULT を返します。

### <a name="remarks"></a>コメント

このメソッドは、 [Atlsetchildsite](composite-control-global-functions.md#atlsetchildsite)を呼び出します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
