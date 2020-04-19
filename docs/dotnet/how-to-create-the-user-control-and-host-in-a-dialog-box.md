---
title: '方法: ダイアログ ボックスで、ユーザー コントロールとホストを作成します。'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: 03a53032-2f03-4fa2-b567-031615a26011
ms.openlocfilehash: bdf7e2f4961a16e6538c7bbcc690ef44ba87fcaf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378971"
---
# <a name="how-to-create-the-user-control-and-host-in-a-dialog-box"></a>方法: ダイアログ ボックスで、ユーザー コントロールとホストを作成します。

この記事の手順では、ダイアログ ベースを作成することを想定しています ([CDialog クラス](../mfc/reference/cdialog-class.md))、Microsoft Foundation Classes (MFC) プロジェクトもにサポートを追加する Windows フォーム コントロールの既存の MFC ダイアログ ボックス。

### <a name="to-create-the-net-user-control"></a>.NET ユーザー コントロールを作成するには

1. という名前の Visual c# Windows フォーム コントロール ライブラリ プロジェクトを作成する`WindowsFormsControlLibrary1`します。

   **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。 **Visual c#** フォルダーで、 **Windows フォーム コントロール ライブラリ**します。

   受け入れる、`WindowsFormsControlLibrary1`プロジェクト名をクリックして**OK**します。

   既定では、.NET コントロールの名前は `UserControl1` です。

1. `UserControl1` に子コントロールを追加します。

   **ツールボックス**、オープン、**すべての Windows フォーム**一覧。 ドラッグ、**ボタン**への制御、`UserControl1`デザイン サーフェイス。

   追加することも、 **TextBox**コントロール。

1. **ソリューション エクスプ ローラー**、ダブルクリックして**UserControl1.Designer.cs**編集用に開きます。 TextBox および Button の説明を `private` から `public` に変更します。

1. プロジェクトをビルドします。

   **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

### <a name="to-create-the-mfc-host-application"></a>MFC ホスト アプリケーションを作成するには

1. MFC アプリケーション プロジェクトを作成します。

   **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。 **Visual C**フォルダーで、 **MFC アプリケーション**します。

   **[名前]** ボックスに「 `MFC01`」と入力します。 ソリューションの設定を変更する**ソリューションに追加**します。 **[OK]** をクリックします。

   **MFC アプリケーション ウィザード**、アプリケーションの種類を選択**ダイアログ ベース**します。 残りの既定の設定をそのまま使用し、をクリックして**完了**します。 これにより、MFC ダイアログ ボックスを伴った MFC アプリケーションが作成されます。

1. MFC ダイアログ ボックスに Placeholder コントロールを追加します。

   **ビュー**  メニューのをクリックして**リソース ビュー**します。 **リソース ビュー**、展開、**ダイアログ**フォルダーをダブルクリックします`IDD_MFC01_DIALOG`します。 ダイアログ リソースが表示される**リソース エディター**します。

   **ツールボックス**、オープン、**ダイアログ エディター**一覧。 ドラッグ、**静的テキスト**ダイアログ リソースを制御します。 **静的テキスト**コントロールは、.NET Windows フォーム コントロールのプレース ホルダーとして機能します。 コントロールのサイズが Windows フォーム コントロールとほぼ同じサイズになるように調整します。

   **プロパティ**ウィンドウで、変更、 **ID**の**静的テキスト**に制御を`IDC_CTRL1`を変更して、 **TabStop**プロパティを**True**します。

1. 共通言語ランタイム (CLR: Common Language Runtime) に対するサポートをプロジェクトに構成します。

   **ソリューション エクスプ ローラー**MFC01 プロジェクト ノードを右クリックし、クリックして**プロパティ**します。

   **プロパティ ページ**ダイアログ ボックスで、**構成プロパティ**を選択します**全般**します。 **プロジェクトの既定値**セクションで、設定**共通言語ランタイム サポート**に**共通言語ランタイム サポート (/clr)** します。

   **構成プロパティ**、展開**C/C++** を選択し、**全般**ノード。 設定**デバッグ情報の形式**に**プログラム データベース (/Zi)** します。

   選択、**コード生成**ノード。 設定**最小リビルドを有効にする**に**いいえ (/Gm-)** します。 設定**基本ランタイム チェック**に**既定**します。

   クリックして**OK**変更を適用します。

1. .NET コントロールへの参照を追加します。

   **ソリューション エクスプ ローラー**mfc01] プロジェクト ノードを右クリックし、[クリックして**追加**、**参照**します。 **プロパティ ページ**、 をクリックして**新しい参照の追加**を選択します**WindowsFormsControlLibrary1** (下、**プロジェクト** タブ)、をクリック**OK**します。 形式での参照が追加されます、 [/FU](../build/reference/fu-name-forced-hash-using-file.md)コンパイラ オプションのプログラムをコンパイルできるようにします。 また、プログラムを実行するために、WindowsFormsControlLibrary1.dll が \MFC01\ プロジェクト フォルダーにコピーされます。

1. Stdafx.h で次の行を見つけます。

    ```
    #endif // _AFX_NO_AFXCMN_SUPPORT
    ```

   その上に次の行を追加します。

    ```
    #include <afxwinforms.h>   // MFC Windows Forms support
    ```

1. マネージド コントロールを作成するためのコードを追加します。

   最初に、マネージド コントロールを宣言します。 MFC01Dlg.h でダイアログ クラスの宣言に移動し、Protected のスコープにユーザー コントロールのデータ メンバーを次のように追加します。

    ```
    class CMFC01Dlg : public CDialog
    {
       // ...
       // Data member for the .NET User Control:
       CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_ctrl1;
    ```

   次に、マネージド コントロールの実装を提供します。 MFC01Dlg.cpp の、MFC アプリケーション ウィザードによって生成された `CMFC01Dlg::DoDataExchange` のダイアログ オーバーライド (同一ファイルの `CAboutDlg::DoDataExchange` ではなく) に次のコードを追加して、マネージド コントロールを作成し、静的なプレースホルダー IDC_CTRL1 に関連付けます。

    ```
    void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
    {
       CDialog::DoDataExchange(pDX);
       DDX_ManagedControl(pDX, IDC_CTRL1, m_ctrl1);
    }
    ```

1. プロジェクトをビルドして実行します。

   **ソリューション エクスプ ローラー**、右クリックして**MFC01**順にクリックします**スタートアップ プロジェクトとして設定**します。

   **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

   **デバッグ** メニューのをクリックして**デバッグなしで開始**します。 MFC ダイアログ ボックスに Windows フォーム コントロールが表示されます。

## <a name="see-also"></a>関連項目

[MFC ダイアログ ボックスにおける Windows フォーム ユーザー コントロールのホスト](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)
