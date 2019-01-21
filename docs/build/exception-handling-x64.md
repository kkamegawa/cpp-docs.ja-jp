---
title: x64 例外処理
ms.date: 12/17/2018
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: 33206dfb885239839c3a64436b6b540fc7d4e6e5
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627541"
---
# <a name="x64-exception-handling"></a>x64 例外処理

構造化例外処理と C++ 例外処理のコーディング規則と、x64 での動作の概要。 例外処理の概要については、次を参照してください。 [Visual c での例外処理](../cpp/exception-handling-in-visual-cpp.md)します。

## <a name="unwind-data-for-exception-handling-debugger-support"></a>アンワインドの例外処理、デバッガーのサポート データ

複数のデータ構造は、例外処理とデバッグのサポートに必要な。

### <a name="struct-runtimefunction"></a>構造体 RUNTIME_FUNCTION

テーブルに基づく例外処理では、スタック領域の割り当てまたは別の関数 (たとえば、非リーフ関数) を呼び出すすべての関数のテーブルのエントリが必要です。 関数のテーブル エントリ フォーマットであります。

|||
|-|-|
|ULONG|関数の開始アドレス|
|ULONG|関数の終了アドレス|
|ULONG|アンワインド情報のアドレス|

RUNTIME_FUNCTION 構造体は、メモリに配置するか DWORD である必要があります。 すべてのアドレスは、イメージからの相対は、関数のテーブルのエントリを含むイメージの開始アドレスからの 32 ビットのオフセット。 これらのエントリは並べ替えられ、pe 32 + イメージの .pdata セクションに配置します。 [JIT コンパイラ] 動的に生成された関数の場合、ランタイムをこれらの関数をサポートする必要がありますまたはを使用 RtlInstallFunctionTableCallback RtlAddFunctionTable オペレーティング システムにこの情報を提供します。 これに失敗すると、信頼性の低い例外処理やプロセスのデバッグが発生します。

### <a name="struct-unwindinfo"></a>構造体 UNWIND_INFO

アンワインド データ情報構造体を使用して、関数のスタック ポインターと不揮発性レジスタがスタックに保存されているが及ぼす影響を記録します。

|||
|-|-|
|UBYTE:3|Version|
|UBYTE:5|フラグ|
|UBYTE|プロローグのサイズ|
|UBYTE|アンワインド コードの数|
|UBYTE:4|フレームの登録|
|UBYTE:4|フレーム (スケール) レジスタのオフセット|
|USHORT \* n|アンワインド コード配列|
|変数|いずれかの形式の (1) またはできます (2) 以下|

(1) 例外ハンドラー

|||
|-|-|
|ULONG|例外ハンドラーのアドレス|
|変数|言語固有のハンドラーのデータ (省略可能)|

(2) チェーン アンワインド情報

|||
|-|-|
|ULONG|関数の開始アドレス|
|ULONG|関数の終了アドレス|
|ULONG|アンワインド情報のアドレス|

UNWIND_INFO 構造体は、メモリに配置するか DWORD である必要があります。 各フィールドの意味を次に示します。

- **Version**

   1 現在、アンワインド データのバージョン番号です。

