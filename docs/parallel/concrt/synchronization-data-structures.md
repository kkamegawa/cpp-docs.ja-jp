---
title: 同期データ構造
ms.date: 11/04/2016
helpviewer_keywords:
- synchronization data structures
ms.assetid: d612757d-e4b7-4019-a627-f853af085b8b
ms.openlocfilehash: 85dec6b003330a3560ae1dcc5c41b5e6d49f765e
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142804"
---
# <a name="synchronization-data-structures"></a>同期データ構造

同時実行ランタイムには、複数のスレッドからの共有データへのアクセスを同期できるデータ構造がいくつか用意されています。 これらのデータ構造は、変更する共有データがあまり使用されない場合に役立ちます。 同期オブジェクト (たとえば、クリティカルセクション) は、共有リソースが使用可能になるまで他のスレッドを待機させます。 このため、このようなオブジェクトを使用して頻繁に使用されるデータへのアクセスを同期する場合、アプリケーションのスケーラビリティが失われる可能性があります。 [並列パターンライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)は、 [concurrency:: 組み合わせ](../../parallel/concrt/reference/combinable-class.md)可能クラスを提供します。これにより、同期を必要とすることなく、複数のスレッドまたはタスク間でリソースを共有できます。 `combinable` クラスの詳細については、「[並列コンテナーとオブジェクト](../../parallel/concrt/parallel-containers-and-objects.md)」を参照してください。

## <a name="top"></a> セクション

このトピックでは、次の非同期メッセージブロックの種類について詳しく説明します。

