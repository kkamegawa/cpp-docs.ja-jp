---
title: クラス ライブラリの概要
ms.date: 09/17/2019
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- grouping MFC classes
- MFC, class library
- classes [MFC], MFC
- class libraries, MFC
- class libraries
ms.assetid: 9b0e3152-ac39-4f52-91b4-f20aa3a674aa
ms.openlocfilehash: 23097c0bf3399a4dced6640f41c0d46dba101b26
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095954"
---
# <a name="class-library-overview"></a>クラス ライブラリの概要

この概要では、MFC (Microsoft Foundation Class) ライブラリ Version 9.0 のクラスを分類し、説明します。 MFC のクラスは、全体として、Windows API 用に記述されたアプリケーションのフレームワークであるアプリケーション フレームワークを構成します。 プログラミング タスクは、アプリケーション固有のコードを入力することです。

ここでは、ライブラリのクラスを次のカテゴリで表します。

- [ルート クラス: CObject](../mfc/root-class-cobject.md)

- [MFC アプリケーション アーキテクチャ クラス](../mfc/mfc-application-architecture-classes.md)

   - [アプリケーションおよびスレッド サポート クラス](../mfc/application-and-thread-support-classes.md)

   - [コマンド ルーティング クラス](../mfc/command-routing-classes.md)

   - [ドキュメント クラス](../mfc/document-classes.md)

   - [ビュー クラス (アーキテクチャ)](../mfc/view-classes-architecture.md)

   - [フレーム ウィンドウ クラス (アーキテクチャ)](../mfc/frame-window-classes-architecture.md)

   - [ドキュメント テンプレート クラス](../mfc/document-template-classes.md)

- [ウィンドウ、ダイアログ、コントロール クラス](../mfc/window-dialog-and-control-classes.md)

   - [フレーム ウィンドウ クラス (Windows)](../mfc/frame-window-classes-windows.md)

   - [ビュー クラス (Windows)](../mfc/view-classes-windows.md)

   - [ダイアログ ボックス クラス](../mfc/dialog-box-classes.md)

   - [コントロール クラス](../mfc/control-classes.md)

   - [コントロール バー クラス](../mfc/control-bar-classes.md)

- [描画および印刷クラス](../mfc/drawing-and-printing-classes.md)

   - [出力 (デバイス コンテキスト) クラス](../mfc/output-device-context-classes.md)

   - [描画ツール クラス](../mfc/drawing-tool-classes.md)

- [単純データ型クラス](../mfc/simple-data-type-classes.md)

- [配列、リスト、マップ クラス](../mfc/array-list-and-map-classes.md)

   - [配列、リスト、マップのテンプレート クラス](../mfc/template-classes-for-arrays-lists-and-maps.md)

   - [使用可能な配列クラス](../mfc/ready-to-use-array-classes.md)

   - [使用可能なリスト クラス](../mfc/ready-to-use-list-classes.md)

   - [使用可能なマップ クラス](../mfc/ready-to-use-map-classes.md)

- [ファイルおよびデータベース クラス](../mfc/file-and-database-classes.md)

   - [ファイル i/o クラス](../mfc/file-i-o-classes.md)

   - [DAO クラス](../mfc/dao-classes.md)

   - [ODBC クラス](../mfc/odbc-classes.md)

   - [OLE DB クラス](../mfc/ole-db-classes.md)

- [インターネットおよびネットワーク クラス](../mfc/internet-and-networking-classes.md)

   - [Windows Sockets クラス](../mfc/windows-sockets-classes.md)

   - [Win32 インターネット クラス](../mfc/win32-internet-classes.md)

- [OLE クラス](../mfc/ole-classes.md)

   - [OLE コンテナー クラス](../mfc/ole-container-classes.md)

   - [OLE サーバー クラス](../mfc/ole-server-classes.md)

   - [OLE ドラッグ アンド ドロップおよびデータ転送クラス](../mfc/ole-drag-and-drop-and-data-transfer-classes.md)

   - [OLE コモン ダイアログ クラス](../mfc/ole-common-dialog-classes.md)

   - [OLE オートメーション クラス](../mfc/ole-automation-classes.md)

   - [OLE コントロール クラス](../mfc/ole-control-classes.md)

   - [アクティブ ドキュメント クラス](../mfc/active-document-classes.md)

   - [OLE 関連クラス](../mfc/ole-related-classes.md)

- [デバッグおよび例外クラス](../mfc/debugging-and-exception-classes.md)

   - [デバッグ サポート クラス](../mfc/debugging-support-classes.md)

   - [例外クラス](../mfc/exception-classes.md)

「[一般的なクラスのデザインの考え方](../mfc/general-class-design-philosophy.md)」では、MFC ライブラリの設計方法について説明します。

フレームワークの概要については、「 [Windows 用のアプリケーションを記述するためのクラスの使用](../mfc/using-the-classes-to-write-applications-for-windows.md)」を参照してください。 上記のクラスの一部は、フレームワークの外部で使用できる汎用クラスであり、コレクション、例外、ファイル、文字列などの便利な抽象化を提供します。

クラスの継承を表示するには、[クラス階層図](../mfc/hierarchy-chart.md)を使用します。

この概要で示されているクラスに加えて、MFC ライブラリには多くのグローバル関数、グローバル変数、およびマクロが含まれています。 これらの概要と詳細な一覧については、「mfc[マクロとグローバル](../mfc/reference/mfc-macros-and-globals.md)」を参照してください。これは、mfc クラスのアルファベット順のリファレンスに従います。

## <a name="see-also"></a>関連項目

[MFC デスクトップ アプリケーション](../mfc/mfc-desktop-applications.md)
