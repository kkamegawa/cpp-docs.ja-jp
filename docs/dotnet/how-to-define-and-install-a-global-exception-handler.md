---
title: '方法: グローバル例外ハンドラー定義およびインストール'
ms.date: 11/04/2016
helpviewer_keywords:
- handlers, global
ms.assetid: dd88a812-3bc7-4ce8-8283-4b674c246534
ms.openlocfilehash: d1b8452d19172bf16817c36032189accfd855539
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387397"
---
# <a name="how-to-define-and-install-a-global-exception-handler"></a>方法: グローバル例外ハンドラー定義およびインストール

次のコード例に示す方法未処理の例外をキャプチャできます。 フォーム例にはには、ボタンが含まれています。、、押されたときにスローされる例外を発生させる、null 参照を実行します。 この機能は、一般的なコード エラーを表します。 アプリケーション全体の例外ハンドラーがメインの関数によってインストールされている結果の例外をキャッチします。

デリゲートをバインドすることによってこれは、<xref:System.Windows.Forms.Application.ThreadException>イベント。 この場合、後続の例外に送信されますし、`App::OnUnhandled`メソッド。

## <a name="example"></a>例

```
// global_exception_handler.cpp
// compile with: /clr
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Drawing;
using namespace System::Windows::Forms;

ref class MyForm : public Form
{
   Button^ b;
public:
   MyForm( )
   {
      b = gcnew Button( );
      b->Text = "Do Null Access";
      b->Size = Drawing::Size(150, 30);
      b->Click += gcnew EventHandler(this, &MyForm::OnClick);
      Controls->Add(b);
   }
   void OnClick(Object^ sender, EventArgs^ args)
   {
      // do something illegal, like call through a null pointer...
      Object^ o = nullptr;
      o->ToString( );
   }
};

ref class App
{
public:
   static void OnUnhandled(Object^ sender, ThreadExceptionEventArgs^ e)
   {
      MessageBox::Show(e->Exception->Message, "Global Exeception");
      Application::ExitThread( );
   }
};

int main()
{
   Application::ThreadException += gcnew
      ThreadExceptionEventHandler(App::OnUnhandled);

   MyForm^ form = gcnew MyForm( );
   Application::Run(form);
}
```

## <a name="see-also"></a>関連項目

[例外処理](../extensions/exception-handling-cpp-component-extensions.md)
