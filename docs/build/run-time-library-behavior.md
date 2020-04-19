---
title: Dll と Visual C++ランタイムライブラリの動作
ms.date: 08/19/2019
f1_keywords:
- _DllMainCRTStartup
- CRT_INIT
helpviewer_keywords:
- DLLs [C++], entry point function
- process detach [C++]
- process attach [C++]
- DLLs [C++], run-time library behavior
- DllMain function
- _CRT_INIT macro
- _DllMainCRTStartup method
- run-time [C++], DLL startup sequence
- DLLs [C++], startup sequence
ms.assetid: e06f24ab-6ca5-44ef-9857-aed0c6f049f2
ms.openlocfilehash: 572a0ba70c1ba2d46d2d9fd6d8ac543a77bbbc01
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630365"
---
# <a name="dlls-and-visual-c-run-time-library-behavior"></a>Dll と Visual C++ランタイムライブラリの動作

Visual Studio を使用してダイナミックリンクライブラリ (DLL) をビルドする場合、既定では、リンカーにはC++ visual ランタイムライブラリ (vcruntime) が含まれます。 VCRuntime には、C/C++実行可能ファイルを初期化して終了するために必要なコードが含まれています。 Dll にリンクされている場合、vcruntime コードは、と呼ば`_DllMainCRTStartup`れる内部 dll エントリポイント関数を提供します。この関数は、Windows OS メッセージを dll に処理して、プロセスまたはスレッドにアタッチまたはデタッチします。 関数`_DllMainCRTStartup`は、スタックバッファーセキュリティのセットアップ、C ランタイムライブラリ (CRT) の初期化と終了、静的オブジェクトとグローバルオブジェクトのコンストラクターとデストラクターの呼び出しなど、重要なタスクを実行します。 `_DllMainCRTStartup`は、WinRT、MFC、ATL などの他のライブラリのフック関数も呼び出して、独自の初期化と終了を実行します。 この初期化がないと、CRT とその他のライブラリ、および静的変数は初期化されていない状態のままになります。 同じ VCRuntime 内部初期化および終了ルーチンは、DLL が静的にリンクされた CRT を使用するか、動的にリンクされた CRT DLL を使用するかにかかわらず呼び出されます。

## <a name="default-dll-entry-point-_dllmaincrtstartup"></a>既定の DLL エントリポイント _DllMainCRTStartup

Windows では、すべての dll にオプションのエントリポイント関数 (通常は`DllMain`と呼ばれます) を含めることができます。これは初期化と終了の両方に対して呼び出されます。 これによって、追加のリソースを必要に応じて、割り当て/解放する機会が与えられます。 Windows には、エントリ ポイント関数が呼び出される 4 つの状況 (プロセスのアタッチ、プロセス デタッチ、スレッド アタッチ、スレッド デタッチ) があります。 DLL がプロセスアドレス空間に読み込まれると、その DLL を使用するアプリケーションが読み込まれたとき、またはアプリケーションが実行時に DLL を要求したときに、オペレーティングシステムによって DLL データのコピーが個別に作成されます。 これを*プロセスアタッチ*と呼びます。 *スレッドのアタッチ*は、DLL が読み込まれるプロセスによって新しいスレッドが作成されるときに発生します。 スレッドの*デタッチ*は、スレッドが終了したときに発生し、*プロセスデタッチ*は、DLL が不要になり、アプリケーションによって解放されたときに発生します。 オペレーティングシステムは、これらの各イベントに対して DLL エントリポイントを個別に呼び出し、各イベントの種類に*reason*引数を渡します。 たとえば、OS は、signal `DLL_PROCESS_ATTACH` process attach に*reason*引数としてを送信します。

Vcruntime ライブラリには、既定の初期化および終了`_DllMainCRTStartup`操作を処理するために呼び出されるエントリポイント関数が用意されています。 プロセスのアタッチ時に`_DllMainCRTStartup` 、関数は、バッファーセキュリティチェックの設定、CRT とその他のライブラリの初期化、ランタイム型情報の初期化、静的およびローカルでないデータのコンストラクターの初期化と呼び出し、スレッドローカルストレージの初期化を行います。は、アタッチごとに内部静的カウンターをインクリメントし、ユーザーまたはライブラリが提供`DllMain`するを呼び出します。 プロセスのデタッチでは、関数はこれらの手順を逆に実行します。 このメソッド`DllMain`は、を呼び出し、内部カウンターをデクリメントし、デストラクターを呼び出し、 `atexit` CRT 終了関数と登録された関数を呼び出し、他のすべてのライブラリが終了したことを通知します。 Attachment カウンターが0になると、この関数は`FALSE`を返し、DLL をアンロードできることを Windows に示します。 関数`_DllMainCRTStartup`は、スレッドのアタッチとスレッドのデタッチ中にも呼び出されます。 このような場合、vcruntime コードは追加の初期化も終了もせず、を呼び出し`DllMain`てメッセージを渡すだけで済みます。 が`DllMain`プロセス`FALSE`のアタッチからを返し、シグナル`_DllMainCRTStartup`が失敗した`DLL_PROCESS_DETACH`場合、を再度呼び出し`DllMain`て*reason*引数として渡した後、残りの終了処理を実行します。

