---
title: ツリー コントロールの使い方
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
ms.openlocfilehash: 9cff48018d728ef9578be38c0d94300011265fa1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411449"
---
# <a name="using-tree-controls"></a>ツリー コントロールの使い方

ツリー コントロールの一般的な使用方法 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 次のパターンします。

- コントロールが作成されます。 コントロールがダイアログ ボックスのテンプレートで指定されている場合、または使用する場合`CTreeView`、ダイアログ ボックスまたはビューの作成時に、作成は自動です。 その他のいくつかのウィンドウの子ウィンドウとしてツリーのコントロールを作成する場合を使用して、[作成](../mfc/reference/ctreectrl-class.md#create)メンバー関数。

- ツリー コントロールのイメージを使用する場合は、イメージ リストを呼び出すことによって設定[SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist)します。 呼び出すことによって、インデントを変更することもできます。 [SetIndent](../mfc/reference/ctreectrl-class.md#setindent)します。 これを行う適切な時刻が[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (用ダイアログ ボックスのコントロール) または[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) (ビュー) の。

- データを呼び出すことによって、コントロールを配置、`CTreeCtrl`の[InsertItem](../mfc/reference/ctreectrl-class.md#insertitem)データ項目ごとに 1 回の関数。 `InsertItem` 子項目を追加する場合など後で、それを参照する際の項目にハンドルを返します。 データを初期化するために適切な時刻が`OnInitDialog`(用ダイアログ ボックスのコントロール) または`OnInitialUpdate`(ビュー) の。

- ユーザー コントロールと対話をさまざまな通知メッセージを送信します。 各コントロール ウィンドウのメッセージ マップで、ON_NOTIFY_REFLECT マクロを追加するか、ON_NOTIFY マクロを親ウィンドウのメッセージ マップに追加することで処理するメッセージを処理する関数を指定することができます。 参照してください[ツリー コントロールの通知メッセージ](../mfc/tree-control-notification-messages.md)可能な通知の一覧については、このトピックで後述します。

- コントロールの値を設定するさまざまなセットのメンバー関数を呼び出します。 実行できる変更には、インデントを設定し、テキスト、画像、または項目に関連付けられているデータの変更が含まれます。

- コントロールの内容を調べるには、さまざまな Get 関数を使用します。 親、子、および指定した項目の兄弟にハンドルを取得するための関数で、ツリー コントロールの内容を走査することもできます。 特定のノードの子を並べ替えることもできます。

- コントロールに完了したらが適切に破棄されることを確認します。 ツリー コントロールがダイアログ ボックスの場合、またはビューである場合に、`CTreeCtrl`オブジェクトが自動的に破棄されます。 かどうか、する必要があることに、両方のコントロールを確認し、`CTreeCtrl`オブジェクトが破棄されました。

## <a name="see-also"></a>関連項目

[CTreeCtrl の使い方](../mfc/using-ctreectrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
