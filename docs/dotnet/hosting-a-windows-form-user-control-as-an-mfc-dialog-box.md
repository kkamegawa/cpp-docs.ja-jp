---
title: MFC ダイアログ ボックスとしての Windows フォーム ユーザー コントロールのホスト
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 4c4ee8c8b4570b598ba20b3bd5e1cf4c706ee885
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222950"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>MFC ダイアログ ボックスとしての Windows フォーム ユーザー コントロールのホスト

MFC は、テンプレート クラスを提供します。 [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md)する Windows フォーム ユーザー コントロールをホストできるように (<xref:System.Windows.Forms.UserControl>) モーダルまたはモードレスの MFC ダイアログ ボックスでします。 `CWinFormsDialog` MFC クラスから派生[CDialog](../mfc/reference/cdialog-class.md)ので、ダイアログ ボックスをモーダルまたはモードレスとして起動することができます。

プロセスを`CWinFormsDialog`ユーザー コントロールをホストするために使用が記載されているに似ています。 [MFC ダイアログ ボックスでは、Windows フォーム ユーザー コントロールをホストしている](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md)します。 ただし、`CWinFormsDialog` は、ユーザー コントロールの初期化およびホストを管理するため、手動でプログラムを作成する必要はありません。

Windows フォームと MFC を示すサンプル アプリケーションの場合、次を参照してください。 [MFC と Windows フォーム統合](http://www.microsoft.com/downloads/details.aspx?FamilyID=987021bc-e575-4fe3-baa9-15aa50b0f599&displaylang=en)します。

### <a name="to-create-the-mfc-host-application"></a>MFC ホスト アプリケーションを作成するには

1. MFC アプリケーション プロジェクトを作成します。

   **ファイル**メニューの [**新規**、] をクリックし、**プロジェクト**します。 **Visual C**フォルダーで、 **MFC アプリケーション**します。

   **名前**ボックスに、入力`MFC03`ソリューションの設定を変更および**ソリューションに追加**します。クリックして**OK**します。

   **MFC アプリケーション ウィザード**すべての既定値をそのまま使用し、クリックして**完了**します。 これにより、マルチ ドキュメント インターフェイスを持つ MFC アプリケーションが作成されます。

1. プロジェクトを構成します。

   **ソリューション エクスプ ローラー**を右クリックし、 **MFC03**プロジェクト ノード、**プロパティ**します。 **プロパティ ページ** ダイアログ ボックスが表示されます。

   **プロパティ ページ** ダイアログ ボックスで、**構成プロパティ**ツリー コントロールで、**全般**、次に、**プロジェクトの既定値**セクションで、設定**共通言語ランタイム サポート**に**共通言語ランタイム サポート (/clr)** します。 **[OK]** をクリックします。

1. .NET コントロールへの参照を追加します。

   **ソリューション エクスプ ローラー**を右クリックし、 **MFC03**プロジェクト ノード**追加**、**参照**します。 **プロパティ ページ**、 をクリックして**新しい参照の追加**、WindowsControlLibrary1 を選択します (下、**プロジェクト** タブ)、 をクリック**OK**。 形式での参照が追加されます、 [/FU](../build/reference/fu-name-forced-hash-using-file.md)コンパイラは、プログラムをコンパイルするためのオプションは、WindowsControlLibrary1.dll にもコピー、`MFC03`プログラムを実行するためのプロジェクト ディレクトリ。

1. stdafx.h の既存の `#include <afxwinforms.h>` ステートメントの最後に `#include` を追加します。

1. `CDialog` をサブクラスとして持つ新しいクラスを追加します。

   プロジェクト名を右クリックし、`CDialog` をサブクラスとして持つ (CHostForWinForm という名前の) MFC クラスを追加します。 ダイアログ ボックスのリソースを使用する必要はありません、ために、リソース ID を削除することができます (選択**リソース ビュー**、展開、**ダイアログ**フォルダーおよび delete`IDD_HOSTFORWINFORM`リソース。  次に、コード内のこの ID への参照を削除します。

1. CHostForWinForm.h ファイルと CHostForWinForm.cpp ファイル内にある `CDialog` を `CWinFormsDialog<WindowsControlLibrary1::UserControl1>` に置き換えます。

1. CHostForWinForm クラスで DoModal を呼び出します。

   MFC03.cpp で、`#include "HostForWinForm.h"` を追加します。

   CMFC03App::InitInstance の定義内の return ステートメントの前に、次のコードを追加します。

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. プロジェクトをビルドして実行します。

   **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

   **デバッグ** メニューのをクリックして**デバッグなしで開始**します。

   次に、MFC アプリケーションから Windows フォーム上のコントロールの状態を監視するコードを追加します。

1. OnInitDialog のハンドラーを追加します。

   表示、**プロパティ**ウィンドウ (F4)。 **クラス ビュー**CHostForWinForm を選択します。 **プロパティ**ウィンドウで、選択をオーバーライドし、OnInitDialog の行、左側の列内をクリックし、選択\<追加 >。 これにより、次の行が CHostForWinForm.h に追加されます。

    ```cpp
    virtual BOOL OnInitDialog();
    ```

1. CHostForWinForm.cpp で、OnInitDialog を次のように定義します。

    ```cpp
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

1. 次に、OnButton1 ハンドラーを追加します。 CHostForWinForm.h 内の CHostForWinForm クラスのパブリック セクションに次の行を追加します。

    ```cpp
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   CHostForWinForm.cpp で、次の定義を追加します。

    ```cpp
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

1. プロジェクトをビルドして実行します。 Windows フォーム上のボタンをクリックすると、MFC アプリケーション内のコードが実行されます。

    次に、MFC コードから Windows フォーム上のテキスト ボックスの値を表示するコードを追加します。

1. CHostForWinForm.h 内の CHostForWinForm クラスのパブリック セクションに、次の宣言を追加します。

    ```cpp
    CString m_sEditBoxOnWinForm;
    ```

1. CHostForWinForm.cpp 内の DoDataExchange の定義で、関数の最後に次の 3 行を追加します。

    ```cpp
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

1. CHostForWinForm.cpp 内の OnButton1 の定義で、関数の最後に次の 3 行を追加します。

    ```cpp
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

1. プロジェクトをビルドして実行します。

## <a name="see-also"></a>関連項目

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[Mfc Windows フォーム ユーザー コントロールの使用](../dotnet/using-a-windows-form-user-control-in-mfc.md)
