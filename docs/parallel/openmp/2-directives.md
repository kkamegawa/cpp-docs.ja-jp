---
title: 2. ディレクティブ
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087341"
---
# <a name="2-directives"></a>2.ディレクティブ

ディレクティブに基づく`#pragma`ディレクティブは、C および C++ 標準で定義されています。  OpenMP C および C++ API をサポートするコンパイラをアクティブ化し、すべての OpenMP コンパイラ ディレクティブの解釈は、コマンド ライン オプションが含まれます。

## <a name="21-directive-format"></a>2.1 ディレクティブの書式

OpenMP ディレクティブの構文は、文法で正式に指定[付録 C](c-openmp-c-and-cpp-grammar.md)、非公式ようとします。

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

各ディレクティブが始まる`#pragma omp`を同じ名前を持つその他 (openmp OpenMP 以外またはベンダー拡張) プラグマ ディレクティブと競合する可能性を削減する。 ディレクティブの残りの部分では、コンパイラ ディレクティブの C および C++ の標準の規則に従います。 具体的には、前後に空白文字を使用することができます、`#`ディレクティブで単語を分離することがあります空白文字を使用する必要があります。 プリプロセス トークンは、`#pragma omp`マクロ置換影響を受けます。

ディレクティブは、大文字小文字を区別します。 ディレクティブの句が表示される順序は意味はありません。 各句の説明に記載の制限に従い、必要に応じて、ディレクティブの句を繰り返すことがあります。 場合*変数一覧*変数のみを指定する必要がありますが、句に表示されます。 1 つだけ*ディレクティブ名*ディレクティブごとに指定できます。  たとえば、次のディレクティブを使用できません。

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

OpenMP ディレクティブは、最大で 1 つの後続のステートメント、構造化ブロックである必要がありますに適用されます。

## <a name="22-conditional-compilation"></a>2.2 条件付きコンパイル

`_OPENMP`マクロ名は 10 進定数として OpenMP に準拠した実装で定義されている*yyyymm*、承認済みの仕様の月と年になります。 このマクロの件名をすることはできません、`#define`または`#undef`プリプロセス ディレクティブ。

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

ベンダーは、openmp の拡張機能を定義する場合は追加の定義済みマクロを指定します。

## <a name="23-parallel-construct"></a>2.3 parallel コンストラクトします。

次のディレクティブは、多くのスレッドを並列で実行されるプログラムの特定の領域には、並列領域を定義します。 このディレクティブは、並列実行を開始する基本的なコンストラクトです。

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

*句*は、次の 1 つです。

