---
title: SQL Server での確認可能なアセンブリの使用 (C++/CLI)
ms.date: 10/17/2018
helpviewer_keywords:
- verifiable assemblies [C++], with SQL Server
ms.assetid: 5248a60d-aa88-4ff3-b30a-b791c3ea2de9
ms.openlocfilehash: 27dec67cc0932a784cdd041ba346bb8c635b280d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384414"
---
# <a name="using-verifiable-assemblies-with-sql-server-ccli"></a>SQL Server での確認可能なアセンブリの使用 (C++/CLI)

ダイナミック リンク ライブラリ (Dll) としてパッケージ化、拡張ストアド プロシージャは、Visual C で開発した関数を使用して SQL Server の機能を拡張する手段を提供します。 拡張ストアド プロシージャは Dll 内の関数として実装されます。 拡張ストアド プロシージャも定義するだけでなく、機能[ユーザー定義型](../cpp/classes-and-structs-cpp.md)と集計関数 (SUM、AVG など)。

クライアントは、拡張ストアド プロシージャを実行するとき、SQL Server DLL を検索は、拡張ストアド プロシージャに関連付けられているし、DLL を読み込みます。 SQL Server では、要求された拡張ストアド プロシージャを呼び出すし、指定したセキュリティ コンテキストで実行します。 拡張にストアド パスの結果が設定され、サーバーにパラメーターを返しますのプロシージャをします。

SQL Server TRANSACT-SQL (T-SQL) は、SQL Server に検証可能なアセンブリをインストールすることを許可する拡張機能を提供します。 SQL Server のアクセス許可セットでは、次のセキュリティ レベルで、セキュリティ コンテキストを指定します。

- 無制限のモード:コードを各自の責任で実行します。コードはタイプ セーフではありません。

- セーフ モード:検証可能なタイプ セーフなコードを実行します。/clr:safe と共にコンパイル。

> [!IMPORTANT]
> Visual Studio 2015 で非推奨とされ、Visual Studio 2017 がサポートしていない、 **/clr: 純粋な**と **/clr:safe**検証可能なプロジェクトを作成します。 検証可能なコードが必要な場合は、c# コードを変換することをお勧めします。

作成しを SQL Server に検証可能なアセンブリを読み込むようアセンブリの作成と DROP ASSEMBLY は、TRANSACT-SQL コマンドを使用します。

```sql
CREATE ASSEMBLY <assemblyName> FROM <'Assembly UNC Path'> WITH
  PERMISSION_SET <permissions>
DROP ASSEMBLY <assemblyName>
```

PERMISSION_SET コマンドでは、セキュリティ コンテキストを指定し、無制限、SAFE、または拡張値を持つことができます。

さらに、クラスでメソッド名にバインドする関数の作成コマンドを使用できます。

```sql
CREATE FUNCTION <FunctionName>(<FunctionParams>)
RETURNS returnType
[EXTERNAL NAME <AssemblyName>:<ClassName>::<StaticMethodName>]
```

## <a name="example"></a>例

次の SQL スクリプト (たとえば、名前付き"MyScript.sql") は、SQL Server にアセンブリを読み込み、クラスのメソッドを使用できるように。

```sql
-- Create assembly without external access
drop assembly stockNoEA
go
create assembly stockNoEA
from
'c:\stockNoEA.dll'
with permission_set safe

-- Create function on assembly with no external access
drop function GetQuoteNoEA
go
create function GetQuoteNoEA(@sym nvarchar(10))
returns real
external name stockNoEA:StockQuotes::GetQuote
go

-- To call the function
select dbo.GetQuoteNoEA('MSFT')
go
```

SQL スクリプトは、SQL クエリ アナライザーまたは sqlcmd.exe ユーティリティを使用したコマンドラインで、対話的に実行できます。 次のコマンド ライン MyServer に接続する、既定のデータベースを使用して、信頼関係接続を使用して、MyScript.sql、入出力 MyResult.txt します。

```cmd
sqlcmd -S MyServer -E -i myScript.sql -o myResult.txt
```

## <a name="see-also"></a>関連項目

[クラスと構造体](../cpp/classes-and-structs-cpp.md)
