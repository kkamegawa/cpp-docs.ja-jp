---
title: ATL OLE DB コンシューマーの追加
ms.date: 05/09/2019
helpviewer_keywords:
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
ms.openlocfilehash: 1e384a283a2a149faa5b8d6e0817eac3cacfeff9
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706920"
---
# <a name="adding-an-atl-ole-db-consumer"></a>ATL OLE DB コンシューマーの追加

::: moniker range="vs-2019"

ATL OLE DB コンシューマー ウィザードは、Visual Studio 2019 以降では使用できません。 ただし、この機能を手動で追加することは可能です。 詳細については、「[ウィザードを使用しないコンシューマーの作成](../../data/oledb/creating-a-consumer-without-using-a-wizard.md)」を参照してください。

::: moniker-end

::: moniker range="<=vs-2017"

このウィザードを使用して、ATL OLE DB コンシューマーをプロジェクトに追加します。 ATL OLE DB コンシューマーは、OLE DB アクセサー クラスとデータ ソースにアクセスするために必要データ バインドで構成されます。 プロジェクトは、ATL COM アプリケーションとして作成されているか、ATL のサポート (ATL OLE DB コンシューマー ウィザードによって自動的に追加されます) を含む MFC または Win32 アプリケーションとして作成されている必要があります。

> [!NOTE]
> MFC プロジェクトに OLE DB コンシューマーを追加できます。 これを行った場合は、プロジェクトに必要な COM サポートが ATL OLE DB コンシューマー ウィザードによって追加されます。 これは、MFC プロジェクトの作成時に、 **[ActiveX コントロール]** チェック ボックス (MFC プロジェクト アプリケーション ウィザードの **[高度な機能]** ページ内) がオンになっていることを前提としています (このチェックボックスは既定でオンになっています)。 このオプションを選択することで、アプリケーションで `CoInitialize` と `CoUninitialize` が必ず呼び出されます。 MFC プロジェクトの作成時に **[ActiveX コントロール]** を選択しなかった場合は、メイン コードで `CoInitialize` と `CoUninitialize` を呼び出す必要があります。

## <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>プロジェクトに ATL OLE DB コンシューマーを追加するには

1. **クラス ビュー**で、プロジェクトを右クリックします。 ショートカット メニューの **[追加]** をクリックし、 **[クラスの追加]** をクリックします。

1. Visual C++ フォルダーで **[ATL OLE DB コンシューマー]** アイコンをダブルクリックするかそれを選択し、 **[開く]** をクリックします。

   ATL OLE DB コンシューマー ウィザードが開きます。

1. 「[ATL OLE DB コンシューマー ウィザード](../../atl/reference/atl-ole-db-consumer-wizard.md)」の説明に従って設定を定義します。

1. **[完了]** をクリックして、ウィザードを終了します。 新しく作成された OLE DB コンシューマー コードがプロジェクトに挿入されます。

::: moniker-end

## <a name="see-also"></a>関連項目

[コード ウィザードを使用した機能の追加](../../ide/adding-functionality-with-code-wizards-cpp.md)
