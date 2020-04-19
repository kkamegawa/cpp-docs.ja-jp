---
title: Unicode のサポート
ms.date: 01/09/2018
helpviewer_keywords:
- globalization [C++], character sets
- portable data types [MFC]
- Unicode [C++]
- wide characters [C++], about wide characters
- character sets [C++], Unicode
- localization [C++], character sets
- Unicode [C++], installing support
ms.openlocfilehash: c30cb1fbfb1930b5e4b026e58c478f0099e8ecdf
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929917"
---
# <a name="support-for-unicode"></a>Unicode のサポート

Unicode は、1バイトでは表現できない文字セットを含む、すべての文字セットをサポートするための仕様です。  国際市場向けにプログラミングしている場合は、Unicode または[マルチバイト文字セット](../text/support-for-multibyte-character-sets-mbcss.md)(MBCS) のいずれかを使用することをお勧めします。 または、スイッチを変更することによってビルドできるようにプログラムをコーディングします。

ワイド文字は、2 バイトの多言語文字コードです。 世界中の最新のコンピューティング環境で使用されているほとんどすべての文字 (技術記号や特殊な出版文字を含む) を含む、数十の文字が、Unicode 仕様に従って、でエンコードされた1つのワイド文字として表現されます。UTF-16 を使用します。 1つのワイド文字では表現できない文字は、unicode サロゲートペア機能を使用して、Unicode ペアで表すことができます。 一般的に使用されるほとんどすべての文字は、1つの16ビットワイド文字で UTF-16 で表されるため、ワイド文字を使用すると、国際文字セットを使用したプログラミングが簡単になります。 16LE (リトルエンディアン用) を使用してエンコードされたワイド文字は、Windows のネイティブ文字形式です。

ワイド文字列は `wchar_t[]` 配列として表現され、`wchar_t*` ポインターで指し示されます。 ASCII 文字は、先頭に文字 L を付けることで、ワイド文字として表現できます。 たとえば、L ' \ 0 ' は、全角 (16 ビット) の終端の NULL 文字です。 同様に、ASCII 文字列リテラルは、ASCII リテラルの先頭に文字 L を付けることで、ワイド文字列リテラルとして表現できます (L"Hello")。

通常、ワイド文字はマルチバイト文字よりもメモリ内の領域を多く必要としますが、処理は速くなります。 さらに、マルチバイトエンコードで一度に表現できるロケールは1つだけです。一方、世界中のすべての文字セットは、Unicode 表現によって同時に表現されます。

MFC フレームワークは Unicode に完全に対応しており、MFC では、次の表に示すように、移植性のあるマクロを使用することで Unicode 対応を実現しています。

## <a name="portable-data-types-in-mfc"></a>MFC での移植性のあるデータ型

|移植性のないデータ型|置き換えに使うマクロ|
|-----------------------------|----------------------------|
|`char`, `wchar_t`|`_TCHAR`|
|`char*`、 `LPSTR` (Win32 データ型)、`LPWSTR`|`LPTSTR`|
|`const char*`、 `LPCSTR` (Win32 データ型)、`LPCWSTR`|`LPCTSTR`|

クラス`CString`は`_TCHAR` 、をベースとして使用し、簡単に変換できるようにコンストラクターと演算子を提供します。 Unicode の文字列操作のほとんどは、操作の基本単位が 8 ビット バイトではなく 16 ビット文字であることを除き、Windows の ANSI 文字セットの操作に使用するのと同じロジックを使用して記述できます。 マルチバイト文字セットの操作と異なり、1 つの Unicode 文字を 2 つの個別のバイトのように扱う必要はなく、また、そのような処理は適切ではありません。 ただし、ワイド文字のサロゲートペアによって表される1文字の可能性に対処する必要があります。 一般に、文字列の長さが、含まれている文字数と同じであることを前提としたコードは記述しないでください。

## <a name="what-do-you-want-to-do"></a>実行する操作

- [MFC Unicode とマルチバイト文字セット (MBCS) のサポートを使用する](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)

- [プログラムで Unicode を有効にする](../text/international-enabling.md)

- [プログラムで Unicode と MBCS の両方を有効にする](../text/internationalization-strategies.md)

- [Unicode を使用して国際化プログラムを作成する](../text/unicode-programming-summary.md)

- [Unicode の利点について説明します。](../text/benefits-of-character-set-portability.md)

- [プログラムにワイド文字引数を渡すことができるように、wmain を使用します。](../text/support-for-using-wmain.md)

- [Unicode プログラミングの概要を確認する](../text/unicode-programming-summary.md)

- [バイト幅の移植性のための汎用テキストマッピングについて説明します。](../text/generic-text-mappings-in-tchar-h.md)

## <a name="see-also"></a>関連項目

[テキストと文字列](../text/text-and-strings-in-visual-cpp.md)<br/>
[wmain の使用](../text/support-for-using-wmain.md)