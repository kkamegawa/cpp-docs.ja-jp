---
title: OLE DB アーキテクチャのデザインの問題
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB, application design considerations
ms.assetid: 8caa7d99-d2bb-42c9-8884-74f228bb6ecc
ms.openlocfilehash: ef2837ea80c61f074cf567ee1fe61fa2cfa0ae73
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2019
ms.locfileid: "65525318"
---
# <a name="ole-db-architectural-design-issues"></a>OLE DB アーキテクチャのデザインの問題

> [!NOTE]
> ATL OLE DB コンシューマー ウィザードは、Visual Studio 2019 以降では使用できません。 ただし、この機能を手動で追加することは可能です。 詳細については、「[ウィザードを使用しないコンシューマーの作成](creating-a-consumer-without-using-a-wizard.md)」をご覧ください。

OLE DB アプリケーションを起動する前に、次の問題を検討してください。

## <a name="what-programming-implementation-will-you-use-to-write-your-ole-db-application"></a>どのプログラミング実装を使用して OLE DB アプリケーションを作成するか

Microsoft では、このタスクを実行するためのライブラリとして、OLE DB テンプレート ライブラリ、OLE DB 属性、および未加工の OLE DB インターフェイスを OLE DB SDK 内に用意しています。 また、プログラム作成に役立つウィザードも用意しています。 これらの実装については、「[OLE DB テンプレート、属性、およびその他の実装](../../data/oledb/ole-db-templates-attributes-and-other-implementations.md)」をご覧ください。

## <a name="do-you-need-to-write-your-own-provider"></a>独自のプロバイダーを作成する必要があるか

ほとんどの場合、開発者は、独自のプロバイダーを作成する必要はありません。 Microsoft が複数のプロバイダーを提供しています。 データ接続を作成するたびに (たとえば、**ATL OLE DB コンシューマー ウィザード**を使用してコンシューマーをプロジェクトに追加するときに)、システムに登録された使用可能なすべてのプロバイダーの一覧が **[データ リンク プロパティ]** ダイアログ ボックスに表示されます。 これらのプロバイダーのいずれかが、ご使用のデータ ストアおよびデータ アクセス アプリケーションに対応している場合は、そのプロバイダーを使用するのが最も簡単です。 ただし、ご使用のデータ ストアがこれらのカテゴリのいずれにも該当しない場合は、独自のプロバイダーを作成する必要があります。 プロバイダーの作成については、[OLE DB プロバイダー テンプレートに関するページ](../../data/oledb/ole-db-provider-templates-cpp.md)をご覧ください。

## <a name="what-level-of-support-do-you-need-for-your-consumer"></a>どのレベルのサポートがコンシューマーに必要であるか

基本的なコンシューマーもあれば、複雑なコンシューマーもあります。 OLE DB オブジェクトの機能は、プロパティで指定されます。 **ATL OLE DB コンシューマー ウィザード**を使用してコンシューマーを作成する場合、または**データベース プロバイダー ウィザード**を使用してプロバイダーを作成する場合は、適切なオブジェクト プロパティが自動的に設定され、一連の標準の機能が利用可能になります。 ただし、ウィザードで生成されたコンシューマー クラスまたはプロバイダー クラスで、必要なすべての処理がサポートされない場合は、[OLE DB テンプレート ライブラリ](../../data/oledb/ole-db-templates.md)で、それらのクラスのインターフェイスを参照する必要があります。 これらのインターフェイスにより、未加工の OLE DB インターフェイスがラップされ、それらをより使いやすくするための追加実装が提供されます。

たとえば、行セットのデータを更新したいと考えているが、ウィザードでコンシューマーを作成するときにそれを指定することを忘れた場合は、後でコマンド オブジェクト上で `DBPROP_IRowsetChange` および `DBPROP_UPDATABILITY` プロパティを設定して、その機能を指定できます。 これにより、行セットは、作成された時点で `IRowsetChange` インターフェイスを持つようになります。

## <a name="do-you-have-older-code-using-another-data-access-technology-ado-odbc-or-dao"></a>別のデータ アクセス テクノロジ (ADO、ODBC、または DAO) を使用している古いコードがあるか

さまざまなテクノロジを組み合わせることができますが (たとえば、ADO コンポーネントと OLE DB コンポーネントを併用したり、ODBC コードを OLE DB に移行したりできます)、Visual C++ ドキュメントの範囲では、すべての状況を説明することはできません。 しかしながら、さまざまなシナリオを含む多くの記事が次の Microsoft Web サイトで公開されています。

- [Microsoft ヘルプおよびサポート](https://support.microsoft.com/)

- [Microsoft Data Access Technical Articles Overview (Microsoft データ アクセス技術に関する記事の概要)](https://msdn.microsoft.com/library/ms810811.aspx)

## <a name="see-also"></a>関連項目

[OLE DB プログラミング](../../data/oledb/ole-db-programming.md)<br/>
[OLE DB プログラミングの概要](../../data/oledb/ole-db-programming-overview.md)
