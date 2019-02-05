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
ms.openlocfilehash: dafa313d9d2c7aae13e83a891c79d437ac276e08
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894498"
---
# <a name="cgopherfilefind-class"></a>CGopherFileFind クラス

gopher サーバーのインターネット ファイル検索を支援します。

> [!NOTE]
>  クラスは、 `CGopherConnection`、 `CGopherFile`、 `CGopherFileFind`、`CGopherLocator`と Windows XP のプラットフォームで機能しませんが、引き続き以前のプラットフォームで動作するため、そのメンバーが使用されなくなりました。

## <a name="syntax"></a>構文

```
class CGopherFileFind : public CFileFind
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CGopherFileFind::CGopherFileFind](#cgopherfilefind)|`CGopherFileFind` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CGopherFileFind::FindFile](#findfile)|Gopher サーバー上のファイルを検索します。|
|[CGopherFileFind::FindNextFile](#findnextfile)|以前の呼び出しからのファイル検索を続行[FindFile](#findfile)します。|
|[CGopherFileFind::GetCreationTime](#getcreationtime)|指定したファイルが作成された時刻を取得します。|
|[CGopherFileFind::GetLastAccessTime](#getlastaccesstime)|指定したファイルの最終アクセス時刻を取得します。|
|[CGopherFileFind::GetLastWriteTime](#getlastwritetime)|指定したファイルに最後に書き込んだ時刻を取得します。|
|[CGopherFileFind::GetLength](#getlength)|(バイト単位)、見つかったファイルの長さを取得します。|
|[CGopherFileFind::GetLocator](#getlocator)|取得、`CGopherLocator`オブジェクト。|
|[CGopherFileFind::GetScreenName](#getscreenname)|Gopher 画面の名前を取得します。|
|[CGopherFileFind::IsDots](#isdots)|ファイルを反復処理中に現在のディレクトリとその親ディレクトリ マーカーをテストします。|

## <a name="remarks"></a>Remarks

`CGopherFileFind` 検索を開始し、ファイルを検索し、ファイルの URL を返すメンバー関数が含まれています。

インターネットとローカル ファイルの検索含む向けに設計されたその他の MFC クラス[CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)と[CFileFind](../../mfc/reference/cfilefind-class.md)します。 組み合わせて`CGopherFileFind`、これらのクラスは、サーバー プロトコル、ファイルの種類または場所 (ローカル コンピューターまたはリモート サーバーのいずれかです) に関係なく、特定のファイルを検索するユーザーのシームレスなメカニズムを提供。HTTP は検索に必要なファイルを直接操作をサポートしていないために、HTTP サーバー上で検索するための MFC クラスがないことに注意してください。

> [!NOTE]
> `CGopherFileFind` その基本クラスの次のメンバー関数はサポートされません[CFileFind](../../mfc/reference/cfilefind-class.md):

- [GetRoot](../../mfc/reference/cfilefind-class.md#getroot)

- [GetFileName](../../mfc/reference/cfilefind-class.md#getfilename)

- [GetFilePath](../../mfc/reference/cfilefind-class.md#getfilepath)

- [GetFileTitle](../../mfc/reference/cfilefind-class.md#getfiletitle)

- [GetFileURL](../../mfc/reference/cfilefind-class.md#getfileurl)

使用するとさらに、 `CGopherFileFind`、`CFileFind`メンバー関数は[IsDots](../../mfc/reference/cfilefind-class.md#isdots)は常に FALSE。

使用する方法の詳細についての`CGopherFileFind`他 WinInet クラスは、記事を参照して、[インターネットが WinInet を使用したプログラミング](../../mfc/win32-internet-extensions-wininet.md)。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CGopherFileFind`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

##  <a name="cgopherfilefind"></a>  CGopherFileFind::CGopherFileFind

このメンバー関数が構築すると呼ばれる、`CGopherFileFind`オブジェクト。