- **フラグ**

   現在、3 つのフラグが定義されています。

   |フラグ|説明|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 関数は、例外ハンドラーが例外を確認する必要がある関数を検索するときに呼び出す必要があります。|
   |`UNW_FLAG_UHANDLER`| 関数には、例外のアンワインド時に呼び出される必要があります終了ハンドラーを指定します。|
   |`UNW_FLAG_CHAININFO`| これはアンワインド情報の構造は、プロシージャの主なものではありません。 代わりに、チェーン アンワインド情報エントリは、前の RUNTIME_FUNCTION エントリの内容とします。 については、次を参照してください。[アンワインド情報の構造の連結された](#chained-unwind-info-structures)します。 このフラグを設定するが存在する UNW_FLAG_EHANDLER と UNW_FLAG_UHANDLER フラグをクリアする必要があります。 また、フレームの登録と固定スタック割り当てフィールドには、プライマリ アンワインド情報と同じ値が必要です。|

- **プロローグのサイズ**

   (バイト単位)、関数プロローグの長さ。

- **アンワインド コードの数**

   アンワインド コード配列のスロットの数。 一部のアンワインド コード、たとえば、UWOP_SAVE_NONVOL、配列内の 1 つ以上のスロットが必要です。

- **フレームの登録**

   関数は、フレーム ポインター (FP) を使用し、0 以外の場合は、このフィールドが UNWIND_CODE ノードの操作情報フィールドに同じエンコーディングを使用して、フレーム ポインターとして使用される不揮発性レジスタの数です。

- **フレーム (スケール) オフセットを登録します。**

   フレームのレジスタのフィールドが 0 以外の場合は、このフィールドから RSP FP に適用されるスケールされたオフセットが確立されるときに登録します。 実際の FP レジスタが RSP + 16 に設定されている\*この番号は、240 の 0 からのオフセットします。 このオフセットは、動的スタック フレームを短い手順 (詳細な手順については、8 ビット符号付きオフセット形式を使用できます) より優れたコードの密度を許可するローカル スタック割り当ての中央に FP レジスタを指すを許可します。

- **アンワインド コード配列**

   不揮発性レジスタと RSP プロローグの効果を説明する項目の配列。 個々 の項目の意味について UNWIND_CODE のセクションを参照してください。 配置のために、この配列は常に偶数のエントリを持ち、最終的なエントリが使用される可能性があります。 その場合は、配列は、1 つのアンワインド コード フィールドの数で示されるよりも長くなります。

- **例外ハンドラーのアドレス**

   関数の言語固有の例外または UNW_FLAG_CHAININFO フラグが存在する UNW_FLAG_EHANDLER または UNW_FLAG_UHANDLER フラグのいずれかで設定されている場合、終了ハンドラーのいずれかへのイメージの相対ポインター。

- **言語固有のハンドラーのデータ**

   関数の言語固有の例外ハンドラーのデータ。 このデータの形式が指定されていないし、使用中の特定の例外ハンドラーによって完全に決定されます。

- **チェーン アンワインド情報**

   UNW_FLAG_CHAININFO フラグが設定されている場合は、3 つ UWORDs で UNWIND_INFO 構造体が終了します。  これら UWORDs では、関数のチェーンのアンワインドの RUNTIME_FUNCTION 情報を表します。

### <a name="struct-unwindcode"></a>構造体 UNWIND_CODE

アンワインド コード配列を使用して、不揮発性レジスタと RSP に影響を与えるプロローグ内で一連の操作を記録します。 各コード項目では、この形式があります。

|||
|-|-|
|UBYTE|プロローグ内のオフセット|
|UBYTE:4|アンワインド コードの操作|
|UBYTE:4|操作情報|

配列は、プロローグ内のオフセットの降順で並べ替えられます。

#### <a name="offset-in-prolog"></a>プロローグ内のオフセット

この操作では、+ 1 (つまり、次の命令の開始のオフセット) を実行する命令の終わりのプロローグの先頭からのオフセットします。

#### <a name="unwind-operation-code"></a>アンワインド コードの操作

メモ:特定のオペレーション コードには、ローカルのスタック フレームの値を符号なしのオフセットが必要です。 このオフセットは固定のスタック割り当ての最下位のアドレスは、開始日です。 Unwind_info フレーム登録フィールドが 0 の場合、このオフセットは RSP からです。 フレームの登録 フィールドが 0 以外の場合は、これは、RSP があった場所 FP レジスタが確立されたときからのオフセット。 これは、場合、FP レジスタのオフセットを引いた FP レジスタになります (16\*フレーム unwind_info オフセットを登録する)。 FP レジスタが使用されている場合、アンワインド コードのオフセットを取得する必要がありますのみ使用 FP レジスタがプロローグで確立された後。

除くすべてのオペコードの`UWOP_SAVE_XMM128`と`UWOP_SAVE_XMM128_FAR`オフセットが 8 の倍数では常に、(スタック自体は 16 バイトでアラインでは常に)、8 バイト境界に、関心のある値が格納されているため、すべてのスタックします。 短いオフセット (512 K 未満) を使用するオペレーション コード、このコードのノードの最後の USHORT は 8 で割った値のオフセットを保持します。 時間のオフセットを使用するオペレーション コードを (512 K < = < 4 GB のオフセット)、このコードの最後の 2 つ USHORT ノード (リトル エンディアン形式) でのオフセットを保持します。

オペコードの`UWOP_SAVE_XMM128`と`UWOP_SAVE_XMM128_FAR`、オフセットのでは常に 16 の倍数で 16 バイトのアラインされたメモリの 128 ビット XMM のすべての操作を行う必要があります。 16 のスケール ファクターを使用するため、`UWOP_SAVE_XMM128`より小さい 1 m 分のオフセットが許可されます。

アンワインド操作コードでは、これらの値の 1 つです。

- `UWOP_PUSH_NONVOL` (0) 1 つのノード

  不揮発性の整数レジスタ、8 でデクリメント RSP をプッシュします。 操作情報は、レジスタの数です。 エピローグでは、上の制約により`UWOP_PUSH_NONVOL`アンワインド コードがプロローグ内の先頭し、同様に、最後のアンワインド コード配列にする必要があります。 この相対順序を除くその他のすべてのアンワインド コードに適用されます`UWOP_PUSH_MACHFRAME`します。

- `UWOP_ALLOC_LARGE` (1) 2 または 3 つのノード

  スタックのサイズの大きい領域を割り当てます。 2 つの形式があります。 操作情報には、0 の場合で割った値割り当てのサイズと等しい 8 は、512 K - 8 まで割り当てを許可する、[次へ] のスロットに記録されます。 操作情報が 1 と等しいかどうかは、割り当て、リトル エンディアン形式で次の 2 つのスロットに、割り当てのサイズはスケーリングが記録された最大 4 GB - 8。

- `UWOP_ALLOC_SMALL` (2) 1 つのノード

  スタック上の小規模な領域を割り当てます。 割り当てのサイズは、操作情報 フィールド\*8 + 8、8 から 128 バイトの割り当てを許可します。

  スタック割り当てのアンワインド コードは、最短エンコードを常に使用する必要があります。

  |**アロケーション サイズ**|**アンワインド コード**|
  |-|-|
  |8 ~ 128 バイト|`UWOP_ALLOC_SMALL`|
  |136 を 512 K に 8 バイト|`UWOP_ALLOC_LARGE`、操作情報 = 0|
  |512 K に 4 G-8 バイト|`UWOP_ALLOC_LARGE`、操作情報 = 1|

- `UWOP_SET_FPREG` (3) 1 つのノード

  フレーム ポインター レジスタを確立するには、現在 RSP のオフセットをレジスタに設定します。 オフセットが UNWIND_INFO の登録のフレーム オフセット (スケール) フィールドに等しい\*16 の 240 の 0 からのオフセット。 オフセットの使用は、命令の短い形式を使用する複数のアクセスを許可することでコードの密度を支援する、固定のスタック割り当ての中央を指すフレーム ポインターの確立を許可します。 操作情報のフィールドは予約されており、使用する必要があります。

- `UWOP_SAVE_NONVOL` (4) 2 つのノード

  MOV を使用して、プッシュではなく、スタック上には、不揮発性の整数レジスタを保存します。 このコードは主に使用*シュリンク*、不揮発性レジスタが割り当てられていた位置でスタックに保存されています。 操作情報は、レジスタの数です。 次の 8 のスケールのスタックのオフセットが記録された上記の注で説明されているように、操作コードのスロットをアンワインドします。

- `UWOP_SAVE_NONVOL_FAR` (5) 3 つのノード

  プッシュではなく MOV を使用して、長いオフセットを使用してスタック上には、不揮発性の整数レジスタを保存します。 このコードは主に使用*シュリンク*、不揮発性レジスタが割り当てられていた位置でスタックに保存されています。 操作情報は、レジスタの数です。 スケールなしのスタックのオフセットが、次に、記録された上記の注で説明されている 2 つのアンワインド操作コードのスロット。

- `UWOP_SAVE_XMM128` (8) 2 つのノード

  スタック上には、不揮発性の XMM レジスタの 128 ビットすべてを保存します。 操作情報は、レジスタの数です。 16 のスケールのスタックのオフセットは、次のスロットに記録されます。

- `UWOP_SAVE_XMM128_FAR` (9) 3 つのノード

  時間のオフセットを使用してスタック上には、不揮発性の XMM レジスタの 128 ビットすべてを保存します。 操作情報は、レジスタの数です。 スケールなしのスタックのオフセットは、次の 2 つのスロットに記録されます。

- `UWOP_PUSH_MACHFRAME` (10) 1 つのノード

  マシンのフレームをプッシュします。  これは、ハードウェアの割り込みまたは例外の効果を記録に使用されます。 2 つの形式があります。 操作情報が 0 の場合、これらのフレームの 1 つは、スタックにプッシュされました。

  |||
  |-|-|
  |RSP + 32|SS|
  |RSP + 24|古い RSP|
  |RSP + 16|立てる|
  |RSP + 8|CS|
  |RSP|RIP|

  操作情報には、1 が達すると、し、これらのフレームのいずれかがプッシュされました。

  |||
  |-|-|
  |RSP + 40|SS|
  |RSP + 32|古い RSP|
  |RSP + 24|立てる|
  |RSP + 16|CS|
  |RSP + 8|RIP|
  |RSP|エラー コード|

  このアンワインド コードは、これが実際に実行されるが、代わりに、割り込みルーチンの実際のエントリ ポイントの前に表示され、マシン フレームのプッシュをシミュレートする場所を提供することのみが存在するダミーのプロローグで常に表示されます。 `UWOP_PUSH_MACHFRAME` 示す、マシンがこの操作を実行して概念的には、そのシミュレーションを記録します。

  1. RIP のリターン アドレスにスタックの一番上からのポップ*Temp*
  
  1. プッシュ SS

  1. 古い RSP をプッシュします。

  1. プッシュ立てる

  1. プッシュ CS

  1. プッシュ*Temp*

  1. (Op 情報では、1 と等しい) 場合は、エラー コードをプッシュします。

  シミュレートされた`UWOP_PUSH_MACHFRAME`40 操作デクリメント RSP (op 情報は、0 に等しい) または 48 (op 情報が 1 と等しくなります)。

#### <a name="operation-info"></a>操作情報

操作情報ビットの意味は、オペレーション コードに依存します。 汎用的な (整数) の登録をエンコードするには、このマッピングが使用されます。

|||
|-|-|
|0|RAX|
|1|RCX|
|2|RDX|
|3|RBX|
|4|RSP|
|5|RBP|
|6|RSI|
|7|RDI|
|8 ~ 15|R15 に R8|

### <a name="chained-unwind-info-structures"></a>チェーン アンワインド情報の構造

UNW_FLAG_CHAININFO フラグが設定されている場合、そのアンワインド情報構造体には、セカンダリの 1 つと、共有の例外のハンドラー/チェーン情報アドレス フィールドには、プライマリのアンワインド情報が含まれています。 このサンプル コードの取得、プライマリ アンワインド情報であると仮定して`unwindInfo`構造を持つ、UNW_FLAG_CHAININFO フラグが設定されます。

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

チェーン情報は、2 つの状況で役に立ちます。 まず、非連続のコード セグメントを使用できます。 チェーン情報を使用するには、プライマリ アンワインド情報からアンワインド コード配列を複製する必要はありませんので、必要なアンワインド情報のサイズを小さくことができます。

Volatile レジスタの保存をグループ化するのにチェーン情報を使用することもできます。 関数のエントリのプロローグの外になるまで、揮発性レジスタの保存、コンパイラが遅れる可能性があります。 グループ化されたコードの前に、関数の部分の情報をプライマリ アンワインドすることでこれを記録して、チェーンのプロローグのアンワインド コードが、不揮発性レジスタの保存を反映ゼロでないサイズの情報を設定します。 その場合は、アンワインド コードは、UWOP_SAVE_NONVOL のすべてのインスタンスです。 PUSH を使用して不揮発性レジスタを保存します。 または、追加の固定スタック割り当てを使用して、RSP レジスタを変更するグループ化がサポートされていません。

UNWIND_INFO を持つ項目が UNWIND_INFO 項目があります設定すると、UNW_FLAG_CHAININFO RUNTIME_FUNCTION エントリを含めることが UNW_FLAG_CHAININFO セットできますとも呼ばれる*複数シュリンク*します。 最終的には、チェーン アンワインド情報を持つクリア; UNW_FLAG_CHAININFO UNWIND_INFO 項目にポインターが到着これは、プライマリの UNWIND_INFO の項目は、実際の手順のエントリ ポイントを指します。

## <a name="unwind-procedure"></a>アンワインド プロシージャ

アンワインド コード配列は降順に並べ替えられます。 例外が発生する場合は、完全なコンテキストがコンテキスト レコードのオペレーティング システムによって格納されます。 例外ディスパッチ ロジックが呼び出され、例外ハンドラーを検索する次の手順を繰り返し実行します。

1. 現在の関数 (または関数部分では、連鎖 UNWIND_INFO エントリ) を記述する RUNTIME_FUNCTION テーブル エントリを検索するには、コンテキスト レコードに格納されている現在の RIP を使用します。

1. 関数テーブルのエントリが見つからない場合は、リーフ関数ではあり、RSP が戻りポインターを直接対処します。 [RSP] の戻りポインターが更新されたコンテキストに格納されている、シミュレートされた RSP が 8 ずつインクリメントされ、手順 1. が繰り返されます。

1. RIP が 3 つのリージョン内にあることができます関数テーブルのエントリが見つかった場合: エピローグ内)、b) では、プロローグ、または c) でコードを例外ハンドラーで対応することがあります。

   - 大文字と小文字の) かどうか、RIP に、エピローグ内にあるし、コントロールは、関数を離れることが必要があります、この関数は、この例外に関連付けられている例外ハンドラーも、呼び出し元関数のコンテキストを計算するエピローグの効果を続行する必要があります。 RIP エピローグ、RIP からコード ストリーム内にあるかどうかを調べるが調べられます。 コード ストリームを正規のエピローグの末尾の部分に一致させることができ、エピローグでは、エピローグの残りの部分がシミュレートされる、コンテキスト レコードがそれぞれの命令として更新が処理されます。 その後、手順 1. が繰り返されます。

   - 関数がケース b) コントロールはありませんが、RIP がプロローグ内にある場合、入力や必要があります、この関数は、この例外に関連付けられている例外ハンドラーを呼び出し元関数のコンテキストの計算にプロローグの効果を元に戻す必要があります。 RIP はプロローグ内では、取り込みには、関数の開始からの距離がプロローグのアンワインド情報でエンコードされたサイズに等しいまたはそれよりも小さい場合。 アンワインド コード配列の最初のエントリのオフセットで小さい関数の開始の RIP のオフセットと等しいかそれよりも、転送をスキャンして、アンワインド コード配列内のすべての残りの項目の効果を元に戻す、プロローグの効果がアンワインドされました。 手順 1 が繰り返されます。

   - ケース c)、RIP がプロローグまたはエピローグと、関数内にない場合は例外ハンドラー (が存在する UNW_FLAG_EHANDLER が設定されます)、し、言語固有のハンドラーが呼び出されます。 ハンドラーがそのデータをスキャンし、フィルターとして適切な関数を呼び出します。 言語固有ハンドラーには、例外が処理されたこと、または検索は、次回に続くを返すことができます。 アンワインドは、直接それも開始できます。

