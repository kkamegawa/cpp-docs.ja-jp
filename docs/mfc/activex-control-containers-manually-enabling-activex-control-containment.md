---
title: ActiveX コントロール コンテナー:ActiveX コントロール サポートを手動で有効にします。
ms.date: 09/12/2018
helpviewer_keywords:
- AfxEnableControlContainer method [MFC]
- ActiveX control containers [MFC], enabling
- ActiveX controls [MFC], enabling containers
ms.assetid: 833bcde9-c9ad-4709-ad12-2fc2150fb6a5
ms.openlocfilehash: 80ca25192f3dbda711b0398917cfa68571cd2c55
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394937"
---
# <a name="activex-control-containers-manually-enabling-activex-control-containment"></a>ActiveX コントロール コンテナー:ActiveX コントロール サポートを手動で有効にします。

場合は、MFC アプリケーション ウィザードを使用してアプリケーションを作成すると ActiveX コントロールのサポートを有効にしなかった、手動でこのサポートを追加する必要があります。 この記事では、既存の OLE コンテナー アプリケーションを手動で ActiveX コントロールのサポートを追加するためのプロセスについて説明します。 事前に、OLE コンテナーで ActiveX コントロールのサポートをすることがわかっている場合、情報の記事を参照してください。 [MFC ActiveX コントロール コンテナーの作成](../mfc/reference/creating-an-mfc-activex-control-container.md)です。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

> [!NOTE]
>  この記事では、ダイアログ ベース ActiveX コントロール コンテナーという名前のプロジェクト コンテナーと円をという名前のプロシージャとコードの例として、埋め込みのコントロールを使用します。

ActiveX コントロールをサポートするには、2 つのプロジェクトのファイルを 1 行のコードを追加する必要があります。

- 変更のメイン ダイアログ ボックスの`InitInstance`関数 (コンテナーが見つかりませんでした。CPP) への呼び出しの MFC アプリケーション ウィザードで[AfxEnableControlContainer](reference/ole-initialization.md#afxenablecontrolcontainer)、次の例。

   [!code-cpp[NVC_MFCOleContainer#34](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_1.cpp)]
    [!code-cpp[NVC_MFCOleContainer#35](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_2.cpp)]

- インクルードには、次を追加します。H ヘッダー ファイル:

   [!code-cpp[NVC_MFCOleContainer#36](../mfc/codesnippet/cpp/activex-control-containers-manually-enabling-activex-control-containment_3.h)]

次の手順を完了すると後、をクリックして、プロジェクトをリビルド**ビルド**上、**ビルド**メニュー。

## <a name="see-also"></a>関連項目

[ActiveX コントロール コンテナー](../mfc/activex-control-containers.md)
