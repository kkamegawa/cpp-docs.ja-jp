---
title: CCommand クラス
ms.date: 11/04/2016
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
- CCommand.Close
- CCommand::Close
- CCommand.Create
- CCommand::Create
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
- CCommand.Prepare
- CCommand::Prepare
- Prepare
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
helpviewer_keywords:
- CCommand class
- Close method
- Create method [C++]
- CreateCommand method
- GetNextResult method
- GetParameterInfo method
- Open method
- Prepare method
- ReleaseCommand method
- SetParameterInfo method
- Unprepare method
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
ms.openlocfilehash: 406a78ff1958d565fcc74781f6a63d4784f48bfc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176097"
---
# <a name="ccommand-class"></a>CCommand クラス

設定およびコマンドを実行するメソッドを提供します。

## <a name="syntax"></a>構文

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset,
   class TMultiple = CNoMultipleResults>
class CCommand :
   public CAccessorRowset <TAccessor, TRowset>,
   public CCommandBase,
   public TMultiple
```

### <a name="parameters"></a>パラメーター

*TAccessor*<br/>
アクセサー クラスの型 (など`CDynamicParameterAccessor`、 `CDynamicStringAccessor`、または`CEnumeratorAccessor`) コマンドで使用します。 既定値は`CNoAccessor`クラスは、こと、いないパラメーターをサポートまたは出力列を指定します。

*TRowset*<br/>
行セット クラスの型 (など`CArrayRowset`または`CNoRowset`) コマンドで使用します。 既定値は `CRowset` です。

*TMultiple*<br/>
複数の結果を返すことができる OLE DB コマンドを使用する指定[CMultipleResults](../../data/oledb/cmultipleresults-class.md)します。 それ以外の場合、使用[CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md)します。 詳細については、次を参照してください。 [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85))します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atldbcli.h

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[閉じる](#close)|現在のコマンドを閉じます。|
|[GetNextResult](#getnextresult)|複数の結果セットを使用する場合は、次の結果をフェッチします。|
|[開く](#open)|実行し、必要に応じて、コマンドをバインドします。|

### <a name="inherited-methods"></a>継承されたメソッド

|||
|-|-|
|[作成](#create)|指定したセッションの新しいコマンドを作成し、コマンド テキストを設定します。|
|[CreateCommand](#createcommand)|新しいコマンドを作成します。|
|[GetParameterInfo](#getparameterinfo)|コマンドのパラメーター、その名前とその型の一覧を取得します。|
|[準備します。](#prepare)|検証し、現在のコマンドを最適化します。|
|[ReleaseCommand](#releasecommand)|必要に応じて、パラメーター アクセサーを解放し、コマンドを解放します。|
|[SetParameterInfo](#setparameterinfo)|各コマンドのパラメーターのネイティブな型を指定します。|
|[Unprepare](#unprepare)|現在のコマンドの実行プランを破棄します。|

## <a name="remarks"></a>Remarks

パラメーターに基づく操作を実行またはコマンドを実行する必要がある場合は、このクラスを使用します。 単なる単純な行セットを開く必要がある場合を使用して、 [CTable](../../data/oledb/ctable-class.md)代わりにします。

使用するアクセサー クラスは、パラメーターおよびデータを連結する方法を決定します。

できませんを使用するストアド プロシージャの OLE DB Provider for Jet そのプロバイダーがサポートされていないためには、(クエリ文字列で定数のみを使用) の手順が格納されています。

## <a name="close"></a> Ccommand::close

コマンドに関連付けられているアクセサーの行セットを解放します。

### <a name="syntax"></a>構文

```cpp
void Close();
```

### <a name="remarks"></a>Remarks

コマンドは、行セット、結果セットのアクセサー、および (必要に応じて) (テーブル、パラメーターをサポートしており、パラメーター アクセサー必要はありません) とは異なり、パラメーター アクセサーを使用します。

コマンドを実行するときに、両方を呼び出す必要があります`Close`と[ReleaseCommand](../../data/oledb/ccommand-releasecommand.md)コマンドの後にします。

同じコマンドを繰り返し実行するときに呼び出すことによって各結果セットのアクセサーを解除する必要が`Close`呼び出す前に`Execute`します。 系列の末尾には、呼び出すことによってパラメーター アクセサーを解放する必要があります`ReleaseCommand`します。 もう 1 つの一般的なシナリオが出力パラメーターを持つストアド プロシージャを呼び出すことです。 (SQL Server 用の OLE DB プロバイダー) などの多くのプロバイダーでは、結果セットのアクセサーを終了するまで、出力パラメーター値をアクセスできません。 呼び出す`Close`返された行セットと結果セットのアクセサーは、パラメーター アクセサーを閉じるできるので、出力パラメーターの値を取得します。

### <a name="example"></a>例

次の例は、呼び出す方法を示しています。`Close`と`ReleaseCommand`繰り返し、同じコマンドを実行するとします。

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="getnextresult"></a> CCommand::GetNextResult

次の結果セットがある場合をフェッチします。

### <a name="syntax"></a>構文

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>パラメーター

*pulRowsAffected*<br/>
[入力/出力]コマンドによって影響を受ける行の数が返されるメモリへのポインター。

*bBind*<br/>
[in]実行されている後に、コマンドを自動的にバインドするかどうかを指定します。 既定値は**true**、それが原因で、コマンドを自動的に連結されます。 設定*bBind*に**false**手動でバインドできるように、コマンドの自動に連結します。 (手動バインドは、OLAP ユーザーにとって特に重要ですが) です。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

結果セットが既にフェッチされている場合、この関数は前の結果セットを解放し、列をバインド解除します。 場合*bBind*は**true**、新しい列をバインドします。

複数の結果を設定して指定した場合にのみ、この関数を呼び出す必要があります、`CCommand`テンプレート パラメーター *TMultiple*=`CMultipleResults`します。

## <a name="open"></a> CCommand::Open

実行し、必要に応じて、コマンドをバインドします。

### <a name="syntax"></a>構文

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   LPCSTR szCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   INT szCommand = NULL,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>パラメーター

*session*<br/>
[in]コマンドを実行するためのセッションです。

*wszCommand*<br/>
[in]を実行するコマンドは、Unicode 文字列として渡されます。 使用する場合、NULL を指定できます`CAccessor`に渡された値からのコマンドは、取得した場合、 [DEFINE_COMMAND](../../data/oledb/define-command.md)マクロ。 参照してください[icommand::execute](/previous-versions/windows/desktop/ms718095(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*詳細についてはします。

*szCommand*<br/>
[in]同じ*wszCommand*する点を除いて、このパラメーターは、ANSI コマンド文字列を取得します。 このメソッドの 4 番目の形式は、NULL 値をとることができます。 詳細については、このトピックの後半の「解説」を参照してください。

*pPropSet*<br/>
[in]配列へのポインター [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))プロパティおよび設定する値を含む構造体。 参照してください[プロパティ セットとプロパティ グループ](/previous-versions/windows/desktop/ms713696(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*Windows SDK にします。

*pRowsAffected*<br/>
[入力/出力]コマンドによって影響を受ける行の数が返されるメモリへのポインター。 場合 *\*pRowsAffected*が null の場合、行カウントは返されません。 それ以外の場合、`Open`設定 *\*pRowsAffected*に従って、次の条件。

|If|Then|
|--------|----------|
|`cParamSets`要素の`pParams`が 1 より大きい|*\*pRowsAffected*実行で指定されたパラメーター セットの影響を受けた行の合計数を表します。|
|影響を受けた行の数がご利用いただけません|*\*pRowsAffected*が-1 に設定します。|
|コマンドが更新されない、削除、または行を挿入|*\*pRowsAffected*が定義されていません。|

*guidCommand*<br/>
[in]コマンド テキストを解析中に、構文と使用するプロバイダーの一般的な規則を指定する GUID。 参照してください[ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85))と[icommandtext::setcommandtext](/previous-versions/windows/desktop/ms709757(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*詳細についてはします。

*bBind*<br/>
[in]実行されている後に、コマンドを自動的にバインドするかどうかを指定します。 既定値は**true**、それが原因で、コマンドを自動的に連結されます。 設定*bBind*に**false**手動でバインドできるように、コマンドの自動に連結します。 (手動バインドは、OLAP ユーザーにとって特に重要ですが) です。

*ulPropSets*<br/>
[in]数[DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85))構造体が渡された、 *pPropSet*引数。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

最初の 3 つのフォーム`Open`セッションをとり、コマンドを作成し、必要に応じて、任意のパラメーターのバインドのコマンドを実行します。

最初のフォーム`Open`は Unicode コマンド文字列を受け取り、既定値はありません。

2 番目の形式の`Open`ANSI コマンド文字列を受け取り (ANSI の既存のアプリケーションの旧バージョンと互換性のために提供される) 既定値はありません。

3 番目の形式`Open`により、null の場合、型のためにコマンド文字列**int**既定値は NULL です。 呼び出し元に提供されている`Open(session, NULL);`または`Open(session);`型の NULL であるため**int**します。このバージョンが必要ですし、あることをアサート、 **int**パラメーターを NULL にします。

4 番目の形式を使用して、`Open`コマンドを既に作成しているし、1 つを実行する[準備](../../data/oledb/ccommand-prepare.md)と複数回実行します。

> [!NOTE]
>  `Open` 呼び出し`Execute`、この`GetNextResult`します。

## <a name="create"></a> Ccommand::create

呼び出し[ccommand::createcommand](../../data/oledb/ccommand-createcommand.md)指定したセッションのコマンドを作成するを呼び出して[icommandtext::setcommandtext](/previous-versions/windows/desktop/ms709825(v=vs.85))コマンド テキストを指定します。

### <a name="syntax"></a>構文

```cpp
HRESULT CCommandBase::Create(const CSession& session,
   LPCWSTR wszCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();

HRESULT CCommandBase::Create(const CSession& session,
   LPCSTR szCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();
```

#### <a name="parameters"></a>パラメーター

*session*<br/>
[in]コマンドを作成するセッションです。

*wszCommand*<br/>
[in]コマンド文字列の Unicode テキストへのポインター。

*szCommand*<br/>
[in]コマンド文字列の ANSI テキストへのポインター。

*guidCommand*<br/>
[in]コマンド テキストを解析中に、構文と使用するプロバイダーの一般的な規則を指定する GUID。 言語については、次を参照してください。 [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

最初のフォーム`Create`Unicode コマンド文字列を受け取ります。 2 番目の形式の`Create`(ANSI の既存のアプリケーションの旧バージョンと互換性のための提供)、ANSI コマンド文字列を取得します。

## <a name="createcommand"></a> CCommand::CreateCommand

新しいコマンドを作成します。

### <a name="syntax"></a>構文

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>パラメーター

*session*<br/>
[in]A`CSession`新しいコマンドに関連するオブジェクト。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

このメソッドは、指定したセッション オブジェクトを使用してコマンドを作成します。

## <a name="getparameterinfo"></a> CCommand::GetParameterInfo

コマンドのパラメーター、その名前とその型の一覧を取得します。

### <a name="syntax"></a>構文

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>パラメーター

参照してください[icommandwithparameters::getparameterinfo](/previous-versions/windows/desktop/ms714917(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="prepare"></a> Ccommand::prepare

検証し、現在のコマンドを最適化します。

### <a name="syntax"></a>構文

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>パラメーター

*cExpectedRuns*<br/>
[in]コマンドを実行する回数。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

このメソッドは、OLE DB メソッドをラップします。 [icommandprepare::prepare](/previous-versions/windows/desktop/ms718370(v=vs.85))します。

## <a name="releasecommand"></a> CCommand::ReleaseCommand

パラメーターのアクセサーを解放し、コマンド自体を解放します。

### <a name="syntax"></a>構文

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Remarks

`ReleaseCommand` 組み合わせて使用が`Close`します。 参照してください[閉じる](../../data/oledb/ccommand-close.md)使用方法の詳細。

## <a name="setparameterinfo"></a> CCommand::SetParameterInfo

各コマンドのパラメーターのネイティブな型を指定します。

### <a name="syntax"></a>構文

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>パラメーター

参照してください[icommandwithparameters::setparameterinfo](/previous-versions/windows/desktop/ms725393(v=vs.85))で、 *OLE DB プログラマーズ リファレンス*します。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

## <a name="unprepare"></a> Ccommand::unprepare

現在のコマンドの実行プランを破棄します。

### <a name="syntax"></a>構文

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

このメソッドは、OLE DB メソッドをラップします。 [ICommandPrepare::Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85))します。

## <a name="see-also"></a>関連項目

[OLE DB コンシューマー テンプレート](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB コンシューマー テンプレート リファレンス](../../data/oledb/ole-db-consumer-templates-reference.md)