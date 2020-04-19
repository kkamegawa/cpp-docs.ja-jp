---
title: TN042:ODBC ドライバーの開発に関する推奨事項
ms.date: 11/04/2016
f1_keywords:
- vc.odbc
helpviewer_keywords:
- ODBC drivers [MFC], writing
- databases [MFC], ODBC
- TN042
ms.assetid: ecc6b5d9-f480-4582-9e22-8309fe561dad
ms.openlocfilehash: 462f8229d995add79f48f34b7f81257710b4a8b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305412"
---
# <a name="tn042-odbc-driver-developer-recommendations"></a>TN042:ODBC ドライバーの開発に関する推奨事項

> [!NOTE]
>  次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

このノートでは、ODBC ドライバー作成者のガイドラインについて説明します。 これは、一般的な要件と MFC データベース クラスを使用する、ODBC の機能と予想されるセマンティックのさまざまな詳細の前提条件について説明します。 3 つをサポートするために、ドライバーの機能に必要な`CRecordset`モードを開きます (**forwardonly です**、**スナップショット**と**ダイナセット**) については説明します。

## <a name="odbcs-cursor-library"></a>ODBC のカーソル ライブラリ

MFC データベース クラスでは、多くの場合ほとんどレベル 1 の ODBC ドライバーによって提供される機能値上限を超えることをユーザーに機能を提示します。 幸いにも、ODBC のカーソル ライブラリがそれ自体のデータベース クラスと、ドライバーのレイヤーし、この追加機能の多くが自動的に提供します。

たとえば、1.0 のほとんどのドライバーでは、旧バージョンとスクロールはできません。 カーソル ライブラリからこれを検出できますと、ドライバーからの行をキャッシュは、しで FETCH_PREV 呼び出しの要求を提示`SQLExtendedFetch`します。

カーソル ライブラリのもう 1 つの重要な例では、位置指定更新です。 1.0 のほとんどのドライバーも位置指定更新ではありませんが、カーソル ライブラリの現在のキャッシュされたデータ値、またはキャッシュされたタイムスタンプ値に基づくデータ ソースで対象の行を識別する update ステートメントが生成されます。

クラス ライブラリの複数の行セットを利用しません。 いくつかそのため、`SQLSetPos`ステートメントは常に、行セットの最初の行に適用します。

## <a name="cdatabases"></a>CDatabases

各`CDatabase`、1 つ割り当てます**HDBC**します。 (場合`CDatabase`の`ExecuteSQL`関数を使用すると、 **HSTMT**が一時的に割り当てられます)。複数の場合は、その`CDatabase`の必要な複数**HDBC**あたり秒**HENV**サポートする必要があります。

データベース クラスには、カーソル ライブラリが必要です。 これに反映されますを`SQLSetConnections`呼び出す**SQL_ODBC_CURSORS**、 **SQL_CUR_USE_ODBC**します。

`SQLDriverConnect`、 **SQL_DRIVER_COMPLETE**を使って`CDatabase::Open`をデータ ソースへの接続を確立します。

ドライバーをサポートする必要があります`SQLGetInfo SQL_ODBC_API_CONFORMANCE`  >=  **SQL_OAC_LEVEL1**、 `SQLGetInfo SQL_ODBC_SQL_CONFORMANCE`  >=  **SQL_OSC_MINIMUM**します。

トランザクションをサポートするために、`CDatabase`とその依存のレコード セット`SQLGetInfo SQL_CURSOR_COMMIT_BEHAVIOR`と**SQL_CURSOR_ROLLBACK_BEHAVIOR**必要があります**SQL_CR_PRESERVE**します。 それ以外の場合、トランザクション管理を実行する試行は無視されます。

`SQLGetInfo SQL_DATA_SOURCE_READ_ONLY` サポートする必要があります。 "Y"が返された場合は、データ ソースの更新操作は実行されません。

場合、`CDatabase`が開かれる読み取り専用、読み取り、データ ソースを設定しようとすると、のみになりますで`SQLSetConnectOption SQL_ACCESS_MODE`、 **SQL_MODE_READ_ONLY**します。

この情報がドライバーから返される識別子では、引用符で囲む必要がある場合、`SQLGetInfo SQL_IDENTIFIER_QUOTE_CHAR`呼び出します。

デバッグのため、`SQLGetInfo SQL_DBMS_VER`と**SQL_DBMS_NAME**ドライバーから取得されます。

`SQLSetStmtOption SQL_QUERY_TIMEOUT` **SQL_ASYNC_ENABLE**で呼び出すことができます、`CDatabase`の**HDBC**します。

`SQLError` いずれかまたはすべての引数 NULL で呼び出すことができます。

もちろん、 `SQLAllocEnv`、 `SQLAllocConnect`、`SQLDisconnect`と`SQLFreeConnect`サポートする必要があります。

