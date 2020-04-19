---
title: x64 での例外処理
ms.date: 10/14/2019
helpviewer_keywords:
- C++ exception handling, x64
- exception handling, x64
ms.assetid: 41fecd2d-3717-4643-b21c-65dcd2f18c93
ms.openlocfilehash: eff4f1a22512b597b5479dbcaabcc9d5fc93c940
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303198"
---
# <a name="x64-exception-handling"></a>x64 での例外処理

構造化例外処理とC++ 、x64 における例外処理のコーディング規則および動作の概要を説明します。 例外処理に関する一般的な情報については、「 [Visual C++での例外処理](../cpp/exception-handling-in-visual-cpp.md)」を参照してください。

## <a name="unwind-data-for-exception-handling-debugger-support"></a>例外処理、デバッガーサポートのためのアンワインドデータ

例外処理とデバッグのサポートには、いくつかのデータ構造が必要です。

### <a name="struct-runtime_function"></a>構造体 RUNTIME_FUNCTION

テーブルベースの例外処理では、スタック領域を割り当てたり、別の関数 (非リーフ関数など) を呼び出したりするすべての関数に対して、テーブルエントリが必要になります。 関数テーブルのエントリの形式は次のとおりです。

|||
|-|-|
|ULONG|関数の開始アドレス|
|ULONG|関数の終了アドレス|
|ULONG|アンワインド情報のアドレス|

RUNTIME_FUNCTION 構造体は、メモリに DWORD で配置する必要があります。 すべてのアドレスは画像に関連しています。つまり、関数テーブルエントリを含むイメージの開始アドレスからの32ビットオフセットです。 これらのエントリは並べ替えられ、PE32 + イメージの pdata セクションに配置されます。 動的に生成される関数 [JIT コンパイラ] の場合、これらの関数をサポートするランタイムでは、RtlInstallFunctionTableCallback または RtlAddFunctionTable を使用して、この情報をオペレーティングシステムに提供する必要があります。 この操作を行わないと、プロセスの例外処理とデバッグが不安定になります。

### <a name="struct-unwind_info"></a>構造体 UNWIND_INFO

アンワインドデータ情報構造体は、関数がスタックポインターに与える影響、および不揮発性レジスタがスタックに保存される場所を記録するために使用されます。

|||
|-|-|
|UBYTE: 3|バージョン|
|UBYTE: 5|フラグ|
|UBYTE|プロローグのサイズ|
|UBYTE|アンワインドコードの数|
|UBYTE: 4|フレームレジスタ|
|UBYTE: 4|フレームレジスタオフセット (スケーリング)|
|USHORT \* n|アンワインドコード配列|
|variable|の形式 (1) または (2) のいずれかを指定できます。|

(1) 例外ハンドラー

|||
|-|-|
|ULONG|例外ハンドラーのアドレス|
|variable|言語固有のハンドラーデータ (省略可能)|

(2) チェーンアンワインド情報

|||
|-|-|
|ULONG|関数の開始アドレス|
|ULONG|関数の終了アドレス|
|ULONG|アンワインド情報のアドレス|

UNWIND_INFO 構造体は、メモリに DWORD で配置する必要があります。 各フィールドの意味は次のとおりです。

- **バージョン**

   アンワインドデータのバージョン番号 (現在は 1)。

