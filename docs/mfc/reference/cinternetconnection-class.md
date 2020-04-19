---
title: CInternetConnection クラス
ms.date: 11/04/2016
f1_keywords:
- CInternetConnection
- AFXINET/CInternetConnection
- AFXINET/CInternetConnection::CInternetConnection
- AFXINET/CInternetConnection::GetContext
- AFXINET/CInternetConnection::GetServerName
- AFXINET/CInternetConnection::GetSession
helpviewer_keywords:
- CInternetConnection [MFC], CInternetConnection
- CInternetConnection [MFC], GetContext
- CInternetConnection [MFC], GetServerName
- CInternetConnection [MFC], GetSession
ms.assetid: 62a5d1c3-8471-4e36-a064-48831829b2a7
ms.openlocfilehash: 9f17c3ade53ec45ddde654e83c77fe1d817d8495
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62345697"
---
# <a name="cinternetconnection-class"></a>CInternetConnection クラス

インターネット サーバーへの接続を管理します。

## <a name="syntax"></a>構文

```
class CInternetConnection : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CInternetConnection::CInternetConnection](#cinternetconnection)|`CInternetConnection` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CInternetConnection::GetContext](#getcontext)|この接続オブジェクトのコンテキスト ID を取得します。|
|[CInternetConnection::GetServerName](#getservername)|接続に関連付けられているサーバーの名前を取得します。|
|[CInternetConnection::GetSession](#getsession)|ポインターを取得、 [CInternetSession](../../mfc/reference/cinternetsession-class.md)接続に関連付けられているオブジェクト。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CInternetConnection::operator HINTERNET](#operator_hinternet)|インターネット セッションへのハンドル。|

## <a name="remarks"></a>Remarks

MFC クラスの基本クラスである[CFtpConnection](../../mfc/reference/cftpconnection-class.md)、 [CHttpConnection](../../mfc/reference/chttpconnection-class.md)、および[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)します。 これらの各クラスは、それぞれ、FTP、HTTP、または gopher サーバーと通信するための追加機能を提供します。

インターネット サーバーと直接通信する必要を[CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトと`CInternetConnection`オブジェクト。

WinInet クラスの動作に関する詳細については、この記事を参照してください。[インターネットが WinInet を使用したプログラミング](../../mfc/win32-internet-extensions-wininet.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CInternetConnection`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

##  <a name="cinternetconnection"></a>  CInternetConnection::CInternetConnection

このメンバー関数が呼び出されます、`CInternetConnection`オブジェクトが作成されます。

```
CInternetConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*pSession*<br/>
ポインターを[CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクト。

*pstrServer*<br/>
サーバー名を含む文字列へのポインター。

*nPort*<br/>
この接続のインターネットのポートを識別する番号。

*dwContext*<br/>
コンテキスト識別子を`CInternetConnection`オブジェクト。 参照してください**解説**の詳細については*独自*します。

### <a name="remarks"></a>Remarks

呼び出さないように`CInternetConnection`考えてください。 代わりに、呼び出し、 [CInternetSession](../../mfc/reference/cinternetsession-class.md)を確立する接続の種類のメンバー関数。

- [CInternetSession::GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)

- [CInternetSession::GetHttpConnection](../../mfc/reference/cinternetsession-class.md#gethttpconnection)

- [CInternetSession::GetGopherConnection](../../mfc/reference/cinternetsession-class.md#getgopherconnection)

既定値*独自*に MFC によって送信される、 `CInternetConnection`-派生オブジェクトから、 [CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトの作成、**インターネット**-派生オブジェクト。 既定値を 1 に設定します。ただしで特定のコンテキスト識別子を割り当てることができますに明示的に、 [CInternetSession](../../mfc/reference/cinternetsession-class.md#cinternetsession)接続のコンス トラクター。 オブジェクトとその動作はコンテキスト ID に関連付けられる コンテキスト識別子が返される[対応](../../mfc/reference/cinternetsession-class.md#onstatuscallback)が識別されるオブジェクトの状態を提供します。 記事をご覧ください[インターネットの最初の手順。WinInet](../../mfc/wininet-basics.md)コンテキスト識別子の詳細についてはします。

##  <a name="getcontext"></a>  CInternetConnection::GetContext

このセッションのコンテキスト ID を取得するには、このメンバー関数を呼び出します。

```
DWORD_PTR GetContext() const;
```

### <a name="return-value"></a>戻り値

アプリケーションに割り当てられたコンテキストの id。

### <a name="remarks"></a>Remarks

コンテキスト ID が指定されていた[CInternetSession](../../mfc/reference/cinternetsession-class.md)し伝達`CInternetConnection`- と[CInternetFile](../../mfc/reference/cinternetfile-class.md)-表示された関数の呼び出しで異なる方法で指定されていない場合、派生クラス接続です。 コンテキスト ID が指定したオブジェクトのすべての操作に関連付けられた、によって返される操作の状態情報を識別します[対応](../../mfc/reference/cinternetsession-class.md#onstatuscallback)します。

詳細について`GetContext`ユーザー状態の情報を提供するその他の WinInet クラスは、記事を参照して[インターネットの最初の手順。WinInet](../../mfc/wininet-basics.md)コンテキスト識別子の詳細についてはします。

##  <a name="getservername"></a>  CInternetConnection::GetServerName

このインターネット接続に関連付けられたサーバーの名前を取得するには、このメンバー関数を呼び出します。

```
CString GetServerName() const;
```

### <a name="return-value"></a>戻り値

この接続オブジェクトの操作は、サーバーの名前。

##  <a name="getsession"></a>  CInternetConnection::GetSession

ポインターを取得するには、このメンバー関数を呼び出す、`CInternetSession`この接続に関連付けられているオブジェクト。

```
CInternetSession* GetSession() const;
```

### <a name="return-value"></a>戻り値

ポインターを[CInternetSession](../../mfc/reference/cinternetsession-class.md)インターネット接続オブジェクトに関連付けられているオブジェクト。

##  <a name="operator_hinternet"></a>  CInternetConnection::operator HINTERNET

この演算子を使用して、現在のインターネット セッションの API レベルのハンドルを取得します。

```
operator HINTERNET() const;
```

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
