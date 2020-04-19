---
title: 'チュートリアル: MFC Scribble アプリケーション (第 2 部) の更新'
ms.date: 04/25/2019
helpviewer_keywords:
- walkthroughs [MFC]
ms.assetid: 602df5c2-17d4-4cd9-8cf6-dff652c4cae5
ms.openlocfilehash: d4655c0a4a8847642b75575e324a291e39bbf42a
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64558169"
---
# <a name="walkthrough-updating-the-mfc-scribble-application-part-2"></a>チュートリアル: MFC Scribble アプリケーション (第 2 部) の更新

[第 1 部](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)クラシックに、Office Fluent リボンを追加する方法を説明しました。 このチュートリアルの Scribble アプリケーション。 この部分は、リボン パネルとユーザーがメニューとコマンドの代わりに使用できるコントロールを追加する方法を示します。

## <a name="prerequisites"></a>必須コンポーネント

[Visual C++ のサンプル](../overview/visual-cpp-samples.md)

##  <a name="top"></a> セクション

このパートは、次のセクションで構成されています。

- [新しいパネルをリボンに追加します。](#addnewpanel)

- [ヘルプ パネルをリボンに追加します。](#addhelppanel)

- [ペン パネルをリボンに追加します。](#addpenpanel)

- [カラー ボタンをリボンに追加します。](#addcolorbutton)

- [ドキュメント クラスへの色のメンバーの追加](#addcolormember)

- [初期化と環境設定の保存](#initpensave)

##  <a name="addnewpanel"></a> 新しいパネルをリボンに追加します。

次の手順は、追加する方法を示す、**ビュー**ツールバーとステータス バーの可視性を制御する 2 つのチェック ボックスを格納しているパネルとも、**ウィンドウ**を垂直方向の分割を含むパネル作成とのマルチ ドキュメント インターフェイス (MDI) ウィンドウの配置を制御するボタン。

### <a name="to-add-a-view-panel-and-window-panel-to-the-ribbon-bar"></a>ビュー-パネルとパネルのウィンドウ、リボン バーを追加するには

1. という名前のパネルを作成`View`、ステータス バーとツールバーを切り替える 2 つのチェック ボックスを持ちます。

   1. **ツールボックス**、ドラッグ、**パネル**を**ホーム**カテゴリ。 2 つをドラッグ**チェック ボックス**パネル。

   1. そのプロパティを変更するパネルをクリックします。 変更**キャプション**に`View`します。

   1. そのプロパティを変更するのには、最初のチェック ボックスをクリックします。 変更**ID**に`ID_VIEW_TOOLBAR`と**キャプション**に`Toolbar`します。

   1. そのプロパティを変更する 2 つ目のチェック ボックスをクリックします。 変更**ID**に`ID_VIEW_STATUS_BAR`と**キャプション**に`Status Bar`します。

1. という名前のパネルを作成`Window`分割ボタンを持ちます。 ユーザーには、分割ボタンがクリックすると、ショートカット メニューには、Scribble アプリケーションで既に定義されている 3 つのコマンドが表示されます。

   1. **ツールボックス**、ドラッグ、**パネル**を**ホーム**カテゴリ。 ドラッグし、**ボタン**パネル。

   1. そのプロパティを変更するパネルをクリックします。 変更**キャプション**に`Window`します。

   1. ボタンをクリックします。 変更**キャプション**に`Windows`、**キー**に`w`、**大きいイメージ インデックス**に`1`、および**分割モード**`False`します。 省略記号をクリックします (**.**) 横に**メニュー項目**を開く、**項目エディター**  ダイアログ ボックス。

   1. クリックして**追加**3 回の 3 つのボタンを追加します。

   1. 最初のボタンをクリックし、変更**キャプション**に`New Window`、および**ID**に`ID_WINDOW_NEW`します。

   1. 2 番目のボタンをクリックし、変更**キャプション**に`Cascade`、および**ID**に`ID_WINDOW_CASCADE`します。

   1. 3 番目のボタンをクリックし、変更**キャプション**に`Tile`、および**ID**に`ID_WINDOW_TILE_HORZ`します。

1. 変更内容を保存し、アプリケーションをビルドして実行します。 **ビュー**と**ウィンドウ**パネルを表示する必要があります。 正しく機能することを確認するためのボタンをクリックします。

##  <a name="addhelppanel"></a> ヘルプ パネルをリボンに追加します。

という名前のリボン ボタンに Scribble アプリケーションで定義されている 2 つのメニュー項目を割り当てることができます、**ヘルプ トピック**と**について Scribble**します。 という名前の新しいパネルにボタンが追加されます**ヘルプ**します。

### <a name="to-add-a-help-panel"></a>ヘルプ パネルを追加するには

1. **ツールボックス**、ドラッグ、**パネル**を**ホーム**カテゴリ。 2 つをドラッグ**ボタン**パネル。

1. そのプロパティを変更するパネルをクリックします。 変更**キャプション**に`Help`します。

1. 最初のボタンをクリックします。 変更**キャプション**に`Help Topics`、および**ID**に`ID_HELP_FINDER`します。

1. 2 番目のボタンをクリックします。 変更**キャプション**に`About Scribble...`、および**ID**に`ID_APP_ABOUT`します。

1. 変更内容を保存し、アプリケーションをビルドして実行します。 A**ヘルプ**を 2 つのリボン ボタンを含むパネルを表示する必要があります。

   > [!IMPORTANT]
   > クリックすると、**ヘルプ トピック**ボタン、Scribble アプリケーションは、という名前の圧縮 (.chm) の HTML ヘルプ ファイルを開きます*your_project_name*.chm。 その結果、プロジェクトが Scribble に名前がない場合、プロジェクトの名前に、ヘルプ ファイルの名前を変更する必要があります。

##  <a name="addpenpanel"></a> ペン パネルをリボンに追加します。

太さ、ペンの色を制御するボタンを表示するパネルを追加します。 このパネルには、シックとシン ペン間を切り替えるチェック ボックスが含まれています。 その機能に似ていますが、**太線**Scribble アプリケーションのメニュー項目。

元の Scribble アプリケーションで、ユーザーがクリックしたときに表示されるダイアログ ボックスからペンの太さを選択します。 ユーザー**ペンの太さ**メニュー。 リボン バーには、新しいコントロールの十分な余裕があるために、リボンの 2 つのコンボ ボックスを使用して、ダイアログ ボックスを置き換えることができます。 1 つのコンボ ボックスは、細いペンの幅を調整し、他のコンボ ボックスが太い線の幅を調整します。

#### <a name="to-add-a-pen-panel-and-combo-boxes-to-the-ribbon"></a>ペンのパネルとコンボ ボックスをリボンに追加するには

1. **ツールボックス**、ドラッグ、**パネル**を**ホーム**カテゴリ。 ドラッグし、 **チェック ボックス** と 2 つ **コンボ ボックス** パネル。

1. そのプロパティを変更するパネルをクリックします。 変更**キャプション**に`Pen`します。

1. チェック ボックスをクリックします。 変更**キャプション**に`Use Thick`、および**ID**に`ID_PEN_THICK_OR_THIN`します。

1. 最初のコンボ ボックスをクリックします。 変更**キャプション**に`Thin Pen`、 **ID**に`ID_PEN_THIN_WIDTH`、**型**に`Drop List`、**データ**に`1;2;3;4;5;6;7;8;9;`、**テキスト**に`2`します。

1. 2 つ目のコンボ ボックスをクリックします。 変更**キャプション**に`Thick Pen`、 **ID**に`ID_PEN_THICK_WIDTH`、**型**に`Drop List`、**データ**に`5;6;7;8;9;10;11;12;13;14;15;16;17;18;19;20;`、**テキスト**に`5`します。

1. 新しいコンボ ボックスはすべて既存のメニュー項目に対応していないため、ペンのオプションをすべてのメニュー項目を作成する必要があります。

   1. **リソース ビュー**ウィンドウを開いて、 **IDR_SCRIBBTYPE**メニュー リソース。

   1. クリックして**ペン**ペン メニューを開きます。 クリックして**ここへ入力**と種類`Thi&n Pen`します。

   1. 開くように入力したテキストを右クリックし、**プロパティ**ウィンドウで、し、変更、ID プロパティを`ID_PEN_THIN_WIDTH`します。

   1. すべてのペン メニュー項目のイベント ハンドラーを作成します。 右クリックし、**足りないと n のペン**メニュー項目を作成し、をクリックし、**イベント ハンドラーの追加**します。 **イベント ハンドラー ウィザード**が表示されます。

   1. **クラス リスト**ウィザードで、選択ボックス**CScribbleDoc**順にクリックします**の追加し、編集**します。 名前付きイベント ハンドラーを作成するコマンドを`CScribbleDoc::OnPenThinWidth`します。

   1. `CScribbleDoc::OnPenThinWidth` に次のコードを追加します。

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        // Get a pointer to the Thin Width combo box
        CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
        CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THIN_WIDTH));

        //Get the selected value
        int nCurSel = pThinComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThinWidth = atoi(CStringA(pThinComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. 次に、メニュー項目とイベントのハンドラーの太さのペンを作成します。

   1. **リソース ビュー**ウィンドウを開いて、 **IDR_SCRIBBTYPE**メニュー リソース。

   1. クリックして**ペン**ペン メニューを開きます。 クリックして**ここへ入力**と種類`Thic&k Pen`します。

   1. 表示するように入力したテキストを右クリックし、**プロパティ**ウィンドウ。 ID プロパティを変更`ID_PEN_THICK_WIDTH`します。

   1. 右クリックし、**太さのペン**メニュー項目を作成し、をクリックし、**イベント ハンドラーの追加**します。 **イベント ハンドラー ウィザード**が表示されます。

   1. **クラス リスト**ボックス、ウィザードの**CScribbleDoc**順にクリックします**の追加し、編集**します。 名前付きイベント ハンドラーを作成するコマンドを`CScribbleDoc::OnPenThickWidth`します。

   1. `CScribbleDoc::OnPenThickWidth` に次のコードを追加します。

        ```cpp
        // Get a pointer to the ribbon bar
        CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx *) AfxGetMainWnd())->GetRibbonBar();
        ASSERT_VALID(pRibbon);

        CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
            CMFCRibbonComboBox, pRibbon->FindByID(ID_PEN_THICK_WIDTH));
        // Get the selected value
        int nCurSel = pThickComboBox->GetCurSel();
        if (nCurSel>= 0)
        {
            m_nThickWidth = atoi(CStringA(pThickComboBox->GetItem(nCurSel)));
        }

        // Create a new pen using the selected width
        ReplacePen();
        ```

1. 変更内容を保存し、アプリケーションをビルドして実行します。 新しいボタンとコンボ ボックスが表示されます。 Scribble を別のペンの幅を使用してください。

##  <a name="addcolorbutton"></a> ペンのパネルにカラー ボタンの追加

次に、追加、 [CMFCRibbonColorButton](../mfc/reference/cmfcribboncolorbutton-class.md)できるように、ユーザー オブジェクトの色で scribble します。

### <a name="to-add-a-color-button-to-the-pen-panel"></a>ペンのパネルにカラー ボタンを追加するには

1. 色のボタンを追加する前に、そのメニュー項目を作成します。 **リソース ビュー**ウィンドウを開いて、 **IDR_SCRIBBTYPE**メニュー リソース。 をクリックして、**ペン**メニュー項目を [ペン] メニューを開きます。 クリックして**ここへ入力**と種類`&Color`します。 表示するように入力したテキストを右クリックし、**プロパティ**ウィンドウ。 ID を `ID_PEN_COLOR`に変更します。

1. 色のボタンを追加します。 **ツールボックス**、ドラッグ、**カラー ボタン**を**ペン**パネル。

1. 色のボタンをクリックします。 変更**キャプション**に`Color`、 **ID**に`ID_PEN_COLOR`、 **Simple Look**に`True`、**大きいイメージ インデックス**に`1`、および**分割モード**に`False`します。

1. 変更内容を保存し、アプリケーションをビルドして実行します。 新しい色のボタンを表示するか、**ペン**パネル。 ただし、イベント ハンドラーがまだないために、このことを使用できません。 次の手順では、色のボタンのイベント ハンドラーを追加する方法を示します。

##  <a name="addcolormember"></a> ドキュメント クラスへの色のメンバーの追加

元の Scribble アプリケーションには、ペンの色が割り当てられていない、ために、それらの実装を記述する必要があります。 ドキュメント クラスに新しいメンバーを追加、ドキュメントのペンの色を格納する`CscribbleDoc`します。

### <a name="to-add-a-color-member-to-the-document-class"></a>ドキュメント クラスに色のメンバーを追加するには

1. Scribdoc.h、内で、`CScribbleDoc`クラス、検索、`// Attributes`セクション。 定義の後に次のコード行を追加、`m_nThickWidth`データ メンバー。

   ```cpp
   // Current pen color
   COLORREF m_penColor;
   ```

1. 各ドキュメントの一覧には、ユーザーが既に描画するストロークします。 すべてのストロークがによって定義されている、`CStroke`オブジェクト。 `CStroke`クラスは、ペンの色に関する情報を含まれないため、クラスを変更する必要があります。 Scribdoc.h、内で、`CStroke`クラスでの定義の後に次のコード行を追加、`m_nPenWidth`データ メンバー。

   ```cpp
   // Pen color for the stroke
   COLORREF m_penColor;
   ```

1. Scribdoc.h で追加する新しい`CStroke`コンス トラクターのパラメーターを持つは、幅と色を指定します。 次の後のコード行を追加、`CStroke(UINT nPenWidth);`ステートメント。

   ```cpp
   CStroke(UINT nPenWidth, COLORREF penColor);
   ```

1. Scribdoc.cpp での新しい実装を追加`CStroke`コンス トラクター。 実装後、次のコードを追加、`CStroke::CStroke(UINT nPenWidth)`コンス トラクター。

   ```cpp
   // Constructor that uses the document's current width and color
   CStroke::CStroke(UINT nPenWidth, COLORREF penColor)
   {
       m_nPenWidth = nPenWidth;
       m_penColor = penColor;
       m_rectBounding.SetRectEmpty();
   }
   ```

1. 2 行目を変更、`CStroke::DrawStroke`メソッドとして、次のとおりです。

   ```cpp
   if (!penStroke.CreatePen(PS_SOLID, m_nPenWidth, m_penColor))
   ```

1. ドキュメント クラスの既定のペンの色を設定します。 Scribdoc.cpp、次の行を追加`CScribbleDoc::InitDocument`後に、`m_nThickWidth = 5;`ステートメント。

   ```cpp
   // default pen color is black
   m_penColor = RGB(0, 0, 0);
   ```

1. Scribdoc.cpp での最初の行を変更する、`CScribbleDoc::NewStroke`次のメソッド。

   ```cpp
   CStroke* pStrokeItem = new CStroke(m_nPenWidth, m_penColor);
   ```

1. 最後の行の変更、`CScribbleDoc::ReplacePen`次のメソッド。

   ```cpp
   m_penCur.CreatePen(PS_SOLID, m_nPenWidth, m_penColor);
   ```

1. 追加した、`m_penColor`前の手順でのメンバー。 ここで、メンバーを設定する色のボタンのイベント ハンドラーを作成します。

   1. **リソース ビュー**ウィンドウ、IDR_SCRIBBTYPE メニュー リソースを開きます。

   1. 右クリックし、**色**メニュー項目をクリックします**イベント ハンドラーの追加**します。 **イベント ハンドラー ウィザード**が表示されます。

   1. **クラス リスト**ウィザードで、選択ボックス**CScribbleDoc**順にクリックします、**の追加し、編集**ボタンをクリックします。 コマンドは、作成、`CScribbleDoc::OnPenColor`イベント ハンドラーのスタブ。

1. スタブを置換、`CScribbleDoc::OnPenColor`イベント ハンドラーを次のコード。

   ```cpp
   void CScribbleDoc::OnPenColor()
   {
       // Change pen color to reflect color button's current selection
       CMFCRibbonBar* pRibbon = ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
       ASSERT_VALID(pRibbon);

       CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
           CMFCRibbonColorButton, pRibbon->FindByID(ID_PEN_COLOR));

       m_penColor = pColorBtn->GetColor();
       // Create new pen using the selected color
       ReplacePen();
   }
   ```

1. 変更を保存し、アプリケーションをビルドして実行します。 色のボタンを押し、ペンの色を変更することができますようになりました。

##  <a name="initpensave"></a> 初期化と環境設定の保存

次に、色とペンの幅を初期化します。 最後に、保存して、色の描画をファイルから読み込みます。

### <a name="to-initialize-controls-on-the-ribbon-bar"></a>リボン バーのコントロールを初期化するには

1. リボン バーでペンを初期化します。

   Scribdoc.cpp に次のコードを追加、`CScribbleDoc::InitDocument`メソッド後に、`m_sizeDoc = CSize(200,200)`ステートメント。

   ```cpp
   // Reset the ribbon UI to its initial values
   CMFCRibbonBar* pRibbon =
       ((CMDIFrameWndEx*) AfxGetMainWnd())->GetRibbonBar();
   ASSERT_VALID(pRibbon);

   CMFCRibbonColorButton* pColorBtn = DYNAMIC_DOWNCAST(
       CMFCRibbonColorButton,
       pRibbon->FindByID(ID_PEN_COLOR));

   // Set ColorButton to black
   pColorBtn->SetColor(RGB(0, 0, 0));

   CMFCRibbonComboBox* pThinComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THIN_WIDTH));

   // Set Thin pen combobox to 2
   pThinComboBox->SelectItem(1);

   CMFCRibbonComboBox* pThickComboBox = DYNAMIC_DOWNCAST(
       CMFCRibbonComboBox,
       pRibbon->FindByID(ID_PEN_THICK_WIDTH));

   // Set Thick pen combobox to 5
   pThickComboBox->SelectItem(0);
   ```

1. 色の描画をファイルに保存します。 Scribdoc.cpp には、次のステートメントを追加、`CStroke::Serialize`メソッド後に、`ar << (WORD)m_nPenWidth;`ステートメント。

   ```cpp
   ar << (COLORREF)m_penColor;
   ```

1. 最後に、ファイルから描画する色を読み込みます。 次のコード行を追加、`CStroke::Serialize`メソッド後に、`m_nPenWidth = w;`ステートメント。

   ```cpp
   ar >> m_penColor;
   ```

1. 今すぐ scribble の色でし、ファイルに図面を保存します。

## <a name="conclusion"></a>まとめ

MFC Scribble アプリケーションを更新しました。 既存のアプリケーションを変更するときに、このチュートリアルをガイドとして使用します。

## <a name="see-also"></a>関連項目

[チュートリアル](../mfc/walkthroughs-mfc.md)<br/>
[チュートリアル: MFC Scribble アプリケーションの更新 (パート 1)](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)
