---
title: ATL パス関数
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, path
f1_keywords:
- ATLPATH/ATL::ATLPath::AddBackslash
- ATLPATH/ATL::ATLPath::AddExtension
- ATLPATH/ATL::ATLPath::Append
- ATLPATH/ATL::ATLPath::BuildRoot
- ATLPATH/ATL::ATLPath::Canonicalize
- ATLPATH/ATL::ATLPath::Combine
- ATLPATH/ATL::ATLPath::CommonPrefix
- ATLPATH/ATL::ATLPath::CompactPath
- ATLPATH/ATL::ATLPath::CompactPathEx
- ATLPATH/ATL::ATLPath::FileExists
- ATLPATH/ATL::ATLPath::FindExtension
- ATLPATH/ATL::ATLPath::FindFileName
- ATLPATH/ATL::ATLPath::GetDriveNumber
- ATLPATH/ATL::ATLPath::IsDirectory
- ATLPATH/ATL::ATLPath::IsFileSpec
- ATLPATH/ATL::ATLPath::IsPrefix
- ATLPATH/ATL::ATLPath::IsRelative
- ATLPATH/ATL::ATLPath::IsRoot
- ATLPATH/ATL::ATLPath::IsSameRoot
- ATLPATH/ATL::ATLPath::IsUNC
- ATLPATH/ATL::ATLPath::IsUNCServer
- ATLPATH/ATL::ATLPath::IsUNCServerShare
- ATLPATH/ATL::ATLPath::MakePretty
- ATLPATH/ATL::ATLPath::MatchSpec
- ATLPATH/ATL::ATLPath::QuoteSpaces
- ATLPATH/ATL::ATLPath::RelativePathTo
- ATLPATH/ATL::ATLPath::RemoveArgs
- ATLPATH/ATL::ATLPath::RemoveBackslash
- ATLPATH/ATL::ATLPath::RemoveBlanks
- ATLPATH/ATL::ATLPath::RemoveExtension
- ATLPATH/ATL::ATLPath::RemoveFileSpec
- ATLPATH/ATL::ATLPath::RenameExtension
- ATLPATH/ATL::ATLPath::SkipRoot
- ATLPATH/ATL::ATLPath::StripPath
- ATLPATH/ATL::ATLPath::StripToRoot
- ATLPATH/ATL::ATLPath::UnquoteSpaces
ms.assetid: d1ec2b8d-7ec7-43ea-90dd-0a740d2a742b
ms.openlocfilehash: 76efbb0bd43b800f186eac1afa168fc2a0c939f6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497983"
---
# <a name="atl-path-functions"></a>ATL パス関数

ATL には、 [Cpatht](cpatht-class.md)の形式でパスを操作するための atlpath クラスが用意されています。 このコードは、atlpath. h にあります。

### <a name="related-classes"></a>関連クラス

|||
|-|-|
|[CPathT クラス](cpatht-class.md)|このクラスは、パスを表します。|

### <a name="related-typedefs"></a>関連する Typedef

|||
|-|-|
|`CPath`|を使用`CString`した[cpatht](cpatht-class.md)の特殊化。|
|`CPathA`|を使用`CStringA`した[cpatht](cpatht-class.md)の特殊化。|
|`CPathW`|を使用`CStringW`した[cpatht](cpatht-class.md)の特殊化。|

### <a name="functions"></a>関数

