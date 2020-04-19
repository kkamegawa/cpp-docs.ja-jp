---
title: '方法: ネイティブ C++ クラスから Windows フォーム イベントをシンクします。'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- event handling, managed/native interop
- event handling, sinking .NET in C++
- event handling, .NET/native interop
- event handling, Windows Forms in C++
ms.assetid: 6e30ddee-d058-4c8d-9956-2a43d86f19d5
ms.openlocfilehash: d02bcea4efce03c8fb11650d344468236737cfbd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387267"
---
# <a name="how-to-sink-windows-forms-events-from-native-c-classes"></a>方法: ネイティブ C++ クラスから Windows フォーム イベントをシンクします。

Windows フォーム コントロールまたは MFC のマクロのマップ形式の他のフォームから発生した管理対象のイベントからのコールバックを受信するネイティブの C++ クラスを有効にすることができます。 ビューとダイアログ ボックスでイベントをシンクは、コントロールに対して同じタスクの実行に似ています。

これを行うには、する必要があります。

- アタッチする`OnClick`イベント ハンドラーを使用してコントロールを[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)します。

- 使用してデリゲート マップ作成[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)、 [END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)、および[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)します。

このサンプルで行った作業を続行する[方法。Windows フォームで DDX/DDV データ バインディング](../dotnet/how-to-do-ddx-ddv-data-binding-with-windows-forms.md)します。

次に、MFC コントロールは関連付けます (`m_MyControl`) と呼ばれる管理対象のイベント ハンドラー デリゲートを使用して`OnClick`、管理対象の<xref:System.Windows.Forms.Control.Click>イベント。

### <a name="to-attach-the-onclick-event-handler"></a>OnClick イベント ハンドラーをアタッチするには。

1. BOOL CMFC01Dlg::OnInitDialog の実装には、次のコードを追加します。

    ```
    m_MyControl.GetControl()->button1->Click += MAKE_DELEGATE( System::EventHandler, OnClick );
    ```

1. CMFC01Dlg クラスの宣言のパブリック セクションに次のコードを追加します。 パブリック CDialog します。

    ```
    // delegate map
    BEGIN_DELEGATE_MAP( CMFC01Dlg )
    EVENT_DELEGATE_ENTRY( OnClick, System::Object^, System::EventArgs^ )
    END_DELEGATE_MAP()

    void OnClick( System::Object^ sender, System::EventArgs^ e );
    ```

1. 実装を最後に、追加`OnClick`CMFC01Dlg.cpp に。

    ```
    void CMFC01Dlg::OnClick(System::Object^ sender, System::EventArgs^ e)
    {
        AfxMessageBox(_T("Button clicked"));
    }
    ```

## <a name="see-also"></a>関連項目

[MAKE_DELEGATE](../mfc/reference/delegate-and-interface-maps.md#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#begin_delegate_map)<br/>
[END_DELEGATE_MAP](../mfc/reference/delegate-and-interface-maps.md#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](../mfc/reference/delegate-and-interface-maps.md#event_delegate_entry)
