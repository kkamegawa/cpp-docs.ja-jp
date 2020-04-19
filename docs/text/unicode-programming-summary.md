---
title: Unicode プログラミングの要約
ms.date: 11/04/2016
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
ms.openlocfilehash: 130c9027a882de2aae7fb339e4761b0cc81b3a6a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410513"
---
# <a name="unicode-programming-summary"></a>Unicode プログラミングの要約

Unicode に対する MFC や C のランタイム機能のサポートを有効にするには、次のようにします。

- 定義`_UNICODE`します。

   シンボルを定義`_UNICODE`プログラムをビルドする前にします。

- エントリ ポイントを指定する。

   **詳細**のページ、**リンカー**プロジェクトのフォルダー[プロパティ ページ](../ide/property-pages-visual-cpp.md)ダイアログ ボックスで、セット、**エントリ ポイント**にシンボル`wWinMainCRTStartup`.

- 移植性の高いランタイム関数と型を使用する。

   Unicode 文字列を取り扱う際は、必ず適切な C ランタイム関数を使います。 使用することができます、`wcs`ファミリが、機能のことも (国際対応の) 完全ポータブル`_TCHAR`マクロ。 これらのマクロはすべてを先頭`_tcs`;、置き換えると、1 つは、1 つの`str`ファミリの関数。 これらの関数がで詳しく説明されている、[国際化](../c-runtime-library/internationalization.md)のセクション、*ランタイム ライブラリ リファレンス*します。 詳細については、次を参照してください。 [tchar.h における汎用テキスト マッピング](../text/generic-text-mappings-in-tchar-h.md)します。

   使用`_TCHAR`で説明されている関連する移植可能なデータ型と[Unicode のサポート](../text/support-for-unicode.md)します。

- リテラル文字列を正しく処理する。

   Visual C++ コンパイラでは、次のリテラル文字列を

    ```cpp
    L"this is a literal string"
    ```

   Unicode 文字の文字列として解釈します。 リテラル文字にも、同じプリフィックスを使うことができます。 使用して、 `_T` unicode の Unicode 文字列または Unicode を含めない ANSI 文字列 (MBCS を含む) としてコンパイルするために一般的に、リテラル文字列をコーディングするマクロ。 たとえば、

    ```cpp
    pWnd->SetWindowText( "Hello" );
    ```

   を使う代わりに、

    ```cpp
    pWnd->SetWindowText( _T("Hello") );
    ```

   `_UNICODE`定義、 `_T` L プレフィックス付きフォームにリテラル文字列を変換します。 それ以外の場合、`_T`を L プレフィックス文字列を変換します。

    > [!TIP]
    >  `_T`マクロのと同じですが、`_TEXT`マクロ。

- 注意して文字列の長さを関数に渡す。

   文字列の文字数を要求する関数もありますが、バイト数を要求する関数もあります。 たとえば場合、`_UNICODE`が定義されている、次の呼び出しを`CArchive`オブジェクトは機能しません (`str`は、 `CString`)。

    ```cpp
    archive.Write( str, str.GetLength( ) );    // invalid
    ```

   Unicode アプリケーションの場合、文字列の長さは文字数を表しますが、各文字が 2 バイト幅なので、正確なバイト数ではありません。 バイト数を渡す場合は、次のコードを記述する必要があります。

    ```cpp
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid
    ```

   このコードにより、正確なバイト数を書き込むことができます。

   これに対して、バイト指向ではなく文字指向の MFC メンバー関数の場合は、この補足コードがなくても正常に機能します。

    ```cpp
    pDC->TextOut( str, str.GetLength( ) );
    ```

   `CDC::TextOut` は、バイト数ではなく文字数を取ります。

- 使用[fopen_s、_wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) Unicode ファイルを開きます。

要約すると、MFC とランタイム ライブラリは Unicode プログラミングの次のサポートを提供します。

- データベース クラスのメンバー関数を除いて、`CString` を含むすべての MFC 関数は、Unicode に対応しています。 また、`CString` には、Unicode/ANSI 変換関数も用意されています。

- ランタイム ライブラリには、すべての文字列操作関数の Unicode バージョンが用意されています。 (また、Unicode や MBCS に適した移植性の高いバージョンとして、 これらは、`_tcs`マクロです)。

- Tchar.h には、移植可能なデータ型と`_T`リテラル文字列と文字を変換するためのマクロ。 詳細については、次を参照してください。 [tchar.h における汎用テキスト マッピング](../text/generic-text-mappings-in-tchar-h.md)します。

- ランタイム ライブラリのワイド文字バージョンを提供します`main`します。 使用`wmain`Unicode 対応のアプリケーションを作成します。

## <a name="see-also"></a>関連項目

[Unicode のサポート](../text/support-for-unicode.md)