|||
|-|-|
|[ATLPath::AddBackslash](#addbackslash)|[Pathaddbackslash ラッシュ](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)用のオーバーロードされたラッパーです。|
|[ATLPath::AddExtension](#addextension)|[Pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)用のオーバーロードされたラッパーです。|
|[ATLPath::Append](#append)|[Pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)用のオーバーロードされたラッパーです。|
|[ATLPath::BuildRoot](#buildroot)|この関数は、 [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)のオーバーロードされたラッパーです。|
|[ATLPath::Canonicalize](#canonicalize)|[Pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)用のオーバーロードされたラッパーです。|
|[ATLPath::Combine](#combine)|[Pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)用のオーバーロードされたラッパーです。|
|[ATLPath::CommonPrefix](#commonprefix)|この関数は、 [Pathcommonprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)用のオーバーロードされたラッパーです。|
|[ATLPath::CompactPath](#compactpath)|この関数は、 [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)のオーバーロードされたラッパーです。|
|[ATLPath::CompactPathEx](#compactpathex)|この関数は、 [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)のオーバーロードされたラッパーです。|
|[ATLPath::FileExists](#fileexists)|[Pathfileexists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)用のオーバーロードされたラッパーです。|
|[ATLPath::FindExtension](#findextension)|この関数は、 [Pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)用のオーバーロードされたラッパーです。|
|[ATLPath::FindFileName](#findfilename)|[Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)用のオーバーロードされたラッパーです。|
|[ATLPath::GetDriveNumber](#getdrivenumber)|この関数は、 [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)のオーバーロードされたラッパーです。|
|[ATLPath::IsDirectory](#isdirectory)|[Pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)用のオーバーロードされたラッパーです。|
|[ATLPath::IsFileSpec](#isfilespec)|[Pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)用のオーバーロードされたラッパーです。|
|[ATLPath::IsPrefix](#isprefix)|この関数は、 [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)のオーバーロードされたラッパーです。|
|[ATLPath::IsRelative](#isrelative)|[Pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)用のオーバーロードされたラッパーです。|
|[ATLPath::IsRoot](#isroot)|この関数は、 [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)のオーバーロードされたラッパーです。|
|[ATLPath::IsSameRoot](#issameroot)|[Pathissameroot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)用のオーバーロードされたラッパーです。|
|[ATLPath::IsUNC](#isunc)|[Pathisunc](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)用のオーバーロードされたラッパーです。|
|[ATLPath::IsUNCServer](#isuncserver)|この関数は、 [Pathis出ないサーバー](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)用のオーバーロードされたラッパーです。|
|[ATLPath::IsUNCServerShare](#isuncservershare)|[Pathisの Servershare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)用のオーバーロードされたラッパーです。|
|[ATLPath::MakePretty](#makepretty)|この関数は、 [Pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)用のオーバーロードされたラッパーです。|
|[ATLPath::MatchSpec](#matchspec)|[Pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)用のオーバーロードされたラッパーです。|
|[ATLPath::QuoteSpaces](#quotespaces)|この関数は、 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)のオーバーロードされたラッパーです。|
|[ATLPath::RelativePathTo](#relativepathto)|この関数は、 [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)のオーバーロードされたラッパーです。|
|[ATLPath::RemoveArgs](#removeargs)|[Pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)用のオーバーロードされたラッパーです。|
|[ATLPath::RemoveBackslash](#removebackslash)|[Pathremovebackslash ラッシュ](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)用のオーバーロードされたラッパーです。|
|[ATLPath::RemoveBlanks](#removeblanks)|[Pathremoveblanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)用のオーバーロードされたラッパーです。|
|[ATLPath::RemoveExtension](#removeextension)|[Pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)用のオーバーロードされたラッパーです。|
|[ATLPath::RemoveFileSpec](#removefilespec)|[Pathremovefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)用のオーバーロードされたラッパーです。|
|[ATLPath::RenameExtension](#renameextension)|[Pathrenameextension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)用のオーバーロードされたラッパーです。|
|[ATLPath::SkipRoot](#skiproot)|この関数は、 [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)のオーバーロードされたラッパーです。|
|[ATLPath::StripPath](#strippath)|[Pathの Ppath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)用のオーバーロードされたラッパーです。|
|[ATLPath::StripToRoot](#striptoroot)|[Pathtoroot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)用のオーバーロードされたラッパーです。|
|[ATLPath::UnquoteSpaces](#unquotespaces)|この関数は、 [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)のオーバーロードされたラッパーです。|

## <a name="requirements"></a>必要条件

**ヘッダー:** atlpath .h

## <a name="addbackslash"></a>ATLPath:: AddBackSlash ラッシュ

[Pathaddbackslash ラッシュ](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline char* AddBackslash(char* pszPath);
inline wchar_t* AddBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathaddbackslash ラッシュ](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)」を参照してください。

## <a name="addextension"></a>ATLPath:: AddExtension

[Pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL AddExtension(char* pszPath, const char* pszExtension);
inline BOOL AddExtension(wchar_t* pszPath, const wchar_t* pszExtension);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw) 」を参照してください。

## <a name="append"></a> ATLPath::Append

[Pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL Append(char* pszPath, const char* pszMore);
inline BOOL Append(wchar_t* pszPath, const wchar_t* pszMore);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw) 」を参照してください。

## <a name="buildroot"></a>ATLPath:: BuildRoot

この関数は、 [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline char* BuildRoot(char* pszPath, int iDrive);
inline wchar_t* BuildRoot(wchar_t* pszPath, int iDrive);
```

### <a name="remarks"></a>Remarks

詳細については、 [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)を参照してください。

## <a name="canonicalize"></a> ATLPath::Canonicalize

[Pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL Canonicalize(char* pszDest, const char* pszSrc);
inline BOOL Canonicalize(wchar_t* pszDest, const wchar_t* pszSrc);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew) 」を参照してください。

## <a name="combine"></a> ATLPath::Combine

[Pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline char* Combine(
   char* pszDest,
   const char* pszDir,
   const char* pszFile
);

inline wchar_t* Combine(
   wchar_t* pszDest,
   const wchar_t* pszDir,
   const wchar_t* pszFile);
```

### <a name="remarks"></a>Remarks

詳細については、「PathCombine」を参照してください。

## <a name="commonprefix"></a> ATLPath::CommonPrefix

この関数は、 [Pathcommonprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline int CommonPrefix(
   const char* pszFile1,
   const char* pszFile2,
   char* pszDest);

inline int CommonPrefix(
   const wchar_t* pszFile1,
   const wchar_t* pszFile2,
   wchar_t* pszDest);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathcommonprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw) 」を参照してください。

## <a name="compactpath"></a> ATLPath::CompactPath

この関数は、 [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL CompactPath(
   HDC hDC,
   char* pszPath,
   UINT dx);

inline BOOL CompactPath(
   HDC hDC,
   wchar_t* pszPath,
   UINT dx);
```

### <a name="remarks"></a>Remarks

詳細については、 [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)を参照してください。

## <a name="compactpathex"></a> ATLPath::CompactPathEx

この関数は、 [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL CompactPathEx(
   char* pszDest,
   const char* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);

inline BOOL CompactPathEx(
   wchar_t* pszDest,
   const wchar_t* pszSrc,
   UINT nMaxChars,
   DWORD dwFlags);
```

### <a name="remarks"></a>Remarks

詳細については、 [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)を参照してください。

## <a name="fileexists"></a> ATLPath::FileExists

[Pathfileexists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL FileExists(const char* pszPath);
inline BOOL FileExists(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathfileexists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw) 」を参照してください。

## <a name="findextension"></a>ATLPath:: FindExtension

この関数は、 [Pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline char* FindExtension(const char* pszPath);
inline wchar_t* FindExtension(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw) 」を参照してください。

## <a name="findfilename"></a> ATLPath::FindFileName

[Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline char* FindFileName(const char* pszPath);
inline wchar_t* FindFileName(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) 」を参照してください。

## <a name="getdrivenumber"></a> ATLPath::GetDriveNumber

この関数は、 [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline int GetDriveNumber(const char* pszPath);
inline int GetDriveNumber(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)を参照してください。

## <a name="isdirectory"></a>  ATLPath::IsDirectory

[Pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)用のオーバーロードされたラッパーです。

```
inline BOOL IsDirectory(const char* pszPath);
inline BOOL IsDirectory(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、PathIsDirectory を参照してください。

## <a name="isfilespec"></a> ATLPath::IsFileSpec

[Pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL IsFileSpec(const char* pszPath);
inline BOOL IsFileSpec(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw) 」を参照してください。

## <a name="isprefix"></a> ATLPath::IsPrefix

この関数は、 [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL IsPrefix(const char* pszPrefix, const char* pszPath);
inline BOOL IsPrefix(const wchar_t* pszPrefix, const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)を参照してください。

## <a name="isrelative"></a> ATLPath::IsRelative

[Pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL IsRelative(const char* pszPath);
inline BOOL IsRelative(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew) 」を参照してください。

## <a name="isroot"></a> ATLPath::IsRoot

この関数は、 [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL IsRoot(const char* pszPath);
inline BOOL IsRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)を参照してください。

## <a name="issameroot"></a> ATLPath::IsSameRoot

[Pathissameroot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL IsSameRoot(const char* pszPath1, const char* pszPath2);
inline BOOL IsSameRoot(const wchar_t* pszPath1, const wchar_t* pszPath2);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathissameroot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw) 」を参照してください。

## <a name="isunc"></a> ATLPath::IsUNC

[Pathisunc](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL IsUNC(const char* pszPath);
inline BOOL IsUNC(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [Pathisunc](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)に関する説明を参照してください。

## <a name="isuncserver"></a> ATLPath::IsUNCServer

この関数は、 [Pathis出ないサーバー](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL IsUNCServer(const char* pszPath);
inline BOOL IsUNCServer(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [Pathisのサーバー](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)を参照してください。

## <a name="isuncservershare"></a> ATLPath::IsUNCServerShare

[Pathisの Servershare](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL IsUNCServerShare(const char* pszPath);
inline BOOL IsUNCServerShare(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [Pathisを](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)参照してください。

## <a name="makepretty"></a> ATLPath::MakePretty

この関数は、 [Pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL MakePretty(char* pszPath);
inline BOOL MakePretty(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw) 」を参照してください。

## <a name="matchspec"></a>ATLPath:: MatchSpec

[Pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL MatchSpec(const char* pszPath, const char* pszSpec);
inline BOOL MatchSpec(const wchar_t* pszPath, const wchar_t* pszSpec);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw) 」を参照してください。

## <a name="quotespaces"></a> ATLPath::QuoteSpaces

この関数は、 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline void QuoteSpaces(char* pszPath);
inline void QuoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)を参照してください。

## <a name="relativepathto"></a> ATLPath::RelativePathTo

この関数は、 [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL RelativePathTo(
   char* pszPath,
   const char* pszFrom,
   DWORD dwAttrFrom,
   const char* pszTo,
   DWORD dwAttrTo);

inline BOOL RelativePathTo(
   wchar_t* pszPath,
   const wchar_t* pszFrom,
   DWORD dwAttrFrom,
   const wchar_t* pszTo,
   DWORD dwAttrTo);
```

### <a name="remarks"></a>Remarks

詳細については、 [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)を参照してください。

## <a name="removeargs"></a> ATLPath::RemoveArgs

[Pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline void RemoveArgs(char* pszPath);
inline void RemoveArgs(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw) 」を参照してください。

## <a name="removebackslash"></a> ATLPath::RemoveBackslash

[Pathremovebackslash ラッシュ](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline char* RemoveBackslash(char* pszPath);
inline wchar_t* RemoveBackslash(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [Pathremovebackslash ラッシュ](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)を参照してください。

## <a name="removeblanks"></a> ATLPath::RemoveBlanks

[Pathremoveblanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline void RemoveBlanks(char* pszPath);
inline void RemoveBlanks(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [Pathremoveblanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)をご覧ください。

## <a name="removeextension"></a> ATLPath::RemoveExtension

[Pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline void RemoveExtension(char* pszPath);
inline void RemoveExtension(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw) 」を参照してください。

## <a name="removefilespec"></a> ATLPath::RemoveFileSpec

[Pathremovefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL RemoveFileSpec(char* pszPath);
inline BOOL RemoveFileSpec(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathremovefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw) 」を参照してください。

## <a name="renameextension"></a> ATLPath::RenameExtension

[Pathrenameextension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL RenameExtension(char* pszPath, const char* pszExt);
inline BOOL RenameExtension(wchar_t* pszPath, const wchar_t* pszExt);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathrenameextension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw) 」を参照してください。

## <a name="skiproot"></a>ATLPath:: SkipRoot

この関数は、 [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline char* SkipRoot(const char* pszPath);
inline wchar_t* SkipRoot(const wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)を参照してください。

## <a name="strippath"></a> ATLPath::StripPath

[Pathの Ppath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline void StripPath(char* pszPath);
inline void StripPath(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [pathの Ppath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw) 」を参照してください。

## <a name="striptoroot"></a> ATLPath::StripToRoot

[Pathtoroot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)用のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline BOOL StripToRoot(char* pszPath);
inline BOOL StripToRoot(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathtoroot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw) 」を参照してください。

## <a name="unquotespaces"></a> ATLPath::UnquoteSpaces

この関数は、 [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)のオーバーロードされたラッパーです。

### <a name="syntax"></a>構文

```
inline void UnquoteSpaces(char* pszPath);
inline void UnquoteSpaces(wchar_t* pszPath);
```

### <a name="remarks"></a>Remarks

詳細については、 [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)を参照してください。
