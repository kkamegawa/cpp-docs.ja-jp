---
title: '[アプリケーションの設定] (ATL プロジェクト ウィザード)'
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.atl.com.appset
helpviewer_keywords:
- ATL Project Wizard, application settings
ms.assetid: d48c9fc5-f439-49fd-884c-8bcfa7d52991
ms.openlocfilehash: bd9d5c6ef1ccb86f2968b1e2d2706092b6db45e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62249001"
---
# <a name="application-settings-atl-project-wizard"></a>[アプリケーションの設定] (ATL プロジェクト ウィザード)

使用して、**アプリケーション設定**デザインし、基本的な機能を新しい ATL プロジェクトに追加する ATL プロジェクト ウィザードのページ。

## <a name="server-type"></a>サーバーの型

次の 3 つのサーバーの種類のいずれかから選択します。

- **ダイナミック リンク ライブラリ (DLL)**

   プロセスでサーバーを作成する場合に選択します。

- **実行可能ファイル (EXE)**

   選択すると、ローカルのアウト プロセス サーバーを作成します。 このオプションでは、MFC または COM + 1.0 のサポートは許可されません。 プロキシ/スタブ コードのマージのことはできません。

- **サービス (EXE)**

   Windows の起動時に、バック グラウンドで実行されている Windows アプリケーションを作成する場合に選択します。 このオプションは、MFC または COM + 1.0 のサポートを許可しないか、プロキシ/スタブ コードのマージは許可されません。

## <a name="additional-options"></a>追加オプション

> [!NOTE]
> その他のオプションは、DLL プロジェクトにのみ使用できます。

- **プロキシ/スタブ コードのマージを許可します。**

   選択、**プロキシ/スタブ コードをマージ**インターフェイスのマーシャ リングすることが必要な場合は便利なようにチェック ボックスをオンします。 このオプションは、同じ、MIDL で生成されたプロキシとスタブ コードを実行可能ファイル サーバーとして。

- **MFC のサポート**

   オブジェクトが、MFC のサポートが含まれることを選択します。 このオプションは、クラスとが含まれている関数のいずれかをアクセスできるように、MFC ライブラリにプロジェクトをリンクします。

- **COM + 1.0 のサポート**

   COM + 1.0 コンポーネントをサポートするプロジェクトのビルド設定を変更する場合に選択します。 ライブラリの標準の一覧だけでなく、ウィザードは、COM + 1.0 コンポーネント固有のライブラリ comsvcs.lib を追加します

   さらに、mtxex.dll は、アプリケーションを起動するときに、ホスト システムに読み込まれる遅延です。

- **コンポーネント レジストラーのサポート**

   ATL プロジェクトに COM + 1.0 コンポーネントのサポートが含まれている場合は、このオプションを設定することができます。 コンポーネント レジストラーは、COM + 1.0 オブジェクトをコンポーネントの一覧を取得、コンポーネントを登録または (個別にまたは一括) コンポーネントの登録を解除できます。

## <a name="see-also"></a>関連項目

[ATL プロジェクト ウィザード](../../atl/reference/atl-project-wizard.md)<br/>
[ATL プロジェクトの作成](../../atl/reference/creating-an-atl-project.md)<br/>
[ATL プロジェクトの既定の構成](../../atl/reference/default-atl-project-configurations.md)
