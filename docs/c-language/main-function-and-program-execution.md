---
title: main 関数とプログラム実行
ms.date: 11/04/2016
helpviewer_keywords:
- program startup [C++]
- entry points, program
- main function, program execution
- startup code, main function
- main function
- programs [C++], terminating
ms.assetid: 5984f1bd-072d-4e06-8640-122fb1454401
ms.openlocfilehash: 28b0d826dc02376f952d3522f2f037eacd298b8e
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123943"
---
# <a name="main-function-and-program-execution"></a>main 関数とプログラム実行

すべての C プログラムには主要な (メイン) 関数があり、その名前は **main** である必要があります。 コードが Unicode プログラミング モデルに準拠する場合、**main** のワイド文字バージョンである **wmain** を使用できます。 **main** 関数は、プログラム実行の開始点として動作します。 通常は、プログラム内の他の関数への呼び出しを指示することによって、プログラムの実行を制御します。 プログラムは通常、**main** の最後に実行を停止しますが、さまざまな理由により、プログラムのその他の場所で終了する場合もあります。 特定のエラーが検出された場合などに、プログラムを強制的に終了することもできます。 そのためには、**exit** 関数を使用します。 [exit](../c-runtime-library/reference/exit-exit-exit.md) 関数の説明および使用例については、「*ランタイム ライブラリ リファレンス*」を参照してくださ。

## <a name="syntax"></a>構文

```
main( int argc, char *argv[ ], char *envp[ ] )
```

## <a name="remarks"></a>Remarks

ソース プログラム内の関数は、1 つ以上の特定のタスクを実行します。 **main** 関数は、これらの関数を呼び出して、それぞれのタスクを実行することができます。 **main** が別の関数を呼び出すときは、その関数の最初のステートメントから実行が開始されるように、その関数に実行制御を渡します。 関数は、`return` ステートメントが実行されたとき、または関数の終わりに達したときに、**main** に制御を戻します。

**main** も含めて、任意の関数を、パラメーターを持つように宣言できます。 "パラメーター" または "仮パラメーター" という用語は、関数に渡された値を受け取る識別子を指します。 パラメーターに引数を渡す方法については、「[パラメーター](../c-language/parameters.md)」を参照してください。 ある関数が別の関数を呼び出すとき、呼び出される関数は呼び出す関数からパラメーターの値を受け取ります。 これらの値は、"引数" と呼ばれます。 **main** には、コマンド ラインから引数を受け取れるように、次の形式を使用して仮パラメーターを宣言できます。

**main** 関数に情報を渡す場合、パラメーターの名前は従来から `argc` および `argv` になっていますが、C コンパイラでこれらの名前でなければならないとされているわけではありません。 `argc` と `argv` の型は、C 言語によって定義されています。 従来、**main** に 3 番目のパラメーターが 渡される場合、その名前は `envp` とされています。 このセクションで後から示す各例で、これら 3 つのパラメーターを使用してコマンド ライン引数にアクセスする方法を説明します。 以降のセクションでは、これらのパラメーターについて説明します。

**main** のワイド文字バージョンについては、「[wmain の使用](../c-language/using-wmain.md)」を参照してください。

## <a name="see-also"></a>関連項目

[main 関数とコマンドライン引数C++()](../cpp/main-function-command-line-args.md)\
[C コマンド ライン引数の解析](../c-language/parsing-c-command-line-arguments.md)
