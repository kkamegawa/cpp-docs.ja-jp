---
title: 'データ ソース:データ ソース : プログラムにおける ODBC データ ソースの設定'
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: 33269b65835812a6e1a03e091833831781d97b6d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62395932"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>データ ソース:データ ソース : プログラムにおける ODBC データ ソースの設定

このトピックでは、ODBC (Open Database Connectivity) データ ソース名をプログラムで設定する方法について説明します。 この方法を使うと、柔軟なデータ アクセスが可能になり、ユーザーが ODBC データ ソース アドミニストレーターなどのプログラムを使って明示的にデータ ソースを指定する必要もありません。

通常、ユーザーは ODBC データ ソース アドミニストレーターを実行してデータ ソースを作成します。ただし、関連付けられたデータベース管理システム (DBMS: Database Management System) がこの操作をサポートすることが条件です。

ODBC データ ソース アドミニストレーターを使用して Microsoft Access ODBC データ ソースを作成する際には、既存の .mdb ファイルを使用するか、新しい .mdb ファイルを作成するかを選択できます。 MFC ODBC アプリケーションからプログラムを通じて .mdb ファイルを作成する方法はありません。 したがって、データを Microsoft Access データ ソース (.mdb ファイル) に格納する必要があるアプリケーションの場合は、空の .mdb ファイルを用意し、必要に応じて使用またはコピーできるようにします。

しかし、多くの DBMS では、プログラム上でデータ ソースを作成できます。 一部のデータ ソースは、データベースのフォルダー仕様を保持しています。 つまり、フォルダーがデータ ソースであり、データ ソース内の各テーブルは別個のファイルに格納されます。たとえば、dBASE の場合、各テーブルは .dbf ファイルです。 Microsoft Access や SQL Server など他の ODBC データベース ドライバーでは、データ ソースを確立する前に、いくつかの条件を満たす必要があります。 たとえば、SQL Server ODBC ドライバーを使用する場合は、SQL Server コンピューターが確立されている必要があります。

##  <a name="_core_sqlconfigdatasource_example"></a> SQLConfigDataSource の例

次の例では、`::SQLConfigDataSource`新しい Excel データ ソースを作成する ODBC API 関数には新しい Excel データ ソースが呼び出されます。

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

このデータ ソースは、実際はフォルダー (C:\EXCELDIR) です。このフォルダーは存在している必要があります。 Excel ドライバーは、フォルダーをそのデータ ソースとして使用し、ファイルを各テーブル (.xls ファイルごとに 1 テーブル) として使用するからです。

テーブルの作成の詳細については、次を参照してください。[データ ソース。プログラムにおける ODBC データ ソース テーブルの作成](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md)です。

次の情報に渡される必要があるパラメーターの説明、 `::SQLConfigDataSource` ODBC API 関数。 使用する`::SQLConfigDataSource`、Odbcinst.h ヘッダー ファイルをインクルードし、Odbcinst.lib インポート ライブラリを使用する必要があります。 また、実行時には、パスに Odbccp32.dll (16 ビットの場合は Odbcinst.dll) を指定する必要があります。

ODBC データ ソース名は、ODBC データ ソース アドミニストレーターなどのユーティリティを使用して作成できます。 しかし、アプリケーションから直接データ ソース名を作成し、ユーザーが別のユーティリティを実行しなくてもアクセスできるようにする方が望ましい場合もあります。

通常、ODBC データ ソース アドミニストレーターは、コントロール パネルにインストールされます。ODBC データ ソース アドミニストレーターは、Windows レジストリ (16 ビットの場合は Odbc.ini ファイル) にエントリを追加することによって、新しいデータ ソースを作成します。 ODBC ドライバー マネージャーは、このファイルを問い合わせてデータ ソースに関する必要な情報を取得します。 呼び出しを指定する必要があるため、レジストリに配置することが必要な情報を把握することが重要`::SQLConfigDataSource`します。

使用せず、この情報をレジストリに直接書き込むことでしたが`::SQLConfigDataSource`、ドライバー マネージャーがそのデータを維持するために使用する現在の手法には任意のアプリケーションが依存します。 新しいバージョンの ODBC ドライバー マネージャーでデータ ソースのレコードを保持する方法に変更があると、この手法を使うアプリケーションは動作しなくなります。 API 関数が提供されている場合はできるだけそれを使うようにしてください。 使用する場合、コードが 16 ビットから 32 ビットへの移植性にはたとえば、`::SQLConfigDataSource`関数は、関数は、Odbc.ini ファイルまたはレジストリに正しく書き込まれるためです。

##  <a name="_core_sqlconfigdatasource_parameters"></a> SQLConfigDataSource のパラメーター

