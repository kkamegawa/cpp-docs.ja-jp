---
title: CDaoException クラス
ms.date: 09/17/2019
f1_keywords:
- CDaoException
- AFXDAO/CDaoException
- AFXDAO/CDaoException::CDaoException
- AFXDAO/CDaoException::GetErrorCount
- AFXDAO/CDaoException::GetErrorInfo
- AFXDAO/CDaoException::m_nAfxDaoError
- AFXDAO/CDaoException::m_pErrorInfo
- AFXDAO/CDaoException::m_scode
helpviewer_keywords:
- CDaoException [MFC], CDaoException
- CDaoException [MFC], GetErrorCount
- CDaoException [MFC], GetErrorInfo
- CDaoException [MFC], m_nAfxDaoError
- CDaoException [MFC], m_pErrorInfo
- CDaoException [MFC], m_scode
ms.assetid: b2b01fa9-7ce2-42a1-842e-40f13dc50da4
ms.openlocfilehash: 92105bfb094f50f3077fcf2c1fc221c43015c4d2
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303826"
---
# <a name="cdaoexception-class"></a>CDaoException クラス

データ アクセス オブジェクト (DAO: Data Accsess Object) を基にした MFC データベース クラスから発生する例外条件を表します。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

## <a name="syntax"></a>構文

```
class CDaoException : public CException
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[CDaoException::CDaoException](#cdaoexception)|`CDaoException` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[CDaoException::GetErrorCount](#geterrorcount)|データベースエンジンの Errors コレクションに含まれるエラーの数を返します。|
|[CDaoException:: GetErrorInfo](#geterrorinfo)|エラーコレクション内の特定のエラーオブジェクトに関するエラー情報を返します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|[CDaoException:: m_nAfxDaoError](#m_nafxdaoerror)|MFC DAO クラスのエラーの拡張エラーコードを格納します。|
|[CDaoException:: m_pErrorInfo](#m_perrorinfo)|1つの DAO エラーオブジェクトに関する情報を格納する[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)オブジェクトへのポインター。|
|[CDaoException:: m_scode](#m_scode)|エラーに関連付けられている[SCODE](#m_scode)値。|

## <a name="remarks"></a>コメント

クラスには、例外の原因を特定するために使用できるパブリックデータメンバーが含まれています。 `CDaoException` オブジェクトは、DAO データベースクラスのメンバー関数によって構築およびスローされます。

> [!NOTE]
>  DAO データベースクラスは、Open Database Connectivity (ODBC) に基づく MFC データベースクラスとは異なります。 すべての DAO データベースクラス名には、"CDao" プレフィックスが付いています。 DAO クラスを使用して ODBC データソースにアクセスすることもできます。 一般に、DAO に基づく MFC クラスは、ODBC に基づく MFC クラスよりも多くの機能を備えています。DAO ベースのクラスは、独自のデータベースエンジンを介して、ODBC ドライバーを介してデータにアクセスできます。 DAO ベースのクラスでは、データ定義言語 (DDL) 操作 (クラスを使用したテーブルの追加など) もサポートされています。 DAO を直接呼び出す必要はありません。 ODBC クラスによってスローされる例外の詳細については、「 [CDBException](../../mfc/reference/cdbexception-class.md)」を参照してください。

例外オブジェクトには、 [CATCH](../../mfc/reference/exception-processing.md#catch)式のスコープ内でアクセスできます。 [AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)グローバル関数を使用して、独自のコードから `CDaoException` オブジェクトをスローすることもできます。

MFC では、すべての DAO エラーは `CDaoException`型の例外として表されます。 この型の例外をキャッチした場合、`CDaoException` メンバー関数を使用して、データベースエンジンの Errors コレクションに格納されている DAO エラーオブジェクトから情報を取得できます。 各エラーが発生すると、エラーコレクションに1つまたは複数のエラーオブジェクトが配置されます。 (通常、コレクションには1つのエラーオブジェクトしか含まれていません。 ODBC データソースを使用している場合は、複数のエラーオブジェクトを取得する可能性が高くなります)。別の DAO 操作によってエラーが生成されると、Errors コレクションがクリアされ、新しい error オブジェクトが Errors コレクションに配置されます。 エラーを生成しない DAO 操作は、Errors コレクションには影響しません。

DAO エラーコードについては、ファイル DAOERR を参照してください。始め. 関連情報については、DAO ヘルプの「トラップ可能なデータアクセスエラー」を参照してください。

一般的な例外処理、または `CDaoException` オブジェクトの詳細については、「[例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md) 」および「[例外: データベース例外](../../mfc/exceptions-database-exceptions.md)」を参照してください。 2番目の記事には、DAO での例外処理を示すコード例が含まれています。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDaoException`

