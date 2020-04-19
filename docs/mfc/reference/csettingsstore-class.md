---
title: CSettingsStore Class
ms.date: 11/04/2016
f1_keywords:
- CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::CSettingsStore
- AFXSETTINGSSTORE/CSettingsStore::Close
- AFXSETTINGSSTORE/CSettingsStore::CreateKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteKey
- AFXSETTINGSSTORE/CSettingsStore::DeleteValue
- AFXSETTINGSSTORE/CSettingsStore::Open
- AFXSETTINGSSTORE/CSettingsStore::Read
- AFXSETTINGSSTORE/CSettingsStore::Write
helpviewer_keywords:
- CSettingsStore [MFC], CSettingsStore
- CSettingsStore [MFC], Close
- CSettingsStore [MFC], CreateKey
- CSettingsStore [MFC], DeleteKey
- CSettingsStore [MFC], DeleteValue
- CSettingsStore [MFC], Open
- CSettingsStore [MFC], Read
- CSettingsStore [MFC], Write
ms.assetid: 0ea181de-a13e-4b29-b560-7c43838223ff
ms.openlocfilehash: 75d86b81d9651e5892913af5919ae0a78fe6bbc5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502922"
---
# <a name="csettingsstore-class"></a>CSettingsStore Class

Windows API 関数をラップし、レジストリへのアクセスに使用するオブジェクト指向インターフェイスを提供します。

## <a name="syntax"></a>構文

```
class CSettingsStore : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSettingsStore:: CSettingsStore](#csettingsstore)|`CSettingsStore` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSettingsStore:: Close](#close)|開いているレジストリキーを閉じます。|
|[CSettingsStore::CreateKey](#createkey)|指定されたキーを開くか、存在しない場合は作成します。|
|[CSettingsStore::DeleteKey](#deletekey)|指定したキーとそのすべての子を削除します。|
|[CSettingsStore::D eleteValue](#deletevalue)|開いているキーの指定した値を削除します。|
|[CSettingsStore:: Open](#open)|指定されたキーを開きます。|
|[CSettingsStore::Read](#read)|指定されたキー値のデータを取得します。|
|[CSettingsStore:: Write](#write)|レジストリの open キーの下に値を書き込みます。|

## <a name="remarks"></a>Remarks

メンバー関数`CreateKey`と`Open`は非常に似ています。 レジストリキーが既に存在する`CreateKey`場合`Open`は、同じように機能します。 ただし、レジストリキーが存在しない場合は`CreateKey` 、によっ`Open`て作成され、エラー値が返されます。

## <a name="example"></a>例

次の例は、 `CSettingsStore`クラスの Open メソッドと Read メソッドを使用する方法を示しています。 このコードスニペットは、[ツールヒントのデモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_ToolTipDemo#1](../../mfc/reference/codesnippet/cpp/csettingsstore-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CSettingsStore`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxsettingsstore

##  <a name="close"></a>  CSettingsStore::Close

開いているレジストリキーを閉じます。

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

既定では、このメソッドは[Csettingsstore クラス](../../mfc/reference/csettingsstore-class.md)のデストラクターから呼び出されます。

##  <a name="createkey"></a>  CSettingsStore::CreateKey

レジストリキーを開くか、存在しない場合は作成します。

```
virtual BOOL CreateKey(LPCTSTR pszPath);
```

### <a name="parameters"></a>パラメーター

*pszPath*<br/>
から作成または開くキーの名前を指定します。

### <a name="return-value"></a>戻り値

成功した場合は0。それ以外の場合は0以外の値。

### <a name="remarks"></a>Remarks

`CreateKey`は`m_hKey` 、レジストリの照会のルートとしてを使用します。 このメソッドは、 *Pszpath*をの`m_hKey`サブキーとして検索します。 キーが存在しない場合は`CreateKey` 、によって作成されます。 それ以外の場合は、キーを開きます。 `CreateKey`次に`m_hKey` 、を作成または開いたキーに設定します。

##  <a name="csettingsstore"></a>CSettingsStore:: CSettingsStore

`CSettngsStore` オブジェクトを作成します。

```
CSettingsStore(
    BOOL bAdmin,
    BOOL bReadOnly);
```