```
explicit CGopherFileFind(
    CGopherConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*pConnection*<br/>
ポインターを[CGopherConnection](../../mfc/reference/cgopherconnection-class.md)オブジェクト。

*dwContext*<br/>
操作のコンテキストの識別子。 参照してください**解説**の詳細については*独自*します。

### <a name="remarks"></a>Remarks

既定値*独自*に MFC によって送信される、`CGopherFileFind`オブジェクトから、 [CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトの作成、`CGopherFileFind`オブジェクト。 構築する際に、`CGopherFileFind`オブジェクト コンテキスト識別子を独自の値に設定する既定値をオーバーライドすることができます。 コンテキスト識別子が返される[対応](../../mfc/reference/cinternetsession-class.md#onstatuscallback)が識別されるオブジェクトの状態を提供します。 記事をご覧ください[インターネットの最初の手順。WinInet](../../mfc/wininet-basics.md)コンテキスト識別子の詳細についてはします。

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
参照を[CGopherLocator](../../mfc/reference/cgopherlocator-class.md)オブジェクト。

*pstrString*<br/>
ファイル名を含む文字列へのポインター。

*dwFlags*<br/>
このセッションを処理する方法を記述するフラグ。 有効なフラグは次のとおりです。

- INTERNET_FLAG_RELOAD は、ローカルにキャッシュされている場合でも、リモート サーバーからデータを取得します。

- ローカル、またはすべてのゲートウェイでは、データをキャッシュ INTERNET_FLAG_DONT_CACHE しません。

- Secure Sockets Layer の割合と、ネットワーク上でのセキュリティで保護されたトランザクションの INTERNET_FLAG_SECURE 要求 このフラグは、HTTP 要求のみに適用されます。

- INTERNET_FLAG_USE_EXISTING 可能な場合は、新しいサーバーに既存の接続を再利用`FindFile`要求は、要求ごとに新しいセッションを作成する代わりにします。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 拡張エラー情報を取得するには、Win32 関数を呼び出す[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)します。

### <a name="remarks"></a>Remarks

呼び出した後`FindFile`呼び出すことができますを gopher の最初のオブジェクトを取得するには、 [FindNextFile](#findnextfile)後続 gopher ファイルを取得します。

##  <a name="findnextfile"></a>  CGopherFileFind::FindNextFile

呼び出しで開始されたファイルの検索を続行するには、このメンバー関数を呼び出す[CGopherFileFind::FindFile](#findfile)します。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>戻り値

以上のファイルがある場合、0 以外の場合ファイルが見つかりましたが、ディレクトリ内の最後の 1 つである場合や、エラーが発生した場合は 0 します。 拡張エラー情報を取得するには、Win32 関数を呼び出す[GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360)します。 ファイルが見つかりましたが、ディレクトリ内の最後のファイル、または一致する場合は、ファイルが見つからなかんだことができます、 `GetLastError` ERROR_NO_MORE_FILES を返します。

##  <a name="getcreationtime"></a>  CGopherFileFind::GetCreationTime

現在のファイルの作成時刻を取得します。

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

成功した場合、0 以外の場合失敗した場合は 0。 `GetCreationTime` 場合にのみ、0 を返します[FindNextFile](#findnextfile)がこの呼び出さ`CGopherFileFind`オブジェクト。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetCreationTime`します。

> [!NOTE]
>  すべてのファイル システムでは、同じセマンティクスを使用して、この関数によって返されるタイムスタンプを実装します。 この関数は、基になるファイル システムまたはサーバーがサポートしない場合、時間属性を維持することは、その他のタイム スタンプ関数によって返されるのと同じ値を返す可能性があります。 参照してください、 [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)時刻の形式については、構造体。 一部のオペレーティング システムは、ファイルが存在するコンピューターにゾーンのローカル時刻の時刻が返されるがあります。 Win32 を参照してください。[詳細](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime)API の詳細についてはします。

##  <a name="getlastaccesstime"></a>  CGopherFileFind::GetLastAccessTime

指定したファイルの最終アクセス時刻を取得します。

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

