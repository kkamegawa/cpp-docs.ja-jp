---
title: CFileFind クラス
ms.date: 11/04/2016
f1_keywords:
- CFileFind
- AFX/CFileFind
- AFX/CFileFind::CFileFind
- AFX/CFileFind::Close
- AFX/CFileFind::FindFile
- AFX/CFileFind::FindNextFile
- AFX/CFileFind::GetCreationTime
- AFX/CFileFind::GetFileName
- AFX/CFileFind::GetFilePath
- AFX/CFileFind::GetFileTitle
- AFX/CFileFind::GetFileURL
- AFX/CFileFind::GetLastAccessTime
- AFX/CFileFind::GetLastWriteTime
- AFX/CFileFind::GetLength
- AFX/CFileFind::GetRoot
- AFX/CFileFind::IsArchived
- AFX/CFileFind::IsCompressed
- AFX/CFileFind::IsDirectory
- AFX/CFileFind::IsDots
- AFX/CFileFind::IsHidden
- AFX/CFileFind::IsNormal
- AFX/CFileFind::IsReadOnly
- AFX/CFileFind::IsSystem
- AFX/CFileFind::IsTemporary
- AFX/CFileFind::MatchesMask
- AFX/CFileFind::CloseContext
- AFX/CFileFind::m_pTM
helpviewer_keywords:
- CFileFind [MFC], CFileFind
- CFileFind [MFC], Close
- CFileFind [MFC], FindFile
- CFileFind [MFC], FindNextFile
- CFileFind [MFC], GetCreationTime
- CFileFind [MFC], GetFileName
- CFileFind [MFC], GetFilePath
- CFileFind [MFC], GetFileTitle
- CFileFind [MFC], GetFileURL
- CFileFind [MFC], GetLastAccessTime
- CFileFind [MFC], GetLastWriteTime
- CFileFind [MFC], GetLength
- CFileFind [MFC], GetRoot
- CFileFind [MFC], IsArchived
- CFileFind [MFC], IsCompressed
- CFileFind [MFC], IsDirectory
- CFileFind [MFC], IsDots
- CFileFind [MFC], IsHidden
- CFileFind [MFC], IsNormal
- CFileFind [MFC], IsReadOnly
- CFileFind [MFC], IsSystem
- CFileFind [MFC], IsTemporary
- CFileFind [MFC], MatchesMask
- CFileFind [MFC], CloseContext
- CFileFind [MFC], m_pTM
ms.assetid: 9990068c-b023-4114-9580-a50182d15240
ms.openlocfilehash: 9eb192e546bcfbba385beea4f1716ce03bbc8ade
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894056"
---
# <a name="cfilefind-class"></a>CFileFind クラス

ローカル ファイルを検索し、基本クラスです[CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)と[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)、インターネット ファイル検索を実行します。

## <a name="syntax"></a>構文

