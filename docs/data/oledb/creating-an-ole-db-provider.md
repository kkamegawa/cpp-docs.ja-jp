---
title: OLE DB プロバイダーの作成
ms.date: 10/13/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: f73017c3-c89f-41a6-a306-ea992cf6092c
ms.openlocfilehash: 3e46e87b0d5d538a0f9fd7e231debfef3fa95210
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361894"
---
# <a name="creating-an-ole-db-provider"></a>OLE DB プロバイダーの作成

OLE DB プロバイダーを作成する推奨される方法は、ウィザードを使用して、ATL COM プロジェクトとプロバイダーを作成し、OLE DB テンプレートを使用してファイルを変更します。 プロバイダーをカスタマイズすると不要なプロパティをコメントにし、省略可能なインターフェイスを追加できます。

基本的な手順を以下に示します。

1. 使用して、 **ATL プロジェクト ウィザード**基本的なプロジェクト ファイルを作成して、 **ATL OLEDB プロバイダー ウィザード**プロバイダーを作成する (選択**ATL OLEDB プロバイダー** から**インストール済み** > **Visual C** > **ATL**フォルダー**新しい項目の追加**)。

   > [!NOTE]
   > プロジェクトに追加する前に MFC サポートを含める必要があります、 **ATL OLEDB プロバイダー**します。

1. コードを変更、`Execute`メソッド[CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md)します。 例については、次を参照してください。[読み取り文字列に OLE DB プロバイダー](../../data/oledb/reading-strings-into-the-ole-db-provider.md)します。

1. プロパティがマップで編集[CustomDS.h](cmyprovidersource-myproviderds-h.md)、 [CustomSess.h](cmyprovidersession-myprovidersess-h.md)、および[CustomRS.h](cmyproviderrowset-myproviderrs-h.md)します。 ウィザードでは、プロバイダーを実装できるすべてのプロパティが含まれているプロパティのマップを作成します。 プロパティ マップを移動し、削除またはコメント アウト プロパティをプロバイダーがサポートする必要はありません。

1. 更新では、PROVIDER_COLUMN_MAP [CCustomRowset(CustomRS.h)](cmyproviderrowset-myproviderrs-h.md)します。 例については、次を参照してください。[を格納する文字列で、OLE DB Provider](../../data/oledb/storing-strings-in-the-ole-db-provider.md)します。

1. プロバイダーをテストする準備ができたらは、プロバイダーの列挙体で、プロバイダーを検出することによってテストできます。 列挙体でプロバイダーを検索するテスト コードの例については、次を参照してください。、 [CATDB](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)と[DBVIEWER](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)サンプルまたは例では、[を実装する単純なコンシューマーの](../../data/oledb/implementing-a-simple-consumer.md)します。

1. 必要なインターフェイスを追加します。 例については、次を参照してください。[単純な読み取り専用プロバイダーの強化](../../data/oledb/enhancing-the-simple-read-only-provider.md)します。

   > [!NOTE]
   > 既定では、ウィザードは、OLE DB レベル 0 の準拠しているコードを生成します。 アプリケーションが、レベル 0 の準拠を引き続きようにするから取り外さないでくださいウィザードで生成されたインターフェイスのいずれかのコード。

## <a name="see-also"></a>関連項目

[CatDB サンプル:データ ソースのスキーマのブラウザー](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/catdb)<br/>
[DBViewer サンプル:データベースのブラウザー](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/dbviewer)
