---
title: CDBException クラス
ms.date: 11/04/2016
f1_keywords:
- CDBException
- AFXDB/CDBException
- AFXDB/CDBException::m_nRetCode
- AFXDB/CDBException::m_strError
- AFXDB/CDBException::m_strStateNativeOrigin
helpviewer_keywords:
- CDBException [MFC], m_nRetCode
- CDBException [MFC], m_strError
- CDBException [MFC], m_strStateNativeOrigin
ms.assetid: eb9e1119-89f5-49a7-b9d4-b91cee1ccc82
ms.openlocfilehash: bdfb9bd0b45fd241de4378a2caa19e7dd9f9bdf2
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877488"
---
# <a name="cdbexception-class"></a>CDBException クラス

データベース クラスから発生する例外状態を表現します。

## <a name="syntax"></a>構文

```
class CDBException : public CException
```

## <a name="members"></a>メンバー

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDBException::m_nRetCode](#m_nretcode)|型へのオープン データベース コネクティビティ (ODBC) 戻りコードが格納されます。|
|[CDBException::m_strError](#m_strerror)|英数字の用語ではエラーを説明する文字列が含まれています。|
|[CDBException::m_strStateNativeOrigin](#m_strstatenativeorigin)|ODBC が返すエラー コードの観点からエラーを説明する文字列が含まれています。|

## <a name="remarks"></a>Remarks

クラスには、例外の原因を特定する、または例外を説明するテキスト メッセージを表示するに使用できる 2 つのパブリック データ メンバーが含まれています。 `CDBException` オブジェクトが構築され、データベース クラスのメンバー関数によってスローされます。

> [!NOTE]
>  このクラスは、MFC の Open Database Connectivity (ODBC) クラスのいずれかです。 代わりに新しいデータ アクセス オブジェクト (DAO) クラスを使用している場合は、使用[CDaoException](../../mfc/reference/cdaoexception-class.md)代わりにします。 DAO クラスの名前では、プレフィックスとして"CDao"があります。 詳細については、この記事を参照してください。[概要。データベース プログラミング](../../data/data-access-programming-mfc-atl.md)します。

例外は、プログラムのコントロールのデータ ソースなどの外部の条件に関連する異常な実行の場合またはネットワーク I/O エラー。 通常、プログラムを実行するを参照してくださいに考えられるエラーは通常、例外考慮されません。

これらのオブジェクトのスコープ内にアクセスすることができます、**キャッチ**式。 スローすることもできます`CDBException`で独自のコードからのオブジェクト、`AfxThrowDBException`グローバル関数。

[全般]、またはについての例外処理の詳細については`CDBException`オブジェクトは、記事をご覧ください[例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md)と[例外。データベース例外](../../mfc/exceptions-database-exceptions.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CDBException`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxdb.h

##  <a name="m_nretcode"></a>  CDBException::m_nRetCode

型を ODBC アプリケーション プログラミング インターフェイス (API) 関数によって返される RETCODE の ODBC エラー コードが含まれています。

### <a name="remarks"></a>Remarks

この型には、ODBC で定義されている SQL プレフィックス付きのコードとデータベース クラスで定義されている AFX_SQL から始まるコードが含まれています。 `CDBException`、このメンバーには、次の値のいずれかが含まれます。

- AFX_SQL_ERROR_API_CONFORMANCE ドライバーの`CDatabase::OpenEx`または`CDatabase::Open`呼び出しが必要な ODBC API への準拠レベル 1 (SQL_OAC_LEVEL1) に準拠していません。

- データ ソースへの接続を AFX_SQL_ERROR_CONNECT_FAIL が失敗しました。 NULL が渡される`CDatabase`、レコード セットのコンス トラクターと接続を作成する後続の試行へのポインターがに基づいて`GetDefaultConnect`できませんでした。

- 記憶域を提供するよりも多くのデータを要求 AFX_SQL_ERROR_DATA_TRUNCATED したとします。 指定されたデータ ストレージを増やす方法について`CString`または`CByteArray`、データ型を参照してください、`nMaxLength`引数[RFX_Text](record-field-exchange-functions.md#rfx_text)と[RFX_Binary](record-field-exchange-functions.md#rfx_binary) "マクロとグローバル変数。"

- AFX_SQL_ERROR_DYNASET_NOT_SUPPORTED A 呼び出し`CRecordset::Open`ダイナセットの要求に失敗しました。 ダイナセットを使う場合は、ドライバーによってサポートされていません。

- テーブルを開こうとした AFX_SQL_ERROR_EMPTY_COLUMN_LIST (または指定した識別できなかったプロシージャ呼び出しとしてまたは**選択**ステートメント) のレコード フィールド エクス (チェンジ RFX) 関数の呼び出しで識別される列がありません`DoFieldExchange`をオーバーライドします。

- AFX_SQL_ERROR_FIELD_SCHEMA_MISMATCH、rfx 関数の種類の関数で、`DoFieldExchange`オーバーライドは、レコード セット内の列のデータ型と互換性がありません。

- AFX_SQL_ERROR_ILLEGAL_MODE するという`CRecordset::Update`以前を呼び出さずに`CRecordset::AddNew`または`CRecordset::Edit`します。

- ODBC ドライバーは、ロックをサポートしていないために、AFX_SQL_ERROR_LOCK_MODE_NOT_SUPPORTED への更新用のレコードのロック要求を完了できませんでした。

- AFX_SQL_ERROR_MULTIPLE_ROWS_AFFECTED するという`CRecordset::Update`または`Delete`ない一意のキーを持つテーブルの複数のレコードを変更します。

- 編集または削除の前に削除されたレコード AFX_SQL_ERROR_NO_CURRENT_RECORD を試みました。 削除した後に、新しい現在のレコードをスクロールする必要があります。

- 位置指定更新を AFX_SQL_ERROR_NO_POSITIONED_UPDATES ODBC ドライバーがサポートされていないために、ダイナセットの要求を完了できませんでした。

- AFX_SQL_ERROR_NO_ROWS_AFFECTED するという`CRecordset::Update`または`Delete`が、レコードが見つからなくなった操作を開始したとき。

- AFX_SQL_ERROR_ODBC_LOAD_FAILED、ODBC を読み込もうとしました。DLL が失敗しました。Windows では、見つからなかったか、この DLL を読み込むことができません。 このエラーは致命的です。

- AFX_SQL_ERROR_ODBC_V2_REQUIRED レベル 2 に準拠している ODBC ドライバーが必要になるために、ダイナセットの要求を完了できませんでした。

- データ ソースは後方スクロールをサポートしていないために、AFX_SQL_ERROR_RECORDSET_FORWARD_ONLY スクロールの試行は成功しませんでした。

- AFX_SQL_ERROR_SNAPSHOT_NOT_SUPPORTED A 呼び出し`CRecordset::Open`スナップショットを要求に失敗しました。 スナップショットは、ドライバーによってサポートされていません。 (これにのみ発生時に ODBC カーソル ライブラリ ODBCCURS。DLL が存在しません。)

- AFX_SQL_ERROR_SQL_CONFORMANCE ドライバーの`CDatabase::OpenEx`または`CDatabase::Open`呼び出しが「最小」(SQL_OSC_MINIMUM) の必要な ODBC SQL への準拠レベルを準拠していません。

- 返せない場合、ODBC ドライバーはの合計サイズを指定できますが、`CLongBinary`データ値。 グローバル メモリ ブロックを事前割り当てしないため、この操作は失敗します。

- 読み取り専用レコード セットを更新しようとする AFX_SQL_ERROR_RECORDSET_READONLY またはデータ ソースは読み取り専用です。 レコード セットと更新操作を実行できませんまたは`CDatabase`が関連付けられているオブジェクト。

- SQL_ERROR 関数が失敗しました。 ODBC 関数によって返されるエラー メッセージ`SQLError`に格納されている場合は、`m_strError`データ メンバー。

- SQL_INVALID_HANDLE 関数は、無効な環境ハンドルを接続ハンドルでは、ステートメント ハンドルの理由により失敗しました。 これは、プログラミング エラーを示します。 ODBC 関数から追加情報はありません`SQLError`します。

Sql コードは、ODBC によって定義されます。 AFX プレフィックス付きのコードは、AFXDB で定義されます。H に定義しています。

##  <a name="m_strerror"></a>  CDBException::m_strError

例外の原因となったエラーを説明する文字列が含まれています。

### <a name="remarks"></a>Remarks

文字列では、英数字の用語では、エラーについて説明します。 詳細な情報と例についてを参照してください。`m_strStateNativeOrigin`します。

##  <a name="m_strstatenativeorigin"></a>  CDBException::m_strStateNativeOrigin

例外の原因となったエラーを説明する文字列が含まれています。

### <a name="remarks"></a>Remarks

文字列が、フォーム"の状態: %s、ネイティブ: %ld 配信元: %s"での順序で、書式コードが記述する値を置き換え。

- SQLSTATE、5 文字のエラー コードを含む null で終わる文字列が返される、 *szSqlState* ODBC 関数のパラメーター`SQLError`します。 SQLSTATE 値は、付録 A に記載されて[ODBC エラー コード](/sql/odbc/reference/appendixes/appendix-a-odbc-error-codes)の*ODBC プログラマ リファレンス*します。 例:"S0022"。

- データ ソースに固有のネイティブ エラー コードが返される、 *pfNativeError*のパラメーター、`SQLError`関数。 例:207.

- 返されるエラー メッセージ テキスト、*後*のパラメーター、`SQLError`関数。 このメッセージは、いくつかのかっこで囲まれた名前で構成されます。 エラーは、ユーザーにそのソースから渡された、各 ODBC コンポーネント (データ ソース、ドライバー、ドライバー マネージャー) は、独自の名前を追加します。 この情報は、エラーの原因を特定するのに役立ちます。 例: [Microsoft] [ODBC SQL Server Driver] [SQL Server]

フレームワークは、エラー文字列を解釈し、そのコンポーネントには、`m_strStateNativeOrigin`場合`m_strStateNativeOrigin`情報が含まれています、1 つ以上のエラー、エラーが改行で区切られました。 フレームワークは、英数字のエラー テキストを`m_strError`します。

この文字列を構成するために使用するコードの詳細については、次を参照してください。、 [SQLError](/sql/odbc/reference/syntax/sqlerror-function)で機能、 *ODBC プログラマ リファレンス*します。

### <a name="example"></a>例

ODBC: から"の状態: S0022、ネイティブ: 207、配信元:\[Microsoft]\[ODBC SQL Server Driver]\[SQL Server] 'ColName' の無効な列名"

`m_strStateNativeOrigin`の場合:"の状態: S0022、ネイティブ: 207、配信元:\[Microsoft]\[ODBC SQL Server Driver]\[SQL Server]」

`m_strError`の場合:「無効な列名 'ColName'」

## <a name="see-also"></a>関連項目

[CException クラス](../../mfc/reference/cexception-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDatabase クラス](../../mfc/reference/cdatabase-class.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)<br/>
[CFieldExchange クラス](../../mfc/reference/cfieldexchange-class.md)<br/>
[CRecordset::Update](../../mfc/reference/crecordset-class.md#update)<br/>
[CRecordset::Delete](../../mfc/reference/crecordset-class.md#delete)<br/>
[CException クラス](../../mfc/reference/cexception-class.md)
