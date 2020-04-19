---
title: _CrtDbgBreak
ms.date: 11/04/2016
api_name:
- _CrtDbgBreak
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
- _CrtDbgBreak
- CrtDbgBreak
helpviewer_keywords:
- CrtDbgBreak function
- _CrtDbgBreak function
ms.assetid: 01f8b4a2-a2c7-4e1f-9f39-e573b4a7871f
ms.openlocfilehash: 9471b1a93abd9777c3a53c54c2517e59896d8160
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942583"
---
# <a name="_crtdbgbreak"></a>_CrtDbgBreak

特定のコード行にブレークポイントを設定します。 (デバッグ モードでのみ使用されます)

## <a name="syntax"></a>構文

```C
void _CrtDbgBreak( void );
```

## <a name="return-value"></a>戻り値

戻り値がありません。

## <a name="remarks"></a>Remarks

**_CrtDbgBreak**関数は、関数が存在する特定のコード行にデバッグブレークポイントを設定します。 この関数はデバッグモードでのみ使用され、以前に定義された **_debug**に依存します。

フックをサポートするその他のランタイム関数の使い方の詳細と、独自のクライアント定義フック関数の記述方法については、「[Writing Your Own Debug Hook Functions](/visualstudio/debugger/debug-hook-function-writing)」 (独自のデバッグ フック関数を記述する) を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_CrtDbgBreak**|\<CRTDBG.h>|

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[__debugbreak](../../intrinsics/debugbreak.md)<br/>