```
class CFileFind : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFileFind::CFileFind](#cfilefind)|`CFileFind` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFileFind::Close](#close)|検索要求を終了します。|
|[CFileFind::FindFile](#findfile)|指定したファイル名用のディレクトリを検索します。|
|[CFileFind::FindNextFile](#findnextfile)|以前の呼び出しからのファイル検索を続行[FindFile](#findfile)します。|
|[CFileFind::GetCreationTime](#getcreationtime)|ファイルが作成された時刻を取得します。|
|[CFileFind::GetFileName](#getfilename)|見つかったファイルの拡張子を含む、名前を取得します。|
|[CFileFind::GetFilePath](#getfilepath)|見つかったファイルの完全パスを取得します。|
|[CFileFind::GetFileTitle](#getfiletitle)|見つかったファイルのタイトルを取得します。 タイトルでは、拡張機能は含まれません。|
|[CFileFind::GetFileURL](#getfileurl)|見つかったファイルのファイル パスを含む URL を取得します。|
|[CFileFind::GetLastAccessTime](#getlastaccesstime)|ファイルが最後にアクセスする時間を取得します。|
|[CFileFind::GetLastWriteTime](#getlastwritetime)|ファイルが最後に変更、保存時間を取得します。|
|[CFileFind::GetLength](#getlength)|(バイト単位)、見つかったファイルの長さを取得します。|
|[CFileFind::GetRoot](#getroot)|見つかったファイルのルート ディレクトリを取得します。|
|[CFileFind::IsArchived](#isarchived)|見つかったファイルがアーカイブになっているかどうかを決定します。|
|[CFileFind::IsCompressed](#iscompressed)|見つかったファイルを圧縮するかどうかを決定します。|
|[CFileFind::IsDirectory](#isdirectory)|見つかったファイルがディレクトリであるかどうかを判断します。|
|[CFileFind::IsDots](#isdots)|見つかったファイルの名前が名前を持つかどうかを判断します".「または」.."、実際にはディレクトリであることを示します。|
|[CFileFind::IsHidden](#ishidden)|かどうか、検索されたファイルが非表示を決定します。|
|[CFileFind::IsNormal](#isnormal)|見つかったファイルが正常かどうかを (つまり、属性を持っていないその他)。|
|[CFileFind::IsReadOnly](#isreadonly)|見つかったファイルが読み取り専用のかどうかを決定します。|
|[CFileFind::IsSystem](#issystem)|見つかったファイルがシステム ファイルであるかどうかを判断します。|
|[CFileFind::IsTemporary](#istemporary)|見つかったファイルが一時的なかどうかを判断します。|
|[CFileFind::MatchesMask](#matchesmask)|検索するファイルの目的のファイル属性を示します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CFileFind::CloseContext](#closecontext)|現在の検索のハンドルで指定されたファイルを閉じます。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CFileFind::m_pTM](#m_ptm)|ポインターを`CAtlTransactionManager`オブジェクト。|

## <a name="remarks"></a>Remarks

`CFileFind` 検索を開始し、ファイルを検索、タイトル、名前、またはファイルのパスを返すメンバー関数が含まれています。 インターネットの検索、メンバー関数は、 [GetFileURL](#getfileurl)ファイルの URL を返します。

`CFileFind` 特定のサーバーの種類を検索するその他の 2 つの MFC クラスの基本クラスが設計: `CGopherFileFind` gopher サーバーでは、具体的には連携と`CFtpFileFind`具体的には FTP サーバーで動作します。 同時に、これら 3 つのクラスは、クライアントがローカル コンピューターまたはリモート サーバーのいずれかのサーバー プロトコル、ファイルの種類または場所に関係なくのファイルを検索するためのシームレスなメカニズムを提供します。

次のコードは、印刷の各ファイルの名前、現在のディレクトリ内のすべてのファイルに列挙されます。

[!code-cpp[NVC_MFCFiles#31](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_1.cpp)]

このコードに例を簡潔にするには、C++ 標準ライブラリを使用して`cout`クラス。 `cout`への呼び出しで行を置き換えることができます`CListBox::AddString`、たとえば、グラフィカル ユーザー インターフェイスを使用してプログラムでします。

使用する方法の詳細についての`CFileFind`他 WinInet クラスは、記事を参照して、[インターネットが WinInet を使用したプログラミング](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CFileFind`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="cfilefind"></a>  CFileFind::CFileFind

このメンバー関数が呼び出されます、`CFileFind`オブジェクトが構築されます。

```
CFileFind();
CFileFind(CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>パラメーター

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetFileName](#getfilename)します。

##  <a name="close"></a>  CFileFind::Close

検索を終了し、コンテキストをリセットし、すべてのリソースを解放するには、このメンバー関数を呼び出します。

```
void Close();
```

### <a name="remarks"></a>Remarks

呼び出した後`Close`、新しいを作成する必要はありません`CFileFind`呼び出す前にインスタンス[FindFile](#findfile)新しい検索を開始します。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetFileName](#getfilename)します。

##  <a name="closecontext"></a>  CFileFind::CloseContext

現在の検索のハンドルで指定されたファイルを閉じます。

```
virtual void CloseContext();
```

### <a name="remarks"></a>Remarks

検索のハンドルの現在の値で指定されたファイルを閉じます。 既定の動作を変更するには、この関数をオーバーライドします。

呼び出す必要があります、 [FindFile](#findfile)または[FindNextFile](#findnextfile)関数を少なくとも 1 回有効な検索のハンドルを取得します。 `FindFile`と`FindNextFile`関数では、検索のハンドルを使用して、指定した名前と一致する名前を持つファイルを検索します。

##  <a name="findfile"></a>  CFileFind::FindFile

ファイル検索を開くには、このメンバー関数を呼び出します。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwUnused = 0);
```

