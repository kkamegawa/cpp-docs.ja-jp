---
title: データ アクセス プログラミング (MFC-ATL)
ms.date: 11/16/2018
helpviewer_keywords:
- MFC [C++], data access applications
- databases [C++], MFC
- OLE DB [C++], data access technologies
- data [C++], data access technologies
- data access [C++], class libraries for databases
ms.assetid: def97b2c-b5a6-445f-afeb-308050fd4852
ms.openlocfilehash: e71e16bef29239e0c6a391b2d5e2129042cd52fa
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221845"
---
# <a name="data-access-programming-mfcatl"></a>データ アクセス プログラミング (MFC/ATL)

長年にわたって、Visual C++ ではデータベースを操作するいくつかの方法を提供してきました。 2011 年には、Microsoft は、ネイティブ コードから SQL Server の製品にアクセスするための推奨されるテクノロジとしてで開いているデータベースの接続 (ODBC) を揃えることが発表しました。 ODBC は業界標準であり、これを使用することで、複数のプラットフォームおよびデータ ソースでのコードの最大の移植性が得られます。 ほとんどの SQL データベース製品および多くの NoSQL 製品で ODBC がサポートされます。 ODBC は、低レベルの ODBC API を呼び出して直接使用できます。あるいは、MFC ODBC ラッパー クラス、またはサードパーティの C++ ラッパー ライブラリを使用することもできます。

OLE DB は、COM 仕様に基づく低レベルで高パフォーマンスの API であり、Windows でのみサポートされます。 プログラムで[リンク サーバー](/sql/relational-databases/linked-servers/linked-servers-database-engine)にアクセスする場合は、OLE DB を使用します。 ATL には OLE DB テンプレートが用意されており、カスタム OLE DB プロバイダーとコンシューマーを容易に作成できます。 ドキュメントには、Microsoft SQL Server の最新のプロバイダーを参照して、 [OLE DB Driver for SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)します。

## <a name="porting-data-applications"></a>データ アプリケーションの移植

レガシ アプリケーションは、SQL Server に接続する OLE DB または ADO の上位レベルのインターフェイスを使用する場合は、最新への移行を検討する必要があります[OLE DB Driver for SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)最新の SQL Server の機能を活用するためにします。 別の方法として、クロス プラットフォームの移植性または最新の SQL Server 機能では、必要としない場合することができます可能性がありますを使用して、Microsoft OLE DB Provider for ODBC (MSDASQL)。  MSDASQL では、OLE DB と ADO (内部的に OLEDB を使用する) に構築されたアプリケーションから、ODBC ドライバーを介してデータ ソースにアクセスできます。 変換レイヤーと同様に、MSDASQL はデータベースのパフォーマンスに影響する可能性があります。 ご利用のアプリケーションに対する影響が大きいかどうかを判別するためにテストを行う必要があります。 MSDASQL は Windows オペレーティング システムに付属しており、Windows Server 2008 および Windows Vista SP1 が、64 ビット バージョンのテクノロジを含めるための最初の Windows リリースです。

場合、C++アプリケーションが SQL Server または ODBC を使用して Azure SQL Database に接続を使用する[最新の ODBC ドライバー](/sql/connect/odbc/download-odbc-driver-for-sql-server)します。

C++/CLI を使用する場合は、引き続き、通常どおり ADO.NET を使用できます。 詳細については、「[ADO.NET によるデータ アクセス (C++/CLI)](../dotnet/data-access-using-adonet-cpp-cli.md)」と「[Visual Studio でのデータ アクセス](/visualstudio/data-tools/accessing-data-in-visual-studio)」を参照してください。

- ODBC ラッパー クラスに加え、MFC では、Access データベースに接続するための Data Access Objects (DAO) ラッパー クラスも提供されます。  ただし、DAO は廃止されています。 CDaoDatabase または CDaoRecordset に基づくすべてのコードをアップグレードする必要があります。

Microsoft Windows でのデータ アクセス テクノロジの歴史の詳細については、ウィキペディアの「[Microsoft Data Access Components](https://en.wikipedia.org/wiki/Microsoft_Data_Access_Components)」を参照してください。

## <a name="see-also"></a>関連項目

[データ アクセス](data-access-in-cpp.md)<br/>
[Microsoft Open Database Connectivity (ODBC)](/sql/odbc/microsoft-open-database-connectivity-odbc)<br/>
