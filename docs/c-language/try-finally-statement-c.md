---
title: try-finally ステートメント (C)
ms.date: 11/04/2016
helpviewer_keywords:
- try-finally keyword [C]
- __finally keyword [C], try-finally statement syntax
- __finally keyword [C]
- structured exception handling, try-finally
ms.assetid: 514400c1-c322-4bf3-9e48-3047240b8a82
ms.openlocfilehash: 82cc5ffa3f50196fc5f518b8bb5b2080ff14fd8d
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56151833"
---
# <a name="try-finally-statement-c"></a>try-finally ステートメント (C)

**Microsoft 固有の仕様**

`try-finally` ステートメントは C 言語に対する Microsoft の拡張機能であり、コードのブロックの実行が中断されたときに、アプリケーションがクリーンアップ コードの実行を保証できるようにします。 クリーンアップは、メモリを解放する、ファイルを閉じる、ファイル ハンドルを解放するなどのタスクで構成されます。 `try-finally` ステートメントは、ルーチンからの不完全な戻りが発生する可能性のあるエラーを複数の場所でチェックするルーチンに特に便利です。

*try-finally-statement*: **__try**  *compound-statement*

**__finally**  *compound-statement*

`__try` 句の後の複合ステートメントは、保護されたセクションです。 `__finally` 句の後の複合ステートメントは、終了ハンドラーです。 ハンドラーは、保護されたセクションが例外によって終了したか (異常終了)、標準的なフォール スルーで終了したか (正常終了) にかかわらず、保護されたセクションが終了したときに実行する一連の操作を指定します。

制御は、単純な順次実行 (フォール スルー) によって `__try` ステートメントに到達します。 制御が `__try` ステートメントに入ると、関連付けられたハンドラーがアクティブになります。 次のように実行されます。

1. 保護されたセクションが実行されます。

1. 終了ハンドラーが呼び出されます。

1. 終了ハンドラーが完了すると、`__finally` ステートメントの後から実行が続けられます。 保護されたセクションがどのように終了したか (保護された本体の外への `goto` ステートメントによってか、`return` ステートメントによってか、など) に関係なく、終了ハンドラーは、制御フローが保護されたセクションの外部に移動する前に実行されます。

`__leave` キーワードは、`try-finally` ステートメント ブロック内で有効です。 `__leave` の効果は、`try-finally` ブロックの末尾に移動することです。 終了ハンドラーはすぐに実行されます。 `goto` ステートメントを使用しても同じ結果が得られますが、`goto` ステートメントではスタックがアンワインドされます。 `__leave` ステートメントは、スタック アンワインドが関与しないため、より効率的です。

`try-finally` ステートメントを、`return` ステートメントまたは `longjmp` ランタイム関数を使用して終了すると、異常終了と見なされます。 `__try` ステートメントにジャンプして入ることはできませんが、このステートメントからジャンプして出ることはできます。 出発点から処理が向かう先までのアクティブなすべての `__finally` ステートメントを実行する必要があります。 これは、"ローカル アンワインド" と呼ばれます。

終了ハンドラーは、`try-finally` ステートメントの実行中にプロセスが中止された場合は呼び出されません。

> [!NOTE]
>  構造化例外処理は、C および C++ のソース ファイルに機能します。 ただし、特に C++ 用にデザインされたものではありません。 C++ 例外処理を使用して、コードの移植性を高めることができます。 また、C++ 例外処理メカニズムは、任意の型の例外を処理できるという点で、より柔軟です。

> [!NOTE]
>  C++ プログラムでは、構造化例外処理ではなく、C++ 例外処理を使用する必要があります。 詳細については、『*C++ 言語リファレンス*』の「[例外処理](../cpp/exception-handling-in-visual-cpp.md)」を参照してください。

[try-except ステートメント](../c-language/try-except-statement-c.md)の動作を確認するには、`try-finally` の例をご覧ください。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[try-finally ステートメント](../cpp/try-finally-statement.md)
