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
ms.openlocfilehash: 4ef970174a56361fdbd2102f363b4849ad4af9f3
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894186"
---
# <a name="support-for-using-wmain"></a>wmain の使用

Visual C のサポートを定義する、 **wmain**関数と、Unicode アプリケーションにワイド文字引数を渡します。 仮パラメーターを宣言する**wmain**のような形式を使用して`main`します。 さらに、ワイド文字の引数と、必要であればワイド文字環境ポインターもプログラムに渡すことができます。 **wmain** の引数 `argv` と `envp` の型は `wchar_t*` です。 例:

```cpp
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )
```

> [!NOTE]
> Unicode の MFC アプリケーションを使用して、`wWinMain`エントリ ポイントとして。 この場合、`CWinApp::m_lpCmdLine`は Unicode 文字列です。 設定を必ず`wWinMainCRTStartup`で、 [/ENTRY](../build/reference/entry-entry-point-symbol.md)リンカー オプション。

プログラムが **main** 関数を使用している場合、マルチバイト文字環境は、プログラムの起動時にランタイム ライブラリが作成します。 マルチバイト文字環境で使われるワイド文字のコピーは、必要に応じて作成されます (たとえば、`_wgetenv` 関数や `_wputenv` 関数が呼び出されたとき)。 最初の呼び出しで`_wputenv`、または最初の呼び出しで`_wgetenv`MBCS 環境が既に存在する場合、対応するワイド文字列環境が作成されます。 環境を指していますし、`_wenviron`ワイド文字バージョンでは、グローバル変数の`_environ`グローバル変数。 この時点では、2 つのコピー (MBCS および Unicode) 環境のでは、同時に存在し、プログラムの有効期間にわたって実行時のシステムによって管理されます。

プログラムが **wmain** 関数を使っている場合は、ワイド文字環境がプログラムの起動時に作成され、また `_wenviron` グローバル変数によって環境のアドレスが示されます。 MBCS (ASCII) 環境を作成する最初の呼び出しで`_putenv`または`getenv`を指していて、`_environ`グローバル変数。

## <a name="see-also"></a>関連項目

[Unicode のサポート](../text/support-for-unicode.md)<br/>
[Unicode プログラミングの要約](../text/unicode-programming-summary.md)<br/>
[WinMain 関数](/windows/desktop/api/winbase/nf-winbase-winmain)