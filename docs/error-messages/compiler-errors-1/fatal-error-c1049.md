---
title: 致命的なエラー C1049
description: コンパイラの致命的なエラー C1049、無効な数値引数、およびその解決方法について説明します。
ms.date: 11/04/2019
f1_keywords:
- C1049
helpviewer_keywords:
- C1049
ms.openlocfilehash: f2669eec4bafb24f26c405d4fa74a96fe5337d13
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633304"
---
# <a name="fatal-error-c1049"></a>致命的なエラー C1049

> 数値の引数 '*value*' が無効です。

CL。EXE コマンドラインパーサーで、数値引数を予期していた*値*が見つかりました。

コンパイラが、次のいずれかのコンパイラオプションの数値引数を見つけられない場合、C1049 エラーが発生する可能性があります。

[/constexpr: 深さ](/cpp/build/reference/constexpr-control-constexpr-evaluation)\
[/constexpr: バックトレース](/cpp/build/reference/constexpr-control-constexpr-evaluation)\
[/constexpr: 手順](/cpp/build/reference/constexpr-control-constexpr-evaluation)

数値引数を予期するコマンドラインコンパイラオプションは、`Command line error D8004`、`Command line error D8021`、`Command line warning D9002`、`Command line warning D9014`、または `Command line warning D9024`を報告する場合もあります。

このエラーを解決するには、コマンドラインで間違っていた引数や不足していないかどうかを確認します。 オプションと引数の間に予期しない空白文字がないことを確認します。 最終的なコマンドラインは、マクロ、環境変数、またはその他のビルドシステム操作によって生成される場合があります。 そのため、コンパイラに渡される実際のコマンドラインを確認することが重要です。

- コマンドファイルまたはメイクファイルでは、 **echo**コマンドを使用して実際のコマンドラインを報告できます。

- Visual Studio で、プロジェクトの **[プロパティページ]** ダイアログを開きます。 **[構成プロパティ]**  >  **[CC++ /**  > **全般**] ページで、 **[スタートアップバナー]** を表示しない プロパティを **[いいえ]** に変更します。 **[OK]** を選択して変更を保存します。 **[出力]** ウィンドウに、著作権線の直後にビルドするとコマンドラインが表示されるようになりました。

その他のビルドシステムには、実際に使用されたコマンドを確認するためのログファイルや詳細オプションがあります。 詳細については、ビルドシステムのドキュメントを確認してください。