次のパラメーターの説明、`::SQLConfigDataSource`関数。 多くの情報は、ODBC API から取得*プログラマーズ リファレンス*Visual C バージョン 1.5 以降で提供されます。

###  <a name="_core_function_prototype"></a> 関数プロトタイプ

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Remarks

####  <a name="_core_parameters_and_usage"></a> パラメーターと使用

*hwndParent*<br/>
新しいデータ ソースに関する追加情報をユーザーから得るために ODBC ドライバー マネージャーまたは特定の ODBC ドライバーが作成するダイアログ ボックスのオーナーとして指定するウィンドウ。 場合、 *lpszAttributes*パラメーターが十分な情報を指定していない、ダイアログ ボックスが表示されます。 *HwndParent*パラメーターは NULL になります。

*lpszDriver*<br/>
ドライバーの名前。 ユーザーに示す名前であり、物理ドライバー名 (DLL) ではありません。

*lpszAttributes*<br/>
"キー名=値" 形式で指定する属性リスト。 各文字列は NULL ターミネータで区切ります。属性リストの最後には NULL ターミネータを 2 つ続けます。 これらの属性は、主として既定のドライバー固有のエントリであり、新しいデータ ソースのレジストリに入ります。 『ODBC API Reference』には説明されていないこの関数の重要なエントリとして、"DSN (data source name)" があります。DSN では、新しいデータ ソースの名前を指定します。 残りのエントリは、新しいデータ ソースのドライバー固有のエントリです。 エントリをすべて指定する必要はありません。ドライバーは、ダイアログ ボックスを表示してユーザーに新しい値を指定させることができるからです。 (設定*hwndParent*を NULL にします)。ユーザーに値の指定を要求しないときは、明示的に既定値を提供します。

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>ODBC データ ソース アドミニストレーターを使用して lpszDriver パラメーターのドライバー名を指定するには

1. ODBC データ ソース アドミニストレーターを実行します。

1. **[追加]** をクリックします。

これにより、インストールされているドライバーとその記述の一覧が表示されます。 この説明としてを使用して、 *lpszDriver*パラメーター。 なお、その際には記述全体を使います。たとえば、"Excel Files (*.xls)" という記述の場合は、ファイル拡張子とかっこも含めます。

別の方法として、レジストリ (16 ビットの場合は Odbcinst.ini ファイル) でレジストリ キー "ODBC Drivers" (Odbcinst.ini の場合は [ODBC Drivers] セクション) の下のすべてのドライバー エントリと記述の一覧を調べることもできます。

キー名と値を検索する方法の 1 つ、 *lpszAttributes*パラメーターは、(おそらく ODBC 管理者によって構成されているもの) を既に構成されているデータ ソースの Odbc.ini ファイルを確認します。

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>lpszAttributes パラメーターのキー名と値を探すには

1. Windows レジストリ エディターを実行します (16 ビットの場合は Odbc.ini ファイルを開きます)。

1. 次のいずれかの方法を使用して ODBC データ ソース情報を検索します。

   - 32 ビットの場合、キーを見つける**HKEY_CURRENT_USER\Software\ODBC\ODBC します。データ ソースの INI\ODBC**左側のウィンドウでします。

      右側のウィンドウには、フォームのエントリが一覧表示されます:"pub:REG_SZ:*<data source name>*"ここで、 *<data source name>* を使用するドライバーに必要な設定を既に構成されているデータ ソースです。 たとえば、SQL Server、データ ソースを選択します。 文字列に続く項目"pub:"では順序、keyname と値で使用するは、 *lpszAttributes*パラメーター。

   - 16 ビットでマークされている Odbc.ini ファイルでセクションを見つけます。 [*\<データ ソース名 >*]。

      この行の後には、"キー名=値" という形式の行が続きます。 使用するエントリのうち、 *lpszAttributes*パラメーター。

使用する特定のドライバーに関するドキュメントを調べるには、ドライバーのオンライン ヘルプを参照してください。 ドライバーのオンライン ヘルプにアクセスするには、ODBC データ ソース アドミニストレーターを実行します。 これらのヘルプ ファイルは、Windows NT、Windows 3.1、または Windows 95 の通常 \system ディレクトリに配置されます。

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>ODBC ドライバーのオンライン ヘルプを参照するには

1. ODBC データ ソース アドミニストレーターを実行します。

1. **[追加]** をクリックします。

1. ドライバー名を選択します。

1. **[OK]** をクリックします。

Odbc データ ソース アドミニストレーターでは、特定のドライバーの新しいデータ ソースを作成するための情報が表示されたら、クリックして**ヘルプ**します。 このドライバーのヘルプ ファイルが開き、通常は、ドライバーの使い方に関する重要な情報が表示されます。

## <a name="see-also"></a>関連項目

[データ ソース (ODBC)](../../data/odbc/data-source-odbc.md)
