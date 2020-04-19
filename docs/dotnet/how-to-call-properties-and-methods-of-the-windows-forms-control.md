---
title: '方法: Windows フォームの呼び出しのプロパティとメソッドの制御'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- method calls, Windows Forms
- calling methods, Windows Forms control
- calling properties, Windows Forms control
- Windows Forms controls [C++], methods
- calling properties
- Windows Forms controls [C++], properties
ms.assetid: 6e647d8a-fdaa-4aa1-b3fe-04f15cff8eb3
ms.openlocfilehash: 61b565839b3f3c24670819fdcf2dde558e3461ac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152814"
---
# <a name="how-to-call-properties-and-methods-of-the-windows-forms-control"></a>方法: Windows フォームの呼び出しのプロパティとメソッドの制御

[CWinFormsView::GetControl](../mfc/reference/cwinformsview-class.md#getcontrol)へのポインターを返します<xref:System.Windows.Forms.Control?displayProperty=fullName>へのポインターではない`WindowsControlLibrary1::UserControl1`、ユーザー コントロールの型のメンバーを追加で、初期化することをお勧め[IView::OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate). メソッドとプロパティを使用してを呼び出すことができますので`m_ViewControl`します。

このトピックでは、完了していた前提としています。[方法。ユーザー コントロールおよびホストを作成 ダイアログ ボックスで](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)と[方法。ユーザー コントロールおよびホスト MDI ビューを作成する](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)します。

### <a name="to-create-the-mfc-host-application"></a>MFC ホスト アプリケーションを作成するには

1. 作成した MFC アプリケーションを開く[方法。ユーザー コントロールおよびホスト MDI ビューを作成する](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)します。

1. オーバーライドのパブリック セクションに次の行を追加、`CMFC02View`クラス MFC02View.h で宣言します。

   `gcroot<WindowsFormsControlLibrary1::UserControl1 ^> m_ViewControl;`

1. フィルターと並べ替え順序の上書きを追加します。

   表示、**プロパティ**ウィンドウ (F4)。 **クラス ビュー** (CTRL + SHIFT + C)、CMFC02View クラスを選択します。 **プロパティ**ウィンドウで、上書きのアイコンを選択します。 フィルターと並べ替え順序を一覧の下にスクロールします。 ドロップダウン リストからをクリックして\<追加 >。 MFC02View.cpp で。 OnInitialUpdate 関数の本体は、次のようにすることを確認します。

    ```
    CWinFormsView::OnInitialUpdate();
    m_ViewControl = safe_cast<WindowsFormsControlLibrary1::UserControl1 ^>(this->GetControl());
    m_ViewControl->textBox1->Text = gcnew System::String("hi");
    ```

1. プロジェクトをビルドして実行します。

   **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

   **デバッグ** メニューのをクリックして**デバッグなしで開始**します。

   テキスト ボックスが現在初期化されていることに注意してください。

## <a name="see-also"></a>関連項目

[MFC ビューとしての Windows フォーム ユーザー コントロールのホスト](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)
