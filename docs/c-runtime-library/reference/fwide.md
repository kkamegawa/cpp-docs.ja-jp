---
title: fwide
ms.date: 11/04/2016
api_name:
- fwide
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
- fwide
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: 2e986ba5ab28072f4933e555eea32a5893c8df56
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956219"
---
# <a name="fwide"></a>fwide

未実装。

## <a name="syntax"></a>構文

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
**ファイル**構造へのポインター (無視)。

*モード*<br/>
ストリームの新しい幅: ワイド文字の場合は正、バイトの場合は負、変更しない場合は 0 にします (この値は無視されます)。

## <a name="return-value"></a>戻り値

現在、この関数は、*モード*を返すだけです。

## <a name="remarks"></a>Remarks

この関数の現在のバージョンは、標準に準拠していません。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。