Visual Studio で dll をビルドする場合、vcruntime `_DllMainCRTStartup`によって提供される既定のエントリポイントは自動的にリンクされます。 [/Entry (エントリポイントシンボル)](reference/entry-entry-point-symbol.md)リンカーオプションを使用して、DLL のエントリポイント関数を指定する必要はありません。

> [!NOTE]
> /Entry: リンカーオプションを使用して DLL 用に別のエントリポイント関数を指定することもできますが、これは推奨されません。これ`_DllMainCRTStartup`は、エントリポイント関数が同じ順序ですべてのものを複製する必要があるためです。 VCRuntime には、動作を複製できるようにする関数が用意されています。 たとえば、プロセスのアタッチ時にすぐに[__ securityinitcookie](../c-runtime-library/reference/security-init-cookie.md)を呼び出して、 [/gs (バッファーのセキュリティチェック)](reference/gs-buffer-security-check.md)バッファーチェックオプションをサポートすることができます。 `_CRT_INIT`関数を呼び出して、エントリポイント関数と同じパラメーターを渡すことにより、残りの DLL 初期化関数または終了関数を実行できます。

<a name="initializing-a-dll"></a>

## <a name="initialize-a-dll"></a>DLL の初期化

Dll の読み込み時に実行する必要がある初期化コードが DLL に含まれている可能性があります。 独自の DLL 初期化関数と終了関数を実行するために、 `_DllMainCRTStartup`は、と呼ば`DllMain`れる関数を呼び出します。 に`DllMain`は、DLL エントリポイントに必要な署名が必要です。 既定のエントリポイント関数`_DllMainCRTStartup`は`DllMain` 、Windows によって渡されたのと同じパラメーターを使用してを呼び出します。 既定では、関数を`DllMain`指定しない場合、Visual Studio はそれを提供し、にリンクして、常にを呼び出すこと`_DllMainCRTStartup`ができるようにします。 つまり、dll を初期化する必要がない場合は、DLL をビルドするときに特別な操作は必要ありません。

これは、次のため`DllMain`に使用される署名です。

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved); // reserved
```

一部のライブラリで`DllMain`は、関数がラップされています。 たとえば、通常の MFC DLL では、 `CWinApp`オブジェクトの`InitInstance`関数と`ExitInstance`メンバー関数を実装して、DLL で必要な初期化と終了を実行します。 詳細については、「[通常の MFC dll の初期化](#initializing-regular-dlls)」セクションを参照してください。

> [!WARNING]
> DLL のエントリポイントで安全に実行できることには大きな制限があります。 「」で`DllMain`は、を呼び出すことができない特定の Windows Api の[一般的なベストプラクティス](/windows/win32/Dlls/dynamic-link-library-best-practices)を参照してください。 必要なものが最も単純な初期化である場合は、DLL の初期化関数でそれを実行します。 を実行してから DLL 内の他の`DllMain`関数を呼び出す前に、アプリケーションが初期化関数を呼び出すように要求することができます。

<a name="initializing-non-mfc-dlls"></a>

### <a name="initialize-ordinary-non-mfc-dlls"></a>通常の (非 MFC) Dll を初期化する

Vcruntime によって指定`_DllMainCRTStartup`されたエントリポイントを使用する通常の (非 MFC) dll で独自の初期化を実行するには、DLL ソースコードにと呼ばれる`DllMain`関数が含まれている必要があります。 次のコードは、の`DllMain`定義がどのようなものかを示す基本的なスケルトンを示しています。

```cpp
#include <windows.h>