- **フラグ**

   現在、次の3つのフラグが定義されています。

   |フラグ|説明|
   |-|-|
   |`UNW_FLAG_EHANDLER`| 関数には、例外を調べる必要がある関数を検索するときに呼び出す必要がある例外ハンドラーがあります。|
   |`UNW_FLAG_UHANDLER`| 関数には、例外のアンワインド時に呼び出される必要がある終了ハンドラーがあります。|
   |`UNW_FLAG_CHAININFO`| このアンワインド情報の構造は、プロシージャのプライマリではありません。 代わりに、チェーンアンワインド情報のエントリは、前の RUNTIME_FUNCTION エントリの内容です。 詳細については、「[チェーンアンワインド情報の構造](#chained-unwind-info-structures)」を参照してください。 このフラグが設定されている場合は、UNW_FLAG_EHANDLER と UNW_FLAG_UHANDLER のフラグをクリアする必要があります。 また、フレームレジスタと固定スタック割り当てのフィールドには、プライマリアンワインド情報と同じ値を指定する必要があります。|

- **プロローグのサイズ**

   関数プロローグの長さ (バイト単位)。

- **アンワインドコードの数**

   アンワインドコード配列内のスロットの数。 たとえば、UWOP_SAVE_NONVOL のアンワインドコードには、配列に複数のスロットが必要です。

- **フレームレジスタ**

   0以外の場合、関数はフレームポインター (FP) を使用します。このフィールドは、UNWIND_CODE ノードの [操作情報] フィールドと同じエンコーディングを使用して、フレームポインターとして使用される不揮発性レジスタの番号です。

- **フレームレジスタオフセット (スケーリング)**

   [フレームレジスタ] フィールドが0以外の場合、このフィールドは、設定時に FP レジスタに適用される RSP からのスケールされたオフセットです。 実際の FP レジスタは RSP + 16 \* この数値に設定され、0 ~ 240 のオフセットが許可されます。 このオフセットにより、FP レジスタを動的スタックフレームのローカルスタック割り当ての途中にポイントすることが許可されます。これにより、短い指示でコード密度を向上させることができます。 (つまり、詳細な命令では、8ビット符号付きオフセット形式を使用できます)。

- **アンワインドコード配列**

   不揮発性レジスタと RSP に対するプロローグの効果を説明する項目の配列。 個々の項目の意味については、UNWIND_CODE に関するセクションを参照してください。 アラインメントのために、この配列には常に偶数のエントリが含まれ、最後のエントリは使用されない可能性があります。 この場合、配列は [アンワインドコードの数] フィールドで示されている長さを超えています。

- **例外ハンドラーのアドレス**

   関数の言語固有の例外または終了ハンドラーへのイメージ相対ポインター。フラグ UNW_FLAG_CHAININFO がクリアされていて、フラグ UNW_FLAG_EHANDLER または UNW_FLAG_UHANDLER が設定されている場合。

- **言語固有のハンドラーデータ**

   関数の言語固有の例外ハンドラーデータ。 このデータの形式は指定されていません。使用中の特定の例外ハンドラーによって完全に決まります。

- **チェーンアンワインド情報**

   フラグ UNW_FLAG_CHAININFO が設定されている場合、UNWIND_INFO 構造は3つの UWORDs で終了します。  これらの UWORDs は、チェーンアンワインドの関数の RUNTIME_FUNCTION 情報を表します。

### <a name="struct-unwind_code"></a>構造体 UNWIND_CODE

アンワインドコード配列は、不揮発性レジスタおよび RSP に影響を与えるプロローグ内の操作のシーケンスを記録するために使用されます。 各コード項目の形式は次のとおりです。

|||
|-|-|
|UBYTE|プロローグ内のオフセット|
|UBYTE: 4|アンワインド操作コード|
|UBYTE: 4|操作情報|

配列は、プロローグ内のオフセットの降順で並べ替えられます。

#### <a name="offset-in-prolog"></a>プロローグ内のオフセット

この操作を実行する命令の末尾のオフセット (プロローグの先頭からのオフセット) と 1 (つまり、次の命令の開始のオフセット)。

#### <a name="unwind-operation-code"></a>アンワインド操作コード

注: 一部の操作コードでは、ローカルスタックフレームの値への符号なしオフセットが必要です。 このオフセットは、先頭からのオフセット (つまり、固定スタック割り当ての最下位アドレス) です。 UNWIND_INFO のフレームレジスタフィールドが0の場合、このオフセットは RSP からのオフセットです。 フレームレジスタフィールドが0以外の場合、このオフセットは、FP レジスタが確立されたときに RSP が配置された場所からのものです。 これは FP レジスタと FP レジスタオフセット (16 \*、UNWIND_INFO 内のスケーリングされたフレームレジスタオフセット) を引いた値と等しくなります。 FP レジスタが使用されている場合、オフセットを取得するアンワインドコードは、プロローグで FP レジスタが確立された後にのみ使用する必要があります。

`UWOP_SAVE_XMM128` と `UWOP_SAVE_XMM128_FAR`を除くすべてのオペコードでは、対象のすべてのスタック値は8バイトの境界に格納されるため、オフセットは常に8の倍数になります (スタック自体は常に16バイトでアラインされます)。 短いオフセット (512K 未満) を受け取る操作コードの場合、このコードのノードの最後の USHORT は、オフセットを8で割った値を保持します。 長いオフセットを受け取る操作コード (512K < = オフセット < 4 GB) の場合、このコードの最後の2つの USHORT ノードにはオフセット (リトルエンディアン形式) が保持されます。

オペコード `UWOP_SAVE_XMM128` と `UWOP_SAVE_XMM128_FAR`の場合、すべての128ビット XMM 操作が16バイトのアラインメントされたメモリ上で行われる必要があるため、オフセットは常に16の倍数になります。 したがって、スケールファクターとして16を使用して `UWOP_SAVE_XMM128`、1M 未満のオフセットを許可します。

アンワインド操作コードは、次のいずれかの値になります。

- `UWOP_PUSH_NONVOL` (0) 1 ノード

  不揮発性整数レジスタをプッシュし、RSP を8にデクリメントします。 操作情報は、レジスタの番号です。 エピローグの制約があるため、アンワインドコード配列の最後に `UWOP_PUSH_NONVOL` アンワインドコードをプロローグ内に配置する必要があります。 この相対順序は、`UWOP_PUSH_MACHFRAME`を除く他のすべてのアンワインドコードに適用されます。

- `UWOP_ALLOC_LARGE` (1) 2 または3ノード

  大きなサイズの領域をスタックに割り当てます。 2つの形式があります。 操作情報が0の場合は、割り当てのサイズを8で割った値が次のスロットに記録され、最大 512 Kb の割り当てが可能になります。 操作情報が1の場合は、割り当てのサイズを縮小しないサイズが、次の2つのスロットのリトルエンディアン形式で記録され、最大 4 GB の割り当てが可能になります。

- `UWOP_ALLOC_SMALL` (2) 1 ノード

  サイズの小さい領域をスタックに割り当てます。 割り当てのサイズは、8 + 8 \* の操作情報フィールドで、8 ~ 128 バイトの割り当てが可能です。

  スタック割り当てのアンワインドコードでは、常に可能な限り短いエンコーディングを使用する必要があります。

  |**割り当てサイズ**|**アンワインドコード**|
  |-|-|
  |8 ~ 128 バイト|`UWOP_ALLOC_SMALL`|
  |136 ~ 512K-8 バイト|`UWOP_ALLOC_LARGE`、操作情報 = 0|
  |512K ~ 4G-8 バイト|`UWOP_ALLOC_LARGE`、操作情報 = 1|

- `UWOP_SET_FPREG` (3) 1 ノード

  現在の RSP のオフセットにレジスタを設定して、フレームポインターレジスタを確立します。 オフセットは、UNWIND_INFO \* 16 のフレームレジスタオフセット (スケール) フィールドと同じであり、0 ~ 240 のオフセットが許可されます。 オフセットを使用すると、固定スタック割り当ての途中を指すフレームポインターを確立できます。これにより、より多くのアクセス許可によって短い命令形式を使用できるようになるため、コードの密度が向上します。 操作情報フィールドは予約されているため、使用できません。

- `UWOP_SAVE_NONVOL` (4) 2 ノード

  プッシュではなく MOV を使用して、スタックに不揮発性整数レジスタを保存します。 このコードは主に、*圧縮の折り返し*に使用されます。この場合、不揮発性レジスタは、以前に割り当てられた位置にスタックに保存されます。 操作情報は、レジスタの番号です。 上のメモで説明したように、8番目のスタックオフセットは、次のアンワインド操作コードスロットに記録されます。

- `UWOP_SAVE_NONVOL_FAR` (5) 3 ノード

  PUSH の代わりに MOV を使用して、長いオフセットでスタックに不揮発性整数レジスタを保存します。 このコードは主に、*圧縮の折り返し*に使用されます。この場合、不揮発性レジスタは、以前に割り当てられた位置にスタックに保存されます。 操作情報は、レジスタの番号です。 スケールなしのスタックオフセットは、上のメモで説明したように、次の2つのアンワインド操作コードスロットに記録されます。

- `UWOP_SAVE_XMM128` (8) 2 ノード

  すべての128ビットの揮発性 XMM レジスタをスタックに保存します。 操作情報は、レジスタの番号です。 16のスタックオフセットは、次のスロットに記録されます。

- `UWOP_SAVE_XMM128_FAR` (9) 3 ノード

  長いオフセットを使用して、すべての128ビットの不揮発性 XMM レジスタをスタックに保存します。 操作情報は、レジスタの番号です。 スケールなしのスタックオフセットは、次の2つのスロットに記録されます。

- `UWOP_PUSH_MACHFRAME` (10) 1 ノード

  マシンフレームをプッシュします。  このアンワインドコードは、ハードウェアの割り込みまたは例外の影響を記録するために使用されます。 2つの形式があります。 操作情報が0の場合は、次のいずれかのフレームがスタックにプッシュされています。

  |||
  |-|-|
  |RSP+32|SS|
  |RSP + 24|古い RSP|
  |RSP + 16|EFLAGS|
  |RSP + 8|CS|
  |RSP|取り込ん|

  操作情報が1の場合は、次のいずれかのフレームがプッシュされています。

  |||
  |-|-|
  |RSP + 40|SS|
  |RSP+32|古い RSP|
  |RSP + 24|EFLAGS|
  |RSP + 16|CS|
  |RSP + 8|取り込ん|
  |RSP|エラー コード|

  このアンワインドコードは、実際には実行されないが、割り込みルーチンの実際のエントリポイントの前に存在するダミーのプロローグに常に表示され、コンピューターフレームのプッシュをシミュレートする場所を提供するためだけに存在します。 シミュレーションを `UWOP_PUSH_MACHFRAME` 記録します。これは、マシンが概念的にこの操作を実行したことを示します。

  1. スタックの先頭から*Temp*に戻りアドレスをポップします
  
  1. プッシュ SS

  1. 古い RSP をプッシュする

  1. EFLAGS をプッシュする

  1. プッシュ CS

  1. *一時*にプッシュ

  1. プッシュエラーコード (op 情報が1の場合)

  シミュレートされた `UWOP_PUSH_MACHFRAME` 操作では、40 (op info が 0) または 48 (op info が 1) によって RSP をデクリメントします。

#### <a name="operation-info"></a>操作情報

操作情報ビットの意味は、操作コードによって異なります。 汎用 (整数) レジスタをエンコードするために、このマッピングが使用されます。

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
|8 ~ 15|R8 から R15 へ|

### <a name="chained-unwind-info-structures"></a>チェーンアンワインド情報の構造

UNW_FLAG_CHAININFO フラグが設定されている場合、アンワインド情報の構造はセカンダリ1であり、[共有例外ハンドラー]/[連鎖的なアドレス] フィールドにはプライマリアンワインド情報が含まれます。 このサンプルコードでは、`unwindInfo` が UNW_FLAG_CHAININFO フラグが設定された構造であると仮定して、プライマリアンワインド情報を取得します。

```cpp
PRUNTIME_FUNCTION primaryUwindInfo = (PRUNTIME_FUNCTION)&(unwindInfo->UnwindCode[( unwindInfo->CountOfCodes + 1 ) & ~1]);
```

チェーンされた情報は、2つの状況で役に立ちます。 1つ目は、連続していないコードセグメントに使用できることです。 チェーンされた情報を使用することにより、アンワインドコード配列をプライマリアンワインド情報から複製する必要がなくなるため、必要なアンワインド情報のサイズを小さくすることができます。

また、チェーンされた情報を使用して、揮発性レジスタの保存をグループ化することもできます。 コンパイラは、関数エントリプロローグの外部になるまで、一部の揮発性レジスタの保存を遅らせている可能性があります。 これを記録するには、グループ化されたコードの前に関数の部分のプライマリアンワインド情報を設定してから、プロローグの0以外のサイズのチェーン情報を設定します。この場合、チェーンされている情報のアンワインドコードには、不揮発性レジスタの保存が反映されます。 その場合、アンワインドコードは、UWOP_SAVE_NONVOL のすべてのインスタンスです。 プッシュを使用して不揮発性レジスタを保存するグループは、追加の固定スタック割り当てを使用して RSP レジスタを変更することはサポートされていません。

UNW_FLAG_CHAININFO セットを持つ UNWIND_INFO 項目には、UNWIND_INFO 項目に UNW_FLAG_CHAININFO 設定されている RUNTIME_FUNCTION エントリを含めることができます (*複数の縮小折り返し*と呼ばれることもあります)。 最終的に、チェーンされたアンワインド情報ポインターは、UNW_FLAG_CHAININFO クリアされた UNWIND_INFO 項目に到達します。 この項目は、実際のプロシージャのエントリポイントを指すプライマリ UNWIND_INFO 項目です。

## <a name="unwind-procedure"></a>アンワインドプロシージャ

アンワインドコード配列は、降順に並べ替えられます。 例外が発生すると、コンテキストレコードにオペレーティングシステムによって完全なコンテキストが格納されます。 次に、例外ディスパッチロジックが呼び出され、これらの手順を繰り返し実行して例外ハンドラーを検索します。

1. コンテキストレコードに格納されている現在の RIP を使用して、現在の関数 (または、チェーン UNWIND_INFO エントリの関数部分) を説明する RUNTIME_FUNCTION テーブルエントリを検索します。

1. 関数テーブルのエントリが見つからない場合は、リーフ関数内にあり、RSP は戻りポインターを直接アドレスに返します。 [RSP] の戻りポインターは更新されたコンテキストに格納され、シミュレートされた RSP は8ずつインクリメントされ、手順1が繰り返されます。

1. 関数テーブルのエントリが見つかった場合、RIP は、プロローグ内のエピローグ、b) 内の3つの領域、または例外ハンドラーによって処理される可能性のあるコード内の c) 内に配置できます。

   - ケース a) RIP がエピローグ内にある場合は、コントロールがその関数を離れると、この例外に関連付けられている例外ハンドラーがこの関数に存在しない可能性があります。また、エピローグの効果は、呼び出し元関数のコンテキストを計算するために続行される必要があります。 RIP がエピローグ内にあるかどうかを判断するには、RIP の後のコードストリームを調べます。 このコードストリームを正当なエピローグの末尾部分と照合できる場合は、エピローグ内にあり、エピローグの残りの部分がシミュレートされ、各命令が処理されるたびにコンテキストレコードが更新されます。 この処理の後、手順 1. を繰り返します。

   - ケース b) RIP がプロローグ内にある場合、コントロールが関数に入力されていない場合は、この例外に関連付けられている例外ハンドラーをこの関数に対して実行することはできず、プロローグの効果を元に戻して呼び出し元関数のコンテキストを計算する必要があります。 関数から RIP までの距離がアンワインド情報でエンコードされたプロローグのサイズ以下の場合、RIP はプロローグ内にあります。 プロローグの効果は、アンワインドコード配列を前方にスキャンして、関数の開始からの RIP のオフセット以下のオフセットを持つ最初のエントリを走査し、アンワインドコード配列内の残りのすべての項目の効果を元に戻すことでアンワインドされます。 次に、手順 1. を繰り返します。

   - ケース c) RIP がプロローグまたはエピローグ内になく、関数に例外ハンドラーがある場合 (UNW_FLAG_EHANDLER が設定されている場合)、言語固有のハンドラーが呼び出されます。 ハンドラーはデータをスキャンし、必要に応じてフィルター関数を呼び出します。 言語固有のハンドラーは、例外が処理されたこと、または検索が続行されることを返すことができます。 また、アンワインドを直接開始することもできます。

