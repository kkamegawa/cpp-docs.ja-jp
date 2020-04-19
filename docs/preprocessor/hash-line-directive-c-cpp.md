---
title: '#line ディレクティブ (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#line'
helpviewer_keywords:
- preprocessor, directives
- line directive (#line)
- '#line directive'
ms.assetid: 585c1dc4-5184-4f01-98f4-80c1909744d7
ms.openlocfilehash: 35bee779ebf059c20d4a46e27b5ad4cbfb3ce5f3
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220231"
---
# <a name="line-directive-cc"></a>#line ディレクティブ (C/C++)

**#line**ディレクティブ、コンパイラの内部に格納された行番号とファイル名を指定した行番号とファイル名に変更するプリプロセッサに指示します。

## <a name="syntax"></a>構文

> **#line** *digit-sequence* ["*filename*"]

## <a name="remarks"></a>Remarks

コンパイラは、行番号および省略可能なファイル名を使用して、コンパイル時に見つかったエラーを参照します。 通常、行番号は現在の入力行を参照し、ファイル名は現在の入力ファイルを参照します。 行番号は、各行が処理された後、インクリメントします。

*数字シーケンス*値には、任意の整数定数を指定できます。 マクロ置換はプリプロセス トークンで実行できますが、結果は正しい構文に評価される必要があります。 *ファイル名*は任意の文字の組み合わせにすることができ、二重引用符 (`" "`) で囲む必要があります。 *Filename*を省略した場合、以前のファイル名は変更されません。

ソース行番号とファイル名を変更するには、 **#line**ディレクティブを記述します。 変換プログラムでは、行番号とファイル名を使用して、定義`__FILE__`済み`__LINE__`のマクロとの値を決定します。 これらのマクロを使用して、説明的なエラー メッセージをプログラム テキストに挿入できます。 これらの定義済みマクロの詳細については、「[定義済みマクロ](../preprocessor/predefined-macros.md)」を参照してください。

マクロ`__FILE__`は、ファイル名が二重引用符 (`" "`) で囲まれた文字列に展開されます。

行番号とファイル名を変更すると、コンパイラでは以前の値が無視され、新しい値で処理が続行されます。 **#Line**ディレクティブは、通常、エラーメッセージが生成されたプログラムではなく元のソースファイルを参照するようにするために、プログラムジェネレーターによって使用されます。

次の例は、 **#line**と`__LINE__`マクロ`__FILE__`とマクロを示しています。

このステートメントでは、内部的に格納された行番号が151に設定され、ファイル名がコピー .c に変更されます。

```C
#line 151 "copy.c"
```

この例では、マクロ`ASSERT`は、定義済み`__LINE__`の`__FILE__`マクロとを使用して、指定されたアサーションが true でない場合にソースファイルに関するエラーメッセージを出力します。

```C
#define ASSERT(cond) if( !(cond) )\
{printf( "assertion error line %d, file(%s)\n", \
__LINE__, __FILE__ );}
```

## <a name="see-also"></a>関連項目

[プリプロセッサディレクティブ](../preprocessor/preprocessor-directives.md)
