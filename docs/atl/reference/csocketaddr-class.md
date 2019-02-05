---
title: CSocketAddr クラス
ms.date: 10/22/2018
f1_keywords:
- CSocketAddr
- ATLSOCKET/ATL::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::CSocketAddr
- ATLSOCKET/ATL::CSocketAddr::FindAddr
- ATLSOCKET/ATL::CSocketAddr::FindINET4Addr
- ATLSOCKET/ATL::CSocketAddr::FindINET6Addr
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfo
- ATLSOCKET/ATL::CSocketAddr::GetAddrInfoList
helpviewer_keywords:
- CSocketAddr class
ms.assetid: 2fb2d8a7-899e-4a36-a342-cc9f4fcdd68c
ms.openlocfilehash: cc0c5f0abc125138c5068682c828a3438dec5102
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893354"
---
# <a name="csocketaddr-class"></a>CSocketAddr クラス

このクラスは、ホスト アドレス、IPv4 と IPV6 の両方の形式をサポートしているホスト名に変換するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
class CSocketAddr
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSocketAddr::CSocketAddr](#csocketaddr)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|指定されたホスト名をホストのアドレスに変換するには、このメソッドを呼び出します。|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|ホスト アドレスを IPv4 ホスト名を変換するには、このメソッドを呼び出します。|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|ホスト アドレス、IPv6 ホスト名を変換するには、このメソッドを呼び出します。|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|特定の要素へのポインターを返すには、このメソッドを呼び出す、`addrinfo`一覧。|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|ポインターを返すには、このメソッドを呼び出して、`addrinfo`一覧。|

## <a name="remarks"></a>Remarks

このクラスは、IP バージョンを Windows で使用するためのネットワーク アドレスを検索するための柔軟なアプローチはソケット API 関数やライブラリのソケット ラッパーを提供します。

ネットワーク アドレスを検索するために使用するこのクラスのメンバーは、Win32 API 関数を使用して[getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)します。 ANSI または UNICODE のバージョンの関数は ANSI または UNICODE のコードをコンパイルするかどうかによって呼び出されます。

このクラスは、両方の IPv4 と Ipv6 ネットワーク アドレスをサポートします。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsocket.h

##  <a name="csocketaddr"></a>  CSocketAddr::CSocketAddr

コンストラクターです。

```
CSocketAddr();
```

### <a name="remarks"></a>Remarks

新たに作成`CSocketAddr`オブジェクトし、応答については、ホストを含むリンク リストを初期化します。

##  <a name="findaddr"></a>  CSocketAddr::FindAddr

指定されたホスト名をホストのアドレスに変換するには、このメソッドを呼び出します。

```
int FindAddr(
    const TCHAR *szHost,
    const TCHAR *szPortOrServiceName,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);

int FindAddr(
    const TCHAR *szHost,
    int nPortNo,
    int flags,
    int addr_family,
    int sock_type,
    int ai_proto);
```

### <a name="parameters"></a>パラメーター

*szHost*<br/>
ホスト名または IP アドレスのドット形式。

*szPortOrServiceName*<br/>
ポート番号またはホスト上のサービスの名前。

*nPortNo*<br/>
ポート番号。

*flags*<br/>
0 または AI_PASSIVE、AI_CANONNAME または AI_NUMERICHOST の組み合わせ。

*addr_family*<br/>
アドレス ファミリ (PF_INET) など。

*sock_type*<br/>
ソケットの種類 (SOCK_STREAM) などです。

*ai_proto*<br/>
(移植または IPPROTO_IPV6) などのプロトコルです。

### <a name="return-value"></a>戻り値

アドレスが正常に計算される場合は、0 を返します。 0 以外の Windows ソケット エラー コードを返します。 成功するのかどうか、計算されるアドレスを使用して参照されているリンクされたリストに格納された`CSocketAddr::GetAddrInfoList`と`CSocketAddr::GetAddrInfo`します。

### <a name="remarks"></a>Remarks

IPv4 または IPv6 のいずれかの形式で、ホスト名のパラメーターがあります。 このメソッドは、Win32 API 関数を呼び出す[getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)変換を実行します。

##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr

ホスト アドレスを IPv4 ホスト名を変換するには、このメソッドを呼び出します。

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>パラメーター

*szHost*<br/>
ホスト名または IP アドレスのドット形式。

*nPortNo*<br/>
ポート番号。

*flags*<br/>
0 または AI_PASSIVE、AI_CANONNAME または AI_NUMERICHOST の組み合わせ。

*sock_type*<br/>
ソケットの種類 (SOCK_STREAM) などです。

### <a name="return-value"></a>戻り値

アドレスが正常に計算される場合は、0 を返します。 0 以外の Windows ソケット エラー コードを返します。 成功するのかどうか、計算されるアドレスを使用して参照されているリンクされたリストに格納された`CSocketAddr::GetAddrInfoList`と`CSocketAddr::GetAddrInfo`します。

### <a name="remarks"></a>Remarks

このメソッドは、Win32 API 関数を呼び出す[getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)変換を実行します。

##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr

ホスト アドレス、IPv6 ホスト名を変換するには、このメソッドを呼び出します。

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>パラメーター

*szHost*<br/>
ホスト名または IP アドレスのドット形式。

*nPortNo*<br/>
ポート番号。

*flags*<br/>
0 または AI_PASSIVE、AI_CANONNAME または AI_NUMERICHOST の組み合わせ。

*sock_type*<br/>
ソケットの種類 (SOCK_STREAM) などです。

### <a name="return-value"></a>戻り値

アドレスが正常に計算される場合は、0 を返します。 0 以外の Windows ソケット エラー コードを返します。 成功するのかどうか、計算されるアドレスを使用して参照されているリンクされたリストに格納された`CSocketAddr::GetAddrInfoList`と`CSocketAddr::GetAddrInfo`します。

### <a name="remarks"></a>Remarks

このメソッドは、Win32 API 関数を呼び出す[getaddrinfo](/windows/desktop/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)変換を実行します。

##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo

特定の要素へのポインターを返すには、このメソッドを呼び出す、`addrinfo`一覧。

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
特定の要素への参照、 [addrinfo](/windows/desktop/api/ws2def/ns-ws2def-addrinfoa)一覧。

### <a name="return-value"></a>戻り値

ポインターを返します、`addrinfo`構造によって参照される*nIndex*ホストについての応答情報を格納しているリンクのリスト。

##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList

ポインターを返すには、このメソッドを呼び出して、`addrinfo`一覧。

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>戻り値

1 つまたは複数のリンク リストへのポインター`addrinfo`応答については、ホストを含む構造体。 詳細については、次を参照してください。 [addrinfo 構造](/windows/desktop/api/ws2def/ns-ws2def-addrinfoa)します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