1. 言語固有のハンドラーが処理済みの状態を返した場合、元のコンテキストレコードを使用して実行が継続されます。

1. 言語固有のハンドラーがない場合、またはハンドラーが "continue search" 状態を返した場合は、コンテキストレコードを呼び出し元の状態にアンワインドする必要があります。 これは、すべてのアンワインドコード配列要素を処理し、それぞれの効果を元に戻すことによって行われます。 次に、手順 1. を繰り返します。

チェーンアンワインド情報が関係している場合でも、これらの基本的な手順に従います。 唯一の違いは、アンワインドコード配列をウォークしてプロローグの効果をアンワインドする一方で、配列の末尾に到達すると、親アンワインド情報にリンクされ、その後で見つかったアンワインドコード配列全体が参照される点です。 このリンクは、UNW_CHAINED_INFO フラグを指定せずにアンワインド情報に到達するまで続行されます。その後、アンワインドコード配列のウォークが終了します。

アンワインドデータの最小セットは8バイトです。 これは、128バイトのスタック以下を割り当てただけで、場合によっては1つの不揮発性レジスタを保存した関数を表します。 アンワインドコードを使用しない長さ0のプロローグのチェーンアンワインド情報構造のサイズでもあります。

## <a name="language-specific-handler"></a>言語固有のハンドラー

