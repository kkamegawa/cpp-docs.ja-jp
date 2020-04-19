---
title: テスト コンテナーでのプロパティとイベントのテスト
ms.date: 11/04/2016
helpviewer_keywords:
- testing, test containers
- tstcon32.exe
- debugging ActiveX controls
- test container
- ActiveX Control Test Container
- ActiveX controls [MFC], testing
- properties [MFC], testing
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
ms.openlocfilehash: 977ef29095e652ab40028a2e8ba7feffabf56418
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62306451"
---
# <a name="testing-properties-and-events-with-test-container"></a>テスト コンテナーでのプロパティとイベントのテスト

Visual C に付属して、テスト コンテナー アプリケーションは、テストと ActiveX コントロールをデバッグ用の ActiveX コントロール コンテナーです。 テスト コンテナーには、コントロールの機能をテストするには、そのプロパティを変更して、メソッドを呼び出し、そのイベントを発生させるコントロール開発者ができるようにします。 テスト コンテナーがデータ バインディングの通知のログを表示し、ActiveX コントロールの永続化機能をテストするための機能も提供します。 ストリームまたはほかのプロパティを保存、再読み込み、および格納されたストリームのデータを調べることができます。 このセクションでは、テスト コンテナーの基本機能を使用する方法について説明します。 詳細については、選択、**ヘルプ**テスト コンテナーの実行中のメニュー。

### <a name="to-access-the-activex-control-test-container"></a>ActiveX コントロール テスト コンテナーへのアクセス

1. ビルド、 [TSTCON サンプル。ActiveX コントロール テスト コンテナー](../overview/visual-cpp-samples.md)します。

### <a name="to-test-your-activex-control"></a>ActiveX コントロールをテストするには

1. **編集**テスト コンテナーのメニュー**新しいコントロールを挿入**します。

1. **コントロールの挿入**ボックスで、目的のコントロールを選択し、をクリックして**OK**します。 コントロールは、コントロール コンテナーに表示されます。

    > [!NOTE]
    >  コントロールが表示されていない場合、**コントロールの挿入** ダイアログ ボックスで、それを登録するかどうかを確認、**コントロールの登録**コマンドを**ファイル**テストのメニューコンテナーです。

この時点で、コントロールのプロパティまたはイベントをテストすることができます。

#### <a name="to-test-properties"></a>プロパティをテストするには

1. **コントロール** メニューのをクリックして**メソッドの呼び出し**します。

1. **メソッド名**ドロップダウン リストで、テストするプロパティの PropPut メソッドを選択します。

1. 変更、**パラメーター値**または**パラメーターの型** をクリックし、**値の設定**ボタンをクリックします。

1. クリックして**Invoke**オブジェクトに新しい値を適用します。

   これで、プロパティには、新しい値が含まれています。

#### <a name="to-test-events-and-specify-the-destination-of-event-information"></a>イベントをテストし、イベント情報の出力先を指定します。

1. **オプション** メニューのをクリックして**ログ**します。

1. イベント情報の出力先を指定します。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[方法: ActiveX コントロールをデバッグする](/visualstudio/debugger/how-to-debug-an-activex-control)
