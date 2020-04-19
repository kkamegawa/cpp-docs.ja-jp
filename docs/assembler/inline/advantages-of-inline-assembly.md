---
title: インライン アセンブラーの長所
ms.date: 08/30/2018
helpviewer_keywords:
- assembler [C++], advantages
- inline assembly [C++], about inline assembly
- inline assembly [C++], using
ms.assetid: 94364d97-faa7-4bdf-8473-570956986c51
ms.openlocfilehash: ecf1598ec90a8600e1fa9aae565724c254dc11e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62167401"
---
# <a name="advantages-of-inline-assembly"></a>インライン アセンブラーの長所

**Microsoft 固有の仕様**

インライン アセンブラーは別のアセンブリとリンクの手順を必要としないので、別のアセンブラーより便利です。 インライン アセンブラー コードでは、スコープ内にある C 変数や関数名を使用できるので、プログラムの C コードと簡単に統合できます。 アセンブリ コードが C または C++ ステートメントでインラインを混在させることができます、ため煩雑であるか、または C または C++ では不可能であるタスクを実行できます。

インライン アセンブリの使用は次のとおりです。

- アセンブリ言語で関数を記述します。

- コードの速度が重要なセクションをスポットを最適化します。

- デバイス ドライバーのハードウェアに直接アクセスを行います。

- 「ネイキッド」の呼び出しのプロローグおよびエピローグのコードを記述します。

インライン アセンブリは、特殊なツールです。 さまざまなマシンにアプリケーションを移植する場合は、別のモジュール内のコンピューターに固有のコードを配置するとする可能性があります。 インライン アセンブラーは、すべての Microsoft Macro Assembler の (MASM) をサポートしないため、マクロとデータ ディレクティブかもしれません MASM をこのようなモジュールを使用する方が便利です。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[インライン アセンブラー](../../assembler/inline/inline-assembler.md)<br/>