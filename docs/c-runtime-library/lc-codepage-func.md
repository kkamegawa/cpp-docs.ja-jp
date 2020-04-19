---
title: ___lc_codepage_func
ms.date: 11/04/2016
api_name:
- ___lc_codepage_func
api_location:
- msvcr120.dll
- msvcr110_clr0400.dll
- msvcr80.dll
- msvcr100.dll
- msvcr90.dll
- msvcr110.dll
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- lc_codepage_func
- ___lc_codepage_func
helpviewer_keywords:
- ___lc_codepage_func
ms.assetid: 6a663bd0-5a63-4a2f-9507-872ec1582aae
ms.openlocfilehash: dbadf8239652f5c96e7177dedd91d340e545b9fe
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70944919"
---
# <a name="___lc_codepage_func"></a>___lc_codepage_func

内部 CRT 関数。 スレッドの現在のコード ページを取得します。

## <a name="syntax"></a>構文

```cpp
UINT ___lc_codepage_func(void);
```

## <a name="return-value"></a>戻り値

スレッドの現在のコード ページ。

## <a name="remarks"></a>解説

`___lc_codepage_func` は、CRT データのスレッド ローカル ストレージから現在のコード ページを取得するために、他の CRT 関数によって使用される内部 CRT 関数です。 この情報は、[_get_current_locale](../c-runtime-library/reference/get-current-locale.md) 関数を使用して取得することもできます。

*コード ページ*は、個別の文字への 1 バイト コードまたは 2 バイト コードのマッピングです。 異なるコード ページには異なる特殊文字が含まれ、それらは通常は 1 つの言語または言語グループ用にカスタマイズされています。 コード ページの詳細については、「 [Code Pages](../c-runtime-library/code-pages.md)」を参照してください。

内部 CRT 関数は実装固有であり、各リリースでの変更の対象です。 コード内では使用しないことをお勧めします。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|`___lc_codepage_func`|crt\src\setlocal.h|

## <a name="see-also"></a>関連項目

[_get_current_locale](../c-runtime-library/reference/get-current-locale.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[_create_locale、_wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)<br/>
[_free_locale](../c-runtime-library/reference/free-locale.md)
