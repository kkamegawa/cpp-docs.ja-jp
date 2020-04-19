---
title: MFC ActiveX コントロール ウィザード
ms.date: 09/12/2018
f1_keywords:
- vc.appwiz.mfc.ctl.overview
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
ms.openlocfilehash: 3341f840c46584c4e45afe3607c83433976e6c37
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65217648"
---
# <a name="mfc-activex-control-wizard"></a>MFC ActiveX コントロール ウィザード

ActiveX コントロールは、特定の種類の[オートメーション サーバー](../../mfc/automation-servers.md);、再利用可能なコンポーネントです。 ActiveX コントロールをホストするアプリケーションは、[オートメーション クライアント](../../mfc/automation-clients.md)を制御するのです。 場合は、目的が、このような再利用可能なコンポーネントを作成するには、コントロールを作成するこのウィザードを使用します。 参照してください[MFC ActiveX コントロール](../../mfc/mfc-activex-controls.md)詳細についてはします。

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](../activex-controls.md)します。

オートメーション サーバー MFC を使用するアプリケーションを作成する代わりに、 [MFC アプリケーション ウィザード](../../mfc/reference/mfc-application-wizard.md)します。

このウィザードで作成された ActiveX コントロールは、ユーザー インターフェイスを持つことができますも表示されることができます。 このオプションを指定することができます、[コントロール設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)ウィザードのページ。 タイマー コントロールを非表示にする ActiveX コントロールの例に示します。

ActiveX コントロールは、複雑なユーザー インターフェイスを持つことができます。 カプセル化されたフォームのような一部のコントロールがあります: 1 つのコントロールの多くを格納しているフィールド、それぞれ独自の権限で Windows のコントロール。 など、MFC ActiveX コントロールとして実装される自動パーツ オブジェクトをユーザーが読み取りし、部品番号、パーツ名、およびその他の情報を編集フォームのようなユーザー インターフェイスを提供する可能性があります。 参照してください[MFC ActiveX コントロール](../../mfc/mfc-activex-controls.md)詳細についてはします。

ActiveX オブジェクトのコンテナーを作成する必要がある場合は、次を参照してください。 [ActiveX コントロール コンテナーの作成](../../mfc/reference/creating-an-mfc-activex-control-container.md)です。

MFC のスターター プログラムには、C++ ソース (.cpp) ファイル、リソース (.rc) ファイル、およびプロジェクト (.vcxproj) ファイルが含まれています。 これらのスターター ファイルで生成されたコードは、MFC に基づいています。

次のサンプル一覧は、タスクおよび ActiveX コントロールの機能強化の種類を示します。

- [ActiveX コントロールを最適化します。](../../mfc/mfc-activex-controls-optimization.md)

- [ActiveX コントロールへのストック イベントの追加](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [カスタム イベントの追加](../../mfc/mfc-activex-controls-adding-custom-events.md)

- [ストック メソッドの追加](../../mfc/mfc-activex-controls-adding-stock-methods.md)

- [カスタム メソッドの追加](../../mfc/mfc-activex-controls-adding-custom-methods.md)

- [ストック プロパティの追加](../../mfc/mfc-activex-controls-adding-stock-properties.md)

- [カスタム プロパティの追加](../../mfc/mfc-activex-controls-adding-custom-properties.md)

- [ActiveX コントロール コンテナーで ActiveX コントロールのプログラミング](../../mfc/programming-activex-controls-in-a-activex-control-container.md)

## <a name="overview"></a>概要

このウィザード ページでは、MFC ActiveX コントロール プロジェクトを作成するには、現在のアプリケーション設定について説明します。 既定では、このウィザードでは、次のようなウィザード プロジェクトが作成されます。

- 既定のプロジェクトには、実行時のライセンスまたはヘルプ ファイルは生成されません。 既定の設定を変更することができます、[アプリケーション設定](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)ページ。 ActiveX コントロール ウィザードのこのページで選択した内容のみが表示される、**概要**ページ。

- プロジェクトには、コントロール クラスと、プロジェクトの名前に基づいて、プロパティ ページ クラスが含まれています。 プロジェクトとファイル名を編集、[コントロール名](../../mfc/reference/control-names-mfc-activex-control-wizard.md)ページ。

- コントロールがない既存の Windows コントロールに基づいた、これが表示される、ユーザー インターフェイスを持つを含めたときにアクティブにする**について** ダイアログ ボックス。 既定の設定を変更することができます、[コントロール設定](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)ページ。

## <a name="see-also"></a>関連項目

[Visual Studio プロジェクト - C++](../../build/creating-and-managing-visual-cpp-projects.md)<br/>
[C++Visual Studio でプロジェクトの種類](../../build/reference/visual-cpp-project-types.md)<br/>
[概念](../../atl/active-template-library-atl-concepts.md)
