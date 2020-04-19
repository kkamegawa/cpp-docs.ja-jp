---
title: オプション、ATL プロパティ ページ ウィザード
ms.date: 05/09/2019
f1_keywords:
- vc.codewiz.class.atl.ppg.options
helpviewer_keywords:
- ATL Property Page Wizard, options
ms.assetid: a7107779-b2ea-4f99-b84b-7f3e0c504bc8
ms.openlocfilehash: 205f6d3debafe22373355af12ef88c83d6a01911
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707002"
---
# <a name="options-atl-property-page-wizard"></a>オプション、ATL プロパティ ページ ウィザード


::: moniker range="vs-2019"

ATL プロパティ ページ ウィザードは、Visual Studio 2019 以降では使用できません。

::: moniker-end

::: moniker range="<=vs-2017"

このウィザード ページを使用して、作成するスレッド モデルとプロパティ ページの集計レベルを定義します。

- **スレッド モデル**

   プロパティ ページで使用されるスレッド モデルを指定します。

   詳細については、「[プロジェクトのスレッド モデルの指定 (ATL)](../../atl/specifying-the-threading-model-for-a-project-atl.md)」を参照してください。

   |オプション|説明|
   |------------|-----------------|
   |**Single**|プロパティ ページは、プライマリ COM スレッドでのみ実行されます。|
   |**Apartment**|任意の単一のスレッド アパートメントにプロパティ ページを作成できます。 これが既定値です。|

- **集計**

   作成するプロパティ ページに集計サポートを追加します。 詳細については、「[集計](../../atl/aggregation.md)」を参照してください。

   |オプション|説明|
   |------------|-----------------|
   |**はい**|集計可能なプロパティ ページを作成します。|
   |**No**|集計が不可能なプロパティ ページを作成します。|
   |**Only**|集計経由でのみインスタンス化できるプロパティ ページを作成します。|

::: moniker-end

## <a name="see-also"></a>関連項目

[ATL プロパティ ページ ウィザード](../../atl/reference/atl-property-page-wizard.md)<br/>
[文字列、ATL プロパティ ページ ウィザード](../../atl/reference/strings-atl-property-page-wizard.md)
