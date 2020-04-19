---
title: '方法: WRL を使用して非同期操作を完了します。'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 02173eae-731b-49bc-b412-f1f69388b99d
ms.openlocfilehash: 09c341e5e3d4f6007d5d5f66b7c06e1f0af5a65c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398343"
---
# <a name="how-to-complete-asynchronous-operations-using-wrl"></a>方法: WRL を使用して非同期操作を完了します。

このドキュメントでは、Windows ランタイム C++ テンプレート ライブラリ (WRL) を使用して、非同期操作を開始し、操作が完了した時点に作業を実行する方法を示します。

このドキュメントでは、2 つの例を示します。 最初の例では、非同期タイマーを開始し、そのタイマーが期限切れになるのを待機します。 この例では、タイマー オブジェクトを作成するときに、非同期アクションを指定します。 2 番目の例では、バックグラウンド ワーカー スレッドを実行します。 この例を返す Windows ランタイム メソッドを使用する方法を示しています、`IAsyncInfo`インターフェイス。 [コールバック](callback-function-wrl.md)非同期操作の結果を処理するイベント ハンドラーを指定することができるため、関数はどちらの例の重要な部分です。

コンポーネントのインスタンスを作成し、プロパティ値を取得する基本的な例は、次を参照してください。[方法。アクティブ化し、Windows ランタイム コンポーネントを使用して、](how-to-activate-and-use-a-windows-runtime-component-using-wrl.md)します。

> [!TIP]
> これらの例では、コールバックを定義するためにラムダ式を使用します。 関数オブジェクト (ファンクター)、関数ポインターを使用することもできます。 または[std::function](../../standard-library/function-class.md)オブジェクト。 C++ のラムダ式の詳細については、次を参照してください。[ラムダ式](../../cpp/lambda-expressions-in-cpp.md)します。

## <a name="example-working-with-a-timer"></a>例:タイマーを使用した作業

以下の手順では、非同期タイマーを開始し、そのタイマーが期限切れになるのを待機します。 完全な例を次に示します。

> [!WARNING]
> 通常は、ユニバーサル Windows プラットフォーム (UWP) アプリで Windows ランタイム C++ テンプレート ライブラリを使用して、この例は、図のコンソール アプリを使用します。 などの関数`wprintf_s`UWP アプリからは使用できません。 型および UWP アプリで使用できる関数の詳細については、次を参照してください。[ユニバーサル Windows プラットフォーム アプリでサポートされない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)と[Win32 および COM UWP アプリの](/uwp/win32-and-com/win32-and-com-for-uwp-apps)します。

