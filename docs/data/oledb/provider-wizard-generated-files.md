---
title: プロバイダー ウィザードで生成されたファイル
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
ms.openlocfilehash: 0638680482546f56f26b70660ab43bd9848438a3
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707484"
---
# <a name="provider-wizard-generated-files"></a>プロバイダー ウィザードで生成されたファイル

::: moniker range="vs-2019"

ATL OLE DB プロバイダー ウィザードは、Visual Studio 2019 以降では使用できません。

::: moniker-end

::: moniker range="<=vs-2017"

**ATL OLE DB プロバイダー ウィザード**では、以下のファイルが生成されます。 以下のトピックでは、*Custom* という短い名前が使用されていますが、正確なファイル名は、プロバイダー作成時に選択した名前によって決まります。

|ファイル名|説明|
|---------------|-----------------|
|*Custom*RS.cpp|コマンド ヘルパー `Execute` メソッドとプロバイダーの列マップが含まれます。|
|*Custom*DS.h|データ ソース オブジェクトが実装されます。 このヘッダー ファイルには、データ ソース プロパティのプロパティ マップが含まれます。|
|*Custom*RS.h|コマンドおよび行セットオブジェクトが実装されます。 このヘッダー ファイルには、行セットおよびコマンド プロパティのプロパティ マップが含まれます。|
|*Custom*Sess.h|セッション オブジェクトが実装されます。 このヘッダー ファイルには、セッション プロパティのプロパティ マップが含まれます。|
|*Custom*.rgs|**OLE DB プロバイダー ウィザード**によって生成された登録済みオブジェクトが含まれます。|

::: moniker-end

## <a name="see-also"></a>関連項目

[OLE DB プロバイダーの作成](../../data/oledb/creating-an-ole-db-provider.md)<br/>
