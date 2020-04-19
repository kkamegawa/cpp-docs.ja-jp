---
title: 例外処理と CLR での動作の違い
ms.date: 11/04/2016
helpviewer_keywords:
- EXCEPTION_CONTINUE_EXECUTION macro
- set_se_translator function
ms.assetid: 2e7e8daf-d019-44b0-a51c-62d7aaa89104
ms.openlocfilehash: ae745cfb96f4efe1ede7e3fc762842f9e4d63323
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400579"
---
# <a name="differences-in-exception-handling-behavior-under-clr"></a>/CLR における例外処理動作の相違点

[マネージ例外の使用で基本的な概念](../dotnet/basic-concepts-in-using-managed-exceptions.md)マネージ アプリケーションでの例外処理について説明します。 このトピックでは、例外処理、およびいくつかの制限の標準の動作の相違点は詳しく説明します。 詳細については、次を参照してください。 [_set_se_translator 関数](../c-runtime-library/reference/set-se-translator.md)します。

##  <a name="vcconjumpingoutofafinallyblock"></a> ジャンプ、Finally ブロック

ネイティブ C で/C++コードでは、警告を生成しますが、構造化例外処理（SEH）を使用して__**finally**ブロックからジャンプできます。  [/clr](../build/reference/clr-common-language-runtime-compilation.md)の移動、**finallyに**ブロックが発生したエラー。

```cpp
// clr_exception_handling_4.cpp
// compile with: /clr
int main() {
   try {}
   finally {
      return 0;   // also fails with goto, break, continue
    }
}   // C3276
```

##  <a name="vcconraisingexceptionswithinanexceptionfilter"></a> 例外フィルター内で例外を発生させる

処理中に例外が発生したとき、[例外フィルター](../cpp/writing-an-exception-filter.md) 、マネージ コード内と、例外はキャッチ フィルター返します 0 として扱われます。

入れ子になった例外が発生した場所、ネイティブ コードの動作とは異なり、これは、 **ExceptionRecord**フィールドに、 **EXCEPTION_RECORD**構造 (によって返される[GetExceptionInformation](/windows/desktop/Debug/getexceptioninformation)) が設定されていると、 **ExceptionFlags** 0x10 ビットをフィールドに設定します。 次の例は、この動作の違いを示しています。

```cpp
// clr_exception_handling_5.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

#ifndef false
#define false 0
#endif

int *p;

int filter(PEXCEPTION_POINTERS ExceptionPointers) {
   PEXCEPTION_RECORD ExceptionRecord =
                     ExceptionPointers->ExceptionRecord;

   if ((ExceptionRecord->ExceptionFlags & 0x10) == 0) {
      // not a nested exception, throw one
      *p = 0; // throw another AV
   }
   else {
      printf("Caught a nested exception\n");
      return 1;
    }

   assert(false);

   return 0;
}

void f(void) {
   __try {
      *p = 0;   // throw an AV
   }
   __except(filter(GetExceptionInformation())) {
      printf_s("We should execute this handler if "
                 "compiled to native\n");
    }
}

int main() {
   __try {
      f();
   }
   __except(1) {
      printf_s("The handler in main caught the "
               "exception\n");
    }
}
```

### <a name="output"></a>Output

```Output
Caught a nested exception
We should execute this handler if compiled to native
```

##  <a name="vccondisassociatedrethrows"></a> 分離再スロー

**/clr**は catch ハンドラーが (関連付けを解除 rethrow と呼ばれます) の外部で例外を再スローをサポートしていません。 この種類の例外が扱われるとして標準の C++ 再スローします。 アクティブなマネージ例外がある場合に、分離の再スローが発生した場合は、例外が C++ 例外としてラップされ、再スローされます。 この種類の例外は、型の例外としてのみキャッチできます<xref:System.Runtime.InteropServices.SEHException>します。

次の例では、マネージ例外として、C++ 例外を再スローを示しています。

