---
title: _splitpath_s、_wsplitpath_s
ms.date: 11/04/2016
api_name:
- _wsplitpath_s
- _splitpath_s
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
- ntoskrnl.exe
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _wsplitpath_s
- splitpath_s
- _splitpath_s
- wsplitpath_s
helpviewer_keywords:
- splitpath_s function
- pathnames
- _splitpath_s function
- _wsplitpath_s function
- path names
- wsplitpath_s function
ms.assetid: 30fff3e2-cd00-4eb6-b5a2-65db79cb688b
ms.openlocfilehash: 8eeb6a0f43827578c5d5ba900c35a3ac30f4ae7c
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73625837"
---
# <a name="_splitpath_s-_wsplitpath_s"></a>_splitpath_s、_wsplitpath_s

パス名をコンポーネントに分割します。 これらは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_splitpath、_wsplitpath](splitpath-wsplitpath.md) です。

## <a name="syntax"></a>構文

```C
errno_t _splitpath_s(
   const char * path,
   char * drive,
   size_t driveNumberOfElements,
   char * dir,
   size_t dirNumberOfElements,
   char * fname,
   size_t nameNumberOfElements,
   char * ext,
   size_t extNumberOfElements
);
errno_t _wsplitpath_s(
   const wchar_t * path,
   wchar_t * drive,
   size_t driveNumberOfElements,
   wchar_t *dir,
   size_t dirNumberOfElements,
   wchar_t * fname,
   size_t nameNumberOfElements,
   wchar_t * ext,
   size_t extNumberOfElements
);
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _splitpath_s(
   const char *path,
   char (&drive)[drivesize],
   char (&dir)[dirsize],
   char (&fname)[fnamesize],
   char (&ext)[extsize]
); // C++ only
template <size_t drivesize, size_t dirsize, size_t fnamesize, size_t extsize>
errno_t _wsplitpath_s(
   const wchar_t *path,
   wchar_t (&drive)[drivesize],
   wchar_t (&dir)[dirsize],
   wchar_t (&fname)[fnamesize],
   wchar_t (&ext)[extsize]
); // C++ only
```

### <a name="parameters"></a>パラメーター

*path*<br/>
完全パス。

*駆動*<br/>
ドライブ文字、コロン ( **:** ) の順に並べます。 ドライブ文字が不要な場合は、このパラメーターに**NULL**を渡すことができます。

*driveNumberOfElements*<br/>
1バイト文字またはワイド文字の*ドライブ*バッファーのサイズ。 *ドライブ*が**NULL**の場合、この値は0にする必要があります。

