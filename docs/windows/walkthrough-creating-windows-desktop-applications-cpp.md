---
title: 'チュートリアル: 従来の Windows デスクトップ アプリケーション (C++) の作成します。'
ms.custom: get-started-article
ms.date: 09/18/2018
helpviewer_keywords:
- Windows applications [C++], Win32
- Windows Desktop applications [C++]
- Windows API [C++]
ms.openlocfilehash: 07da91ea092b4e7bee974b0387e72ea0cacaec8e
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893900"
---
# <a name="walkthrough-create-a-traditional-windows-desktop-application-c"></a>チュートリアル: 従来の Windows デスクトップ アプリケーション (C++) の作成します。

このチュートリアルでは、Visual Studio での従来の Windows デスクトップ アプリケーションを作成する方法を示します。 作成するサンプル アプリケーションでは、Windows API を使用して、「こんにちは, Windows デスクトップ!」を表示 。ウィンドウです。 このチュートリアルで開発したコードは、他の Windows デスクトップ アプリケーションを作成するためのパターンとして使用できます。

Windows API (とも呼ばれる、Win32 API、Windows デスクトップ API、および Windows クラシック API) は、Windows アプリケーションを作成するための C 言語ベースのフレームワークです。 1980 年代から存在していますが、数十年の Windows アプリケーションの作成に使用されています。 プログラムを簡単にし、高度なフレームワークは、MFC、ATL、および .NET フレームワークなど、Windows API の上に構築されています。 C++ で記述された UWP およびストア アプリのも、ほとんどの最新コード/cli WinRT が下にある Windows API を使用します。 Windows API の詳細については、次を参照してください。 [Windows API インデックス](/windows/desktop/apiindex/windows-api-list)します。 Windows アプリケーションを作成する方法はたくさんありますが、上記のプロセスが 1 つ目。

