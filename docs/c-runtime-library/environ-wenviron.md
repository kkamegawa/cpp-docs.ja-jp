---
title: _environ、_wenviron
ms.date: 11/04/2016
f1_keywords:
- environ
- wenviron
- _wenviron
- _environ
helpviewer_keywords:
- environ function
- _environ function
- _wenviron function
- process environment
- wenviron function
ms.assetid: 7e639962-6536-47cd-8095-0cbe44a56e03
ms.openlocfilehash: 56f6f1d06d834ccab68daf859fac065cf215582c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748924"
---
# <a name="environ-wenviron"></a>_environ、_wenviron

`_environ` 変数は、プロセスの環境を構成するマルチバイト文字列へのポインターの配列を指すポインターです。 このグローバル変数は非推奨となりました。セキュリティを強化したバージョンである [getenv_s、_wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md) および[_putenv_s、_wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md) を、グローバル変数の代わりに使用する必要があります。 `_environ` は Stdlib.h で宣言されています。

> [!IMPORTANT]
>  この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```
extern char **_environ;
```

## <a name="remarks"></a>解説

`main` 関数を使用するプログラムでは、`_environ` は、オペレーティング システムの環境から取られる設定に従って、プログラムの起動時に初期化されます。 環境は、次の形式の 1 つ以上のエントリから構成されます。

`ENVVARNAME` `=string`

`getenv_s` と `putenv_s` は `_environ` 変数を使用して環境テーブルにアクセスし、これを変更します。 `_putenv` を呼び出して環境の設定が追加または削除されると、環境テーブルのサイズが変わります。 プログラムのメモリ要件によっては、メモリ内での場所も変わる可能性があります。 `_environ` の値は、それらの変化に応じて自動的に調整されます。

`_wenviron` 変数は、Stdlib.h で次のように宣言されています。

```
extern wchar_t **_wenviron;
```

この関数は、`_environ` 関数のワイド文字バージョンです。 `wmain` 関数を使用するプログラムでは、`_wenviron` は、オペレーティング システムの環境から取られる設定に従って、プログラムの起動時に初期化されます。

`main` を使用するプログラムでは、環境がマルチバイト文字の文字列で構成されるため、`_wenviron` の初期値は **NULL** です。 `_wgetenv` または `_wputenv` の最初の呼び出し時に、対応するワイド文字の文字列環境が作成され、`_wenviron` がその環境をポイントするようになります。

同様に、`wmain` を使用するプログラムでは、環境がワイド文字の文字列で構成されるため、`_environ` の初期値は **NULL** です。 `_getenv` または `_putenv` の最初の呼び出し時に、対応するマルチバイト文字の文字列環境が作成され、`_environ` がその環境をポイントするようになります。

2 つの環境のコピー (MBCS および Unicode) がプログラムに同時に存在する場合、ランタイム システムは、両方のコピーを保持する必要があるため、実行時間が長くなります。 たとえば、`_putenv` を呼び出す場合は、2 つの環境文字列が対応するように `_wputenv` も自動的に呼び出されます。

> [!CAUTION]
>  まれに、ランタイム システムが Unicode バージョンとマルチバイト バージョンの両方の環境を保持している場合、これら 2 つのバージョンの環境が正確には対応しないことがあります。 これは、一意のマルチバイト文字列はすべて一意の Unicode 文字列に対応していますが、一意の Unicode 文字列は必ずしも一意のマルチバイト文字列に対応していないためです。 このため、2 つの個別の Unicode 文字列が、同一のマルチバイト文字列にマップされる可能性があります。

Unicode コンテキストで `_environ` をポーリングすることは、[/MD](../build/reference/md-mt-ld-use-run-time-library.md) または `/MDd` リンケージが使用される場合には無意味です。 CRT DLL では、プログラムの種類 (ワイドまたはマルチバイト) は不明です。 ほとんどの場合のシナリオどおり、マルチバイトの種類のプログラムだけが作成されます。

この仕組みについて、擬似コードによる次の例で説明します。

```
int i, j;
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:
                                      // putenv ("env_var_z=string1")
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:
                                      // putenv("env_var_z=string2")
```

この例で使用する表記法では、文字列は C の文字列リテラルではありません。そうではなく、`_wputenv` 呼び出しでは Unicode 環境文字列リテラルを表すプレースホルダーであり、`putenv` 呼び出しではマルチバイト環境文字列を表すプレースホルダーです。 2 つの個別の Unicode 環境文字列に含まれる文字のプレースホルダー '`x`' と '`y`' は、現在の MBCS の文字に一意にマップされません。 その代わりに、両方は何かの MBCS 文字 '`z`' にマップされます。これは、文字列を変換しようとした場合の既定の結果です。

したがって、マルチバイト環境では、値 "`env_var_z`" は `putenv` への最初の暗黙的な呼び出しの後には "`string1`" ですが、`putenv` への 2 回目の暗黙的な呼び出しでこの値は上書きされ、"`env_var_z`" の値は "`string2`" に設定されます。 Unicode 環境 (`_wenviron` にある) およびマルチバイト環境 (`_environ` にある) は、この一連の呼び出しの後には異なっていることになります。

## <a name="see-also"></a>関連項目

[グローバル変数](../c-runtime-library/global-variables.md)<br/>
[getenv、 _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)<br/>
[getenv_s、_wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)<br/>
[_putenv、_wputenv](../c-runtime-library/reference/putenv-wputenv.md)<br/>
[_putenv_s、_wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)
