---
title: E. OpenMP C/C の実装で定義された動作
ms.date: 01/22/2019
ms.assetid: b8d660ca-9bb3-4b6b-87af-45c67d43a731
ms.openlocfilehash: 3d8e9493cad1fce02e5d482cd5e612afb44bb37b
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087224"
---
# <a name="e-implementation-defined-behaviors-in-openmp-cc"></a>E. OpenMP C/C の実装で定義された動作

この付録では、「実装で定義されている」この api として記述されている動作をまとめたものです。  各動作は、メインの仕様では、その説明に相互参照します。

## <a name="remarks"></a>Remarks

実装が定義し、このような場合は、その動作を文書化するために必要には、この一覧は完全でない可能性があります。

- **スレッドの数:** プログラムの動作は、スレッドの数を動的に調整が無効になっているし、並列領域に対して要求されたスレッドの数は、実行時のシステムを提供できる数を超えるときに、並行領域が発生した場合実装の定義 (9 ページを参照してください)。

   Visual C で入れ子になっていない並列領域の 64 個のスレッド (最大) が提供されます。

- **プロセッサの数:** 実際には、特定の時点でスレッドをホストしている物理プロセッサの数は、実装定義 (10 ページを参照してください)。

   Visual C では、この数が一定でないされ、オペレーティング システムによって制御されます。

- **スレッドのチームを作成するには。** チーム内の入れ子になった並列領域を実行するスレッドの数は、実装定義 (10 ページを参照してください)。

   Visual C では、この数は、オペレーティング システムによって決定されます。

- **schedule(runtime):** スケジュールについて意思決定は、実行時まで延期されます。 スケジュールの種類とチャンクのサイズを設定して実行時に選択できます、`OMP_SCHEDULE`環境変数。 この環境変数が設定されていない場合、結果として得られるスケジュールは、実装定義 (13 ページを参照してください)。

   スケジュールの種類は、Visual C で`static`チャンク サイズがありません。

- **既定のスケジュールします。** スケジュール句のない場合は、既定のスケジュールは、実装定義 (13 ページを参照してください)。

   既定のスケジュールの種類は、Visual C で`static`チャンク サイズがありません。

- **ATOMIC:** これは実装で定義された実装がすべてを置換するかどうか`atomic`ディレクティブを`critical`ディレクティブを持つ同じ一意の名前 (20 ページを参照してください)。

   によってデータが変更された場合、Visual C で[アトミック](reference/openmp-directives.md#atomic)自然なアラインメントに記載されていないまたはそのプロパティを満たすすべてのアトミック操作が 1 つの重要なセクションを使用する場合は 1 つまたは 2 バイト、long は。 それ以外の場合、重要なセクションでは使用されません。

- **[omp_get_num_threads](3-run-time-library-functions.md#312-omp_get_num_threads-function):** スレッドの数は、ユーザーが明示的に設定されていない場合、既定値は実装定義 (9 ページを参照してください)。

   Visual c は、既定のスレッド数がプロセッサの数と等しくします。

- **[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function):** 動的なスレッドの調整に既定では、実装で定義されます。

   既定では、Visual C で`FALSE`します。

- **[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function):** 入れ子になった並列処理が有効にすると入れ子になった並列領域の実行に使用されるスレッドの数は実装定義です。

   Visual C では、スレッドの数をオペレーティング システムによって決まります。

- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)環境変数。この環境変数の既定値は、実装で定義されます。

   スケジュールの種類は、Visual C で`static`チャンク サイズがありません。

- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境変数。値が指定されていない場合、`OMP_NUM_THREADS`環境変数、または指定された値が正の整数をいないまたは値が、システムでサポートできるスレッドの最大数よりも大きい場合は、使用するスレッドの数は実装定義です。

   Visual C でがゼロの値が指定されている場合または、以下の場合、スレッドの数がプロセッサの数と等しい。  値が 64 より大きい場合は、スレッドの数は 64 です。

- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)環境変数。既定値は、実装で定義されます。

   既定では、Visual C で`FALSE`します。