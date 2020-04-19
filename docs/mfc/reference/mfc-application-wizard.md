---
title: MFC アプリケーション ウィザード
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: e97c7a29dd56a69fad99e85c206ca2104fa71798
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708190"
---
# <a name="mfc-application-wizard"></a>MFC アプリケーション ウィザード

MFC アプリケーション ウィザードでは、コンパイル時に Windows 実行可能アプリケーション (.exe) の基本機能が実装されるアプリケーションが生成されます。 MFC の初期アプリケーションには、C++ ソース (.cpp) ファイル、リソース (.rc) ファイル、ヘッダー (.h) ファイル、およびプロジェクト (.vcxproj) ファイルが含まれます。 これらの初期ファイルで生成されるコードは、MFC に基づいています。

> [!NOTE]
>  選択したオプションに応じて、ウィザードがこの他のファイルをプロジェクトに作成します。 例では、選択した場合の**状況依存のヘルプ**上、[高度な機能](../../mfc/reference/advanced-features-mfc-application-wizard.md) ページで、ウィザードは、プロジェクトのヘルプ ファイルをコンパイルするために必要なファイルを作成します。 ウィザードで作成されるファイルの詳細については、次を参照してください。 [Visual Studio に対して作成されるファイルの種類C++プロジェクト](../../build/reference/file-types-created-for-visual-cpp-projects.md)、およびプロジェクトの Readme.txt ファイルを参照してください。

## <a name="overview"></a>概要

ウィザードのこのページでは、作成する MFC アプリケーションの現在のアプリケーション設定が示されます。 既定では、このウィザードでは、次のようなウィザード プロジェクトが作成されます。

- [[アプリケーションの種類] (MFC アプリケーション ウィザード)](../../mfc/reference/application-type-mfc-application-wizard.md)

   - タブ付きのマルチ ドキュメント インターフェイス (MDI: Multiple Document Interface) をサポートするプロジェクト。 詳細については、次を参照してください。 [SDI と MDI](../../mfc/sdi-and-mdi.md)します。

   - プロジェクトを使用して、[ドキュメント/ビュー アーキテクチャ](../../mfc/document-view-architecture.md)します。

   - Unicode ライブラリを使用するプロジェクト

   - Visual Studio のプロジェクト形式を使用して作成された、表示形式の切り替えができるプロジェクト

   - 共有 DLL 内の MFC を使用するプロジェクト 詳細については、次を参照してください。[作成 C/C++ Visual Studio で Dll](../../build/dlls-in-visual-cpp.md)します。

- [[複合ドキュメント サポート] (MFC アプリケーション ウィザード)](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

   - 複合ドキュメントをサポートするプロジェクト

- [[ドキュメント テンプレート文字列] (MFC アプリケーション ウィザード)](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

   - 既定のドキュメント テンプレート文字列としてプロジェクト名を使用するプロジェクト

- [[データベース サポート] (MFC アプリケーション ウィザード)](../../mfc/reference/database-support-mfc-application-wizard.md)

   - データベースをサポートするプロジェクト

- [[ユーザー インターフェイスの機能] (MFC アプリケーション ウィザード)](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

   - 標準の Windows ユーザー インターフェイスがシステム メニューのステータス バー、最大化し、ボックスに、最小限に抑えるように機能を実装するプロジェクト、**について**ボックス、標準のメニュー バーとドッキング ツールバー、および子フレーム。

- [[高度な機能] (MFC アプリケーション ウィザード)](../../mfc/reference/advanced-features-mfc-application-wizard.md)

   - 印刷と印刷プレビューをサポートするプロジェクト

   - ActiveX コントロールをサポートするプロジェクト 詳細については、次を参照してください。 [ActiveX コントロールの作成の操作のシーケンス](../../mfc/sequence-of-operations-for-creating-activex-controls.md)します。

   - プロジェクトのサポートを提供しない[Automation](../../mfc/automation.md)、 [MAPI](../../mfc/mapi-support-in-mfc.md)、 [Windows Sockets](../../mfc/windows-sockets-in-mfc.md)、または Active Accessibility します。

   - サポートするプロジェクト、**エクスプ ローラー** 、ドッキング ペイン、**出力**、ドッキング ペインと**プロパティ**ドッキング ペイン。

- [[生成されたクラス] (MFC アプリケーション ウィザード)](../../mfc/reference/generated-classes-mfc-application-wizard.md)

   - プロジェクトのビュー クラスから派生、 [CView クラス](../../mfc/reference/cview-class.md)します。

   - プロジェクトのアプリケーションのクラスから派生、 [CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)します。

   - プロジェクトのドキュメント クラスから派生、 [CDocument クラス](../../mfc/reference/cdocument-class.md)します。

   - プロジェクトのメイン フレーム クラスから派生、 [CMDIFrameWndEx クラス](../../mfc/reference/cmdiframewndex-class.md)します。

   - プロジェクトの子フレーム クラスから派生、 [CMDIChildWndEx クラス](../../mfc/reference/cmdichildwndex-class.md)します。

これらの既定の設定を変更するには、ウィザードの左の列で該当するタブ タイトルをクリックし、表示されるページで必要な変更を行います。

オブジェクトまたはコントロールを追加 Visual C を使用して、プロジェクトに MFC アプリケーション プロジェクトを作成したら、[コード ウィザード](../../ide/adding-functionality-with-code-wizards-cpp.md)します。

## <a name="see-also"></a>関連項目

[MFC アプリケーションの作成](../../mfc/reference/creating-an-mfc-application.md)<br/>
[MFC デスクトップ アプリケーション](../../mfc/mfc-desktop-applications.md)<br/>
[クラスを使用した Windows アプリケーションの作成](../../mfc/using-the-classes-to-write-applications-for-windows.md)
