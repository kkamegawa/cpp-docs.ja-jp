---
title: 'Unicode とマルチバイト文字セット (MBCS: Multibyte Character Set) のサポート'
ms.date: 01/09/2017
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.openlocfilehash: 983b3d9bc72d99ab3c665f86cffd205dccf873e8
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927901"
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>Unicode とマルチバイト文字セット (MBCS: Multibyte Character Set) のサポート

日本語や中国語などの一部の言語は巨大な文字セットを扱います。 これらの市場のプログラミングをサポートするために、Microsoft Foundation Class ライブラリ (MFC) では、大きな文字セットを処理する2つの異なる方法を使用できます。

- [Unicode](#mfc-support-for-unicode-strings)で`wchar_t` 、utf-16 としてエンコードされたワイド文字と文字列。

- ロケール固有の文字セットでエンコードされた[マルチバイト文字セット (MBCS)](#mfc-support-for-mbcs-strings)、**文字ベースの**1 バイト文字、または2バイト文字と文字列。

Microsoft では、すべての新規開発に MFC Unicode ライブラリを推奨しています。また、MBCS ライブラリは Visual Studio 2013 と Visual Studio 2015 で非推奨とされました。 現在のバージョンには該当しません。 Visual Studio 2017 では、MBCS の非推奨の警告が削除されました。

## <a name="mfc-support-for-unicode-strings"></a>MFC がサポートする Unicode 文字列

MFC クラスライブラリ全体では、Unicode 文字およびワイド文字に格納されている文字列を UTF-16 として条件付きで有効にしています。 特に、クラス[CString](../atl-mfc-shared/reference/cstringt-class.md)は Unicode に対応しています。

これらのライブラリ、デバッガー、および DLL ファイルは、MFC で Unicode をサポートするために使用されます。

|||||
|-|-|-|-|
|UAFXCW.LIB|UAFXCW.PDB|UAFXCWD.LIB|UAFXCWD.PDB|
|MFC*バージョン*u. .lib|MFC*バージョン*u. .pdb|MFC*バージョン*U .dll|MFC*バージョン*UD。変数|
|MFC*バージョン*UD。PDB|MFC*バージョン*UD。DLL|MFCS*バージョン*u. .lib|MFCS*バージョン*u. .pdb|
|MFCS*バージョン*UD。変数|MFCS*バージョン*UD。PDB|MFCM*バージョン*u. .lib|MFCM*バージョン*u. .pdb|
|MFCM*バージョン*u. .dll|MFCM*バージョン*UD。変数|MFCM*バージョン*UD。PDB|MFCM*version*UD.DLL|

(*version*は、ファイルのバージョン番号を表します。たとえば、' 140 ' はバージョン14.0 を意味します)。

`CString`は、TCHAR データ型に基づいています。 プログラムのビルドにシンボル _unicode が定義されている場合、TCHAR は16ビット`wchar_t`文字エンコード型として定義されます。 それ以外の場合、TCHAR は、通常の8ビット文字エンコーディングである**char**として定義されます。 このため、Unicode を使用するときは、`CString` を 16 ビット幅の文字で構成します。 Unicode を使用しない場合、 **char**型の文字で構成されます。

アプリケーションを Unicode 対応にするには、次のことも行う必要があります。

- _T マクロを使用して、Unicode に移植できるようにリテラル文字列を条件付きでコーディングします。

- 文字列を引数として渡すときは、その関数が文字列の長さを文字数とバイト数のどちらで数えるのかを注意してください。 Unicode 文字列を使用するときは、文字数とバイト数の長さが異なります。

- C ランタイム ライブラリの文字列操作関数は Unicode 対応バージョンを使用してください。

- 文字および文字へのポインターには、以下の型を使用してください。

   - **Char**を使用する場合は、TCHAR を使用します。

   - <strong>Char\*</strong>を使用する場合は、LPTSTR を使用します。

   - **Const char**<strong>\*</strong>を使用する場合は、LPCTSTR を使用します。 `CString`と LPCTSTR の間で`CString`変換を行うための演算子 LPCTSTR を提供します。

`CString` のコンストラクター、代入演算子、比較演算子は Unicode を適切に処理します。

[ランタイムライブラリリファレンス](../c-runtime-library/c-run-time-library-reference.md)では、すべての文字列処理関数の移植可能なバージョンが定義されています。 詳細については、「[国際化](../c-runtime-library/internationalization.md)」を参照してください。

## <a name="mfc-support-for-mbcs-strings"></a>MFC がサポートする MBCS 文字列

このクラス ライブラリではマルチバイト文字セットもサポートされていますが、サポートされているのは、2 バイト文字セット (DBCS: Double-Byte Character Sets) のみです。

マルチバイト文字セットでは、文字は 1 バイト幅または 2 バイト幅になります。 2 バイト幅の文字では 1 バイト目が "先行バイト" になり、特定の範囲の文字を含むコード ページを指定します。 先行バイトと 2 バイト目の "後続バイト" を組み合わせると、そのコードが表す文字が決まります。

プログラムのビルドにシンボル _MBCS が定義されている場合は、「TCHAR」 `CString`と入力します。この場合のベースは**char**にマップされます。 _MBCS シンボルを定義したときは、`CString` 中のどのバイトが先行バイトであり、どのバイトが後続バイトであるかはプログラマが判定してください。 この判定用の関数は C ランタイム ライブラリで定義されています。

DBCS では、文字列の中に任意の ANSI の 1 バイト文字と 2 バイト文字を混在させることができます。 したがって、DBCS では文字列の解析時に特別な注意が必要です。 このようなリソースとして、`CString` オブジェクトがあります。

> [!NOTE]
> MFC における Unicode 文字列のシリアル化は、Unicode 文字列と MBCS 文字列の両方について、どちらのバージョンのアプリケーションを使用しているのかを考慮せずに読み込むことができます。 データ ファイルはプログラムの Unicode 版と MBCS 版の間で移植性があります。

`CString` のメンバー関数は、特別な "汎用テキスト" バージョンの C ランタイム ライブラリ関数を使用します。つまり、Unicode 対応の関数を使用します。 したがって、たとえば、`CString` のメンバー関数が通常 `strcmp` を呼び出す場所では、代わりに "汎用テキスト" 関数 `_tcscmp` を呼び出します。 シンボルの _MBCS と _unicode の定義方法に応じて`_tcscmp` 、は次のようにマップされます。

|||
|-|-|
|_MBCS が定義されている場合|`_mbscmp`|
|_UNICODE が定義されている場合|`wcscmp`|
|どちらのシンボルも定義されていない場合|`strcmp`|

> [!NOTE]
> シンボル _MBCS と _UNICODE は相互に排他的です。

すべてのランタイム文字列処理ルーチンの汎用テキスト関数のマッピングについては、「 [C ランタイムライブラリリファレンス](../c-runtime-library/c-run-time-library-reference.md)」で説明されています。 一覧については、「[国際化](../c-runtime-library/internationalization.md)」を参照してください。

同様に`CString` 、ジェネリックデータ型のマッピングを使用してメソッドが実装されます。 MBCS と Unicode の両方を有効にするには 、MFC `wchar_t`では、char 型`wchar_t*`の場合は TCHAR、 **char** <strong>\*</strong>型`const wchar_t*`の場合は LPTSTR、 **const char** <strong>\*</strong>の場合は LPCTSTR、の場合はを使用します。 これによって、MBCS または Unicode への正しいマッピングが確保されます。

## <a name="see-also"></a>関連項目

[文字列 (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[文字列操作](../c-runtime-library/string-manipulation-crt.md)
