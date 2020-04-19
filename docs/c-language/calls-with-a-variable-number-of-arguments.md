---
title: 可変個の引数を使用した呼び出し
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- arguments [C++], variable number of
- VARARGS.H
- ellipses (...), variable number of arguments
- STDARGS.H
- function calls, arguments
- '... ellipsis'
- function calls, variable number of arguments
ms.assetid: 8808fb26-4822-42f5-aba3-ac64b54e151b
ms.openlocfilehash: f358d0a6d9369aed27dc7e3efa1ce88fbacee343
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150117"
---
# <a name="calls-with-a-variable-number-of-arguments"></a>可変個の引数を使用した呼び出し

部分的なパラメーター リストは、コンマの後に 3 つのピリオドが続く省略記号表記 (**、...**) で終了させることができます。これによって、関数に渡される引数がまだあること、ただしこれ以上の情報は与えられないことを示すことができます。 型チェックは、このような引数に対しては実行されません。 1 個以上のパラメーターを省略記号表記の前に指定する必要があります。省略記号表記は、パラメーター リストの最後のトークンである必要があります。 省略記号表記がない場合、パラメーター リストで宣言されている型以外のパラメーターを受け取った関数の動作は未定義です。

可変個の引数で関数を呼び出すには、単に関数の呼び出しに任意の数の引数を指定します。 例は、C ランタイム ライブラリの `printf` 関数です。 関数呼び出しでは、パラメーター リストまたは引数の型のリストで宣言された型の名前ごとに、1 つの引数を含める必要があります。

関数呼び出しで指定されたすべての引数は、`__fastcall` 呼び出し規約を指定しない限り、スタックに配置されます。 関数のために宣言されたパラメーターの数により、いくつの引数がタスクから取得され、パラメーターに代入されるかが決定します。 スタックからの追加の引数の取得と、存在する引数の数の判断は、自分で行う必要があります。 STDARG.H ファイルには、可変数の引数を受け取る関数の引数にアクセスするための ANSI 形式マクロが含まれています。 また、VARARGS.H の XENIX- スタイルのマクロは引き続きサポートされます。

このサンプル宣言は、可変個の引数を受け取る関数用です。

```
int average( int first, ...);
```

## <a name="see-also"></a>関連項目

[関数呼び出し](../c-language/function-calls.md)