言語固有のハンドラーの相対アドレスは、フラグ UNW_FLAG_EHANDLER または UNW_FLAG_UHANDLER が設定されるたびに UNWIND_INFO に存在します。 前のセクションで説明したように、言語固有のハンドラーは、例外ハンドラーの検索の一部として、またはアンワインドの一部として呼び出されます。 このプロトタイプは次のようになります。

```cpp
typedef EXCEPTION_DISPOSITION (*PEXCEPTION_ROUTINE) (
    IN PEXCEPTION_RECORD ExceptionRecord,
    IN ULONG64 EstablisherFrame,
    IN OUT PCONTEXT ContextRecord,
    IN OUT PDISPATCHER_CONTEXT DispatcherContext
);
```

**Exceptionrecord**は、標準の Win64 定義を持つ例外レコードへのポインターを提供します。

**EstablisherFrame**は、この関数の固定スタック割り当てのベースのアドレスです。

**Contextrecord**は、例外が発生した時点 (例外ハンドラーの場合) または現在の "アンワインド" コンテキスト (終了ハンドラーケースの場合) で、例外コンテキストをポイントします。

**DispatcherContext**は、この関数のディスパッチャーコンテキストをポイントします。 この定義は次のとおりです。

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

**Controlpc**は、この関数内の RIP の値です。 この値は、例外アドレス、またはコントロールが確立している関数の左側にあるアドレスのいずれかです。 RIP は、この関数内の保護されたコンストラクトの中にコントロールがあるかどうかを判断するために使用されます。たとえば、`__try`/`__except` または `__try`/`__finally`の `__try` ブロックなどです。

