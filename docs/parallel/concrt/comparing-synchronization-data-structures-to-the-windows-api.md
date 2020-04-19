---
title: 同期データ構造と Windows API の比較
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures, compared to Windows API
- event class, example
ms.assetid: 8b0b1a3a-ef80-408c-91fa-93e6af920b4e
ms.openlocfilehash: 16d58431ae3f9859677302010f15a75b37ebedbf
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510595"
---
# <a name="comparing-synchronization-data-structures-to-the-windows-api"></a>同期データ構造と Windows API の比較

ここでは、コンカレンシー ランタイムが提供する同期データ構造と Windows API が提供する同期データ構造の動作を比較します。

同時実行ランタイムによって提供される同期データ構造は、*協調スレッドモデル*に従います。 協調スレッド処理モデルでは、同期プリミティブは処理リソースを他のスレッドに明示的に譲渡します。 これは、制御スケジューラまたはオペレーティングシステムによって処理リソースが他のスレッドに転送される、*プリエンプティブなスレッドモデル*とは異なります。

## <a name="critical_section"></a>critical_section

[Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)クラスは、1つ`CRITICAL_SECTION`のプロセスのスレッドだけが使用できるため、Windows の構造に似ています。 Windows API の重要なセクションの詳細については、「[クリティカルセクションオブジェクト](/windows/win32/Sync/critical-section-objects)」を参照してください。

## <a name="reader_writer_lock"></a>reader_writer_lock

[Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)クラスは、Windows スリムリーダー/ライター (SRW) ロックに似ています。 類似点と相違点を次の表に示します。

|機能|`reader_writer_lock`|SRW ロック|
|-------------|--------------------------|--------------|
|再入不可能|[はい]|[はい]|
|リーダーをライターに昇格 (アップグレード サポート)|いいえ|いいえ|
|ライターをリーダーに降格 (ダウングレード サポート)|いいえ|いいえ|
|書き込み優先ロック|[はい]|いいえ|
|ライターへの FIFO アクセス|[はい]|いいえ|

SRW ロックの詳細については、Platform SDK の「[スリムリーダー/ライター (SRW) ロック](/windows/win32/sync/slim-reader-writer--srw--locks)」を参照してください。

## <a name="event"></a>event

[Concurrency:: event](../../parallel/concrt/reference/event-class.md)クラスは、名前のない Windows 手動リセットイベントに似ています。 ただし、`event` オブジェクトは協調して動作しますが、Windows イベントはプリエンプティブに動作します。 Windows イベントの詳細については、「[イベントオブジェクト](/windows/win32/Sync/event-objects)」を参照してください。

## <a name="example"></a>例

### <a name="description"></a>説明

`event` クラスと Windows イベントの相違点をより詳しく理解するために、次の例について考えてみましょう。 この例により、スケジューラは最大で 2 つの同時タスクを作成した後、`event` クラスと Windows 手動リセット イベントを使用する 2 つの類似した関数を呼び出すことができます。 各関数は、まず共有イベントがシグナル状態になるのを待機する複数のタスクを作成します。 次に、実行中のタスクに制御を渡し、イベントに通知します。 その後、各関数はシグナル状態イベントを待機します。

### <a name="code"></a>コード

[!code-cpp[concrt-event-comparison#1](../../parallel/concrt/codesnippet/cpp/comparing-synchronization-data-structures-to-the-windows-api_1.cpp)]

### <a name="comments"></a>コメント

この例では、次のサンプル出力が生成されます。

```Output
Cooperative event:
    Context 0: waiting on an event.
    Context 1: waiting on an event.
    Context 2: waiting on an event.
    Context 3: waiting on an event.
    Context 4: waiting on an event.
    Setting the event.
    Context 5: received the event.
    Context 6: received the event.
    Context 7: received the event.
    Context 8: received the event.
    Context 9: received the event.
Windows event:
    Context 10: waiting on an event.
    Context 11: waiting on an event.
    Setting the event.
    Context 12: received the event.
    Context 14: waiting on an event.
    Context 15: received the event.
    Context 16: waiting on an event.
    Context 17: received the event.
    Context 18: waiting on an event.
    Context 19: received the event.
    Context 13: received the event.
```

`event` クラスは協調して動作するため、イベントがシグナル状態になるのを待機している場合、スケジューラは処理リソースを別のコンテキストに再割り当てすることができます。 したがって、`event` クラスを使用するバージョンで、より多くの作業が実行されます。 Windows イベントを使用するバージョンでは、待機中の各タスクは次のタスクが開始される前にシグナル状態になる必要があります。

タスクの詳細については、「[タスクの並列](../../parallel/concrt/task-parallelism-concurrency-runtime.md)化」を参照してください。

## <a name="see-also"></a>関連項目

[同期データ構造](../../parallel/concrt/synchronization-data-structures.md)