1. 言語固有のハンドラーが処理済みのステータスを返しますとしている場合、実行が継続元のコンテキスト レコードを使用します。

1. 言語固有のハンドラーがないか、ハンドラーは、"検索を続行する の状態を返しますの場合は、コンテキスト レコードが、呼び出し元の状態をアンワインドしてください。 これは、それぞれの効果を元に戻す、アンワインド コード配列要素のすべてを処理することによって実現されます。 手順 1 が繰り返されます。

チェーン アンワインド情報が含まれる、基本的な手順が実行されます。 唯一の違いには、配列の末尾に達すると、プロローグの効果をアンワインドするアンワインド コード配列をウォーク、しにリンクされている親のアンワインド情報と、そこで見つかった全体のアンワインド コード配列を走査します。 UNW_CHAINED_INFO フラグを設定しないアンワインド情報に到着するまでは引き続きこのリンクし、そのアンワインド コード配列をウォークし終了します。

最小限のアンワインド データは 8 バイトです。 これはのみ以下の場合、またはスタックの 128 バイトを割り当てられ、可能性がある 1 つの不揮発性レジスタを保存する関数を表します。 これは、チェーンのサイズでもないアンワインド コードを長さ 0 のプロローグのアンワインド情報。

## <a name="language-specific-handler"></a>言語固有のハンドラー

