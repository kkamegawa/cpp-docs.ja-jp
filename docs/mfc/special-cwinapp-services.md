---
title: CWinApp のその他のサービス
ms.date: 11/04/2016
f1_keywords:
- LoadStdProfileSettings
- EnableShellOpen
helpviewer_keywords:
- files [MFC], most recently used
- DragAcceptFiles method [MFC]
- MRU lists
- GDI+, initializing for MFC
- GDI+, suppressing background thread [MFC]
- CWinApp class [MFC], shell registration
- application objects [MFC], services
- CWinApp class [MFC], initializing GDI+
- MFC, shell registration
- CWinApp class [MFC], File Manager drag and drop
- LoadStdProfileSettings method [MFC]
- MFC, most-recently-used file list
- RegisterShellFileTypes method [MFC]
- drag and drop [MFC], files
- registering file types
- Shell, registering file types
- services, provided by CWinApp
- CWinApp class [MFC], recently used documents
- CWinApp class [MFC], services
- files [MFC], drag and drop
- EnableShellOpen method [MFC]
- registry [MFC], most recently used files
- MFC, file operations
- registration [MFC], shell
ms.assetid: 0480cd01-f629-4249-b221-93432d95b431
ms.openlocfilehash: 04c7357d67dc1a5daee4b8b8135c9a54eda8504a
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127830"
---
# <a name="special-cwinapp-services"></a>CWinApp のその他のサービス

メッセージループを実行するだけでなく、アプリケーションを初期化し、後でクリーンアップすることもできます。 [CWinApp](../mfc/reference/cwinapp-class.md)には他のいくつかのサービスが用意されています。

##  <a name="_core_shell_registration"></a>シェル登録

既定では、MFC アプリケーションウィザードを使用すると、アプリケーションが作成したデータファイルをエクスプローラーまたはファイルマネージャーでダブルクリックして開くことができます。 アプリケーションが MDI アプリケーションで、アプリケーションで作成されるファイルの拡張子を指定すると、MFC アプリケーションウィザードによって、 [CWinApp](../mfc/reference/cwinapp-class.md)の[RegisterShellFileTypes](../mfc/reference/cwinapp-class.md#registershellfiletypes)および[EnableShellOpen](../mfc/reference/cwinapp-class.md#enableshellopen)メンバー関数の呼び出しが、書き込み先のオーバーライド `InitInstance` に追加されます。

`RegisterShellFileTypes`、アプリケーションのドキュメントの種類をエクスプローラーまたはファイルマネージャーに登録します。 関数は、Windows が保持する登録データベースにエントリを追加します。 エントリは、各ドキュメントの種類を登録し、ファイル拡張子をファイルの種類に関連付け、アプリケーションを開くコマンドラインを指定し、動的データエクスチェンジ (DDE) コマンドを指定してその種類のドキュメントを開きます。

`EnableShellOpen` は、ユーザーが選択したファイルを開くために、アプリケーションがエクスプローラーまたはファイルマネージャーから DDE コマンドを受け取ることができるようにすることで、プロセスを完了します。

`CWinApp` でのこの自動登録サポートにより、アプリケーションで .reg ファイルを配布したり、特別なインストール作業を実行したりする必要がなくなります。

( [InitInstance](../mfc/reference/cwinapp-class.md#initinstance)関数で[GdiplusStartup](/windows/win32/api/gdiplusinit/nf-gdiplusinit-gdiplusstartup)を呼び出すことによって) アプリケーションの gdi + を初期化する場合は、gdi + のバックグラウンドスレッドを非表示にする必要があります。

これを行うには、 [GdiplusStartupInput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupinput)構造体の `SuppressBackgroundThread` メンバーを**TRUE**に設定します。 GDI + のバックグラウンドスレッドを抑制する場合は、アプリケーションのメッセージループを開始して終了する直前に、`NotificationHook` と `NotificationUnhook` の呼び出しを行う必要があります。 これらの呼び出しの詳細については、「 [GdiplusStartupOutput](/windows/win32/api/gdiplusinit/ns-gdiplusinit-gdiplusstartupoutput)」を参照してください。 したがって、次に示すように、`GdiplusStartup` とフック通知関数は、仮想関数[CWinApp:: Run](../mfc/reference/cwinapp-class.md#run)をオーバーライドすることをお勧めします。

[!code-cpp[NVC_MFCDocView#6](../mfc/codesnippet/cpp/special-cwinapp-services_1.cpp)]

バックグラウンド GDI + スレッドを抑制しない場合、メインウィンドウが作成される前に、アプリケーションに対して DDE コマンドが事前に発行される可能性があります。 シェルによって発行された DDE コマンドは、途中で中止されることがあり、その結果、エラーメッセージが表示されます。

##  <a name="_core_file_manager_drag_and_drop"></a>ファイルマネージャーのドラッグアンドドロップ

ファイルは、ファイルマネージャーまたはエクスプローラーのファイルビューウィンドウからアプリケーションのウィンドウにドラッグできます。 たとえば、MDI アプリケーションのメインウィンドウに1つ以上のファイルをドラッグできるようにすることもできます。この場合、アプリケーションはファイル名を取得し、それらのファイルの MDI 子ウィンドウを開くことができます。

アプリケーションでファイルのドラッグアンドドロップを有効にするために、MFC アプリケーションウィザードでは、`InitInstance`内のメインフレームウィンドウの[CWnd](../mfc/reference/cwnd-class.md)メンバー関数[dragacceptfiles](../mfc/reference/cwnd-class.md#dragacceptfiles)への呼び出しが書き込まれます。 ドラッグアンドドロップ機能を実装しない場合は、その呼び出しを削除できます。

> [!NOTE]
>  OLE を使用すると、より一般的なドラッグアンドドロップ機能を実装して、ドキュメント内またはドキュメント内でデータをドラッグすることもできます。 詳細については、「 [OLE ドラッグアンドドロップ](../mfc/drag-and-drop-ole.md)」を参照してください。

##  <a name="_core_keeping_track_of_the_most_recently_used_documents"></a>最近使用したドキュメントを追跡する

ユーザーがファイルを開いて閉じると、アプリケーションオブジェクトは最近使用した4つのファイルを追跡します。 これらのファイルの名前は [ファイル] メニューに追加され、変更すると更新されます。 フレームワークは、これらのファイル名をレジストリまたは .ini ファイルのどちらかに保存します。プロジェクトと同じ名前を付けて、アプリケーションの起動時にファイルから読み取ります。 MFC アプリケーションウィザードによって作成される `InitInstance` オーバーライドには、 [CWinApp](../mfc/reference/cwinapp-class.md)メンバー関数[LoadStdProfileSettings](../mfc/reference/cwinapp-class.md#loadstdprofilesettings)の呼び出しが含まれます。これにより、最近使用したファイル名を含むレジストリまたは .ini ファイルから情報が読み込まれます。

これらのエントリは次のように格納されます。

- Windows NT、Windows 2000、およびそれ以降では、値はレジストリキーに格納されます。

- Windows 2.x では、値は WIN に格納されます。INI ファイル。

- Windows 95 以降では、値はキャッシュされた WIN のバージョンに格納されます.INI.

## <a name="see-also"></a>参照

[CWinApp: アプリケーション クラス](../mfc/cwinapp-the-application-class.md)