extern "C" BOOL WINAPI DllMain (
    HINSTANCE const instance,  // handle to DLL module
    DWORD     const reason,    // reason for calling function
    LPVOID    const reserved)  // reserved
{
    // Perform actions based on the reason for calling.
    switch (reason)
    {
    case DLL_PROCESS_ATTACH:
        // Initialize once for each new process.
        // Return FALSE to fail DLL load.
        break;

    case DLL_THREAD_ATTACH:
        // Do thread-specific initialization.
        break;

    case DLL_THREAD_DETACH:
        // Do thread-specific cleanup.
        break;

    case DLL_PROCESS_DETACH:
        // Perform any necessary cleanup.
        break;
    }
    return TRUE;  // Successful DLL_PROCESS_ATTACH.
}
```

> [!NOTE]
> 以前の Windows SDK のドキュメントでは、/ENTRY オプションを使用して、リンカーコマンドラインに DLL エントリポイント関数の実際の名前を指定する必要があることが示されています。 Visual Studio では、エントリポイント関数の名前が`DllMain`の場合に/entry オプションを使用する必要はありません。 実際、/entry オプションを使用して、エントリポイント関数に以外`DllMain`の名前を指定した場合、エントリポイント関数がを持つ`_DllMainCRTStartup`同じ初期化呼び出しを行う場合を除き、CRT は適切に初期化されません。

<a name="initializing-regular-dlls"></a>

### <a name="initialize-regular-mfc-dlls"></a>レギュラー MFC Dll の初期化

通常の mfc dll には`CWinApp`オブジェクトが含まれているので、mfc アプリケーションと同じ場所で初期化タスクと終了タスクを`InitInstance`実行する必要があります。 `CWinApp`DLL の派生クラスのおよび`ExitInstance`メンバー関数では、講義. MFC には、 `DllMain`および`_DllMainCRTStartup` `DLL_PROCESS_ATTACH` `DllMain`のによって呼び出される関数が用意されているため、独自の関数を記述しないでください。 `DLL_PROCESS_DETACH` MFC に用意さ`DllMain`れて`InitInstance`いる関数は、dll が読み込ま`ExitInstance`れるときにを呼び出し、dll がアンロードされる前にを呼び出します。

通常の MFC DLL では、その`InitInstance`関数で[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)と[TlsGetValue](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsgetvalue)を呼び出すことによって、複数のスレッドを追跡できます。 これらの関数は、DLL がスレッド固有のデータを追跡できるようにします。

Mfc に動的にリンクするレギュラー MFC DLL では、mfc OLE、MFC Database (または DAO)、または MFC ソケットのサポートをそれぞれ使用している場合は、mfc 拡張dll のデバッグ、mfco バージョンd. .DLL、および mfco*バージョン*d. .dll (versionはバージョン番号です) が自動的にリンクされます。 通常の MFC DLL の`CWinApp::InitInstance`で使用している各 dll に対して、次の定義済みの初期化関数のいずれかを呼び出す必要があります。

|MFC のサポートの種類|呼び出す初期化関数|
|-------------------------|-------------------------------------|
|MFC OLE (MFCO*バージョン*d. .dll)|`AfxOleInitModule`|
|MFC データベース (MFCD*バージョン*d. .dll)|`AfxDbInitModule`|
|MFC ソケット (MFCN*バージョン*d. .dll)|`AfxNetInitModule`|

<a name="initializing-extension-dlls"></a>

### <a name="initialize-mfc-extension-dlls"></a>MFC 拡張 Dll の初期化

Mfc 拡張 dll には、(通常`CWinApp`の mfc dll と同様に) 派生オブジェクトがないため、mfc dll ウィザードによって生成さ`DllMain`れる関数に初期化コードと終了コードを追加する必要があります。

ウィザードには、MFC 拡張 Dll 用の次のコードが用意されています。 コードでは、 `PROJNAME`はプロジェクトの名前のプレースホルダーです。

```cpp
#include "pch.h" // For Visual Studio 2017 and earlier, use "stdafx.h"
#include <afxdllx.h>

#ifdef _DEBUG
#define new DEBUG_NEW
#undef THIS_FILE
static char THIS_FILE[] = __FILE__;
#endif
static AFX_EXTENSION_MODULE PROJNAMEDLL = { NULL, NULL };

