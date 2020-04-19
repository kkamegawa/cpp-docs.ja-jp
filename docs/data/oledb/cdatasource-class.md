---
title: CDataSource クラス
ms.date: 11/04/2016
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
- ATL::CDataSource::Close
- ATL.CDataSource.Close
- CDataSource::Close
- CDataSource.Close
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- GetProperties
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
helpviewer_keywords:
- CDataSource class
- Close method
- GetInitializationString method
- GetProperties method
- GetProperty method
- Open method
- OpenFromFileName method
- OpenFromInitializationString method
- OpenWithPromptFileName method
- OpenWithServiceComponents method
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
ms.openlocfilehash: 2564d4d9b0a2e5df1f575d6f2627ce80f48533c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176086"
---
# <a name="cdatasource-class"></a>CDataSource クラス

データ ソース プロバイダー経由の接続を表す OLE DB データ ソース オブジェクトに対応します。

## <a name="syntax"></a>構文

```cpp
class CDataSource
```

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[閉じる](#close)|接続を閉じます。|
|[GetInitializationString](#getinitializationstring)|現在開かれているデータ ソースの初期化文字列を取得します。|
|[GetProperties](#getproperties)|現在接続されているデータ ソースの設定のプロパティの値を取得します。|
|[GetProperty](#getproperty)|接続されたデータ ソースに設定されている 1 つのプロパティの値を取得します。|
|[開く](#open)|いずれかを使用してプロバイダー (データ ソース) への接続を作成、 `CLSID`、 `ProgID`、または`CEnumerator`モニカーが呼び出し元によって提供されます。|
|[OpenFromFileName](#openfromfilename)|ユーザー指定のファイル名で指定されたファイルからデータ ソースを開きます。|
|[OpenFromInitializationString](#openfrominitializationstring)|初期化文字列で指定されたデータ ソースを開きます。|
|[OpenWithPromptFileName](#openwithpromptfilename)|対応するデータ ソースを開くために作成したデータ リンク ファイルを選択できます。|
|[OpenWithServiceComponents](#openwithservicecomponents)|データ リンク ダイアログ ボックスを使用してデータ ソース オブジェクトを開きます。|

## <a name="remarks"></a>Remarks

1 つまたは複数のデータベース セッションは、1 つの接続を作成できます。 これらのセッションがによって表される`CSession`します。 呼び出す必要があります[cdatasource::open](../../data/oledb/cdatasource-open.md)とのセッションを作成する前に、接続を開く`CSession::Open`します。

使用する方法の例については`CDataSource`を参照してください、 [CatDB](../../overview/visual-cpp-samples.md)サンプル。

## <a name="close"></a> CDataSource::Close

解放することによって、接続を閉じ、`m_spInit`ポインター。

### <a name="syntax"></a>構文

```cpp
void Close() throw();
```

## <a name="getinitializationstring"></a> CDataSource::GetInitializationString

現在開かれているデータ ソースの初期化文字列を取得します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>パラメーター

*pInitializationString*<br/>
[out]初期化文字列へのポインター。

*bIncludePassword*<br/>
[in]**true**場合、文字列には、パスワードが含まれています。 それ以外の場合**false**します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

結果として得られる初期化文字列を使用して、後でこのデータ ソース接続を再び開くことができます。

## <a name="getproperties"></a> Cdatasource::getproperties

接続されているデータ ソース オブジェクトに対して要求されたプロパティ情報を返します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetProperties(ULONG ulPropIDSets,
   constDBPROPIDSET* pPropIDSet,
   ULONG* pulPropertySets,
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>パラメーター

参照してください[idbproperties::getproperties](/previous-versions/windows/desktop/ms714344(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*Windows SDK にします。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

1 つのプロパティを取得する[GetProperty](../../data/oledb/cdatasource-getproperty.md)します。

## <a name="getproperty"></a> Cdatasource::getproperty

接続されているデータ ソース オブジェクトの指定したプロパティの値を返します。

### <a name="syntax"></a>構文

```cpp
HRESULT GetProperty(const GUID& guid,
   DBPROPID propid,
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>パラメーター

*guid*<br/>
[in]プロパティを取得する対象のプロパティの設定を識別する GUID。

*propid*<br/>
[in]プロパティを返すには、プロパティの ID。

*pVariant*<br/>
[out]バリアントへのポインターを`GetProperty`プロパティの値を返します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

複数のプロパティを取得する[GetProperties](../../data/oledb/cdatasource-getproperties.md)します。

## <a name="open"></a> CDataSource::Open

使用してデータ ソースへの接続を開き、 `CLSID`、 `ProgID`、または`CEnumerator`モニカー、または、ロケーター ダイアログ ボックスでユーザー。

### <a name="syntax"></a>構文

```cpp
HRESULT Open(const CLSID& clsid,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CLSID& clsid,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,
   LPCTSTR pName,  LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(const CEnumerator& enumerator,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CEnumerator& enumerator,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(HWND hWnd = GetActiveWindow(),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,
   LPCTSTR pName,LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();
```

#### <a name="parameters"></a>パラメーター

*clsid*<br/>
[in]`CLSID`のデータ プロバイダー。

*pPropSet*<br/>
[in]配列へのポインター [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))プロパティおよび設定する値を含む構造体。 参照してください[プロパティ セットとプロパティ グループ](/previous-versions/windows/desktop/ms713696(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*Windows SDK にします。

*nPropertySets*<br/>
[in]数[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))構造体が渡された、 *pPropSet*引数。

*pName*<br/>
[入力] 接続先のデータベース名。

*pUserName*<br/>
[入力] ユーザーの名前。

*pPassword*<br/>
[入力] ユーザーのパスワード。

*nInitMode*<br/>
[入力] データベースの初期化モード。 参照してください[初期化プロパティ](/previous-versions/windows/desktop/ms723127(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*有効な初期化モードの一覧については、Windows SDK に含まれています。 場合*nInitMode*がゼロ初期化モードが、接続を開くために使用するプロパティ セットに含まれます。

*szProgID*<br/>
[入力] プログラム ID。

*enumerator*<br/>
[in]A [CEnumerator](../../data/oledb/cenumerator-class.md) 、呼び出し元が指定されていない場合は、接続を開くためのモニカーを取得するために使用するオブジェクト、`CLSID`します。

*hWnd*<br/>
[入力] ダイアログ ボックスの親であるウィンドウへのハンドル。 使用する関数のオーバー ロードを使用して、 *hWnd*パラメーターがサービス コンポーネントを自動的に起動されます。 詳細については、「解説」を参照してください。

*dwPromptOptions*<br/>
[入力] 表示するロケーター ダイアログ ボックスのスタイルを指定します。 使用できる値については、Msdasc.h を参照してください。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

メソッドのオーバー ロードを使用する、 *hWnd*パラメーターは、oledb32.dll 内のサービス コンポーネントを持つデータ ソース オブジェクトを開きます。 この DLL には、リソース プールで自動などのサービス コンポーネント機能の実装が含まれています。トランザクションの参加、という具合です。 詳細については、"の OLE DB サービスでの OLE DB プログラマーズ リファレンスを参照してください。 [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)します。

メソッドのオーバー ロードを使用しない、 *hWnd*パラメーターは、oledb32.dll 内のサービス コンポーネントを使用せず、データ ソース オブジェクトを開きます。 A [CDataSource](../../data/oledb/cdatasource-class.md)これらの関数オーバー ロードで開かれたオブジェクトはサービス コンポーネントの機能を利用することはできません。

### <a name="example"></a>例

次のコードは、OLE DB テンプレートを使用して Jet 4.0 データ ソースを開く方法を示します。 Jet データ ソースは、OLE DB データ ソースとして扱います。 ただし、呼び出し`Open`2 つのプロパティ セットが必要: DBPROPSET_DBINIT、DBPROPSET_JETOLEDB_DBINIT、もう 1 つずつ DBPROP_JETOLEDB_DATABASEPASSWORD を設定できるようにします。

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="openfromfilename"></a> CDataSource::OpenFromFileName

ユーザー指定のファイル名で指定されたファイルからデータ ソースを開きます。

### <a name="syntax"></a>構文

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>パラメーター

*szFileName*<br/>
[in] ファイル名、通常はデータ ソース接続 (.UDL) ファイル。

データ リンク ファイル (.udl ファイル) の詳細については、次を参照してください。 [Data Link API の概要](/previous-versions/windows/desktop/ms718102(v=vs.85))Windows SDK に含まれています。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

このメソッドは、oledb32.dll 内のサービス コンポーネントを使ってデータ ソース オブジェクトを開きます。この DLL には、リソース共有や自動トランザクション登録などのサービス コンポーネント機能の実装が含まれています。 詳細については、"の OLE DB サービスでの OLE DB プログラマーズ リファレンスを参照してください。 [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)します。

## <a name="openfrominitializationstring"></a> CDataSource::OpenFromInitializationString

ユーザーが指定した初期化文字列で指定されたデータ ソースを開きます。

### <a name="syntax"></a>構文

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>パラメーター

*szInitializationString*<br/>
[in]初期化文字列。

*fPromptForInfo*<br/>
[in]この引数に設定されている場合**true**、し`OpenFromInitializationString`詳細が必要な場合にのみ、ユーザーが求められますことを指定する DBPROP_INIT_PROMPT プロパティを設定します。 これは、初期化文字列、パスワードが必要なデータベースを指定する場合に便利ですが、文字列にパスワードが含まれていません。 パスワード (または不足している他の情報) のユーザーが求めるデータベースに接続しようとしています。

既定値は**false**ユーザーは、メッセージを表示 (DBPROP_INIT_PROMPT を DBPROMPT_NOPROMPT セット) を決してでを指定します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

このメソッドは、oledb32.dll 内のサービス コンポーネントを使ってデータ ソース オブジェクトを開きます。この DLL には、リソース共有や自動トランザクション登録などのサービス コンポーネント機能の実装が含まれています。

## <a name="openwithpromptfilename"></a> CDataSource::OpenWithPromptFileName

このメソッドは、ダイアログ ボックスをユーザーに表示し、ユーザーが指定したファイルを使用してデータ ソースを開きます。

### <a name="syntax"></a>構文

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>パラメーター

*hWnd*<br/>
[入力] ダイアログ ボックスの親であるウィンドウへのハンドル。

*dwPromptOptions*<br/>
[入力] 表示するロケーター ダイアログ ボックスのスタイルを指定します。 使用できる値については、Msdasc.h を参照してください。

*szInitialDirectory*<br/>
[入力] ロケーター ダイアログ ボックスに表示される初期ディレクトリ。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

このメソッドは、oledb32.dll 内のサービス コンポーネントを使ってデータ ソース オブジェクトを開きます。この DLL には、リソース共有や自動トランザクション登録などのサービス コンポーネント機能の実装が含まれています。 詳細については、"の OLE DB サービスでの OLE DB プログラマーズ リファレンスを参照してください。 [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)します。

## <a name="openwithservicecomponents"></a> Cdatasource::openwithservicecomponents

oledb32.dll 内のサービス コンポーネントを使用してデータ ソース オブジェクトを開きます。

### <a name="syntax"></a>構文

```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);

HRESULT OpenWithServiceComponents (LPCSTR szProgID,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);
```

#### <a name="parameters"></a>パラメーター

*clsid*<br/>
[in]`CLSID`のデータ プロバイダー。

*szProgID*<br/>
[入力] データ プロバイダーのプログラム ID。

*pPropset*<br/>
[in]配列へのポインター [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))プロパティおよび設定する値を含む構造体。 参照してください[プロパティ セットとプロパティ グループ](/previous-versions/windows/desktop/ms713696(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*Windows SDK にします。 データ ソース オブジェクトが初期化されている場合、プロパティはデータ ソース プロパティ グループに属している必要があります。 同じプロパティが複数回指定されている場合*pPropset*プロバイダーに固有では使用されている値。 場合*ulPropSets* 0 の場合は、このパラメーターは無視されます。

*ulPropSets*<br/>
[in]数[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))構造体が渡された、 *pPropSet*引数。 0 の場合は、プロバイダーは無視されます*pPropset*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

このメソッドは、oledb32.dll 内のサービス コンポーネントを使ってデータ ソース オブジェクトを開きます。この DLL には、リソース共有や自動トランザクション登録などのサービス コンポーネント機能の実装が含まれています。 詳細については、"の OLE DB サービスでの OLE DB プログラマーズ リファレンスを参照してください。 [ https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true](https://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true)します。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)