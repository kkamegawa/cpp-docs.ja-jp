---
title: F. 新機能とバージョン 2.0 の説明
ms.date: 01/22/2019
ms.assetid: 0d4beb66-f2d5-468c-8cd3-4b00dcbab061
ms.openlocfilehash: 2e186bbc82f4f43e831dd05cdded2a9e946d1dd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62362715"
---
# <a name="f-new-features-and-clarifications-in-version-20"></a>F. 新機能とバージョン 2.0 の説明

この付録では、OpenMP C と C++ 仕様バージョン 1.0 からバージョン 2.0 に移行する際に変更をまとめたものです。 次の項目は、仕様に追加された新機能を示します。

- OpenMP ではコンマは許可[ディレクティブ](2-directives.md#21-directive-format)します。

- 追加、`num_threads`句。 この句により、特定のスレッド数の要求でユーザーに、 [parallel コンストラクト](2-directives.md#23-parallel-construct)します。

- [Threadprivate](2-directives.md#271-threadprivate-directive)ディレクティブが静的ブロック スコープ変数を受け入れるように拡張されています。

- C99 可変長配列は完全な型と指定できる任意の場所の一覧など、許可されている完全な型が、 `private`、 `firstprivate`、および`lastprivate`句 (を参照してください[セクション 2.7.2](2-directives.md#272-data-sharing-attribute-clauses))。

- 並列領域内のプライベート変数をマークする[プライベート](2-directives.md#2721-private)入れ子になったディレクティブにもう一度です。

- `copyprivate`句が追加されました。 これは、プライベート変数を使用して、他のメンバーにチームの 1 つのメンバーから値をブロードキャストするメカニズムを提供します。 このような共有変数を提供するが難しい (たとえばの各レベルで別の変数を必要とする再帰) ときに、値の共有変数を使用する代わりにすることをお勧めします。 [Copyprivate](2-directives.md#2728-copyprivate)句にのみ表示できる、`single`ディレクティブ。

- タイミング ルーチンの加算[omp_get_wtick](3-run-time-library-functions.md#332-omp_get_wtick-function)と[omp_get_wtime](3-run-time-library-functions.md#331-omp_get_wtime-function) MPI ルーチンに似ています。 これらの関数は、ウォール クロックの実行に必要です。

- 付録の一覧を[動作の実装で定義された](e-implementation-defined-behaviors-in-openmp-c-cpp.md)OpenMP C と C++ が追加されました。 実装は、定義し、このような場合は、その動作を文書化する必要があります。

- 明確にまたは C と C++ の以前の OpenMP API 仕様の機能を修正するには、次の変更を果たします。

  - 明確にされましたの動作[omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)と[omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)とき`omp_in_parallel`返します 0 以外の値は定義されていません。

  - 明確[ディレクティブの入れ子](2-directives.md#29-directive-nesting)入れ子になった並列が使用されます。

  - [ロック初期化](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions)と[ロック破棄](3-run-time-library-functions.md#322-omp_destroy_lock-and-omp_destroy_nest_lock-functions)並列領域で関数を呼び出すことができます。

  - 追加された新しい例[付録 A](a-examples.md)します。