- `if(` *scalar-expression* `)`
- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `default(shared | none)`
- `shared(` *variable-list* `)`
- `copyin(` *variable-list* `)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `num_threads(` *integer-expression* `)`

スレッドは、parallel コンストラクトに取得、次のいずれかが true の場合、スレッドのチームは作成されます。

- いいえ`if`句が存在します。
- `if`式が 0 以外の値に評価されます。

このスレッドがスレッド数が 0 の場合、チームのマスター スレッドとなり、マスター スレッドなど、チームのすべてのスレッドでは、リージョンを並列に実行します。 場合の値、`if`式が 0 では、領域はシリアル化します。

次の規則が要求されるスレッドの数を決定するには、順に見なされます。 条件が満たされる最初の規則が適用されます。

1. 場合、`num_threads`句が存在し、整数型の式の値は、要求スレッドの数。

1. 場合、`omp_set_num_threads`ライブラリ関数が呼び出された後、最後に実行された呼び出しの引数の値は、要求スレッドの数。

1. 場合、環境変数`OMP_NUM_THREADS`が定義されている場合は、この環境変数の値は要求されたスレッドの数。

1. 上にある方法のいずれを使用する場合、要求スレッドの数は実装定義です。

場合、`num_threads`句が存在し、スレッドによって要求された数よりも優先されますが、`omp_set_num_threads`ライブラリ関数、または`OMP_NUM_THREADS`のみに適用される並列領域に対する環境変数。 後での並列領域は、によって影響を受けません。

並列領域を実行するスレッドの数は、スレッドの数を動的に調整が有効になっているかどうかによっても異なります。 動的な調整が無効になっている場合、要求された数のスレッドは、並列領域を実行します。 動的に調整が有効になっている場合、要求された数のスレッドが並列領域を実行するスレッドの最大数とします。

プログラムの動作は、スレッドの数を動的に調整が無効になっているし、並列領域に対して要求されたスレッドの数は、実行時のシステムを提供できる数を超えるときに、並行領域が発生した場合実装で定義します。 実装は、プログラムの実行を中断などの可能性があります、または並列領域がシリアル化することがあります。

`omp_set_dynamic`ライブラリ関数、および`OMP_DYNAMIC`を有効にし、スレッドの数を動的に調整を無効にする環境変数を使用できます。

実際には、特定の時点でスレッドをホストしている物理プロセッサの数は、実装で定義されます。 作成されると、並列領域の間チーム内のスレッドの数が一定にします。 ユーザーが明示的にまたは 1 つの並列領域からの実行時システムによって自動的に変更できます。

各スレッドで並列領域の動的範囲内に含まれるステートメントが実行し、各スレッドが他のスレッドとは異なるステートメントのパスを実行します。 並列領域の構文の範囲外で発生するディレクティブは、孤立したディレクティブと呼ばれます。

並列領域の最後に暗黙のバリアがあります。 チームのマスター スレッドのみでは、並列領域の最後に実行を継続します。

並列領域を実行するチーム内のスレッドには、別の parallel コンストラクトが発生すると、新しいチームを作成およびその新しいチームのマスターになります。 入れ子になった並列領域は、既定でシリアル化されます。 その結果、既定では、入れ子になった並列領域は 1 つのスレッドから成るチームによって実行されます。 ランタイム ライブラリ関数を使用して、既定の動作を変更することがあります`omp_set_nested`または環境変数`OMP_NESTED`します。 ただし、チーム内の入れ子になった並列領域を実行するスレッドの数は、実装定義にします。

制限は、`parallel`ディレクティブは、次のとおり。

- 最大で 1 つ`if`句は、ディレクティブに表示されます。

- 場合は、内部の効果をいずれかの側かどうか指定されていない式または`num_threads`式が発生します。

- A`throw`並行領域内で実行を同じ構造化ブロックの動的範囲内で再開が発生する必要がありますが実行され、例外をスローしたのと同じスレッドで検出する必要があります。

- 1 つだけ`num_threads`句は、ディレクティブに表示されます。 `num_threads`式は、並列領域の外のコンテキストが評価され、正の整数値に評価される必要があります。

- 評価の順序、`if`と`num_threads`句が指定されていません。

### <a name="cross-references"></a>相互参照

- `private`、 `firstprivate`、 `default`、 `shared`、 `copyin`、および`reduction`句 ([セクション 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)環境変数
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)ライブラリ関数
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)環境変数
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)関数
- [OMP_NESTED](4-environment-variables.md#44-omp_nested)環境変数
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function)ライブラリ関数

## <a name="24-work-sharing-constructs"></a>2.4 動作共有のコンストラクトします。

Work-sharing コンス トラクターは、これを検出したチームのメンバーの間で関連付けられているステートメントの実行を配布します。 動作共有ディレクティブは、新しいスレッドが起動されないし、エントリ work-sharing コンス トラクターを暗黙の壁がなくなります。

作業の共有のシーケンスを構築し、`barrier`で発生するディレクティブは、チーム内のすべてのスレッドで同じである必要があります。

OpenMP は、次の作業の共有のコンストラクトを定義し、これらのコンストラクトは、次のセクションで説明されています。

- [ディ](#241-for-construct)レクティブ
- [セクション](#242-sections-construct)ディレクティブ
- [1 つ](#243-single-construct)ディレクティブ

### <a name="241-for-construct"></a>2.4.1 for コンストラクト

`for`ディレクティブが関連付けられているループのイテレーションが並列で実行されることを指定する反復的な作業の共有のコンストラクトを識別します。 反復処理、`for`ループは、バインドする、parallel コンストラクトを実行するチームに既に存在するスレッド間で分散されます。 構文、`for`コンス トラクターを次に示します。

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

句は、次のいずれか。

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `lastprivate(` *variable-list* `)`
- `reduction(` *operator* `:` *variable-list* `)`
- `ordered`
- `schedule(` *kind* [`,` *chunk_size*] `)`
- `nowait`

`for`ディレクティブに対応する構造体での制限の配置`for`ループします。 具体的には、対応する`for`ループ正規形である必要があります。

`for (` *init-expr* `;` *var  logical-op  b* `;` *incr-expr* `)`

*init-expr*<br/>
次のいずれかになります。

- *var* = *lb*
- *integer-type var* = *lb*

*incr-expr*<br/>
次のいずれかになります。

- `++` *var*
- *var* `++`
- `--` *var*
- *var* `--`
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*var*<br/>
符号付き整数変数です。 この変数を共有することがそれ以外の場合は場合、暗黙的になりますプライベートの期間中、`for`します。 本文内でこの変数は変更しないでください、`for`ステートメント。 変数を指定しない限り`lastprivate`、その値の後、ループが不定になります。

*logical-op*<br/>
次のいずれかになります。

- `<`
- `<=`
- `>`
- `>=`

*lb*、 *b*、および*incr*<br>
ループのインバリアント整数式。 これらの式の評価中に同期がないため、評価の副作用が不確定な結果を生成します。

正規の形式は、エントリ、ループを計算するループのイテレーションの数を許可します。 型で値を持つこの計算が行われた*var*、整数の上位変換後にします。 特に、値の*b* `-` *lb* `+` *incr*型、結果は不確定で表すことができません。 さらに、if*論理 op*は`<`または`<=`、し*incr expr*が発生する必要があります*var*ループの反復ごとに増加します。   場合*op 論理*は`>`または`>=`、し*incr expr*が発生する必要があります*var*がループの反復ごとに小さくなっています。

`schedule`句を指定する方法のイテレーション、`for`ループは、チームのスレッドに分割します。 プログラムの正確性は、特定のイテレーションを実行するスレッドに依存する必要があります。 値*chunk_size*、指定した場合は正の値をループのインバリアント整数式でなければなりません。 この式の評価中に同期がないため、評価副作用が不確定な結果を生成します。 スケジュール*種類*値は次のいずれかを指定できます。

表 2-1:`schedule`句*種類*値

|||
|-|-|
|静的|ときに`schedule(static,` *chunk_size* `)`を指定すると、イテレーションがで指定したサイズのチャンクに分割されて*chunk_size*します。 チャンクはスレッド番号順のラウンド ロビン方式で、チーム内のスレッドに静的に割り当てられます。 ない場合*chunk_size*を指定すると、イテレーションの領域は約サイズが同じで、各スレッドに割り当てられている 1 つのチャンクをチャンクに分かれています。|
|dynamic|ときに`schedule(dynamic,` *chunk_size* `)`を指定すると、イテレーションは、一連の各を格納しているチャンクに分けられます*chunk_size*イテレーション。 各チャンクの割り当てを待機しているスレッドが割り当てられます。 スレッドは、チャンクの処理を実行し、まで、割り当てられるチャンクが残っていないが、次の割り当てを待機します。 最後のチャンクを割り当てるには、イテレーションの数を減らしてがあります。 ない場合*chunk_size*を指定すると、既定値は 1 です。|
|ガイド付き|ときに`schedule(guided,` *chunk_size* `)`を指定すると、イテレーションはサイズが減少しているチャンク内のスレッドに割り当てられます。 スレッドには、その割り当てられたチャンクの処理が完了するが動的に割り当てられるもう 1 つのチャンクでは、none のままになるまでです。 *Chunk_size* 1、各チャンクのサイズが反復処理をスレッドの数で割った値おおよその数。 これらのサイズは、1 にほぼ指数関数的に小さくなります。 *Chunk_size*値を持つ*k* 1 より大きいサイズを減らすには指数関数的にほぼ*k*最後のチャンクがありますよりも少ないことを除いて、 *k*イテレーション。 ない場合*chunk_size*を指定すると、既定値は 1 です。|
|ランタイム|ときに`schedule(runtime)`が指定されている実行時まで遅延に関するスケジュールが決定します。 スケジュール*種類*を環境変数を設定して実行時に、チャンクのサイズを選択して`OMP_SCHEDULE`します。 この環境変数が設定されていない場合、結果として得られるスケジュールは、実装で定義します。 ときに`schedule(runtime)`が指定されている*chunk_size*指定されていない必要があります。|

明示的に定義されているがない場合は、`schedule`句では、既定の`schedule`実装で定義されます。

適切な実行の特定のスケジュール、OpenMP に準拠したプログラムは使用しないでください。 プログラムは、スケジュールを使用しないでください*種類*を同じスケジュールの実装にバリエーションがある可能性があるために、上記の説明に正確に準拠した*種類*全体異なるコンパイラ。 説明には、特定の状況に適切なスケジュールを選択ができます。

`ordered`句必要がある場合に`ordered`ディレクティブのバインド、`for`を構築します。

最後に、暗黙的な壁が、`for`れない限り、作成、`nowait`句を指定します。

制限は、`for`ディレクティブは、次のとおり。

- `for`ループは、構造化ブロックである必要があり、さらに、それを実行する必要がありますを終了できませんが、`break`ステートメント。

- ループの値の式の制御、`for`ループに関連付けられている、`for`ディレクティブは、チームのすべてのスレッドで同じである必要があります。

- `for`ループの反復変数は符号付き整数型である必要があります。

- 1 つだけ`schedule`句に表示できる、`for`ディレクティブ。

- 1 つだけ`ordered`句に表示できる、`for`ディレクティブ。

- 1 つだけ`nowait`句に表示できる、`for`ディレクティブ。

- 指定されていない場合または内の任意の辺の効果どのくらいの頻度、 *chunk_size*、 *lb*、 *b*、または*incr*式が発生します。

- 値、 *chunk_size*式は、チームのすべてのスレッドで同じである必要があります。

#### <a name="cross-references"></a>相互参照

- `private`、 `firstprivate`、 `lastprivate`、および`reduction`句 ([セクション 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)環境変数
- [順序付けられた](#266-ordered-construct)構築
- [スケジュール](d-using-the-schedule-clause.md)句

### <a name="242-sections-construct"></a>2.4.2 セクションを作成します。

`sections`ディレクティブは、チーム内のスレッド間で分配する構成要素のセットを示す noniterative の work-sharing コンストラクトを識別します。 各セクションは、チーム内のスレッドで 1 回実行されます。 構文、`sections`ディレクティブを次に示します。

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

句は、次のいずれか。

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `lastprivate(` *variable-list* `)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `nowait`

