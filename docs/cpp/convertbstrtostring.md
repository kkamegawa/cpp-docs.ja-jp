---
title: ConvertBSTRToString
ms.date: 11/04/2016
f1_keywords:
- ConvertBSTRToString
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
ms.openlocfilehash: df123dc218aa770a67536bf1bad7d8bafcf4c318
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392324"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString

**Microsoft 固有の仕様**

変換を`BSTR`値を`char *`します。

## <a name="syntax"></a>構文

```
char* __stdcall ConvertBSTRToString(BSTR pSrc);
```

#### <a name="parameters"></a>パラメーター

*pSrc*<br/>
BSTR 変数。

## <a name="remarks"></a>Remarks

**ConvertBSTRToString**する必要がありますを削除する文字列を割り当てます。

## <a name="example"></a>例

```cpp
// ConvertBSTRToString.cpp
#include <comutil.h>
#include <stdio.h>

#pragma comment(lib, "comsuppw.lib")

int main() {
   BSTR bstrText = ::SysAllocString(L"Test");
   wprintf_s(L"BSTR text: %s\n", bstrText);

   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);
   printf_s("char * text: %s\n", lpszText2);

   SysFreeString(bstrText);
   delete[] lpszText2;
}
```

```Output
BSTR text: Test
char * text: Test
```

**Microsoft 固有の仕様はここまで**

## <a name="requirements"></a>必要条件

**Header:** \<comutil.h >

**Lib:** comsuppw.lib または comsuppwd.lib (詳細は「[/Zc:wchar_t (wchar_t をネイティブ型として認識)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)」を参照してください)

## <a name="see-also"></a>関連項目

[コンパイラ COM のグローバル関数](../cpp/compiler-com-global-functions.md)