成功した場合、0 以外の場合失敗した場合は 0。 `GetLastAccessTime` 場合にのみ、0 を返します[FindNextFile](#findnextfile)がこの呼び出さ`CGopherFileFind`オブジェクト。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetLastAccessTime`します。

> [!NOTE]
>  すべてのファイル システムでは、同じセマンティクスを使用して、この関数によって返されるタイムスタンプを実装します。 この関数は、基になるファイル システムまたはサーバーがサポートしない場合、時間属性を維持することは、その他のタイム スタンプ関数によって返されるのと同じ値を返す可能性があります。 参照してください、 [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)時刻の形式については、構造体。 一部のオペレーティング システムは、ファイルが存在するコンピューターにゾーンのローカル時刻の時刻が返されるがあります。 Win32 を参照してください。[詳細](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime)API の詳細についてはします。

##  <a name="getlastwritetime"></a>  CGopherFileFind::GetLastWriteTime

ファイルが変更された最終時刻を取得します。

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

成功した場合、0 以外の場合失敗した場合は 0。 `GetLastWriteTime` 場合にのみ、0 を返します[FindNextFile](#findnextfile)がこの呼び出さ`CGopherFileFind`オブジェクト。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`GetLastWriteTime`します。

> [!NOTE]
>  すべてのファイル システムでは、同じセマンティクスを使用して、この関数によって返されるタイムスタンプを実装します。 この関数は、基になるファイル システムまたはサーバーがサポートしない場合、時間属性を維持することは、その他のタイム スタンプ関数によって返されるのと同じ値を返す可能性があります。 参照してください、 [Win32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)時刻の形式については、構造体。 一部のオペレーティング システムは、ファイルが存在するコンピューターにゾーンのローカル時刻の時刻が返されるがあります。 Win32 を参照してください。[詳細](/windows/desktop/api/fileapi/nf-fileapi-filetimetolocalfiletime)API の詳細についてはします。

##  <a name="getlength"></a>  CGopherFileFind::GetLength

見つかったファイルのバイト単位の長さを取得するには、このメンバー関数を呼び出します。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>戻り値

見つかったファイルの長さ、(バイト単位)。

### <a name="remarks"></a>Remarks

`GetLength` Win32 構造を使用して[WIN32_FIND_DATA](/windows/desktop/api/minwinbase/ns-minwinbase-_win32_find_dataa)バイト単位でのファイル サイズの値を取得します。

> [!NOTE]
>  時点で、MFC 7.0、 `GetLength` 64 ビット整数型をサポートしています。 この新しいバージョンのライブラリで構築された既存のコードは、切り捨ての警告があります。

### <a name="example"></a>例

  例をご覧ください[結び付けてその中](../../mfc/reference/cfile-class.md#getlength)(基本クラスの実装)。

##  <a name="getlocator"></a>  CGopherFileFind::GetLocator

取得するには、このメンバー関数を呼び出す、 [CGopherLocator](../../mfc/reference/cgopherlocator-class.md)オブジェクトを[FindFile](#findfile)を使用して、gopher ファイルを検索します。

```
CGopherLocator GetLocator() const;
```

### <a name="return-value"></a>戻り値

`CGopherLocator` オブジェクト。

##  <a name="getscreenname"></a>  CGopherFileFind::GetScreenName

Gopher 画面の名前を取得するには、このメンバー関数を呼び出します。

```
CString GetScreenName() const;
```

### <a name="return-value"></a>戻り値

Gopher 画面の名前。

##  <a name="isdots"></a>  CGopherFileFind::IsDots

ファイルを反復処理中に現在のディレクトリとその親ディレクトリ マーカーをテストします。

```
virtual BOOL IsDots() const;
```

### <a name="return-value"></a>戻り値

見つかったファイルが、名前を持つ場合、0 以外の場合".「または」.."、見つかったファイルが実際にディレクトリを示します。 それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

呼び出す必要があります[FindNextFile](#findnextfile)呼び出す前に少なくとも 1 回`IsDots`します。

## <a name="see-also"></a>関連項目

[CFileFind クラス](../../mfc/reference/cfilefind-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CFtpFileFind クラス](../../mfc/reference/cftpfilefind-class.md)<br/>
[CFileFind クラス](../../mfc/reference/cfilefind-class.md)<br/>
[CInternetFile クラス](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile クラス](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile クラス](../../mfc/reference/chttpfile-class.md)
