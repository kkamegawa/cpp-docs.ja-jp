---
title: テキスト モードとバイナリ モードのファイル入出力
ms.date: 04/11/2018
f1_keywords:
- c.io
helpviewer_keywords:
- files [C++], open functions
- I/O [CRT], text files
- functions [CRT], file access
- binary access, binary mode file I/O
- translation, modes
- I/O [CRT], binary
- text files, I/O
- I/O [CRT], translation modes
- translation modes (file I/O)
- binary access
ms.assetid: 3196e321-8b87-4609-b302-cd6f3c516051
ms.openlocfilehash: 2c875350aedadb55d8f96fb682d6215030be2198
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738585"
---
# <a name="text-and-binary-mode-file-io"></a>テキスト モードとバイナリ モードのファイル入出力

ファイル I/O 操作は、ファイルを開いたモードによって、2 つの変換モード、"*テキスト*" または "*バイナリ*" のいずれかで行われます。 通常、データ ファイルはテキスト モードで処理されます。 ファイル変換モードを制御するには、以下を行います。

- 現在の既定の設定を保持し、選択したファイルを開く場合にのみ、別のモードを指定します。

- 関数 [_set_fmode](../c-runtime-library/reference/set-fmode.md) を使用して、新しく開くファイルの既定のモードを変更します。 [_get_fmode](../c-runtime-library/reference/get-fmode.md) を使用して、現在の既定のモードを取得します。 初期の既定値はテキスト モード (**_O_TEXT**) です。

- プログラム内でグローバル変数 [_fmode](../c-runtime-library/fmode.md) を設定することで、既定の変換モードを直接変更します。 関数 **_set_fmode** でこの変数の値を設定しますが、直接設定することもできます。

[_open](../c-runtime-library/reference/open-wopen.md)、[fopen](../c-runtime-library/reference/fopen-wfopen.md)、[fopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md)、[freopen](../c-runtime-library/reference/freopen-wfreopen.md)、[freopen_s](../c-runtime-library/reference/freopen-s-wfreopen-s.md)、[_fsopen](../c-runtime-library/reference/fsopen-wfsopen.md)、または[_sopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md) などのファイルを開く関数を呼び出すときに、関数 [_set_fmode](../c-runtime-library/reference/set-fmode.md) に適切な引数を指定することで、**_fmode** の現在の既定の設定をオーバーライドすることができます。 **stdin**、**stdout**、**stderr** ストリームは常に既定でテキスト モードで開きます。これらのファイルのいずれかを開くときに、この既定の設定をオーバーライドすることもできます。 ファイルを開いた後、ファイル記述子を使用して変換モードを変更するには、[_setmode](../c-runtime-library/reference/setmode.md) を使用します。

## <a name="see-also"></a>関連項目

[入出力](../c-runtime-library/input-and-output.md)<br/>
[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
