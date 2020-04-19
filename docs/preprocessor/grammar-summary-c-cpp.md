---
title: プリプロセッサの文法の概要C++(C/)
description: Microsoft C/C++コンパイラ (MSVC) プリプロセッサ文法構文を定義し、説明します。
ms.date: 08/29/2019
helpviewer_keywords:
- grammar
- preprocessor, grammar
ms.assetid: 0acb6e9b-364c-4ef8-ace4-7be980521121
ms.openlocfilehash: 99e7e8218a80e28d67767392cadfb5c4918a3bfe
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302186"
---
# <a name="preprocessor-grammar-summary-cc"></a>プリプロセッサの文法の概要C++(C/)

この記事では、C およびC++プリプロセッサの正式な文法について説明します。 プリプロセスディレクティブと演算子の構文について説明します。 詳細については、「[プリプロセッサ](../preprocessor/preprocessor.md)[ディレクティブとプラグマディレクティブ」と「__pragma キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)」を参照してください。

## <a name="definitions"></a>文法の概要の定義

終端は構文定義内のエンドポイントです。 他の解決はありません。 終端には、予約語およびユーザー定義の識別子が含まれます。

非終端は構文内のプレースホルダーです。 ほとんどは、この構文概要の他の場所で定義されています。 定義は再帰的に行うことができます。 次の非終端要素は、  *C++言語リファレンス*の[構文規則](../cpp/lexical-conventions.md)のセクションで定義されています。

*定数*、*定数式*、*識別子*、*キーワード*、*演算子*、*など*

省略可能な構成要素には添字 <sub>opt</sub> を付けます。 たとえば、次の構文は、中かっこで囲まれた省略可能な式を示しています。

**{** *expression*<sub>opt</sub> **}**

## <a name="conventions"></a>ドキュメントの表記規則

構文規則では、構文のコンポーネントごとに異なるフォント属性を使用します。 シンボルとフォントは次のとおりです。

| 属性 | 説明 |
|---------------|-----------------|
| *nonterminal* | 斜体は、非終端要素を示します。 |
| **#include** | 太字で示される終端要素は、示されたとおりに入力する必要があるリテラル予約語およびシンボルです。 このコンテキストの文字は、常に大文字と小文字が区別されます。 |
| <sub>opt</sub> | 後ろに <sub>opt</sub> が続く非終端要素は、常に省略可能です。|
| 既定のタイプフェイス | このタイプフェイスで記述されているか、示されているセット内の文字は、ステートメント内で終端要素として使用できます。 |

非終端要素に続くコロン ( **:** ) は、定義の説明を示します。 代替定義は別の行に示されます。

コード構文ブロックでは、既定のタイプフェイスのこれらのシンボルには特別な意味があります。

| [記号] | 説明 |
|---|---|
| \[ ] | 角かっこは、省略可能な要素を囲みます。 |
| {\|} | 中かっこは、縦棒で区切られた別の要素を囲みます。 |
| ... | 前の要素パターンを繰り返すことができることを示します。 |

コード構文ブロック、コンマ (`,`)、ピリオド (`.`)、セミコロン (`;`)、コロン (`:`)、かっこ (`( )`)、二重引用符 (`"`)、および単一引用符 (`'`) はリテラルです。

## <a name="grammar"></a>プリプロセッサの文法

*制御線*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *識別子* *トークン-文字列*<sub>選択</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#define** *識別子* **(** *識別子*<sub></sub> **の**選択... **,** *identifier*<sub>opt</sub> **)** *トークン文字列の*<sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **"** _パス仕様_ **"** \
&nbsp;&nbsp;&nbsp;&nbsp; **#include** **\<** _パス仕様_ **>** \
&nbsp;&nbsp;&nbsp;&nbsp; **#line** *digit-シーケンス* **"** _filename_ **"** <sub>opt</sub>\
&nbsp;&nbsp;&nbsp;&nbsp; **#undef** *識別子*\
&nbsp;&nbsp;&nbsp;&nbsp; **#error** *トークン-文字列*\
&nbsp;&nbsp;&nbsp;&nbsp; **#pragma** *token-string*

*定数式*: \
&nbsp;&nbsp;&nbsp;&nbsp;**定義されている (** *識別子* **)** \
&nbsp;&nbsp;&nbsp;&nbsp;**定義された***識別子*\
他の定数式 &nbsp;&nbsp;&nbsp;&nbsp;

*条件*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if-部分* *elif-部分*<sub>選択</sub>*else-パート*<sub>選択</sub>*endif-行*

*if-part*: \
&nbsp;&nbsp;&nbsp;&nbsp;*if 行* *テキスト*

*改行*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#if** *定数式*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifdef** *識別子*\
&nbsp;&nbsp;&nbsp;&nbsp; **#ifndef** *identifier*

*elif-parts*: \
&nbsp;&nbsp;&nbsp;&nbsp;*elif 行の* *テキスト*\
&nbsp;&nbsp;&nbsp;&nbsp;*elif パーツ* *elif 行* *テキスト*

*elif 行*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#elif** *constant-expression*

*else-パート*: \
&nbsp;&nbsp;&nbsp;&nbsp;その*他の行の* *テキスト*

*他の行*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#else**

*endif-行*: \
&nbsp;&nbsp;&nbsp;&nbsp; **#endif**

*数字-シーケンス*: \
&nbsp;&nbsp;&nbsp;&nbsp;*数字*\
&nbsp;&nbsp;&nbsp;&nbsp;*桁の* *数字*

*digit*: 次のいずれか \
&nbsp;&nbsp;&nbsp;&nbsp;**0 1 2 3 4 5 6 7 8 9**

*トークン文字列*: \
&nbsp;&nbsp;&nbsp;&nbsp;トークンの文字列

*トークン*: \
&nbsp;&nbsp;&nbsp;&nbsp;*キーワード*\
&nbsp;&nbsp;&nbsp;&nbsp;*識別子*\
&nbsp;&nbsp;&nbsp;&nbsp;*定数*\
&nbsp;&nbsp;&nbsp;&nbsp;*演算子*\
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*ファイル名*: \
&nbsp;&nbsp;&nbsp;&nbsp;有効なオペレーティングシステムファイル名

*パスの仕様*: \
&nbsp;&nbsp;&nbsp;&nbsp;有効なファイル パス

*テキスト*: \
任意のテキストシーケンス &nbsp;&nbsp;&nbsp;を &nbsp;する

> [!NOTE]
> 次の非終端要素は、  *C++言語リファレンス*の[構文表記規則](../cpp/lexical-conventions.md)(*定数*、*定数式*、*識別子*、*キーワード*、*演算子*、および*など*) で拡張されています。


## <a name="see-also"></a>関連項目

[C/C++プリプロセッサリファレンス](../preprocessor/c-cpp-preprocessor-reference.md)