存在する UNW_FLAG_EHANDLER または UNW_FLAG_UHANDLER フラグが設定されるたびに、言語固有のハンドラーの相対アドレスは UNWIND_INFO 内に存在します。 前のセクションで説明した、またはアンワインドの一部として例外ハンドラーの検索の一部として、言語固有のハンドラーが呼び出されます。 このプロトタイプがあります。

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**ExceptionRecord** Win64 の標準の定義がある例外のレコードへのポインターを提供します。

**EstablisherFrame**のこの関数の固定のスタック割り当てのベース アドレスです。

**ContextRecord** (例外ハンドラーの例) では、例外が発生した時または現在の例外コンテキストへのポインター「アンワインド」(終了ハンドラーの場合) のコンテキスト。

**DispatcherContext**この関数のコンテキストをディスパッチャーを指します。 この定義があります。

```cpp
typedef struct _DISPATCHER_CONTEXT {
    ULONG64 ControlPc;
    ULONG64 ImageBase;
    PRUNTIME_FUNCTION FunctionEntry;
    ULONG64 EstablisherFrame;
    ULONG64 TargetIp;
    PCONTEXT ContextRecord;
    PEXCEPTION_ROUTINE LanguageHandler;
    PVOID HandlerData;
} DISPATCHER_CONTEXT, *PDISPATCHER_CONTEXT;
```