## <a name="executesql"></a>ExecuteSQL

割り当てと解放、一時的なだけでなく**HSTMT**、`ExecuteSQL`呼び出し`SQLExecDirect`、 `SQLFetch`、`SQLNumResultCol`と`SQLMoreResults`します。 `SQLCancel` 呼び出すことができます、 **HSTMT**します。

## <a name="getdatabasename"></a>GetDatabaseName

`SQLGetInfo SQL_DATABASE_NAME` 呼び出されます。

## <a name="begintrans-committrans-rollback"></a>BeginTrans、CommitTrans、ロールバック

`SQLSetConnectOption SQL_AUTOCOMMIT` `SQLTransact SQL_COMMIT`、 **SQL_ROLLBACK**と**SQL_AUTOCOMMIT**がトランザクション要求が行われた場合に呼び出されます。

## <a name="crecordsets"></a>CRecordsets

`SQLAllocStmt`、 `SQLPrepare`、 `SQLExecute` (の`Open`と`Requery`)、 `SQLExecDirect` (操作)、更新プログラムの`SQLFreeStmt`サポートする必要があります。 `SQLNumResultCols` `SQLDescribeCol`は結果セットのさまざまな時点で呼び出されます。

`SQLSetParam` パラメーターのデータ バインドは広く使用と**DATA_AT_EXEC**機能します。

`SQLBindCol` 登録に幅広く使用 odbc 列のデータ記憶域の場所を出力します。

2 つ`SQLGetData`呼び出しを使用して取得**SQL_LONG_VARCHAR**と**SQL_LONG_VARBINARY**データ。 最初の呼び出しが、呼び出すことによって、列の値の合計の長さを検索しようとしています。 `SQLGetData` cbMaxValue 0 ではなく、有効な pcbValue します。 PcbValue 保持している場合**SQL_NO_TOTAL**例外がスローされます。 それ以外の場合、 **HGLOBAL**は、割り当て済み別および`SQLGetData`呼び出し全体の結果を取得します。

## <a name="updating"></a>Updating

排他ロックが要求された場合`SQLGetInfo SQL_LOCK_TYPES`は照会されます。 場合**SQL_LCK_EXCLUSIVE**はサポートされていない例外がスローされます。

更新しようとしています、 `CRecordset` (**スナップショット**または**ダイナセット**) により、1 秒あたり**HSTMT**割り当てられます。 サポートしていないドライバーの 2 つ目の**HSTMT**、カーソル ライブラリはこの機能をシミュレートします。 残念ながら、この場合もあります可能性が最初に、現在のクエリを強制**HSTMT** 、2 つ目を処理する前に完了するまで**HSTMT**の要求。

`SQLFreeStmt SQL_CLOSE` **SQL_RESET_PARAMS**と`SQLGetCursorName`が更新操作中に呼び出されます。

ある場合**CLongBinarys**で、 **outputColumns**、ODBC の**DATA_AT_EXEC**機能をサポートする必要があります。 これは、返すことが含まれています。 **SQL_NEED_DATA**から`SQLExecDirect`、`SQLParamData`と`SQLPutData`します。

`SQLRowCount` によって、1 レコードのみが更新されたことを確認する実行後に呼び出されますが、`SQLExecDirect`します。

## <a name="forwardonly-cursors"></a>前方向カーソル

のみ`SQLFetch`に必要な`Move`操作。 なお**forwardonly です**カーソルは更新プログラムをサポートしていません。

## <a name="snapshot-cursors"></a>スナップショット カーソル

スナップショット機能が必要です`SQLExtendedFetch`をサポートします。 前述のように、ドライバーがサポートされていないときに ODBC カーソル ライブラリは検出`SQLExtendedFetch`、自体に必要なサポートを提供します。

`SQLGetInfo`、 **SQL_SCROLL_OPTIONS**をサポートする必要があります**SQL_SO_STATIC**します。

## <a name="dynaset-cursors"></a>ダイナセットのカーソル

ダイナセットを開くために必要な最小のサポートを次に示します。

`SQLGetInfo`、 **SQL_ODBC_VER**返す必要があります >「01」です。

`SQLGetInfo`、 **SQL_SCROLL_OPTIONS**をサポートする必要があります**SQL_SO_KEYSET_DRIVEN**します。

`SQLGetInfo`、 **SQL_ROW_UPDATES** "Y"を返す必要があります。

`SQLGetInfo`、 **SQL_POSITIONED_UPDATES**をサポートする必要があります**SQL_PS_POSITIONED_DELETE**と**SQL_PS_POSITIONED_UPDATE**します。

さらに、排他ロックが要求された場合に呼び出し`SQLSetPos`irow 1、FALSE fRefresh 群れと**SQL_LCK_EXCLUSIVE**になります。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
