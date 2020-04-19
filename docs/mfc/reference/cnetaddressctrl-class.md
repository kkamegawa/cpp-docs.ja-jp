---
title: CNetAddressCtrl クラス
ms.date: 11/19/2018
f1_keywords:
- CNetAddressCtrl
- AFXCMN/CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::CNetAddressCtrl
- AFXCMN/CNetAddressCtrl::Create
- AFXCMN/CNetAddressCtrl::CreateEx
- AFXCMN/CNetAddressCtrl::DisplayErrorTip
- AFXCMN/CNetAddressCtrl::GetAddress
- AFXCMN/CNetAddressCtrl::GetAllowType
- AFXCMN/CNetAddressCtrl::SetAllowType
helpviewer_keywords:
- CNetAddressCtrl [MFC], CNetAddressCtrl
- CNetAddressCtrl [MFC], Create
- CNetAddressCtrl [MFC], CreateEx
- CNetAddressCtrl [MFC], DisplayErrorTip
- CNetAddressCtrl [MFC], GetAddress
- CNetAddressCtrl [MFC], GetAllowType
- CNetAddressCtrl [MFC], SetAllowType
ms.assetid: cb4c6aca-3f49-4b52-b76c-65f57096155b
ms.openlocfilehash: 5e485c22bcc4bf35f61226d84345102052689f89
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "69504533"
---
# <a name="cnetaddressctrl-class"></a>CNetAddressCtrl クラス

`CNetAddressCtrl` クラスは、ネットワーク アドレス コントロールを表します。このコントロールを使用すると、IPv4 アドレス、IPv6 アドレス、および名前付き DNS アドレスの形式を入力して検証できます。

## <a name="syntax"></a>構文