**ControlPc** RIP のこの関数内の値です。 この値は例外アドレスまたはアドレスのコントロールを確立する関数のままです。 コントロールが、この関数の内部でいくつかの保護されたコンス トラクターになどがあるか判断 RIP が使用される、`__try`ブロック`__try` / `__except`または`__try` /`__finally`します。

**ImageBase**イメージ ベース (の読み込みアドレス) の関数のエントリで使用される 32 ビット オフセットに追加して、アンワインド相対アドレスを記録する情報をこの関数を含むモジュールは、します。

**FunctionEntry** RUNTIME_FUNCTION へのポインターを提供しますが、関数を保持するエントリを関数をアンワインド情報イメージ ベースの相対アドレスはこの関数の。

**EstablisherFrame**のこの関数の固定のスタック割り当てのベース アドレスです。

**TargetIp**アンワインドの継続のアドレスを指定する省略可能な命令アドレスを提供します。 場合、このアドレスは無視されます**EstablisherFrame**が指定されていません。

**ContextRecord**システム例外ディスパッチ/アンワインド コードで使用するため、例外コンテキストを指しています。

**LanguageHandler**呼び出されている言語に固有の言語ハンドラー ルーチンを指します。

**HandlerData**この関数の言語固有のハンドラーのデータを指します。