各セクションは、前に、`section`ディレクティブが、`section`ディレクティブは、最初のセクションを省略できます。 `section`ディレクティブはの構文範囲内でなければなりません。、`sections`ディレクティブ。 最後に、暗黙的な壁が、`sections`れない限り、作成、`nowait`を指定します。

制限は、`sections`ディレクティブは、次のとおり。

- A`section`の構文の範囲外ディレクティブが表示されない必要があります、`sections`ディレクティブ。

- 1 つだけ`nowait`句に表示できる、`sections`ディレクティブ。

#### <a name="cross-references"></a>相互参照

- `private`、 `firstprivate`、 `lastprivate`、および`reduction`句 ([セクション 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 single コンストラクト

`single`ディレクティブ (必ずしもマスター スレッド) のチームで 1 つのスレッドによって、関連付けられている構造化ブロックが実行されることを指定する構成要素を識別します。 構文、`single`ディレクティブを次に示します。

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

句は、次のいずれか。

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `copyprivate(` *variable-list* `)`
- `nowait`

後に暗黙の壁が、`single`れない限り、作成、`nowait`句を指定します。

制限は、`single`ディレクティブは、次のとおり。

- 1 つだけ`nowait`句に表示できる、`single`ディレクティブ。
- `copyprivate`句を使用しないで、`nowait`句。

#### <a name="cross-references"></a>相互参照

- `private`、 `firstprivate`、および`copyprivate`句 ([セクション 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 結合された並行動作共有のコンストラクト

結合された並行動作共有のコンストラクトは、1 つだけの work-sharing コンス トラクターを含む並列領域を指定するためのショートカットです。 これらのディレクティブのセマンティクスは、明示的に指定した場合と同じ、`parallel`ディレクティブの後に 1 つ work-sharing コンス トラクター。

次のセクションでは、結合された並行動作共有コンストラクトについて説明します。

- [並列](#251-parallel-for-construct)ディレクティブ
- [セクションの並列](#252-parallel-sections-construct)ディレクティブ

### <a name="251-parallel-for-construct"></a>2.5.1 parallel for コンストラクト

`parallel for`ディレクティブは、ショートカット、`parallel`が 1 つのみを含む領域`for`ディレクティブ。 構文、`parallel for`ディレクティブを次に示します。

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

このディレクティブのすべての句を使用して、`parallel`ディレクティブと`for`ディレクティブを除く、`nowait`と同じ意味と制限の句。 セマンティクスは、明示的に指定した場合と同じ、`parallel`ディレクティブの直後に続く、`for`ディレクティブ。

#### <a name="cross-references"></a>相互参照

- [並列](#23-parallel-construct)ディレクティブ
- [ディ](#241-for-construct)レクティブ
- [データ属性句](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 セクションでは parallel コンストラクト

`parallel sections`ディレクティブを指定するためのショートカット フォームの提供、`parallel`を 1 つだけを持つリージョン`sections`ディレクティブ。 セマンティクスは、明示的に指定した場合と同じ、`parallel`ディレクティブの直後に続く、`sections`ディレクティブ。 構文、`parallel sections`ディレクティブを次に示します。

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

*句*で受け入れられる句のいずれか、`parallel`と`sections`ディレクティブを除く、`nowait`句。

#### <a name="cross-references"></a>相互参照

- [並列](#23-parallel-construct)ディレクティブ
- [セクション](#242-sections-construct)ディレクティブ

## <a name="26-master-and-synchronization-directives"></a>2.6 マスター ディレクティブと同期ディレクティブ

次のセクションについて説明します。

- [マスター](#261-master-construct)構築
- [重要な](#262-critical-construct)構築
- [バリア](#263-barrier-directive)ディレクティブ
- [アトミック](#264-atomic-construct)構築
- [フラッシュ](#265-flush-directive)ディレクティブ
- [順序付けられた](#266-ordered-construct)構築

### <a name="261-master-construct"></a>2.6.1 master コンストラクト

`master`ディレクティブは、チームのマスター スレッドによって実行される構造化ブロックを指定する構成を識別します。 構文、`master`ディレクティブを次に示します。

```cpp
#pragma omp master new-linestructured-block
```

チームの他のスレッドは、関連付けられている構造化ブロックを実行しません。 エントリまたは master コンストラクトから終了のいずれかの暗黙の壁がなくなります。

### <a name="262-critical-construct"></a>2.6.2 critical コンストラクト

`critical`ディレクティブは、一度に 1 つのスレッドに関連付けられている構造化ブロックの実行を制限する構成要素を識別します。 構文、`critical`ディレクティブを次に示します。

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

省略可能な*名前*クリティカル領域を識別するために使用可能性があります。 重要な領域を識別するために使用される識別子は外部リンケージを持ち、ラベル、タグ、メンバー、および通常の識別子で使用される名前空間から分離された名前空間では。

スレッドは、他のスレッドが同じ名前の重要な領域 (任意の場所でプログラム) を実行していないまで、クリティカル領域の先頭に待機します。 名前のないすべて`critical`ディレクティブが指定されていない名前が同じものにマップします。

### <a name="263-barrier-directive"></a>2.6.3 barrier ディレクティブ

`barrier`ディレクティブは、チーム内のすべてのスレッドを同期します。 発生すると、チーム内の各スレッドはこのポイント他のすべてに到達するまで待機します。 構文、`barrier`ディレクティブを次に示します。

```cpp
#pragma omp barrier new-line
```

チームのすべてのスレッドは、障害が発生した、チーム内の各スレッドが並列で barrier ディレクティブの後、ステートメントの実行開始されます。 `barrier`ディレクティブは、構文の一部として、C 言語のステートメントがない、プログラム内の位置でいくつかの制限があります。 正式な文法の詳細については、次を参照してください。[付録 C](c-openmp-c-and-cpp-grammar.md)します。次の例では、これらの制限事項を示します。

```cpp
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```

### <a name="264-atomic-construct"></a>2.6.4 atomic コンストラクト

`atomic`ディレクティブでは、複数の可能性が公開することではなく特定のメモリ位置が、アトミックに更新されたことにより、同時スレッドを作成します。 構文、`atomic`ディレクティブを次に示します。

```cpp
#pragma omp atomic new-lineexpression-stmt
```

式ステートメントは、次の形式のいずれかが必要です。

- *x binop* `=` *expr*
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

上記の式。

- *x*スカラー型の左辺値式を指定します。

- *expr* 、スカラー型の式で指定されたオブジェクトを参照していない*x*します。

- *binop*オーバー ロードされた演算子のないの 1 つ`+`、 `*`、 `-`、 `/`、 `&`、 `^`、 `|`、 `<<`、または`>>`します。

実装で定義された実装がすべてを置換するかどうか`atomic`ディレクティブを`critical`ディレクティブが同じ一意*名前*、`atomic`ディレクティブより優れた最適化を許可. 多くの場合、ハードウェアの手順については、最小限のオーバーヘッドでアトミックな更新プログラムを実行することができます。

負荷とで指定されたオブジェクトのストアのみ*x*がアトミック; の評価*expr*アトミックではありません。 競合状態を避けるためには、並列の場所のすべての更新プログラムで保護する必要があります、`atomic`競合状態の認識されているもの以外のディレクティブ。

制限は、`atomic`ディレクティブは、次のとおり。

- プログラム全体で x 記憶域の場所へのすべての分割不可能な参照は、互換性のある型である必要があります。

#### <a name="examples"></a>使用例

```cpp
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```

### <a name="265-flush-directive"></a>2.6.5 flush ディレクティブ

`flush`ディレクティブで明示的または黙示に関わらず、かどうかは実装が現在チームのすべてのスレッドは、特定のオブジェクトがメモリ内 (以下) の一貫したビューでいることを確認に必要な場合は、「スレッド間」シーケンス ポイントを指定します。 これは、前のこれらのオブジェクトを参照する式の評価が完了し、以降の評価が開始されていないことを意味します。 たとえば、コンパイラは、メモリにレジスタからのオブジェクトの値を復元する必要があり、ハードウェアは、メモリへの書き込みバッファーをフラッシュし、メモリからオブジェクトの値を再読み込みする必要があります。

構文、`flush`ディレクティブを次に示します。

```cpp
#pragma omp flush [(variable-list)]  new-line
```

同期が必要なオブジェクトすべて指定するには、変数で、省略可能なこれらの変数を指定することができる場合*変数一覧*します。 ポインターがある場合、*変数一覧*、ポインター自体がフラッシュされる、オブジェクトではなく、ポインターが参照します。

A`flush`せずディレクティブ、*変数一覧*自動ストレージ存続期間とアクセスできないオブジェクトを除くすべての共有オブジェクトを同期します。 (よりも多くのオーバーヘッドがある可能性があります、`flush`で、*変数一覧*)。A`flush`せずディレクティブ、*変数一覧*が暗黙的に次のディレクティブの指定します。

- `barrier`
- エントリとからの終了 `critical`
- エントリとからの終了 `ordered`
- エントリとからの終了 `parallel`
- 終了時 `for`
- 終了時 `sections`
- 終了時 `single`
- エントリとからの終了 `parallel for`
- エントリとからの終了 `parallel sections`

場合、ディレクティブが暗黙的に指定されていない、`nowait`句が存在します。 注意するべきことを`flush`次のいずれかのディレクティブが暗黙的に指定されていません。

- 入る `for`
- エントリをまたはからの終了 `master`
- 入る `sections`
- 入る `single`

Volatile で修飾された型のオブジェクトの値にアクセスするための参照があった場合と同様に、`flush`ディレクティブの前のシーケンス ポイントにそのオブジェクトを指定します。 Volatile で修飾された型のオブジェクトの値を変更するための参照があった場合と同様に、`flush`後続シーケンス ポイントにそのオブジェクトを指定するディレクティブ。

`flush`ディレクティブは、構文の一部として、C 言語のステートメントがない、プログラム内の位置でいくつかの制限があります。 正式な文法の詳細については、次を参照してください。[付録 C](c-openmp-c-and-cpp-grammar.md)します。次の例では、これらの制限事項を示します。

```cpp
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

制限は、`flush`ディレクティブは、次のとおり。

- 指定される変数を`flush`ディレクティブが参照型に必要ありません。

### <a name="266-ordered-construct"></a>2.6.6 順序付けられた構造

構造化ブロックの後、`ordered`ディレクティブはシーケンシャル ループのイテレーションが実行は順序で実行されます。 構文、`ordered`ディレクティブを次に示します。

```cpp
#pragma omp ordered new-linestructured-block
```

`ordered`ディレクティブはの動的範囲内である必要があります、`for`または`parallel for`を構築します。 `for`または`parallel for`するディレクティブ、`ordered`コンストラクトにバインドする必要がありますが、 `ordered` 」の説明に従って指定された句[2.4.1 セクション](#241-for-construct)します。 実行時に、`for`または`parallel for`で構築、`ordered`句、`ordered`コンストラクトはシーケンシャル ループの実行で実行される順序で厳密に実行されます。

制限は、`ordered`ディレクティブは、次のとおり。

- 使用して、ループのイテレーションを`for`コンストラクトする必要があります、同じ順序付けられたディレクティブは 2 回以上実行されず、1 つ以上実行する必要がありますいない`ordered`ディレクティブ。

## <a name="27-data-environment"></a>2.7 データ環境

このセクションでは、ディレクティブと次のように、並行領域の実行中にデータ環境を制御するためのいくつかの句では。

- A [threadprivate](#271-threadprivate-directive)ディレクティブは、作成、ファイル スコープ、名前空間スコープ、または静的のブロック スコープ変数をこのスレッドにローカルに提供されます。

- 並列または動作共有のコンストラクトの実行中の変数の共有の属性を制御するディレクティブで指定できる句が記載されて[セクション 2.7.2](#272-data-sharing-attribute-clauses)します。

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate ディレクティブ

`threadprivate`ディレクティブによって、名前付きのファイル スコープ、名前空間スコープ、または静的ブロック スコープの変数で指定された、*変数一覧*スレッドに対してプライベートです。 *変数リスト*が不完全な型がない変数のコンマ区切り一覧。 構文、`threadprivate`ディレクティブを次に示します。

```cpp
#pragma omp threadprivate(variable-list) new-line
```

各コピーを`threadprivate`変数が初期化される 1 回、そのコピーが最初に参照する前にプログラムで、通常の方法で指定されていない点の位置 (つまり、プログラムの直列実行では、マスター コピーを初期化すると) とします。 明示的な初期化子でオブジェクトが参照されている場合、`threadprivate`変数、およびオブジェクトの値が、変数のコピーが最初に参照する前に変更し、動作は指定されていません。

ように、任意のプライベート変数のスレッドを参照しないでの別のスレッドのコピーを`threadprivate`オブジェクト。 シリアル領域や、プログラムのマスターの地域において、中には、参照をオブジェクトのマスター スレッドのコピーになります。

最初の並行領域内のデータ実行した後、`threadprivate`オブジェクトを並行領域のすべてのスレッドの数は変更されない場合にのみ、場合は、動的なスレッドのメカニズムを無効になっていますを保持することが保証されます。

制限、`threadprivate`ディレクティブは、次のとおり。

- A`threadprivate`ファイル スコープまたは名前空間スコープの変数のディレクティブは、任意の定義または宣言の外側に表示する必要があり、その一覧で、変数のいずれかに対するすべての参照の前に構文的する必要があります。

- 内の各変数、*変数一覧*の`threadprivate`ファイルまたは名前空間のスコープでディレクティブを指定する必要があります字句ディレクティブの前にあるファイルまたは名前空間のスコープで変数の宣言を参照してください。

- A`threadprivate`と入れ子になったスコープではなく、変数のスコープ内で静的ブロック スコープ変数のディレクティブを表示する必要があります。 構文的ディレクティブは、変数のいずれかにすべての参照を前に、リストにする必要があります。

- 内の各変数、*変数一覧*の`threadprivate`ディレクティブ ブロック スコープでは、字句ディレクティブの前にある同じスコープ内で変数の宣言を指す必要があります。 変数の宣言には、静的ストレージ クラス指定子を使用する必要があります。

- 変数がで指定されている場合、`threadprivate`ディレクティブを 1 つの翻訳単位で、これで指定する必要を`threadprivate`が宣言されている各翻訳単位でディレクティブ。

- A`threadprivate`を除くすべての句に変数がない必要があります、 `copyin`、 `copyprivate`、 `schedule`、 `num_threads`、または`if`句。

- アドレスを`threadprivate`変数は、アドレスは一定です。

- A`threadprivate`変数は不完全な型または参照型をしなければなりません。

- A`threadprivate`非 POD クラス型の変数は、明示的な初期化子で宣言されている場合、あいまいでないアクセス可能なコピー コンス トラクターにいる必要があります。

次の例では、方法、初期化子に表示される変数を変更する可能性が未定義の動作と補助オブジェクトおよびコピー コンス トラクターを使用してこの問題を回避する方法も示しています。

```cpp
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

#### <a name="cross-references"></a>相互参照

- [動的なスレッド](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)環境変数

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 データ共有属性句

いくつかのディレクティブは、ユーザーが、リージョンの間の変数の共有の属性を制御できるようにする句を受け入れます。 共有属性句は、句が表示される、ディレクティブの構文範囲内の変数にのみ適用されます。 次の句の一部は、すべてのディレクティブで許可されます。 特定のディレクティブで有効な句の一覧については、ディレクティブを使用して説明します。

変数は、並列操作を実行すると表示される、または動作共有のコンストラクトが見つかりましたが、変数が共有属性句で指定されていない場合または`threadprivate`ディレクティブ、変数が共有されます。 並列領域の動的範囲内で宣言された静的変数が共有されます。 メモリを割り当てられたヒープ (を使用するなど`malloc()`C または C++ でまたは`new`c++ 演算子) が共有します。 (このメモリへのポインター、ただしできますプライベートまたは共有のいずれか。)自動ストレージ存続期間を並行領域の動的範囲内で宣言された変数はプライベートです。

句のほとんどを受け入れる、*変数一覧*が表示されている変数のコンマ区切りのリストの引数。 変数が参照されている場合は、データ共有属性句が、テンプレートから派生した型、他のプログラムでその変数への参照がないと、動作は定義。

ディレクティブの句内に表示されるすべての変数は、表示である必要があります。 句は、必要に応じて繰り返すことが変数可能性がありますが指定されていない 1 つ以上の句でする点を除いて、両方の変数を指定できます、`firstprivate`と`lastprivate`句。

次のセクションでは、データ共有属性句について説明します。

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [shared](#2724-shared)
- [default](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

`private`句のチームでは、各スレッドに対してプライベートにするには、変数の一覧の変数を宣言します。 構文、`private`句を次に示します。

```cpp
private(variable-list)
```

指定される変数の動作を`private`句を次に示します。 自動ストレージ存続期間で新しいオブジェクトは、構造に割り当てられます。 新しいオブジェクトの配置とサイズについては、変数の型によって決まります。 この割り当ては、チーム内の各スレッドの 1 回発生し、必要に応じて、クラス オブジェクトの既定のコンス トラクターが呼び出されますそれ以外の場合、初期値は、不確定ではありません。  変数によって参照されている元のオブジェクトは、コンストラクトに入ったときに中間の値を持つ、コンストラクトの動的範囲内で変更しないで、およびコンストラクトから終了時に中間の値を持ちます。

ディレクティブのコンストラクトの構文の範囲では、変数は、新しいスレッドによって割り当てられたプライベート オブジェクトを参照します。

制限、`private`句は、次のとおり。

- 指定されているクラス型の変数を`private`句は、あいまいでないアクセス可能な既定のコンス トラクターをいる必要があります。

- 指定される変数を`private`句は必要ありません、 `const`-型をクラスがない限り、型を修飾、`mutable`メンバー。

- 指定される変数を`private`句が不完全な型または参照型は必要ありません。

- 表示される変数、`reduction`の句、`parallel`でディレクティブを指定することはできません、 `private` parallel コンストラクトにバインドされる動作共有ディレクティブの句。

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

`firstprivate`句によって提供される機能のスーパー セットを提供する、`private`句。 構文、`firstprivate`句を次に示します。

```cpp
firstprivate(variable-list)
```

指定する変数*変数一覧*が`private`句セマンティクス」の説明に従って[2.7.2.1 セクション](#2721-private)します。 初期化または構築は、コンス トラクターのスレッドの実行前に、スレッドあたり 1 回実行された場合に発生します。 `firstprivate` Parallel コンストラクトの句は、新しいプライベート オブジェクトの初期値は、これが発生したスレッドの parallel コンストラクトする直前にある元のオブジェクトの値。 `firstprivate` Work-sharing コンス トラクターで句、work-sharing コンス トラクターを実行する各スレッドの場合は、新しいプライベート オブジェクトの初期値は前の時点を検出すると、同じスレッドのことが存在する元のオブジェクトの値、work-sharing コンス トラクター。 さらに、C++ のオブジェクトの各スレッドの新しいプライベート オブジェクトは、元のオブジェクトから構築されたコピーです。

制限、`firstprivate`句は、次のとおり。

- 指定される変数を`firstprivate`句が不完全な型または参照型は必要ありません。

- として指定されているクラス型の変数を`firstprivate`あいまいでないアクセス可能なコピー コンス トラクターを含める必要があります。

- 並行領域内でプライベート変数に表示される、`reduction`の句、`parallel`でディレクティブを指定することはできません、 `firstprivate` parallel コンストラクトにバインドされる動作共有ディレクティブの句。

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

`lastprivate`句によって提供される機能のスーパー セットを提供する、`private`句。 構文、`lastprivate`句を次に示します。

```cpp
lastprivate(variable-list)
```

指定する変数、*変数一覧*が`private`句セマンティクスです。 ときに、`lastprivate`コンストラクト作業の共有、それぞれの値を識別するディレクティブの句が表示されます`lastprivate`に関連付けられているループ、または構文的に最後のセクション ディレクティブでは、順に最後のイテレーションからの変数が割り当てられている、変数の元のオブジェクト。 最後の反復によって値が割り当てられていない変数、`for`または`parallel for`、またはの構文的に最後のセクションで、`sections`または`parallel sections`ディレクティブ、不確定な値が、構築後にあります。 割り当てられていないサブオブジェクトも、構築後に、不確定な値であります。

制限、`lastprivate`句は、次のとおり。

- すべての制限の`private`を適用します。

- として指定されているクラス型の変数を`lastprivate`あいまいでないアクセス可能なコピー代入演算子を指定する必要があります。

- 並行領域内でプライベート変数に表示される、`reduction`の句、`parallel`でディレクティブを指定することはできません、 `lastprivate` parallel コンストラクトにバインドされる動作共有ディレクティブの句。

#### <a name="2724-shared"></a>2.7.2.4 shared

この句に出現する変数を共有する、*変数一覧*チーム内のすべてのスレッド間で。 チーム内のすべてのスレッドへのアクセスに同じ記憶域`shared`変数。

構文、`shared`句を次に示します。

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

`default`句に変数のデータ共有属性の影響を与えるユーザーを使用できます。 構文、`default`句を次に示します。

```cpp
default(shared | none)
```

指定する`default(shared)`に現在表示されている各変数を明示的に一覧表示するのと同じですが、`shared`句である場合を除き`threadprivate`または`const`-修飾します。 明示的ながない場合は、`default`句では、既定の動作と同じだ場合`default(shared)`指定されました。

指定する`default(none)`parallel コンストラクトの構文範囲内の変数への参照をすべて true に設定で、次の少なくとも 1 つなければならないことが必要です。

- 変数は、参照を含んでいる構造のデータ共有属性句で明示的に一覧表示します。

- 変数は、parallel コンストラクト内で宣言されています。

- 変数が`threadprivate`します。

- 変数が、 `const`-型を修飾します。

- 変数が for ループ コントロール変数を`for`直後に続くループ、`for`または`parallel for`ループ内で、ディレクティブ、および変数の参照が表示されます。

変数を指定する、 `firstprivate`、 `lastprivate`、または`reduction`と、変数への暗黙的な参照をそれを囲むコンテキスト内に含まれているディレクティブの句。 このような暗黙的な参照は、上記の要件の対象も。

1 つだけ`default`句で指定できる、`parallel`ディレクティブ。

変数の既定のデータ共有属性を使用してオーバーライドできます、 `private`、 `firstprivate`、 `lastprivate`、`reduction`と`shared`句は、次の例に示すようにします。

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

この句に表示されるスカラー変数でリダクションを実行します*変数一覧*、演算子を含む*op*します。 構文、`reduction`句を次に示します。

`reduction(` *op* `:` *variable-list* `)`

リダクションは、通常、次の形式のいずれかのステートメントに対して指定します。

- *x* `=` *x* *op* *expr*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x* (減算) を除く
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

それぞれの文字について以下に説明します。

*x*<br/>
一覧で指定されたリダクション変数の 1 つ。

*variable-list*<br/>
スカラー リダクション変数のコンマ区切りの一覧。

*expr*<br/>
参照しないスカラー型の式*x*します。

*op*<br/>
オーバー ロードされた演算子ではなく 1 つ残して`+`、 `*`、 `-`、 `&`、 `^`、 `|`、 `&&`、または`||`します。

*binop*<br/>
オーバー ロードされた演算子ではなく 1 つ残して`+`、 `*`、 `-`、 `&`、 `^`、または`|`します。

例を次に、`reduction`句。

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

例に示すように関数呼び出しの内部で、演算子が非表示に可能性があります。 ユーザーが注意が必要で、演算子が指定されているように、`reduction`句に一致するリダクション演算。

右オペランド、`||`演算子この例では副作用がない、許可されている、相手は、注意して使用する必要があります。 このコンテキストで、並列実行中に、ループの連続した実行中に発生が保証されていることの副作用があります。 この違いは、イテレーションの実行の順序は不確定場合に発生します。

演算子を削減のため、コンパイラによって使用される任意のプライベート変数の初期値を確認し、終了演算子が決定に使用されます。 演算子を明示的に指定すると、構文、コンストラクトの範囲外にあるリダクション ステートメントができます。 任意の数の`reduction`、ディレクティブの句を指定することがありますが、最大で 1 つに、変数が表示されます`reduction`そのディレクティブの句。

内の各変数のプライベート コピーを*変数一覧*作成されると、スレッドごとに 1 つとして、`private`句が使用されている必要があります。 プライベート コピーが、演算子に従って初期化されます (次の表を参照してください)。

対象の領域の最後に、`reduction`句が指定されて、指定された演算子を使用してプライベート コピーのそれぞれの最終的な値で元の値を組み合わせた結果を反映するように、元のオブジェクトが更新されます。 リダクション演算子は、すべて (減算) を除くと、コンパイラは、最終的な値の計算を関連付けし直す自由に。 (減算のリダクションの部分的な結果は、最終的な値をフォームに追加されます)。

最初のスレッドが含む句に達するし、リダクションの計算が完了するまで、維持、元のオブジェクトの値は不確定になります。  通常、計算を; 構造の最後に完了します。ただし場合、`reduction`句を使用して先のコンストラクトに`nowait`も適用すると、元のオブジェクトの値が不確定なバリア同期が実行されるすべてのスレッドが、を完了していることを確認するまで`reduction`句。

次の表は、有効な演算子とその標準的な初期値を示します。 実際の初期値は減少変数のデータ型と一致になります。

|演算子|初期化|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

制限、`reduction`句は、次のとおり。

- 変数の型、`reduction`ポインター型と参照型が使用できないことを除いて句が有効、減少演算子である必要があります。

- 指定されている変数、`reduction`句がある必要がありますいない`const`-修飾します。

- 並行領域内でプライベート変数に表示される、`reduction`の句、`parallel`でディレクティブを指定することはできません、 `reduction` parallel コンストラクトにバインドされる動作共有ディレクティブの句。

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```

#### <a name="2727-copyin"></a>2.7.2.7 copyin

`copyin`句に同じ値を代入するためのメカニズムを提供する`threadprivate`並列領域を実行する、チーム内の各スレッドの変数。 指定された各変数に対して、`copyin`並列領域の先頭に、スレッド プライベート コピーへの代入した場合と同じ句では、チームのマスター スレッド内の変数の値をコピーします。 構文、`copyin`句を次に示します。

```cpp

copyin(
variable-list
)
```

制限、`copyin`句は、次のとおり。

- 指定されている変数、`copyin`句があいまいでないアクセス可能なコピー代入演算子を指定する必要があります。

- 指定されている変数、`copyin`句がある必要があります、`threadprivate`変数。

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

`copyprivate`句がプライベート変数を使用して、他のメンバーにチームの 1 つのメンバーから値をブロードキャストするメカニズムを提供します。 このような共有変数を提供するが難しい (たとえばの各レベルで別の変数を必要とする再帰) ときに、値の共有変数を使用する代わりにすることをお勧めします。 `copyprivate`句にのみ表示できる、`single`ディレクティブ。

構文、`copyprivate`句を次に示します。

```cpp

copyprivate(
variable-list
)
```

効果、`copyprivate`句の変数リストに、変数に関連付けられている構造化ブロックの実行後に発生します、`single`構築、およびコンス トラクターの末尾にバリアを左チーム内のスレッドの前にします。 その後、それぞれの変数に、チームの他のすべてのスレッドで、*変数一覧*、対応する値をその変数になります (割り当て) した場合と同じ定義されている、コンストラクトを実行するスレッドの変数の構造化ブロックです。

制限は、`copyprivate`句は、次のとおり。

- 指定されている変数、`copyprivate`句は必要がありますには表示されない、`private`または`firstprivate`同じ句`single`ディレクティブ。

- 場合、`single`ディレクティブ、`copyprivate`で指定されたすべての変数を並行領域の動的範囲で、句が発生しました、`copyprivate`句は外側のコンテキストではプライベートである必要があります。

- 指定されている変数、`copyprivate`句は、アクセス可能な明確なコピー代入演算子を指定する必要があります。

## <a name="28-directive-binding"></a>2.8 ディレクティブのバインディング

ディレクティブの動的バインドは、次の規則に従う必要があります。

- `for`、 `sections`、 `single`、 `master`、および`barrier`ディレクティブに動的にそれを囲むバインド`parallel`いずれかの値に関係なく、存在する場合、`if`句を上に存在する可能性があります。ディレクティブ。 並列領域が現在実行されていない、ディレクティブは、マスター スレッドのみから成るチームによって実行されます。

- `ordered`ディレクティブに動的にそれを囲むバインド`for`します。

- `atomic`ディレクティブを排他アクセスを強制する`atomic`現在のチームだけでなく、すべてのスレッドでのディレクティブ。

- `critical`ディレクティブを排他アクセスを強制する`critical`現在のチームだけでなく、すべてのスレッドでのディレクティブ。

- ディレクティブとも、最も近い外側の任意のディレクティブを動的にバインドできませんを囲む`parallel`します。

## <a name="29-directive-nesting"></a>2.9 ディレクティブの入れ子

ディレクティブの動的なネストは、次の規則に従う必要があります。

- A`parallel`別内で動的にディレクティブ`parallel`論理的に現在のスレッドのみから構成される、新しいチームが、並列処理を入れ子になっている場合を除きが有効になってを確立します。

- `for`、 `sections`、および`single`に同じバインド ディレクティブ`parallel`は互いの内部で入れ子にできません。

- `critical` 同じ名前のディレクティブは互いの内部で入れ子にできません。 この制限はデッドロックを防止するための十分なことに注意してください。

- `for`、 `sections`、および`single`ディレクティブはの動的範囲で許可`critical`、 `ordered`、および`master`場合は、ディレクティブのバインドを同じリージョン`parallel`領域として。

- `barrier` ディレクティブはの動的範囲で許可されていない`for`、 `ordered`、 `sections`、 `single`、 `master`、および`critical`場合は、ディレクティブのバインドを同じリージョン`parallel`地域として。

- `master` ディレクティブはの動的範囲で許可されていない`for`、 `sections`、および`single`ディレクティブ場合、`master`ディレクティブのバインドを同じ`parallel`動作共有ディレクティブとして。

- `ordered` ディレクティブはの動的範囲で許可されていない`critical`場合は、ディレクティブのバインドを同じリージョン`parallel`地域として。

- 並列領域外で実行されるときに、並行領域内で動的に実行されるときに許可される任意のディレクティブが許可されても。 ユーザー指定の並列領域の外側に動的に実行される、ディレクティブは、マスター スレッドのみから成るチームによって実行されます。
