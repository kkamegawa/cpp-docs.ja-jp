---
title: '#line ディレクティブ (C/C++)'
ms.date: 10/18/2017
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: e478d287af097081910d192e2ac0fbee6890bfa2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614761"
---
# <a name="line-directive-cc"></a>#line ディレクティブ (C/C++)

**#line**ディレクティブ、コンパイラの内部に格納された行番号とファイル名を指定した行番号とファイル名に変更するプリプロセッサに指示します。

## <a name="syntax"></a>構文

> **#line** *digit-sequence* ["*filename*"]

## <a name="remarks"></a>Remarks

コンパイラは、行番号および省略可能なファイル名を使用して、コンパイル時に見つかったエラーを参照します。 通常、行番号は現在の入力行を参照し、ファイル名は現在の入力ファイルを参照します。 行番号は、各行が処理された後、インクリメントします。

*数字シーケンス*値は、任意の整数定数を指定できます。 マクロ置換はプリプロセス トークンで実行できますが、結果は正しい構文に評価される必要があります。 *Filename*文字の組み合わせにすることができ、二重引用符で囲む必要があります (**""**)。 場合*filename*は省略すると、前のファイル名は変更されません。

ソース行番号とファイル名を変更するには記述することで、 **#line**ディレクティブ。 トランスレーターは、行番号とファイル名を使用して、定義済みマクロの値を決定する`__FILE__`と`__LINE__`します。 これらのマクロを使用して、説明的なエラー メッセージをプログラム テキストに挿入できます。 これらの定義済みマクロの詳細については、次を参照してください。[定義済みマクロ](../preprocessor/predefined-macros.md)します。

`__FILE__`マクロは、二重引用符で囲まれたファイル名で構成される文字列に展開されます (**""**)。

行番号とファイル名を変更すると、コンパイラでは以前の値が無視され、新しい値で処理が続行されます。 **#Line**通常そのディレクティブを使用プログラム ジェネレーターによって、生成されたプログラムの代わりに元のソース ファイルを参照してエラー メッセージが表示します。

次の例を示しています **#line**と`__LINE__`と`__FILE__`マクロ。

このステートメントでは、内部に格納された行番号は 151 に設定し、copy.c にファイル名を変更します。

```cpp
#line 151 "copy.c"
```

この例では、マクロで`ASSERT`定義済みマクロを使用して`__LINE__`と`__FILE__`特定のアサーションが true でない場合は、ソース ファイルに関するエラー メッセージを印刷します。

```cpp
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>関連項目

[プリプロセッサ ディレクティブ](../preprocessor/preprocessor-directives.md)
