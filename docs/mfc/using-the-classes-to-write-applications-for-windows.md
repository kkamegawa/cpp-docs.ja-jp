---
title: クラスを使用した Windows アプリケーションの作成
ms.date: 11/04/2016
helpviewer_keywords:
- Windows applications [MFC], MFC application framework
- MFC, application development
- applications [OLE], MFC application framework
- MFC ActiveX controls [MFC], creating
- OLE applications [MFC], MFC application framework
- database applications [MFC], creating
ms.assetid: 73f63470-857d-43dd-9a54-b38b7be0f1b7
ms.openlocfilehash: c8b3d7061c0ef06063d9c6993f24d23fc2e1f92e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411475"
---
# <a name="using-the-classes-to-write-applications-for-windows"></a>クラスを使用した Windows アプリケーションの作成

これらをまとめると、Microsoft Foundation Class (MFC) ライブラリ内のクラスは、「アプリケーション フレームワーク、」Windows オペレーティング システム用のアプリケーションをビルドするを構成します。 非常に一般的なレベルでは、フレームワークは、アプリケーションのスケルトンを定義し、スケルトンに配置できる標準のユーザー インターフェイスの実装を提供します。 プログラマは、スケルトンの残りの部分を埋めるために、アプリケーションに固有のものであります。 有利なスタートは、非常に詳細なスターター アプリケーション用のファイルを作成する MFC アプリケーション ウィザードを使用して取得できます。 特定のアプリケーション ロジックを実装するのに、ユーザー インターフェイス要素を視覚的に、デザインに Microsoft Visual C リソース エディター コード、およびクラス ライブラリにそれらの要素を接続クラス ビューのコマンドを使用するとします。

3.0 以降、MFC フレームワークのバージョンでは、Win32 プラットフォームは、Microsoft Windows 95 などと、後でプログラミングおよび Windows NT version 3.51 以降をサポートします。 マルチ スレッド MFC Win32 のサポートが含まれます。 バージョン 1.5 を使用して*x* 16 ビットのプログラミングを行う必要がある場合。

この一連のトピックは、アプリケーション フレームワークの大まかな概要を表示します。 アプリケーションの作成方法を構成する主要なオブジェクトについても調べます。 次の記事で取り上げるトピック間では、次のように示します。

- [フレームワーク](../mfc/framework-mfc.md)します。

- フレームワークと」の説明に従って、コード間の作業分担[フレームワーク上に構築](../mfc/building-on-the-framework.md)します。

- [アプリケーション クラス](../mfc/cwinapp-the-application-class.md)、アプリケーション レベルの機能をカプセル化します。

- どの[ドキュメント テンプレート](../mfc/document-templates-and-the-document-view-creation-process.md)フレーム ウィンドウの作成し、ドキュメントと関連付けられたビューを管理します。

- クラス[CWnd](../mfc/window-objects.md)、すべての windows のルートの基本クラス。

- [グラフィック オブジェクト](../mfc/graphic-objects.md)ペンとブラシなど。

フレームワークの他の部分は次のとおりです。

- [ウィンドウ オブジェクト:概要](../mfc/window-objects.md)

- [メッセージの処理とのマッピング](../mfc/message-handling-and-mapping.md)

- [CObject、ルートの基本クラス (mfc の)](../mfc/using-cobject.md)

- [ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)

- [ダイアログ ボックス](../mfc/dialog-boxes.md)

- [コントロール](../mfc/controls-mfc.md)

- [コントロール バー](../mfc/control-bars.md)

- [OLE](../mfc/ole-in-mfc.md)

- [メモリ管理](../mfc/memory-management.md)

   Windows オペレーティング システムのアプリケーションを作成する利点を渡すと、MFC もは、具体的には OLE リンクと埋め込みのテクノロジを使用するアプリケーションの記述が簡単です。 行うことができます、アプリケーション、OLE ビジュアル編集コンテナー、OLE ビジュアル編集サーバー、またはその両方とオートメーションを追加するには、他のアプリケーションは、アプリケーションからオブジェクトを使用したり、でもリモートでドライブようにします。

- [MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)

   OLE コントロールの開発キット (CDK) が完全に統合フレームワークです。 ここでは、mfc ActiveX コントロールの開発の概要を提供します。 (ActiveX コントロールが以前の OLE コントロール。)

- [データベースのプログラミング](../data/data-access-programming-mfc-atl.md)

   MFC では、書き込みのデータ アクセスを簡略化するデータベース クラスの 2 つのセットも用意されてアプリケーション。 ODBC データベース クラスを使用して、Open Database Connectivity (ODBC) ドライバーを通じてデータベースに接続する、テーブルからレコードを選択してレコード情報を表示する画面上のフォームです。 データ アクセス オブジェクト (DAO) クラスを使用して、扱えるデータベース、Microsoft Jet データベース エンジンまたは ODBC データ ソースを含む、外部の (非 Jet) データ ソースを使用します。

   さらに、MFC が Unicode を使用するアプリケーションの記述を完全に有効にし、マルチバイト文字セット (MBCS)、具体的には 2 バイト文字セット (DBCS)。

MFC のドキュメントを一般的なガイドは、次を参照してください。 [MFC の一般的なトピック](../mfc/general-mfc-topics.md)します。

## <a name="see-also"></a>関連項目

[MFC の一般的なトピック](../mfc/general-mfc-topics.md)
