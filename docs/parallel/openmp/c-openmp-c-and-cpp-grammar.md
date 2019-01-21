---
title: 'C:  OpenMP C および C++ の文法'
ms.date: 01/16/2019
ms.assetid: 97a878ce-1533-47f7-a134-66fcbff48524
ms.openlocfilehash: 85e18161079b49e83cc9fedb3184ee220c889e75
ms.sourcegitcommit: 2ebbf8093fadb9a1b78a4381439bcd5c01a89267
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397356"
---
# <a name="c-openmp-c-and-c-grammar"></a>C:  OpenMP C および C++ の文法

[C.1 表記](#c1-notation)<br/>
[C.2 規則](#c2-rules)

## <a name="c1-notation"></a>C.1 表記

文法規則は、非-ターミナルでの名前の後に別の行に交換用の代替手段を続けて、コロンです。

式の構文用語<sub>opt</sub>という用語が置換内で省略可能であることを示します。

構文の式*用語*<sub>optseq</sub>と等価*用語 seq*<sub>opt</sub>次の追加の規則で。

*term-seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*用語*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*term-seq* *term*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*term-seq*   `,` *term*

## <a name="c2-rules"></a>C.2 規則

表記法は、C 規格の 6.1 で説明します。 この文章の付録では、OpenMP C および C++ のディレクティブの基本言語の文法を拡張機能を示します。

**/\* C++ (ISO/IEC 14882:1998) \*/**

*statement-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-seq statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-seq openmp-directive*

**/\* C90 で (ISO/IEC 9899:1990) \*/**

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ステートメント list ステートメント*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ステートメントの一覧の openmp ディレクティブ*

**/\* C99 (ISO/IEC 9899:1999) \*/**

*block-item*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp-directive*

**/\* 標準的なステートメント \*/**

*statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*openmp コンストラクト*

*openmp コンストラクト*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*並列のコンス トラクター*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*for コンストラクト*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*セクションのコンス トラクター*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*1 つのコンス トラクター*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*並列-for のコンストラクト*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*parallel-sections-construct*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master コンストラクト*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critical コンストラクト*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic コンストラクト*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*順序付けのコンス トラクター*

*openmp ディレクティブ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*barrier ディレクティブ*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*flush ディレクティブ*

*構造化ブロック*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*

*parallel-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*並列ディレクティブ構造化ブロック*

*parallel-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel` *parallel-clause*<sub>optseq</sub> *new-line*

*並列句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*unique-parallel-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `if (` *expression*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `num_threads (` *expression*   `)`

*コンス トラクターの*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*イテレーション ステートメントの for ディレクティブ*

*ディレクティブの*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp for` *for-clause*<sub>optseq</sub> *new-line*

*for 句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*unique-for-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `ordered`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *schedule-kind*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `schedule (` *schedule-kind*   `,` *expression*   `)`

*スケジュールの種類*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `static`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `dynamic`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `guided`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `runtime`

*sections-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*セクション ディレクティブのセクションのスコープ*

*sections-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp sections` *sections-clause*<sub>optseq</sub> *new-line*

*sections-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*section-scope*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*{ section-sequence }*

*section-sequence*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*section-directive*<sub>opt</sub> *structured-block*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*セクション シーケンス構造セクション ディレクティブのブロック*

*section-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp section` *new-line*

*1 つのコンス トラクター*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*単一ディレクティブ構造化ブロック*

*single-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp single` *single-clause*<sub>optseq</sub> *new-line*

*単一句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `nowait`

*parallel-for-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ディレクティブの並列の繰り返しステートメント*

*parallel-for-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel for` *parallel-for-clause*<sub>optseq</sub> *new-line*

*並列-句の*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-for-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*parallel-sections-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*並列のセクションでは、ディレクティブのセクション スコープ*

*parallel-sections-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp parallel sections` *parallel-sections-clause*<sub>optseq</sub> *new-line*

*parallel-sections-clause*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*unique-parallel-clause*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*data-clause*

*マスター コンストラクト*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*master ディレクティブ構造化ブロック*

*master ディレクティブ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp master` *new-line*

*critical-construct*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*critical ディレクティブ構造化ブロック*

*critical ディレクティブ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp critical` *region-phrase*<sub>opt</sub> *new-line*

*リージョン語句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(識別子)*

*barrier ディレクティブ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp barrier` *new-line*

*atomic コンストラクト*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*atomic ディレクティブの式ステートメント*

*atomic ディレクティブ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp atomic` *new-line*

*flush ディレクティブ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp flush` *flush-vars*<sub>opt</sub> *new-line*

*フラッシュ var*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*(変数リスト)*

*順序付けられたコンストラクト*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ordered ディレクティブ構造化ブロック*

*ordered ディレクティブ*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp ordered` *new-line*

**/\* 標準の宣言 \*/**

*declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*threadprivate-directive*

*threadprivate-directive*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `# pragma omp threadprivate (` *variable-list*    `)` *new-line*

*データ句*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `private (` *variable-list*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyprivate (`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `firstprivate (`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `lastprivate (` *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `shared (` *variable-list*   `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( shared )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `default ( none )`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `reduction (`  *reduction-operator*    `:`  *variable-list*    `)`<br/>
&nbsp;&nbsp;&nbsp;&nbsp;  `copyin (`  *variable-list*    `)`

*減少演算子*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;いずれか:   `+ \* - & ^ | && ||`

**/\* C で \*/**

*変数リスト*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*variable-list*   `,` *identifier*

**/\* C++ では \*/**

*変数リスト*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*id-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*variable-list*   `,` *id-expression*
