---
title: ARM アセンブラー ディレクティブ
ms.date: 08/30/2018
ms.assetid: 9cfa8896-ec10-4e77-855a-3135c40d7d2a
ms.openlocfilehash: 9124f893b3334e0893073332c9d5f5a1388373d9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167674"
---
# <a name="arm-assembler-directives"></a>ARM アセンブラー ディレクティブ

ほとんどの場合、Microsoft ARM アセンブラーが記載されている ARM アセンブリ言語を使用して、 [ARM コンパイラ armasm リファレンス ガイド](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)します。 ただし、一部のアセンブリ ディレクティブの Microsoft 実装には、ARM アセンブリ ディレクティブによって異なります。 この記事では、相違点について説明します。

## <a name="microsoft-implementations-of-arm-assembly-directives"></a>Microsoft の実装の ARM アセンブリ ディレクティブ

- 領域

   これらをサポートする Microsoft ARM アセンブラー`AREA`属性: `ALIGN`、 `CODE`、 `CODEALIGN`、 `DATA`、 `NOINIT`、 `READONLY`、 `READWRITE`、 `THUMB`、`ARM`します。

   除くすべて`THUMB`と`ARM`に記載されている作業、 [ARM コンパイラ armasm リファレンス ガイド](http://infocenter.arm.com/help/topic/com.arm.doc.dui0802b/index.html)します。

   Microsoft ARM アセンブラー、`THUMB`ことを示します、`CODE`セクションが Thumb コードが含まれの既定値は、`CODE`セクション。  `ARM` ARM コードにはセクションが含まれていることを示します。

- ATTR

   サポートされていません。

- コード 16

   Microsoft ARM アセンブラーが許可されていない pre UAL Thumb 構文を使用すると、発生するので、サポートされていません。  使用して、`THUMB`代わりに、UAL 構文と共にディレクティブ。

- 一般的です

   一般的な領域の配置の仕様がサポートされていません。

- DCDO

   サポートされていません。

- `DN`、 `QN`、 `SN`

   型またはレジスタ エイリアスのレーンの仕様がサポートされていません。

- エントリ

   サポートされていません。

- EQU

   定義されているシンボルの型の仕様がサポートされていません。

- `EXPORT` および `GLOBAL`

   この構文を使用してエクスポートを指定します。

   > **EXPORT**|**GLOBAL** <em>sym</em>{ **[** <em>type</em> **]** }

   *sym*はエクスポートする記号です。  [*型*]、指定した場合いずれかになります`[DATA]`シンボル データをポイントすることを示すまたは`[FUNC]`をシンボルがコードを指していることを示します。 `GLOBAL` は `EXPORT`のシノニムです。

- EXPORTAS

   サポートされていません。

- フレーム

   サポートされていません。

- `FUNCTION` および `PROC`

   Assembly 構文は、カスタムの仕様をサポートしていますは、呼び出し元の保存と呼び出し先保存されるレジスタの一覧を表示して、プロシージャの呼び出し規約、Microsoft ARM アセンブラーは、構文を受け入れますが、レジスタの一覧を無視します。  アセンブラーによって生成されるデバッグ情報には、既定の呼び出し規約のみがサポートしています。

- `IMPORT` および `EXTERN`

   この構文を使用してインポートを指定します。

   > **IMPORT**|**EXTERN** *sym*{ **, WEAK***エイリアス*{ **, TYPE***t*}}

   *sym*をインポートするシンボルの名前を指定します。

   場合`WEAK`*エイリアス*が指定されていることを示します*sym*弱い外部です。 リンク時に、その定義が見つからないかどうかへの参照がすべてをバインドする代わりに*エイリアス*します。

   場合`TYPE` *t*が指定されると、 *t*解決するのには、リンカーを試みる必要がある方法を示します*sym*します。  これらの値の*t*が考えられます。

   |[値]|説明|
   |-|-|
   |1|ライブラリの検索を実行しない*sym*|
   |2|ライブラリの検索を実行*sym*|
   |3|*sym*の別名です*エイリアス*(既定値)|

   `EXTERN` シノニムです`IMPORT`ことを除いて、 *sym*への参照が現在のアセンブリである場合にのみをインポートします。

- MACRO

   マクロの条件コードを保持する変数の使用がサポートされていません。 既定の値はマクロのパラメーターがサポートされていません。

- NOFP

   サポートされていません。

- `OPT`、 `TTL`、 `SUBT`

   Microsoft ARM アセンブラーが番組表を生成しないため、サポートされていません。

- PRESERVE8

   サポートされていません。

- 再配置します。

   `RELOC n` 命令またはデータ定義ディレクティブしか従うことができます。 これは、シンボルがありません。"匿名"を再配置することができます。

- 必要です。

   サポートされていません。

- REQUIRE8

   サポートされていません。

- THUMBX

   Microsoft ARM アセンブラーは 2 ee のつまみの命令セットをサポートしていないためにサポートされていません。

## <a name="see-also"></a>関連項目

[ARM アセンブラーのコマンド ライン リファレンス](../../assembler/arm/arm-assembler-command-line-reference.md)<br/>
[ARM アセンブラー診断メッセージ](../../assembler/arm/arm-assembler-diagnostic-messages.md)<br/>
