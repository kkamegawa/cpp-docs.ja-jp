---
title: try-except ステートメント (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-except keyword [C]
- structured exception handling, try-except
- try-catch keyword [C]
- __try keyword [C]
- __except keyword [C]
- __except keyword [C], in try-except
- try-catch keyword [C], try-except keyword [C]
ms.assetid: f76db9d1-fc78-417f-b71f-18e545fc01c3
ms.openlocfilehash: 9940fdf983f6141c0de207509bb800533b0f1eb8
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152327"
---
# <a name="try-except-statement-c"></a>try-except ステートメント (C)

**Microsoft 固有の仕様**

**try-except** ステートメントは、C 言語に対する Microsoft の拡張機能であり、正常に実行を終了するイベントが発生したときに、アプリケーションがプログラムの制御を取得できるようにします。 このようなイベントは例外と呼ばれ、例外を処理する機構は構造化例外処理と呼ばれます。

例外は、ハードウェアベースまたはソフトウェアベースです。 アプリケーションがハードウェア例外またはソフトウェア例外から完全に回復できない場合でも、構造化例外処理はエラー情報を表示し、問題の診断に役立つアプリケーションの内部状態をトラップすることができます。 これは、簡単に再現できない断続的な問題の場合に特に便利です。

## <a name="syntax"></a>構文

*try-except-statement*: **__try**  *compound-statement*

**__except (**  *expression*  **)**  *compound-statement*

`__try` 句の後の複合ステートメントは、保護されたセクションです。 `__except` 句の後の複合ステートメントは、例外ハンドラーです。 ハンドラーは、保護されたセクションの実行中に例外が発生した場合に行われる一連の操作を指定します。 次のように実行されます。

1. 保護されたセクションが実行されます。

1. 保護されたセクションの実行中に例外が発生しなかった場合、実行は `__except` 句の後のステートメントから続行されます。

1. 保護されたセクションの実行中または保護されたセクションで呼び出された任意のルーチンで例外が発生した場合、`__except` 式が評価され、返された値で例外の処理方法が決定されます。 次の 3 つの値があります。

   `EXCEPTION_CONTINUE_SEARCH` 例外は認識されていません。 最初に **try-except** ステートメントを含むハンドラーを検索してから、次に優先順位が最も高いハンドラーについてスタックを検索し続けます。

   `EXCEPTION_CONTINUE_EXECUTION` 例外が認識されましたが、破棄されました。 例外が発生した位置から実行を継続します。

   `EXCEPTION_EXECUTE_HANDLER` 例外が認識されました。 `__except` 複合ステートメントの実行によって例外ハンドラーに制御を移動した後、例外が発生した時点から実行を続行します。

`__except` 式は C の式として評価されるため、1 つの値、条件式の演算子、またはコンマ演算子に制限されます。 より広範な処理が必要な場合、前に挙げた 3 つの値の 1 つを返すルーチンを式で呼び出すことができます。

> [!NOTE]
>  構造化例外処理は、C および C++ のソース ファイルに機能します。 ただし、特に C++ 用にデザインされたものではありません。 C++ 例外処理を使用して、コードの移植性を高めることができます。 また、C++ 例外処理メカニズムは、任意の型の例外を処理できるという点で、より柔軟です。

> [!NOTE]
>  C++ プログラムでは、構造化例外処理ではなく、C++ 例外処理を使用する必要があります。 詳細については、『*C++ 言語リファレンス*』の「[例外処理](../cpp/exception-handling-in-visual-cpp.md)」を参照してください。

アプリケーションの各ルーチンには、それぞれ独自の例外ハンドラーがある場合があります。 `__except` 式は、`__try` 本体のスコープ内で実行されます。 これは、そこで宣言された任意のローカル変数にアクセスできることを意味します。

`__leave` キーワードは、**try-except** ステートメント ブロック内で有効です。 `__leave` の効果は、**try-except** ブロックの末尾に移動することです。 実行は、例外ハンドラーの終了後に再開します。 `goto` ステートメントを使用しても同じ結果が得られますが、`goto` ステートメントではスタックがアンワインドされます。 `__leave` ステートメントは、スタック アンワインドが関与しないため、より効率的です。

**try-except** ステートメントを `longjmp` ランタイム関数を使用して終了すると、異常終了と見なされます。 `__try` ステートメントにジャンプして入ることはできませんが、このステートメントからジャンプして出ることはできます。 例外ハンドラーは、プロセスが **try-except** ステートメントの実行中に中止された場合は呼び出されません。

## <a name="example"></a>例

例外ハンドラーと終了ハンドラーの例を次に示します。 終了ハンドラーの詳細については、「[try-finally ステートメント](../c-language/try-finally-statement-c.md)」を参照してください。

```
.
.
.
puts("hello");
__try{
   puts("in try");
   __try{
      puts("in try");
      RAISE_AN_EXCEPTION();
   }__finally{
      puts("in finally");
   }
}__except( puts("in filter"), EXCEPTION_EXECUTE_HANDLER ){
   puts("in except");
}
puts("world");
```

これは、例からの出力です。右側にコメントが追加されています。

```
hello
in try              /* fall into try                     */
in try              /* fall into nested try                */
in filter           /* execute filter; returns 1 so accept  */
in finally          /* unwind nested finally                */
in except           /* transfer control to selected handler */
world               /* flow out of handler                  */
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[try-except ステートメント](../cpp/try-except-statement.md)
