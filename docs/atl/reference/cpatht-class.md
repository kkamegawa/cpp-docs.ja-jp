---
title: CPathT クラス
ms.date: 03/27/2019
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
ms.openlocfilehash: ba1c831d772deef34449d17adc2c8e7a6f90eaef
ms.sourcegitcommit: 8178d22701047d24f69f10d01ba37490e3d67241
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "69496618"
---
# <a name="cpatht-class"></a>CPathT クラス

このクラスは、パスを表します。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>パラメーター

*StringType*<br/>
パスに使用する ATL/MFC 文字列クラス (「 [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)」を参照)。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名|説明|
|----------|-----------------|
|[CPathT::P CXSTR](#pcxstr)|定数文字列型。|
|[CPathT::P XSTR](#pxstr)|文字列型。|
|[CPathT:: XCHAR](#xchar)|文字型。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名|説明|
|----------|-----------------|
|[CPathT:: CPathT](#cpatht)|パスのコンストラクター。|

### <a name="public-methods"></a>パブリック メソッド

|名|説明|
|----------|-----------------|
|[CPathT:: AddBackslash ラッシュ](#addbackslash)|パスの正しい構文を作成するために、このメソッドを呼び出して、文字列の末尾に円記号を追加します。|
|[CPathT:: AddExtension](#addextension)|ファイル拡張子をパスに追加するには、このメソッドを呼び出します。|
|[CPathT:: Append](#append)|現在のパスに文字列を追加するには、このメソッドを呼び出します。|
|[CPathT:: BuildRoot](#buildroot)|指定したドライブ番号からルートパスを作成するには、このメソッドを呼び出します。|
|[CPathT:: 正規化](#canonicalize)|パスを正規の形式に変換するには、このメソッドを呼び出します。|
|[CPathT:: 結合](#combine)|ディレクトリ名を表す文字列と、ファイルパス名を表す文字列を1つのパスに連結するには、このメソッドを呼び出します。|
|[CPathT:: CommonPrefix](#commonprefix)|指定したパスが現在のパスと共通のプレフィックスを共有するかどうかを確認するには、このメソッドを呼び出します。|
|[CPathT:: CompactPath](#compactpath)|パスコンポーネントを省略記号に置き換えることにより、このメソッドを呼び出して、指定したピクセル幅に収まるようにファイルパスを切り捨てます。|
|[CPathT:: CompactPathEx](#compactpathex)|パスコンポーネントを省略記号で置き換えることにより、このメソッドを呼び出して、指定された文字数に収まるようにファイルパスを切り捨てます。|
|[CPathT:: FileExists](#fileexists)|このパス名のファイルが存在するかどうかを確認するには、このメソッドを呼び出します。|
|[CPathT:: FindExtension](#findextension)|パス内のファイル拡張子の位置を検索するには、このメソッドを呼び出します。|
|[CPathT:: FindFileName](#findfilename)|パス内のファイル名の位置を検索するには、このメソッドを呼び出します。|
|[CPathT:: GetDriveNumber](#getdrivenumber)|' A ' ~ ' Z ' の範囲内のドライブ文字のパスを検索し、対応するドライブ番号を返すには、このメソッドを呼び出します。|
|[CPathT:: GetExtension](#getextension)|パスからファイル拡張子を取得するには、このメソッドを呼び出します。|
|[CPathT:: IsDirectory](#isdirectory)|パスが有効なディレクトリであるかどうかを確認するには、このメソッドを呼び出します。|
|[CPathT:: IsFileSpec](#isfilespec)|パス区切り文字 (': '、' \\ ' など) を検索するには、このメソッドを呼び出します。 パス区切り文字が存在しない場合、パスはファイル仕様パスと見なされます。|
|[CPathT:: IsPrefix](#isprefix)|このメソッドを呼び出して、 *Pszprefix*によって渡された型の有効なプレフィックスがパスに含まれているかどうかを確認します。|
|[CPathT:: IsRelative](#isrelative)|パスが相対パスかどうかを判断するには、このメソッドを呼び出します。|
|[CPathT:: IsRoot](#isroot)|パスがディレクトリルートであるかどうかを判断するには、このメソッドを呼び出します。|
|[CPathT:: IsSameRoot](#issameroot)|現在のパスを持つ共通のルートコンポーネントが別のパスにあるかどうかを確認するには、このメソッドを呼び出します。|
|[CPathT:: IsUNC](#isunc)|パスがサーバーと共有の有効な UNC (汎用名前付け規則) パスであるかどうかを判断するには、このメソッドを呼び出します。|
|[CPathT:: Isデストラクタサーバー](#isuncserver)|パスがサーバーの有効な UNC (汎用名前付け規則) パスであるかどうかを確認するには、このメソッドを呼び出します。|
|[CPathT:: Isデストラクタ Servershare](#isuncservershare)|パスが有効な UNC (汎用名前付け規則) 共有パスであるかどうかを確認するには、このメソッドを呼び出します。 \ *サーバー* \ *共有*\\ ます。|
|[CPathT:: MakePretty](#makepretty)|パスをすべて小文字に変換して、パスを一貫した外観にするには、このメソッドを呼び出します。|
|[CPathT:: MatchSpec](#matchspec)|ワイルドカードの一致の種類を含む文字列のパスを検索するには、このメソッドを呼び出します。|
|[CPathT:: QuoteSpaces](#quotespaces)|スペースが含まれている場合は、このメソッドを呼び出して、パスを引用符で囲みます。|
|[CPathT:: RelativePathTo](#relativepathto)|ファイルまたはフォルダー間で相対パスを作成するには、このメソッドを呼び出します。|
|[CPathT:: RemoveArgs](#removeargs)|パスからコマンドライン引数を削除するには、このメソッドを呼び出します。|
|[CPathT:: RemoveBackslash ラッシュ](#removebackslash)|パスから末尾の円記号を削除するには、このメソッドを呼び出します。|
|[CPathT:: RemoveBlanks](#removeblanks)|パスから先頭と末尾の空白をすべて削除するには、このメソッドを呼び出します。|
|[CPathT:: RemoveExtension](#removeextension)|パスからファイル拡張子を削除するには、このメソッドを呼び出します (存在する場合)。|
|[CPathT:: RemoveFileSpec](#removefilespec)|パスの末尾にあるファイル名と円記号を削除するには、このメソッドを呼び出します。|
|[CPathT:: RenameExtension](#renameextension)|パスのファイル名拡張子を新しい拡張子に置き換えるには、このメソッドを呼び出します。 ファイル名に拡張子が含まれていない場合は、文字列の末尾に拡張子が付けられます。|
|[CPathT:: SkipRoot](#skiproot)|パスを解析するには、ドライブ文字または UNC サーバー/共有パスの部分を無視して、このメソッドを呼び出します。|
|[CPathT:: という Ppath](#strippath)|完全修飾パスとファイル名のパス部分を削除するには、このメソッドを呼び出します。|
|[CPathT:: トーラス](#striptoroot)|ルート情報を除くパスのすべての部分を削除するには、このメソッドを呼び出します。|
|[CPathT:: UnquoteSpaces](#unquotespaces)|パスの先頭と末尾から引用符を削除するには、このメソッドを呼び出します。|

### <a name="public-operators"></a>パブリック演算子

|名|説明|
|----------|-----------------|
|[CPathT:: operator const StringType &](#operator_const_stringtype_amp)|この演算子を使用すると、オブジェクトを文字列のように扱うことができます。|
|[CPathT:: operator CPathT::P CXSTR](#operator_cpatht__pcxstr)|この演算子を使用すると、オブジェクトを文字列のように扱うことができます。|
|[CPathT:: operator StringType &](#operator_stringtype_amp)|この演算子を使用すると、オブジェクトを文字列のように扱うことができます。|
|[CPathT:: operator + =](#operator_add_eq)|この演算子は、パスに文字列を追加します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名|説明|
|----------|-----------------|
|[CPathT:: m_strPath](#m_strpath)|パス。|

## <a name="remarks"></a>Remarks

`CPath`、`CPathA`、および `CPathW` は、次のように定義された `CPathT` のインスタンス化です。

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>［要件］

**ヘッダー:** atlpath .h

##  <a name="addbackslash"></a>CPathT:: AddBackslash ラッシュ

パスの正しい構文を作成するために、このメソッドを呼び出して、文字列の末尾に円記号を追加します。 パスの末尾に円記号が既に含まれている場合、円記号は追加されません。

```
void AddBackslash();
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathaddbackslash ラッシュ](/windows/win32/api/shlwapi/nf-shlwapi-pathaddbackslashw)」を参照してください。

##  <a name="addextension"></a>CPathT:: AddExtension

ファイル拡張子をパスに追加するには、このメソッドを呼び出します。

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>パラメーター

*pszExtension*<br/>
追加するファイル拡張子。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathaddextension](/windows/win32/api/shlwapi/nf-shlwapi-pathaddextensionw)」を参照してください。

##  <a name="append"></a>CPathT:: Append

現在のパスに文字列を追加するには、このメソッドを呼び出します。

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>パラメーター

*pszMore*<br/>
追加する文字列。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathappend](/windows/win32/api/shlwapi/nf-shlwapi-pathappendw)」を参照してください。

##  <a name="buildroot"></a>CPathT:: BuildRoot

指定したドライブ番号からルートパスを作成するには、このメソッドを呼び出します。

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>パラメーター

*iDrive*<br/>
ドライブ番号 (0 は A:、1は B: など)。

### <a name="remarks"></a>Remarks

詳細については、「 [PathBuildRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathbuildrootw)」を参照してください。

##  <a name="canonicalize"></a>CPathT:: 正規化

パスを正規の形式に変換するには、このメソッドを呼び出します。

```
void Canonicalize();
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathcanonicalize](/windows/win32/api/shlwapi/nf-shlwapi-pathcanonicalizew)」を参照してください。

##  <a name="combine"></a>CPathT:: 結合

ディレクトリ名を表す文字列と、ファイルパス名を表す文字列を1つのパスに連結するには、このメソッドを呼び出します。

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>パラメーター

*pszDir*<br/>
ディレクトリパス。

*pszFile*<br/>
ファイルパス。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathcombine](/windows/win32/api/shlwapi/nf-shlwapi-pathcombinew)」を参照してください。

##  <a name="commonprefix"></a>CPathT:: CommonPrefix

指定したパスが現在のパスと共通のプレフィックスを共有するかどうかを確認するには、このメソッドを呼び出します。

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>パラメーター

*pszOther*<br/>
現在のものと比較するパス。

### <a name="return-value"></a>戻り値

共通のプレフィックスを返します。

### <a name="remarks"></a>Remarks

プレフィックスは次のいずれかの型です: "C: \\ \\"、"."、".."、"..\\ \\ "。 詳細については、「 [Pathcommonprefix](/windows/win32/api/shlwapi/nf-shlwapi-pathcommonprefixw)」を参照してください。

##  <a name="compactpath"></a>CPathT:: CompactPath

パスコンポーネントを省略記号に置き換えることにより、このメソッドを呼び出して、指定したピクセル幅に収まるようにファイルパスを切り捨てます。

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>パラメーター

*hDC*<br/>
フォントメトリックに使用されるデバイスコンテキスト。

*nWidth*<br/>
文字列が強制的に格納される幅 (ピクセル単位)。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [PathCompactPath](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathw)」を参照してください。

##  <a name="compactpathex"></a>CPathT:: CompactPathEx

パスコンポーネントを省略記号で置き換えることにより、このメソッドを呼び出して、指定された文字数に収まるようにファイルパスを切り捨てます。

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>パラメーター

*nMaxChars*<br/>
新しい文字列に格納される最大文字数 (終端の NULL 文字を含む)。

*dwFlags*<br/>
予約済み。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [PathCompactPathEx](/windows/win32/api/shlwapi/nf-shlwapi-pathcompactpathexw)」を参照してください。

##  <a name="cpatht"></a>CPathT:: CPathT

コンストラクターです。

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>パラメーター

*pszPath*<br/>
パス文字列へのポインター。

*path*<br/>
パス文字列。

##  <a name="fileexists"></a>CPathT:: FileExists

このパス名のファイルが存在するかどうかを確認するには、このメソッドを呼び出します。

```
BOOL FileExists() const;
```

### <a name="return-value"></a>戻り値

ファイルが存在する場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathfileexists](/windows/win32/api/shlwapi/nf-shlwapi-pathfileexistsw)」を参照してください。

##  <a name="findextension"></a>CPathT:: FindExtension

パス内のファイル拡張子の位置を検索するには、このメソッドを呼び出します。

```
int FindExtension() const;
```

### <a name="return-value"></a>戻り値

拡張子の前の "." の位置を返します。 拡張機能が見つからない場合は、-1 を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathfindextension](/windows/win32/api/shlwapi/nf-shlwapi-pathfindextensionw)」を参照してください。

##  <a name="findfilename"></a>CPathT:: FindFileName

パス内のファイル名の位置を検索するには、このメソッドを呼び出します。

```
int FindFileName() const;
```

### <a name="return-value"></a>戻り値

ファイル名の位置を返します。 ファイル名が見つからない場合は、-1 を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)」を参照してください。

##  <a name="getdrivenumber"></a>CPathT:: GetDriveNumber

' A ' ~ ' Z ' の範囲内のドライブ文字のパスを検索し、対応するドライブ番号を返すには、このメソッドを呼び出します。

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>戻り値

ドライブ番号を 0 ~ 25 (' A ' から ' Z ' に対応する) の整数として返します。パスにドライブ文字がある場合は、それ以外の場合は-1 を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [PathGetDriveNumber](/windows/win32/api/shlwapi/nf-shlwapi-pathgetdrivenumberw)」を参照してください。

##  <a name="getextension"></a>CPathT:: GetExtension

パスからファイル拡張子を取得するには、このメソッドを呼び出します。

```
StringType GetExtension() const;
```

### <a name="return-value"></a>戻り値

ファイル拡張子を返します。

##  <a name="isdirectory"></a>CPathT:: IsDirectory

パスが有効なディレクトリであるかどうかを確認するには、このメソッドを呼び出します。

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>戻り値

パスがディレクトリである場合は0以外の値 (16) を返します。それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathisdirectory](/windows/win32/api/shlwapi/nf-shlwapi-pathisdirectoryw)」を参照してください。

##  <a name="isfilespec"></a>CPathT:: IsFileSpec

パス区切り文字 (': '、' \\ ' など) を検索するには、このメソッドを呼び出します。 パス区切り文字が存在しない場合、パスはファイル仕様パスと見なされます。

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>戻り値

パス内にパス区切り文字がない場合は TRUE を返します。パス区切り文字がある場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathisfilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathisfilespecw)」を参照してください。

##  <a name="isprefix"></a>CPathT:: IsPrefix

このメソッドを呼び出して、 *Pszprefix*によって渡された型の有効なプレフィックスがパスに含まれているかどうかを確認します。

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>パラメーター

*pszPrefix*<br/>
検索対象のプレフィックス。 プレフィックスは次のいずれかの型です: "C: \\ \\"、"."、".."、"..\\ \\ "。

### <a name="return-value"></a>戻り値

パスにプレフィックスが含まれている場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [PathIsPrefix](/windows/win32/api/shlwapi/nf-shlwapi-pathisprefixw)」を参照してください。

##  <a name="isrelative"></a>CPathT:: IsRelative

パスが相対パスかどうかを判断するには、このメソッドを呼び出します。

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>戻り値

相対パスの場合は TRUE、絶対パスの場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathisrelative](/windows/win32/api/shlwapi/nf-shlwapi-pathisrelativew)」を参照してください。

##  <a name="isroot"></a>CPathT:: IsRoot

パスがディレクトリルートであるかどうかを判断するには、このメソッドを呼び出します。

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>戻り値

パスがルートの場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [PathIsRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathisrootw)」を参照してください。

##  <a name="issameroot"></a>CPathT:: IsSameRoot

現在のパスを持つ共通のルートコンポーネントが別のパスにあるかどうかを確認するには、このメソッドを呼び出します。

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>パラメーター

*pszOther*<br/>
もう1つのパス。

### <a name="return-value"></a>戻り値

両方の文字列が同じルートコンポーネントを持つ場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathissameroot](/windows/win32/api/shlwapi/nf-shlwapi-pathissamerootw)」を参照してください。

##  <a name="isunc"></a>CPathT:: IsUNC

パスがサーバーと共有の有効な UNC (汎用名前付け規則) パスであるかどうかを判断するには、このメソッドを呼び出します。

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>戻り値

パスが有効な UNC パスである場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathisunc](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncw)」を参照してください。

##  <a name="isuncserver"></a>CPathT:: Isデストラクタサーバー

パスがサーバーの有効な UNC (汎用名前付け規則) パスであるかどうかを確認するには、このメソッドを呼び出します。

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>戻り値

文字列がサーバーの有効な UNC パスである (共有名がない) 場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathisを](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserverw)使用しないサーバー」を参照してください。

##  <a name="isuncservershare"></a>CPathT:: Isデストラクタ Servershare

パスが有効な UNC (汎用名前付け規則) 共有パスであるかどうかを確認するには、このメソッドを呼び出します。 \ *サーバー* \ *共有*\\ ます。

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>戻り値

パスが \\ \ *サーバー* \ *共有*の形式である場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathisのサーバー共有](/windows/win32/api/shlwapi/nf-shlwapi-pathisuncserversharew)」を参照してください。

##  <a name="m_strpath"></a>CPathT:: m_strPath

パス。

```
StringType m_strPath;
```

### <a name="remarks"></a>Remarks

`StringType` は、`CPathT` するテンプレートパラメーターです。

##  <a name="makepretty"></a>CPathT:: MakePretty

パスをすべて小文字に変換して、パスを一貫した外観にするには、このメソッドを呼び出します。

```
BOOL MakePretty();
```

### <a name="return-value"></a>戻り値

パスが変換されている場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathmakepretty](/windows/win32/api/shlwapi/nf-shlwapi-pathmakeprettyw)」を参照してください。

##  <a name="matchspec"></a>CPathT:: MatchSpec

ワイルドカードの一致の種類を含む文字列のパスを検索するには、このメソッドを呼び出します。

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>パラメーター

*pszSpec*<br/>
検索対象のファイルの種類を持つ null で終わる文字列へのポインター。 たとえば、現在のパスにあるファイルが DOC ファイルであるかどうかをテストするには、 *Pszspec*を "* .doc" に設定する必要があります。

### <a name="return-value"></a>戻り値

文字列がと一致する場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathmatchspec](/windows/win32/api/shlwapi/nf-shlwapi-pathmatchspecw)」を参照してください。

##  <a name="operator_add_eq"></a>CPathT:: operator + =

この演算子は、パスに文字列を追加します。

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>パラメーター

*pszMore*<br/>
追加する文字列。

### <a name="return-value"></a>戻り値

更新されたパスを返します。

##  <a name="operator_const_stringtype_amp"></a>CPathT:: operator const StringType &amp;

この演算子を使用すると、オブジェクトを文字列のように扱うことができます。

```
operator const StringType&() const throw();
```

### <a name="return-value"></a>戻り値

このオブジェクトによって管理されている現在のパスを表す文字列を返します。

##  <a name="operator_cpatht__pcxstr"></a>CPathT:: operator CPathT::P CXSTR

この演算子を使用すると、オブジェクトを文字列のように扱うことができます。

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>戻り値

このオブジェクトによって管理されている現在のパスを表す文字列を返します。

##  <a name="operator_stringtype_amp"></a>CPathT:: operator StringType &amp;

この演算子を使用すると、オブジェクトを文字列のように扱うことができます。

```
operator StringType&() throw();
```

### <a name="return-value"></a>戻り値

このオブジェクトによって管理されている現在のパスを表す文字列を返します。

##  <a name="pcxstr"></a>CPathT::P CXSTR

定数文字列型。

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Remarks

`StringType` は、`CPathT` するテンプレートパラメーターです。

##  <a name="pxstr"></a>CPathT::P XSTR

文字列型。

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Remarks

`StringType` は、`CPathT` するテンプレートパラメーターです。

##  <a name="quotespaces"></a>CPathT:: QuoteSpaces

スペースが含まれている場合は、このメソッドを呼び出して、パスを引用符で囲みます。

```
void QuoteSpaces();
```

### <a name="remarks"></a>Remarks

詳細については、「 [PathQuoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathquotespacesw)」を参照してください。

##  <a name="relativepathto"></a>CPathT:: RelativePathTo

ファイルまたはフォルダー間で相対パスを作成するには、このメソッドを呼び出します。

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>パラメーター

*psz*<br/>
相対パスの開始。

*dwAttrFrom*<br/>
*Pszfrom*のファイル属性。 この値に FILE_ATTRIBUTE_DIRECTORY が含まれている場合、 *Pszfrom*はディレクトリであると見なされます。それ以外の場合、*の pszfrom*ファイルと見なされます。

*pszTo*<br/>
相対パスの終点。

*dwAttrTo*<br/>
*Pszto へ*のファイル属性。 この値に FILE_ATTRIBUTE_DIRECTORY が含まれている場合、 *Pszto*はディレクトリであると見なされます。それ以外の場合、 *pszto*はファイルと見なされます。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [PathRelativePathTo](/windows/win32/api/shlwapi/nf-shlwapi-pathrelativepathtow)」を参照してください。

##  <a name="removeargs"></a>CPathT:: RemoveArgs

パスからコマンドライン引数を削除するには、このメソッドを呼び出します。

```
void RemoveArgs();
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathremoveargs](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveargsw)」を参照してください。

##  <a name="removebackslash"></a>CPathT:: RemoveBackslash ラッシュ

パスから末尾の円記号を削除するには、このメソッドを呼び出します。

```
void RemoveBackslash();
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathremovebackslash ラッシュ](/windows/win32/api/shlwapi/nf-shlwapi-pathremovebackslashw)」を参照してください。

##  <a name="removeblanks"></a>CPathT:: RemoveBlanks

パスから先頭と末尾の空白をすべて削除するには、このメソッドを呼び出します。

```
void RemoveBlanks();
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathremoveblanks](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveblanksw)」を参照してください。

##  <a name="removeextension"></a>CPathT:: RemoveExtension

パスからファイル拡張子を削除するには、このメソッドを呼び出します (存在する場合)。

```
void RemoveExtension();
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathremoveextension](/windows/win32/api/shlwapi/nf-shlwapi-pathremoveextensionw)」を参照してください。

##  <a name="removefilespec"></a>CPathT:: RemoveFileSpec

パスの末尾にあるファイル名と円記号を削除するには、このメソッドを呼び出します。

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathremovefilespec](/windows/win32/api/shlwapi/nf-shlwapi-pathremovefilespecw)」を参照してください。

##  <a name="renameextension"></a>CPathT:: RenameExtension

パスのファイル名拡張子を新しい拡張子に置き換えるには、このメソッドを呼び出します。 ファイル名に拡張子が含まれていない場合は、パスの末尾に拡張子が付けられます。

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>パラメーター

*pszExtension*<br/>
新しいファイル名の拡張子。前に "." 文字が付きます。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、失敗した場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathrenameextension](/windows/win32/api/shlwapi/nf-shlwapi-pathrenameextensionw)」を参照してください。

##  <a name="skiproot"></a>CPathT:: SkipRoot

パスを解析するには、ドライブ文字または UNC (汎用名前付け規則) サーバー/共有パスの部分を無視して、このメソッドを呼び出します。

```
int SkipRoot() const;
```

### <a name="return-value"></a>戻り値

ルート (ドライブ文字または UNC サーバー/共有) の後にあるサブパスの先頭の位置を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [PathSkipRoot](/windows/win32/api/shlwapi/nf-shlwapi-pathskiprootw)」を参照してください。

##  <a name="strippath"></a>CPathT:: という Ppath

完全修飾パスとファイル名のパス部分を削除するには、このメソッドを呼び出します。

```
void StripPath();
```

### <a name="remarks"></a>Remarks

詳細については、「 [Pathの Ppath](/windows/win32/api/shlwapi/nf-shlwapi-pathstrippathw)」を参照してください。

##  <a name="striptoroot"></a>CPathT:: トーラス

ルート情報を除くパスのすべての部分を削除するには、このメソッドを呼び出します。

```
BOOL StripToRoot();
```

### <a name="return-value"></a>戻り値

有効なドライブ文字がパスで見つかった場合は TRUE、それ以外の場合は FALSE を返します。

### <a name="remarks"></a>Remarks

詳細については、「 [Pathstriptoroot](/windows/win32/api/shlwapi/nf-shlwapi-pathstriptorootw)」を参照してください。

##  <a name="unquotespaces"></a>CPathT:: UnquoteSpaces

パスの先頭と末尾から引用符を削除するには、このメソッドを呼び出します。

```
void UnquoteSpaces();
```

### <a name="remarks"></a>Remarks

詳細については、「 [PathUnquoteSpaces](/windows/win32/api/shlwapi/nf-shlwapi-pathunquotespacesw)」を参照してください。

##  <a name="xchar"></a>CPathT:: XCHAR

文字型。

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Remarks

`StringType` は、`CPathT` するテンプレートパラメーターです。

## <a name="see-also"></a>関連項目

[クラス](../../atl/reference/atl-classes.md)<br/>
[CStringT クラス](../../atl-mfc-shared/reference/cstringt-class.md)