1. 含まれます (`#include`) 必須の Windows ランタイム、Windows ランタイム C++ テンプレート ライブラリ、または C++ 標準ライブラリ ヘッダー。

   [!code-cpp[wrl-consume-async#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_1.cpp)]

   `Windows.System.Threading.h` 非同期のタイマーを使用するために必要な型を宣言します。

   コードを読みやすくするために、.cpp ファイルでは `using namespace` ディレクティブを使用することをお勧めします。

2. Windows ランタイムを初期化します。

   [!code-cpp[wrl-consume-async#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_2.cpp)]

3. `ABI::Windows::System::Threading::IThreadPoolTimer` インターフェイスに対応するアクティベーション ファクトリを作成します。

   [!code-cpp[wrl-consume-async#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_3.cpp)]

   Windows ランタイム型を識別するために完全修飾名を使用します。 `RuntimeClass_Windows_System_Threading_ThreadPoolTimer`パラメーターは、文字列は、Windows ランタイムによって提供され、必要なランタイム クラス名を含むです。

4. 作成、[イベント](event-class-wrl.md)タイマーのコールバックをメイン アプリを同期するオブジェクト。

   [!code-cpp[wrl-consume-async#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_4.cpp)]

   > [!NOTE]
   > このイベントは、コンソール アプリケーションの一部としてデモのみを目的としています。 この例では、アプリケーションが終了する前に非同期操作が完了したことを確認するために、イベントを使用します。 ほとんどのアプリケーションでは、通常は非同期操作の完了を待機しません。

5. 2 秒後に期限切れになる `IThreadPoolTimer` オブジェクトを作成します。 `Callback` 関数を使用して、イベント ハンドラー (`ABI::Windows::System::Threading::ITimerElapsedHandler` オブジェクト) を作成します。

   [!code-cpp[wrl-consume-async#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_5.cpp)]

6. メッセージをコンソールに出力し、タイマーからのコールバックが完了するのを待機します。 すべての `ComPtr` オブジェクトと RAII オブジェクトは自動的にスコープから外れて解放されます。

   [!code-cpp[wrl-consume-async#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_6.cpp)]

完全な例を次に示します。

[!code-cpp[wrl-consume-async#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_7.cpp)]

### <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするにコピーし、Visual Studio プロジェクトに貼り付けるかという名前のファイルに貼り付ける`wrl-consume-async.cpp`Visual Studio コマンド プロンプト ウィンドウで、次のコマンドを実行します。

`cl.exe wrl-consume-async.cpp runtimeobject.lib`

## <a name="example-working-with-a-background-thread"></a>例:バック グラウンド スレッドの操作

以下の手順では、ワーカー スレッドを開始し、そのスレッドによって実行されるアクションを定義します。 完全な例を次に示します。

> [!TIP]
> この例では、`ABI::Windows::Foundation::IAsyncAction` インターフェイスを使用して作業する方法を示します。 `IAsyncInfo`、`IAsyncAction`、`IAsyncActionWithProgress`、`IAsyncOperation`、および `IAsyncOperationWithProgress` を実装するすべてのインターフェイスに、このパターンを追加できます。

1. 含まれます (`#include`) 必須の Windows ランタイム、Windows ランタイム C++ テンプレート ライブラリ、または C++ 標準ライブラリ ヘッダー。

   [!code-cpp[wrl-consume-asyncOp#2](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_8.cpp)]

   Windows.System.Threading.h は、ワーカー スレッドを使用するために必要な型を宣言します。

   コードを読みやすくするために、.cpp ファイルでは `using namespace` ディレクティブを使用することをお勧めします。

2. Windows ランタイムを初期化します。

   [!code-cpp[wrl-consume-asyncOp#3](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_9.cpp)]

3. `ABI::Windows::System::Threading::IThreadPoolStatics` インターフェイスに対応するアクティベーション ファクトリを作成します。

   [!code-cpp[wrl-consume-asyncOp#4](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_10.cpp)]

4. 作成、[イベント](event-class-wrl.md)メイン アプリケーションをワーカー スレッドの完了を同期するオブジェクト。

   [!code-cpp[wrl-consume-asyncOp#5](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_11.cpp)]

   > [!NOTE]
   > このイベントは、コンソール アプリケーションの一部としてデモのみを目的としています。 この例では、アプリケーションが終了する前に非同期操作が完了したことを確認するために、イベントを使用します。 ほとんどのアプリケーションでは、通常は非同期操作の完了を待機しません。

5. ワーカー スレッドを作成するには、`IThreadPoolStatics::RunAsync` メソッドを呼び出します。 アクションを定義するには、`Callback` 関数を使用します。

   [!code-cpp[wrl-consume-asyncOp#6](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_12.cpp)]

   `IsPrime` 関数は、この後に続く完全な例で定義します。

6. メッセージをコンソールに出力し、スレッドが完了するのを待機します。 すべての `ComPtr` オブジェクトと RAII オブジェクトは自動的にスコープから外れて解放されます。

   [!code-cpp[wrl-consume-asyncOp#7](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_13.cpp)]

完全な例を次に示します。

[!code-cpp[wrl-consume-asyncOp#1](../codesnippet/CPP/how-to-complete-asynchronous-operations-using-wrl_14.cpp)]

### <a name="compiling-the-code"></a>コードのコンパイル

コードをコンパイルするにコピーし、Visual Studio プロジェクトに貼り付けるかという名前のファイルに貼り付ける`wrl-consume-asyncOp.cpp`で、次のコマンドを実行し、 **Visual Studio コマンド プロンプト**ウィンドウ。

`cl.exe wrl-consume-asyncOp.cpp runtimeobject.lib`

## <a name="see-also"></a>関連項目

[Windows ランタイム C++ テンプレート ライブラリ (WRL)](windows-runtime-cpp-template-library-wrl.md)