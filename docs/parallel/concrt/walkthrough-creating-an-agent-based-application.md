---
title: 'チュートリアル: エージェント ベースのアプリケーションの作成'
ms.date: 04/25/2019
helpviewer_keywords:
- asynchronous agents, creating
- agent class, example
ms.assetid: 730f42ce-6d58-4753-b948-fd9c9ef2ce6c
ms.openlocfilehash: 3ece04811a75fba22db447875dc6ed08c22987b5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142050"
---
# <a name="walkthrough-creating-an-agent-based-application"></a>チュートリアル: エージェント ベースのアプリケーションの作成

ここでは、基本的なエージェント ベースのアプリケーションの作成方法について説明します。 このチュートリアルでは、テキスト ファイルから非同期的にデータを読み取るエージェントを作成できます。 このアプリケーションでは、Adler-32 チェックサム アルゴリズムを使用して、そのファイルの内容のチェックサムを計算します。

## <a name="prerequisites"></a>前提条件

このチュートリアルを完了するには、次のトピックを理解する必要があります。

- [非同期エージェント](../../parallel/concrt/asynchronous-agents.md)

- [非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)

- [メッセージ パッシング関数](../../parallel/concrt/message-passing-functions.md)

- [同期データ構造](../../parallel/concrt/synchronization-data-structures.md)

## <a name="top"></a> セクション

このチュートリアルでは、次のタスクを実行する方法を示します。

