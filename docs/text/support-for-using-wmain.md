---
title: wmain の使用
ms.date: 11/04/2016
f1_keywords:
- wWinMain
helpviewer_keywords:
- wide characters [C++], wmain function
- wWinMain function
- wmain function
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
ms.openlocfilehash: 4af389c00f6065df631f891dadcb0b2f350f984d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491196"
---
# <a name="support-for-using-wmain"></a>wmain の使用

Visual C++は、 **wmain**関数を定義し、ワイド文字引数を Unicode アプリケーションに渡すことをサポートしています。 **Wmain**に対して仮パラメーターを宣言するに`main`は、のような形式を使用します。 さらに、ワイド文字の引数と、必要であればワイド文字環境ポインターもプログラムに渡すことができます。 **wmain** の引数 `argv` と `envp` の型は `wchar_t*` です。 例えば:

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> MFC Unicode アプリケーションは`wWinMain` 、エントリポイントとしてを使用します。 この場合、 `CWinApp::m_lpCmdLine`は Unicode 文字列です。 必ず [/ENTRY](../build/reference/entry-entry-point-symbol.md) リンカー オプションを使用して `wWinMainCRTStartup` を設定してください。

プログラムが **main** 関数を使用している場合、マルチバイト文字環境は、プログラムの起動時にランタイム ライブラリが作成します。 マルチバイト文字環境で使われるワイド文字のコピーは、必要に応じて作成されます (たとえば、`_wgetenv` 関数や `_wputenv` 関数が呼び出されたとき)。 を`_wputenv`最初に呼び出すとき、または MBCS 環境が既`_wgetenv`に存在する場合にを最初に呼び出すときに、対応するワイド文字の文字列環境が作成されます。 次に、グローバル変数 ( `_wenviron` `_environ`グローバル変数のワイド文字バージョン) によって環境がポイントされます。 この時点で、2つの環境のコピー (MBCS および Unicode) が同時に存在し、プログラムの有効期間中はランタイムシステムによって保持されます。

プログラムが **wmain** 関数を使っている場合は、ワイド文字環境がプログラムの起動時に作成され、また `_wenviron` グローバル変数によって環境のアドレスが示されます。 MBCS (ASCII) 環境は、 `_putenv`または`getenv`の最初の呼び出しで作成され、 `_environ`グローバル変数によってポイントされます。

## <a name="see-also"></a>関連項目

[Unicode のサポート](../text/support-for-unicode.md)<br/>
[Unicode プログラミングの要約](../text/unicode-programming-summary.md)<br/>
[WinMain 関数](/windows/win32/api/winbase/nf-winbase-winmain)