```cpp
// clr_exception_handling_6.cpp
// compile with: /clr
using namespace System;
#include <assert.h>
#include <stdio.h>

void rethrow( void ) {
   // This rethrow is a dissasociated rethrow.
   // The exception would be masked as SEHException.
   throw;
}

int main() {
   try {
      try {
         throw gcnew ApplicationException;
      }
      catch ( ApplicationException^ ) {
         rethrow();
         // If the call to rethrow() is replaced with
         // a throw statement within the catch handler,
         // the rethrow would be a managed rethrow and
         // the exception type would remain
         // System::ApplicationException
      }
   }

    catch ( ApplicationException^ ) {
      assert( false );

      // This will not be executed since the exception
      // will be masked as SEHException.
    }
   catch ( Runtime::InteropServices::SEHException^ ) {
      printf_s("caught an SEH Exception\n" );
    }
}
```

### <a name="output"></a>Output

```Output
caught an SEH Exception
```

##  <a name="vcconexceptionfiltersandexception_continue_execution"></a> 例外フィルターと EXCEPTION_CONTINUE_EXECUTION

フィルターを返す場合`EXCEPTION_CONTINUE_EXECUTION`、マネージ アプリケーションでは扱われます、フィルターを返す場合、`EXCEPTION_CONTINUE_SEARCH`します。 これらの定数の詳細については、[try-except ステートメント](../cpp/try-except-statement.md)を参照してください。

次の例では、この違いを示しています。

```cpp
// clr_exception_handling_7.cpp
#include <windows.h>
#include <stdio.h>
#include <assert.h>

int main() {
   int Counter = 0;
   __try {
      __try  {
         Counter -= 1;
         RaiseException (0xe0000000|'seh',
                         0, 0, 0);
         Counter -= 2;
      }
      __except (Counter) {
         // Counter is negative,
         // indicating "CONTINUE EXECUTE"
         Counter -= 1;
      }
    }
    __except(1) {
      Counter -= 100;
   }

   printf_s("Counter=%d\n", Counter);
}
```

### <a name="output"></a>Output

```Output
Counter=-3
```

##  <a name="vcconthe_set_se_translatorfunction"></a> _Set_se_translator 関数

変換関数はの設定への呼び出しによって`_set_se_translator`、アンマネージ コードでキャッチのみに影響を与えます。 次の例では、この制限を示しています。

```cpp
// clr_exception_handling_8.cpp
// compile with: /clr /EHa
#include <iostream>
#include <windows.h>
#include <eh.h>
#pragma warning (disable: 4101)
using namespace std;
using namespace System;

#define MYEXCEPTION_CODE 0xe0000101

class CMyException {
public:
   unsigned int m_ErrorCode;
   EXCEPTION_POINTERS * m_pExp;

   CMyException() : m_ErrorCode( 0 ), m_pExp( NULL ) {}

   CMyException( unsigned int i, EXCEPTION_POINTERS * pExp )
         : m_ErrorCode( i ), m_pExp( pExp ) {}

   CMyException( CMyException& c ) : m_ErrorCode( c.m_ErrorCode ),
                                      m_pExp( c.m_pExp ) {}

   friend ostream& operator <<
                 ( ostream& out, const CMyException& inst ) {
      return out <<  "CMyException[\n" <<
             "Error Code: " << inst.m_ErrorCode <<  "]";
    }
};

#pragma unmanaged
void my_trans_func( unsigned int u, PEXCEPTION_POINTERS pExp ) {
   cout <<  "In my_trans_func.\n";
   throw CMyException( u, pExp );
}

#pragma managed
void managed_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE, 0, 0, 0 );
   }
   catch ( CMyException x ) {}
   catch ( ... ) {
      printf_s("This is invoked since "
               "_set_se_translator is not "
               "supported when /clr is used\n" );
    }
}

#pragma unmanaged
void unmanaged_func() {
   try  {
      RaiseException( MYEXCEPTION_CODE,
                      0, 0, 0 );
   }
   catch ( CMyException x ) {
      printf("Caught an SEH exception with "
             "exception code: %x\n", x.m_ErrorCode );
    }
    catch ( ... ) {}
}

// #pragma managed
int main( int argc, char ** argv ) {
   _set_se_translator( my_trans_func );

   // It does not matter whether the translator function
   // is registered in managed or unmanaged code
   managed_func();
   unmanaged_func();
}
```

### <a name="output"></a>Output

```Output
This is invoked since _set_se_translator is not supported when /clr is used
In my_trans_func.
Caught an SEH exception with exception code: e0000101
```

## <a name="see-also"></a>関連項目

[例外処理](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[例外処理](../cpp/exception-handling-in-visual-cpp.md)
