---
title: コード ページ
ms.date: 11/04/2016
f1_keywords:
- c.international
helpviewer_keywords:
- character sets [C++], code pages
- ANSI [C++], code pages
- system-default code page
- multibyte code pages [C++]
- localization [C++], code pages
- code pages [C++], types of
- locale code pages [C++]
ms.assetid: 4a26fc42-185a-4add-98bf-a7b314ae6186
ms.openlocfilehash: 83c54a3d624ddad4de6c359c44c3b4be80c95a6e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57738569"
---
# <a name="code-pages"></a>コード ページ

"*コード ページ*" は文字セットです。数字、句読点、その他のグリフを入れることができます。 言語やロケールが異なると、コード ページも異なる場合があります。 たとえば、ANSI コード ページ 1252 は英語やほとんどのヨーロッパ言語で使われていますが、日本語の漢字には OEM コード ページ 932 が使われています。

コード ページはテーブルで表すことができます。文字を 1 バイト値やマルチバイト値にマッピングします。 多くのコード ページは、範囲 0x00 - 0x7F の文字に関して、ASCII 文字セットを共有しています。

Microsoft ランタイム ライブラリでは、次の種類のコード ページが使用されています。

- システム既定の ANSI コード ページ。 既定では、ランタイム システムはマルチバイト コード ページをシステムの既定の ANSI コード ページに自動的に設定します。既定のページはオペレーティング システムから取得されます。 呼び出し:

    ```C
    setlocale ( LC_ALL, "" );
    ```

   また、システム既定の ANSI コード ページにロケールを設定します。

- ロケールのコード ページ。 ランタイム ルーチンの動作は、ロケール コード ページを含む、現在のロケール設定に依存します。 (詳細については、[ロケール依存のルーチン](../c-runtime-library/locale.md)に関するページを参照してください。)既定では、Microsoft ランタイム ライブラリのすべてのロケール依存ルーチンで "C" ロケールに相当するコード ページが使用されます。 実行時、[setlocale](../c-runtime-library/reference/setlocale-wsetlocale.md) を呼び出し、使用中のロケール コード ページを変更したり、クエリを実行したりできます。

- マルチバイト コード ページ。 ランタイム ライブラリのマルチバイト文字のほとんどの動作は、現在のマルチバイト コード ページ設定に依存します。 既定では、これらのルーチンではシステム既定の ANSI コード ページが使用されます。 実行時に、[_getmbcp](../c-runtime-library/reference/getmbcp.md) と [_setmbcp](../c-runtime-library/reference/setmbcp.md) でマルチバイト コード ページをそれぞれ照会または変更できます。

- "C" ロケールは、従来、C プログラムが実行されていたロケールに対応するよう、ANSI により定義されます。 "C" ロケールのコード ページ ("C" コード ページ) は ASCII 文字セットに対応します。 たとえば、"C" ロケールでは、**islower** は値 0x61 - 0x7A にのみ true を返します。 別のロケールの場合、**islower** は、そのロケールによる定義に基づき、値 0x61 - 0x7A とその他の値に true を返すことがあります。

## <a name="see-also"></a>関連項目

[国際化](../c-runtime-library/internationalization.md)<br/>
[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
