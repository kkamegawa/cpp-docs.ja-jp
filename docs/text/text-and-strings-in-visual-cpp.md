---
title: Visual C++ のテキストと文字列
ms.date: 11/04/2016
helpviewer_keywords:
- globalization [C++], character sets
- programming [C++], international
- multiple language support [C++]
- Unicode [C++]
- international applications [C++], about international applications
- portability [C++]
- translation [C++], character sets
- non-European characters [C++]
- character sets [C++]
- globalization [C++]
- Japanese characters [C++]
- Kanji character support [C++]
- local character sets [C++]
- ASCII characters [C++]
- character sets [C++], about character sets
- localization [C++], character sets
- translating code [C++]
- localization [C++]
- character sets [C++], non-European
- portability [C++], character sets
- MBCS [C++], international programming
ms.assetid: a1bb27ac-abe5-4c6b-867d-f761d4b93205
ms.openlocfilehash: c6083fcf9db8236df15d1cb5e7de4cc15fe5916e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411800"
---
# <a name="text-and-strings-in-visual-c"></a>Visual C++ のテキストと文字列

国際市場をターゲットにアプリケーションを開発する場合は、地域の文字セットをサポートすることが重要です。 ASCII 文字セットでは、0x00 から 0x7F までの範囲の文字を定義しています。 そのほかに、ASCII 文字セットと同じ 0x00 から 0x7F までの範囲の文字に加え、0x80 から 0xFF までの拡張文字セットも定義している、主にヨーロッパ向けの文字セットもあります。 多くのヨーロッパ系言語の文字と ASCII 文字セットを表現するには、8 ビットの 1 バイト文字セット (SBCS: Single-Byte-Character Set) で十分です。 ただし、日本語の漢字など、ヨーロッパ以外の文字セットでは、1 バイトのコード体系ですべての文字を表現しきれないため、マルチバイト文字セット (MBCS: Multibyte-Character Set) エンコーディングが必要になります。

## <a name="in-this-section"></a>このセクションの内容

[Unicode と MBCS](../text/unicode-and-mbcs.md)<br/>
Visual C++ でサポートする Unicode プログラミングと MBCS プログラミングについて説明します。

[Unicode のサポート](../text/support-for-unicode.md)<br/>
1 バイト文字では表現できない文字セットを含むあらゆる文字セットをサポートする Unicode について説明します。

[マルチバイト文字セット (MBCS) のサポート](../text/support-for-multibyte-character-sets-mbcss.md)<br/>
Unicode の代わりとして、日本語や中国語など、1 バイト文字では表現できない文字セットをサポートする MBCS について説明します。

[tchar.h における汎用テキストのマッピング](../text/generic-text-mappings-in-tchar-h.md)<br/>
多くのデータ型、ルーチン、およびその他のオブジェクトに対する、Microsoft 固有の汎用テキストのマッピングについて説明します。

[方法: さまざまな文字列型間で変換する](../text/how-to-convert-between-various-string-types.md)<br/>
さまざまな Visual C++ 文字列型を他の文字列に変換する方法について説明します。

## <a name="related-sections"></a>関連項目

[国際化](../c-runtime-library/internationalization.md)<br/>
C ランタイム ライブラリの国際対応のサポートについて説明します。

[国際対応のサンプル](https://github.com/Microsoft/VCSamples)<br/>
Visual C++ の国際化のアプローチを示すサンプルへのリンクを提供します。

[言語および国/地域識別文字列](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
C ランタイム ライブラリの言語および国/地域識別文字列について説明します。
