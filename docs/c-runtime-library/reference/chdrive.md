---
title: _chdrive
ms.date: 11/04/2016
api_name:
- _chdrive
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
- api-ms-win-crt-filesystem-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- chdrive
- _chdrive
helpviewer_keywords:
- drives, changing
- _chdrive function
- chdrive function
ms.assetid: 212a1a4b-4fa8-444e-9677-7fca4c8c47e3
ms.openlocfilehash: 3ee292c03c9d31944e0a555c2159d7a5dd2cd0eb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939240"
---
# <a name="_chdrive"></a>_chdrive

現在の作業ドライブを変更します。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _chdrive(
   int drive
);
```

### <a name="parameters"></a>パラメーター

*駆動*<br/>
現在の作業ドライブを指定する 1 ～ 26 の整数 (1 = A、2 = B など)。

## <a name="return-value"></a>戻り値

現在の作業ドライブが正常に変更された場合はゼロ (0)、それ以外の場合は -1。

## <a name="remarks"></a>Remarks

*Drive*が 1 ~ 26 の範囲内にない場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **_chdrive**関数は-1 を返し、 **errno**は**EACCES**に設定され、 **_doserrno**は**ERROR_INVALID_DRIVE**に設定されます。

**_chdrive** 関数は、スレッド セーフではない **SetCurrentDirectory** 関数に依存するため、スレッド セーフではありません。 マルチスレッド アプリケーションで **_chdrive** を安全に使用するには、独自のスレッド同期を用意する必要があります。 詳細については、「 [SetCurrentDirectory](/windows/win32/api/winbase/nf-winbase-setcurrentdirectory)」を参照してください。

**_chdrive** 関数は現在の作業ドライブのみを変更します。 **_chdir** は現在の作業ディレクトリを変更します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_chdrive**|\<direct.h>|

詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

[_getdrive](getdrive.md) の例を参照してください。

## <a name="see-also"></a>関連項目

[ディレクトリ制御](../../c-runtime-library/directory-control.md)<br/>
[_chdir、_wchdir](chdir-wchdir.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getcwd、_wgetcwd](getcwd-wgetcwd.md)<br/>
[_getdrive](getdrive.md)<br/>
[_mkdir、_wmkdir](mkdir-wmkdir.md)<br/>
[_rmdir、_wrmdir](rmdir-wrmdir.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
