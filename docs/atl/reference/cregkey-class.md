---
title: CRegKey クラス
ms.date: 11/04/2016
f1_keywords:
- CRegKey
- ATLBASE/ATL::CRegKey
- ATLBASE/ATL::CRegKey::CRegKey
- ATLBASE/ATL::CRegKey::Attach
- ATLBASE/ATL::CRegKey::Close
- ATLBASE/ATL::CRegKey::Create
- ATLBASE/ATL::CRegKey::DeleteSubKey
- ATLBASE/ATL::CRegKey::DeleteValue
- ATLBASE/ATL::CRegKey::Detach
- ATLBASE/ATL::CRegKey::EnumKey
- ATLBASE/ATL::CRegKey::Flush
- ATLBASE/ATL::CRegKey::GetKeySecurity
- ATLBASE/ATL::CRegKey::NotifyChangeKeyValue
- ATLBASE/ATL::CRegKey::Open
- ATLBASE/ATL::CRegKey::QueryBinaryValue
- ATLBASE/ATL::CRegKey::QueryDWORDValue
- ATLBASE/ATL::CRegKey::QueryGUIDValue
- ATLBASE/ATL::CRegKey::QueryMultiStringValue
- ATLBASE/ATL::CRegKey::QueryQWORDValue
- ATLBASE/ATL::CRegKey::QueryStringValue
- ATLBASE/ATL::CRegKey::QueryValue
- ATLBASE/ATL::CRegKey::RecurseDeleteKey
- ATLBASE/ATL::CRegKey::SetBinaryValue
- ATLBASE/ATL::CRegKey::SetDWORDValue
- ATLBASE/ATL::CRegKey::SetGUIDValue
- ATLBASE/ATL::CRegKey::SetKeySecurity
- ATLBASE/ATL::CRegKey::SetKeyValue
- ATLBASE/ATL::CRegKey::SetMultiStringValue
- ATLBASE/ATL::CRegKey::SetQWORDValue
- ATLBASE/ATL::CRegKey::SetStringValue
- ATLBASE/ATL::CRegKey::SetValue
- ATLBASE/ATL::CRegKey::m_hKey
- ATLBASE/ATL::CRegKey::m_pTM
helpviewer_keywords:
- CRegKey class
- ATL, registry
- registry, deleting values
- registry, writing to
- registry, deleting keys
ms.assetid: 3afce82b-ba2c-4c1a-8404-dc969e1af74b
ms.openlocfilehash: 3faf446f74577034a3d0676b90ebe7027ef6da06
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496534"
---
# <a name="cregkey-class"></a>CRegKey クラス

