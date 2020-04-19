---
title: データベース マクロとデータベース グローバル関数
ms.date: 11/04/2016
f1_keywords:
- AFXDB/AFX_ODBC_CALL
- AFXDB/AFX_SQL_ASYNC
- AFXDB/AFX_SQL_SYNC
- AFXDB/AfxGetHENV
helpviewer_keywords:
- global database functions [MFC]
- database macros [MFC]
- database globals [MFC]
- global functions [MFC], database functions
- macros [MFC], MFC database
ms.assetid: 5b9b9e61-1cf9-4345-9f29-3807dd466488
ms.openlocfilehash: 47a1bb434801c24ab8eee048d9ef8f93793101cc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62323191"
---
# <a name="database-macros-and-globals"></a>データベース マクロとデータベース グローバル関数

マクロとグローバル変数を以下に示すは、ODBC ベースのデータベース アプリケーションに適用されます。 DAO ベースのアプリケーションでは使用されません。

MFC の 4.2、マクロの前に`AFX_SQL_ASYNC`と`AFX_SQL_SYNC`非同期操作の他のプロセスに時間を得ることを指定します。 MFC の 4.2、これらのマクロ、MFC ODBC クラスは、同期操作のみを使用しているために、変更の実装から。 マクロ`AFX_ODBC_CALL`MFC 4.2 に新しく追加されました。

### <a name="database-macros"></a>データベース マクロ

