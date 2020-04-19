---
title: '方法: WRL を使用したイベントの処理'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 1c77543f-7b0c-4a94-93bf-e3225885ed76
ms.openlocfilehash: 959a85d6cf6de666ae56d09035acefe9a3828ae8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398317"
---
# <a name="how-to-handle-events-using-wrl"></a>方法: WRL を使用したイベントの処理

このドキュメントでは、Windows ランタイム C++ テンプレート ライブラリ (WRL) を使用してサブスクライブして、Windows ランタイム オブジェクトのイベントを処理する方法を示します。

そのコンポーネントのインスタンスを作成し、プロパティ値を取得する基本的な例は、次を参照してください。[方法。アクティブ化し、Windows ランタイム コンポーネントを使用して、](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)します。

## <a name="subscribing-to-and-handling-events"></a>イベントのサブスクライブと処理

次の手順では `ABI::Windows::System::Threading::IDeviceWatcher` オブジェクトを開始し、イベント ハンドラーを使用して進行状況を監視します。 `IDeviceWatcher` インターフェイスを使用すると、デバイスを非同期的にまたはバックグラウンドで列挙でき、デバイスが追加、削除、または変更された場合に通知を受け取ることができます。 [コールバック](callback-function-wrl.md)をバック グラウンド操作の結果を処理するイベント ハンドラーを指定するには有効にするので、関数はこの例の重要な部分です。 完全な例を次に示します。

> [!WARNING]
> 通常は、ユニバーサル Windows プラットフォーム アプリで Windows ランタイム C++ テンプレート ライブラリを使用して、この例は、図のコンソール アプリを使用します。 などの関数`wprintf_s`ユニバーサル Windows プラットフォーム アプリからは使用できません。 型およびユニバーサル Windows プラットフォーム アプリで使用できる関数の詳細については、次を参照してください。[ユニバーサル Windows プラットフォーム アプリでサポートされない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)と[Win32 および COM UWP アプリの](/uwp/win32-and-com/win32-and-com-for-uwp-apps)します。

1. 含まれます (`#include`) 必須の Windows ランタイム、Windows ランタイム C++ テンプレート ライブラリ、または C++ 標準ライブラリ ヘッダー。

   [!code-cpp[wrl-consume-event#2](../codesnippet/CPP/how-to-handle-events-using-wrl_1.cpp)]

   `Windows.Devices.Enumeration.h` デバイスを列挙するために必要な型を宣言します。

   コードを読みやすくするために、.cpp ファイルでは `using namespace` ディレクティブを使用することをお勧めします。

2. アプリ用のローカル変数を宣言します。 この例では、後でイベント サブスクリプションを解除できるようにするために、列挙されたデバイスと登録トークンの数を保持します。

   [!code-cpp[wrl-consume-event#7](../codesnippet/CPP/how-to-handle-events-using-wrl_2.cpp)]

3. Windows ランタイムを初期化します。

   [!code-cpp[wrl-consume-event#3](../codesnippet/CPP/how-to-handle-events-using-wrl_3.cpp)]

4. 作成、[イベント](event-class-wrl.md)をメイン アプリ列挙プロセスの完了を同期するオブジェクト。

   [!code-cpp[wrl-consume-event#4](../codesnippet/CPP/how-to-handle-events-using-wrl_4.cpp)]

   > [!NOTE]
   > このイベントは、コンソール アプリケーションの一部としてデモのみを目的としています。 この例では、アプリケーションが終了する前に非同期操作が完了したことを確認するために、イベントを使用します。 ほとんどのアプリケーションでは、通常は非同期操作の完了を待機しません。

5. `IDeviceWatcher` インターフェイスに対応するアクティベーション ファクトリを作成します。

   [!code-cpp[wrl-consume-event#5](../codesnippet/CPP/how-to-handle-events-using-wrl_5.cpp)]

   Windows ランタイム型を識別するために完全修飾名を使用します。 `RuntimeClass_Windows_Devices_Enumeration_DeviceInformation`パラメーターは、文字列は、Windows ランタイムによって提供され、必要なランタイム クラス名を含むです。

6. `IDeviceWatcher` オブジェクトを作成します。

   [!code-cpp[wrl-consume-event#6](../codesnippet/CPP/how-to-handle-events-using-wrl_6.cpp)]

7. `Callback` 関数を使用して `Added`、`EnumerationCompleted`、および `Stopped` の各イベントをサブスクライブします。

   [!code-cpp[wrl-consume-event#8](../codesnippet/CPP/how-to-handle-events-using-wrl_7.cpp)]

   `Added` イベント ハンドラーは、列挙されたデバイス数をインクリメントします。 デバイスが10 個検出されると、列挙プロセスが停止します。

   `Stopped` イベント ハンドラーは、イベント ハンドラーを削除し、完了イベントを設定します。

   `EnumerationCompleted` イベント ハンドラーは、列挙プロセスを停止します。 このイベントはデバイスの数が 10 未満である場合に処理されます。

   > [!TIP]
   > この例では、ラムダ式を使用してコールバックを定義します。 関数オブジェクト (ファンクター)、関数ポインターを使用することもできます。 または[std::function](../../standard-library/function-class.md)オブジェクト。 ラムダ式について詳しくは、「[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)」をご覧ください。

8. 列挙プロセスを開始します。

   [!code-cpp[wrl-consume-event#9](../codesnippet/CPP/how-to-handle-events-using-wrl_8.cpp)]

9. 列挙プロセスが完了するのを待機し、メッセージを出力します。 すべての `ComPtr` オブジェクトと RAII オブジェクトは自動的にスコープから外れて解放されます。

   [!code-cpp[wrl-consume-event#10](../codesnippet/CPP/how-to-handle-events-using-wrl_9.cpp)]

完全な例を次に示します。

[!code-cpp[wrl-consume-event#1](../codesnippet/CPP/how-to-handle-events-using-wrl_10.cpp)]

## <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするにコピーし、Visual Studio プロジェクトに貼り付けるかという名前のファイルに貼り付ける`wrl-consume-events.cpp`で、次のコマンドを実行し、 **Visual Studio コマンド プロンプト**ウィンドウ。

`cl.exe wrl-consume-events.cpp runtimeobject.lib`

## <a name="see-also"></a>関連項目

[Windows ランタイム C++ テンプレート ライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)