### <a name="parameters"></a>パラメーター

*bAdmin*<br/>
からオブジェクトが管理者モードで`CSettingsStore`動作しているかどうかを指定するブール型パラメーターです。

*bReadOnly*<br/>
からオブジェクトが読み取り専用モードで`CSettingsStore`作成されているかどうかを指定するブール型パラメーターです。

### <a name="remarks"></a>Remarks

*Badmin*が TRUE に設定されて`m_hKey`いる場合、メンバー変数は**HKEY_LOCAL_MACHINE**に設定されます。 *Badmin*を FALSE に設定すると`m_hKey` 、が**HKEY_CURRENT_USER**に設定されます。

セキュリティアクセスは、 *bReadOnly*パラメーターに依存します。 *BReadonly*が FALSE の場合、セキュリティアクセスは**KEY_ALL_ACCESS**に設定されます。 *BReadyOnly*が TRUE の場合、セキュリティアクセスは、 **KEY_QUERY_VALUE、KEY_NOTIFY** 、および**KEY_ENUMERATE_SUB_KEYS**の組み合わせに設定されます。 レジストリとのセキュリティアクセスの詳細については、「[レジストリキーのセキュリティとアクセス権](/windows/win32/SysInfo/registry-key-security-and-access-rights)」を参照してください。

の`CSettingsStore`デストラクターは、 `m_hKey`自動的に解放されます。

##  <a name="deletekey"></a>  CSettingsStore::DeleteKey

レジストリからキーとそのすべての子を削除します。

```
virtual BOOL DeleteKey(
    LPCTSTR pszPath,
    BOOL bAdmin = FALSE);
```

### <a name="parameters"></a>パラメーター

*pszPath*<br/>
から削除するキーの名前。

*bAdmin*<br/>
から削除するキーの場所を指定するスイッチ。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

オブジェクトが読み取り専用モードの`CSettingsStore`場合、このメソッドは失敗します。

パラメーター *badmin*が0の場合は`DeleteKey` 、 **HKEY_CURRENT_USER**の下で削除するキーを検索します。 *Badmin*が0以外の`DeleteKey`場合は、 **HKEY_LOCAL_MACHINE**の下で削除するキーを検索します。

##  <a name="deletevalue"></a>  CSettingsStore::DeleteValue

から`m_hKey`値を削除します。

```
virtual BOOL DeleteValue(LPCTSTR pszValue);
```

### <a name="parameters"></a>パラメーター

*pszValue*<br/>
から削除する値フィールドを指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="open"></a>  CSettingsStore::Open

レジストリキーを開きます。

```
virtual BOOL Open(LPCTSTR pszPath);
```

### <a name="parameters"></a>パラメーター

*pszPath*<br/>
からレジストリキーの名前。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメソッドは、指定されたキーを正常`m_hKey`に開くと、このキーのハンドルにを設定します。

##  <a name="read"></a>  CSettingsStore::Read

レジストリ内のキーから値を読み取ります。

```
virtual BOOL Read(
    LPCTSTR pszKey,
    int& iVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    DWORD& dwVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CString& sVal);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Read(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Read(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Read(
    LPCTSTR pszKey,
    CRect& rect);

virtual BOOL Read(
    LPCTSTR pszKey,
    BYTE** ppData,
    UINT* pBytes);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Read(
    LPCTSTR pszKey,
    CObject*& pObj);
```

### <a name="parameters"></a>パラメーター

*pszKey*<br/>
からレジストリから読み取る値の名前を含む null で終わる文字列へのポインター。

*iVal*<br/>
入出力レジストリキーから読み取られた値を受け取る整数変数への参照。

*dwVal*<br/>
入出力レジストリキーから読み取られた値を受け取る32ビットのダブルワード変数への参照。

*sVal*<br/>
入出力レジストリキーから読み取られた値を受け取る文字列変数への参照。

*scStringList*<br/>
入出力レジストリキーから読み取られた値を受け取る文字列リスト変数への参照。

*scArray*<br/>
入出力レジストリキーから読み取られた値を受け取る文字列配列変数への参照。

