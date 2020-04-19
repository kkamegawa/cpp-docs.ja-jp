---
title: MFC プログラムまたはコントロールのソース ファイルとヘッダー ファイル
ms.date: 11/04/2016
helpviewer_keywords:
- file types [C++], MFC source and header
ms.assetid: f61419a8-bf69-4bbb-8f7c-1734be5e6db6
ms.openlocfilehash: 6a6561e993016e70764186114e1f7cabd93cdc2d
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707435"
---
# <a name="mfc-program-or-control-source-and-header-files"></a>MFC プログラムまたはコントロールのソース ファイルとヘッダー ファイル

Visual Studio で MFC プロジェクトを作成する場合、作成するプロジェクト用に選択したオプションに応じて、次のファイルが作成されます。 たとえば、プロジェクトに <*プロジェクト名*>dlg.cpp および <*プロジェクト名*>dlg.h ファイルが含まれるのは、ダイアログベースのプロジェクトまたはクラスを作成した場合だけです。

これらのファイルはすべて、*Projname* ディレクトリ、およびソリューション エクスプローラーのヘッダー ファイル (.h ファイル) フォルダーまたはソース ファイル (.cpp ファイル) フォルダーにあります。

|ファイル名|説明|
|---------------|-----------------|
|<*プロジェクト名*>.h|プログラムまたは DLL のメイン インクルード ファイルです。 すべてのグローバル シンボルおよび他のヘッダー ファイルに対する `#include` ディレクティブが含まれます。 `CWinApp` から `CPrjnameApp` クラスが派生され、`InitInstance` メンバー関数が宣言されています。 コントロールの場合、`CPrjnameApp` クラスは `COleControlModule` から派生されます。|
|<*プロジェクト名*>.cpp|メイン プログラム ソース ファイルです。 `CWinApp` から派生する `CPrjnameApp` クラスのオブジェクトを 1 つ作成し、`InitInstance` メンバー関数をオーバーライドします。<br /><br /> 実行可能ファイルの場合、`CPrjnameApp::InitInstance` は複数のことを行います。 ドキュメントとビュー間の接続として機能するドキュメント テンプレートを登録し、メイン フレーム ウィンドウを作成し、空のドキュメントを作成します (または、アプリケーションに対するコマンド ライン引数として指定されている場合は、ドキュメントを開きます)。<br /><br /> DLL および ActiveX (旧称 OLE) コントロールの場合は、`CProjNameApp::InitInstance` は `COleObjectFactory::RegisterAll` を呼び出すことによってコントロールのオブジェクト ファクトリを OLE に登録し、`AfxOLEInit` を呼び出します。 さらに、メンバー関数 `CProjNameApp::ExitInstance` を使い、**AfxOleTerm** を呼び出してメモリからコントロールをアンロードします。<br /><br /> このファイルは、`DllRegisterServer` および `DllUnregisterServer` 関数を実装することにより、Windows 登録データベース内のコントロールの登録と登録解除も行います。|
|<*プロジェクト名*>ctrl.h、<*プロジェクト名*>ctrl.cpp|`CProjnameCtrl` クラスを宣言および実装します。 `CProjnameCtrl` は `COleControl` から派生し、コントロールを初期化、描画、およびシリアル化 (読み込みと保存) する一部のメンバー関数のスケルトン実装が定義されています。 メッセージ、イベント、およびディスパッチのマップも定義されています。|
|<*プロジェクト名*>dlg.cpp、<*プロジェクト名*>dlg.h|ダイアログ ベースのアプリケーションを選択した場合に作成されます。 これらのファイルは `CProjnameDlg` という名前のダイアログ クラスから派生してそれを実装し、ダイアログを初期化してダイアログ データ交換 (DDX) を実行するスケルトン メンバー関数を含みます。 About ダイアログ クラスも、<*プロジェクト名*>.cpp 内ではなくこれらのファイルに配置されます。|
|Dlgproxy.cpp、Dlgproxy.h|ダイアログ ベースのプログラムでは、メイン ダイアログのプロジェクトのオートメーション プロキシ クラスに対する実装およびヘッダー ファイルで。 オートメーションのサポートを選択した場合にのみ使用されます。|
|<*プロジェクト名*>doc.cpp、<*プロジェクト名*>doc.h|`CProjnameDoc` という名前のドキュメント クラスから派生してそれを実装し、ドキュメントの初期化、ドキュメントのシリアル化 (保存と読み込み)、デバッグ診断の実装を行うためのスケルトン メンバー関数を含みます。|
|<*プロジェクト名*>set.h/.cpp|データベースをサポートするプログラムを作成した場合に作成され、レコードセット クラスを含みます。|
|<*プロジェクト名*>view.cpp、<*プロジェクト名*>view.h|ビュー クラス `CProjnameView` を派生して実装し、ドキュメント データの表示と印刷に使用されます。 `CProjnameView` クラスは、次のいずれかの MFC クラスから派生します。<br /><br />- [CEditView](../../mfc/reference/ceditview-class.md)<br />- [CFormView](../../mfc/reference/cformview-class.md)<br />- [CRecordView](../../mfc/reference/crecordview-class.md)<br />- [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)<br />- [CTreeView](../../mfc/reference/ctreeview-class.md)<br />- [CListView](../../mfc/reference/clistview-class.md)<br />- [CRichEditView](../../mfc/reference/cricheditview-class.md)<br />- [CScrollView](../../mfc/reference/cscrollview-class.md)<br />- [CView](../../mfc/reference/cview-class.md)<br />- [CHTMLView](../../mfc/reference/chtmlview-class.md)<br />- [CHTMLEditView](../../mfc/reference/chtmleditview-class.md)<br /><br /> プロジェクトのビュー クラスには、ビューを描画し、デバッグ診断を実装する、スケルトン メンバー関数が含まれています。 印刷のサポートを有効にした場合は、印刷、印刷セットアップ、および印刷プレビューのコマンド メッセージに対するメッセージ マップ エントリが追加されます。 これらのエントリは、ビューの基底クラスの対応するメンバー関数を呼び出します。|
|<*プロジェクト名*>PropPage.h、<*プロジェクト名*>PropPage.cpp|`CProjnamePropPage` クラスを宣言および実装します。 `CProjnamePropPage` は `COlePropertyPage` から派生し、スケルトン メンバー関数 `DoDataExchange` がデータ交換と検証の実装用に提供されます。|
|IPframe.cpp、IPframe.h|アプリケーション ウィザードの **[Automation オプション]** ページ (ステップ 3/6) でミニ サーバーまたはフル サーバー オプションが選択された場合に作成されます。 ファイルは、インプレース フレーム ウィンドウ クラス **CInPlaceFrame** を派生して実装し、サーバーがコンテナー プログラムによってインプレース アクティブ化されるときに使われます。|
|Mainfrm.cpp、Mainfrm.h|[CFrameWnd](../../mfc/reference/cframewnd-class.md) (SDI アプリケーションの場合) または [CMDIFrameWnd](../../mfc/reference/cmdiframewnd-class.md) (MDI アプリケーションの場合) から **CMainFrame** クラスを派生します。 アプリケーション ウィザードの **[アプリケーション オプション]** ページ (ステップ 4/6) で対応するオプションが選択されている場合、**CMainFrame** クラスはツール バーのボタンとステータス バーの作成を処理します。 **CMainFrame** の使い方については、「[アプリケーション ウィザードで作成されるフレーム ウィンドウ クラス](../../mfc/frame-window-classes-created-by-the-application-wizard.md)」をご覧ください。|
|Childfrm.cpp、Childfrm.h|[CMDIChildWnd](../../mfc/reference/cmdichildwnd-class.md) から **CChildFrame** クラスを派生します。 **CChildFrame** クラスは MDI ドキュメント フレーム ウィンドウに使われます。 MDI オプションを選択すると、これらのファイルが常に作成されます。|

## <a name="see-also"></a>関連項目

[Visual Studio の C++ プロジェクトに対して作成されるファイルの種類](file-types-created-for-visual-cpp-projects.md)<br>
[ATL プログラムまたはコントロールのソース ファイルとヘッダー ファイル](atl-program-or-control-source-and-header-files.md)<br>
[CLR プロジェクト](files-created-for-clr-projects.md)