## <a name="unwind-helpers-for-masm"></a>MASM のアンワインド ヘルパー

適切なアセンブリ ルーチンを記述するためには、一連の擬似演算と並行して実際のアセンブリ命令、適切な .pdata および .xdata を作成するのに使用できます。 その最も一般的な用途の擬似演算の使用を簡単に、一連のマクロを提供することもできます。

### <a name="raw-pseudo-operations"></a>生の擬似演算

|擬似演算|説明|
|-|-|
|PROC フレーム\[:*ehandler*]|原因関数を生成する MASM がテーブルでは、.pdata エントリと .xdata 内の情報を関数の構造化のアンワインドの例外処理のアンワインド動作します。  場合*ehandler*が存在する場合は、このプロシージャは、言語固有のハンドラーとして .xdata で入力します。<br /><br /> フレームの属性を使用する場合続けてする必要があります、します。ENDPROLOG ディレクティブです。  関数がリーフ関数の場合 (で定義されている[関数型](../build/stack-usage.md#function-types)) フレーム属性は必要に応じて、これらの擬似演算の残りの部分がありません。|
|.PUSHREG*登録*|現在のプロローグ内のオフセットを使用して指定のレジスタ番号の UWOP_PUSH_NONVOL アンワインド コードのエントリを生成します。<br /><br /> これは、不揮発性の整数レジスタでのみ使用する必要があります。  Volatile レジスタのプッシュを使用します。ALLOCSTACK 8 では、代わりに|
|.SETFRAME*登録*、*オフセット*|フレームの塗りつぶしは、指定されたレジスタおよびオフセットを使用して、アンワインド情報のフィールドとオフセットを登録します。 オフセットは 16 の倍数である必要があります、240 以下。 このディレクティブは、現在のプロローグのオフセットを使用して指定されたレジスタの UWOP_SET_FPREG アンワインド コードのエントリも生成されます。|
|.ALLOCSTACK*サイズ*|プロローグ内、UWOP_ALLOC_SMALL または現在のオフセットのサイズを指定して、UWOP_ALLOC_LARGE を生成します。<br /><br /> *サイズ*オペランドは 8 の倍数である必要があります。|
|.SAVEREG*登録*、*オフセット*|UWOP_SAVE_NONVOL、または指定されたレジスタとプロローグの現在のオフセットを使用してオフセット UWOP_SAVE_NONVOL_FAR アンワインド コードのエントリを生成します。 MASM では、最も効率的なエンコーディングを選択します。<br /><br /> *オフセット*、正の数値と 8 の倍数にする必要があります。 *オフセット*RSP で一般的には、プロシージャのフレームの底に対する相対パスですまたは、フレーム ポインターをスケールなしのフレーム ポインターを使用します。|
|.SAVEXMM128*登録*、*オフセット*|UWOP_SAVE_XMM128、または指定の XMM レジスタとプロローグの現在のオフセットを使用してオフセット UWOP_SAVE_XMM128_FAR アンワインド コードのエントリを生成します。 MASM では、最も効率的なエンコーディングを選択します。<br /><br /> *オフセット*、正の数値と 16 の倍数にする必要があります。  *オフセット*RSP で一般的には、プロシージャのフレームの底に対する相対パスですまたは、フレーム ポインターをスケールなしのフレーム ポインターを使用します。|
|.PUSHFRAME \[*コード*]|UWOP_PUSH_MACHFRAME アンワインド コードのエントリを生成します。 場合、省略可能な*コード*を指定すると、アンワインド コードのエントリが 1 の修飾子を指定します。 それ以外の場合、修飾子には 0 です。|
|.ENDPROLOG|プロローグの宣言の終了を通知します。  関数の最初の 255 バイト単位で発生する必要があります。|

ほとんどのオペコードの適切な使用方法をサンプル関数のプロローグを次に示します。

```MASM
sample PROC FRAME
    db      048h; emit a REX prefix, to enable hot-patching
    push rbp
    .pushreg rbp
    sub rsp, 040h
    .allocstack 040h
    lea rbp, [rsp+020h]
    .setframe rbp, 020h
    movdqa [rbp], xmm7
    .savexmm128 xmm7, 020h ;the offset is from the base of the frame
                           ;not the scaled offset of the frame
    mov [rbp+018h], rsi
    .savereg rsi, 038h
    mov [rsp+010h], rdi
    .savereg rdi, 010h ; you can still use RSP as the base of the frame
                       ; or any other register you choose
    .endprolog

; you can modify the stack pointer outside of the prologue (similar to alloca)
; because we have a frame pointer.
; if we didn’t have a frame pointer, this would be illegal
; if we didn’t make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren’t saved with a push
; this isn’t part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here’s the official epilog

    lea rsp, [rbp-020h]
    pop rbp
    ret
sample ENDP
```

### <a name="masm-macros"></a>MASM マクロ

使用を簡略化するため、[生の擬似演算](#raw-pseudo-operations)、一般的な手順のプロローグおよびエピローグを作成するために使用できる、ksamd64.inc で定義されている、マクロのセットがあります。

|マクロ|説明|
|-|-|
|alloc_stack(n)|N バイトのスタック フレームを割り当てます (を使用して`sub rsp, n`)、し、出力、適切なアンワインド情報 (.allocstack n)|
|save_reg *reg*、 *loc*|不揮発性レジスタを保存します。 *reg*スタック上で、RSP オフセット*loc*、し、出力、適切なアンワインド情報。 (.savereg reg、loc)|
|push_reg *reg*|不揮発性レジスタをプッシュ*reg*スタック上に出力して、適切なアンワインド情報。 (.pushreg reg)|
|rex_push_reg *reg*|2 バイトのプッシュを使用して、スタック上不揮発性レジスタを保存し、出力、適切なアンワインド情報 (.pushreg reg)、プッシュが、関数、関数がホット パッチ可能なことを確認する最初の命令の場合これを使用する必要があります。|
|save_xmm128 *reg*、 *loc*|不揮発性の XMM レジスタを保存します*reg*スタック上で、RSP オフセット*loc*、し、出力、適切なアンワインド情報 (.savexmm128 reg、loc)。|
|set_frame *reg*、*オフセット*|フレームの登録を設定*reg* 、RSP に +*オフセット*(を使用して、 `mov`、または`lea`)、し、出力、適切なアンワインド情報 (.set_frame reg、オフセット)|
|push_eflags|プッシュを立てる、`pushfq`命令、し、出力、適切なアンワインド情報 (.alloc_stack 8)|

次のマクロの適切な使用方法をサンプル関数プロローグに示します。

```MASM
SkFrame struct
    Fill    dq ?; fill to 8 mod 16
    SavedRdi dq ?; saved register RDI
    SavedRsi dq ?; saved register RSI
SkFrame ends

sampleFrame struct
    Filldq?; fill to 8 mod 16
    SavedRdidq?; Saved Register RDI
    SavedRsi  dq?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here’s the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>アンワインド C でのデータの定義

C アンワインド データの説明を次に示します。

```C
typedef enum _UNWIND_OP_CODES {
    UWOP_PUSH_NONVOL = 0, /* info == register number */
    UWOP_ALLOC_LARGE,     /* no info, alloc size in next 2 slots */
    UWOP_ALLOC_SMALL,     /* info == size of allocation / 8 - 1 */
    UWOP_SET_FPREG,       /* no info, FP = RSP + UNWIND_INFO.FPRegOffset*16 */
    UWOP_SAVE_NONVOL,     /* info == register number, offset in next slot */
    UWOP_SAVE_NONVOL_FAR, /* info == register number, offset in next 2 slots */
    UWOP_SAVE_XMM128 = 8, /* info == XMM reg number, offset in next slot */
    UWOP_SAVE_XMM128_FAR, /* info == XMM reg number, offset in next 2 slots */
    UWOP_PUSH_MACHFRAME   /* info == 0: no error-code, 1: error-code */
} UNWIND_CODE_OPS;

typedef union _UNWIND_CODE {
    struct {
        UBYTE CodeOffset;
        UBYTE UnwindOp : 4;
        UBYTE OpInfo   : 4;
    };
    USHORT FrameOffset;
} UNWIND_CODE, *PUNWIND_CODE;

#define UNW_FLAG_EHANDLER  0x01
#define UNW_FLAG_UHANDLER  0x02
#define UNW_FLAG_CHAININFO 0x04

typedef struct _UNWIND_INFO {
    UBYTE Version       : 3;
    UBYTE Flags         : 5;
    UBYTE SizeOfProlog;
    UBYTE CountOfCodes;
    UBYTE FrameRegister : 4;
    UBYTE FrameOffset   : 4;
    UNWIND_CODE UnwindCode[1];
/*  UNWIND_CODE MoreUnwindCode[((CountOfCodes + 1) & ~1) - 1];
*   union {
*       OPTIONAL ULONG ExceptionHandler;
*       OPTIONAL ULONG FunctionEntry;
*   };
*   OPTIONAL ULONG ExceptionData[]; */
} UNWIND_INFO, *PUNWIND_INFO;

typedef struct _RUNTIME_FUNCTION {
    ULONG BeginAddress;
    ULONG EndAddress;
    ULONG UnwindData;
} RUNTIME_FUNCTION, *PRUNTIME_FUNCTION;

#define GetUnwindCodeEntry(info, index) \
    ((info)->UnwindCode[index])

#define GetLanguageSpecificDataPtr(info) \
    ((PVOID)&GetUnwindCodeEntry((info),((info)->CountOfCodes + 1) & ~1))

#define GetExceptionHandler(base, info) \
    ((PEXCEPTION_HANDLER)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetChainedFunctionEntry(base, info) \
    ((PRUNTIME_FUNCTION)((base) + *(PULONG)GetLanguageSpecificDataPtr(info)))

#define GetExceptionDataPtr(info) \
    ((PVOID)((PULONG)GetLanguageSpecificData(info) + 1)
```

## <a name="see-also"></a>関連項目

[x64 ソフトウェア規約](../build/x64-software-conventions.md)