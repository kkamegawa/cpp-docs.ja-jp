---
title: 'チュートリアル: ユーザー インターフェイス スレッドからの処理の除去'
ms.date: 08/19/2019
helpviewer_keywords:
- user-interface threads, removing work from [Concurrency Runtime]
- removing work from user-interface threads [Concurrency Runtime]
ms.assetid: a4a65cc2-b3bc-4216-8fa8-90529491de02
ms.openlocfilehash: 518044d4e3adea44c3776793c8277939076066d6
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140705"
---
# <a name="walkthrough-removing-work-from-a-user-interface-thread"></a>チュートリアル: ユーザー インターフェイス スレッドからの処理の除去

このドキュメントでは、同時実行ランタイムを使用して、Microsoft Foundation Classes (MFC) アプリケーションのユーザーインターフェイス (UI) スレッドによって実行される作業をワーカースレッドに移動する方法について説明します。 このドキュメントでは、時間のかかる描画操作のパフォーマンスを向上させる方法についても説明します。

ワーカースレッドに対してブロッキング操作 (描画など) をオフロードすることによって UI スレッドから作業を削除すると、アプリケーションの応答性が向上します。 このチュートリアルでは、マンデルブロフラクタルを生成する描画ルーチンを使用して、時間のかかるブロッキング操作を示します。 また、マンデルブロフラクタルの生成も、並列処理の候補として適しています。これは、各ピクセルの計算が他のすべての計算から独立しているためです。

## <a name="prerequisites"></a>前提条件

このチュートリアルを開始する前に、次のトピックを参照してください。

- [タスクの並列化](../../parallel/concrt/task-parallelism-concurrency-runtime.md)

- [非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)

- [メッセージ パッシング関数](../../parallel/concrt/message-passing-functions.md)

- [並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)

- [PPL における取り消し処理](cancellation-in-the-ppl.md)

また、このチュートリアルを開始する前に、MFC アプリケーションの開発と GDI + の基本について理解しておくことをお勧めします。 MFC の詳細については、「 [Mfc Desktop Applications](../../mfc/mfc-desktop-applications.md)」を参照してください。 GDI + の詳細については、「 [Gdi +](/windows/win32/gdiplus/-gdiplus-gdi-start)」を参照してください。

## <a name="top"></a> セクション

このチュートリアルは、次のセクションで構成されています。

