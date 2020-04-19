---
title: OLE DB プロバイダー テンプレート (C++)
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers [C++], about providers
- databases [C++], OLE DB templates
- OLE DB provider templates [C++], about OLE DB provider templates
- templates [C++], OLE DB
ms.assetid: fccff85f-2af8-4500-82bd-6312d28a74b8
ms.openlocfilehash: 793aa08630ec92f99c33c2a4f3688e78630a6c58
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361257"
---
# <a name="ole-db-provider-templates-c"></a>OLE DB プロバイダー テンプレート (C++)

OLE DB は、Microsoft Universal Data Access 戦略の重要な部分です。 OLE DB の設計では、任意のデータ ソースからのパフォーマンスの高いデータ アクセスを許可します。 表形式データでは、データベースからの送信かどうかに関係なく OLE DB で表示できます。 柔軟性を使用すると、大量の電力ができます。

説明したよう[OLE DB コンシューマーとプロバイダー](../../data/oledb/ole-db-consumers-and-providers.md)、OLE DB コンシューマーとプロバイダーの概念を使用します。 コンシューマーは、データに対する要求を行うプロバイダーは、コンシューマーに表形式でデータを返します。 プログラミングの観点からこのモデルの最も重要な意味は、プロバイダーがコンシューマーが行うすべての呼び出しを実装する必要があります。

## <a name="what-is-a-provider"></a>プロバイダーとは何ですか。

OLE DB プロバイダーは、(データ ストアと呼ばれます) の持続性のあるソースからコンシューマーに表形式でデータを転送するコンシューマー オブジェクト、インターフェイスの呼び出しを処理する COM オブジェクトのセットです。

プロバイダーは、単純または複雑なを指定できます。 プロバイダーは、複数のインターフェイスを実装することで、最小限の機能または本格的な運用環境品質プロバイダーをサポートできます。 プロバイダーでは、テーブルを返す、クライアントが、そのテーブルの形式を決定できる、およびそのデータに対して操作を実行できます。

各プロバイダーは、すべての OLE DB コンシューマーが (C++ など、基本的な) の言語に関係なく、任意のプロバイダーからデータをアクセスできること、クライアントからの要求を処理する COM オブジェクトの標準セットを実装します。

各 COM オブジェクトには、その一部は必須でありその一部は省略可能ないくつかのインターフェイスが含まれています。 必須のインターフェイスを実装するは、プロバイダーは、任意のクライアントが使用できるようにする機能 (コンプライアンスと呼ばれる) の最小レベルを保証します。 プロバイダーは、追加の機能を提供する省略可能なインターフェイスを実装できます。 [OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)これらのインターフェイスの詳細について説明します。 クライアントは常に呼び出す必要があります`QueryInterface`をプロバイダーが特定のインターフェイスをサポートしているかを判断します。

## <a name="ole-db-specification-level-support"></a>OLE DB 仕様のレベルのサポート

OLE DB プロバイダー テンプレートは、OLE DB バージョン 2.7 仕様をサポートします。 OLE DB プロバイダー テンプレートを使用して、レベル 0 の準拠のプロバイダーを実装できます。 `Provider`サンプルでは、たとえば、テンプレートを使用して、DOS DIR コマンドで、ファイル システムのクエリを実行して non-MS-DOS コマンド サーバーが実装されます。 `Provider`サンプルは、表形式のデータを返すための標準の OLE DB メカニズムは、行セット ディレクトリ情報を返します。

OLE DB テンプレートでサポートされているプロバイダーの最も単純な型は、コマンドが存在しないと読み取り専用プロバイダーです。 コマンドでプロバイダーは、ブックマークの設定と読み取り/書き込み機能もサポートされます。 追加のコードを記述することで、読み取り/書き込みのプロバイダーを実装できます。 動的な行セットおよびトランザクションが現在のバージョンでサポートされていませんが、する場合は追加することができます。

## <a name="when-do-you-need-to-create-an-ole-db-provider"></a>OLE DB プロバイダーの作成に必要な場合

常に、独自のプロバイダーを作成する必要はありません。Microsoft 提供のいくつかのあらかじめパッケージ化された、標準的なプロバイダー、**データ リンク プロパティ**Visual C でのダイアログ ボックス。 OLE DB プロバイダーを作成する主な理由は、汎用的なデータ アクセス戦略を活用するためにです。 これの利点のためいくつか示します。

- C++、Basic、および Visual Basic Scripting Edition などの任意の言語を使用してデータにアクセスします。 これにより、どのような言語の使用、組織内の複数のプログラマに関係なく同じ方法で同じデータにアクセスできます。

- SQL Server、Excel、およびアクセスなどの他のデータ ソースにデータを開きます。 これは、さまざまな形式の間でデータを転送する場合に便利だことができます。

- (異種) 間のデータ ソースの操作に参加します。 データ ウェアハウスの効果的な方法を指定できます。 OLE DB プロバイダーを使用するは、ネイティブ形式でデータを保持し、単純な操作でアクセスできます。

- クエリ処理などのデータに追加機能を追加します。

- 操作方法を制御することでデータへのアクセスのパフォーマンスが向上します。

- 保全性の向上。 独自のデータ形式がある場合、1 つだけのプログラマにアクセスできる、危険性が。 OLE DB プロバイダーを使用して、すべてのプログラマにその独自の形式を開くことができます。

## <a name="read-only-and-updatable-providers"></a>読み取り専用と更新可能なプロバイダー

プロバイダーは、複雑さと機能が大幅に異なります。 読み取り専用プロバイダー、および更新可能なプロバイダーのプロバイダーに分類すると便利です。

- Visual C 6.0 には、読み取り専用プロバイダーのみがサポートされています。 [OLE DB プロバイダーを作成する](../../data/oledb/creating-an-ole-db-provider.md)読み取り専用プロバイダーを作成する方法について説明します。
- Visual C は、更新可能なプロバイダーは、更新をサポートしています (書き込む) データ ストア。 更新可能なプロバイダーについては、次を参照してください。[更新可能なプロバイダーを作成する](../../data/oledb/creating-an-updatable-provider.md)、 [UpdatePV](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Provider/UPDATEPV)サンプルは、更新可能なプロバイダーの例を示します。

詳細については次を参照してください:

- [OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)

- [OLE DB プロバイダーの作成](../../data/oledb/creating-an-ole-db-provider.md)

- [OLE DB プログラミング](../../data/oledb/ole-db-programming.md)

## <a name="see-also"></a>関連項目

[データ アクセス](../data-access-in-cpp.md)<br/>
[OLE DB SDK のドキュメント](/previous-versions/windows/desktop/ms722784(v=vs.85))<br/>
[OLE DB プログラマーズ リファレンス](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming)<br/>