**ImageBase**は、この関数を含むモジュールのイメージベース (読み込みアドレス) です。この関数は、相対アドレスを記録するために、関数エントリおよびアンワインド情報で使用される32ビットオフセットに追加されます。

**Functionentry**は、この関数の関数とアンワインド情報のイメージベースの相対アドレスを保持する RUNTIME_FUNCTION 関数のエントリへのポインターを提供します。

**EstablisherFrame**は、この関数の固定スタック割り当てのベースのアドレスです。

**Targetip**アンワインドの継続アドレスを指定する省略可能な命令アドレスを提供します。 **EstablisherFrame**が指定されていない場合、このアドレスは無視されます。

**Contextrecord**は、システム例外のディスパッチ/アンワインドコードによって使用される例外コンテキストをポイントします。

言語**ハンドラー**は、呼び出される言語固有の言語ハンドラールーチンを指します。

この関数の言語固有のハンドラーデータへのデータポイントを**ハンドラ**します。

## <a name="unwind-helpers-for-masm"></a>MASM のアンワインドヘルパー

適切なアセンブリルーチンを記述するために、実際のアセンブリ命令と並行して使用できる一連の擬似操作を使用して、適切な .xdata を作成します。 また、最も一般的に使用される擬似操作を簡単に使用できるようにするマクロのセットもあります。

