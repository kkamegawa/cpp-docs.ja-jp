---
title: _set_se_translator
ms.date: 02/21/2018
api_name:
- _set_se_translator
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_se_translator
- set_se_translator
helpviewer_keywords:
- set_se_translator function
- exception handling, changing
- _set_se_translator function
ms.assetid: 280842bc-d72a-468b-a565-2d3db893ae0f
ms.openlocfilehash: 781deaad091b6aed72350100f7575c566bbae793
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948391"
---
# <a name="_set_se_translator"></a>_set_se_translator

Win32 例外 (C 構造化例外) を型指定された例外にC++変換するスレッドごとのコールバック関数を設定します。

## <a name="syntax"></a>構文

```cpp
_se_translator_function _set_se_translator(
    _se_translator_function seTransFunction
);
```

### <a name="parameters"></a>パラメーター

*seTransFunction*<br/>
ユーザーが作成した C 構造化例外の変換関数へのポインター。

## <a name="return-value"></a>戻り値

前の関数を後で復元できるように、 **_set_se_translator**によって登録されている前の変換関数へのポインターを返します。 前の関数が設定されていない場合は、戻り値を使用して既定の動作を復元できます。この値は**nullptr**にすることができます。

## <a name="remarks"></a>Remarks

**_Set_se_translator**関数は、型指定された例外としてC++ Win32 例外 (C 構造化例外) を処理する方法を提供します。 各 c 例外がC++ **catch**ハンドラーによって処理されるようにするには、まず、特定のクラス型を c 例外に属性化するために使用または派生できる c 例外ラッパークラスを定義します。 このクラスを使用するには、C 例外が発生するたびに内部例外処理メカニズムによって呼び出されるカスタム C 例外変換関数をインストールします。 変換関数内では、一致C++する**catch**ハンドラーによってキャッチされる可能性のある型指定された例外をスローできます。

**_Set_se_translator**を使用する場合は、 [/eha](../../build/reference/eh-exception-handling-model.md)を使用する必要があります。

カスタム変換関数を指定するには、変換関数の名前を引数として使用して **_set_se_translator**を呼び出します。 記述する変換関数は、 **try**ブロックを持つスタック上の関数呼び出しごとに1回呼び出されます。 既定の変換関数はありません。

変換関数は、C++ 型の例外をスローする以外のことは何もすべきではありません。 スローに加えて何かを行う場合 (たとえば、ログ ファイルへの書き込みなど)、プログラムが期待どおりに動作しない可能性があります。それは、変換関数が呼び出される回数がプラットフォームに依存するためです。

マルチスレッド環境では、変換関数は各スレッドとは別に管理されます。 新しい各スレッドは、それぞれの変換関数をインストールする必要があります。 したがって、各スレッドが、それぞれの変換処理を担当します。 **_set_se_translator**は、1つのスレッドに固有です。別の DLL で別の変換関数をインストールすることもできます。

記述する*Setransfunction*関数は、ネイティブコンパイル関数 (/clr でコンパイルされません) である必要があります。 これは、引数として、符号なし整数と Win32**例外ポインター**構造体へのポインターを受け取る必要があります。 引数は、それぞれ Win32 API **Getexceptioncode**関数と**getexceptioncode**関数への呼び出しの戻り値です。

```cpp
typedef void (__cdecl *_se_translator_function)(unsigned int, struct _EXCEPTION_POINTERS* );
```

**_Set_se_translator**の場合、CRT に動的にリンクするときには影響があります。プロセス内の別の DLL が **_set_se_translator**を呼び出し、ハンドラーをそれ自体のに置き換える場合があります。

マネージコード (/clr でコンパイルされたコード) または混合ネイティブコードまたはマネージコードから **_set_se_translator**を使用する場合は、変換プログラムがネイティブコードでのみ生成される例外に影響することに注意してください。 マネージド コードで生成されるマネージド例外 (`System::Exception` の発生時のものなど) はいずれも、変換関数経由ではルーティングされません。 Win32 関数**RaiseException**を使用してマネージコードで発生した例外や、ゼロ除算例外などのシステム例外によって発生した例外は、変換プログラムを通じてルーティングされます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_set_se_translator**|\<eh.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

このサンプルでは、の呼び出しをラップして、構造化例外変換器を設定し、RAII クラス`Scoped_SE_Translator`で古いものを復元します。 このクラスを使用すると、スコープ固有の変換を1つの宣言として導入できます。 クラスデストラクターは、コントロールがスコープから外れたときに元のトランスレーターを復元します。

```cpp
// crt_settrans.cpp
// compile with: cl /W4 /EHa crt_settrans.cpp
#include <stdio.h>
#include <windows.h>
#include <eh.h>
#include <exception>

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

void SEFunc()
{
    __try
    {
        printf( "In __try, about to force exception\n" );
        int x = 5;
        int y = 0;
        int *p = &y;
        *p = x / *p;
    }
    __finally
    {
        printf( "In __finally\n" );
    }
}

void trans_func( unsigned int u, EXCEPTION_POINTERS* )
{
    throw SE_Exception( u );
}

int main()
{
    Scoped_SE_Translator scoped_se_translator{ trans_func };
    try
    {
        SEFunc();
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught a __try exception, error %8.8x.\n", e.getSeNumber() );
    }
}
```

```Output
In __try, about to force exception
In __finally
Caught a __try exception, error c0000094.
```

## <a name="example"></a>例

**_Set_se_translator**によって提供される機能はマネージコードでは使用できませんが、ネイティブコードが **/clr**スイッチの下のコンパイルにある場合でも、ネイティブコードでこのマッピングを使用することができます。を使用`#pragma unmanaged`して指定されます。 構造化例外が、マップされるマネージコードでスローされている場合は、例外を生成して処理するコードを`#pragma unmanaged`としてマークする必要があります。 次のコードは考えられる使用法を示しています。 詳細については、「[プラグマ ディレクティブと __Pragma キーワード](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)」を参照してください。

```cpp
// crt_set_se_translator_clr.cpp
// compile with: cl /W4 /clr crt_set_se_translator_clr.cpp
#include <windows.h>
#include <eh.h>
#include <stdio.h>
#include <exception>

int thrower_func( int i ) {
   int y = 0;
   int *p = &y;
   *p = i / *p;
   return 0;
}

class SE_Exception : public std::exception
{
private:
    const unsigned int nSE;
public:
    SE_Exception() noexcept : SE_Exception{ 0 } {}
    SE_Exception( unsigned int n ) noexcept : nSE{ n } {}
    unsigned int getSeNumber() const noexcept { return nSE; }
};

class Scoped_SE_Translator
{
private:
    const _se_translator_function old_SE_translator;
public:
    Scoped_SE_Translator( _se_translator_function new_SE_translator ) noexcept
        : old_SE_translator{ _set_se_translator( new_SE_translator ) } {}
    ~Scoped_SE_Translator() noexcept { _set_se_translator( old_SE_translator ); }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS )
{
    throw SE_Exception( u );
}

void DoTest()
{
    try
    {
        thrower_func( 10 );
    }
    catch( const SE_Exception& e )
    {
        printf( "Caught SE_Exception, error %8.8x\n", e.getSeNumber() );
    }
    catch(...)
    {
        printf( "Caught unexpected SEH exception.\n" );
    }
}
#pragma managed

int main() {
    Scoped_SE_Translator scoped_se_translator{ my_trans_func };

    DoTest();
}
```

```Output
Caught SE_Exception, error c0000094
```

## <a name="see-also"></a>関連項目

[例外処理ルーチン](../../c-runtime-library/exception-handling-routines.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
[unexpected](unexpected-crt.md)<br/>
