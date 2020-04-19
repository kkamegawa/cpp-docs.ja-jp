---
title: _countof マクロ
ms.date: 03/22/2018
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
- _countof
- countof
helpviewer_keywords:
- countof macro
- _countof macro
ms.assetid: 86198767-f7e5-4beb-898d-3cbbf60350a3
ms.openlocfilehash: 3debd63da7d218e29f31847034c69d89b4691643
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942686"
---
# <a name="_countof-macro"></a>_countof マクロ

静的に割り当てられた配列内の要素の数を計算します。

## <a name="syntax"></a>構文

```C
#define _countof(array) (sizeof(array) / sizeof(array[0]))
```

### <a name="parameters"></a>パラメーター

*array*<br/>
配列の名前。

## <a name="return-value"></a>戻り値

**Size_t**として表される、配列内の要素の数。

## <a name="remarks"></a>Remarks

**の countof**は、関数に似たプリプロセッサマクロとして実装されています (_c)。 このC++バージョンには、静的に宣言された配列ではなくポインターが渡された場合に、コンパイル時に検出する追加のテンプレート機構があります。

*配列*が実際にはポインターではなく配列であることを確認します。 C では、*配列*がポインターである場合、**は、が誤った結果**を生成します。 でC++は、*配列*がポインターである場合、**の countは**コンパイルに失敗します。  *ポインターに decays*する関数にパラメーターとして渡された配列。つまり、関数内では、を使用して配列の範囲を**決定すること**はできません。

## <a name="requirements"></a>必要条件

|マクロ|必須ヘッダー|
|-----------|---------------------|
|**_countof**|\<stdlib.h>|

## <a name="example"></a>例

```cpp
// crt_countof.cpp
#define _UNICODE
#include <stdio.h>
#include <stdlib.h>
#include <tchar.h>

int main( void )
{
   _TCHAR arr[20], *p;
   printf( "sizeof(arr) = %zu bytes\n", sizeof(arr) );
   printf( "_countof(arr) = %zu elements\n", _countof(arr) );
   // In C++, the following line would generate a compile-time error:
   // printf( "%zu\n", _countof(p) ); // error C2784 (because p is a pointer)

   _tcscpy_s( arr, _countof(arr), _T("a string") );
   // unlike sizeof, _countof works here for both narrow- and wide-character strings
}
```

```Output
sizeof(arr) = 40 bytes
_countof(arr) = 20 elements
```

## <a name="see-also"></a>関連項目

[sizeof 演算子](../../cpp/sizeof-operator.md)<br/>
