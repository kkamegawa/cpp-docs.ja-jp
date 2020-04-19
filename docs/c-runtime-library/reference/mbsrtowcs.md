---
title: mbsrtowcs
ms.date: 11/04/2016
api_name:
- mbsrtowcs
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
- api-ms-win-crt-convert-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- mbsrtowcs
helpviewer_keywords:
- mbsrtowcs function
ms.assetid: f3a29de8-e36e-425b-a7fa-a258e6d7909d
ms.openlocfilehash: de7b25ea8a520dfe2c9cb26ec8989624b670dcb9
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952047"
---
# <a name="mbsrtowcs"></a>mbsrtowcs

現在のロケールのマルチバイト文字列を、対応するワイド文字の文字列に変換します。マルチバイト文字の途中から再開することが可能です。 この関数のセキュリティが強化されたバージョンについては、「[mbsrtowcs_s](mbsrtowcs-s.md)」をご覧ください。

## <a name="syntax"></a>構文

```C
size_t mbsrtowcs(
   wchar_t *wcstr,
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
);
template <size_t size>
size_t mbsrtowcs(
   wchar_t (&wcstr)[size],
   const char **mbstr,
   sizeof count,
   mbstate_t *mbstate
); // C++ only
```

### <a name="parameters"></a>パラメーター

*wcstr*<br/>
結果として変換されたワイド文字の文字列を格納するアドレス。

*mbstr*<br/>
変換するマルチバイト文字列の場所への間接ポインター。

*count*<br/>
*Wcstr*に変換して格納する最大文字数 (バイト数ではない)。

*mbstate*<br/>
**Mbstate_t**の変換状態オブジェクトへのポインター。 この値が null ポインターの場合、静的な内部変換状態オブジェクトが使用されます。 内部**mbstate_t**オブジェクトはスレッドセーフではないため、常に独自の*mbstate*パラメーターを渡すことをお勧めします。

## <a name="return-value"></a>戻り値

正常に変換された文字数を返します (終端の null 文字があっても含まれません)。 エラーが発生した場合は (size_t) (-1) を返し、 **errno**を EILSEQ に設定します。

## <a name="remarks"></a>Remarks

**Mbsrtowcs**関数は、 *mbstr*によって間接的に指されたマルチバイト文字の文字列を、 *mbstate*に含まれる変換状態を使用して、 *wcstr*が指すバッファーに格納されているワイド文字に変換します。 終端の null マルチバイト文字が検出されるまで、または現在のロケールの有効な文字に対応しないマルチバイトシーケンスが検出されるまで、または*カウント*文字が使用されるまで、文字ごとに変換が続行されます。後. **Mbsrtowcs**が*count*の発生前または発生時にマルチバイト null 文字 (' \ 0 ') を検出すると、それを16ビットの終端 null 文字に変換して停止します。

このため、 *wcstr*のワイド文字の文字列は、 **mbsrtowcs**が変換中にマルチバイトの null 文字を検出した場合にのみ、null で終了します。 *Mbstr*と*wcstr*が指すシーケンスが重なり合う場合、 **mbsrtowcs**の動作は未定義になります。 **mbsrtowcs**は、現在のロケールの LC_TYPE カテゴリの影響を受けます。

**Mbsrtowcs**関数は、 [mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)の再起動によって異なります。 変換状態は、同じまたはその他の再開可能な関数への後続の呼び出しのために*mbstate*に格納されます。 再開可能な関数と再開不可能な関数を混用した場合、結果は未定義です。  たとえば、 **mbsrtowcs**の後続の呼び出しが**mbstowcs**の代わりに使用される場合、アプリケーションでは**mbslen**ではなく**mbsrlen**を使用する必要があります。

*Wcstr*が null ポインターでない場合は、終端の null 文字に到達したために変換が停止した場合、 *mbstr*が指すポインターオブジェクトに null ポインターが割り当てられます。 それ以外の場合、変換された最後のマルチバイト文字がある場合は、その後ろのアドレスが割り当てられます。 これにより、後続の関数呼び出しで、この呼び出しが停止した場所から変換を再開できます。

*Wcstr*引数が null ポインターの場合、count 引数は無視され、 **mbsrtowcs**はコピー先の文字列に必要なサイズをワイド文字*数*で返します。 *Mbstate*が null ポインターの場合、関数はスレッドセーフではない静的な内部**mbstate_t**変換状態オブジェクトを使用します。 文字シーケンス*mbstr*に対応するマルチバイト文字表現がない場合は、-1 が返され、 **errno**が**EILSEQ**に設定されます。

*Mbstr* isa null ポインターの場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、この関数は**errno**を**EINVAL**に設定し、-1 を返します。

C++ では、この関数にテンプレートのオーバーロードがあります。このオーバーロードは、この関数に対応するセキュリティで保護された新しい関数を呼び出します。 詳細については、「 [Secure Template Overloads](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

## <a name="exceptions"></a>例外

**Mbsrtowcs**関数は、この関数が実行されていて、 *mbstate*引数が null ポインターでない限り、現在のスレッドの関数が**setlocale**を呼び出すことができない限り、マルチスレッドセーフです。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**mbsrtowcs**|\<wchar.h>|

## <a name="see-also"></a>関連項目

[データ変換](../../c-runtime-library/data-conversion.md)<br/>
[ロケール](../../c-runtime-library/locale.md)<br/>
[マルチバイト文字のシーケンスの解釈](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)<br/>
[mbrtowc](mbrtowc.md)<br/>
[mbtowc、_mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[mbstowcs、_mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbsinit](mbsinit.md)<br/>