*エイリアス*<br/>
末尾のスラッシュを含む、ディレクトリ パス。 スラッシュ ( **/** )、円記号 ( **\\** )、またはその両方を使用できます。 ディレクトリパスが不要な場合は、このパラメーターに**NULL**を渡すことができます。

*dirNumberOfElements*<br/>
1バイト文字またはワイド文字の*dir*バッファーのサイズ。 *Dir*が**NULL**の場合、この値は0である必要があります。

*氏名*<br/>
拡張子なしの基本ファイル名。 ファイル名が不要な場合は、このパラメーターに**NULL**を渡すことができます。

*nameNumberOfElements*<br/>
1バイト文字またはワイド文字の*fname*バッファーのサイズ。 *Fname*が**NULL**の場合、この値は0である必要があります。

*ext*<br/>
先頭のピリオド ( **.** ) を含むファイル名の拡張子。ファイル名の拡張子が不要な場合は、このパラメーターに**NULL**を渡すことができます。

*extNumberOfElements*<br/>
1バイト文字またはワイド文字の*ext*バッファーのサイズ。 *Ext*が**NULL**の場合、この値は0である必要があります。

## <a name="return-value"></a>戻り値

正常終了した場合は 0 を返します。失敗した場合はエラー コードを返します。

### <a name="error-conditions"></a>エラー条件

|条件|戻り値|
|---------------|------------------|
|*パス*が**NULL**です|**EINVAL**|
|*ドライブ*が**NULL**で、 *driveNumberOfElements*が0ではない|**EINVAL**|
|*ドライブ*が**NULL**以外で、 *driveNumberOfElements*が0です。|**EINVAL**|
|*dir*が**NULL**です。 *dirnumberofelements*が0ではありません|**EINVAL**|
|*dir*が**NULL**ではありません。 *dirnumberofelements*が0です。|**EINVAL**|
|*fname*が**NULL**で、 *nameNumberOfElements*が0ではありません|**EINVAL**|
|*fname*が**NULL**以外で、 *nameNumberOfElements*が0です。|**EINVAL**|
|*ext*が**NULL**で、 *extnumberofelements*が0ではありません|**EINVAL**|
|*ext*が**NULL**ではなく、 *extnumberofelements*が0です。|**EINVAL**|

上記のいずれかの条件が発生すると、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」に説明されているように、無効なパラメーター ハンドラーが呼び出されます。 実行の継続が許可された場合、これらの関数は**errno**を**einval**に設定し、 **einval**を返します。

バッファーのいずれかが短すぎて結果を保持できない場合、これらの関数はすべてのバッファーを空の文字列にクリアし、 **errno**を**ERANGE**に設定し、 **ERANGE**を返します。

## <a name="remarks"></a>Remarks

**_Splitpath_s**関数は、パスを4つのコンポーネントに分割します。 **_splitpath_s**は、現在使用中のマルチバイトコードページに従ってマルチバイト文字シーケンスを認識し、マルチバイト文字列の引数を適切な方法で自動的に処理します。 **_wsplitpath_s**は、 **_splitpath_s**のワイド文字バージョンです。 **_wsplitpath_s**の引数はワイド文字列です。 それ以外では、これらの関数の動作は同じです

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|TCHAR.H のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsplitpath_s**|**_splitpath_s**|**_splitpath_s**|**_wsplitpath_s**|

完全パスの各コンポーネントは、個別のバッファーに格納されます。マニフェスト**定数 (** **_MAX_DIR**、 **_MAX_FNAME**、および stdlib.h> で定義されて**いる)。** H) 各ファイルコンポーネントに許容される最大サイズを指定します。 対応するマニフェスト定数よりも大きいファイル コンポーネントでは、ヒープ破損が発生します。

マニフェスト定数の値を次の表に示します。

|名|[値]|
|----------|-----------|
|_MAX_DRIVE|3|
|_MAX_DIR|256|
|_MAX_FNAME|256|
|_MAX_EXT|256|

完全なパスにコンポーネント (たとえばファイル名) が含まれていない場合、 **_splitpath_s**は対応するバッファーに空の文字列を割り当てます。

C++ では、テンプレートのオーバーロードによってこれらの関数を簡単に使用できます。オーバーロードでは、バッファー長を自動的に推論できるため、サイズ引数を指定する必要がなくなります。 詳細については、「[セキュリティ保護されたテンプレート オーバーロード](../../c-runtime-library/secure-template-overloads.md)」を参照してください。

これらの関数のデバッグライブラリバージョンは、最初にバッファーを0xFE で埋めます。 この動作を無効にするには、[_CrtSetDebugFillThreshold](crtsetdebugfillthreshold.md) を使用します。

## <a name="requirements"></a>［要件］

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_splitpath_s**|\<stdlib.h>|
|**_wsplitpath_s**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

「[_makepath_s、_wmakepath_s](makepath-s-wmakepath-s.md)」の例を参照してください。

## <a name="see-also"></a>関連項目

[ファイル処理](../../c-runtime-library/file-handling.md)<br/>
[_splitpath、_wsplitpath](splitpath-wsplitpath.md)<br/>
[_fullpath、_wfullpath](fullpath-wfullpath.md)<br/>
[_getmbcp](getmbcp.md)<br/>
[_makepath、_wmakepath](makepath-wmakepath.md)<br/>
[_setmbcp](setmbcp.md)<br/>