- [コンソール アプリケーションの作成](#createapplication)

- [File_reader クラスの作成](#createagentclass)

- [アプリケーションでの file_reader クラスの使用](#useagentclass)

## <a name="createapplication"></a>コンソールアプリケーションの作成

このセクションでは、プログラムでC++使用するヘッダーファイルを参照するコンソールアプリケーションを作成する方法について説明します。 最初の手順は、使用している Visual Studio のバージョンによって異なります。 このページの左上にあるバージョンセレクターが正しく設定されていることを確認します。

::: moniker range="vs-2019"

### <a name="to-create-a-c-console-application-in-visual-studio-2019"></a>Visual Studio 2019 C++でコンソールアプリケーションを作成するには

1. メインメニューから、[**ファイル**>**新しい**>**プロジェクト**] を選択して **[新しいプロジェクトの作成]** ダイアログボックスを開きます。

1. ダイアログの上部で、 **[言語]** を **[C++]** に、 **[プラットフォーム]** を **[Windows]** に、 **[プロジェクト タイプ]** を **[コンソール]** に設定します。 

1. フィルター処理されたプロジェクト タイプの一覧から、 **[コンソール アプリ]** を選択して、 **[次へ]** を選択します。 次のページで、プロジェクトの名前として「`BasicAgent`」と入力し、必要に応じてプロジェクトの場所を指定します。

1. **[作成]** ボタンをクリックしてプロジェクトを作成します。

1. **ソリューションエクスプローラー**でプロジェクトノードを右クリックし、 **[プロパティ]** を選択します。 **構成プロパティ** > **CC++ /**  > **プリコンパイル済み**ヘッダー > プリコンパイル済み**ヘッダー**  の順に選択し、**作成** を選択します。

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-c-console-application-in-visual-studio-2017-and-earlier"></a>Visual Studio 2017 C++以前でコンソールアプリケーションを作成するには

1. **[ファイル]** メニューの **[新規作成]** をクリックし、 **[プロジェクト]** をクリックして **[新しいプロジェクト]** ダイアログボックスを表示します。

1. **[新しいプロジェクト]** ダイアログボックスの **[プロジェクトの種類]** ペインで**ビジュアルC++** ノードを選択し、 **[テンプレート]** ペインで **[Win32 コンソールアプリケーション]** を選択します。 プロジェクトの名前 (たとえば、`BasicAgent`) を入力し、 **[OK]** をクリックして、 **Win32 コンソールアプリケーションウィザード**を表示します。

1. **[Win32 コンソールアプリケーションウィザード]** ダイアログボックスで、 **[完了]** をクリックします。

::: moniker-end

1. *.Pch* (Visual Studio 2017 以前の*stdafx.h* ) で、次のコードを追加します。

[!code-cpp[concrt-basic-agent#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_1.h)]

   ヘッダーファイル agents. h には、 [concurrency:: agent](../../parallel/concrt/reference/agent-class.md)クラスの機能が含まれています。

1. アプリケーションをビルドして実行することにより、アプリケーションが正常に作成されたことを確認します。 アプリケーションをビルドするには、 **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。 アプリケーションが正常にビルドされた場合は、 **[デバッグ]** メニューの **[デバッグ開始]** をクリックしてアプリケーションを実行します。

[[トップ](#top)]

## <a name="createagentclass"></a>File_reader クラスの作成

ここでは、`file_reader` クラスの作成方法について説明します。 ランタイムは、各エージェントがそれぞれのコンテキストで処理を実行するようにスケジュールを設定します。 そのため、処理を同期的に実行する一方で、他のコンポーネントとは非同期的に通信するエージェントを作成できます。 `file_reader` クラスでは、指定された入力ファイルからデータを読み取り、そのファイルのデータを指定されたターゲット コンポーネントに送信します。

#### <a name="to-create-the-file_reader-class"></a>file_reader クラスを作成するには

1. 新しい C++ ヘッダー ファイルをプロジェクトに追加します。 これを行うには、**ソリューションエクスプローラー**で **[ヘッダーファイル]** ノードを右クリックし、 **[追加]** をクリックして、 **[新しい項目]** をクリックします。 **[テンプレート]** ペインで、 **[ヘッダーファイル (.h)]** を選択します。 **[新しい項目の追加]** ダイアログボックスで、 **[名前]** ボックスに「`file_reader.h`」と入力し、 **[追加]** をクリックします。

1. file_reader.h に、次のコードを追加します。

[!code-cpp[concrt-basic-agent#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_2.h)]

1. file_reader.h に、`file_reader` から派生する `agent` という名前のクラスを作成します。

[!code-cpp[concrt-basic-agent#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_3.h)]

1. クラスの `private` セクションに次のデータ メンバーを追加します。

[!code-cpp[concrt-basic-agent#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_4.h)]

   `_file_name` メンバーは、エージェントが読み取る対象のファイル名です。 `_target` メンバーは、エージェントがファイルの内容を書き込む[concurrency:: ITarget](../../parallel/concrt/reference/itarget-class.md)オブジェクトです。 `_error` メンバーでは、エージェントの有効期間中に発生したエラーを保持します。

1. `file_reader` クラスの `public` セクションに `file_reader` コンストラクターの次のコードを追加します。

[!code-cpp[concrt-basic-agent#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_5.h)]

   各コンストラクター オーバーロードによって、`file_reader` データ メンバーが設定されます。 2 番目と 3 番目のコンストラクター オーバーロードによって、アプリケーションでエージェントに対して特定のスケジューラを使用できるようにします。 最初のオーバーロードでは、エージェントに対して既定のスケジューラを使用します。

1. `get_error` クラスのパブリック セクションに `file_reader` メソッドを追加します。

[!code-cpp[concrt-basic-agent#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_6.h)]

   `get_error` メソッドにより、エージェントの有効期間中に発生したエラーを取得します。

1. クラスの `protected` セクションで、 [concurrency:: agent:: run](reference/agent-class.md#run)メソッドを実装します。

[!code-cpp[concrt-basic-agent#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_7.h)]

`run` メソッドによりファイルを開き、そこからデータを読み取ります。 `run` メソッドでは、例外処理を使用して、ファイルの処理中に発生したエラーをキャプチャします。

   このメソッドは、ファイルからデータを読み取るたびに、 [concurrency:: asend](reference/concurrency-namespace-functions.md#asend)関数を呼び出して、そのデータをターゲットバッファーに送信します。 処理の終了を示す際には、空の文字列をターゲット バッファーに送信します。

file_reader.h の内容全体の例を次に示します。

[!code-cpp[concrt-basic-agent#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_8.h)]

[[トップ](#top)]

## <a name="useagentclass"></a>アプリケーションでの file_reader クラスの使用

ここでは、`file_reader` クラスを使用して、テキスト ファイルの内容を読み取る方法について説明します。 また、このファイルデータを受け取り、その Adler-32 チェックサムを計算する[concurrency:: call](../../parallel/concrt/reference/call-class.md)オブジェクトを作成する方法についても説明します。

#### <a name="to-use-the-file_reader-class-in-your-application"></a>アプリケーションで file_reader クラスを使用するには

1. BasicAgent.cpp に、次の `#include` ステートメントを追加します。

[!code-cpp[concrt-basic-agent#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_9.cpp)]

1. BasicAgent.cpp に、次の `using` ディレクティブを追加します。

[!code-cpp[concrt-basic-agent#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_10.cpp)]

1. `_tmain` 関数で、処理の終了を通知する[concurrency:: event](../../parallel/concrt/reference/event-class.md)オブジェクトを作成します。

[!code-cpp[concrt-basic-agent#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_11.cpp)]

1. データを受け取ったときにチェックサムを更新する `call` オブジェクトを作成します。

[!code-cpp[concrt-basic-agent#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_12.cpp)]

   また、この `call` オブジェクトは、処理の終了を通知する空の文字列を受け取ると、`event` オブジェクトを設定します。

1. test.txt ファイルから読み取り、そのファイルの内容を `file_reader` オブジェクトに書き込む `call` オブジェクトを作成します。

[!code-cpp[concrt-basic-agent#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_13.cpp)]

1. エージェントを開始し、エージェントが終了するまで待機します。

[!code-cpp[concrt-basic-agent#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_14.cpp)]

1. `call` オブジェクトがすべてのデータを受け取り、終了するまで待機します。

[!code-cpp[concrt-basic-agent#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_15.cpp)]

1. エラーが発生していないかどうかファイル リーダーを確認します。 エラーが発生していない場合は、最終的な Adler-32 チェックサムを計算し、その結果をコンソールに出力します。

[!code-cpp[concrt-basic-agent#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_16.cpp)]

完全な BasicAgent.cpp ファイルの例を次に示します。

[!code-cpp[concrt-basic-agent#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-an-agent-based-application_17.cpp)]

[[トップ](#top)]

## <a name="sample-input"></a>入力のサンプル

これは、入力ファイル text.txt の内容のサンプルです。

```Output
The quick brown fox
jumps
over the lazy dog
```

## <a name="sample-output"></a>出力例

入力のサンプルを使用すると、このプログラムでは、次の出力が生成されます。

```Output
Adler-32 sum is fefb0d75
```

## <a name="robust-programming"></a>堅牢性の高いプログラミング

データ メンバーへの同時アクセスを回避するために、クラスの `protected` セクションまたは `private` セクションに、処理を実行するメソッドを追加することをお勧めします。 クラスの `public` セクションには、メッセージをエージェントに送信するメソッドまたはメッセージをエージェントから受信するメソッドのみを追加してください。

常に[concurrency:: agent::d 1 つ](reference/agent-class.md#done)のメソッドを呼び出して、エージェントを完了状態に移行します。 通常、このメソッドは、`run` メソッドから制御が戻る前に呼び出します。

## <a name="next-steps"></a>次の手順

エージェントベースのアプリケーションの別の例については、「[チュートリアル: join を使用したデッドロックの回避](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)」を参照してください。

## <a name="see-also"></a>参照

[非同期エージェント ライブラリ](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[メッセージ パッシング関数](../../parallel/concrt/message-passing-functions.md)<br/>
[同期データ構造](../../parallel/concrt/synchronization-data-structures.md)<br/>
[チュートリアル: join を使用したデッドロックの防止](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md)
