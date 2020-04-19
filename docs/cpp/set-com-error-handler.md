---
title: _set_com_error_handler
ms.date: 11/04/2016
helpviewer_keywords:
- _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
ms.openlocfilehash: 226dce24de68edd66ca68c43e41ce0cb5b8a1b48
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857295"
---
# <a name="_set_com_error_handler"></a>_set_com_error_handler

COM のエラー処理に使用する既定の関数を置き換えます。 **_set_com_error_handler**は Microsoft 固有です。

## <a name="syntax"></a>構文

```
void __stdcall _set_com_error_handler(
   void (__stdcall *pHandler)(
      HRESULT hr,
      IErrorInfo* perrinfo
   )
);
```

#### <a name="parameters"></a>パラメーター

*pHandler*<br/>
置換する関数へのポインター。

*hr*<br/>
HRESULT 情報。

*perrinfo*<br/>
`IErrorInfo` オブジェクト。

## <a name="remarks"></a>Remarks

既定では、 [_com_raise_error](../cpp/com-raise-error.md)はすべての com エラーを処理します。 この動作を変更するには、 **_set_com_error_handler**を使用して独自のエラー処理関数を呼び出します。

置換関数には `_com_raise_error` のシグネチャと等価のシグニチャが必要です。

## <a name="example"></a>使用例

```cpp
// _set_com_error_handler.cpp
// compile with /EHsc
#include <stdio.h>
#include <comdef.h>
#include <comutil.h>

// Importing ado dll to attempt to establish an ado connection.
// Not related to _set_com_error_handler
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")

void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)
{
   throw "Unable to establish the connection!";
}

int main()
{
   _set_com_error_handler(_My_com_raise_error);
   _bstr_t bstrEmpty(L"");
   _ConnectionPtr Connection = NULL;
   try
   {
      Connection.CreateInstance(__uuidof(Connection));
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);
   }
   catch(char* errorMessage)
   {
      printf("Exception raised: %s\n", errorMessage);
   }

   return 0;
}
```

```Output
Exception raised: Unable to establish the connection!
```

## <a name="requirements"></a>要件

**ヘッダー:** \<comdef. h >

**Lib:** **/Zc: wchar_t**コンパイラオプションが指定されている場合 (既定)、comsuppw または comsuppw を使用します。 **/Zc: wchar_t**コンパイラオプションが指定されている場合は、comsupp .lib を使用します。 IDE でこのオプションを設定する方法など、詳細については、「 [/zc: wchar_t (Wchar_t はネイティブ型)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)」を参照してください。

## <a name="see-also"></a>参照

[コンパイラ COM のグローバル関数](../cpp/compiler-com-global-functions.md)
