---
title: '[アプリケーションの種類] (MFC アプリケーション ウィザード)'
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.apptype
helpviewer_keywords:
- static libraries, MFC
ms.assetid: c3f62b0e-3f13-42c5-9859-d3890d0c3e1d
ms.openlocfilehash: c6d8a57c577dad20ac7bb8f579220a77d2a34850
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65708265"
---
# <a name="application-type-mfc-application-wizard"></a>[アプリケーションの種類] (MFC アプリケーション ウィザード)

このページを使用して、 [MFC アプリケーション ウィザード](../../mfc/reference/mfc-application-wizard.md)を設計し、新しい MFC アプリケーションへの基本的な機能を追加します。

- **アプリケーションの種類**

  アプリケーションで作成するドキュメントのサポートの種類を指定します。 選択したアプリケーションの種類は、アプリケーションで利用可能なユーザー インターフェイスのオプションを決定します。 参照してください[ユーザー インターフェイスの機能には、MFC アプリケーション ウィザード](../../mfc/reference/user-interface-features-mfc-application-wizard.md)詳細についてはします。

   ドキュメントの種類の詳細についてを参照してください。

  - [SDI と MDI](../../mfc/sdi-and-mdi.md)

  - [フレーム ウィンドウ](../../mfc/frame-windows.md)

  - [フレーム ウィンドウ クラス](../../mfc/frame-window-classes.md)

  - [ドキュメント、ビュー、フレームワーク](../../mfc/documents-views-and-the-framework.md)

  - [ダイアログ ボックス](../../mfc/dialog-boxes.md)

  |オプション|説明|
  |------------|-----------------|
  |**1 つのドキュメント**|ビュー クラスがに基づいて、アプリケーションのシングル ドキュメント インターフェイス (SDI) アーキテクチャを作成します。 [CView クラス](../../mfc/reference/cview-class.md)します。 ビューの基本クラスを変更することができます、[クラスの生成、MFC アプリケーション ウィザード](../../mfc/reference/generated-classes-mfc-application-wizard.md)ウィザードのページ。 たとえば、フォーム ベースのアプリケーションを作成するを使用して[CFormView クラス](../../mfc/reference/cformview-class.md)ビュー クラス。<br /><br /> この種のアプリケーションでは、ドキュメントのフレーム ウィンドウは、1 つだけのドキュメントを保持できます。|
  |**複数のドキュメント**|ビュー クラスがに基づいて、アプリケーションの複数ドキュメント インターフェイス (MDI) アーキテクチャを作成します。`CView`します。 ビューの基本クラスを変更することができます、**生成されたクラス**ウィザードのページ。 たとえば、フォーム ベースのアプリケーションを作成するを使用して`CFormView`ビュー クラス。<br /><br /> この種のアプリケーションでは、ドキュメントのフレーム ウィンドウ保持できる複数の子ウィンドウ。|
  |**タブ付きドキュメント**|別のタブには、各ドキュメントを配置します。|
  |**ダイアログ ベース**|ダイアログ クラスがに基づいて、アプリケーションのダイアログ ベースのアーキテクチャを作成します。`CDialog`します。 (HTML ダイアログを作成するには、ボックスをオン**ダイアログを使用して HTML**)。|
  |**HTML ダイアログを使用して、**|ダイアログ ボックス アプリケーションのみです。 ダイアログ クラスから派生した[CDHtmlDialog クラス](../../mfc/reference/cdhtmldialog-class.md)の代わりに[CDialog クラス](../../mfc/reference/cdialog-class.md)します。 場合は、このボックスをオン`CDHtmlDialog`に格納されて、**基本クラス**ボックスに、[クラスの生成、MFC アプリケーション ウィザード](../../mfc/reference/generated-classes-mfc-application-wizard.md)ウィザードのページ。<br /><br /> A `CDHtmlDialog`-派生 ダイアログ ボックスは、HTML ベースのダイアログ ボックスを表示、HTML を使用してデータを交換を制御し、HTML のイベントを処理します。|
  |**複数のトップレベル ドキュメント**|ビュー クラスがに基づいて、アプリケーションの最上位アーキテクチャを複数作成`CView`です。<br /><br /> この種のアプリケーション、ユーザーがクリックしたときに**新規**(または**新しいフレーム**) で、**ファイル**メニューで、アプリケーションはその親は、デスクトップでは暗黙的にウィンドウを作成します。 新しいドキュメントのフレームでは、タスク バーに表示され、アプリケーション ウィンドウのクライアント領域に限定されません。|

