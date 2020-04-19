---
title: assert マクロ、_assert、_wassert
ms.date: 11/04/2016
api_name:
- assert
- _assert
- _wassert
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- assert
- _assert
- _wassert
- assert/_wassert
helpviewer_keywords:
- aborting programs
- assert function
- assert macro
ms.assetid: a9ca031a-648b-47a6-bdf1-65fc7399dd40
ms.openlocfilehash: badca46a0793e51602f0de87dfca21816dcd6295
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939623"
---
# <a name="assert-macro-_assert-_wassert"></a>assert マクロ、_assert、_wassert

式を評価し、結果が**false**の場合に診断メッセージを出力し、プログラムを中止します。

## <a name="syntax"></a>構文

```C
assert(
   expression
);
void _assert(
   char const* message,
   char const* filename,
   unsigned line
);
void _wassert(
   wchar_t const* message,
   wchar_t const* filename,
   unsigned line
);
```

### <a name="parameters"></a>パラメーター

*式 (expression)*<br/>
0以外 (**true**) または 0 (**false**) に評価されるスカラー式 (ポインター式)。

*message*<br/>
表示するメッセージ。

*ファイル名*<br/>
アサーションが失敗したソース ファイルの名前。

*直線*<br/>
失敗したアサーションのソース ファイルの行番号。

## <a name="remarks"></a>Remarks

**Assert**マクロは、通常、プログラム開発中の論理エラーを識別するために使用されます。 *式*引数を実装して、プログラムが正しく動作していない場合にのみ**false**に評価されるようにすることで、予期しない条件が発生したときにプログラムの実行を停止します。 マクロ**NDEBUG**を定義することで、コンパイル時にアサーションチェックをオフにすることができます。 **/Dndebug**コマンドラインオプションを使用して、ソースファイルを変更せずに**assert**マクロをオフにすることができます。 Assert > が含まれている前に`#define NDEBUG` \<ディレクティブを使用して、ソースコードの assert マクロをオフにすることができます。

*Expression*が**false** (0) と評価された場合、 **assert**マクロは診断メッセージを出力し、 [abort](abort.md)を呼び出してプログラムの実行を終了します。 *Expression*が**true** (0 以外) の場合、アクションは実行されません。 診断メッセージには、失敗した式、ソース ファイルの名前、アサーションが失敗した行番号が含まれます。

診断メッセージはワイド文字で出力されます。 したがって、式に Unicode 文字がある場合でも、予期していたとおりに機能します。

ルーチンを呼び出したアプリケーションの種類に基づいて診断メッセージの出力先が決まります。 コンソールアプリケーションは、常に**stderr**を通じてメッセージを受信します。 Windows ベースのアプリケーションでは、 **assert**は windows [MessageBox](/windows/win32/api/winuser/nf-winuser-messagebox)関数を呼び出して、メッセージボックスを作成し、メッセージを **[OK** ] ボタンと共に表示します。 ユーザーが **[OK]** をクリックすると、プログラムはすぐに中止されます。

アプリケーションがランタイムライブラリのデバッグバージョンにリンクされている場合、 **assert**は、次の3つのボタンを含むメッセージボックスを作成します。**Abort**、 **Retry**、および**Ignore**。 ユーザーが **[中止]** をクリックすると、プログラムはすぐに中止されます。 ユーザーが **[再試行]** をクリックすると、Just-In-Time (JIT) デバッグが有効になっている場合、デバッガーが呼び出され、ユーザーはプログラムをデバッグできます。 ユーザーが **[無視]** をクリックすると、通常の実行である**assert**が続行されます。 **[OK** ] ボタンを使用したメッセージボックスの作成です。 なお、エラー状況が存在するときに **[無視]** をクリックすると、"未定義の動作" という結果になることがあります。

CRT デバッグの詳細については、「[CRT のデバッグ技術](/visualstudio/debugger/crt-debugging-techniques)」を参照してください。

**_Assert**関数と **_wassert**関数は、内部 CRT 関数です。 これらは、アサーションをサポートするためのオブジェクト ファイルに必要なコードを最小限に抑えるうえで役立ちます。 これらの関数を直接呼び出すことはお勧めしません。

**Assert**マクロは、 **NDEBUG**が定義されていない場合に、C ランタイムライブラリのリリースバージョンとデバッグバージョンの両方で有効になります。 **NDEBUG**が定義されている場合、マクロは使用できますが、引数は評価されず、効果はありません。 この設定を有効にすると、 **assert**マクロは実装のために **_wassert**を呼び出します。 その他のアサーション マクロの [_ASSERT](assert-asserte-assert-expr-macros.md)、 [_ASSERTE](assert-asserte-assert-expr-macros.md) 、 [_ASSERT_EXPR](assert-asserte-assert-expr-macros.md)も使用できますが、これらは、 [_DEBUG](../../c-runtime-library/debug.md) マクロが定義されており、かつ C ランタイム ライブラリのデバッグ バージョンとリンクされたコードにある場合にのみ、渡される式を評価します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**assert**、 **_wassert**|\<assert.h>|

**_Assert**関数の署名は、ヘッダーファイルでは使用できません。 **_Wassert**関数の署名は、 **NDEBUG**マクロが定義されていない場合にのみ使用できます。

## <a name="example"></a>例

このプログラムでは、 **analyze_string**関数は**assert**マクロを使用して、文字列と長さに関連するいくつかの条件をテストします。 条件のいずれかが失敗した場合、プログラムは失敗の原因を示すメッセージを出力します。

```C
// crt_assert.c
// compile by using: cl /W4 crt_assert.c
#include <stdio.h>
#include <assert.h>
#include <string.h>

void analyze_string( char *string );   // Prototype

int main( void )
{
   char  test1[] = "abc", *test2 = NULL, test3[] = "";

   printf ( "Analyzing string '%s'\n", test1 ); fflush( stdout );
   analyze_string( test1 );
   printf ( "Analyzing string '%s'\n", test2 ); fflush( stdout );
   analyze_string( test2 );
   printf ( "Analyzing string '%s'\n", test3 ); fflush( stdout );
   analyze_string( test3 );
}

// Tests a string to see if it is NULL,
// empty, or longer than 0 characters.
void analyze_string( char * string )
{
   assert( string != NULL );        // Cannot be NULL
   assert( *string != '\0' );       // Cannot be empty
   assert( strlen( string ) > 2 );  // Length must exceed 2
}
```

プログラムは次の出力を生成します。

```Output
Analyzing string 'abc'
Analyzing string '(null)'
Assertion failed: string != NULL, file crt_assert.c, line 25
```

アサーションが失敗した後、オペレーティング システムとランタイム ライブラリのバージョンに応じて、以下のような内容のメッセージ ボックスが表示される可能性があります。

```Output
A problem caused the program to stop working correctly. Windows will close the program and notify you if a solution is available.
```

デバッガーがインストールされている場合は **[デバッグ]** ボタンを選択してデバッガーを開始するか、 **[プログラムの終了]** をクリックして終了します。

## <a name="see-also"></a>関連項目

[エラー処理](../../c-runtime-library/error-handling-crt.md)<br/>
[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[raise](raise.md)<br/>
[signal](signal.md)<br/>
[_ASSERT、_ASSERTE、_ASSERT_EXPR Macros](assert-asserte-assert-expr-macros.md)<br/>
[_DEBUG](../../c-runtime-library/debug.md)<br/>
