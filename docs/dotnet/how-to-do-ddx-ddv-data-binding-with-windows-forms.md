---
title: '方法: Windows フォーム バインディング DDX-DDV データの操作を行います'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], hosting a Windows Forms Control
- Windows Forms [C++], MFC support
ms.assetid: b2957370-cf1f-4779-94ac-228cd393686c
ms.openlocfilehash: 558c763fd18cd1569ff23435bf6156b3117f117d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387319"
---
# <a name="how-to-do-ddxddv-data-binding-with-windows-forms"></a>方法: Windows フォーム バインディング DDX/DDV データの操作を行います

[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)呼び出し[CWinFormsControl::CreateManagedControl](../mfc/reference/cwinformscontrol-class.md#createmanagedcontrol)リソース コントロールの ID に一致するコントロールを作成するには 使用する場合`DDX_ManagedControl`の`CWinFormsControl`コントロール (ウィザードで生成されたコードで)、呼び出す必要はありません`CreateManagedControl`同じコントロールを明示的にします。

呼び出す`DDX_ManagedControl`で[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)リソース Id からコントロールを作成します。 データ交換では、Windows フォーム コントロールで DDX/DDV 関数を使用する必要はありません。 マネージ コントロールのプロパティにアクセスするためのコードを配置する代わりに、`DoDataExchange`次の例のように、ダイアログ (またはビュー) のクラスのメソッド。

次の例では、ネイティブ C++ 文字列を .NET ユーザー コントロールにバインドする方法を示します。

## <a name="example"></a>例

MFC 文字列の DDX/DDV データ バインディングの例を次に`m_str`ユーザー定義の`NameText`.NET ユーザー コントロールのプロパティ。

コントロールが作成された[CDialog::OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)呼び出し`CMyDlg::DoDataExchange`初めて、そのため、コードを参照する`m_UserControl`後必要があります、`DDX_ManagedControl`呼び出します。

このコードで作成した [MFC01 アプリケーションに実装できる[方法。ユーザー コントロールおよびホストを作成] ダイアログ ボックスで](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)します。

CMFC01Dlg の宣言では、次のコードを配置します。

```
class CMFC01Dlg : public CDialog
{
   CWinFormsControl<WindowsFormsControlLibrary1::UserControl1> m_MyControl;
   CString m_str;
};
```

## <a name="example"></a>例

CMFC01Dlg の実装では、次のコードを配置します。

```
void CMFC01Dlg::DoDataExchange(CDataExchange* pDX)
{
   CDialog::DoDataExchange(pDX);
   DDX_ManagedControl(pDX, IDC_CTRL1, m_MyControl);

   if (pDX->m_bSaveAndValidate) {
      m_str = m_MyControl->textBox1->Text;
   } else
   {
      m_MyControl->textBox1->Text = gcnew System::String(m_str);
   }
}
```

## <a name="example"></a>例

[Ok] ボタンのクリック ハンドラー メソッドを追加します。 をクリックして、**リソース ビュー**タブ。リソース ビューで、ダブルクリック`IDD_MFC01_DIALOG`します。 ダイアログ リソースでは、リソース エディターで表示されます。 [Ok] ボタンがダブルクリックし.

次のように、ハンドラーを定義します。

```
void CMFC01Dlg::OnBnClickedOk()
{
   AfxMessageBox(CString(m_MyControl.GetControl()->textBox1->Text));
   OnOK();
}
```

## <a name="example"></a>例

BOOL CMFC01Dlg::OnInitDialog() の実装を次の行を追加します。

```
m_MyControl.GetControl()->textBox1->Text = "hello";
```

ビルドして、アプリケーションを実行することができますようになりました。 確認すると、アプリケーションを閉じるときに、ポップアップ メッセージ ボックスに、テキスト ボックスにテキストを表示します。

## <a name="see-also"></a>関連項目

[CWinFormsControl クラス](../mfc/reference/cwinformscontrol-class.md)<br/>
[DDX_ManagedControl](../mfc/reference/standard-dialog-data-exchange-routines.md#ddx_managedcontrol)<br/>
[CWnd::DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange)
