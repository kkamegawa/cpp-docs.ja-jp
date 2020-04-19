---
title: ソース ファイルとソース プログラム
ms.date: 11/04/2016
helpviewer_keywords:
- files [C++], source
- programs [C++], source
- source files, specifying in compiler
- source programs
ms.assetid: 18bb2826-17da-48e5-92a2-10e649f1bc9f
ms.openlocfilehash: 4562f8397e9d2d3e044086b8da8d56ba25047ebd
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152535"
---
# <a name="source-files-and-source-programs"></a>ソース ファイルとソース プログラム

ソース プログラムは、1 つ以上の "ソース ファイル" または "翻訳単位" に分割できます。 コンパイラへの入力は "翻訳単位" と呼ばれます。

## <a name="syntax"></a>構文

*translation-unit*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*external-declaration* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*translation-unit* *external-declaration*

*external-declaration*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*function-definition*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*

「[宣言の概要](../c-language/overview-of-declarations.md)」では、非終端要素である `declaration` の構文を示します。『*プリプロセッサ リファレンス*』では、[翻訳単位](../preprocessor/phases-of-translation.md)の処理方法について説明します。

> [!NOTE]
>  ANSI 構文規則については、「[C 言語の構文の概要](../c-language/c-language-syntax-summary.md)」の説明を参照してください。

翻訳単位の構成要素は、関数定義および識別子宣言を含む外部宣言です。 これらの宣言と定義は、ソース ファイル、ヘッダー ファイル、ライブラリなど、プログラムが必要とするファイルに含めることができます。 各翻訳単位をコンパイルし、結果のオブジェクト ファイルをリンクして、プログラムを作成する必要があります。

C の "ソース プログラム" は、ディレクティブ、プラグマ、宣言、定義、ステートメント ブロック、および関数のコレクションです。 Microsoft C プログラムの有効な構成要素であるためには、それぞれがこのブックで説明された構文に従う必要があります。ただし、プログラム内で登場する順序は任意です (このブック全体で示された規則に従います)。 ただし、これらの構成要素の場所は、変数と関数がプログラムでどのように使用されるかに影響します  (詳細については、「[有効期間、スコープ、可視性、およびリンケージ](../c-language/lifetime-scope-visibility-and-linkage.md)」を参照してください)。

ソース ファイルは、実行可能なステートメントを含む必要はありません。 たとえば、変数の定義を 1 つのソース ファイルに置き、これらの変数を使用する他のソース ファイルでこれらの変数への参照を宣言すると便利な場合があります。 この手法により、必要なときに簡単に定義を見つけて更新できるようになります。 同じ理由から、定数およびマクロは、ソース ファイルで必要に応じて参照できる "インクルード ファイル" または "ヘッダー ファイル" という名前の別個のファイルにまとめることがよくあります。 [マクロ](../preprocessor/macros-c-cpp.md)および[インクルード ファイル](../preprocessor/hash-include-directive-c-cpp.md)については、『*プリプロセッサ リファレンス*』の説明を参照してください。

## <a name="see-also"></a>関連項目

[プログラムの構造](../c-language/program-structure.md)
