---
title: outp、outp、_outp、_outpw、_outpd
description: Microsoft C ランタイムライブラリ (CRT) の廃止された outp、outp、_outp、_outpw、および _outpd 関数について説明します。
ms.date: 12/09/2019
api_name:
- _outpd
- _outp
- _outpw
- outp
- outpw
api_location:
- msvcrt.dll
- msvcr100.dll
- msvcr120.dll
- msvcr90.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _outpw
- _outpd
- _outp
- outp
- outpw
- outpd
helpviewer_keywords:
- outpw function
- words
- _outpd function
- outpd function
- outp function
- ports, writing bytes at
- bytes, writing to ports
- words, writing to ports
- double words
- double words, writing to ports
- _outpw function
- _outp function
ms.assetid: c200fe22-41f6-46fd-b0be-ebb805b35181
ms.openlocfilehash: 03d3df0bae9c2fa3cdd107f3c0de65105077c401
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988377"
---
# <a name="outp-outpw-_outp-_outpw-_outpd"></a>outp、outp、_outp、_outpw、_outpd

ポート、バイト (`outp`、`_outp`)、ワード (`outpw`、`_outpw`)、またはダブルワード (`_outpd`) に出力します。

> [!IMPORTANT]
> これらは古い関数です。 Visual Studio 2015 以降では、CRT で使用できません。  
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```cpp
int _outp(
   unsigned short port,
   int databyte
);
unsigned short _outpw(
   unsigned short port,
   unsigned short dataword
);
unsigned long _outpd(
   unsigned short port,
   unsigned long dataword
);
```

### <a name="parameters"></a>パラメーター

*ポート*\
ポート番号です。

*databyte、dataword*\
出力値。

## <a name="return-value"></a>戻り値

関数は、出力データを返します。 エラーの戻り値はありません。

## <a name="remarks"></a>Remarks

`_outp`、 `_outpw`、 `_outpd` の各関数は、指定された出力ポートへそれぞれバイト、ワード、ダブルワードを 1 つ書き込みます。 *port* 引数は、0 - 65,535 の任意の符号なし整数です。 *databyte* は、0 - 255 の任意の整数です。*dataword* は、整数、符号なし短整数、および符号なし長整数の範囲の任意の値です。

これらの関数は I/O ポートへ直接書き込まれるため、ユーザー コードで使用できません。 これらのオペレーティング システムでの I/O ポートの使用方法については、MSDN で「Serial Communications in Win32 (Win32 のシリアル通信)」を検索してください。

`outp` と `outpw` の名前は、`_outp` および `_outpw` 関数の古い名前で、非推奨とされています。 詳細については、「 [POSIX 関数名](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md#posix-function-names)」を参照してください。

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|`_outp`|\<conio.h>|
|`_outpw`|\<conio.h>|
|`_outpd`|\<conio.h>|

互換性について詳しくは、「[互換性](../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>参照

[コンソール入出力とポート入出力](../c-runtime-library/console-and-port-i-o.md)\
[sct.inp、inpw、_inp、_inpw、_inpd](../c-runtime-library/inp-inpw-inpd.md)