### <a name="parameters"></a>パラメーター

*pstrName*<br/>
検索するファイルの名前を含む文字列へのポインター。 NULL を渡す場合*pstrName*、`FindFile`は、ワイルドカード (*.\*) 検索します。

*dwUnused*<br/>
作成するために予約`FindFile`派生クラス。 0 である必要があります。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 拡張エラー情報を取得するには、Win32 関数を呼び出す[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)します。

### <a name="remarks"></a>Remarks

呼び出した後`FindFile`ファイル検索を開始する[FindNextFile](#findnextfile)を後続のファイルを取得します。 呼び出す必要があります`FindNextFile`次の属性のいずれかにメンバー関数を呼び出す前に少なくとも 1 回。

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

### <a name="example"></a>例

  例をご覧ください[CFileFind::IsDirectory](#isdirectory)します。

##  <a name="findnextfile"></a>  CFileFind::FindNextFile

以前の呼び出しからのファイル検索を続行するには、このメンバー関数を呼び出す[FindFile](#findfile)します。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>戻り値

以上のファイルがある場合、0 以外の場合ファイルが見つかりましたが、ディレクトリ内の最後の 1 つである場合や、エラーが発生した場合は 0 します。 拡張エラー情報を取得するには、Win32 関数を呼び出す[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)します。 ファイルが見つかりましたが、ディレクトリ内の最後のファイル、または一致する場合は、ファイルが見つからなかんだことができます、 `GetLastError` ERROR_NO_MORE_FILES を返します。

### <a name="remarks"></a>Remarks

呼び出す必要があります`FindNextFile`次の属性のいずれかにメンバー関数を呼び出す前に少なくとも 1 回。

- [GetCreationTime](#getcreationtime)

- [GetFileName](#getfilename)

- [GetFileTitle](#getfiletitle)

- [GetFilePath](#getfilepath)

- [GetFileURL](#getfileurl)

- [GetLastAccessTime](#getlastaccesstime)

- [GetLastWriteTime](#getlastwritetime)

- [GetLength](#getlength)

- [GetRoot](#getroot)

- [IsArchived](#isarchived)

- [IsCompressed](#iscompressed)

- [IsDirectory](#isdirectory)

- [IsDots](#isdots)

- [IsHidden](#ishidden)

- [IsNormal](#isnormal)

- [IsReadOnly](#isreadonly)

- [IsSystem](#issystem)

- [IsTemporary](#istemporary)

- [MatchesMask](#matchesmask)

`FindNextFile` Win32 関数をラップ[FindNextFile](/windows/desktop/api/fileapi/nf-fileapi-findnextfilea)します。

### <a name="example"></a>例

  例をご覧ください[CFileFind::IsDirectory](#isdirectory)します。

##  <a name="getcreationtime"></a>  CFileFind::GetCreationTime

指定したファイルが作成された時刻を取得するには、このメンバー関数を呼び出します。

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>パラメーター

*pTimeStamp*<br/>
ポインターを[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)ファイルが作成された時刻を含む構造体。

*refTime*<br/>
参照を[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、0 以外の場合失敗した場合は 0。 `GetCreationTime` 場合にのみ、0 を返します[FindNextFile](#findnextfile)がこの呼び出さ`CFileFind`オブジェクト。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetCreationTime`します。

> [!NOTE]
>  すべてのファイル システムでは、同じセマンティクスを使用して、この関数によって返されるタイムスタンプを実装します。 この関数は、基になるファイル システムまたはサーバーがサポートしない場合、時間属性を維持することは、その他のタイム スタンプ関数によって返されるのと同じ値を返す可能性があります。 参照してください、 [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)時刻の形式については、構造体。 いくつかのオペレーティング システムでは、ファイルが存在するコンピューターにゾーンのローカル タイムの時刻が返されることが。 Win32 を参照してください。[詳細](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime)API の詳細についてはします。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetLength](#getlength)します。

##  <a name="getfilename"></a>  CFileFind::GetFileName

見つかったファイルの名前を取得するには、このメンバー関数を呼び出します。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>戻り値

最後に見つかったファイルの名前。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile) GetFileName を呼び出す前に少なくとも 1 回です。

`GetFileName` 3 つの 1 つ`CFileFind`を何らかの形式のファイル名を返すメンバー関数。 次の一覧では、3 つと、その違いについて説明します。

- `GetFileName` 拡張子を含むファイル名を返します。 たとえば、呼び出し`GetFileName`ファイルに関するユーザー メッセージを生成する*c:\myhtml\myfile.txt*ファイル名を返します*myfile.txt*します。

- [まで含めた](#getfilepath)全体、ファイルのパスを返します。 たとえば、呼び出し`GetFilePath`ファイルに関するユーザー メッセージを生成する*c:\myhtml\myfile.txt*ファイル パスを返します*c:\myhtml\myfile.txt*します。

- [GetFileTitle](#getfiletitle)ファイル拡張子を除いて、ファイル名を返します。 たとえば、呼び出し`GetFileTitle`ファイルに関するユーザー メッセージを生成する*c:\myhtml\myfile.txt*ファイルのタイトルを返します*myfile*します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#32](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_2.cpp)]

##  <a name="getfilepath"></a>  CFileFind::GetFilePath

指定したファイルの完全なパスを取得するには、このメンバー関数を呼び出します。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>戻り値

指定したファイルのパス。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetFilePath`します。

`GetFilePath` 3 つの 1 つ`CFileFind`を何らかの形式のファイル名を返すメンバー関数。 次の一覧では、3 つと、その違いについて説明します。

- [GetFileName](#getfilename)拡張子を含む、ファイル名を返します。 たとえば、呼び出し`GetFileName`ファイルに関するユーザー メッセージを生成する*c:\myhtml\myfile.txt*ファイル名を返します*myfile.txt*します。

- `GetFilePath` ファイルのパス全体を返します。 たとえば、呼び出し`GetFilePath`ファイルに関するユーザー メッセージを生成する`c:\myhtml\myfile.txt`ファイル パスを返します`c:\myhtml\myfile.txt`します。

- [GetFileTitle](#getfiletitle)ファイル拡張子を除いて、ファイル名を返します。 たとえば、呼び出し`GetFileTitle`ファイルに関するユーザー メッセージを生成する*c:\myhtml\myfile.txt*ファイルのタイトルを返します*myfile*します。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetFileName](#getfilename)します。

##  <a name="getfiletitle"></a>  CFileFind::GetFileTitle

見つかったファイルのタイトルを取得するには、このメンバー関数を呼び出します。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>戻り値

ファイルのタイトル。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetFileTitle`します。

`GetFileTitle` 3 つの 1 つ`CFileFind`を何らかの形式のファイル名を返すメンバー関数。 次の一覧では、3 つと、その違いについて説明します。

- [GetFileName](#getfilename)拡張子を含む、ファイル名を返します。 たとえば、呼び出し`GetFileName`ファイルに関するユーザー メッセージを生成する*c:\myhtml\myfile.txt*ファイル名を返します*myfile.txt*します。

- [まで含めた](#getfilepath)全体、ファイルのパスを返します。 たとえば、呼び出し`GetFilePath`ファイルに関するユーザー メッセージを生成する*c:\myhtml\myfile.txt*ファイル パスを返します*c:\myhtml\myfile.txt*します。

- `GetFileTitle` ファイル拡張子を除いて、ファイル名を返します。 たとえば、呼び出し`GetFileTitle`ファイルに関するユーザー メッセージを生成する*c:\myhtml\myfile.txt*ファイルのタイトルを返します*myfile*します。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetFileName](#getfilename)します。

##  <a name="getfileurl"></a>  CFileFind::GetFileURL

指定した URL を取得するには、このメンバー関数を呼び出します。

```
virtual CString GetFileURL() const;
```

### <a name="return-value"></a>戻り値

完全な URL。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetFileURL`します。

`GetFileURL` メンバー関数のような[まで含めた](#getfilepath)形式で URL を返す点が、`file://path`します。 たとえば、呼び出し`GetFileURL`の完全な URL を取得する*myfile.txt* URL を返します`file://c:\myhtml\myfile.txt`します。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetFileName](#getfilename)します。

##  <a name="getlastaccesstime"></a>  CFileFind::GetLastAccessTime

指定したファイルの最終アクセス時刻を取得するには、このメンバー関数を呼び出します。

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>パラメーター

*refTime*<br/>
参照を[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクト。

*pTimeStamp*<br/>
ポインターを[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)ファイルの最終アクセス時刻を含む構造体。

### <a name="return-value"></a>戻り値

成功した場合、0 以外の場合失敗した場合は 0。 `GetLastAccessTime` 場合にのみ、0 を返します[FindNextFile](#findnextfile)がこの呼び出さ`CFileFind`オブジェクト。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetLastAccessTime`します。

> [!NOTE]
>  すべてのファイル システムでは、同じセマンティクスを使用して、この関数によって返されるタイムスタンプを実装します。 この関数は、基になるファイル システムまたはサーバーがサポートしない場合、時間属性を維持することは、その他のタイム スタンプ関数によって返されるのと同じ値を返す可能性があります。 参照してください、 [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)時刻の形式については、構造体。 いくつかのオペレーティング システムでは、ファイルが存在するコンピューターにゾーンのローカル タイムの時刻が返されることが。 Win32 を参照してください。[詳細](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime)API の詳細についてはします。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetLength](#getlength)します。

##  <a name="getlastwritetime"></a>  CFileFind::GetLastWriteTime

最後に、ファイルが変更された時刻を取得するには、このメンバー関数を呼び出します。

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>パラメーター

*pTimeStamp*<br/>
ポインターを[FILETIME](/windows/desktop/api/minwinbase/ns-minwinbase-filetime)ファイルの最終書き込み時刻を含む構造体。

*refTime*<br/>
参照を[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクト。

### <a name="return-value"></a>戻り値

成功した場合、0 以外の場合失敗した場合は 0。 `GetLastWriteTime` 場合にのみ、0 を返します[FindNextFile](#findnextfile)がこの呼び出さ`CFileFind`オブジェクト。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetLastWriteTime`します。

> [!NOTE]
>  すべてのファイル システムでは、同じセマンティクスを使用して、この関数によって返されるタイムスタンプを実装します。 この関数は、基になるファイル システムまたはサーバーがサポートしない場合、時間属性を維持することは、その他のタイム スタンプ関数によって返されるのと同じ値を返す可能性があります。 参照してください、 [Win32_Find_Data](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)時刻の形式については、構造体。 いくつかのオペレーティング システムでは、ファイルが存在するコンピューターにゾーンのローカル タイムの時刻が返されることが。 Win32 を参照してください。[詳細](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime)API の詳細についてはします。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetLength](#getlength)します。

##  <a name="getlength"></a>  CFileFind::GetLength

(バイト単位)、検索したファイルの長さを取得するには、このメンバー関数を呼び出します。

```
ULONGLONG GetLength() const;
```

### <a name="return-value"></a>戻り値

(バイト単位)、検索したファイルの長さ。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetLength`します。

`GetLength` Win32 構造を使用して[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)を取得し、ファイル サイズの値をバイト単位で返します。

> [!NOTE]
>  時点で、MFC 7.0、 `GetLength` 64 ビット整数型をサポートしています。 以前、ライブラリのこの新しいバージョンで構築された既存のコードについては、切り捨ての警告があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#33](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_3.cpp)]

##  <a name="getroot"></a>  CFileFind::GetRoot

見つかったファイルのルートを取得するには、このメンバー関数を呼び出します。

```
virtual CString GetRoot() const;
```

### <a name="return-value"></a>戻り値

アクティブな検索のルートです。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetRoot`します。

このメンバー関数は、ドライブ指定子と検索を開始するために使用するパス名を返します。 などを呼び出す[FindFile](#findfile)で`*.dat`結果`GetRoot`空の文字列を返します。 など、パスを渡して`c:\windows\system\*.dll`を`FindFile`結果`GetRoot`返す`c:\windows\system\`します。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetFileName](#getfilename)します。

##  <a name="isarchived"></a>  CFileFind::IsArchived

見つかったファイルがアーカイブになっているかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL IsArchived() const;
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

アプリケーションがバックアップまたは削除、FILE_ATTRIBUTE_ARCHIVE で識別されるファイル属性には、アーカイブ ファイルをマーク、 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)構造体。

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`IsArchived`します。

メンバー関数を参照してください。[は](#matchesmask)ファイル属性の完全な一覧についてはします。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetLength](#getlength)します。

##  <a name="iscompressed"></a>  CFileFind::IsCompressed

見つかったファイルを圧縮するかどうかを判断するには、このメンバー関数を呼び出します。

```
BOOL IsCompressed() const;
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

圧縮されたファイルが FILE_ATTRIBUTE_COMPRESSED でマークされた、ファイル属性がで識別される、 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)構造体。 ファイルの場合は、この属性は、すべてのファイルにデータが圧縮されているを示します。 ディレクトリの場合は、この属性は、圧縮が新しく作成されたファイルとサブディレクトリの既定値を示します。

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`IsCompressed`します。

メンバー関数を参照してください。[は](#matchesmask)ファイル属性の完全な一覧についてはします。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetLength](#getlength)します。

##  <a name="isdirectory"></a>  CFileFind::IsDirectory

見つかったファイルがディレクトリであるかを判断するには、このメンバー関数を呼び出します。

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

ディレクトリであるファイルが FILE_ATTRIBUTE_DIRECTORY で識別されるファイル属性でマークされた、 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)構造体。

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`IsDirectory`します。

メンバー関数を参照してください。[は](#matchesmask)ファイル属性の完全な一覧についてはします。

### <a name="example"></a>例

この小さなプログラムでは、C:\ ドライブのすべてのディレクトリを再帰処理し、ディレクトリの名前を出力します。

[!code-cpp[NVC_MFCFiles#34](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_4.cpp)]

##  <a name="isdots"></a>  CFileFind::IsDots

ファイルを反復処理中に現在のディレクトリとその親ディレクトリのマーカーをテストするには、このメンバー関数を呼び出します。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>戻り値

見つかったファイルが、名前を持つ場合、0 以外の場合".「または」.."、見つかったファイルが実際にディレクトリを示します。 それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`IsDots`します。

### <a name="example"></a>例

  例をご覧ください[CFileFind::IsDirectory](#isdirectory)します。

##  <a name="ishidden"></a>  CFileFind::IsHidden

かどうか、検索されたファイルが非表示を確認するには、このメンバー関数を呼び出します。

```
BOOL IsHidden() const;
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

FILE_ATTRIBUTE_HIDDEN で示されている、すべてのファイルのファイル属性が識別される、 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)構造体。 隠しファイルは通常のディレクトリ一覧に含まれていません。

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`IsHidden`します。

メンバー関数を参照してください。[は](#matchesmask)ファイル属性の完全な一覧についてはします。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetLength](#getlength)します。

##  <a name="isnormal"></a>  CFileFind::IsNormal

見つかったファイルが通常のファイルを確認するには、このメンバー関数を呼び出します。

```
BOOL IsNormal() const;
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

FILE_ATTRIBUTE_NORMAL でマークされたファイル、ファイル属性の識別、 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)構造体。 通常のファイルには、他の属性セットがありません。 その他のすべてのファイル属性は、この属性をオーバーライドします。

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`IsNormal`します。

メンバー関数を参照してください。[は](#matchesmask)ファイル属性の完全な一覧についてはします。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetLength](#getlength)します。

##  <a name="isreadonly"></a>  CFileFind::IsReadOnly

このメンバー関数は、見つかったファイルが読み取り専用であるかどうかを呼び出します。

```
BOOL IsReadOnly() const;
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

読み取り専用ファイルが FILE_ATTRIBUTE_READONLY でマークされた、ファイル属性がで識別される、 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)構造体。 アプリケーションは、この種類のファイルを読み取ることができますが、書き込みまたは削除することはできません。

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`IsReadOnly`します。

メンバー関数を参照してください。[は](#matchesmask)ファイル属性の完全な一覧についてはします。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetLength](#getlength)します。

##  <a name="issystem"></a>  CFileFind::IsSystem

見つかったファイルがシステム ファイルであるかを判断するには、このメンバー関数を呼び出します。

```
BOOL IsSystem() const;
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

システム ファイルが、FILE_ATTRIBUTE_SYSTEM でマークされた、ファイル属性がで識別される、 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)構造体。 システム ファイルはの一部であるまたはのみ、オペレーティング システムによって使用されます。

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`IsSystem`します。

メンバー関数を参照してください。[は](#matchesmask)ファイル属性の完全な一覧についてはします。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetLength](#getlength)します。

##  <a name="istemporary"></a>  CFileFind::IsTemporary

見つかったファイルが一時ファイルを確認するには、このメンバー関数を呼び出します。

```
BOOL IsTemporary() const;
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

一時ファイルが FILE_ATTRIBUTE_TEMPORARY でマークされた、ファイル属性がで識別される、 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)構造体。 一時ファイルは、一時的なストレージに使用されます。 アプリケーションは、どうしても必要な場合にのみ、ファイルを書き込む必要があります。 ファイルのデータのほとんどは、ファイルがすぐに削除されるため、メディアに書き込まれずに、メモリに残ります。

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`IsTemporary`します。

メンバー関数を参照してください。[は](#matchesmask)ファイル属性の完全な一覧についてはします。

### <a name="example"></a>例

  例をご覧ください[CFileFind::GetLength](#getlength)します。

##  <a name="m_ptm"></a>  CFileFind::m_pTM

ポインターを`CAtlTransactionManager`オブジェクト。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Remarks

##  <a name="matchesmask"></a>  CFileFind::MatchesMask

見つかったファイルのファイル属性をテストするには、このメンバー関数を呼び出します。

```
virtual BOOL MatchesMask(DWORD dwMask) const;
```

### <a name="parameters"></a>パラメーター

*dwMask*<br/>
識別される 1 つまたは複数のファイル属性を指定します、 [WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)見つかったファイルの構造体。 複数の属性を検索するには、ビットごとの OR を使用して (&#124;) 演算子。 次の属性の任意の組み合わせが、許容されます。

- FILE_ATTRIBUTE_ARCHIVE ファイルは、アーカイブ ファイルです。 アプリケーションでは、この属性を使用して、ファイルをバックアップまたは削除のマークします。

- FILE_ATTRIBUTE_COMPRESSED ファイルまたはディレクトリは圧縮されます。 ファイルをすべてのファイルにデータが圧縮されていることを意味します。 ディレクトリが新しく作成されたファイルとサブディレクトリの既定値で圧縮されることを意味します。

- FILE_ATTRIBUTE_DIRECTORY ファイルはディレクトリです。

- FILE_ATTRIBUTE_NORMAL ファイルには、他の属性セットがありません。 この属性は、単独で使用される場合にのみ有効です。 その他のすべてのファイル属性は、この属性をオーバーライドします。

- FILE_ATTRIBUTE_HIDDEN ファイルは表示されません。 通常のディレクトリ一覧に含めることは。

- FILE_ATTRIBUTE_READONLY ファイルは読み取り専用です。 アプリケーションできますファイルの読み取りことはできませんへの書き込みまたは削除します。

- FILE_ATTRIBUTE_SYSTEM ファイルの一部であるまたはオペレーティング システムによって排他的に使用されます。

- FILE_ATTRIBUTE_TEMPORARY ファイルは、一時的なストレージの使用されています。 アプリケーションは、どうしても必要な場合にのみ、ファイルを書き込む必要があります。 ファイルのデータのほとんどは、ファイルがすぐに削除されるため、メディアに書き込まれずに、メモリに残ります。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 拡張エラー情報を取得するには、Win32 関数を呼び出す[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)します。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`MatchesMask`します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#35](../../atl-mfc-shared/reference/codesnippet/cpp/cfilefind-class_5.cpp)]

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind クラス](../../mfc/reference/cftpfilefind-class.md)<br/>
[CGopherFileFind クラス](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile クラス](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile クラス](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile クラス](../../mfc/reference/chttpfile-class.md)
