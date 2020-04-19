---
title: CDataConnection クラス
ms.date: 03/27/2019
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
ms.openlocfilehash: 94c7025185a24b07d5968157d49c856d4359b33a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209296"
---
# <a name="cdataconnection-class"></a>CDataConnection クラス

データ ソースとの接続を管理します。

## <a name="syntax"></a>構文

```cpp
class CDataConnection
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[CDataConnection](#cdataconnection)|コンストラクターです。 インスタンスを作成し、初期化、`CDataConnection`オブジェクト。|
|[コピー](#copy)|既存のデータ接続のコピーを作成します。|
|[開く](#open)|初期化文字列を使用してデータ ソースへの接続を開きます。|
|[OpenNewSession](#opennewsession)|現在の接続で新しいセッションを開きます。|

### <a name="operators"></a>演算子

|||
|-|-|
|[BOOL 演算子](#op_bool)|現在のセッションが開いているかどうかを判断します。|
|[operator bool](#op_bool_ole)|現在のセッションが開いているかどうかを判断します。|
|[CDataSource 演算子 (& a)](#op_cdata_amp)|格納されている参照を返します`CDataSource`オブジェクト。|
|[CDataSource * 演算子](#op_cdata_star)|格納されているポインターを返します`CDataSource`オブジェクト。|
|[演算子 CSession &](#op_csession_amp)|格納されている参照を返します`CSession`オブジェクト。|
|[演算子 CSession *](#op_csession_star)|格納されているポインターを返します`CSession`オブジェクト。|

## <a name="remarks"></a>Remarks

`CDataConnection` 必要なオブジェクト (データ ソースとセッション) とデータ ソースに接続するときに行う必要がある作業の一部をカプセル化するためにクライアントを作成するための便利なクラスです。

せず`CDataConnection`、作成する必要が、`CDataSource`オブジェクトを呼び出すその[OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md)メソッドのインスタンスを作成し、 [CSession](../../data/oledb/csession-class.md)オブジェクトを呼び出すその[開いている](../../data/oledb/csession-open.md)メソッドを作成し、 [CCommand](../../data/oledb/ccommand-class.md)オブジェクトと呼び出しその`Open`* メソッド。

`CDataConnection`、接続オブジェクトを作成し、初期化文字列を渡す、コマンドを開く、その接続を使用するだけで済みます。 を繰り返し、データベースへの接続を使用する予定の場合は、開いている接続を維持することをお勧めし`CDataConnection`を実行する便利な手段を提供します。

> [!NOTE]
>  複数のセッションを処理する必要があるデータベース アプリケーションを作成する場合は、使用する必要があります。 [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)します。

## <a name="cdataconnection"></a> CDataConnection::CDataConnection

インスタンスを作成し、初期化、`CDataConnection`オブジェクト。

### <a name="syntax"></a>構文

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>パラメーター

*ds*<br/>
[in]既存のデータ接続への参照。

### <a name="remarks"></a>Remarks

最初のオーバーライドを作成する新しい`CDataConnection`既定の設定を持つオブジェクト。

2 番目のオーバーライドを作成する新しい`CDataConnection`設定を指定するデータ接続オブジェクトと等しいオブジェクト。

## <a name="copy"></a> CDataConnection::Copy

既存のデータ接続のコピーを作成します。

### <a name="syntax"></a>構文

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>パラメーター

*ds*<br/>
[in]コピーする既存のデータ接続への参照。

## <a name="open"></a> CDataConnection::Open

初期化文字列を使用してデータ ソースへの接続を開きます。

### <a name="syntax"></a>構文

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>パラメーター

*szInitString*<br/>
[in]データ ソース初期化文字列。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="opennewsession"></a> CDataConnection::OpenNewSession

現在の接続オブジェクトのデータ ソースを使用して新しいセッションを開きます。

### <a name="syntax"></a>構文

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>パラメーター

*session*<br/>
[入力/出力]新しいセッション オブジェクトへの参照。

### <a name="remarks"></a>Remarks

新しいセッションでは、現在の接続オブジェクトのデータ ソース オブジェクトが、親として使用し、すべてのデータ ソースと同じ情報にアクセスできます。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="op_bool"></a> CDataConnection::operator BOOL

現在のセッションが開いているかどうかを判断します。

### <a name="syntax"></a>構文

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Remarks

返します**BOOL** (MFC の typedef) 値。 **TRUE**現在のセッションが開いていることを意味します**FALSE**現在のセッションが閉じられたことを意味します。

## <a name="op_bool_ole"></a> Cdataconnection::operator bool (OLE DB)

現在のセッションが開いているかどうかを判断します。

### <a name="syntax"></a>構文

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Remarks

返します、 **bool** (C++ データ型) の値。 **true**現在のセッションが開いていることを意味します**false**現在のセッションが閉じられたことを意味します。

## <a name="op_cdata_amp"></a> CDataConnection::operator CDataSource&amp;

格納されている参照を返します`CDataSource`オブジェクト。

### <a name="syntax"></a>構文

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Remarks

この演算子は、包含への参照を返します`CDataSource`を渡すことにより、オブジェクト、`CDataConnection`オブジェクトを`CDataSource`参照が必要です。

### <a name="example"></a>例

関数がある場合 (など`func`の下) を受け取る、`CDataSource`使用する参照、`CDataSource&`を渡す、`CDataConnection`オブジェクトの代わりにします。

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="op_cdata_star"></a> CDataConnection::operator CDataSource*

格納されているポインターを返します`CDataSource`オブジェクト。

### <a name="syntax"></a>構文

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Remarks

この演算子が格納されているへのポインターを返します`CDataSource`を渡すことにより、オブジェクト、`CDataConnection`オブジェクトを`CDataSource`ポインターが必要です。

参照してください[演算子 CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)使用例についてはします。

## <a name="op_csession_amp"></a> Cdataconnection::operator CSession&amp;

格納されている参照を返します`CSession`オブジェクト。

### <a name="syntax"></a>構文

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Remarks

この演算子は、包含への参照を返します`CSession`を渡すことにより、オブジェクト、`CDataConnection`オブジェクトを`CSession`参照が必要です。

### <a name="example"></a>例

関数がある場合 (など`func`の下) を受け取る、`CSession`使用する参照、`CSession&`を渡す、`CDataConnection`オブジェクトの代わりにします。

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="op_csession_star"></a> Cdataconnection::operator CSession *

格納されているポインターを返します`CSession`オブジェクト。

### <a name="syntax"></a>構文

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Remarks

この演算子が格納されているへのポインターを返します`CSession`を渡すことにより、オブジェクト、`CDataConnection`オブジェクトを`CSession`ポインターが必要です。

### <a name="example"></a>例

参照してください[演算子 CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md)使用例についてはします。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)