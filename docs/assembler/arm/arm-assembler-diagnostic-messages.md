---
title: ARM アセンブラー診断メッセージ
ms.date: 08/30/2018
f1_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
helpviewer_keywords:
- A2193
- A2196
- A2202
- A2513
- A2557
- A4228
- A4508
- A4509
ms.assetid: 52b38267-6023-4bdc-a0ef-863362f48eec
ms.openlocfilehash: 72c1ea64501ef8104fee9bdf914a1464c07c3b76
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449216"
---
# <a name="arm-assembler-diagnostic-messages"></a>ARM アセンブラー診断メッセージ

Microsoft ARM アセンブラー (*armasm*) それらを見つけたときに、診断の警告とエラーを出力します。 この記事では、最もよく発生したメッセージについて説明します。

## <a name="syntax"></a>構文

> <em>ファイル名</em> **(** <em>行番号</em> **):** \[**エラー**|**警告**] **A**<em>数</em> **:** *メッセージ*

## <a name="diagnostic-messages---errors"></a>エラーの診断メッセージ

> この命令の A2193: は予期しない動作が生成されます。

ARM アーキテクチャでは、この命令が実行されるときの動作を保証できません。  詳細については、この命令の明確に定義されたフォームを参照してください、 [ARM アーキテクチャ リファレンス マニュアル](https://go.microsoft.com/fwlink/p/?linkid=246464)します。

```asm
    ADD r0, r8, pc         ; A2193: this instruction generates unpredictable behavior
```

> A2196: 命令は 16 ビットでエンコードすることはできません。

指定された命令は、16 ビットの Thumb 命令としてエンコードすることはできません。  16 ビット命令の範囲に先のラベルを表示するコードを再配置または 32 ビット命令を指定します。

アセンブラーしようと 16 ビット分岐をエンコードし、このエラーで失敗する場合でも、32 ビット分岐は encodable します。 この問題を解決するを使用して、`.W`指定子として 32 ビット分岐を明示的にマークします。

```asm
    ADD.N r0, r1, r2      ; A2196: instruction cannot be encoded in 16 bits

    B.W label             ; OK
    B.N label             ; A2196: instruction cannot be encoded in 16 bits
    SPACE 10000
label
```

> A2202:プレ UAL 命令の構文が THUMB のリージョンでは使用できません。

Thumb コードでは、Unified アセンブラー言語 (UAL) の構文を使用する必要があります。  古い構文は受け付けられません。

```asm
    ADDEQS r0, r1         ; A2202: Pre-UAL instruction syntax not allowed in THUMB region
    ADDSEQ r0, r1         ; OK
```

> A2513:回転は偶数になる必要があります。

ARM モードでは、定数を指定するための代替構文です。  書き込みではなく`#<const>`、書き込める`#<byte>,#<rot>`、回転値を取得する定数値を表す`<byte>`を右`<rot>`します。  この構文を使用する場合は、値を行う必要があります`<rot>`もします。

```asm
    MOV r0, #4, #2       ; OK
    MOV r0, #4, #1       ; A2513: Rotation must be even
```

> A2557:書き戻しのバイト数が正しくないです。

NEON 構造体に読み込みおよびストア (`VLDn`、 `VSTn`)、ベース レジスタへの書き戻しを指定するための代替の構文があります。  アドレスの後に感嘆符 (!) を実装することではなく基本登録に追加するオフセットを示すイミディ エイト値を指定できます。  この構文を使用する場合は、読み込まれたまたは命令によって格納されたバイト数の正確なを指定する必要があります。

```asm
    VLD1.8 {d0-d3}, [r0]!         ; OK
    VLD1.8 {d0-d3}, [r0], #32     ; OK
    VLD1.8 {d0-d3}, [r0], #100    ; A2557: Incorrect number of bytes to write back
```

## <a name="diagnostic-messages---warnings"></a>警告の診断メッセージ

> A4228:配置の値は、領域の配置を超えています。配置とは限りません

指定されている配置、`ALIGN`ディレクティブが、それを囲むの配置よりも大きい`AREA`します。  そのため、アセンブラーが保証ことはできませんが、`ALIGN`ディレクティブが受け入れられます。

これを解決するで指定することができます、`AREA`ディレクティブ、`ALIGN`目的の配置を示す属性です。

```asm
AREA |.myarea1|
ALIGN 8           ; A4228: Alignment value exceeds AREA alignment; alignment not guaranteed

AREA |.myarea2|,ALIGN=3
ALIGN 8           ; OK
```

> A4508:この回転定数の使用は非推奨します。

ARM モードでは、定数を指定するための代替構文です。  書き込みではなく`#<const>`、書き込める`#<byte>,#<rot>`、回転値を取得する定数値を表す`<byte>`を右`<rot>`します。  一部のコンテキストで ARM は回転したこれらの定数の使用非推奨とされます。 このような場合は、基本的なを使用して、`#<const>`構文代わりにします。

```asm
    ANDS r0, r0, #1                ; OK
    ANDS r0, r0, #4, #2            ; A4508: Use of this rotated constant is deprecated
```

> A4509:この形式の条件付き命令が非推奨とされます。

この形式の条件付き命令は ARMv8 アーキテクチャでは ARM で廃止されました。 条件付き分岐を使用するコードを変更することをお勧めします。 どの条件付き命令は引き続きサポートを表示するを参照してください、 [ARM アーキテクチャ リファレンス マニュアル](https://go.microsoft.com/fwlink/p/?linkid=246464)します。

この警告がないときに出力、 **- oldit**コマンド ライン スイッチを使用します。

```asm
    ADDEQ r0, r1, r8              ; A4509: This form of conditional instruction is deprecated
```

## <a name="see-also"></a>関連項目

[ARM アセンブラーのコマンド ライン リファレンス](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[ARM アセンブラー ディレクティブ](../../assembler/arm/arm-assembler-directives.md)<br/>
