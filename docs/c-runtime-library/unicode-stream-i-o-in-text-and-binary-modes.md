---
title: テキスト モードとバイナリ モードの Unicode ストリーム入出力
ms.date: 11/04/2016
f1_keywords:
- c.io
helpviewer_keywords:
- stream I/O routines
- I/O [CRT], unicode stream
- Unicode, stream I/O routines
- Unicode stream I/O
ms.assetid: 68be0c3e-a9e6-4fd5-b34a-1b5207f0e7d6
ms.openlocfilehash: 10f77c7142c707d4df841899b50be2807b1b9c7f
ms.sourcegitcommit: 878a164fe6d550ca81ab87d8425c8d3cd52fe384
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/22/2019
ms.locfileid: "68376271"
---
# <a name="unicode-stream-io-in-text-and-binary-modes"></a>テキスト モードとバイナリ モードの Unicode ストリーム入出力

Unicode ストリームの入出力ルーチン (**fwprintf**、**fwscanf**、**fgetwc**、**fputwc**、**fgetws**、**fputws** など) がテキスト モード (既定) で開かれたファイルを操作すると、次の 2 種類の文字変換が行われます。

- Unicode からマルチバイト文字セット (MBCS: Multibyte Character Set) への変換、または MBCS から Unicode への変換。 Unicode ストリーム入出力関数をテキスト モードで実行すると、入力ストリームまたは出力ストリームはマルチバイト文字のシーケンスであると想定されます。 このため、Unicode ストリーム入力関数はマルチバイト文字をワイド文字に変換し、 **mbtowc** 関数を呼び出した場合と同様の効果を得ます。 同様の理由で、Unicode ストリーム出力関数は、 **wctomb** 関数が呼び出されたかのように、ワイド文字をマルチバイト文字に変換します。

- 復帰改行 (CR-LF) の変換。 CR-LF 変換は、MBCS から Unicode への変換の前 (Unicode ストリーム入力関数の場合) と Unicode から MBCS への変換の後 (Unicode ストリーム出力関数の場合) に行われます。 入力時には、CR-LF の組み合わせが 1 つの LF 文字に変換されます。 出力時には、LF 文字が CR-LF の組み合わせに変換されます。

ただし、Unicode ストリーム入出力関数をバイナリ モードで実行すると、ファイルが Unicode であると想定されるため、入出力時に CR-LF 変換も文字変換も行われません。 `wcin` を UNICODE テキスト ファイルに対して正しく使用するには、`_setmode( _fileno( stdin ), _O_BINARY );` 命令を使用します。

## <a name="see-also"></a>関連項目

[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
[入出力](../c-runtime-library/input-and-output.md)<br/>