- [critical_section](#critical_section)

- [reader_writer_lock](#reader_writer_lock)

- [scoped_lock と scoped_lock_read](#scoped_lock)

- [event](#event)

## <a name="critical_section"></a>critical_section

[Concurrency:: critical_section](../../parallel/concrt/reference/critical-section-class.md)クラスは、他のタスクを実行するのではなく、その他のタスクを生成する協調相互排他オブジェクトを表します。 重要なセクションは、複数のスレッドが共有データに対する排他的読み取りと書き込みアクセスを必要とする場合に役立ちます。

`critical_section` クラスは再入可能ではありません。 [Concurrency:: critical_section:: lock](reference/critical-section-class.md#lock)メソッドは、既にロックを所有しているスレッドによって呼び出された場合に、 [concurrency:: improper_lock](../../parallel/concrt/reference/improper-lock-class.md)型の例外をスローします。

### <a name="methods-and-features"></a>メソッドと機能

次の表は、`critical_section` クラスによって定義される重要なメソッドを示しています。

|方法|説明|
|------------|-----------------|
|[lock](reference/critical-section-class.md#lock)|クリティカルセクションを取得します。 呼び出しコンテキストは、ロックが取得されるまでブロックされます。|
|[try_lock](reference/critical-section-class.md#try_lock)|クリティカルセクションを取得しようとしますが、ブロックしません。|
|[unlock](reference/critical-section-class.md#unlock)|クリティカルセクションを解放します。|

[[トップ](#top)]

## <a name="reader_writer_lock"></a>reader_writer_lock

[Concurrency:: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)クラスは、共有データに対してスレッドセーフな読み取り/書き込み操作を提供します。 複数のスレッドが共有リソースへの同時読み取りアクセスを必要とするが、その共有リソースへの書き込みはほとんど行わない場合は、リーダー/ライターロックを使用します。 このクラスは、オブジェクトに対して常に1つのスレッド書き込みアクセスを提供します。

`reader_writer_lock` クラスは、`critical_section` クラスよりもパフォーマンスが向上します。これは、`critical_section` オブジェクトが共有リソースへの排他アクセスを取得し、同時読み取りアクセスができないためです。

`critical_section` クラスと同様に、`reader_writer_lock` クラスは協調相互排他オブジェクトを表します。このオブジェクトは、その他のタスクを優先するのではなく、その他のタスクに対して生成します。

共有リソースへの書き込みを必要とするスレッドがリーダー/ライターロックを取得すると、そのリソースにもアクセスする必要がある他のスレッドは、ライターがロックを解放するまでブロックされます。 `reader_writer_lock` クラスは*書き込み設定*ロックの例です。これは、待機中のリーダーのブロックを解除する前に、待機中のライターのブロックを解除するロックです。

`critical_section` クラスと同様に、`reader_writer_lock` クラスは再入不可です。 [Concurrency:: reader_writer_lock:: lock](reference/reader-writer-lock-class.md#lock)メソッドと[concurrency:: reader_writer_lock:: lock_read](reference/reader-writer-lock-class.md#lock_read)メソッドは、既にロックを所有しているスレッドによって呼び出された場合に、型 `improper_lock` の例外をスローします。

> [!NOTE]
> `reader_writer_lock` クラスは再入可能でないため、読み取り専用ロックをリーダー/ライターロックにアップグレードしたり、リーダー/ライターロックを読み取り専用ロックにダウングレードしたりすることはできません。 これらの操作のいずれかを実行すると、未定義の動作が発生します。

### <a name="methods-and-features"></a>メソッドと機能

次の表は、`reader_writer_lock` クラスによって定義される重要なメソッドを示しています。

|方法|説明|
|------------|-----------------|
|[lock](reference/reader-writer-lock-class.md#lock)|ロックへの読み取り/書き込みアクセス権を取得します。|
|[try_lock](reference/reader-writer-lock-class.md#try_lock)|ロックへの読み取り/書き込みアクセスを取得しようとしますが、ブロックしません。|
|[lock_read](reference/reader-writer-lock-class.md#lock_read)|ロックへの読み取り専用アクセスを取得します。|
|[try_lock_read](reference/reader-writer-lock-class.md#try_lock_read)|ロックへの読み取り専用アクセスを取得しようとしますが、ブロックしません。|
|[unlock](reference/reader-writer-lock-class.md#unlock)|ロックを解放します。|

[[トップ](#top)]

## <a name="scoped_lock"></a>scoped_lock と scoped_lock_read

`critical_section` クラスと `reader_writer_lock` クラスには、相互排他オブジェクトの操作方法を簡略化する、入れ子になったヘルパークラスが用意されています。 これらのヘルパークラスは、*スコープロック*と呼ばれます。

`critical_section` クラスには、 [concurrency:: critical_section:: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class)クラスが含まれています。 コンストラクターは、指定された `critical_section` オブジェクトへのアクセスを取得します。デストラクターは、そのオブジェクトへのアクセスを解放します。 `reader_writer_lock` クラスには、指定された `reader_writer_lock` オブジェクトへの書き込みアクセスを管理することを除けば、`critical_section::scoped_lock`に似た[concurrency:: reader_writer_lock:: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class)クラスが含まれています。 `reader_writer_lock` クラスには、 [concurrency:: reader_writer_lock:: scoped_lock_read](reference/reader-writer-lock-class.md#scoped_lock_read_class)クラスも含まれています。 このクラスは、指定された `reader_writer_lock` オブジェクトへの読み取りアクセスを管理します。

スコープが指定されたロックは、`critical_section` と `reader_writer_lock` オブジェクトを手動で操作する場合に、いくつかの利点があります。 通常は、スコープが指定されたロックをスタックに割り当てます。 スコープが指定されたロックは、その相互排他オブジェクトが破棄されると自動的に解放されます。そのため、基になるオブジェクトのロックを手動で解除する必要はありません。 これは、関数に複数の `return` ステートメントが含まれている場合に便利です。 スコープが指定したロックは、例外セーフなコードを記述するのにも役立ちます。 `throw` ステートメントによってスタックがアンワインドされると、アクティブなスコープを持つロックのデストラクターが呼び出されます。そのため、相互排他オブジェクトは常に正しく解放されます。

> [!NOTE]
> `critical_section::scoped_lock`、`reader_writer_lock::scoped_lock`、および `reader_writer_lock::scoped_lock_read` クラスを使用する場合は、基になる相互排他オブジェクトへのアクセスを手動で解放しないでください。 これにより、ランタイムを無効な状態にすることができます。

## <a name="event"></a>場合

[Concurrency:: event](../../parallel/concrt/reference/event-class.md)クラスは、状態がシグナルまたは非シグナルである同期オブジェクトを表します。 重要なセクションなど、共有データへのアクセスを保護することが目的である同期オブジェクトとは異なり、イベントは実行のフローを同期します。

`event` クラスは、あるタスクが別のタスクに対して作業を完了したときに便利です。 たとえば、あるタスクが、ネットワーク接続またはファイルからデータを読み取ることを別のタスクに通知する場合があります。

### <a name="methods-and-features"></a>メソッドと機能

次の表は、`event` クラスによって定義されるいくつかの重要なメソッドを示しています。

|方法|説明|
|------------|-----------------|
|[待機](reference/event-class.md#wait)|イベントがシグナル状態になるのを待機します。|
|[set](reference/event-class.md#set)|イベントをシグナル状態に設定します。|
|[reset](reference/event-class.md#reset)|イベントをシグナル状態以外の状態に設定します。|
|[wait_for_multiple](reference/event-class.md#wait_for_multiple)|複数のイベントがシグナル状態になるのを待機します。|

### <a name="example"></a>例

`event` クラスの使用方法を示す例については、「[同期データ構造と WINDOWS API の比較](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)」を参照してください。

[[トップ](#top)]

## <a name="related-sections"></a>関連セクション

[同期データ構造と Windows API の比較](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
同期データ構造の動作を、Windows API によって提供されるものと比較します。

[コンカレンシー ランタイム](../../parallel/concrt/concurrency-runtime.md)<br/>
並列プログラミングを容易にするコンカレンシー ランタイムについて説明します。また、関連トピックへのリンクを示します。
