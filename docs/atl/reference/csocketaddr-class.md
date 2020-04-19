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
ms.openlocfilehash: 2a131323e64b1bf67f76ec92e7a3e4fcba899661
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496341"
---
# <a name="csocketaddr-class"></a>CSocketAddr クラス

このクラスは、IPv4 形式と IPV6 形式の両方をサポートするホスト名をホストアドレスに変換するためのメソッドを提供します。

## <a name="syntax"></a>構文

```
class CSocketAddr
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSocketAddr:: CSocketAddr](#csocketaddr)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSocketAddr::FindAddr](#findaddr)|指定したホスト名をホストアドレスに変換するには、このメソッドを呼び出します。|
|[CSocketAddr::FindINET4Addr](#findinet4addr)|IPv4 ホスト名をホストアドレスに変換するには、このメソッドを呼び出します。|
|[CSocketAddr::FindINET6Addr](#findinet6addr)|IPv6 ホスト名をホストアドレスに変換するには、このメソッドを呼び出します。|
|[CSocketAddr::GetAddrInfo](#getaddrinfo)|`addrinfo`リスト内の特定の要素へのポインターを返すには、このメソッドを呼び出します。|
|[CSocketAddr::GetAddrInfoList](#getaddrinfolist)|`addrinfo`リストへのポインターを返すには、このメソッドを呼び出します。|

## <a name="remarks"></a>Remarks

このクラスは、ライブラリ内の Windows sockets API 関数およびソケットラッパーで使用されるネットワークアドレスを検索するための、IP バージョンに依存しないアプローチを提供します。

ネットワークアドレスを検索するために使用されるこのクラスのメンバーは、Win32 API 関数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)を使用します。 Ansi または UNICODE バージョンの関数は、コードが ANSI または UNICODE のどちら用にコンパイルされているかによって呼び出されます。

このクラスは、IPv4 andIPv6 ネットワークアドレスの両方をサポートします。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsocket .h

##  <a name="csocketaddr"></a>  CSocketAddr::CSocketAddr

コンストラクターです。

```
CSocketAddr();
```

### <a name="remarks"></a>Remarks

新しい`CSocketAddr`オブジェクトを作成し、ホストに関する応答情報を含むリンクリストを初期化します。

##  <a name="findaddr"></a>  CSocketAddr::FindAddr

指定したホスト名をホストアドレスに変換するには、このメソッドを呼び出します。

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
ホスト名またはドット形式の IP アドレス。

*szPortOrServiceName*<br/>
ホスト上のサービスのポート番号または名前。

*nPortNo*<br/>
ポート番号。

*flags*<br/>
0または AI_PASSIVE、AI_CANONNAME、または AI_NUMERICHOST の組み合わせ。

*addr_family*<br/>
アドレスファミリ (PF_INET など)。

*sock_type*<br/>
ソケットの種類 (SOCK_STREAM など)。

*ai_proto*<br/>
プロトコル (IPPROTO_IP や IPPROTO_IPV6 など)。

### <a name="return-value"></a>戻り値

アドレスが正常に計算された場合は0を返します。 エラー発生時に0以外の Windows ソケットエラーコードを返します。 成功した場合、計算されたアドレスは、および`CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`を使用して参照できるリンクリストに格納されます。

### <a name="remarks"></a>Remarks

ホスト名パラメーターは、IPv4 形式または IPv6 形式のいずれかにすることができます。 このメソッドは Win32 API 関数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)を呼び出して変換を実行します。

##  <a name="findinet4addr"></a>  CSocketAddr::FindINET4Addr

IPv4 ホスト名をホストアドレスに変換するには、このメソッドを呼び出します。

```
int FindINET4Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>パラメーター

*szHost*<br/>
ホスト名またはドット形式の IP アドレス。

*nPortNo*<br/>
ポート番号。

*flags*<br/>
0または AI_PASSIVE、AI_CANONNAME、または AI_NUMERICHOST の組み合わせ。

*sock_type*<br/>
ソケットの種類 (SOCK_STREAM など)。

### <a name="return-value"></a>戻り値

アドレスが正常に計算された場合は0を返します。 エラー発生時に0以外の Windows ソケットエラーコードを返します。 成功した場合、計算されたアドレスは、および`CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`を使用して参照できるリンクリストに格納されます。

### <a name="remarks"></a>Remarks

このメソッドは Win32 API 関数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)を呼び出して変換を実行します。

##  <a name="findinet6addr"></a>  CSocketAddr::FindINET6Addr

IPv6 ホスト名をホストアドレスに変換するには、このメソッドを呼び出します。

```
int FindINET6Addr(
    const TCHAR *szHost,
    int nPortNo,
    int flags = 0,
    int sock_type = SOCK_STREAM);
```

### <a name="parameters"></a>パラメーター

*szHost*<br/>
ホスト名またはドット形式の IP アドレス。

*nPortNo*<br/>
ポート番号。

*flags*<br/>
0または AI_PASSIVE、AI_CANONNAME、または AI_NUMERICHOST の組み合わせ。

*sock_type*<br/>
ソケットの種類 (SOCK_STREAM など)。

### <a name="return-value"></a>戻り値

アドレスが正常に計算された場合は0を返します。 エラー発生時に0以外の Windows ソケットエラーコードを返します。 成功した場合、計算されたアドレスは、および`CSocketAddr::GetAddrInfoList` `CSocketAddr::GetAddrInfo`を使用して参照できるリンクリストに格納されます。

### <a name="remarks"></a>Remarks

このメソッドは Win32 API 関数[getaddrinfo](/windows/win32/api/ws2tcpip/nf-ws2tcpip-getaddrinfo)を呼び出して変換を実行します。

##  <a name="getaddrinfo"></a>  CSocketAddr::GetAddrInfo

`addrinfo`リスト内の特定の要素へのポインターを返すには、このメソッドを呼び出します。

```
addrinfo* const GetAddrInfo(int nIndex = 0) const;
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
[Addrinfo](/windows/win32/api/ws2def/ns-ws2def-addrinfow)リスト内の特定の要素への参照。

### <a name="return-value"></a>戻り値

ホストに関する応答情報`addrinfo`を格納している、リンクリスト内の*nIndex*によって参照されている構造体へのポインターを返します。

##  <a name="getaddrinfolist"></a>  CSocketAddr::GetAddrInfoList

`addrinfo`リストへのポインターを返すには、このメソッドを呼び出します。

```
addrinfo* const GetAddrInfoList() const;
```

### <a name="return-value"></a>戻り値

ホストに関する応答情報を格納して`addrinfo`いる1つまたは複数の構造体のリンクリストへのポインター。 詳細については、「 [addrinfo 構造体](/windows/win32/api/ws2def/ns-ws2def-addrinfow)」を参照してください。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
