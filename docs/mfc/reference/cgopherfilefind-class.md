---
title: CGopherFileFind クラス
ms.date: 11/04/2016
f1_keywords:
- CGopherFileFind
- AFXINET/CGopherFileFind
- AFXINET/CGopherFileFind::CGopherFileFind
- AFXINET/CGopherFileFind::FindFile
- AFXINET/CGopherFileFind::FindNextFile
- AFXINET/CGopherFileFind::GetCreationTime
- AFXINET/CGopherFileFind::GetLastAccessTime
- AFXINET/CGopherFileFind::GetLastWriteTime
- AFXINET/CGopherFileFind::GetLength
- AFXINET/CGopherFileFind::GetLocator
- AFXINET/CGopherFileFind::GetScreenName
- AFXINET/CGopherFileFind::IsDots
helpviewer_keywords:
- CGopherFileFind [MFC], CGopherFileFind
- CGopherFileFind [MFC], FindFile
- CGopherFileFind [MFC], FindNextFile
- CGopherFileFind [MFC], GetCreationTime
- CGopherFileFind [MFC], GetLastAccessTime
- CGopherFileFind [MFC], GetLastWriteTime
- CGopherFileFind [MFC], GetLength
- CGopherFileFind [MFC], GetLocator
- CGopherFileFind [MFC], GetScreenName
- CGopherFileFind [MFC], IsDots
ms.assetid: 8465a979-6323-496d-ab4b-e81383fb999d
ms.openlocfilehash: 55c40fc04934f00ccb541a01cce611d9532bee1a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506172"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind クラス

gopher サーバーのインターネット ファイル検索を支援します。

> [!NOTE]
>  クラス`CGopherConnection` 、`CGopherFile`、 、`CGopherLocator`およびそれらのメンバーは、Windows XP プラットフォームでは動作しないため、非推奨とされますが、以前のプラットフォームでも引き続き動作します。 `CGopherFileFind`

