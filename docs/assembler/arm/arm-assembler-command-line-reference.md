---
title: ARM アセンブラーのコマンド ライン リファレンス
description: Microsoft ARM アセンブラーのコマンドラインオプションのリファレンスガイドです。
ms.date: 02/09/2020
ms.assetid: f7b89478-1ab5-4995-8cde-a805f0462c45
ms.openlocfilehash: a63273e8d21e7a28574ec79d62c15f29ee59cd50
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257380"
---
# <a name="arm-assembler-command-line-reference"></a>ARM アセンブラーのコマンド ライン リファレンス

この記事では、Microsoft ARM アセンブラーの**armasm**に関するコマンドライン情報について説明します。 **armasm**は、ARMv7 Thumb アセンブリ言語を Microsoft による共通オブジェクトファイル形式 (COFF) の実装にアセンブルします。 リンカーは、ARM アセンブラーと C コンパイラの両方によって生成された COFF コードオブジェクトをリンクできます。 また、ライブラリアンによって作成されたオブジェクトライブラリとリンクすることもできます。

## <a name="syntax"></a>構文

> **`armasm`** [*オプション*] *source_file* *object_file*\
> **`armasm`** [*オプション*] **`-o`** *object_file* *source_file*

### <a name="parameters"></a>パラメーター

*オプション*\
次のオプションの0個以上の組み合わせ。

- **`-errors`** *ファイル名*\
   エラーメッセージと警告メッセージを*ファイル名*にリダイレクトします。

- **`-i`** *ディレクトリ*[ **`;`** <em>dir</em>] \
   指定したディレクトリをインクルード検索パスに追加します。

- **`-predefine`** *ディレクティブ*\
   シンボルを事前に定義するには、SETA、SETL、または SETS ディレクティブを指定します。
   例: `armasm.exe -predefine "COUNT SETA 150" source.asm`\
   詳細については、 [ARM コンパイラ armasm リファレンスガイド](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)を参照してください。

- **`-nowarn`**\
   すべての警告メッセージを無効にします。

- **`-ignore`** *警告*\
   指定した警告を無効にします。 使用可能な値については、警告に関するセクションを参照してください。

- **`-help`**\
   コマンドラインヘルプメッセージを出力します。

- **`-machine`** *マシン*\
   PE ヘッダーに設定するコンピューターの種類を指定します。  *コンピューター*の使用可能な値: \
   **ARM**—コンピューターの種類を IMAGE_FILE_MACHINE_ARMNT に設定します。 このオプションは既定値です。
   **THUMB**: コンピューターの種類を IMAGE_FILE_MACHINE_THUMB に設定します。

- **`-oldit`**\
   ARMv7 の IT ブロックを生成します。  既定では、ARMv8 と互換性のある IT ブロックが生成されます。

- **`-via`** *ファイル名*\
   *Filename*から追加のコマンドライン引数を読み取ります。

- **`-16`**\
   ソースを16ビットの Thumb 命令としてアセンブルします。  これは既定のオプションです。

- **`-32`**\
   ソースを32ビット ARM 命令としてアセンブルします。

- **`-g`**\
   デバッグ情報を生成します。

- **`-errorReport:`** *オプション*\
   このオプションは非推奨とされます。 Windows Vista 以降では、エラー報告は[Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。

*source_file*\
ソース ファイルの名前。

*object_file*\
オブジェクト (出力) ファイルの名前。

## <a name="remarks"></a>コメント

次の例は、一般的なシナリオで armasm を使用する方法を示しています。 最初に、armasm を使用して、アセンブリ言語ソース (.asm) ファイルをオブジェクト (.obj) ファイルにビルドします。 次に、CL コマンドライン C コンパイラを使用してソース (.c) ファイルをコンパイルします。また、リンカーオプションを指定して、ARM オブジェクトファイルをリンクすることもできます。

```cmd
armasm myasmcode.asm -o myasmcode.obj
cl myccode.c /link myasmcode.obj
```

## <a name="see-also"></a>参照

[ARM アセンブラー診断メッセージ](../../assembler/arm/arm-assembler-diagnostic-messages.md)\
[ARM アセンブラーディレクティブ](../../assembler/arm/arm-assembler-directives.md)