- [MFC アプリケーションの作成](#application)

- [ブロマンアプリケーションのシリアルバージョンの実装](#serial)

- [ユーザーインターフェイススレッドからの作業の削除](#removing-work)

- [描画パフォーマンスの向上](#performance)

- [キャンセルのサポートの追加](#cancellation)

## <a name="application"></a>MFC アプリケーションの作成

ここでは、基本的な MFC アプリケーションを作成する方法について説明します。

### <a name="to-create-a-visual-c-mfc-application"></a>Visual C++ MFC アプリケーションを作成するには

1. **Mfc アプリケーションウィザード**を使用して、すべての既定の設定を含む mfc アプリケーションを作成します。 お使いのバージョンの Visual Studio のウィザードを開く方法については[、「チュートリアル: 新しい MFC シェルコントロールの使用](../../mfc/walkthrough-using-the-new-mfc-shell-controls.md)」を参照してください。

1. プロジェクトの名前 (たとえば、`Mandelbrot`) を入力し、[ **OK** ] をクリックして**MFC アプリケーションウィザード**を表示します。

1. [**アプリケーションの種類**] ペインで、[**単一ドキュメント**] を選択します。 [**ドキュメント/ビューアーキテクチャのサポート**] チェックボックスがオフになっていることを確認します。

1. [**完了**] をクリックしてプロジェクトを作成し、 **MFC アプリケーションウィザード**を閉じます。

   アプリケーションをビルドして実行することにより、アプリケーションが正常に作成されたことを確認します。 アプリケーションをビルドするには、[**ビルド**] メニューの [**ソリューションのビルド**] をクリックします。 アプリケーションが正常にビルドされた場合は、[**デバッグ**] メニューの [**デバッグ開始**] をクリックしてアプリケーションを実行します。

## <a name="serial"></a>ブロマンアプリケーションのシリアルバージョンの実装

このセクションでは、マンデルブロフラクタルを描画する方法について説明します。 このバージョンは、マンデルブローフラクタルを GDI +[ビットマップ](/windows/win32/api/gdiplusheaders/nl-gdiplusheaders-bitmap)オブジェクトに描画し、そのビットマップの内容をクライアントウィンドウにコピーします。

#### <a name="to-implement-the-serial-version-of-the-mandelbrot-application"></a>ブロマンアプリケーションのシリアルバージョンを実装するには

1. *.Pch* (Visual Studio 2017 以前の*stdafx.h* ) で、次の `#include` ディレクティブを追加します。

   [!code-cpp[concrt-mandelbrot#1](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_1.h)]

1. ChildView .h で、`pragma` ディレクティブの後に `BitmapPtr` 型を定義します。 `BitmapPtr` 型を使用すると、`Bitmap` オブジェクトへのポインターを複数のコンポーネントで共有できます。 `Bitmap` オブジェクトは、コンポーネントによって参照されなくなったときに削除されます。

   [!code-cpp[concrt-mandelbrot#2](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_2.h)]

1. ChildView. h で、次のコードを `CChildView` クラスの `protected` セクションに追加します。

   [!code-cpp[concrt-mandelbrot#3](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_3.h)]

1. ChildView .cpp で、次の行をコメントアウトするか削除します。

   [!code-cpp[concrt-mandelbrot#4](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_4.cpp)]

   デバッグビルドでは、この手順によって、GDI + と互換性のない `DEBUG_NEW` アロケーターをアプリケーションで使用できなくなります。

1. ChildView .cpp で、`Gdiplus` 名前空間に `using` ディレクティブを追加します。

   [!code-cpp[concrt-mandelbrot#5](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_5.cpp)]

1. 次のコードを `CChildView` クラスのコンストラクターおよびデストラクターに追加して、GDI + を初期化してシャットダウンします。

   [!code-cpp[concrt-mandelbrot#6](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_6.cpp)]

1. `CChildView::DrawMandelbrot` メソッドを実装します。 このメソッドは、指定された `Bitmap` オブジェクトにマンデルブロフラクタルを描画します。

   [!code-cpp[concrt-mandelbrot#7](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_7.cpp)]

1. `CChildView::OnPaint` メソッドを実装します。 このメソッドは `CChildView::DrawMandelbrot` を呼び出し、`Bitmap` オブジェクトの内容をウィンドウにコピーします。

   [!code-cpp[concrt-mandelbrot#8](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_8.cpp)]

1. アプリケーションをビルドして実行することで、アプリケーションが正常に更新されたことを確認します。

次の図は、マンデルブロアプリケーションの結果を示しています。

![マンデルブロアプリケーション](../../parallel/concrt/media/mandelbrot.png "マンデルブロ アプリケーション")

各ピクセルの計算は計算に負荷がかかるため、全体的な計算が終了するまで、UI スレッドは追加のメッセージを処理できません。 これにより、アプリケーションの応答性が低下する可能性があります。 ただし、UI スレッドから作業を削除することで、この問題を軽減できます。

[[トップ](#top)]

## <a name="removing-work"></a>UI スレッドからの作業の削除

このセクションでは、マンデルブロアプリケーションの UI スレッドから描画作業を削除する方法について説明します。 描画作業を UI スレッドからワーカースレッドに移動すると、ワーカースレッドがバックグラウンドでイメージを生成するときに、UI スレッドがメッセージを処理できます。

同時実行ランタイムには、タスク[グループ](../../parallel/concrt/task-parallelism-concurrency-runtime.md)、[非同期エージェント](../../parallel/concrt/asynchronous-agents.md)、および[軽量タスク](../../parallel/concrt/task-scheduler-concurrency-runtime.md)の3つのタスク実行方法が用意されています。 これらのメカニズムのいずれかを使用して UI スレッドから作業を削除できますが、この例では、タスクグループがキャンセルをサポートしているため、 [concurrency:: task_group](reference/task-group-class.md)オブジェクトを使用しています。 このチュートリアルでは、後でキャンセルを使用して、クライアントウィンドウのサイズ変更時に実行される作業量を減らし、ウィンドウが破棄されたときにクリーンアップを実行します。

また、この例では、[同時実行:: unbounded_buffer](reference/unbounded-buffer-class.md)オブジェクトを使用して、UI スレッドとワーカースレッドが相互に通信できるようにします。 ワーカースレッドはイメージを生成した後、`Bitmap` オブジェクトへのポインターを `unbounded_buffer` オブジェクトに送信し、描画メッセージを UI スレッドにポストします。 次に、UI スレッドは、`unbounded_buffer` オブジェクトから `Bitmap` オブジェクトを受け取り、それをクライアントウィンドウに描画します。

#### <a name="to-remove-the-drawing-work-from-the-ui-thread"></a>UI スレッドから描画作業を削除するには

1. *.Pch* (Visual Studio 2017 以前の*stdafx.h* ) で、次の `#include` ディレクティブを追加します。

   [!code-cpp[concrt-mandelbrot#101](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_9.h)]

1. ChildView .h で、`CChildView` クラスの `protected` セクションに `task_group` および `unbounded_buffer` メンバー変数を追加します。 `task_group` オブジェクトは、描画を実行するタスクを保持します。`unbounded_buffer` オブジェクトは、完成したマンデルブローイメージを保持します。

   [!code-cpp[concrt-mandelbrot#102](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_10.h)]

1. ChildView .cpp で、`concurrency` 名前空間に `using` ディレクティブを追加します。

   [!code-cpp[concrt-mandelbrot#103](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_11.cpp)]

1. `CChildView::DrawMandelbrot` メソッドで、`Bitmap::UnlockBits`を呼び出した後、 [concurrency:: send](reference/concurrency-namespace-functions.md#send)関数を呼び出して、`Bitmap` オブジェクトを UI スレッドに渡します。 次に、描画メッセージを UI スレッドにポストし、クライアント領域を無効にします。

   [!code-cpp[concrt-mandelbrot#104](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_12.cpp)]

1. `CChildView::OnPaint` メソッドを更新して、更新された `Bitmap` オブジェクトを受信し、クライアントウィンドウにイメージを描画します。

   [!code-cpp[concrt-mandelbrot#105](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_13.cpp)]

   `CChildView::OnPaint` メソッドは、マンデルブロイメージがメッセージバッファーに存在しない場合に、そのイメージを生成するタスクを作成します。 最初の描画メッセージや、クライアントウィンドウの前に別のウィンドウが移動された場合、メッセージバッファーには `Bitmap` オブジェクトが含まれません。

1. アプリケーションをビルドして実行することで、アプリケーションが正常に更新されたことを確認します。

描画作業がバックグラウンドで実行されるため、UI の応答性が向上しました。

[[トップ](#top)]

## <a name="performance"></a>描画パフォーマンスの向上

各ピクセルの計算は他のすべての計算から独立しているため、マンデルブロフラクタルの生成は並列化の候補として適しています。 描画プロシージャを並列化するには、次のように、`CChildView::DrawMandelbrot` メソッドの外側の `for` ループを[concurrency::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for)アルゴリズムへの呼び出しに変換します。

[!code-cpp[concrt-mandelbrot#301](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_14.cpp)]

各 bitmap 要素の計算は独立しているため、ビットマップメモリにアクセスする描画操作を同期する必要はありません。 これにより、使用可能なプロセッサの数が増えるにつれて、パフォーマンスを向上させることができます。

[[トップ](#top)]

## <a name="cancellation"></a>キャンセルのサポートの追加

このセクションでは、ウィンドウのサイズ変更を処理する方法と、ウィンドウが破棄されたときにアクティブな描画タスクをキャンセルする方法について説明します。

[PPL における](cancellation-in-the-ppl.md)ドキュメントのキャンセルでは、ランタイムでのキャンセルの動作について説明します。 取り消しは協調しています。そのため、すぐには発生しません。 取り消されたタスクを停止するために、ランタイムは、後続のタスクからランタイムへの呼び出し中に内部例外をスローします。 前のセクションでは、`parallel_for` アルゴリズムを使用して描画タスクのパフォーマンスを向上させる方法について説明します。 `parallel_for` を呼び出すと、ランタイムはタスクを停止することができるため、キャンセルが有効になります。

### <a name="cancelling-active-tasks"></a>アクティブなタスクの取り消し

マンデルブロアプリケーションでは、クライアントウィンドウのサイズに合わせて寸法が一致する `Bitmap` オブジェクトを作成します。 クライアントウィンドウのサイズが変更されるたびに、新しいウィンドウサイズのイメージを生成するためのバックグラウンドタスクが追加されます。 アプリケーションは、これらの中間イメージを必要としません。最終的なウィンドウサイズにはイメージのみが必要です。 アプリケーションでこの追加の作業が実行されないようにするには、メッセージハンドラーで `WM_SIZE` および `WM_SIZING` メッセージのアクティブな描画タスクをキャンセルしてから、ウィンドウのサイズを変更した後で描画作業のスケジュールを再設定します。

ウィンドウのサイズが変更されたときにアクティブな描画タスクをキャンセルするには、アプリケーションは `WM_SIZING` と `WM_SIZE` メッセージのハンドラーで[concurrency:: task_group:: cancel](reference/task-group-class.md#cancel)メソッドを呼び出します。 また、`WM_SIZE` メッセージのハンドラーは、 [concurrency:: task_group:: wait](reference/task-group-class.md#wait)メソッドを呼び出して、すべてのアクティブなタスクが完了するのを待ってから、更新されたウィンドウサイズの描画タスクを再スケジュールします。

クライアントウィンドウが破棄されたら、アクティブな描画タスクをキャンセルすることをお勧めします。 アクティブな描画タスクをキャンセルすると、クライアントウィンドウが破棄された後に、ワーカースレッドが UI スレッドにメッセージをポストしないようにすることができます。 アプリケーションは、`WM_DESTROY` メッセージのハンドラー内のアクティブな描画タスクをキャンセルします。

### <a name="responding-to-cancellation"></a>キャンセルへの応答

描画タスクを実行する `CChildView::DrawMandelbrot` メソッドは、キャンセルに応答する必要があります。 ランタイムは例外処理を使用してタスクを取り消すため、`CChildView::DrawMandelbrot` メソッドでは、すべてのリソースが正しくクリーンアップされることを保証するために、例外セーフメカニズムを使用する必要があります。 この例では、*リソース取得は初期化*(RAII) パターンを使用して、タスクが取り消されたときにビットマップビットのロックが解除されることを保証します。

##### <a name="to-add-support-for-cancellation-in-the-mandelbrot-application"></a>マンデルブロアプリケーションでキャンセルのサポートを追加するには

1. ChildView .h の `CChildView` クラスの `protected` セクションで、`OnSize`、`OnSizing`、および `OnDestroy` メッセージマップ関数の宣言を追加します。

   [!code-cpp[concrt-mandelbrot#201](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_15.h)]

1. ChildView .cpp で、メッセージマップを変更して、`WM_SIZE`、`WM_SIZING`、および `WM_DESTROY` メッセージのハンドラーが含まれるようにします。

   [!code-cpp[concrt-mandelbrot#202](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_16.cpp)]

1. `CChildView::OnSizing` メソッドを実装します。 このメソッドは、既存の描画タスクをキャンセルします。

   [!code-cpp[concrt-mandelbrot#203](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_17.cpp)]

1. `CChildView::OnSize` メソッドを実装します。 このメソッドは、既存の描画タスクをキャンセルし、更新されたクライアントウィンドウサイズの新しい描画タスクを作成します。

   [!code-cpp[concrt-mandelbrot#204](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_18.cpp)]

1. `CChildView::OnDestroy` メソッドを実装します。 このメソッドは、既存の描画タスクをキャンセルします。

   [!code-cpp[concrt-mandelbrot#205](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_19.cpp)]

1. ChildView .cpp で、RAII パターンを実装する `scope_guard` クラスを定義します。

   [!code-cpp[concrt-mandelbrot#206](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_20.cpp)]

1. `Bitmap::LockBits`の呼び出しの後に、`CChildView::DrawMandelbrot` メソッドに次のコードを追加します。

   [!code-cpp[concrt-mandelbrot#207](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_21.cpp)]

   このコードでは、`scope_guard` オブジェクトを作成することによって取り消し処理を行います。 オブジェクトがスコープから出ると、ビットマップビットのロックが解除されます。

1. ビットマップビットのロックが解除された後、UI スレッドにメッセージが送信される前に、`CChildView::DrawMandelbrot` メソッドの末尾を変更して、`scope_guard` オブジェクトを破棄します。 これにより、ビットマップビットのロックが解除される前に UI スレッドが更新されないようにします。

   [!code-cpp[concrt-mandelbrot#208](../../parallel/concrt/codesnippet/cpp/walkthrough-removing-work-from-a-user-interface-thread_22.cpp)]

9. アプリケーションをビルドして実行することで、アプリケーションが正常に更新されたことを確認します。

ウィンドウのサイズを変更すると、描画作業は、最終的なウィンドウサイズに対してのみ実行されます。 アクティブな描画タスクも、ウィンドウが破棄されたときにキャンセルされます。

[[トップ](#top)]

## <a name="see-also"></a>参照

[コンカレンシー ランタイムのチュートリアル](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[タスクの並列化](../../parallel/concrt/task-parallelism-concurrency-runtime.md)<br/>
[非同期メッセージ ブロック](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[メッセージ パッシング関数](../../parallel/concrt/message-passing-functions.md)<br/>
[並列アルゴリズム](../../parallel/concrt/parallel-algorithms.md)<br/>
[PPL における取り消し処理](cancellation-in-the-ppl.md)<br/>
[MFC デスクトップ アプリケーション](../../mfc/mfc-desktop-applications.md)
