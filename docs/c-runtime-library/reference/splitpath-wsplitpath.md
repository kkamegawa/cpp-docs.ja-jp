---
title: _splitpath、_wsplitpath
ms.date: 11/04/2016
api_name:
- _wsplitpath
- _splitpath
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
- wsplitpath
- _splitpath
- splitpath
- _wsplitpath
- _tsplitpath
helpviewer_keywords:
- _splitpath function
- pathnames
- wsplitpath function
- splitpath function
- _wsplitpath function
- tsplitpath function
- path names
- _tsplitpath function
ms.assetid: 32bd76b5-1385-4ee8-a64c-abcb541cd2e4
ms.openlocfilehash: a502977faf91d744868c4aef79b3a40ca240a90f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958041"
---
# <a name="_splitpath-_wsplitpath"></a>_splitpath、_wsplitpath

パス名をコンポーネントに分割します。 これらの関数のセキュリティを強化したバージョンについては、「[_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)」をご覧ください。

## <a name="syntax"></a>構文

```C
void _splitpath(
   const char *path,
   char *drive,
   char *dir,
   char *fname,
   char *ext
);
void _wsplitpath(
   const wchar_t *path,
   wchar_t *drive,
   wchar_t *dir,
   wchar_t *fname,
   wchar_t *ext
);
```

### <a name="parameters"></a>パラメーター

*path*<br/>
完全なパス。

*駆動*<br/>
ドライブ文字、コロン ( **:** ) の順に並べます。 ドライブ文字が不要な場合は、このパラメーターに**NULL**を渡すことができます。

*エイリアス*<br/>
末尾のスラッシュを含むディレクトリ パス。 スラッシュ ( **/** )、円記号 ( **\\** )、またはその両方を使用できます。 ディレクトリパスが不要な場合は、このパラメーターに**NULL**を渡すことができます。

*fname*<br/>
基本ファイル名 (拡張子なし)。 ファイル名が不要な場合は、このパラメーターに**NULL**を渡すことができます。

*ext*<br/>
先頭のピリオド ( **.** ) を含むファイル名の拡張子。 ファイル名の拡張子が不要な場合は、このパラメーターに**NULL**を渡すことができます。

## <a name="remarks"></a>Remarks

**_Splitpath**関数は、パスを4つのコンポーネントに分割します。 **_splitpath**は、現在使用中のマルチバイトコードページに従ってマルチバイト文字シーケンスを認識し、マルチバイト文字列の引数を適切な方法で自動的に処理します。 **_wsplitpath**は、 **_splitpath**のワイド文字バージョンです。 **_wsplitpath**の引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです。

**セキュリティに関するメモ**これらの関数は、バッファー オーバーランの問題によって潜在的な脅威を引き起こすことがあります。 バッファー オーバーランは、システムを攻撃するときによく使用される方法であり、その結果、認められていない権限が昇格されます。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。 これらの関数のセキュリティを強化したバージョンについては、「[_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)」をご覧ください。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath**|**_splitpath**|**_splitpath**|**_wsplitpath**|

完全パスの各コンポーネントは、個別のバッファーに格納されます。マニフェスト**定数 (** **_MAX_DIR**、 **_MAX_FNAME**、および stdlib.h> で定義されて**いる)。** H) 各ファイルコンポーネントの最大サイズを指定します。 対応するマニフェスト定数よりも大きいファイル コンポーネントでは、ヒープ破損が発生します。

各バッファーは、バッファー オーバーランの発生を回避するために、対応するマニフェスト定数と同じ大きさである必要があります。

マニフェスト定数の値を次の表に示します。

|名前|値|
|----------|-----------|
|**ドライブ (_S)**|3|
|**_MAX_DIR**|256|
|**_MAX_FNAME**|256|
|**拡張 (_S)**|256|

完全なパスにコンポーネント (たとえばファイル名) が含まれていない場合、 **_splitpath**は対応するバッファーに空の文字列を割り当てます。

不要な*パス*以外のパラメーターについては、 **NULL**を **_splitpath**に渡すことができます。

*Path*が**NULL**の場合は、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。 実行の継続が許可された場合、 **errno**は**einval**に設定され、関数は**einval**を返します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_splitpath**|\<stdlib.h>|
|**_wsplitpath**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[_makepath](makepath-wmakepath.md)」の例をご覧ください。

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[_splitpath_s、_wsplitpath_s](splitpath-s-wsplitpath-s.md)<br/>
