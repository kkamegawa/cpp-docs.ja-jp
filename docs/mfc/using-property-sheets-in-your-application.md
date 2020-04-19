---
title: アプリケーションでのプロパティ シートの使用
ms.date: 11/04/2016
helpviewer_keywords:
- dialog templates [MFC], property sheets
- dialog resources
- property pages [MFC], property sheets
- DoModal method property sheets
- AddPage method [MFC]
- property sheets, about property sheets
- Create method [MFC], property sheets
- CPropertyPage class [MFC], styles
ms.assetid: 240654d4-152b-4e3f-af7b-44234339206e
ms.openlocfilehash: 4fd68f57db082ab0b0da0e8248e0be239c63c99a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411527"
---
# <a name="using-property-sheets-in-your-application"></a>アプリケーションでのプロパティ シートの使用

プロパティ シートをアプリケーションで使用するには、次の手順を完了します。

1. 各プロパティ ページのダイアログ テンプレート リソースを作成します。 ユーザー切り替えて使用する 1 つのページから、各レイアウト ページできるだけ一貫性を保つため、注意してください。

   すべてのページのダイアログ テンプレートは同じサイズではありません。 フレームワークでは、最大のページのサイズを使用して、プロパティ ページのプロパティ シートで割り当てる領域の量を決定します。

   プロパティ ページのダイアログ テンプレート リソースを作成するときに、ダイアログのプロパティのプロパティ シートで、次のスタイルを指定する必要があります。

   - 設定、**キャプション**で編集ボックス、**全般**をこのページのタブに表示するテキスト ページ。

   - 設定、**スタイル**でリスト ボックス、**スタイル**へのページング**子**します。

   - 設定、**境界線**でリスト ボックス、**スタイル**へのページング**Thin**します。

   - いることを確認、 **Titlebar**チェック ボックスをオン、**スタイル**ページが選択されています。

   - いることを確認、**無効になっている**チェック ボックスをオン、**スタイルより**ページが選択されています。

1. 作成、 [CPropertyPage](../mfc/reference/cpropertypage-class.md)-プロパティ ページ ダイアログの各テンプレートに対応するクラスを派生します。 参照してください[クラスの追加](../ide/adding-a-class-visual-cpp.md)します。 選択`CPropertyPage`基底クラスとして。

1. このプロパティ ページの値を保持する変数のメンバーを作成します。 プロパティ ページにメンバー変数を追加するプロセスは、プロパティ ページが特別なダイアログ ボックスであるため正確に ダイアログ ボックスでは、メンバー変数を追加すると同じです。 詳細については、次を参照してください。[ダイアログ コントロールのメンバー変数を定義する](../windows/defining-member-variables-for-dialog-controls.md)します。

1. 構築、 [CPropertySheet](../mfc/reference/cpropertysheet-class.md)ソース コード内のオブジェクト。 通常、構築、`CPropertySheet`プロパティ シートを表示するコマンドのハンドラー内のオブジェクト。 このオブジェクトは、プロパティ シート全体を表します。 持つモーダル プロパティ シートを作成する場合、 [DoModal](../mfc/reference/cpropertysheet-class.md#domodal)関数、フレームワークは、既定で 3 つのコマンド ボタンを提供します。[Ok] をキャンセルし、適用します。 フレームワークにはコマンド ボタン作成なしで作成したモードレス プロパティ シートの[作成](../mfc/reference/cpropertysheet-class.md#create)関数。 クラスを派生する必要はありません`CPropertySheet`(プレビュー ウィンドウ) などの他のコントロールを追加するか、モードレス プロパティ シートを表示する場合を除き、します。 プロパティ シートを閉じてするために使用する既定のコントロールが含まれていないために、この手順はモードレス プロパティ シートの必要があります。

1. プロパティ シートに追加するには、各ページには、次の操作を行います。

   - ごとに 1 つのオブジェクトを構築`CPropertyPage`-このプロセスで以前に作成したクラスを派生します。

   - 呼び出す[が](../mfc/reference/cpropertysheet-class.md#addpage)ページごとにします。

   通常、オブジェクトを作成する、`CPropertySheet`も作成、`CPropertyPage`この手順内のオブジェクト。 ただし、実装する場合、 `CPropertySheet`-派生クラスで埋め込むことができます、`CPropertyPage`内のオブジェクト、`CPropertySheet`オブジェクトと呼び出し`AddPage`からページごとに、 `CPropertySheet`-派生したクラスのコンス トラクター。 `AddPage` 追加、`CPropertyPage`オブジェクトのページのプロパティ シートの一覧には、そのページは、ウィンドウを実際には作成されません。 そのため、ウィンドウの作成、プロパティ シートを呼び出すまで待機する必要はありません`AddPage`; 呼び出せる`AddPage`プロパティ シートのコンス トラクターから。

   既定では、プロパティ シートのプロパティ シートで、1 行に収まらないのタブがある場合、タブは複数の行に積み重ねられます。 重なりを無効にする[CPropertySheet::EnableStackedTabs](../mfc/reference/cpropertysheet-class.md#enablestackedtabs)パラメーターを設定して**FALSE**します。 呼び出す必要があります`EnableStackedTabs`プロパティ シートを作成する場合。

1. 呼び出す[する](../mfc/reference/cpropertysheet-class.md#domodal)または[作成](../mfc/reference/cpropertysheet-class.md#create)プロパティ シートを表示します。 呼び出す`DoModal`モーダル ダイアログ ボックスのプロパティ シートを作成します。 呼び出す**作成**モードレス ダイアログ ボックスのプロパティ シートを作成します。

1. プロパティ ページとプロパティ シートの所有者間でデータを交換します。 これは、情報の記事で説明[データの交換](../mfc/exchanging-data.md)します。

プロパティ シートを使用する方法の例は、MFC 標準サンプルを参照してください。 [PROPDLG](../overview/visual-cpp-samples.md)します。

## <a name="see-also"></a>関連項目

[プロパティ シート](../mfc/property-sheets-mfc.md)