|||
|-|-|
|[AFX_ODBC_CALL](#afx_odbc_call)|返す ODBC API 関数を呼び出す`SQL_STILL_EXECUTING`します。 `AFX_ODBC_CALL` 繰り返し関数を呼び出すまでされなく返します`SQL_STILL_EXECUTING`します。|
|[AFX_SQL_ASYNC](#afx_sql_async)|`AFX_ODBC_CALL`.|
|[AFX_SQL_SYNC](#afx_sql_sync)|返さない ODBC API 関数を呼び出す`SQL_STILL_EXECUTING`します。|

### <a name="database-globals"></a>データベースのグローバル関数

|||
|-|-|
|[AfxDbInitModule](#afxdbinitmodule)|MFC と動的にリンクされるレギュラー MFC DLL のデータベース サポートを追加します。|
|[AfxGetHENV](#afxgethenv)|MFC で使用されている ODBC 環境ハンドルを取得します。 このハンドルは、ODBC の直接の呼び出しで使用できます。|

## <a name="afxdbinitmodule"></a> AfxDbInitModule

MFC データベース (または DAO) は、MFC と動的にリンクされるレギュラー MFC DLL からサポートは、この関数の呼び出しを追加でレギュラー MFC DLL の`CWinApp::InitInstance`MFC を初期化する関数を DLL のデータベースします。

### <a name="syntax"></a>構文

```
void AFXAPI AfxDbInitModule( );
```

### <a name="remarks"></a>Remarks

この呼び出しは、基底クラスに対する呼び出しの前に発生しますまたは、追加のコード、MFC DLL をデータベースにアクセスが確認します。 MFC データベース DLL が MFC 拡張 DLL です。MFC 拡張 DLL にワイヤード (有線) を取得するため、`CDynLinkLibrary`チェーンを作成する必要がありますが、`CDynLinkLibrary`使用するすべてのモジュールのコンテキスト内のオブジェクト。 `AfxDbInitModule` 作成、`CDynLinkLibrary`にワイヤード (有線) を取得するために、レギュラー MFC DLL のコンテキストでオブジェクト、`CDynLinkLibrary`レギュラー MFC DLL のチェーンのオブジェクトします。

### <a name="requirements"></a>必要条件

**ヘッダー:** \<afxdll_.h >

##  <a name="afx_odbc_call"></a>  AFX_ODBC_CALL

このマクロを使用して返す可能性のある任意の ODBC API 関数を呼び出す`SQL_STILL_EXECUTING`します。

```
AFX_ODBC_CALL(SQLFunc)
```

### <a name="parameters"></a>パラメーター

*SQLFunc*<br/>
ODBC API 関数。 ODBC API 関数の詳細については、Windows SDK を参照してください。

### <a name="remarks"></a>Remarks

`AFX_ODBC_CALL` 繰り返しまでの呼び出し関数が不要になった返します`SQL_STILL_EXECUTING`します。

呼び出す前に`AFX_ODBC_CALL`、変数を宣言する必要があります`nRetCode`RETCODE 型。

MFC ODBC クラスのみ同期処理を今すぐ使用のことに注意してください。 非同期操作を実行するには、ODBC API 関数を呼び出す必要があります`SQLSetConnectOption`します。 詳細については、「関数の非同期実行」、Windows sdk のトピックを参照してください。

### <a name="example"></a>例

この例では`AFX_ODBC_CALL`を呼び出す、 `SQLColumns` ODBC API 関数は、によってという名前のテーブル内の列の一覧を返します`strTableName`します。 宣言に注意してください`nRetCode`と関数にパラメーターを渡すレコード セットのデータ メンバーを使用します。 呼び出しの結果を確認しても例`Check`、クラスのメンバー関数`CRecordset`します。 変数`prs`へのポインター、`CRecordset`別の場所で宣言されたオブジェクト。

[!code-cpp[NVC_MFCDatabase#39](../../mfc/codesnippet/cpp/database-macros-and-globals_1.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afxdb.h

##  <a name="afx_sql_async"></a>  AFX_SQL_ASYNC

このマクロを MFC 4.2 で変更の実装です。

```
AFX_SQL_ASYNC(prs, SQLFunc)
```

### <a name="parameters"></a>パラメーター

*プル要求*<br/>
ポインターを`CRecordset`オブジェクトまたは`CDatabase`オブジェクト。 MFC の 4.2 以降では、このパラメーターの値は無視されます。

*SQLFunc*<br/>
ODBC API 関数。 ODBC API 関数の詳細については、Windows SDK を参照してください。

### <a name="remarks"></a>Remarks

`AFX_SQL_ASYNC` マクロを呼び出すだけです[AFX_ODBC_CALL](#afx_odbc_call)を無視し、 *pr*パラメーター。 MFC の 4.2、以前のバージョンで`AFX_SQL_ASYNC`返す可能性のある ODBC API 関数の呼び出しに使用された`SQL_STILL_EXECUTING`します。 ODBC API 関数が返す場合`SQL_STILL_EXECUTING`、し`AFX_SQL_ASYNC`呼び出して`prs->OnWaitForDataSource`します。

> [!NOTE]
>  MFC ODBC クラスは、同期処理を使用するようになりました。 非同期操作を実行するには、ODBC API 関数を呼び出す必要があります`SQLSetConnectOption`します。 詳細については、「関数の非同期実行」、Windows sdk のトピックを参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdb.h

##  <a name="afx_sql_sync"></a>  AFX_SQL_SYNC

`AFX_SQL_SYNC`マクロ、関数を呼び出すだけです`SQLFunc`します。

```
AFX_SQL_SYNC(SQLFunc)
```

### <a name="parameters"></a>パラメーター

*SQLFunc*<br/>
ODBC API 関数。 これらの関数の詳細については、Windows SDK を参照してください。

### <a name="remarks"></a>Remarks

このマクロは返されません ODBC API 関数を呼び出すを使用して`SQL_STILL_EXECUTING`します。

呼び出しの前に`AFX_SQL_SYNC`、変数を宣言する必要があります`nRetCode`RETCODE 型。 値をチェックする`nRetCode`マクロ呼び出しの後にします。

注意の実装`AFX_SQL_SYNC`MFC 4.2 に変更します。 サーバーの状態の確認が必要な不要になったため、`AFX_SQL_SYNC`単に値を割り当てます`nRetCode`します。 呼び出すのではなく、たとえば、

[!code-cpp[NVC_MFCDatabase#40](../../mfc/codesnippet/cpp/database-macros-and-globals_2.cpp)]

割り当てを行うことができますだけです。

[!code-cpp[NVC_MFCDatabase#41](../../mfc/codesnippet/cpp/database-macros-and-globals_3.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdb.h

##  <a name="afxgethenv"></a>  AfxGetHENV

ODBC の直接の呼び出しで返されたハンドルを使用できますが、いないハンドルを閉じるか、ハンドルで既存のすべての後に有効であり、使用可能なが前提としています。 必要があります`CDatabase`- または`CRecordset`の派生オブジェクトが破棄されています。

```
HENV AFXAPI AfxGetHENV();
```

### <a name="return-value"></a>戻り値

MFC で使用されている ODBC 環境ハンドルです。 `SQL_HENV_NULL`がある場合ありません[CDatabase](../../mfc/reference/cdatabase-class.md)オブジェクトと no [CRecordset](../../mfc/reference/crecordset-class.md)使用中のオブジェクト。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdb.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
