---
title: MFC インターネット プログラミングのタスク
ms.date: 09/12/2018
helpviewer_keywords:
- Internet applications [MFC], getting started
- Internet applications [MFC], first steps
ms.assetid: 6377e9b8-07c4-4380-b63b-05f5a9061313
ms.openlocfilehash: 1b0a8696e25054099cdbf208dd5a1f713bfbe6d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164957"
---
# <a name="mfc-internet-programming-tasks"></a>MFC インターネット プログラミングのタスク

このセクションには、アプリケーションへのインターネットのサポートを追加する詳細な手順が含まれています。 トピックには、既存の COM コンポーネントをアクティブなドキュメントのサポートを追加する方法と、既存のアプリケーションにインターネット対応に MFC クラスを使用する方法が含まれます。 最新の株価情報、ジョージア州ピッツバーグ市のフットボールのスコアを持つドキュメントを作成して、南極 Microsoft の最新の温度をインターネット経由で行うのに役立つテクノロジのいくつか提供されます。

Active テクノロジには、ActiveX コントロールが含まれます (以前の OLE コントロール) とアクティブなドキュメントです。WinInet を簡単に取得およびインターネットの間でファイルを保存します。効率的なデータをダウンロードするための非同期のモニカー。 Visual C を提供するためのウィザードは、初期アプリケーションをすばやく開始します。 これらのテクノロジの概要については、次を参照してください。 [MFC インターネット プログラミングの基礎](../mfc/mfc-internet-programming-basics.md)と[MFC COM](../mfc/mfc-com.md)します。

ファイルを FTP たいと思ってをしていない WinSock とネットワーク プロトコル WinInet クラスをプログラミングをカプセル化するこれらのプロトコルでは、ファイルをダウンロードするインターネット上のクライアント アプリケーションの作成に使用できる関数の単純なセットを提供します。HTTP、FTP、および gopher を使用します。 WinInet を使用すると、ハード ドライブに、世界中のディレクトリを検索します。 透過的にいくつかのさまざまな種類のデータを収集し、統合されたインターフェイスでユーザーに表示できます。

大量の非同期にダウンロードするデータのモニカーはラージ オブジェクトのレンダリングをプログレッシブに COM (コンポーネント オブジェクト モデル) ソリューションを提供します。 Wininet の基礎は、非同期的にも使用できます。

次の表では、これらのテクノロジで実行できるもののいくつかについて説明します。

|あります。|をします。|必要があります。|
|--------------|-----------------|----------------|
|Web サーバー。|ログオンし、URL 要求に関する詳細情報を追跡します。|ログオン イベントと URL マッピングの通知を要求フィルターを作成します。|
|Web ブラウザー。|動的なコンテンツを提供します。|ActiveX コントロールとアクティブなドキュメントを作成します。|
|ドキュメント ベースのアプリケーション。|FTP ファイルには、サポートを追加します。|WinInet または非同期モニカーを使用します。|

開始するための詳細については、次のトピックを参照してください。

- [アプリケーションのデザイン上の検討事項](../mfc/application-design-choices.md)

- [MFC アプリケーションの作成](../mfc/writing-mfc-applications.md)

- [インターネット上の ActiveX コントロール](../mfc/activex-controls-on-the-internet.md)

- [既存の ActiveX コントロールのアップグレード](../mfc/upgrading-an-existing-activex-control.md)

- [インターネット上の非同期モニカー](../mfc/asynchronous-monikers-on-the-internet.md)

- [インターネット アプリケーションのテスト](../mfc/testing-internet-applications.md)

- [インターネット セキュリティ](../mfc/internet-security-cpp.md)

## <a name="see-also"></a>関連項目

[MFC インターネット プログラミングの基礎](../mfc/mfc-internet-programming-basics.md)<br/>
[タスク別のインターネット情報](../mfc/internet-information-by-task.md)
