---
title: プロパティ マップ
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 9df98dc85c9242693319542cea0730341d87a052
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284034"
---
# <a name="property-maps"></a>プロパティ マップ

セッション、行セット、および省略可能なコマンド オブジェクトを使用は、各プロバイダーは、1 つまたは複数のプロパティをサポートします。 によって作成されたヘッダー ファイルに格納されているプロパティのマップでこれらのプロパティが定義されている、 **OLE DB プロバイダー ウィザード**します。 各ヘッダー ファイルには、オブジェクトまたはそのファイルで定義されたオブジェクトに対して定義されている OLE DB プロパティのグループのプロパティのマップが含まれています。 データ ソース オブジェクトを含むヘッダー ファイルには、プロパティのマップも含まれています、 [DataSource プロパティ](https://msdn.microsoft.com/library/ms724188)します。 `Session.h` プロパティのマップが含まれています、[セッション プロパティ](/previous-versions/windows/desktop/ms714221(v=vs.85))します。 行セットとコマンド オブジェクトはという 1 つのヘッダー ファイルの*projectname*RS.h します。 これらのプロパティのメンバーである、[行セット プロパティ](/previous-versions/windows/desktop/ms711252(v=vs.85))グループ。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレートのアーキテクチャ](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
