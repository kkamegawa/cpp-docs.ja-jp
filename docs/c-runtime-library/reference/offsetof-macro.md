---
title: offsetof マクロ
ms.date: 11/04/2016
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
- offsetof
helpviewer_keywords:
- structure members, offset
- offsetof macro
ms.assetid: f3b4eb16-a882-4d38-afc9-eebd976a7352
ms.openlocfilehash: 278fca89046fcfc98e8c3ff726918cb4319e4ab0
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951259"
---
# <a name="offsetof-macro"></a>offsetof マクロ

親構造体の先頭からメンバーのオフセットを取得します。

## <a name="syntax"></a>構文

```C
size_t offsetof(
   structName,
   memberName
);
```

### <a name="parameters"></a>パラメーター

*structName*<br/>
親データ構造体の名前。

*memberName*<br/>
オフセットを決定する親データ構造体のメンバーの名前。

## <a name="return-value"></a>戻り値

**offsetof**は、親データ構造体の先頭から、指定されたメンバーのオフセットをバイト単位で返します。 ビット フィールドには定義されません。

## <a name="remarks"></a>Remarks

**Offsetof**マクロは、 *structName*で指定された構造体の先頭からのバイト*単位のオフセット*を**size_t**型の値として返します。 **Struct**キーワードを使用して型を指定できます。

> [!NOTE]
> **offsetof**は関数ではなく、C プロトタイプを使用して記述することはできません。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**offsetof**|\<stddef.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[メモリ割り当て](../../c-runtime-library/memory-allocation.md)<br/>
