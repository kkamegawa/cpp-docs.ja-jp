---
title: OLE DB コンシューマー テンプレート (C++)
ms.date: 10/22/2018
helpviewer_keywords:
- databases [C++], OLE DB templates
- OLE DB consumers [C++], data access
- OLE DB consumer templates [C++]
- databases [C++], consumers
ms.assetid: d3e42612-0bc0-4d65-9c32-0e8a7b219e82
ms.openlocfilehash: d2697c955d2063bb075e06536b083c0b138aa4ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284047"
---
# <a name="ole-db-consumer-templates-c"></a>OLE DB コンシューマー テンプレート (C++)

OLE DB コンシューマー テンプレートは、OLE DB Version 2.6 仕様をサポートしています (OLE DB コンシューマー テンプレートは OLE DB 2.6 でテストされますが、仕様内のすべてのインターフェイスをサポートしない)。コンシューマー テンプレートを使用すると、OLE DB コンシューマーを実装するために記述するコードの量を最小限に抑えられます。 テンプレートには、次に示す機能があります。

- OLE DB 機能への簡単なアクセスと ATL および MFC との簡単な統合。

- データベースのパラメーターと列の簡単なバインド モデル。

- OLE DB プログラミング用のネイティブの C/C++ データ型。

OLE DB テンプレートを使用するには、C++ テンプレート、COM、および OLE DB インターフェイスに関する知識が必要です。 OLE DB を知らない場合は、次を参照してください。 [Microsoft OLE DB Driver for SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)します。

OLE DB テンプレートは、新しいオブジェクト モデルを追加するのではなく、既存の OLE DB オブジェクト モデルをサポートします。 OLE DB コンシューマー テンプレートの最上位クラスは、OLE DB 仕様で定義されたコンポーネントと同等のものです。 OLE DB コンシューマー テンプレートのデザインには、1 つの行セットに対する複数のアクセサーなどの高度な機能が含まれます。 テンプレートと多重継承を使用することで、ライブラリを小型で柔軟なものにすることができます。

## <a name="how-ole-db-consumers-access-data"></a>OLE DB コンシューマーがデータにアクセスする方法

コンシューマーは、複数の種類のオブジェクトを使用します。これらのオブジェクトについては、次に示すトピックで説明しています。

- [データ ソースとセッション](../../data/oledb/data-sources-and-sessions.md)

- [アクセサーと行セット](../../data/oledb/accessors-and-rowsets.md)

- [コマンドとテーブル](../../data/oledb/commands-and-tables.md)

- [ユーザー レコード](../../data/oledb/user-records.md)

コンシューマーが何らかの処理を行う前に、アクセスする必要のあるデータベースの種類 (SQL、Oracle、ODBC、MSDS など) に適した OLE DB プロバイダーを選択します。 プロバイダーを選択するには、通常は列挙子を使用します (「 [データ ソースとセッション](../../data/oledb/cenumerator-class.md) 」の説明にある「 [CEnumerator](../../data/oledb/data-sources-and-sessions.md)」を参照してください)。

[データ ソース オブジェクト](../../data/oledb/data-sources-and-sessions.md) は、選択したデータ ソースへの接続に必要な接続情報を提供します。 データ ソース オブジェクトには、認証情報 (ログイン名やパスワードなど) も含まれています。この認証情報は、データ ソースへのアクセス許可をユーザーに付与するために使用されます。 データ ソース オブジェクトは、データベースへの接続を確立してから、1 つ以上のセッション オブジェクトを作成します。 各 [セッション オブジェクト](../../data/oledb/data-sources-and-sessions.md) は、データベースとの独自の相互作用 (データのクエリと取得) を管理し、その他の既存のセッションに依存することなく、これらのトランザクションを実行します。

セッションは、行セット オブジェクトとコマンド オブジェクトを作成します。 [コマンド オブジェクト](../../data/oledb/commands-and-tables.md) により、ユーザーは、たとえば SQL コマンドを使用してデータベースと対話できます。 [行セット オブジェクト](../../data/oledb/accessors-and-rowsets.md) とは、データのセットであり、このセット内を移動して、 [行を更新、削除、および挿入](../../data/oledb/updating-rowsets.md)できます。

OLE DB コンシューマーは、データベース テーブル内の列をローカル変数とバインドします。このバインドは、コンシューマー内でデータが格納される方法についてのマップを含む、 [アクセサー](../../data/oledb/accessors-and-rowsets.md)を使用して行われます。 このマップは、テーブルの列とコンシューマー アプリケーションのローカル バッファー (変数) との間のバインディングのセットで構成されます。

コンシューマーを扱うときの 1 つの重要な概念は、コンシューマーでは、 [コマンド (またはテーブル) クラス](../../data/oledb/commands-and-tables.md) と [ユーザー レコード クラス](../../data/oledb/user-records.md)の 2 つのクラスを宣言することです。 行セットには、コマンド (またはテーブル) クラスを使用してアクセスします。このクラスは、アクセサー クラスと行セット クラスの両方から継承します。 ユーザー レコード クラスには、前述した行セットのバインド マップが含まれます。

詳細については、次のトピックを参照してください。

- [OLE DB コンシューマーの作成](../../data/oledb/creating-an-ole-db-consumer.md)

- [OLE DB コンシューマーの一般的なシナリオ (使用例)](../../data/oledb/working-with-ole-db-consumer-templates.md)

## <a name="see-also"></a>関連項目

[OLE DB プログラミング](../../data/oledb/ole-db-programming.md)<br/>
[データ アクセス](../data-access-in-cpp.md)<br/>
[OLE DB SDK のドキュメント](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[Microsoft OLE DB Driver for SQL Server](/sql/connect/oledb/oledb-driver-for-sql-server)
