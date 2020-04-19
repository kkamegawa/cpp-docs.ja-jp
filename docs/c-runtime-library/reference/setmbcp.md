---
title: _setmbcp
ms.date: 11/04/2016
api_name:
- _setmbcp
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-locale-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _setmbcp
- setmbcp
helpviewer_keywords:
- setmbcp function
- _setmbcp function
- multibyte code pages
ms.assetid: cfde53b5-0b73-4684-81b1-a8d3aafc85de
ms.openlocfilehash: a3408f04eb60a33a84c628c989ebc9c4c4a261df
ms.sourcegitcommit: f38f770bfda1c174d2b81fabda7c893b15bd83a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473878"
---
# <a name="_setmbcp"></a>_setmbcp

新しいマルチバイト コード ページを設定します。

## <a name="syntax"></a>構文

```C
int _setmbcp(
   int codepage
);
```

### <a name="parameters"></a>パラメーター

*codepage*<br/>
ロケールに依存しないマルチバイトのルーチンのための新しいコード ページ設定。

## <a name="return-value"></a>戻り値

コード ページが正常に設定されている場合は、0 を返します。 コードページに無効なコードページ値が指定されている場合、は-1 を返し、コード*ページの設定*は変更されません。 メモリ割り当てエラーが発生した場合に、 **errno**を**EINVAL**に設定します。

## <a name="remarks"></a>コメント

**_Setmbcp**関数は、新しいマルチバイトコードページを指定します。 既定では、ランタイム システムはマルチバイト コード ページを、システムの既定の ANSI コード ページに自動的に設定します。 マルチバイト コード ページの設定は、ロケールに依存していないすべてのマルチバイトのルーチンに影響します。 ただし、現在のロケールに対して定義されているコードページを使用するように **_setmbcp**に指示することはできます (次のマニフェスト定数と関連する動作の結果の一覧を参照してください)。 マルチバイト コード ページではなく、ロケールのコード ページに依存しているマルチバイトのルーチンの一覧については、「[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)」を参照してください。

マルチバイト コード ページは、次のランタイム ライブラリ ルーチンによる、マルチバイト文字の処理にも影響します。

||||
|-|-|-|
|[_exec 関数](../../c-runtime-library/exec-wexec-functions.md)|[_mktemp](mktemp-wmktemp.md)|[_stat](stat-functions.md)|
|[_fullpath](fullpath-wfullpath.md)|[_spawn 関数](../../c-runtime-library/spawn-wspawn-functions.md)|[_tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|
|[_makepath](makepath-wmakepath.md)|[_splitpath](splitpath-wsplitpath.md)|[tempnam](tempnam-wtempnam-tmpnam-wtmpnam.md)|

また、マルチバイト文字の*argv*または*envp*プログラム引数をパラメーターとして受け取るすべてのランタイムライブラリルーチン ( **_exec**や **_spawn**ファミリなど) は、マルチバイトコードページに従ってこれらの文字列を処理します。 そのため、これらのルーチンは、マルチバイトコードページを変更する **_setmbcp**を呼び出すことによっても影響を受けます。

*Codepage*引数は、次のいずれかの値に設定できます。

- **_MB_CP_ANSI**プログラムの起動時にオペレーティングシステムから取得した ANSI コードページを使用します。

- **_MB_CP_LOCALE**以前の[setlocale](setlocale-wsetlocale.md)の呼び出しから取得した現在のロケールのコードページを使用します。

- **_MB_CP_OEM**プログラムの起動時にオペレーティングシステムから取得した OEM コードページを使用します。

- **_MB_CP_SBCS**1バイトのコードページを使用します。 コードページが **_MB_CP_SBCS**に設定されている場合、 [_ismbblead](ismbblead-ismbblead-l.md)などのルーチンは常に false を返します。

- **_MB_CP_UTF8**UTF-8 を使用します。  コードページが **_MB_CP_UTF8**に設定されている場合、 [_ismbblead](ismbblead-ismbblead-l.md)などのルーチンは常に false を返します。

- その他の有効なコードページ値。値が ANSI、OEM、またはその他のオペレーティングシステムでサポートされているコードページ (ただし、サポートされていない UTF-7 を除く) です。

## <a name="requirements"></a>要件

|ルーチン|必須ヘッダー|
|-------------|---------------------|
|**_setmbcp**|\<mbctype.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>参照

[_getmbcp](getmbcp.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