このクラスには、システムレジストリのエントリを操作するためのメソッドが用意されています。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CRegKey
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CRegKey:: CRegKey](#cregkey)|コンストラクターです。|
|[CRegKey:: ~ CRegKey](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRegKey:: Attach](#attach)|このメソッドを呼び出して、 [m_hKey](#m_hkey)メンバーハンドル`CRegKey`をに`hKey`設定することにより、オブジェクトに HKEY をアタッチします。|
|[CRegKey:: Close](#close)|このメソッドを呼び出して、 [m_hKey](#m_hkey)メンバーハンドルを解放し、NULL に設定します。|
|[CRegKey:: Create](#create)|指定したキーがの`hKeyParent`サブキーとして存在しない場合は、このメソッドを呼び出して作成します。|
|[CRegKey::D eleteSubKey](#deletesubkey)|指定したキーをレジストリから削除するには、このメソッドを呼び出します。|
|[CRegKey::D eleteValue](#deletevalue)|[M_hKey](#m_hkey)から値フィールドを削除するには、このメソッドを呼び出します。|
|[CRegKey::D etach](#detach)|このメソッドを呼び出して、 [m_hKey](#m_hkey)メンバーハンドルを`CRegKey`オブジェクトからデタッチし`m_hKey` 、を NULL に設定します。|
|[CRegKey:: EnumKey](#enumkey)|このメソッドを呼び出して、開いているレジストリキーのサブキーを列挙します。|
|[CRegKey:: Flush](#flush)|このメソッドを呼び出して、開いているレジストリキーのすべての属性をレジストリに書き込みます。|
|[CRegKey:: GetKeySecurity](#getkeysecurity)|開いているレジストリキーを保護しているセキュリティ記述子のコピーを取得するには、このメソッドを呼び出します。|
|[CRegKey::NotifyChangeKeyValue](#notifychangekeyvalue)|このメソッドは、開いているレジストリキーの属性または内容への変更について、呼び出し元に通知します。|
|[CRegKey:: Open](#open)|このメソッドを呼び出して、指定したキーを開き、 [m_hKey](#m_hkey)をこのキーのハンドルに設定します。|
|[CRegKey::QueryBinaryValue](#querybinaryvalue)|指定した値の名前のバイナリデータを取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryDWORDValue](#querydwordvalue)|指定した値名の DWORD データを取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryGUIDValue](#queryguidvalue)|指定した値の名前の GUID データを取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryMultiStringValue](#querymultistringvalue)|指定した値名の文字列データを取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryQWORDValue](#queryqwordvalue)|指定した値名の QWORD データを取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryStringValue](#querystringvalue)|指定した値名の文字列データを取得するには、このメソッドを呼び出します。|
|[CRegKey::QueryValue](#queryvalue)|[M_hKey](#m_hkey)の指定した値フィールドのデータを取得するには、このメソッドを呼び出します。 このメソッドの以前のバージョンはサポートされなくなり、ATL_DEPRECATED としてマークされます。|
|[CRegKey::RecurseDeleteKey](#recursedeletekey)|指定したキーをレジストリから削除し、サブキーを明示的に削除するには、このメソッドを呼び出します。|
|[CRegKey:: SetBinaryValue](#setbinaryvalue)|レジストリキーのバイナリ値を設定するには、このメソッドを呼び出します。|
|[CRegKey:: SetDWORDValue](#setdwordvalue)|レジストリキーの DWORD 値を設定するには、このメソッドを呼び出します。|
|[CRegKey:: SetGUIDValue](#setguidvalue)|レジストリキーの GUID 値を設定するには、このメソッドを呼び出します。|
|[CRegKey:: SetKeySecurity](#setkeysecurity)|レジストリキーのセキュリティを設定するには、このメソッドを呼び出します。|
|[CRegKey:: SetKeyValue](#setkeyvalue)|指定したキーの指定した値フィールドにデータを格納するには、このメソッドを呼び出します。|
|[CRegKey:: SetMultiStringValue](#setmultistringvalue)|レジストリキーの文字列値を設定するには、このメソッドを呼び出します。|
|[CRegKey:: SetQWORDValue](#setqwordvalue)|レジストリキーの QWORD 値を設定するには、このメソッドを呼び出します。|
|[CRegKey:: SetStringValue](#setstringvalue)|レジストリ キーの文字列値を設定します。|
|[CRegKey:: SetValue](#setvalue)|[M_hKey](#m_hkey)の指定した値フィールドにデータを格納するには、このメソッドを呼び出します。 このメソッドの以前のバージョンはサポートされなくなり、ATL_DEPRECATED としてマークされます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CRegKey:: operator HKEY](#operator_hkey)|オブジェクトを`CRegKey` HKEY に変換します。|
|[CRegKey:: operator =](#operator_eq)|代入演算子。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CRegKey::m_hKey](#m_hkey)|`CRegKey`オブジェクトに関連付けられたレジストリキーのハンドルを格納します。|
|[CRegKey::m_pTM](#m_ptm)|オブジェクトへ`CAtlTransactionManager`のポインター|

## <a name="remarks"></a>Remarks

`CRegKey`システムレジストリのキーと値を作成および削除するためのメソッドを提供します。 レジストリには、ソフトウェアのバージョン番号、インストールされているハードウェアの論理対一のマッピング、COM オブジェクトなど、システムコンポーネントのインストール固有の定義セットが含まれています。

`CRegKey`特定のコンピューターのシステムレジストリに対するプログラミングインターフェイスを提供します。 たとえば、特定のレジストリキーを開くには、 `CRegKey::Open`を呼び出します。 データ値を取得または変更するに`CRegKey::QueryValue`は`CRegKey::SetValue`、それぞれまたはを呼び出します。 キーを閉じるには、 `CRegKey::Close`を呼び出します。

キーを閉じると、そのレジストリデータがハードディスクに書き込まれます (フラッシュされます)。 このプロセスには数秒かかることがあります。 アプリケーションがレジストリデータをハードディスクに明示的に書き込む必要がある場合は、 [Regflushkey](/windows/win32/api/winreg/nf-winreg-regflushkey) Win32 関数を呼び出すことができます。 ただし、 `RegFlushKey`は多くのシステムリソースを使用するため、必要な場合にのみ呼び出す必要があります。

> [!IMPORTANT]
>  呼び出し元がレジストリの場所を指定できるようにするメソッドは、信頼できないデータを読み取る可能性があります。 [Regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)を使用するメソッドでは、この関数が NULL で終了する文字列を明示的に処理しないことを考慮する必要があります。 呼び出し元のコードで両方の条件を確認する必要があります。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="attach"></a>CRegKey:: Attach

[M_hKey](#m_hkey)メンバーハンドルを*hkey*に設定して`CRegKey` 、このメソッドを呼び出して、オブジェクトに hkey をアタッチします。

```
void Attach(HKEY hKey) throw();
```

### <a name="parameters"></a>パラメーター

*hKey*<br/>
レジストリキーのハンドル。

### <a name="remarks"></a>Remarks

`Attach`が NULL 以外`m_hKey`の場合は、をアサートします。

##  <a name="close"></a>CRegKey:: Close

このメソッドを呼び出して、 [m_hKey](#m_hkey)メンバーハンドルを解放し、NULL に設定します。

```
LONG Close() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。それ以外の場合は、エラー値を返します。

##  <a name="create"></a>CRegKey:: Create

このメソッドを呼び出して、指定したキーが*H鍵 Arent*のサブキーとして存在しない場合は作成します。

```
LONG Create(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPTSTR lpszClass = REG_NONE,
    DWORD dwOptions = REG_OPTION_NON_VOLATILE,
    REGSAM samDesired = KEY_READ | KEY_WRITE,
    LPSECURITY_ATTRIBUTES lpSecAttr = NULL,
    LPDWORD lpdwDisposition = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*hKeyParent*<br/>
開いているキーのハンドル。

*lpszKeyName*<br/>
作成または開くキーの名前を指定します。 この名前は、 *hsubkey Arent*のサブキーである必要があります。

*lpszClass*<br/>
作成または開くキーのクラスを指定します。 既定値は REG_NONE です。

*dwOptions*<br/>
キーのオプション。 既定値は REG_OPTION_NON_VOLATILE です。 使用可能な値と説明の一覧については、Windows SDK の「 [Regcreatekeyex](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) 」を参照してください。

*samDesired*<br/>
キーのセキュリティアクセス。 既定値は KEY_READ &#124; KEY_WRITE です。 使用可能な値と説明の一覧につい`RegCreateKeyEx`ては、「」を参照してください。

*lpSecAttr*<br/>
キーのハンドルを子プロセスが継承できるかどうかを示す[SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))構造体へのポインター。 既定では、このパラメーターは NULL です (つまり、ハンドルを継承することはできません)。

*lpdwDisposition*<br/>
入出力NULL 以外の場合は、REG_CREATED_NEW_KEY (キーが存在していて作成された場合) または REG_OPENED_EXISTING_KEY (キーが存在し、開かれた場合) を取得します。

### <a name="return-value"></a>戻り値

成功した場合、は ERROR_SUCCESS を返し、キーを開きます。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

`Create`[m_hKey](#m_hkey)メンバーをこのキーのハンドルに設定します。

##  <a name="cregkey"></a>CRegKey:: CRegKey

コンストラクターです。

```
CRegKey() throw();
CRegKey(CRegKey& key) throw();
explicit CRegKey(HKEY hKey) throw();
CRegKey(CAtlTransactionManager* pTM) throw();
```

### <a name="parameters"></a>パラメーター

*key*<br/>
`CRegKey` オブジェクトへの参照。

*hKey*<br/>
レジストリキーへのハンドル。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

新しい `CRegKey` オブジェクトを作成します。 オブジェクトは、既存`CRegKey`のオブジェクト、またはレジストリキーへのハンドルから作成できます。

##  <a name="dtor"></a>CRegKey:: ~ CRegKey

デストラクターです。

```
~CRegKey() throw();
```

### <a name="remarks"></a>Remarks

デストラクターが解放`m_hKey`されます。

##  <a name="deletesubkey"></a>  CRegKey::DeleteSubKey

指定したキーをレジストリから削除するには、このメソッドを呼び出します。

```
LONG DeleteSubKey(LPCTSTR lpszSubKey) throw();
```

### <a name="parameters"></a>パラメーター

*lpszSubKey*<br/>
削除するキーの名前を指定します。 この名前は、 [m_hKey](#m_hkey)のサブキーである必要があります。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

`DeleteSubKey`は、サブキーを持たないキーのみを削除できます。 キーにサブキーがある場合は、代わりに[RecurseDeleteKey](#recursedeletekey)を呼び出します。

##  <a name="deletevalue"></a>CRegKey::D eleteValue

[M_hKey](#m_hkey)から値フィールドを削除するには、このメソッドを呼び出します。

```
LONG DeleteValue(LPCTSTR lpszValue) throw();
```

### <a name="parameters"></a>パラメーター

*lpszValue*<br/>
削除する値フィールドを指定します。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

##  <a name="detach"></a>CRegKey::D etach

このメソッドを呼び出して、 [m_hKey](#m_hkey)メンバーハンドルを`CRegKey`オブジェクトからデタッチし`m_hKey` 、を NULL に設定します。

```
HKEY Detach() throw();
```

### <a name="return-value"></a>戻り値

`CRegKey`オブジェクトに関連付けられている HKEY。

##  <a name="enumkey"></a>CRegKey:: EnumKey

このメソッドを呼び出して、開いているレジストリキーのサブキーを列挙します。

```
LONG EnumKey(
    DWORD iIndex,
    LPTSTR pszName,
    LPDWORD pnNameLength,
    FILETIME* pftLastWriteTime = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
サブキーのインデックス。 最初の呼び出しではこのパラメーターを0にし、その後の呼び出しに対して増分する必要があります。

*pszName*<br/>
サブキーの名前を受け取るバッファーへのポインター (終端の null 文字を含む)。 キーの完全階層ではなく、サブキーの名前のみがバッファーにコピーされます。

*pnNameLength*<br/>
*Pszname*パラメーターによって指定されたバッファーのサイズ (tchars 単位) を指定する変数へのポインター。 このサイズには、終端の null 文字を含める必要があります。 メソッドから制御が戻ったとき、 *pnNameLength*が指す変数には、バッファーに格納されている文字数が格納されます。 返されるカウントには、終端の null 文字は含まれません。

*pftLastWriteTime*<br/>
列挙されたサブキーが最後に書き込まれた時刻を受け取る変数へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

サブキーを列挙するに`CRegKey::EnumKey`は、インデックス0を使用してを呼び出します。 インデックス値をインクリメントし、メソッドが ERROR_NO_MORE_ITEMS を返すまで繰り返します。 詳細については、Windows SDK の「 [RegEnumKeyEx](/windows/win32/api/winreg/nf-winreg-regenumkeyexw) 」を参照してください。

##  <a name="flush"></a>CRegKey:: Flush

このメソッドを呼び出して、開いているレジストリキーのすべての属性をレジストリに書き込みます。

```
LONG Flush() throw();
```

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [RegEnumFlush](/windows/win32/api/winreg/nf-winreg-regflushkey) 」を参照してください。

##  <a name="getkeysecurity"></a>  CRegKey::GetKeySecurity

開いているレジストリキーを保護しているセキュリティ記述子のコピーを取得するには、このメソッドを呼び出します。

```
LONG GetKeySecurity(
    SECURITY_INFORMATION si,
    PSECURITY_DESCRIPTOR psd,
    LPDWORD pnBytes) throw();
```

### <a name="parameters"></a>パラメーター

*si*<br/>
要求されたセキュリティ情報を示す[SECURITY_INFORMATION](/windows/win32/SecAuthZ/security-information)値。

*psd*<br/>
要求されたセキュリティ記述子のコピーを受け取るバッファーへのポインター。

*pnBytes*<br/>
*Psd*によってポイントされるバッファーのサイズ (バイト単位)。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 メソッドが失敗した場合、戻り値は、WINERROR.H で定義されている0以外のエラーコードです。始め.

### <a name="remarks"></a>Remarks

詳細については、「 [Reggetkeysecurity](/windows/win32/api/winreg/nf-winreg-reggetkeysecurity)」を参照してください。

##  <a name="m_hkey"></a>  CRegKey::m_hKey

`CRegKey`オブジェクトに関連付けられたレジストリキーのハンドルを格納します。

```
HKEY m_hKey;
```

##  <a name="m_ptm"></a>  CRegKey::m_pTM

オブジェクトへの`CAtlTransactionManager`ポインター。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Remarks

##  <a name="notifychangekeyvalue"></a>  CRegKey::NotifyChangeKeyValue

このメソッドは、開いているレジストリキーの属性または内容への変更について、呼び出し元に通知します。

```
LONG NotifyChangeKeyValue(
    BOOL bWatchSubtree,
    DWORD dwNotifyFilter,
    HANDLE hEvent,
    BOOL bAsync = TRUE) throw();
```

### <a name="parameters"></a>パラメーター

*bWatchSubtree*<br/>
指定したキーとそのすべてのサブキーの変更を報告するか、または指定したキーのみをレポートするかを示すフラグを指定します。 このパラメーターが TRUE の場合、メソッドは、キーとそのサブキーの変更を報告します。 パラメーターが FALSE の場合、メソッドは、キーでのみ変更を報告します。

*dwNotifyFilter*<br/>
どのような変更を報告するかを制御するフラグのセットを指定します。 このパラメーターは、次の値の組み合わせにすることができます。

|[値]|説明|
|-----------|-------------|
|REG_NOTIFY_CHANGE_NAME|サブキーが追加または削除された場合は、呼び出し元に通知します。|
|REG_NOTIFY_CHANGE_ATTRIBUTES|セキュリティ記述子の情報など、キーの属性の変更を呼び出し元に通知します。|
|REG_NOTIFY_CHANGE_LAST_SET|キーの値に対する変更を呼び出し元に通知します。 これには、値を追加または削除したり、既存の値を変更したりすることができます。|
|REG_NOTIFY_CHANGE_SECURITY|キーのセキュリティ記述子への変更を呼び出し元に通知します。|

*hEvent*<br/>
イベントに対するハンドル。 *BAsync*パラメーターが TRUE の場合、メソッドはすぐに制御を戻し、変更はこのイベントを通知することによって報告されます。 *BAsync*が FALSE の場合、 *hevent*は無視されます。

*bAsync*<br/>
メソッドがどのように変更を報告するかを示すフラグを指定します。 このパラメーターが TRUE の場合、メソッドはすぐに制御を戻し、指定されたイベントを通知して変更を報告します。 このパラメーターが FALSE の場合、メソッドは変更が発生するまで戻りません。 *Hevent*に有効なイベントが指定されていない場合、 *BASYNC*パラメーターを TRUE にすることはできません。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  このメソッドは、指定されたキーが削除された場合に、呼び出し元に通知しません。

詳細とサンプルプログラムについては、「 [Regnotifychangekeyvalue](/windows/win32/api/winreg/nf-winreg-regnotifychangekeyvalue)」を参照してください。

##  <a name="open"></a>CRegKey:: Open

このメソッドを呼び出して、指定したキーを開き、 [m_hKey](#m_hkey)をこのキーのハンドルに設定します。

```
LONG Open(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    REGSAM samDesired = KEY_READ | KEY_WRITE) throw();
```

### <a name="parameters"></a>パラメーター

*hKeyParent*<br/>
開いているキーのハンドル。

*lpszKeyName*<br/>
作成または開くキーの名前を指定します。 この名前は、 *hsubkey Arent*のサブキーである必要があります。

*samDesired*<br/>
キーのセキュリティアクセス。 既定値は KEY_ALL_ACCESS です。 使用可能な値と説明の一覧については、Windows SDK の「 [Regcreatekeyex](/windows/win32/api/winreg/nf-winreg-regcreatekeyexw) 」を参照してください。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。それ以外の場合は、WINERROR.H で定義されている0以外のエラー値。始め.

### <a name="remarks"></a>Remarks

*Lpszkeyname*パラメーターが NULL の場合、または空の文字列を`Open`指している場合、は hキーを使って識別されるキーの新しいハンドルを開きますが、以前に開いたハンドルは閉じません。

[CRegKey:: Create](#create)とは`Open`異なり、指定されたキーが存在しない場合、では作成されません。

##  <a name="operator_hkey"></a>CRegKey:: operator HKEY

オブジェクトを`CRegKey` HKEY に変換します。

```
operator HKEY() const throw();
```

##  <a name="operator_eq"></a>CRegKey:: operator =

代入演算子。

```
CRegKey& operator= (CRegKey& key) throw();
```

### <a name="parameters"></a>パラメーター

*key*<br/>
コピーするキー。

### <a name="return-value"></a>戻り値

新しいキーへの参照を返します。

### <a name="remarks"></a>Remarks

この演算子は、現在のオブジェクトから*キー*をデタッチし、 `CRegKey`代わりにそのオブジェクトに割り当てます。

##  <a name="querybinaryvalue"></a>  CRegKey::QueryBinaryValue

指定した値の名前のバイナリデータを取得するには、このメソッドを呼び出します。

```
LONG QueryBinaryValue(
    LPCTSTR pszValueName,
    void* pValue,
    ULONG* pnBytes) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリ対象の値の名前を格納している null で終わる文字列へのポインター。

*pValue*<br/>
値のデータを受け取るバッファーへのポインター。

*pnBytes*<br/>
*PValue*パラメーターによってポイントされるバッファーのサイズ (バイト単位) を指定する変数へのポインター。 メソッドから制御が戻ると、この変数にはバッファーにコピーされたデータのサイズが格納されます。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドが値の読み取りに失敗した場合は、WINERROR.H で定義されている0以外のエラーコードを返します。始め. 参照されているデータが REG_BINARY 型でない場合は、ERROR_INVALID_DATA が返されます。

### <a name="remarks"></a>Remarks

このメソッドは、を`RegQueryValueEx`使用して、正しい型のデータが返されることを確認します。 詳細については、「 [regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)」を参照してください。

> [!IMPORTANT]
>  このメソッドを使用すると、呼び出し元は任意のレジストリの場所を指定でき、信頼できないデータを読み取る可能性があります。 また、このメソッドで使用される[regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)関数は、NULL で終了する文字列を明示的に処理しません。 呼び出し元のコードで両方の条件を確認する必要があります。

##  <a name="querydwordvalue"></a>  CRegKey::QueryDWORDValue

指定した値名の DWORD データを取得するには、このメソッドを呼び出します。

```
LONG QueryDWORDValue(
    LPCTSTR pszValueName,
    DWORD& dwValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリ対象の値の名前を格納している null で終わる文字列へのポインター。

*dwValue*<br/>
DWORD を受け取るバッファーへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドが値の読み取りに失敗した場合は、WINERROR.H で定義されている0以外のエラーコードを返します。始め. 参照されるデータが REG_DWORD 型でない場合は、ERROR_INVALID_DATA が返されます。

### <a name="remarks"></a>Remarks

このメソッドは、を`RegQueryValueEx`使用して、正しい型のデータが返されることを確認します。 詳細については、「 [regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)」を参照してください。

> [!IMPORTANT]
>  このメソッドを使用すると、呼び出し元は任意のレジストリの場所を指定でき、信頼できないデータを読み取る可能性があります。 また、このメソッドで使用される[regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)関数は、NULL で終了する文字列を明示的に処理しません。 呼び出し元のコードで両方の条件を確認する必要があります。

##  <a name="queryguidvalue"></a>  CRegKey::QueryGUIDValue

指定した値の名前の GUID データを取得するには、このメソッドを呼び出します。

```
LONG QueryGUIDValue(
    LPCTSTR pszValueName,
    GUID& guidValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリ対象の値の名前を格納している null で終わる文字列へのポインター。

*guidValue*<br/>
GUID を受け取る変数へのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドが値の読み取りに失敗した場合は、WINERROR.H で定義されている0以外のエラーコードを返します。始め. 参照されているデータが有効な GUID でない場合は、ERROR_INVALID_DATA が返されます。

### <a name="remarks"></a>Remarks

このメソッドは`CRegKey::QueryStringValue` 、を使用して、 [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring)を使用して文字列を GUID に変換します。

> [!IMPORTANT]
>  このメソッドを使用すると、呼び出し元は任意のレジストリの場所を指定でき、信頼できないデータを読み取る可能性があります。

##  <a name="querymultistringvalue"></a>  CRegKey::QueryMultiStringValue

指定した値名の文字列データを取得するには、このメソッドを呼び出します。

```
LONG QueryMultiStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリ対象の値の名前を格納している null で終わる文字列へのポインター。

*pszValue*<br/>
文字列データを受け取るバッファーへのポインター。 複数文字列は、null で終わる文字列の配列で、2つの null 文字で終了します。

*pnChars*<br/>
*Pszvalue*が指すバッファーのサイズ (tchars 単位)。 メソッドから制御が戻ったとき、取得した文字列のサイズ (tchars) には、終端の null 文字が含まれます。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドが値の読み取りに失敗した場合は、WINERROR.H で定義されている0以外のエラーコードを返します。始め. 参照されるデータの種類が REG_MULTI_SZ でない場合は、ERROR_INVALID_DATA が返されます。

### <a name="remarks"></a>Remarks

このメソッドは、を`RegQueryValueEx`使用して、正しい型のデータが返されることを確認します。 詳細については、「 [regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)」を参照してください。

> [!IMPORTANT]
>  このメソッドを使用すると、呼び出し元は任意のレジストリの場所を指定でき、信頼できないデータを読み取る可能性があります。 また、このメソッドで使用される[regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)関数は、NULL で終了する文字列を明示的に処理しません。 呼び出し元のコードで両方の条件を確認する必要があります。

##  <a name="queryqwordvalue"></a>  CRegKey::QueryQWORDValue

指定した値名の QWORD データを取得するには、このメソッドを呼び出します。

```
LONG QueryQWORDValue(
    LPCTSTR pszValueName,
    ULONGLONG& qwValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリ対象の値の名前を格納している null で終わる文字列へのポインター。

*qwValue*<br/>
QWORD を受け取るバッファーへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドが値の読み取りに失敗した場合は、WINERROR.H で定義されている0以外のエラーコードを返します。始め. 参照されているデータが REG_QWORD 型でない場合は、ERROR_INVALID_DATA が返されます。

### <a name="remarks"></a>Remarks

このメソッドは、を`RegQueryValueEx`使用して、正しい型のデータが返されることを確認します。 詳細については、「 [regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)」を参照してください。

> [!IMPORTANT]
>  このメソッドを使用すると、呼び出し元は任意のレジストリの場所を指定でき、信頼できないデータを読み取る可能性があります。 また、このメソッドで使用される[regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)関数は、NULL で終了する文字列を明示的に処理しません。 呼び出し元のコードで両方の条件を確認する必要があります。

##  <a name="querystringvalue"></a>  CRegKey::QueryStringValue

指定した値名の文字列データを取得するには、このメソッドを呼び出します。

```
LONG QueryStringValue(
    LPCTSTR pszValueName,
    LPTSTR pszValue,
    ULONG* pnChars) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリ対象の値の名前を格納している null で終わる文字列へのポインター。

*pszValue*<br/>
文字列データを受け取るバッファーへのポインター。

*pnChars*<br/>
*Pszvalue*が指すバッファーのサイズ (tchars 単位)。 メソッドから制御が戻ったとき、取得された文字列の TCHARs のサイズ (終端の null 文字を含む) が*Pnchars*に含まれています。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、ERROR_SUCCESS が返されます。 メソッドが値の読み取りに失敗した場合は、WINERROR.H で定義されている0以外のエラーコードを返します。始め. 参照されるデータの種類が REG_SZ でない場合は、ERROR_INVALID_DATA が返されます。 メソッドが ERROR_MORE_DATA を返す場合、 *Pnchars*は0であり、必要なバッファーサイズ (バイト単位) ではありません。

### <a name="remarks"></a>Remarks

このメソッドは、を`RegQueryValueEx`使用して、正しい型のデータが返されることを確認します。 詳細については、「 [regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)」を参照してください。

> [!IMPORTANT]
>  このメソッドを使用すると、呼び出し元は任意のレジストリの場所を指定でき、信頼できないデータを読み取る可能性があります。 また、このメソッドで使用される[regqueryvalueex が](/windows/win32/api/winreg/nf-winreg-regqueryvalueexw)関数は、NULL で終了する文字列を明示的に処理しません。 呼び出し元のコードで両方の条件を確認する必要があります。

##  <a name="queryvalue"></a>  CRegKey::QueryValue

[M_hKey](#m_hkey)の指定した値フィールドのデータを取得するには、このメソッドを呼び出します。 このメソッドの以前のバージョンはサポートされなくなり、ATL_DEPRECATED としてマークされます。

```
LONG QueryValue(
    LPCTSTR pszValueName,
    DWORD* pdwType,
    void* pData,
    ULONG* pnBytes) throw();

ATL_DEPRECATED LONG QueryValue(
    DWORD& dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG QueryValue(
    LPTSTR szValue,
    LPCTSTR lpszValueName,
    DWORD* pdwCount);
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
クエリ対象の値の名前を格納している null で終わる文字列へのポインター。 *Pszvaluename*が NULL または空の文字列 "" の場合、メソッドは、キーの名前なしの値または既定値 (存在する場合) の型とデータを取得します。

*pdwType*<br/>
指定された値に格納されているデータの型を示すコードを受け取る変数へのポインター。 型コードが不要な場合は、 *pdwType*パラメーターを NULL にすることができます。

*pData*<br/>
値のデータを受け取るバッファーへのポインター。 データが不要な場合は、このパラメーターに NULL を指定できます。

*pnBytes*<br/>
*PData*パラメーターによってポイントされるバッファーのサイズ (バイト単位) を指定する変数へのポインター。 メソッドから制御が戻るときに、この変数には、PData にコピーされるデータのサイズが含まれ*ます。*

*dwValue*<br/>
値フィールドの数値データ。

*lpszValueName*<br/>
照会する値フィールドを指定します。

*szValue*<br/>
値フィールドの文字列データ。

*pdwCount*<br/>
文字列データのサイズ。 この値は、最初は*szvalue*バッファーのサイズに設定されます。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。それ以外の場合は、WINERROR.H で定義されている0以外のエラーコード。始め.

### <a name="remarks"></a>Remarks

の元の2つ`QueryValue`のバージョンはサポートされなくなり、ATL_DEPRECATED としてマークされます。 これらの形式が使用されている場合、コンパイラは警告を発行します。

残りのメソッドは、Regqueryvalueex がを呼び出します。

> [!IMPORTANT]
>  このメソッドを使用すると、呼び出し元は任意のレジストリの場所を指定でき、信頼できないデータを読み取る可能性があります。 また、このメソッドで使用される Regqueryvalueex が関数は、NULL で終了する文字列を明示的に処理しません。 呼び出し元のコードで両方の条件を確認する必要があります。

##  <a name="recursedeletekey"></a>  CRegKey::RecurseDeleteKey

指定したキーをレジストリから削除し、サブキーを明示的に削除するには、このメソッドを呼び出します。

```
LONG RecurseDeleteKey(LPCTSTR lpszKey) throw();
```

### <a name="parameters"></a>パラメーター

*lpszKey*<br/>
削除するキーの名前を指定します。 この名前は、 [m_hKey](#m_hkey)のサブキーである必要があります。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。それ以外の場合は、WINERROR.H で定義されている0以外のエラー値。始め.

### <a name="remarks"></a>Remarks

キーにサブキーがある場合は、このメソッドを呼び出してキーを削除する必要があります。

##  <a name="setbinaryvalue"></a>CRegKey:: SetBinaryValue

レジストリキーのバイナリ値を設定するには、このメソッドを呼び出します。

```
LONG SetBinaryValue(
    LPCTSTR pszValueName,
    const void* pValue,
    ULONG nBytes) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*pValue*<br/>
指定された値名で格納されるデータを格納しているバッファーへのポインター。

*nBytes*<br/>
*PValue*パラメーターによって示される情報のサイズ (バイト単位) を指定します。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドは、 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)を使用してレジストリに値を書き込みます。

##  <a name="setdwordvalue"></a>CRegKey:: SetDWORDValue

レジストリキーの DWORD 値を設定するには、このメソッドを呼び出します。

```
LONG SetDWORDValue(LPCTSTR pszValueName, DWORD dwValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*dwValue*<br/>
指定された値名で格納される DWORD データ。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドは、 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)を使用してレジストリに値を書き込みます。

##  <a name="setguidvalue"></a>CRegKey:: SetGUIDValue

レジストリキーの GUID 値を設定するには、このメソッドを呼び出します。

```
LONG SetGUIDValue(LPCTSTR pszValueName, REFGUID guidValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*guidValue*<br/>
指定された値名で格納される GUID への参照。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドは`CRegKey::SetStringValue` 、を使用し、 [StringFromGUID2](/windows/win32/api/combaseapi/nf-combaseapi-stringfromguid2)を使用して GUID を文字列に変換します。

##  <a name="setkeyvalue"></a>CRegKey:: SetKeyValue

指定したキーの指定した値フィールドにデータを格納するには、このメソッドを呼び出します。

```
LONG SetKeyValue(
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL) throw();
```

### <a name="parameters"></a>パラメーター

*lpszKeyName*<br/>
作成または開くキーの名前を指定します。 この名前は、 [m_hKey](#m_hkey)のサブキーである必要があります。

*lpszValue*<br/>
格納するデータを指定します。 このパラメーターには NULL 以外の値を指定する必要があります。

*lpszValueName*<br/>
設定する値フィールドを指定します。 この名前の値フィールドがキーにまだ存在しない場合は、追加されます。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。それ以外の場合は、WINERROR.H で定義されている0以外のエラーコード。始め.

### <a name="remarks"></a>Remarks

このメソッドを呼び出して、 *Lpszkeyname*キーを作成または開き 、Lpszkeyname データを*lpszkeyname*値フィールドに格納します。

##  <a name="setkeysecurity"></a>  CRegKey::SetKeySecurity

レジストリキーのセキュリティを設定するには、このメソッドを呼び出します。

```
LONG SetKeySecurity(SECURITY_INFORMATION si, PSECURITY_DESCRIPTOR psd) throw();
```

### <a name="parameters"></a>パラメーター

*si*<br/>
設定するセキュリティ記述子のコンポーネントを指定します。 値は、次の値の組み合わせにすることができます。

|[値]|説明|
|-----------|-------------|
|DACL_SECURITY_INFORMATION|キーの随意アクセス制御リスト (DACL) を設定します。 キーには WRITE_DAC アクセスが必要です。または、呼び出し元のプロセスがオブジェクトの所有者である必要があります。|
|GROUP_SECURITY_INFORMATION|キーのプライマリグループセキュリティ識別子 (SID) を設定します。 キーには WRITE_OWNER アクセスが必要です。または、呼び出し元のプロセスがオブジェクトの所有者である必要があります。|
|OWNER_SECURITY_INFORMATION|キーの所有者 SID を設定します。 キーには WRITE_OWNER アクセスが必要です。または、呼び出し元のプロセスがオブジェクトの所有者であるか、または SE_TAKE_OWNERSHIP_NAME 特権が有効になっている必要があります。|
|SACL_SECURITY_INFORMATION|キーのシステムアクセス制御リスト (SACL: system access control list) を設定します。 キーには ACCESS_SYSTEM_SECURITY アクセスが必要です。 このアクセスを取得する適切な方法は、呼び出し元の現在のアクセストークンで SE_SECURITY_NAME[特権](/windows/win32/secauthz/privileges)を有効にし、ACCESS_SYSTEM_SECURITY アクセスのハンドルを開いて、特権を無効にすることです。|

*psd*<br/>
指定されたキーに設定するセキュリティ属性を指定する[SECURITY_DESCRIPTOR](/windows/win32/api/winnt/ns-winnt-security_descriptor)構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

キーのセキュリティ属性を設定します。 詳細については、「 [RegSetKeySecurity](/windows/win32/api/winreg/nf-winreg-regsetkeysecurity) 」を参照してください。

##  <a name="setmultistringvalue"></a>CRegKey:: SetMultiStringValue

レジストリキーの文字列値を設定するには、このメソッドを呼び出します。

```
LONG SetMultiStringValue(LPCTSTR pszValueName, LPCTSTR pszValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*pszValue*<br/>
指定された値名で格納される文字列データへのポインター。 複数文字列は、null で終わる文字列の配列で、2つの null 文字で終了します。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドは、 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)を使用してレジストリに値を書き込みます。

##  <a name="setqwordvalue"></a>CRegKey:: SetQWORDValue

レジストリキーの QWORD 値を設定するには、このメソッドを呼び出します。

```
LONG SetQWORDValue(LPCTSTR pszValueName, ULONGLONG qwValue) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*qwValue*<br/>
指定された値の名前で格納される QWORD データ。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドは、 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)を使用してレジストリに値を書き込みます。

##  <a name="setstringvalue"></a>CRegKey:: SetStringValue

レジストリ キーの文字列値を設定します。

```
LONG SetStringValue(
    LPCTSTR pszValueName,
    LPCTSTR pszValue,
    DWORD dwType = REG_SZ) throw();
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がまだ存在しない場合は、メソッドによりキーに追加されます。

*pszValue*<br/>
指定された値名で格納される文字列データへのポインター。

*dwType*<br/>
レジストリに書き込む文字列の型。REG_SZ (既定値) または REG_EXPAND_SZ (複数文字列の場合)。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。 失敗した場合は、WINERROR.H で定義されている 0 以外のエラー コードが返されます。

### <a name="remarks"></a>Remarks

このメソッドは、 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)を使用してレジストリに値を書き込みます。

##  <a name="setvalue"></a>CRegKey:: SetValue

[M_hKey](#m_hkey)の指定した値フィールドにデータを格納するには、このメソッドを呼び出します。 このメソッドの以前のバージョンはサポートされなくなり、ATL_DEPRECATED としてマークされます。

```
LONG SetValue(
    LPCTSTR pszValueName,
    DWORD dwType,
    const void* pValue,
    ULONG nBytes) throw();

static LONG WINAPI SetValue(
    HKEY hKeyParent,
    LPCTSTR lpszKeyName,
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL);

ATL_DEPRECATED LONG SetValue(
    DWORD dwValue,
    LPCTSTR lpszValueName);

ATL_DEPRECATED LONG SetValue(
    LPCTSTR lpszValue,
    LPCTSTR lpszValueName = NULL,
    bool bMulti = false,
    int nValueLen = -1);
```

### <a name="parameters"></a>パラメーター

*pszValueName*<br/>
設定する値の名前を格納する文字列へのポインター。 この名前の値がキーにまだ存在しない場合は、メソッドによってキーに追加されます。 *Pszvaluename*が NULL または空の文字列 "" の場合、メソッドは、キーの名前のない値または既定値の型とデータを設定します。

*dwType*<br/>
*PValue*パラメーターが指すデータの型を示すコードを指定します。

*pValue*<br/>
指定された値名で格納されるデータを格納しているバッファーへのポインター。

*nBytes*<br/>
*PValue*パラメーターによって示される情報のサイズ (バイト単位) を指定します。 データの種類が REG_SZ、REG_EXPAND_SZ、または REG_MULTI_SZ の場合、 *Nbytes*には終端の null 文字のサイズが含まれている必要があります。

*hKeyParent*<br/>
開いているキーのハンドル。

*lpszKeyName*<br/>
作成または開くキーの名前を指定します。 この名前は、 *hsubkey Arent*のサブキーである必要があります。

*lpszValue*<br/>
格納するデータを指定します。 このパラメーターには NULL 以外の値を指定する必要があります。

*lpszValueName*<br/>
設定する値フィールドを指定します。 この名前の値フィールドがキーにまだ存在しない場合は、追加されます。

*dwValue*<br/>
格納するデータを指定します。

*bMulti*<br/>
False の場合は、文字列が REG_SZ 型であることを示します。 True の場合、文字列が REG_MULTI_SZ 型の文字数であることを示します。

*nValueLen*<br/>
*Bmulti*が true の場合、 *Nvaluelen*は*lpszvalue*文字列の長さを文字数で示します。 *Bmulti*が false の場合、値-1 は、メソッドが長さを自動的に計算することを示します。

### <a name="return-value"></a>戻り値

成功した場合は、ERROR_SUCCESS を返します。それ以外の場合は、WINERROR.H で定義されている0以外のエラーコード。始め.

### <a name="remarks"></a>Remarks

の元の2つ`SetValue`のバージョンは ATL_DEPRECATED としてマークされているため、使用できなくなりました。 これらの形式が使用されている場合、コンパイラは警告を発行します。

3番目のメソッドは、 [RegSetValueEx](/windows/win32/api/winreg/nf-winreg-regsetvalueexw)を呼び出します。

## <a name="see-also"></a>関連項目

[DCOM のサンプル](../../overview/visual-cpp-samples.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
