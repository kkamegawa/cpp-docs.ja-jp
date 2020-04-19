---
title: ハードウェア例外
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions [C++], hardware
- errors [C++], low-level
- errors [C++], hardware
- hardware exceptions [C++]
- low level errors
ms.assetid: 06ac6f01-a8cf-4426-bb12-1688315ae1cd
ms.openlocfilehash: 59b74f47cd86d94b50ab9213b3e517c2b08db696
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246547"
---
# <a name="hardware-exceptions"></a>ハードウェア例外

オペレーティング システムによって認識される標準例外のほとんどは、ハードウェア定義された例外です。 Windows はいくつかの低レベルのソフトウェア例外を認識しますが、それらは通常、オペレーティング システムで処理するのが適しています。

Windows は、異なるプロセッサのハードウェア エラーを、このセクションの例外コードにマップします。 場合によっては、プロセッサはこれらの例外のサブセットのみを生成します。 Windows は例外に関する情報を前処理して、適切な例外コードを発行します。

Windows で認識されるハードウェア例外を次の表にまとめました。

|例外コード|例外の原因|
|--------------------|------------------------|
|STATUS_ACCESS_VIOLATION|アクセスできないメモリ位置に対する読み取りまたは書き込み。|
|STATUS_BREAKPOINT|ハードウェア定義されたブレークポイントに遭遇しました。デバッガーでのみ使用します。|
|STATUS_DATATYPE_MISALIGNMENT|適切にアラインされていないアドレスにあるデータの読み取りまたは書き込み。たとえば、16 ビットのエンティティは 2 バイト境界上に配置する必要があります (Intel 80*x*86 プロセッサには適用されません。)|
|STATUS_FLOAT_DIVIDE_BY_ZERO|浮動小数点型の 0.0 による除算。|
|STATUS_FLOAT_OVERFLOW|浮動小数点型の正の値の指数の最大値を超えています。|
|STATUS_FLOAT_UNDERFLOW|浮動小数点型の負の値の指数の絶対値の最大値を超えています。|
|STATUS_FLOATING_RESEVERED_OPERAND|予約された浮動小数点形式を使用しています (形式の無効な使用)。|
|STATUS_ILLEGAL_INSTRUCTION|プロセッサで定義されていない命令コードの実行を試みています。|
|STATUS_PRIVILEGED_INSTRUCTION|現在のコンピューター モードでは、命令の実行が許可されていません。|
|STATUS_INTEGER_DIVIDE_BY_ZERO|整数型の 0 による除算。|
|STATUS_INTEGER_OVERFLOW|整数の範囲を超える演算を試みています。|
|STATUS_SINGLE_STEP|シングル ステップ モードで 1 つの命令を実行しています。デバッガーでのみ使用されます。|

前の表に示した多くの例外は、デバッガーやオペレーティング システムなどの低レベルのコードで処理されることが前提となっています。 整数と浮動小数点数のエラーを除き、コードでこれらのエラーを処理しないでください。 したがって、通常は例外処理フィルターを使用して例外を無視 (0 に評価) してください。 そうしないと、下位レベルのしくみで適切に対応できなくなります。 ただし、[終了ハンドラーを記述](../cpp/writing-a-termination-handler.md)することによって、これらの低レベルエラーの潜在的な影響に対して適切な予防措置を講じることができます。

## <a name="see-also"></a>参照

[例外ハンドラーの記述](../cpp/writing-an-exception-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)