```
class CNetAddressCtrl : public CEdit
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CNetAddressCtrl::CNetAddressCtrl](#cnetaddressctrl)|`CNetAddressCtrl` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CNetAddressCtrl::Create](#create)|指定されたスタイルを使用してネットワークアドレスコントロールを作成`CNetAddressCtrl`し、現在のオブジェクトに添付します。|
|[CNetAddressCtrl::CreateEx](#createex)|指定した拡張スタイルを使用してネットワークアドレスコントロールを作成し`CNetAddressCtrl` 、現在のオブジェクトにアタッチします。|
|[CNetAddressCtrl::DisplayErrorTip](#displayerrortip)|現在のネットワークアドレスコントロールでサポートされていないネットワークアドレスをユーザーが入力したときに、エラーバルーンヒントを表示します。|
|[CNetAddressCtrl::GetAddress](#getaddress)|現在のネットワークアドレスコントロールに関連付けられているネットワークアドレスの検証および解析された表現を取得します。|
|[CNetAddressCtrl::GetAllowType](#getallowtype)|現在のネットワークアドレスコントロールがサポートできるネットワークアドレスの種類を取得します。|
|[CNetAddressCtrl::SetAllowType](#setallowtype)|現在のネットワークアドレスコントロールがサポートできるネットワークアドレスの種類を設定します。|

## <a name="remarks"></a>コメント

ネットワークアドレスコントロールは、ユーザーが入力したアドレスの形式が正しいことを確認します。 コントロールは実際にはネットワークアドレスに接続していません。 [CNetAddressCtrl:: SetAllowType](#setallowtype)メソッドは、 [CNetAddressCtrl:: getaddress](#getaddress)メソッドが解析および検証できるアドレスの1つ以上の型を指定します。 アドレスは、サーバー、ネットワーク、ホスト、またはブロードキャストメッセージ送信先の IPv4、IPv6、または名前付きアドレスの形式にすることができます。 アドレスの形式が正しくない場合は、 [CNetAddressCtrl::D isplayErrorTip](#displayerrortip)メソッドを使用して、ネットワークアドレスコントロールのテキストボックスをグラフィカルに示すヒントメッセージボックスを表示し、定義済みのエラーメッセージを表示することができます。

クラスは、[CEdit](../../mfc/reference/cedit-class.md) クラスから派生します。`CNetAddressCtrl` その結果、ネットワークアドレス制御によって、すべての Windows エディットコントロールメッセージにアクセスできるようになります。

次の図は、ネットワークアドレスコントロールを含むダイアログを示しています。 ネットワークアドレスコントロールのテキストボックス (1) に無効なネットワークアドレスが含まれています。 ネットワークアドレスが無効な場合は、ヒントメッセージ (2) が表示されます。

![ネットワークアドレスコントロールとヒントを含むダイアログ。](../../mfc/reference/media/cnetaddctrl.png "ネットワークアドレスコントロールとヒントを含むダイアログ。")

## <a name="example"></a>例

次のコード例は、ネットワークアドレスを検証するダイアログの一部です。 3つのオプションボタンのイベントハンドラーでは、ネットワークアドレスが3つのアドレスの種類のいずれかであることを指定します。 ユーザーは、ネットワークコントロールのテキストボックスにアドレスを入力し、ボタンを押してアドレスを検証します。 アドレスが有効な場合は、成功メッセージが表示されます。それ以外の場合は、定義済みのヒントエラーメッセージが表示されます。

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#1](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_1.cpp)]

## <a name="example"></a>例

ダイアログヘッダーファイルの次のコード例では、 [CNetAddressCtrl:: GetAddress](#getaddress)メソッドで必要とされる[NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address)変数と[NET_ADDRESS_INFO](/windows/win32/shell/hkey-type)変数を定義しています。

[!code-cpp[NVC_MFC_CNetAddressCtrl_s1#2](../../mfc/reference/codesnippet/cpp/cnetaddressctrl-class_2.h)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CEdit](../../mfc/reference/cedit-class.md)

`CNetAddressCtrl`

## <a name="requirements"></a>要件

**ヘッダー:** afxcmn.h

このクラスは、Windows Vista 以降でサポートされています。

このクラスの追加要件については、「 [Windows Vista コモンコントロールのビルド要件](../../mfc/build-requirements-for-windows-vista-common-controls.md)」を参照してください。

##  <a name="cnetaddressctrl"></a>  CNetAddressCtrl::CNetAddressCtrl

`CNetAddressCtrl` オブジェクトを構築します。

```
CNetAddressCtrl();
```

### <a name="remarks"></a>コメント

[CNetAddressCtrl:: Create](#create)メソッドまたは[CNetAddressCtrl:: CreateEx](#createex)メソッドを使用して、ネットワークコントロールを作成し`CNetAddressCtrl` 、オブジェクトにアタッチします。

##  <a name="create"></a>  CNetAddressCtrl::Create

指定されたスタイルを使用してネットワークアドレスコントロールを作成`CNetAddressCtrl`し、現在のオブジェクトに添付します。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*dwStyle*|からコントロールに適用されるスタイルのビットごとの組み合わせ。 詳細については、「[スタイルの編集](../../mfc/reference/styles-used-by-mfc.md#edit-styles)」を参照してください。|
|*rect*|からコントロールの位置とサイズを格納している[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。|
|*pParentWnd*|からコントロールの親ウィンドウである[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへの null 以外のポインター。|
|*nID*|からコントロールの ID。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

##  <a name="createex"></a>  CNetAddressCtrl::CreateEx

指定した拡張スタイルを使用してネットワークアドレスコントロールを作成し`CNetAddressCtrl` 、現在のオブジェクトにアタッチします。

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*dwExStyle*|からコントロールに適用される拡張スタイルのビットごとの組み合わせ (または)。 詳細については、 [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw)関数の*dwexstyle*パラメーターを参照してください。|
|*dwStyle*|からコントロールに適用されるスタイルのビットごとの組み合わせ (または)。 詳細については、「[スタイルの編集](../../mfc/reference/styles-used-by-mfc.md#edit-styles)」を参照してください。|
|*rect*|からコントロールの位置とサイズを格納している[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。|
|*pParentWnd*|からコントロールの親ウィンドウである[CWnd](../../mfc/reference/cwnd-class.md)オブジェクトへの null 以外のポインター。|
|*nID*|からコントロールの ID。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は TRUE。それ以外の場合は FALSE。

##  <a name="displayerrortip"></a>  CNetAddressCtrl::DisplayErrorTip

現在のネットワークアドレスコントロールに関連付けられているバルーンヒントにエラーメッセージを表示します。

```
HRESULT DisplayErrorTip();
```

### <a name="return-value"></a>戻り値

このメソッド`S_OK`が正常に実行された場合は値。それ以外の場合はエラーコード。

### <a name="remarks"></a>コメント

[CNetAddressCtrl:: SetAllowType](#setallowtype)メソッドを使用して、現在のネットワークアドレスコントロールがサポートできるアドレスの種類を指定します。 [CNetAddressCtrl:: GetAddress](#getaddress)メソッドを使用して、ユーザーが入力したネットワークアドレスを検証し、解析します。 [CNetAddressCtrl:: GetAddress](#getaddress)メソッドが失敗した場合にエラーメッセージヒントを表示するには、 [CNetAddressCtrl::D isplayErrorTip](#displayerrortip)メソッドを使用します。

このメッセージは、Windows SDK で説明されている[NetAddr_DisplayErrorTip](/windows/win32/api/shellapi/nf-shellapi-netaddr_displayerrortip)マクロを呼び出します。 そのマクロによっ`NCM_DISPLAYERRORTIP`てメッセージが送信されます。

##  <a name="getaddress"></a>  CNetAddressCtrl::GetAddress

現在のネットワークアドレスコントロールに関連付けられているネットワークアドレスの検証および解析された表現を取得します。

```
HRESULT GetAddress(PNC_ADDRESS pAddress) const;
```

### <a name="parameters"></a>パラメーター

*pAddress*<br/>
[入力、出力][NC_ADDRESS](/windows/win32/api/shellapi/ns-shellapi-nc_address)構造体へのポインター。  GetAddress メソッドを呼び出す前に、この構造体の*Paddrinfo*メンバーを[NET_ADDRESS_INFO](/windows/win32/shell/hkey-type)構造体のアドレスに設定します。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は、値 S_OK。それ以外の場合は、COM エラーコード。 考えられるエラーコードの詳細については、 [NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress)マクロの「戻り値」セクションを参照してください。

### <a name="remarks"></a>コメント

このメソッドが成功した場合、 [NET_ADDRESS_INFO](/windows/win32/shell/hkey-type)構造体にはネットワークアドレスに関する追加情報が含まれます。

[CNetAddressCtrl:: SetAllowType](#setallowtype)メソッドを使用して、現在のネットワークアドレスコントロールがサポートできるアドレスの種類を指定します。 [CNetAddressCtrl:: GetAddress](#getaddress)メソッドを使用して、ユーザーが入力したネットワークアドレスを検証し、解析します。 [CNetAddressCtrl:: GetAddress](#getaddress)メソッドが失敗した場合にエラーメッセージヒントを表示するには、 [CNetAddressCtrl::D isplayErrorTip](#displayerrortip)メソッドを使用します。

このメソッドは、Windows SDK で説明されている[NetAddr_GetAddress](/windows/win32/api/shellapi/nf-shellapi-netaddr_getaddress)マクロを呼び出します。 このマクロは、NCM_GETADDRESS メッセージを送信します。

##  <a name="getallowtype"></a>  CNetAddressCtrl::GetAllowType

現在のネットワークアドレスコントロールがサポートできるネットワークアドレスの種類を取得します。

```
DWORD GetAllowType() const;
```

### <a name="return-value"></a>戻り値

ネットワークアドレスコントロールがサポートできるアドレスの種類を指定するフラグのビットごとの組み合わせ (or)。 詳細については、「 [NET_STRING](/windows/win32/shell/net-string)」を参照してください。

### <a name="remarks"></a>コメント

このメッセージは、Windows SDK で説明されている[NetAddr_GetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_getallowtype)マクロを呼び出します。 このマクロは、NCM_GETALLOWTYPE メッセージを送信します。

##  <a name="setallowtype"></a>  CNetAddressCtrl::SetAllowType

現在のネットワークアドレスコントロールがサポートできるネットワークアドレスの種類を設定します。

```
HRESULT SetAllowType(DWORD dwAddrMask);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*dwAddrMask*|からネットワークアドレスコントロールがサポートできるアドレスの種類を指定するフラグのビットごとの組み合わせ (or)。 詳細については、「 [NET_STRING](/windows/win32/shell/net-string)」を参照してください。|

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は S_OK。それ以外の場合は、COM エラーコード。

### <a name="remarks"></a>コメント

[CNetAddressCtrl:: SetAllowType](#setallowtype)メソッドを使用して、現在のネットワークアドレスコントロールがサポートできるアドレスの種類を指定します。 [CNetAddressCtrl:: GetAddress](#getaddress)メソッドを使用して、ユーザーが入力したネットワークアドレスを検証し、解析します。 [CNetAddressCtrl:: GetAddress](#getaddress)メソッドが失敗した場合にエラーメッセージヒントを表示するには、 [CNetAddressCtrl::D isplayErrorTip](#displayerrortip)メソッドを使用します。

このメッセージは、Windows SDK で説明されている[NetAddr_SetAllowType](/windows/win32/api/shellapi/nf-shellapi-netaddr_setallowtype)マクロを呼び出します。 このマクロは、NCM_SETALLOWTYPE メッセージを送信します。

## <a name="see-also"></a>関連項目

[CNetAddressCtrl クラス](../../mfc/reference/cnetaddressctrl-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CEdit クラス](../../mfc/reference/cedit-class.md)