*dwcArray*<br/>
入出力レジストリキーから読み取られた値を受け取る32ビットの double ワード配列変数への参照。

*wcArray*<br/>
入出力レジストリキーから読み取られた値を受け取る16ビットワード配列変数への参照。

*bcArray*<br/>
入出力レジストリキーから読み取られた値を受け取るバイト配列変数への参照。

*lpPoint*<br/>
入出力レジストリキーから読み取られた`POINT`値を受け取る構造体へのポインターへの参照。

*rect*<br/>
入出力レジストリキーから読み取られた値を受け取る、 [CRect](../../atl-mfc-shared/reference/crect-class.md)変数への参照。

*ppData*<br/>
入出力レジストリキーから読み取られた値を受け取るデータへのポインターへのポインター。

*pBytes*<br/>
入出力符号なし整数変数へのポインター。 この変数は、 *Ppdata*が指すバッファーのサイズを受け取ります。

*リスト*<br/>
入出力レジストリキーから読み取られた値を受け取る、 [CObList](../../mfc/reference/coblist-class.md)変数への参照。

*obj*<br/>
入出力レジストリキーから読み取られた値を受け取る[CObject](../../mfc/reference/cobject-class.md)変数への参照。

*pObj*<br/>
入出力レジストリキーから読み取られた`CObject`値を受け取る変数へのポインターへの参照。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

`Read`*Pszkey*がの`m_hKey`サブキーとしてチェックされます。

##  <a name="write"></a>  CSettingsStore::Write

レジストリの open キーの下に値を書き込みます。

```
virtual BOOL Write(
    LPCTSTR pszKey,
    int iVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    DWORD dwVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPCTSTR pszVal);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringList& scStringList);

virtual BOOL Write(
    LPCTSTR pszKey,
    CByteArray& bcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CStringArray& scArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CDWordArray& dwcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    CWordArray& wcArray);

virtual BOOL Write(
    LPCTSTR pszKey,
    const CRect& rect);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPPOINT& lpPoint);

virtual BOOL Write(
    LPCTSTR pszKey,
    LPBYTE pData,
    UINT nBytes);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObList& list);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject& obj);

virtual BOOL Write(
    LPCTSTR pszKey,
    CObject* pObj);
```

### <a name="parameters"></a>パラメーター

*pszKey*<br/>
から設定する値の名前を含む文字列へのポインター。

*iVal*<br/>
から格納するデータを格納している整数変数への参照。

*dwVal*<br/>
から格納するデータを格納する32ビットの double ワード変数への参照。

*pszVal*<br/>
から格納するデータを格納している null で終わる文字列変数へのポインター。

*scStringList*<br/>
から格納するデータを格納している[Cstringlist](../../mfc/reference/cstringlist-class.md)変数への参照。

*bcArray*<br/>
から格納するデータを格納しているバイト配列変数への参照。

*scArray*<br/>
から格納するデータを格納する文字列配列変数への参照。

*dwcArray*<br/>
から格納するデータを格納する32ビットの double ワード配列変数への参照。

*wcArray*<br/>
から格納するデータを格納している16ビットワード配列変数への参照。

*rect*<br/>
から格納するデータを含む[CRect](../../atl-mfc-shared/reference/crect-class.md)変数への参照。

*lpPoint*<br/>
から格納するデータを格納し`POINT`ている変数へのポインターへの参照。

*pData*<br/>
から格納するデータを格納しているバッファーへのポインター。

*nBytes*<br/>
から*PData*パラメーターが指すデータのサイズをバイト単位で指定します。

*リスト*<br/>
から格納するデータを含む、 [CObList](../../mfc/reference/coblist-class.md)変数への参照。

*obj*<br/>
から格納するデータを格納している[CObject](../../mfc/reference/cobject-class.md)変数への参照。

*pObj*<br/>
から格納するデータを格納し`CObject`ている変数へのポインターへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

レジストリに書き込むには、 [Csettingsstore](../../mfc/reference/csettingsstore-class.md)オブジェクトを作成するときに、 *bReadOnly*を0以外の値に設定する必要があります。 詳細については、「 [csettingsstore:: csettingsstore](#csettingsstore)」を参照してください。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)
