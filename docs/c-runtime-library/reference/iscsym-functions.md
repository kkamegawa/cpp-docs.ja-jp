---
title: iscsym、iscsymf、__iscsym、__iswcsym、__iscsymf、__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l
ms.date: 11/04/2016
api_name:
- _iswcsym_l
- __iswcsym
- __iscsym
- _iswcsymf_l
- _iscsym_l
- __iswcsymf
- __iscsymf
- _iscsymf_l
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _iswcsym_l
- _iswcsymf_l
- iscsymf
- iswcsymf
- __iswcsym
- __iswcsymf
- iscsym
- iswcsym
- __iscsym
- _iscsym_l
- _iscsymf_l
- __iscsymf
- ctype/iscsym
- ctype/iscsymf
- ctype/__iscsym
- ctype/__iscsymf
- ctype/__iscsym_l
- ctype/__iscsymf_l
- ctype/__iswcsym
- ctype/__iswcsymf
- ctype/__iswcsym_l
- ctype/__iswcsymf_l
helpviewer_keywords:
- iscsymf_l function
- iswsym_l function
- _iswcsym_l function
- iscsym_l function
- _iscsymf_l function
- _iswcsymf_l function
- _iscsym_l function
- __iscsym function
- __iswcsymf function
- iswsymf_l function
- __iscsymf function
- __iswcsym function
- iscsym function
- iscsymf function
ms.assetid: 944dfb99-f2b8-498c-9f55-dbcf370d0a2c
ms.openlocfilehash: bc38e72818446a94a51a37b8df5c8c8582971b3f
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857763"
---
# <a name="iscsym-iscsymf-__iscsym-__iswcsym-__iscsymf-__iswcsymf-_iscsym_l-_iswcsym_l-_iscsymf_l-_iswcsymf_l"></a>iscsym、iscsymf、__iscsym、__iswcsym、__iscsymf、__iswcsymf、_iscsym_l、_iswcsym_l、_iscsymf_l、_iswcsymf_l

整数が識別子に使用できる文字を表すかどうかを判別します。

## <a name="syntax"></a>構文

```C
int __iscsym(
   int c
);
int __iswcsym(
   wint_t c
);
int __iscsymf(
   int c
);
int __iswcsymf(
   wint_t c
);
int _iscsym_l(
   int c,
   _locale_t locale
);
int _iswcsym_l(
   wint_t c,
   _locale_t locale
);
int _iscsymf_l(
   int c,
   _locale_t locale
);
int _iswcsymf_l(
   wint_t c,
   _locale_t locale
);
#define iscsym __iscsym
#define iscsymf __iscsymf
```

### <a name="parameters"></a>パラメーター

*c*<br/>
テストする整数。 関数のナロー文字バージョンでは、 *c*は0-255 の範囲内である必要があります。

*locale*<br/>
使用するロケール。

## <a name="return-value"></a>戻り値

*C*が文字、アンダースコア、または数字の場合、 **__iscsym**と **__iswcsym**の両方で0以外の値が返されます。 *C*が文字またはアンダースコアの場合、 **__iscsymf**と **__iswcsymf**の両方で0以外の値が返されます。 これらの各ルーチンは、 *c*がテスト条件を満たしていない場合は0を返します。 **_L**サフィックスを持つこれらの関数のバージョンは同じですが、ロケールに依存する動作に現在のロケールではなく渡された*ロケール*を使用する点が異なります。 詳細については、「 [Locale](../../c-runtime-library/locale.md)」を参照してください。

## <a name="remarks"></a>Remarks

これらのルーチンは、プリプロセッサ マクロ _CTYPE_DISABLE_MACROS が定義されていない場合、マクロとして定義されます。 これらのルーチンのマクロ バージョンを使用する際には、引数を複数回評価できます。 引数リスト内で副作用がある式を使用するときにはご注意ください。

旧バージョンとの互換性のために、 **iscsym**と**iscsymf**は[ &#95; &#95;、&#95; STDC](../../preprocessor/predefined-macros.md)が定義されていない場合、または0として定義されている場合にのみ、マクロとして定義それ以外の場合は未定義です。

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**iscsym**、 **iscsymf**、 **__iscsym**、 **__iswcsym**、 **__iscsymf**、 **__iswcsymf**、 **_iscsym_l**、 **_iswcsym_l**、 **_iscsymf_l**、 **_iswcsymf_l**|C: \<ctype.h><br /><br /> C++: \<cctype> または \<ctype.h>|

**Iscsym**、 **iscsymf**、 **__iscsym**、 **__iswcsym**、 **__iscsymf**、 **__iswcsymf**、 **_iscsym_l**、 **_iswcsym_l**、 **_iscsymf_l**、および **_iswcsymf_l**ルーチンは、Microsoft 固有のものです。 互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>参照

[文字分類](../../c-runtime-library/character-classification.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[is、isw 系ルーチン](../../c-runtime-library/is-isw-routines.md)<br/>