## <a name="requirements"></a>要件

**ヘッダー:** afxdao

##  <a name="cdaoexception"></a>CDaoException::CDaoException

`CDaoException` オブジェクトを構築します。

```
CDaoException();
```

### <a name="remarks"></a>コメント

通常、フレームワークは、コードが例外をスローしたときに例外オブジェクトを作成します。 例外オブジェクトを明示的に作成する必要はほとんどありません。 独自のコードから `CDaoException` をスローする場合は、グローバル関数[AfxThrowDaoException](../../mfc/reference/exception-processing.md#afxthrowdaoexception)を呼び出します。

ただし、MFC クラスによってカプセル化された DAO インターフェイスポインターを使用して DAO を直接呼び出す場合は、例外オブジェクトを明示的に作成することもできます。 その場合は、DAO からエラー情報を取得する必要があります。 ワークスペースの Databases コレクションに対して DAODatabases インターフェイスを介して DAO メソッドを呼び出したときに、DAO でエラーが発生したとします。

##### <a name="to-retrieve-the-dao-error-information"></a>DAO エラー情報を取得するには

1. `CDaoException` オブジェクトを構築します。

1. 例外オブジェクトの[GetErrorCount](#geterrorcount)メンバー関数を呼び出して、データベースエンジンの Errors コレクションに含まれるエラーオブジェクトの数を確認します。 (通常は1つだけです。 ODBC データソースを使用している場合を除きます)。

1. 例外オブジェクトの[GetErrorInfo](#geterrorinfo)メンバー関数を呼び出して、例外オブジェクトを介して、コレクション内のインデックスを使用して、一度に1つの特定のエラーオブジェクトを取得します。 例外オブジェクトは、1つの DAO エラーオブジェクトのプロキシとして考えてください。

1. [M_pErrorInfo](#m_perrorinfo)データメンバーで `GetErrorInfo` 返される現在の[CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)構造体を調べます。 そのメンバーは、DAO エラーに関する情報を提供します。

1. ODBC データソースの場合は、さらに多くのエラーオブジェクトについて、必要に応じて手順 3. と 4. を繰り返します。

1. ヒープに例外オブジェクトを構築した場合は、終了時に**delete**演算子を使用して削除します。

MFC DAO クラスでのエラー処理の詳細については、「[例外: データベース例外](../../mfc/exceptions-database-exceptions.md)」を参照してください。

##  <a name="geterrorcount"></a>CDaoException::GetErrorCount

データベースエンジンの Errors コレクションに含まれる DAO エラーオブジェクトの数を取得するには、このメンバー関数を呼び出します。

```
short GetErrorCount();
```

### <a name="return-value"></a>戻り値

データベースエンジンの Errors コレクションに含まれる DAO エラーオブジェクトの数です。

### <a name="remarks"></a>コメント

この情報は、エラーコレクションをループ処理して、コレクション内の1つ以上の DAO エラーオブジェクトを取得するのに役立ちます。 エラーオブジェクトをインデックスまたは DAO エラー番号で取得するには、 [GetErrorInfo](#geterrorinfo)メンバー関数を呼び出します。

> [!NOTE]
>  通常、Errors コレクションには、エラーオブジェクトが1つだけあります。 ただし、ODBC データソースを操作している場合は、複数存在する可能性があります。

##  <a name="geterrorinfo"></a>CDaoException:: GetErrorInfo

エラーコレクション内の特定のエラーオブジェクトに関するエラー情報を返します。

```
void GetErrorInfo(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
インデックスによる検索のための、データベースエンジンの Errors コレクション内のエラー情報のインデックスです。

### <a name="remarks"></a>コメント

このメンバー関数を呼び出して、例外に関する次の種類の情報を取得します。

- エラー コード

- ソース

- 説明

- ヘルプ ファイル

- ヘルプコンテキスト

`GetErrorInfo` は、例外オブジェクトの `m_pErrorInfo` データメンバーに情報を格納します。 返される情報の簡単な説明については、「 [m_pErrorInfo](#m_perrorinfo)」を参照してください。 MFC によってスローさ `CDaoException` 型の例外をキャッチした場合、`m_pErrorInfo` メンバーは既に入力されています。 DAO を直接呼び出すことを選択した場合は、例外オブジェクトの `GetErrorInfo` メンバー関数を呼び出して `m_pErrorInfo`を埋める必要があります。 詳細については、 [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)構造体を参照してください。

DAO の例外とコード例の詳細については、「[例外: データベースの例外](../../mfc/exceptions-database-exceptions.md)」を参照してください。

##  <a name="m_nafxdaoerror"></a>CDaoException:: m_nAfxDaoError

MFC の拡張エラーコードを格納します。

### <a name="remarks"></a>コメント

このコードは、MFC DAO クラスの特定のコンポーネントに誤りがある場合に提供されます。

指定できる値は次のとおりです。

- NO_AFX_DAO_ERROR 最新の操作では、MFC の拡張エラーは発生しませんでした。 ただし、操作によって DAO または OLE から他のエラーが生成された可能性があるため、 [m_pErrorInfo](#m_perrorinfo)を確認し、場合によっては[m_scode](#m_scode)する必要があります。

- AFX_DAO_ERROR_ENGINE_INITIALIZATION MFC は Microsoft Jet データベースエンジンを初期化できませんでした。 OLE の初期化に失敗したか、DAO データベースエンジンオブジェクトのインスタンスを作成できなかった可能性があります。 これらの問題は、通常、DAO または OLE の不適切なインストールを提案します。

- DAO レコードフィールドエクスチェンジ (DFX) 関数呼び出しで使用されているアドレスが存在しないか、無効です (アドレスはデータをバインドするために使用されませんでした)。 AFX_DAO_ERROR_DFX_BIND DFX 呼び出しで間違ったアドレスが渡されたか、または DFX 操作の間にアドレスが無効になった可能性があります。

- クエリを実行しようとしたが、オープン状態ではない tabledef オブジェクトまたは tabledef オブジェクトに基づいてレコードセットを開こうとした AFX_DAO_ERROR_OBJECT_NOT_OPEN。

##  <a name="m_perrorinfo"></a>CDaoException:: m_pErrorInfo

[GetErrorInfo](#geterrorinfo)を呼び出すことによって最後に取得した DAO error オブジェクトに関する情報を提供する `CDaoErrorInfo` 構造体へのポインターを格納します。

### <a name="remarks"></a>コメント

このオブジェクトには、次の情報が含まれています。

|CDaoErrorInfo メンバー|情報|意味|
|--------------------------|-----------------|-------------|
|`m_lErrorCode`|エラー コード|DAO エラーコード|
|`m_strSource`|ソース|最初にエラーを生成したオブジェクトまたはアプリケーションの名前|
|`m_strDescription`|説明|エラーに関連付けられている説明文字列|
|`m_strHelpFile`|ヘルプファイル|ユーザーが問題に関する情報を取得できる Windows ヘルプファイルへのパス|
|`m_lHelpContext`|ヘルプコンテキスト|DAO ヘルプファイルのトピックのコンテキスト ID|

`CDaoErrorInfo` オブジェクトに含まれる情報の詳細については、 [CDaoErrorInfo](../../mfc/reference/cdaoerrorinfo-structure.md)構造体を参照してください。

##  <a name="m_scode"></a>CDaoException:: m_scode

エラーを説明する `SCODE` 型の値を格納します。

### <a name="remarks"></a>コメント

これは OLE コードです。 ほとんどの場合、この値を使用する必要はほとんどありません。これは、他の `CDaoException` データメンバーで、より具体的な MFC または DAO のエラー情報を利用できるためです。

SCODE の詳細については、「Windows SDK での[OLE エラーコードの構造](/windows/win32/com/structure-of-com-error-codes)」を参照してください。 SCODE データ型は、HRESULT データ型にマップされます。

## <a name="see-also"></a>参照

[CException クラス](../../mfc/reference/cexception-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CException クラス](../../mfc/reference/cexception-class.md)
