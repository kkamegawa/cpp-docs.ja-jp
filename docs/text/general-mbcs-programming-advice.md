---
title: MBCS プログラミングにおける一般的なアドバイス
ms.date: 11/04/2016
f1_keywords:
- _mbcs
helpviewer_keywords:
- MBCS [C++], dialog box fonts
- MS Shell Dlg
- MBCS [C++], programming
- dialog boxes [C++], fonts
ms.assetid: 7b541235-f3e5-4af0-b2c2-a0112cd5fbfb
ms.openlocfilehash: 800e94bfb8a52b806ad45368499f126fbf163389
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626696"
---
# <a name="general-mbcs-programming-advice"></a>MBCS プログラミングにおける一般的なアドバイス

次のヒントを使用します。

- 柔軟性を高めるには、実行時マクロをなど使用`_tcschr`と`_tcscpy`可能な場合。 詳細については、次を参照してください。 [tchar.h における汎用テキスト マッピング](../text/generic-text-mappings-in-tchar-h.md)します。

- C ランタイムを使用して、`_getmbcp`関数が現在のコード ページに関する情報を取得します。

- 文字列リソースを再利用しません。 ターゲット言語に応じて、指定された文字列に変換すると、さまざまな意味をことがあります。 たとえば、"File"で、アプリケーションのメイン メニューは可能性があります ダイアログ ボックスには、"File"の文字列から異なる方法で変換します。 同じ名前の 1 つ以上の文字列を使用する必要がある場合は、それぞれ別の文字列 Id を使用します。

- Mbcs のオペレーティング システム、アプリケーションが実行されているかどうかを確認することがあります。 そのためには、プログラムの起動時にフラグを設定します。API 呼び出しに依存しないでください。

- ダイアログ ボックスを設計するときは、約 30% を許可する MBCS 変換用の静的なテキスト コントロールの末尾に余分な領域。

- 一部のフォントは、すべてのシステムで使用されていないため、このプロパティの値は慎重に、アプリケーションのフォントを選択します。

- 使用して、ダイアログ ボックスのフォントを選択すると、 [MS Shell Dlg](/windows/desktop/Intl/using-ms-shell-dlg-and-ms-shell-dlg-2) MS Sans Serif」または「Helvetica の代わりにします。 MS Shell Dlg は、ダイアログ ボックスを作成する前に、システムによって、適切なフォントに置き換えが。 MS Shell Dlg を使うと、このフォントを処理するオペレーティング システムのすべての変更は自動的に利用できることができます。 (MFC 置き換えます MS Shell Dlg DEFAULT_GUI_FONT またはシステム フォント Windows 95、Windows 98、および Windows NT 4 のこれらのシステムは MS Shell Dlg が正しく処理されないためです。)

- アプリケーションを設計するときは、文字列をローカライズすることができますを決定します。 不明な場合に、すべての文字列をローカライズすることを想定しています。 そのため、混在させないでくださいローカライズ可能な文字列のことができません。

## <a name="see-also"></a>関連項目

[MBCS のプログラミングについて](../text/mbcs-programming-tips.md)<br/>
[ポインターのインクリメントとデクリメント](../text/incrementing-and-decrementing-pointers.md)
