---
title: プロバイダーの作成
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 7a8b4caf85ff7d0310c97cb953739796cca21c43
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707575"
---
# <a name="creating-the-provider"></a>プロバイダーの作成

::: moniker range="vs-2019"

ATL OLE DB プロバイダー ウィザードは、Visual Studio 2019 以降では使用できません。

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>ATL OLE DB プロバイダー ウィザードで OLE DB プロバイダーを作成するには

1. プロジェクトを右クリックします。

1. ショートカット メニューの **[追加]** 、 **[クラスの追加]** を順にクリックします。

1. **[クラスの追加]** ダイアログ ボックスで、 **[インストール済み]** > **[Visual C++]** > **[ATL]** の下にある **[ATL OLEDB プロバイダー]** アイコンを選択し、 **[開く]** をクリックします。

1. **ATL OLE DB プロバイダー ウィザード**で、 **[短い名前]** ボックスにプロバイダーの短い名前を入力します。 以降のトピックでは、短い名前として *Custom* を使用しますが、別の名前を使用してもかまいません。 他の名前ボックスは、入力した名前に基づいて設定されます。

1. 必要に応じて、他の名前ボックスを編集します。 オブジェクト名やファイル名のほかにも、以下を編集できます。

   - **コクラス**:COM がプロバイダーを作成するために使用する名前です。

   - **ProgID**:プログラムの ID。GUID の代わりに使用できるテキスト文字列です。

   - **バージョン**:ProgID とコクラスとともに、バージョンに依存するプログラム ID を生成するために使用されます。

1. **[完了]** をクリックします。

::: moniker-end

## <a name="see-also"></a>関連項目

[OLE DB プロバイダーの作成](../../data/oledb/creating-an-ole-db-provider.md)
