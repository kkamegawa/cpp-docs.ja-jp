---
title: データ ソース:接続 (ODBC)
ms.date: 11/04/2016
helpviewer_keywords:
- ODBC data sources [C++], multiuser environments
- generalizing connection strings
- ODBC [C++], disconnecting from data sources
- connection strings [C++], generalizing
- database connections [C++], creating
- GetDefaultConnect method
- connections [C++], data source
- ODBC connections [C++], configuring
- disconnecting from data sources
- databases [C++], connecting to
- ODBC connections [C++], disconnecting
- data sources [C++], connecting to
- ODBC connections [C++], connecting to data source
- ODBC data sources [C++], connections
- database connections [C++], MFC ODBC classes
ms.assetid: c0adbcdd-c000-40c6-b199-09ffdc7b6ef2
ms.openlocfilehash: 5b646ca0eb86d3addabaad59ca23f56cfe914114
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395951"
---
# <a name="data-source-managing-connections-odbc"></a>データ ソース:接続 (ODBC)

このトピックの内容は、MFC ODBC クラスに該当します。

このトピックでは、次の内容について説明します。

- [データ ソースを構成する方法](#_core_configuring_a_data_source)します。

- [データ ソースおよびそのレコード セットのマルチ ユーザー環境の影響](#_core_working_in_a_multiuser_environment)します。

- [データ ソースへの接続文字列の汎用](#_core_generalizing_the_connection_string)します。

- [データ ソースに接続する方法](#_core_connecting_to_a_specific_data_source)します。

- [データ ソースから切断する方法](#_core_disconnecting_from_a_data_source)します。

- [CDatabase オブジェクトを再利用する方法](#_core_reusing_a_cdatabase_object)します。

データ ソースとの接続とは、データにアクセスするために DBMS との通信を確立することです。 ODBC ドライバーを通じてデータ ソースと接続すると、データ ソースの位置がローカルでもネットワークでも、自動的に接続されます。

ODBC ドライバーがあるデータ ソースならば、どのデータ ソースにでも接続できます。 アプリケーションのユーザーも、同じ ODBC ドライバーを持つ必要があります。 ODBC ドライバーの再配布の詳細については、次を参照してください。[の配布の ODBC コンポーネントの再配布](../../data/odbc/redistributing-odbc-components-to-your-customers.md)します。

##  <a name="_core_configuring_a_data_source"></a> データ ソースを構成します。

データ ソースの設定は、ODBC データ ソース アドミニストレーターを使って行います。 データ ソースの追加や削除も行うことができます。 アプリケーションを作成する際には、ODBC データ ソース アドミニストレーターを使用してデータ ソースを追加するようにアプリケーションのユーザーに指示するか、アプリケーション内で ODBC インストール呼び出しを直接行って ODBC データ ソース アドミニストレーターの機能を組み込むことができます。 詳細については、次を参照してください。 [ODBC アドミニストレーター](../../data/odbc/odbc-administrator.md)します。

データ ソースとして Excel ファイルを使用してが登録されに表示されるように、ファイルを構成する必要があります、**データ ソースの選択** ダイアログ ボックス。

#### <a name="to-use-an-excel-file-as-a-data-source"></a>Excel のファイルをデータ ソースとして使うには

1. ODBC データ ソース アドミニストレーターを使ってファイルを設定します。

1. **ファイル DSN** ] タブで [**追加**します。

1. **データ ソースの新規作成** ダイアログ ボックスでは、Excel ドライバーを選択し、クリックして**次**。

1. クリックして**参照**、データ ソースとして使用するファイルの名前を選択します。

> [!NOTE]
>  選択する必要があります**すべてのファイル**.xls ファイルを表示するドロップダウン メニュー。

1. **[次へ]** をクリックし、 **[完了]** をクリックします。

1. **ODBC Microsoft Excel Setup**  ダイアログ ボックスで、データベースのバージョンとブックを選択します。

##  <a name="_core_working_in_a_multiuser_environment"></a> マルチ ユーザー環境での作業

複数のユーザーが同じデータ ソースにアクセスする場合は、自分がアクセスしているレコードセットのデータが、ほかのユーザーによって変更されてしまうおそれがあります。 同じように、自分が他のユーザーのレコードセットを変更してしまう場合もあります。 詳細については、次を参照してください。[レコード セット。レコード セットの更新プログラムによる (ODBC) の記録](../../data/odbc/recordset-how-recordsets-update-records-odbc.md)と[トランザクション (ODBC)](../../data/odbc/transaction-odbc.md)します。

##  <a name="_core_generalizing_the_connection_string"></a> 接続文字列を汎用化します。

ウィザードは、既定の接続文字列を使ってデータ ソースとの接続を行います。 アプリケーションの開発時には、この接続を使ってテーブルや列を表示できます。 しかし、この既定の接続文字列は、アプリケーションのユーザーがデータ ソースに接続する際に適切ではない場合もあります。 たとえば、実際に使われるデータ ソースおよびその位置を表すパスは、開発時とは異なる場合があります。 その場合を再実装する必要があります、 [:getdefaultconnect](../../mfc/reference/crecordset-class.md#getdefaultconnect)メンバーより汎用的な方法で機能し、ウィザード実装を破棄します。 たとえば、次のような方法があります。

- ODBC データ ソース アドミニストレーターを使って接続文字列の登録、管理を行います。

- 接続文字列を編集し、データ ソース名を削除します。 フレームワークによって、データ ソース名として ODBC が指定され、実行時には、ODBC では、データ ソース名などの必要な接続情報の入力を求めるダイアログ ボックスが表示されます。

- データ ソース名だけを指定します。 ODBC は、必要に応じて、ユーザー ID とパスワードの入力を求めます。 たとえば、元の接続文字列が次のようになっているとします。

    ```cpp
    CString CApp1Set::GetDefaultConnect()
    {
       return "ODBC;DSN=afx;Trusted_Connection=Yes;";
    }
    ```

   この接続文字列には、Windows NT 統合セキュリティを使用する、信頼関係接続を指定します。 セキュリティ上の重大な弱点が生成されるため、パスワードのハードコーディングや空白のパスワードの指定は避けてください。 その代わりに、`GetDefaultConnect` に新しい接続文字列を指定して、ユーザー ID とパスワードの問い合わせができます。

    ```cpp
    // User must select data source and supply user ID and password:
        return "ODBC;";
    // User ID and password required:
        return "ODBC;DSN=mydb;";
    // Password required (myuserid must be replaced with a valid user ID):
        return "ODBC;DSN=mydb;UID=myuserid;";
    // Hard-coded user ID and password (SECURITY WEAKNESS--AVOID):
        return "ODBC;DSN=mydb;UID=sa;PWD=777;";
    ```

##  <a name="_core_connecting_to_a_specific_data_source"></a> 特定のデータ ソースへの接続

特定のデータ ソースに接続する場合、データ ソース必要があります既にで構成されている[ODBC アドミニストレーター](../../data/odbc/odbc-administrator.md)します。

#### <a name="to-connect-to-a-specific-data-source"></a>データ ソースに接続するには

1. `CDatabase` オブジェクトを構築します。

1. 呼び出すその`OpenEx`または`Open`メンバー関数。

ウィザードを使用して指定されている以外のものである場合は、データ ソースを指定する方法の詳細については、次を参照してください[cdatabase::openex](../../mfc/reference/cdatabase-class.md#openex)または[cdatabase::open](../../mfc/reference/cdatabase-class.md#open)で、 *MFC。参照*します。

##  <a name="_core_disconnecting_from_a_data_source"></a> データ ソースからの切断

呼び出しの前に、開いているレコード セットを閉じる必要があります、`Close`のメンバー関数`CDatabase`します。 関連付けられているレコード セットでは、`CDatabase`オブジェクトを終了する場合に、保留中の`AddNew`または`Edit`ステートメントはキャンセルされ、保留中のトランザクションがすべてロールバックされます。

#### <a name="to-disconnect-from-a-data-source"></a>データ ソースとの接続を終了するには

1. 呼び出す、`CDatabase`オブジェクトの[閉じる](../../mfc/reference/cdatabase-class.md#close)メンバー関数。

1. 再利用しない場合にはオブジェクトを破棄します。

##  <a name="_core_reusing_a_cdatabase_object"></a> CDatabase オブジェクトを再利用

接続を終了した後で `CDatabase`オブジェクトを再利用できます。再利用時の接続先は、同じデータ ソースでも別のデータ ソースでもかまいません。

#### <a name="to-reuse-a-cdatabase-object"></a>CDatabase オブジェクトを再利用するには

1. オブジェクトの元の接続を閉じます。

1. 呼び出すオブジェクトを破棄せずに、その`OpenEx`または`Open`メンバー関数をもう一度です。

## <a name="see-also"></a>関連項目

[データ ソース (ODBC)](../../data/odbc/data-source-odbc.md)<br/>
[データ ソース: データ ソースのスキーマの判定 (ODBC)](../../data/odbc/data-source-determining-the-schema-of-the-data-source-odbc.md)<br/>
[CRecordset クラス](../../mfc/reference/crecordset-class.md)