> [!IMPORTANT]
> 説明を簡潔にするため、一部のコード ステートメントは、テキストで省略されます。 [コードをビルドして](#build-the-code)セクションにこのドキュメントの末尾には完全なコードが表示されます。

## <a name="prerequisites"></a>必須コンポーネント

- Microsoft Windows 7 またはそれ以降のバージョンを実行するコンピューター。 開発のベスト エクスペリエンスを実現するには Windows 10 をお勧めします。

- Visual Studio 2017 のコピー。 ダウンロードして Visual Studio をインストールする方法については、次を参照してください。 [Visual Studio のインストール](/visualstudio/install/install-visual-studio)します。 インストーラーを実行するときに、以下のことを確認、 **C++ によるデスクトップ開発**ワークロードがチェックされます。 Visual Studio をインストールしたときに、このワークロードをインストールしなかった場合、心配しないでください。 インストーラーをもう一度実行して、今すぐインストールします。

   ![C++ によるデスクトップ開発](../build/media/desktop-development-with-cpp.png "C++ によるデスクトップ開発")

- Visual Studio IDE の使用の基本を理解します。 前に、Windows デスクトップ アプリを使用した場合保持できます可能性があります。 概要については、次を参照してください。 [Visual Studio IDE 機能ツアー](/visualstudio/ide/visual-studio-ide)します。

- 十分な作業を進めるには C++ 言語の基礎について理解します。 ご心配なく、あまり複雑な何もしません。

## <a name="create-a-windows-desktop-project"></a>Windows デスクトップ プロジェクトを作成します。

以下の手順を実行する最初の Windows デスクトップ プロジェクトを作成し、動作する Windows デスクトップ アプリケーションのコードを入力します。 Visual Studio の Visual Studio 2017 バージョン 15.3 より前のバージョンを使用している場合に進みます[Visual Studio 2017 RTM での Windows デスクトップ プロジェクトを作成する](#create-in-vs2017-rtm)します。

### <a name="to-create-a-windows-desktop-project-in-visual-studio-2017-update-153-and-later"></a>Visual Studio 2017 Update 15.3 以降の Windows デスクトップ プロジェクトを作成するには

1. **[ファイル]** メニューの **[新規作成]** を選択し、**[プロジェクト]** を選択します。

1. **新しいプロジェクト**ダイアログ ボックスの左側のウィンドウで、**インストール済み** > **Visual C**を選択し、 **Windows デスクトップ**. 中央のペインで選択**Windows デスクトップ ウィザード**します。

   **名前**など、プロジェクトの名前を入力ボックスに、 *DesktopApp*します。 **[OK]** をクリックします。

   ![DesktopApp プロジェクト](../build/media/desktop-app-new-project-name-153.png "DesktopApp プロジェクトの名前")

1. **Windows デスクトップ プロジェクト**ダイアログで、**アプリケーションの種類**を選択します**Windows アプリケーション (.exe)** します。 **[追加のオプション]** の **[空のプロジェクト]** を選択します。 その後、**OK** を選択すると、プロジェクトが作成されます。

   ![Windows デスクトップ プロジェクト ウィザードで DesktopApp を作成する](../build/media/desktop-app-new-project-wizard-153.png "DesktopApp を Windows デスクトップ プロジェクト ウィザードで作成")

1. **ソリューション エクスプ ローラー**を右クリックし、 **DesktopApp**プロジェクトで、選択**追加**を選び、**新しい項目の**。

   ![DesktopApp プロジェクトに新しい項目の追加](../build/media/desktop-app-project-add-new-item-153.gif "DesktopApp プロジェクトに新しい項目の追加")

1. **[新しい項目の追加]** ダイアログ ボックスで、 **[C++ ファイル (.cpp)]** をクリックします。 **名前**など、ファイルの名前を入力ボックスに、 *HelloWindowsDesktop.cpp*します。 **[追加]** をクリックします。

   ![DesktopApp プロジェクトに追加の .cpp ファイル](../build/media/desktop-app-add-cpp-file-153.png "DesktopApp プロジェクトに .cpp ファイルの追加")

プロジェクトが作成され、ソース ファイルが、エディターで開かれます。 続けるには、」に進みます[コードを作成する](#create-the-code)します。

### <a id="create-in-vs2017-rtm"></a> Visual Studio 2017 RTM での Windows デスクトップ プロジェクトを作成するには

1. **[ファイル]** メニューの **[新規作成]** を選択し、**[プロジェクト]** を選択します。

1. **新しいプロジェクト**ダイアログ ボックスの左側のウィンドウで、**インストール済み** > **テンプレート** > **Visual C**、し、 **Win32**します。 中央のペインで、 **[Win32 プロジェクト]** を選択します。

   **名前**など、プロジェクトの名前を入力ボックスに、 *DesktopApp*します。 **[OK]** をクリックします。

   ![DesktopApp プロジェクト](../build/media/desktop-app-new-project-name-150.png "DesktopApp プロジェクトの名前")

1. **概要**のページ、 **Win32 アプリケーション ウィザード**、選択**次**します。

   ![Win32 アプリケーション ウィザードの概要作成 DesktopApp](../build/media/desktop-app-win32-wizard-overview-150.png "DesktopApp を Win32 アプリケーション ウィザードの概要の作成")

1. **アプリケーション設定**] ページ [**アプリケーションの種類**を選択します**Windows アプリケーション**します。 **[追加のオプション]** の **[空のプロジェクト]** を選択します。 選択**完了**プロジェクトを作成します。

   ![Win32 アプリケーション ウィザードの設定で DesktopApp を作成する](../build/media/desktop-app-win32-wizard-settings-150.png "DesktopApp を Win32 アプリケーション ウィザードの設定の作成")

1. **ソリューション エクスプ ローラー**、DesktopApp プロジェクトを右クリックし、選択**追加**を選び、**新しい項目の**します。

   ![DesktopApp プロジェクトに新しい項目の追加](../build/media/desktop-app-project-add-new-item-150.gif "DesktopApp プロジェクトに新しい項目の追加")

1. **[新しい項目の追加]** ダイアログ ボックスで、 **[C++ ファイル (.cpp)]** をクリックします。 **名前**など、ファイルの名前を入力ボックスに、 *HelloWindowsDesktop.cpp*します。 **[追加]** をクリックします。

   ![DesktopApp プロジェクトに追加の .cpp ファイル](../build/media/desktop-app-add-cpp-file-150.png "DesktopApp プロジェクトに .cpp ファイルの追加")

プロジェクトが作成され、ソース ファイルが、エディターで開かれます。

## <a name="create-the-code"></a>コードを作成します。

次に、Visual Studio での Windows デスクトップ アプリケーションのコードを作成する方法について説明します。

### <a name="to-start-a-windows-desktop-application"></a>Windows デスクトップ アプリケーションを開始するには

1. すべての c と C++ アプリケーションする必要がありますが、`main`関数のすべての Windows デスクトップ アプリケーションする必要がありますが、その開始点として、`WinMain`関数。 `WinMain` の構文は、次のとおりです。

   ```cpp
   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   );
   ```

   この関数の戻り値とパラメーターについては、次を参照してください。 [WinMain エントリ ポイント](/windows/desktop/api/winbase/nf-winbase-winmain)します。

   > [!NOTE]
   > など、すべての余分な単語は`CALLBACK`、または`HINSTANCE`、または`_In_`でしょうか。 Typedef を使用する従来の Windows API と抽象化するには、広範囲にプリプロセッサ マクロの種類とプラットフォーム固有の詳細の一部のコード、呼び出し規則など **_ _declspec**宣言、およびコンパイラのプラグマ。 Visual Studio で IntelliSense を使用することができます[クイック ヒント](/visualstudio/ide/using-intellisense#quick-info)機能をこれらの typedef、マクロ定義内容を参照してください。 関心のある単語の上にマウスを移動または選択し、 **Ctrl**+**K**、 **Ctrl**+**は**用、定義を含む小さなポップアップ ウィンドウ。 詳細については、「[IntelliSense の使用](/visualstudio/ide/using-intellisense)」を参照してください。 パラメーターと戻り値の型が多くの場合、使用*SAL 注釈*に役立つプログラミング エラーをキャッチします。 詳細については、次を参照してください。 [C と C++ コードの欠陥を削減する SAL 注釈を使って](/visualstudio/code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects)します。

1. Windows デスクトップ プログラムを必要と&lt;windows.h >。 &lt;tchar.h > を定義、`TCHAR`マクロで、最終的に解決する**wchar_t**場合 UNICODE 記号は、プロジェクトで定義されているが、それ以外の場合に解決される**char**します。  TCHAR 必要があり、だけを使用してない場合は常に有効になっている UNICODE を使用したビルドが、 **wchar_t**直接します。

   ```cpp
   #include <windows.h>
   #include <tchar.h>
   ```

1. `WinMain` 関数のほかに、すべての Windows デスクトップ アプリケーションにはウィンドウ プロシージャ関数が必要です。 この関数の名前は通常`WndProc`がすることができます、どのような名前します。 `WndProc` の構文は、次のとおりです。

   ```cpp
   LRESULT CALLBACK WndProc(
      _In_ HWND   hwnd,
      _In_ UINT   uMsg,
      _In_ WPARAM wParam,
      _In_ LPARAM lParam
   );
   ```

   この関数で処理するコードを記述する*メッセージ*アプリケーションが Windows から受信するときに*イベント*発生します。 たとえば場合は、ユーザーは、アプリケーションで、[ok] ボタンを選択、Windows では、メッセージを送信して、内のコードを記述することができます、`WndProc`はどのような作業が適切な関数です。 呼び出された*処理*イベント。 アプリケーションに関連するイベントを処理するだけです。

   詳細については、「 [ウィンドウ プロシージャ](/windows/desktop/winmsg/window-procedures)」を参照してください。

### <a name="to-add-functionality-to-the-winmain-function"></a>WinMain 関数に機能を追加するには

1. `WinMain`関数、型の構造体の値を設定する[WNDCLASSEX](/windows/desktop/api/winuser/ns-winuser-tagwndclassexa)します。 構造体には、アプリケーションのアイコン、タイトル バー、および重要なは、ウィンドウ プロシージャへの関数ポインターの表示名 ウィンドウの背景色など、ウィンドウに関する情報が含まれています。 一般的な `WNDCLASSEX` 構造体の例を次に示します。

   ```cpp
   WNDCLASSEX wcex;

   wcex.cbSize         = sizeof(WNDCLASSEX);
   wcex.style          = CS_HREDRAW | CS_VREDRAW;
   wcex.lpfnWndProc    = WndProc;
   wcex.cbClsExtra     = 0;
   wcex.cbWndExtra     = 0;
   wcex.hInstance      = hInstance;
   wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
   wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
   wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
   wcex.lpszMenuName   = NULL;
   wcex.lpszClassName  = szWindowClass;
   wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);
   ```

   上記の構造体のフィールドの詳細については、次を参照してください。 [WNDCLASSEX](/windows/desktop/api/winuser/ns-winuser-tagwndclassexa)します。

1. 登録、`WNDCLASSEX`で Windows メッセージを送信する方法と、ウィンドウの詳細が認識できるようにします。 [RegisterClassEx](/windows/desktop/api/winuser/nf-winuser-registerclassexa) 関数を使用して、ウィンドウ クラス構造体を引数として渡します。 `_T`マクロを使用しているために使用、`TCHAR`型。

   ```cpp
   if (!RegisterClassEx(&wcex))
   {
      MessageBox(NULL,
         _T("Call to RegisterClassEx failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

1. これで、ウィンドウを作成できます。 [CreateWindow](/windows/desktop/api/winuser/nf-winuser-createwindowa) 関数を使用します。

   ```cpp
   static TCHAR szWindowClass[] = _T("DesktopApp");
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   // The parameters to CreateWindow explained:
   // szWindowClass: the name of the application
   // szTitle: the text that appears in the title bar
   // WS_OVERLAPPEDWINDOW: the type of window to create
   // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
   // 500, 100: initial size (width, length)
   // NULL: the parent of this window
   // NULL: this application does not have a menu bar
   // hInstance: the first parameter from WinMain
   // NULL: not used in this application
   HWND hWnd = CreateWindow(
      szWindowClass,
      szTitle,
      WS_OVERLAPPEDWINDOW,
      CW_USEDEFAULT, CW_USEDEFAULT,
      500, 100,
      NULL,
      NULL,
      hInstance,
      NULL
   );
   if (!hWnd)
   {
      MessageBox(NULL,
         _T("Call to CreateWindow failed!"),
         _T("Windows Desktop Guided Tour"),
         NULL);

      return 1;
   }
   ```

   この関数を返します、`HWND`ウィンドウのハンドルであります。 ハンドルは、Windows が開いているウィンドウを追跡するために使用するポインターのようなものです。 詳細については、「 [Windows のデータ型](/windows/desktop/WinProg/windows-data-types)」を参照してください。

1. この時点では、ウィンドウが作成されたらが表示されるように Windows に指示する必要があります。 このコードを行っています。

   ```cpp
   // The parameters to ShowWindow explained:
   // hWnd: the value returned from CreateWindow
   // nCmdShow: the fourth parameter from WinMain
   ShowWindow(hWnd,
      nCmdShow);
   UpdateWindow(hWnd);
   ```

   表示されたウィンドウはまだ実装されていないため、コンテンツがない、`WndProc`関数。 つまり、アプリケーションは、Windows は、今すぐに送信するメッセージを処理まだはありません。

1. メッセージを処理するために Windows を送信するメッセージをリッスンするようにメッセージ ループを最初に追加します。 このループをディスパッチするアプリケーションでは、メッセージを受信したときに、`WndProc`処理する関数。 メッセージ ループのコードは、次のようになります。

   ```cpp
   MSG msg;
   while (GetMessage(&msg, NULL, 0, 0))
   {
      TranslateMessage(&msg);
      DispatchMessage(&msg);
   }

   return (int) msg.wParam;
   ```

   構造体とメッセージ ループ内の関数の詳細については、次を参照してください[MSG](/windows/desktop/api/winuser/ns-winuser-msg)、 [GetMessage](/windows/desktop/api/winuser/nf-winuser-getmessage)、 [TranslateMessage](/windows/desktop/api/winuser/nf-winuser-translatemessage)、および[DispatchMessage](/windows/desktop/api/winuser/nf-winuser-dispatchmessage)。

   この段階では、 `WinMain` 関数のコードは次のようになります。

   ```cpp
   int WINAPI WinMain(HINSTANCE hInstance,
                      HINSTANCE hPrevInstance,
                      LPSTR lpCmdLine,
                      int nCmdShow)
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application dows not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }
   ```

### <a name="to-add-functionality-to-the-wndproc-function"></a>WndProc 関数に機能を追加するには

1. `WndProc` 関数を有効にしてアプリケーションが受け取るメッセージを処理するために、switch ステートメントを実装します。

   1 つの重要なメッセージを処理するためには、 [WM_PAINT](/windows/desktop/gdi/wm-paint)メッセージ。 アプリケーションが受信、`WM_PAINT`メッセージとその表示されたウィンドウの一部を更新する必要があります。 これらのイベントが発生した場合、アプリケーションが認識しないと、ユーザーは、ウィンドウの前にウィンドウを移動し、移動しますから、もう一度イベントが発生します。 Windows のみを知っていればに通知するように`WM_PAINT`します。 最初に、ウィンドウが表示されるときにすべての更新する必要があります。

   `WM_PAINT` メッセージを処理するには、まず [BeginPaint](/windows/desktop/api/winuser/nf-winuser-beginpaint)を呼び出して、ウィンドウのテキスト、ボタン、その他のコントロールをレイアウトするためのすべてのロジックを処理し、次に [EndPaint](/windows/desktop/api/winuser/nf-winuser-endpaint)を呼び出します。 アプリケーションで、最初の呼び出しと最後の呼び出しの間のロジックは文字列「こんにちは, Windows デスクトップ!」を表示するには ウィンドウです。 次のコードでは、文字列を表示するために [TextOut](/windows/desktop/api/wingdi/nf-wingdi-textouta) 関数が使用されていることに注意してください。

   ```cpp
   PAINTSTRUCT ps;
   HDC hdc;
   TCHAR greeting[] = _T("Hello, Windows desktop!");

   switch (message)
   {
   case WM_PAINT:
      hdc = BeginPaint(hWnd, &ps);

      // Here your application is laid out.
      // For this introduction, we just print out "Hello, Windows desktop!"
      // in the top left corner.
      TextOut(hdc,
         5, 5,
         greeting, _tcslen(greeting));
      // End application-specific layout section.

      EndPaint(hWnd, &ps);
      break;
   }
   ```

   `HDC` コードは、Windows を使用して、グラフィックス サブシステムと通信するアプリケーションを有効にするデータ構造体である、デバイス コンテキストを識別するハンドル。 `BeginPaint`と`EndPaint`関数は良き市民と同様に動作する、アプリケーションを作成して、デバイス コンテキストを必要以上に長期間使用しません。 関数のヘルプ make グラフィックス サブシステムは、他のアプリケーションで使用可能です。

1. アプリケーションで他の多くのメッセージをたとえば、処理通常[WM_CREATE](/windows/desktop/winmsg/wm-create)ウィンドウが最初に作成したときと[WM_DESTROY](/windows/desktop/winmsg/wm-destroy)ウィンドウを閉じるときにします。 単純でも完成した `WndProc` 関数のコードを次に示します。

   ```cpp
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

## <a name="build-the-code"></a>コードをビルドします。

お約束どおり、次に、動作するアプリケーションの完全なコードを示します。

### <a name="to-build-this-example"></a>この例をビルドするには

1. 入力した任意のコードを削除*HelloWindowsDesktop.cpp*エディターでします。 このコード例をコピーして貼り付けます*HelloWindowsDesktop.cpp*:

   ```cpp
   // HelloWindowsDesktop.cpp
   // compile with: /D_UNICODE /DUNICODE /DWIN32 /D_WINDOWS /c

   #include <windows.h>
   #include <stdlib.h>
   #include <string.h>
   #include <tchar.h>

   // Global variables

   // The main window class name.
   static TCHAR szWindowClass[] = _T("DesktopApp");

   // The string that appears in the application's title bar.
   static TCHAR szTitle[] = _T("Windows Desktop Guided Tour Application");

   HINSTANCE hInst;

   // Forward declarations of functions included in this code module:
   LRESULT CALLBACK WndProc(HWND, UINT, WPARAM, LPARAM);

   int CALLBACK WinMain(
      _In_ HINSTANCE hInstance,
      _In_ HINSTANCE hPrevInstance,
      _In_ LPSTR     lpCmdLine,
      _In_ int       nCmdShow
   )
   {
      WNDCLASSEX wcex;

      wcex.cbSize = sizeof(WNDCLASSEX);
      wcex.style          = CS_HREDRAW | CS_VREDRAW;
      wcex.lpfnWndProc    = WndProc;
      wcex.cbClsExtra     = 0;
      wcex.cbWndExtra     = 0;
      wcex.hInstance      = hInstance;
      wcex.hIcon          = LoadIcon(hInstance, IDI_APPLICATION);
      wcex.hCursor        = LoadCursor(NULL, IDC_ARROW);
      wcex.hbrBackground  = (HBRUSH)(COLOR_WINDOW+1);
      wcex.lpszMenuName   = NULL;
      wcex.lpszClassName  = szWindowClass;
      wcex.hIconSm        = LoadIcon(wcex.hInstance, IDI_APPLICATION);

      if (!RegisterClassEx(&wcex))
      {
         MessageBox(NULL,
            _T("Call to RegisterClassEx failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // Store instance handle in our global variable
      hInst = hInstance;

      // The parameters to CreateWindow explained:
      // szWindowClass: the name of the application
      // szTitle: the text that appears in the title bar
      // WS_OVERLAPPEDWINDOW: the type of window to create
      // CW_USEDEFAULT, CW_USEDEFAULT: initial position (x, y)
      // 500, 100: initial size (width, length)
      // NULL: the parent of this window
      // NULL: this application does not have a menu bar
      // hInstance: the first parameter from WinMain
      // NULL: not used in this application
      HWND hWnd = CreateWindow(
         szWindowClass,
         szTitle,
         WS_OVERLAPPEDWINDOW,
         CW_USEDEFAULT, CW_USEDEFAULT,
         500, 100,
         NULL,
         NULL,
         hInstance,
         NULL
      );

      if (!hWnd)
      {
         MessageBox(NULL,
            _T("Call to CreateWindow failed!"),
            _T("Windows Desktop Guided Tour"),
            NULL);

         return 1;
      }

      // The parameters to ShowWindow explained:
      // hWnd: the value returned from CreateWindow
      // nCmdShow: the fourth parameter from WinMain
      ShowWindow(hWnd,
         nCmdShow);
      UpdateWindow(hWnd);

      // Main message loop:
      MSG msg;
      while (GetMessage(&msg, NULL, 0, 0))
      {
         TranslateMessage(&msg);
         DispatchMessage(&msg);
      }

      return (int) msg.wParam;
   }

   //  FUNCTION: WndProc(HWND, UINT, WPARAM, LPARAM)
   //
   //  PURPOSE:  Processes messages for the main window.
   //
   //  WM_PAINT    - Paint the main window
   //  WM_DESTROY  - post a quit message and return
   LRESULT CALLBACK WndProc(HWND hWnd, UINT message, WPARAM wParam, LPARAM lParam)
   {
      PAINTSTRUCT ps;
      HDC hdc;
      TCHAR greeting[] = _T("Hello, Windows desktop!");

      switch (message)
      {
      case WM_PAINT:
         hdc = BeginPaint(hWnd, &ps);

         // Here your application is laid out.
         // For this introduction, we just print out "Hello, Windows desktop!"
         // in the top left corner.
         TextOut(hdc,
            5, 5,
            greeting, _tcslen(greeting));
         // End application-specific layout section.

         EndPaint(hWnd, &ps);
         break;
      case WM_DESTROY:
         PostQuitMessage(0);
         break;
      default:
         return DefWindowProc(hWnd, message, wParam, lParam);
         break;
      }

      return 0;
   }
   ```

1. **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。 コンパイルの結果が表示されます、**出力**Visual Studio のウィンドウ。

   ![DesktopApp プロジェクトをビルド](../build/media/desktop-app-project-build-150.gif "DesktopApp プロジェクトをビルド")

1. キーを押して、アプリケーションを実行する**F5**します。 テキスト「こんにちは, Windows デスクトップ!」を含むウィンドウ 画面の左上隅に表示されます。

   ![DesktopApp プロジェクト実行](../build/media/desktop-app-project-run-157.png "DesktopApp プロジェクトを実行します。")

おめでとうございます! このチュートリアルを完了し、従来の Windows デスクトップ アプリケーションを構築しました。

## <a name="see-also"></a>関連項目

[Windows デスクトップ アプリケーション](../windows/windows-desktop-applications-cpp.md)