---
title: MBCS プログラミングにおける一般的なアドバイス
ms.date: 11/04/2016
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 887387220105614eb3257f008ec601a6fc0adc18
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491182"
---
# <a name="general-mbcs-programming-advice"></a>MBCS プログラミングにおける一般的なアドバイス

次のヒントを参考にしてください。

- 柔軟性を高めるには、可能であれば`_tcschr` 、 `_tcscpy`などのランタイムマクロを使用します。 詳細については、「 [tchar. h の汎用テキストマップ](../text/generic-text-mappings-in-tchar-h.md)」を参照してください。

- 現在のコードページに関する`_getmbcp`情報を取得するには、C ランタイム関数を使用します。

- 文字列リソースは再利用しないでください。 対象の言語によっては、特定の文字列が翻訳時に異なる意味を持つ場合があります。 たとえば、アプリケーションのメインメニューの "File" は、ダイアログボックス内の文字列 "File" とは異なる変換を行う場合があります。 同じ名前の複数の文字列を使用する必要がある場合は、それぞれに異なる文字列 Id を使用します。

- アプリケーションが MBCS が有効なオペレーティングシステムで実行されているかどうかを確認することもできます。 これを行うには、プログラムの起動時にフラグを設定します。API 呼び出しに依存しないでください。

- ダイアログボックスをデザインするときに、MBCS 翻訳の静的テキストコントロールの最後に約 30% の余分なスペースを許可します。

- 一部のフォントはすべてのシステムで使用できるわけではないため、アプリケーションのフォントを選択するときは注意してください。

- ダイアログボックスのフォントを選択する場合は、MS Sans Serif または Helvetica, の代わりに[Ms Shell Dlg](/windows/win32/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2)を使用します。 MS Shell Dlg は、ダイアログボックスを作成する前に、システムによって正しいフォントに置き換えられます。 MS Shell Dlg を使用すると、このフォントを処理するためにオペレーティングシステムに加えられた変更がすべて自動的に使用できるようになります。 (これらのシステムでは MS Shell Dlg が正しく処理されないため、MS Shell Dlg は、Windows 95、Windows 98、および Windows NT 4 の DEFAULT_GUI_FONT またはシステムフォントに置き換えられます)。

- アプリケーションを設計するときに、ローカライズできる文字列を決定します。 不明な場合は、特定の文字列がローカライズされることを前提としています。 そのため、では実行できない文字列とローカライズできる文字列を混在させないでください。

## <a name="see-also"></a>関連項目

[MBCS のプログラミングについて](../text/mbcs-programming-tips.md)<br/>
[ポインターのインクリメントとデクリメント](../text/incrementing-and-decrementing-pointers.md)