## <a name="syntax"></a>構文

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CGopherFileFind:: CGopherFileFind](#cgopherfilefind)|`CGopherFileFind` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|Gopher サーバー上のファイルを検索します。|
|[CGopherFileFind::FindNextFile](#findnextfile)|以前の[FindFile](#findfile)の呼び出しからファイル検索を続行します。|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|指定したファイルが作成された時刻を取得します。|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|指定したファイルに最後にアクセスした時刻を取得します。|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|指定したファイルに最後に書き込みが行われた時刻を取得します。|
|[CGopherFileFind::GetLength](#getlength)|検出されたファイルの長さをバイト単位で取得します。|
|[CGopherFileFind::GetLocator](#getlocator)|オブジェクトを`CGopherLocator`取得します。|
|[CGopherFileFind::GetScreenName](#getscreenname)|Gopher 画面の名前を取得します。|
|[CGopherFileFind::IsDots](#isdots)|ファイルの反復処理中に、現在のディレクトリマーカーと親ディレクトリマーカーをテストします。|

## <a name="remarks"></a>Remarks

`CGopherFileFind`検索を開始し、ファイルを検索して、ファイルの URL を返すメンバー関数が含まれています。

インターネット用に設計されたその他の MFC クラスと検索対象のローカルファイルには、 [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)と[CFileFind](../../mfc/reference/cfilefind-class.md)があります。 これらの`CGopherFileFind`クラスは、と共に、サーバープロトコル、ファイルの種類、場所 (ローカルコンピューターまたはリモートサーバー) に関係なく、ユーザーが特定のファイルを検索するためのシームレスなメカニズムを提供します。Http では検索に必要な直接ファイル操作がサポートされていないため、HTTP サーバーを検索するための MFC クラスは存在しないことに注意してください。

> [!NOTE]
> `CGopherFileFind`は、基底クラス[CFileFind](../../mfc/reference/cfilefind-class.md)の次のメンバー関数をサポートしていません。

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

さらに、と共`CGopherFileFind` `CFileFind`に使用した場合、メンバー関数[isdots](../../mfc/reference/cfilefind-class.md#isdots)は常に FALSE になります。

とその他の wininet クラスの`CGopherFileFind`使用方法の詳細については、「 [wininet を使用したインターネットプログラミング](../../mfc/win32-internet-extensions-wininet.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

##  <a name="cgopherfilefind"></a>  CGopherFileFind::CGopherFileFind

このメンバー関数は、オブジェクトを`CGopherFileFind`構築するために呼び出されます。

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*pConnection*<br/>
[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)オブジェクトへのポインター。

*dwContext*<br/>
操作のコンテキスト識別子。 *DwContext*の詳細については、「**解説**」を参照してください。

### <a name="remarks"></a>Remarks

*DwContext*の既定値は、 `CGopherFileFind` `CGopherFileFind`オブジェクトを作成した[CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトからオブジェクトに、MFC によって送信されます。 `CGopherFileFind`オブジェクトを構築するときに、既定値をオーバーライドして、コンテキスト識別子を任意の値に設定できます。 コンテキスト識別子は、 [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)に返され、識別されたオブジェクトの状態を提供します。 インターネットの最初[の手順に関する記事を参照してください。WinInet](../../mfc/wininet-basics.md)の詳細については、「」を参照してください。

##  <a name="findfile"></a>  CGopherFileFind::FindFile

Gopher ファイルを検索するには、このメンバー関数を呼び出します。

```
virtual BOOL FindFile(
    CGopherLocator& refLocator,
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);

virtual BOOL FindFile(
    LPCTSTR pstrString,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>パラメーター

*refLocator*<br/>
[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)オブジェクトへの参照。

*pstrString*<br/>
ファイル名を格納している文字列へのポインター。

*dwFlags*<br/>
このセッションの処理方法を説明するフラグ。 有効なフラグは次のとおりです。

- INTERNET_FLAG_RELOAD ローカルにキャッシュされている場合でも、リモートサーバーからデータを取得します。

- INTERNET_FLAG_DONT_CACHE は、ローカルまたはどのゲートウェイにもデータをキャッシュしません。

- INTERNET_FLAG_SECURE または PCT Secure Sockets Layer でにセキュリティで保護されたトランザクションを要求します。 このフラグは、HTTP 要求にのみ適用されます。

- INTERNET_FLAG_USE_EXISTING 可能な場合は、要求ごとに新しいセッションを作成`FindFile`するのではなく、新しい要求に対してサーバーへの既存の接続を再利用します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 拡張されたエラー情報を取得するには、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出します。

### <a name="remarks"></a>Remarks

を呼び出し`FindFile`て最初の gopher オブジェクトを取得した後、 [FindNextFile](#findnextfile)を呼び出して、後続の gopher ファイルを取得できます。

##  <a name="findnextfile"></a>  CGopherFileFind::FindNextFile

[CGopherFileFind:: FindFile](#findfile)の呼び出しで開始されたファイル検索を続行するには、このメンバー関数を呼び出します。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>戻り値

他のファイルがある場合は0以外。見つかったファイルがディレクトリ内の最後のファイルであるか、エラーが発生した場合は0。 拡張されたエラー情報を取得するには、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出します。 見つかったファイルがディレクトリ内の最後のファイルである場合、または一致するファイルが見つからない`GetLastError`場合、関数は ERROR_NO_MORE_FILES を返します。

##  <a name="getcreationtime"></a>  CGopherFileFind::GetCreationTime

現在のファイルの作成時刻を取得します。

```
virtual BOOL GetCreationTime(FILETIME* pTimeStamp) const;
virtual BOOL GetCreationTime(CTime& refTime) const;
```

### <a name="parameters"></a>パラメーター

*pTimeStamp*<br/>
ファイルが作成された時刻を格納している[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)構造体へのポインター。

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへの参照。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。失敗した場合は0。 `GetCreationTime`この`CGopherFileFind`オブジェクトで[FindNextFile](#findnextfile)が呼び出されたことがない場合にのみ、0を返します。

### <a name="remarks"></a>Remarks

を呼び出す`GetCreationTime`前に、 [FindNextFile](#findnextfile)を少なくとも1回呼び出す必要があります。

> [!NOTE]
>  すべてのファイルシステムで同じセマンティクスを使用して、この関数によって返されるタイムスタンプが実装されるわけではありません。 基になるファイルシステムまたはサーバーが time 属性の保持をサポートしていない場合、この関数は、他のタイムスタンプ関数から返される値と同じ値を返すことがあります。 時刻形式の詳細については、 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)構造体を参照してください。 一部のオペレーティングシステムでは、返された時間は、コンピューターのローカルのタイムゾーンでファイルが見つかりました。 詳細については、Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API に関する説明を参照してください。

##  <a name="getlastaccesstime"></a>  CGopherFileFind::GetLastAccessTime

指定したファイルに最後にアクセスした時刻を取得します。

```
virtual BOOL GetLastAccessTime(CTime& refTime) const;
virtual BOOL GetLastAccessTime(FILETIME* pTimeStamp) const;
```

### <a name="parameters"></a>パラメーター

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへの参照。

*pTimeStamp*<br/>
ファイルが最後にアクセスされた時刻を格納している[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)構造体へのポインター。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。失敗した場合は0。 `GetLastAccessTime`この`CGopherFileFind`オブジェクトで[FindNextFile](#findnextfile)が呼び出されたことがない場合にのみ、0を返します。

### <a name="remarks"></a>Remarks

を呼び出す`GetLastAccessTime`前に、 [FindNextFile](#findnextfile)を少なくとも1回呼び出す必要があります。

> [!NOTE]
>  すべてのファイルシステムで同じセマンティクスを使用して、この関数によって返されるタイムスタンプが実装されるわけではありません。 基になるファイルシステムまたはサーバーが time 属性の保持をサポートしていない場合、この関数は、他のタイムスタンプ関数から返される値と同じ値を返すことがあります。 時刻形式の詳細については、 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)構造体を参照してください。 一部のオペレーティングシステムでは、返された時間は、コンピューターのローカルのタイムゾーンでファイルが見つかりました。 詳細については、Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API に関する説明を参照してください。

##  <a name="getlastwritetime"></a>  CGopherFileFind::GetLastWriteTime

ファイルが最後に変更された時刻を取得します。

```
virtual BOOL GetLastWriteTime(FILETIME* pTimeStamp) const;
virtual BOOL GetLastWriteTime(CTime& refTime) const;
```

### <a name="parameters"></a>パラメーター

*pTimeStamp*<br/>
ファイルが最後に書き込まれた時刻を格納している[FILETIME](/windows/win32/api/minwinbase/ns-minwinbase-filetime)構造体へのポインター。

*refTime*<br/>
[CTime](../../atl-mfc-shared/reference/ctime-class.md)オブジェクトへの参照。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。失敗した場合は0。 `GetLastWriteTime`この`CGopherFileFind`オブジェクトで[FindNextFile](#findnextfile)が呼び出されたことがない場合にのみ、0を返します。

### <a name="remarks"></a>Remarks

を呼び出す`GetLastWriteTime`前に、 [FindNextFile](#findnextfile)を少なくとも1回呼び出す必要があります。

> [!NOTE]
>  すべてのファイルシステムで同じセマンティクスを使用して、この関数によって返されるタイムスタンプが実装されるわけではありません。 基になるファイルシステムまたはサーバーが time 属性の保持をサポートしていない場合、この関数は、他のタイムスタンプ関数から返される値と同じ値を返すことがあります。 時刻形式の詳細については、 [WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)構造体を参照してください。 一部のオペレーティングシステムでは、返された時間は、コンピューターのローカルのタイムゾーンでファイルが見つかりました。 詳細については、Win32 [FileTimeToLocalFileTime](/windows/win32/api/fileapi/nf-fileapi-filetimetolocalfiletime) API に関する説明を参照してください。

##  <a name="getlength"></a>  CGopherFileFind::GetLength

このメンバー関数を呼び出して、検出されたファイルの長さをバイト単位で取得します。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>戻り値

検出されたファイルの長さ (バイト単位)。

### <a name="remarks"></a>Remarks

`GetLength`Win32 構造体[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)を使用して、ファイルサイズの値をバイト単位で取得します。

> [!NOTE]
>  MFC 7.0 の As で`GetLength`は、は64ビットの整数型をサポートしています。 この新しいバージョンのライブラリでビルドされた既存のコードでは、切り捨ての警告が発生する可能性があります。

### <a name="example"></a>例

  「 [CFile:: GetLength](../../mfc/reference/cfile-class.md#getlength) (基底クラスの実装)」の例を参照してください。

##  <a name="getlocator"></a>  CGopherFileFind::GetLocator

このメンバー関数を呼び出して、 [FindFile](#findfile)が gopher ファイルを検索するために使用する[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)オブジェクトを取得します。

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>戻り値

`CGopherLocator` オブジェクト。

##  <a name="getscreenname"></a>  CGopherFileFind::GetScreenName

このメンバー関数を呼び出して、gopher 画面の名前を取得します。

```
CString GetScreenName() const;
```

### <a name="return-value"></a>戻り値

Gopher 画面の名前。

##  <a name="isdots"></a>  CGopherFileFind::IsDots

ファイルの反復処理中に、現在のディレクトリマーカーと親ディレクトリマーカーをテストします。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>戻り値

見つかったファイルの名前が "." または ".." である場合は0以外の値。見つかったファイルが実際にはディレクトリであることを示します。 それ以外の場合は0です。

### <a name="remarks"></a>Remarks

を呼び出す`IsDots`前に、 [FindNextFile](#findnextfile)を少なくとも1回呼び出す必要があります。

## <a name="see-also"></a>関連項目

[CFileFind クラス](../../mfc/reference/cfilefind-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind クラス](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind クラス](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile クラス](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile クラス](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile クラス](../../mfc/reference/chttpfile-class.md)