extern "C" int APIENTRY
DllMain(HINSTANCE hInstance, DWORD dwReason, LPVOID lpReserved)
{
   if (dwReason == DLL_PROCESS_ATTACH)
   {
      TRACE0("PROJNAME.DLL Initializing!\n");

      // MFC extension DLL one-time initialization
      AfxInitExtensionModule(PROJNAMEDLL,
                                 hInstance);

      // Insert this DLL into the resource chain
      new CDynLinkLibrary(Dll3DLL);
   }
   else if (dwReason == DLL_PROCESS_DETACH)
   {
      TRACE0("PROJNAME.DLL Terminating!\n");
   }
   return 1;   // ok
}
```

初期化中に`CDynLinkLibrary`新しいオブジェクトを作成すると、MFC 拡張 DLL `CRuntimeClass`がオブジェクトまたはリソースをクライアントアプリケーションにエクスポートできるようになります。

1つ以上の通常の mfc dll から mfc 拡張 dll を使用する場合は、オブジェクトを`CDynLinkLibrary`作成する初期化関数をエクスポートする必要があります。 この関数は、MFC 拡張 DLL を使用する通常の MFC Dll から呼び出す必要があります。 この初期化関数を呼び出す適切な場所は、mfc `InitInstance`拡張 dll のエクスポートされたクラス`CWinApp`または関数のいずれかを使用する前に、通常の mfc DLL の派生オブジェクトのメンバー関数に含まれています。

`COleObjectFactory` `AfxInitExtensionModule` `CRuntimeClass` MFC DLL ウィザードによって生成さ`CDynLinkLibrary`れるでは、を呼び出すことによって、モジュールのランタイムクラス (構造体) だけでなく、オブジェクトの作成時に使用するオブジェクトファクトリ (オブジェクト) がキャプチャされます。 `DllMain` の`AfxInitExtensionModule`戻り値を確認する必要があります。から`AfxInitExtensionModule`0 の値が返された場合`DllMain`は、関数からゼロを返します。

MFC 拡張 DLL が実行可能ファイルに明示的にリンクされる場合 (つまり`AfxLoadLibrary` 、実行可能ファイルが DLL にリンクするために呼び出される`AfxTermExtensionModule`場合`DLL_PROCESS_DETACH`) は、の呼び出しをに追加する必要があります。 この関数を使用すると、各プロセスが mfc 拡張 dll からデタッチされたときに mfc 拡張 dll をクリーンアップできます (プロセスが終了したとき、または dll `AfxFreeLibrary`が呼び出しの結果としてアンロードされたときに発生します)。 MFC 拡張 DLL がアプリケーションに暗黙的にリンクされる場合、へ`AfxTermExtensionModule`の呼び出しは必要ありません。

MFC 拡張 dll に明示的にリンクするアプリケーション`AfxTermExtensionModule`は、dll を解放するときにを呼び出す必要があります。 また、アプリケーションで`AfxLoadLibrary`複数`AfxFreeLibrary`のスレッドを使用する場合`LoadLibrary`は`FreeLibrary`、と (Win32 関数およびの代わりに) を使用する必要があります。 および`AfxLoadLibrary`を`AfxFreeLibrary`使用すると、mfc 拡張 DLL が読み込まれてアンロードされたときに実行される起動コードとシャットダウンコードが、mfc のグローバル状態を破壊することがなくなります。

が呼び出された時点`DllMain`で mfcx0.dll が完全に初期化されているため、(mfc の16ビットバージョンとは異なり) で`DllMain`メモリを割り当て、mfc 関数を呼び出すことができます。

拡張 dll では、 `DLL_THREAD_ATTACH` `DllMain`関数のおよび`DLL_THREAD_DETACH`ケースを処理することによって、マルチスレッド処理を行うことができます。 これらのケースは、 `DllMain`スレッドが DLL からアタッチおよびデタッチするときにに渡されます。 Dll がアタッチされているときに[TlsAlloc](/windows/win32/api/processthreadsapi/nf-processthreadsapi-tlsalloc)を呼び出すと、DLL は dll にアタッチされているすべてのスレッドに対してスレッドローカルストレージ (TLS) インデックスを維持できます。

ヘッダーファイル Afxdllx には、および`AFX_EXTENSION_MODULE` `CDynLinkLibrary`の定義など、MFC 拡張 dll で使用される構造体の特別な定義が含まれていることに注意してください。 このヘッダーファイルは、MFC 拡張 DLL に含める必要があります。

> [!NOTE]
>  *Pch* (Visual Studio 2017 以前では*stdafx.h* ) でマクロ`_AFX_NO_XXX`を定義したり、未定義にしたりすることはできません。 これらのマクロは、特定のターゲットプラットフォームでその機能がサポートされているかどうかを確認するためだけに存在します。 これらのマクロをチェックするようにプログラムを記述できます`#ifndef _AFX_NO_OLE_SUPPORT`(たとえば、)。ただし、プログラムでこれらのマクロを定義または未定義にすることはできません。

マルチスレッド処理を行うサンプル初期化関数は、Windows SDK の[ダイナミックリンクライブラリにあるスレッドローカルストレージを使用](/windows/win32/Dlls/using-thread-local-storage-in-a-dynamic-link-library)する場合に含まれます。 このサンプルにはという`LibMain`エントリポイント関数が含まれていますが、MFC および C ランタイムライブラリで動作するように、この関数`DllMain`に名前を付けてください。

## <a name="see-also"></a>関連項目

[Visual Studio での C/C++ Dll の作成](dlls-in-visual-cpp.md)<br/>
[DllMain エントリポイント](/windows/win32/Dlls/dllmain)<br/>
[ダイナミックリンクライブラリのベストプラクティス](/windows/win32/Dlls/dynamic-link-library-best-practices)