- **ドキュメント/ビュー アーキテクチャ サポート**

  使用して、アプリケーションでドキュメント/ビュー アーキテクチャを含めるかどうかを指定します、 [CDocument クラス](../../mfc/reference/cdocument-class.md)と[CView クラス](../../mfc/reference/cview-class.md)(既定値)。 非 MFC アプリケーションを移植する場合、または、コンパイル済み実行可能ファイルのサイズを小さく場合は、このチェック ボックスをオフにします。 既定では、ドキュメント/ビュー アーキテクチャを備えていないアプリケーションがから派生した[CWinApp クラス](../../mfc/reference/cwinapp-class.md)、ディスク ファイルからドキュメントを開くために MFC サポートは含まれません。

- **リソース言語**

  リソースの言語を設定します。 一覧は、Visual Studio がインストールされている、システムで使用できる言語を表示します。 システムの言語以外の言語を選択する場合は、その言語の適切なテンプレート フォルダー既にインストールする必要があります。

  選択した言語に反映されます、**ローカライズ文字列**のオプション、[ドキュメント テンプレート文字列、MFC アプリケーション ウィザード](../../mfc/reference/document-template-strings-mfc-application-wizard.md)ウィザードのページ。

- **Unicode ライブラリを使用して**

  Unicode または Unicode 以外のバージョンの MFC ライブラリを使用するかどうかを指定します。

- **プロジェクトのスタイル**

  アプリケーションが、標準 MFC、ファイル エクスプ ローラー、Visual Studio、または Office のアーキテクチャおよび表示にするかどうかを示します。 詳細については、次を参照してください。[ファイル エクスプ ローラー スタイルの MFC アプリケーションの作成](../../mfc/reference/creating-a-file-explorer-style-mfc-application.md)です。

  |オプション|説明|
  |------------|-----------------|
  |**MFC の標準**|標準の MFC アプリケーション アーキテクチャを提供します。|
  |**ファイル エクスプ ローラー**|左側のウィンドウは分割ウィンドウを使用して、ファイル エクスプ ローラーのようなアプリケーションを実装、 [CTreeView クラス](../../mfc/reference/ctreeview-class.md)右側のウィンドウであり、 [CListView クラス](../../mfc/reference/clistview-class.md)。|
  |**Visual Studio**|ドッキング可能な 4 つのペインを含む Visual Studio のようなアプリケーションの実装 (**ファイル ビュー**、**クラス ビュー**、**プロパティ**、および**出力**) から派生した[CDockablePane クラス](../../mfc/reference/cdockablepane-class.md)から派生したメイン フレーム ウィンドウと[CMDIFrameWndEx クラス](../../mfc/reference/cmdiframewndex-class.md)(既定値)。|
  |**Office**|派生したリボンを含む Office のようなアプリケーションを実装する[CMFCRibbonBar クラス](../../mfc/reference/cmfcribbonbar-class.md)、Outlook バーから派生した[CMFCOutlookBar クラス](../../mfc/reference/cmfcoutlookbar-class.md)から派生したキャプション バー[CMFCCaptionBar クラス](../../mfc/reference/cmfccaptionbar-class.md)とから派生したメイン フレーム[CMDIFrameWndEx クラス](../../mfc/reference/cmdiframewndex-class.md)します。|

- **Visual スタイルと色**

  アプリケーションの visual スタイルを決定します。 次のオプションを使用できます。

  - **Windows ネイティブ/既定**

  - **Office 2003**

  - **Visual Studio 2005**

  - **Office 2007 (青のテーマ)**

  - **Office 2007 (黒のテーマ)**

  - **Office 2007 (シルバーのテーマ)**

  - **Office 2007 (アクア テーマ)**

- **Visual スタイルの切り替えを有効にします。**

  かどうか、ユーザーことができます、視覚スタイルを変更、実行時にアプリケーションの通常 メニューまたはリボンから適切な visual スタイルを選択して指定します。

- **MFC の使用法**

  MFC ライブラリにリンクする方法を指定します。 既定では、MFC は、共有 DLL としてリンクされます。

  |オプション|説明|
  |------------|-----------------|
  |**共有 DLL で MFC を使用します。**|MFC ライブラリを共有 DLL としてアプリケーションにリンクします。 アプリケーションが実行時に、MFC ライブラリへの呼び出しを行います。 このオプションは、MFC ライブラリを使用して複数の実行可能ファイルで構成されるアプリケーションのディスクとメモリの量を削減します。 Win32 と MFC の両方のアプリケーションは、(既定値)、DLL で関数を呼び出すことができます。|
  |**スタティック ライブラリで MFC を使用します。**|ビルド時に、MFC のスタティック ライブラリをアプリケーションにリンクします。|

## <a name="see-also"></a>関連項目

[MFC アプリケーション ウィザード](../../mfc/reference/mfc-application-wizard.md)<br/>
[Visual Studio のファイルの種類を作成C++プロジェクト](../../build/reference/file-types-created-for-visual-cpp-projects.md)