### <a name="raw-pseudo-operations"></a>生の擬似操作

|擬似操作|説明|
|-|-|
|PROC FRAME \[:*ehandler*]|MASM によって、関数の構造化例外処理アンワインドの動作について、.xdata 内の関数テーブルエントリが生成されます。  *Ehandler*が存在する場合、このプロシージャは言語固有のハンドラーとして .xdata に入力されます。<br /><br /> FRAME 属性を使用する場合は、の後にを指定する必要があります。ENDPROLOG ディレクティブ。  関数が ([関数型](../build/stack-usage.md#function-types)で定義されているように) リーフ関数の場合、これらの擬似演算の残りの部分と同様に、FRAME 属性は不要です。|
|.PUSHREG*レジスタ*|プロローグ内の現在のオフセットを使用して、指定したレジスタ番号に UWOP_PUSH_NONVOL アンワインドコードエントリを生成します。<br /><br /> 不揮発性整数レジスタでのみ使用してください。  Volatile レジスタのプッシュの場合は、を使用します。ALLOCSTACK 8、代わりに|
|.SETFRAME*レジスタ*、 *offset*|指定したレジスタとオフセットを使用して、アンワインド情報のフレームレジスタフィールドおよびオフセットを設定します。 オフセットは、16の倍数で240以下である必要があります。 また、このディレクティブは、現在のプロローグオフセットを使用して、指定されたレジスタの UWOP_SET_FPREG アンワインドコードエントリを生成します。|
|.ALLOCSTACK*サイズ*|プロローグ内の現在のオフセットに対して、指定したサイズの UWOP_ALLOC_SMALL または UWOP_ALLOC_LARGE を生成します。<br /><br /> *サイズ*オペランドは8の倍数である必要があります。|
|.SAVEREG *register*、 *offset*|現在のプロローグオフセットを使用して、指定したレジスタおよびオフセットの UWOP_SAVE_NONVOL または UWOP_SAVE_NONVOL_FAR アンワインドコードエントリを生成します。 MASM は、最も効率的なエンコードを選択します。<br /><br /> *オフセット*は正の整数で、8の倍数である必要があります。 *オフセット*は、プロシージャのフレームのベース (通常は RSP)、またはフレームポインターを使用している場合は、スケーリングされていないフレームポインターのベースに対して相対的です。|
|.SAVEXMM128 *register*、 *offset*|現在のプロローグオフセットを使用して、指定された XMM register および offset の UWOP_SAVE_XMM128 または UWOP_SAVE_XMM128_FAR アンワインドコードエントリを生成します。 MASM は、最も効率的なエンコードを選択します。<br /><br /> *オフセット*は正、16の倍数である必要があります。  *オフセット*は、プロシージャのフレームのベース (通常は RSP)、またはフレームポインターを使用している場合は、スケーリングされていないフレームポインターのベースに対して相対的です。|
|.PUSHFRAME \[*コード*]|アンワインドコードエントリ UWOP_PUSH_MACHFRAME を生成します。 省略可能な*コード*が指定されている場合、アンワインドコードのエントリには1という修飾子が与えられます。 それ以外の場合、修飾子は0です。|
|.ENDPROLOG|プロローグ宣言の終了を通知します。  は、関数の最初の255バイトで発生する必要があります。|

次に、ほとんどのオペコードを適切に使用する関数プロローグのサンプルを示します。

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
; if we didn't have a frame pointer, this would be illegal
; if we didn't make this modification,
; there would be no need for a frame pointer

    sub rsp, 060h

; we can unwind from the next AV because of the frame pointer

    mov rax, 0
    mov rax, [rax] ; AV!

; restore the registers that weren't saved with a push
; this isn't part of the official epilog, as described in section 2.5

    movdqa xmm7, [rbp]
    mov rsi, [rbp+018h]
    mov rdi, [rbp-010h]

; Here's the official epilog

    lea rsp, [rbp+020h] ; deallocate both fixed and dynamic portions of the frame
    pop rbp
    ret
sample ENDP
```

エピローグの例の詳細については、「 [x64 プロローグとエピローグ](prolog-and-epilog.md)の[エピローグコード](prolog-and-epilog.md#epilog-code)」を参照してください。

### <a name="masm-macros"></a>MASM マクロ

[生の擬似操作](#raw-pseudo-operations)の使用を簡略化するために、ksamd64 で定義されているマクロのセットがあります。このマクロを使用して、一般的なプロシージャプロローグとエピローグを作成できます。

|マクロ|説明|
|-|-|
|alloc_stack (n)|(`sub rsp, n`を使用して) n バイトのスタックフレームを割り当て、適切なアンワインド情報 (. allocstack n) を出力します。|
|save_reg *reg*、 *loc*|非揮発性レジスタ*reg*を RSP オフセット*loc*のスタックに保存し、適切なアンワインド情報を出力します。 (. savereg reg, loc)|
|push_reg *reg*|不揮発性レジスタ*reg*をスタックにプッシュし、適切なアンワインド情報を出力します。 (pushreg reg)|
|rex_push_reg *reg*|2バイトプッシュを使用してスタックに不揮発性レジスタを保存し、適切なアンワインド情報 (pushreg reg) を生成します。  関数がホットパッチ可能なであることを確認するために、プッシュが関数の最初の命令である場合は、このマクロを使用します。|
|save_xmm128 *reg*、 *loc*|RSP XMM register *reg*を RSP オフセット*loc*のスタックに保存し、適切なアンワインド情報 (. savexmm128 reg, loc) を出力します。|
|set_frame *reg*、 *offset*|フレームレジスタ*reg*を RSP + *offset* (`mov`または `lea`を使用) に設定し、適切なアンワインド情報 (. set_frame reg, offset) を出力します。|
|push_eflags|`pushfq` 命令と共に eflags をプッシュし、適切なアンワインド情報 (. alloc_stack 8) を出力します。|

マクロを適切に使用する関数プロローグの例を次に示します。

```MASM
sampleFrame struct
    Fill     dq ?; fill to 8 mod 16
    SavedRdi dq ?; Saved Register RDI
    SavedRsi dq ?; Saved Register RSI
sampleFrame ends

sample2 PROC FRAME
    alloc_stack(sizeof sampleFrame)
    save_reg rdi, sampleFrame.SavedRdi
    save_reg rsi, sampleFrame.SavedRsi
    .end_prolog

; function body

    mov rsi, sampleFrame.SavedRsi[rsp]
    mov rdi, sampleFrame.SavedRdi[rsp]

; Here's the official epilog

    add rsp, (sizeof sampleFrame)
    ret
sample2 ENDP
```

## <a name="unwind-data-definitions-in-c"></a>C でのアンワインドデータ定義

アンワインドデータの C の説明を次に示します。

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

## <a name="see-also"></a>参照

[x64 ソフトウェア規約](../build/x64-software-conventions.md)
