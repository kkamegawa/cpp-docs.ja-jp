---
title: メモリ管理関数
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: aa1951211283ddf7e4823a920d5cdf19bd6d977d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141838"
---
# <a name="memory-management-functions"></a>メモリ管理関数

このドキュメントでは、同時実行方式でメモリの割り当てと解放を支援するために同時実行ランタイムに用意されているメモリ管理関数について説明します。

> [!TIP]
> コンカレンシー ランタイムには既定のスケジューラが用意されているため、アプリケーションにスケジューラを作成する必要はありません。 タスクスケジューラはアプリケーションのパフォーマンスを微調整するのに役立ちます。そのため、同時実行ランタイムを初めて使用する場合は、[並列パターンライブラリ (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)または[非同期エージェントライブラリ](../../parallel/concrt/asynchronous-agents-library.md)から始めることをお勧めします。

同時実行ランタイムには、同時にメモリブロックの割り当てと解放を行うために最適化された、2つのメモリ管理関数が用意されています。 [Concurrency:: Alloc](reference/concurrency-namespace-functions.md#alloc)関数は、指定されたサイズを使用してメモリのブロックを割り当てます。 [Concurrency:: Free](reference/concurrency-namespace-functions.md#free)関数は、`Alloc`によって割り当てられたメモリを解放します。

> [!NOTE]
> `Alloc` 関数と `Free` 関数は相互に依存しています。 `Free` 関数は、`Alloc` 関数を使用して割り当てたメモリを解放する場合にのみ使用します。 また、`Alloc` 関数を使用してメモリを割り当てる場合は、`Free` 関数だけを使用してそのメモリを解放します。

さまざまなスレッドまたはタスクから固定された割り当てサイズのセットを割り当てて解放するときに、`Alloc` および `Free` 関数を使用します。 同時実行ランタイムは、C ランタイムヒープから割り当てられたメモリをキャッシュします。 同時実行ランタイムは、実行中のスレッドごとに個別のメモリキャッシュを保持します。このため、ランタイムは、ロックやメモリバリアを使用せずにメモリを管理します。 アプリケーションでは、メモリキャッシュへのアクセス頻度が高くなると、`Alloc` と `Free` の機能が向上します。 たとえば、`Alloc` と `Free` の両方を頻繁に呼び出すスレッドは、主に `Alloc` または `Free`を呼び出すスレッドよりも優れています。

> [!NOTE]
> これらのメモリ管理機能を使用し、アプリケーションで大量のメモリを使用すると、アプリケーションは、予想よりも早くメモリ不足の状態になる可能性があります。 1つのスレッドによってキャッシュされたメモリブロックは、他のスレッドでは使用できないため、1つのスレッドが大量のメモリを保持している場合、そのメモリは使用できません。

## <a name="example"></a>例

`Alloc` および `Free` 関数を使用してメモリパフォーマンスを向上させる例については、「[方法: Alloc と Free を使用してメモリパフォーマンスを向上](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)させる」を参照してください。

## <a name="see-also"></a>参照

[タスク スケジューラ](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[方法: Alloc および Free を使用してメモリ パフォーマンスを改善する](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
