---
title: mbrtoc16、mbrtoc323
ms.date: 10/22/2019
api_name:
- mbrtoc16
- mbrtoc32
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
- mbrtoc16
- mbrtoc32
- uchar/mbrtoc16
- uchar/mbrtoc32
helpviewer_keywords:
- mbrtoc16 function
- mbrtoc32 function
ms.assetid: 099ade4d-56f7-4e61-8b45-493f1d7a64bd
ms.openlocfilehash: 793eadf433f3117d89b4f0dc7c8397762405406b
ms.sourcegitcommit: 0a5518fdb9d87fcc326a8507ac755936285fcb94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2019
ms.locfileid: "72811137"
---
# <a name="mbrtoc16-mbrtoc32"></a>mbrtoc16、mbrtoc32

文字列内の最初の UTF-8 マルチバイト文字を等価の UTF-16 または 32 UTF-8 文字に変換します。

## <a name="syntax"></a>構文

```C
size_t mbrtoc16(
   char16_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);

size_t mbrtoc32(
   char32_t* destination,
   const char* source,
   size_t max_bytes,
   mbstate_t* state
);
```

### <a name="parameters"></a>パラメーター

*宛先*の\
変換する UTF-8 マルチバイト文字に相当する**char16_t**または**char32_t**へのポインター。 Null の場合、関数は値を格納しません。

*ソース*\
変換する UTF-8 マルチバイト文字の文字列へのポインター。

*max_bytes*\
変換する文字を検査する*ソース*内の最大バイト数。 この引数には、*ソース*の残りのバイト数と、null 終端記号を含むバイト数の間の値を指定する必要があります。

*状態*\
UTF-8 マルチバイト文字列を1つ以上の出力文字に解釈するために使用される**mbstate_t**変換状態オブジェクトへのポインター。

## <a name="return-value"></a>戻り値

成功した場合、現在の*状態*の値に基づいて、次の条件が適用される最初の値が返されます。

|[値]|条件|
|-----------|---------------|
|0|*Source*から変換された次の*max_bytes*文字数は、null ワイド文字に相当します。これは、 *destination*が null でない場合に格納される値です。<br /><br /> *状態*には初期のシフト状態が含まれます。|
|1から*max_bytes*までの範囲|返される値は、有効なマルチバイト文字を完成させる*ソース*のバイト数です。 変換*先*が null でない場合、変換されたワイド文字が格納されます。|
|-3|前の関数の呼び出しの結果として返される次のワイド文字が、 *destination*が null でない場合、*変換先*に格納されています。 関数のこの呼び出しでは、*ソース*からのバイトは使用されません。<br /><br /> *ソース*が1つ以上のワイド文字を表す必要がある utf-8 マルチバイト文字 (サロゲートペアなど) を指している場合は、次の関数呼び出しが追加の文字を書き出すように*state*値が更新されます。|
|-2|次の*max_bytes*バイトは、不完全であるが有効な utf-8 マルチバイト文字を表します。 値が*変換先*に格納されていません。 この結果は、 *max_bytes*が0の場合に発生する可能性があります。|
|-1|エンコーディング エラーが発生しました。 次の*max_bytes*以下のバイトは、完全かつ有効な utf-8 マルチバイト文字に寄与しません。 値が*変換先*に格納されていません。<br /><br /> **EILSEQ**は**errno**に格納され、変換状態値の*状態*は指定されていません。|

## <a name="remarks"></a>Remarks

**Mbrtoc16**関数は、 *source*から最大*max_bytes*バイトを読み取り、最初の完全な有効な utf-8 マルチバイト文字を検索してから、等価の utf-16 文字を*変換先*に格納します。 文字にサロゲートペアなどの複数の UTF-16 出力文字が必要な場合、 *state*値は、次に**mbrtoc16**を呼び出したときに、次の utf-16 文字を*変換先*に格納するように設定されます。 **Mbrtoc32**関数は同じですが、出力は32文字として格納されます。

*Source*が null の場合、これらの関数は、 *source*に対して**null**の引数を使用して行われた呼び出しに相当するもの *`""` を返し*、 *max_bytes*の場合は1を返します。 *Destination*と*max_bytes*の渡された値は無視されます。

*Source*が null でない場合、関数は文字列の先頭から開始し、最大*max_bytes*バイトを検査して、次の utf-8 マルチバイト文字 (シフトシーケンスを含む) を完了するために必要なバイト数を決定します。 検査されたバイトに有効な UTF-8 マルチバイト文字が含まれている場合、関数はその文字を等価の16ビットまたは32ビットのワイド文字に変換します。 *Destination*が null でない場合、関数は最初の (および場合によっては唯一の) 結果の文字を変換先に格納します。 追加の出力文字が必要な場合、値は*状態*で設定されるため、後続の関数の呼び出しで追加の文字が出力され、値-3 が返されます。 これ以上出力文字が不要な場合は、 *state*が初期のシフト状態に設定されます。

UTF-8 以外のマルチバイト文字を UTF-16 LE 文字に変換するには、 [mbrtowc](mbrtowc.md)、 [mbtowc、または _mbtowc_l](mbtowc-mbtowc-l.md)関数を使用します。

## <a name="requirements"></a>［要件］

|機能|C ヘッダー|C++ ヘッダー|
|--------------|--------------|------------------|
|**mbrtoc16**、 **mbrtoc32**|\<uchar.h>|\<cuchar>|

互換性の詳細については、「[互換性](../compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ変換](../data-conversion.md)の\
[ロケール](../locale.md)\
[マルチバイト文字のシーケンスの解釈](../interpretation-of-multibyte-character-sequences.md)\
[c16rtomb、c32rtomb](c16rtomb-c32rtomb1.md)\
[mbrtowc](mbrtowc.md)\
[mbsrtowcs](mbsrtowcs.md)\
[mbsrtowcs_s](mbsrtowcs-s.md)
