---
title: CFtpConnection クラス
ms.date: 08/29/2019
f1_keywords:
- CFtpConnection
- AFXINET/CFtpConnection
- AFXINET/CFtpConnection::CFtpConnection
- AFXINET/CFtpConnection::Command
- AFXINET/CFtpConnection::CreateDirectory
- AFXINET/CFtpConnection::GetCurrentDirectory
- AFXINET/CFtpConnection::GetCurrentDirectoryAsURL
- AFXINET/CFtpConnection::GetFile
- AFXINET/CFtpConnection::OpenFile
- AFXINET/CFtpConnection::PutFile
- AFXINET/CFtpConnection::Remove
- AFXINET/CFtpConnection::RemoveDirectory
- AFXINET/CFtpConnection::Rename
- AFXINET/CFtpConnection::SetCurrentDirectory
helpviewer_keywords:
- CFtpConnection [MFC], CFtpConnection
- CFtpConnection [MFC], Command
- CFtpConnection [MFC], CreateDirectory
- CFtpConnection [MFC], GetCurrentDirectory
- CFtpConnection [MFC], GetCurrentDirectoryAsURL
- CFtpConnection [MFC], GetFile
- CFtpConnection [MFC], OpenFile
- CFtpConnection [MFC], PutFile
- CFtpConnection [MFC], Remove
- CFtpConnection [MFC], RemoveDirectory
- CFtpConnection [MFC], Rename
- CFtpConnection [MFC], SetCurrentDirectory
ms.assetid: 5e3a0501-8893-49cf-a3d5-0628d8d6b936
ms.openlocfilehash: 94ee4cb938ee061470282eb2f08a94d83c908805
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177283"
---
# <a name="cftpconnection-class"></a>CFtpConnection クラス

インターネットサーバーへの FTP 接続を管理し、そのサーバー上のディレクトリとファイルを直接操作できるようにします。

## <a name="syntax"></a>構文

```
class CFtpConnection : public CInternetConnection
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFtpConnection:: CFtpConnection](#cftpconnection)|`CFtpConnection` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFtpConnection:: Command](#command)|FTP サーバーに直接コマンドを送信します。|
|[CFtpConnection::CreateDirectory](#createdirectory)|サーバーにディレクトリを作成します。|
|[CFtpConnection::GetCurrentDirectory](#getcurrentdirectory)|この接続の現在のディレクトリを取得します。|
|[CFtpConnection::GetCurrentDirectoryAsURL](#getcurrentdirectoryasurl)|この接続の現在のディレクトリを URL として取得します。|
|[CFtpConnection::GetFile](#getfile)|接続されているサーバーからファイルを取得します。|
|[CFtpConnection::OpenFile](#openfile)|接続されたサーバー上のファイルを開きます。|
|[CFtpConnection::PutFile](#putfile)|サーバーにファイルを配置します。|
|[CFtpConnection::Remove](#remove)|サーバーからファイルを削除します。|
|[CFtpConnection::RemoveDirectory](#removedirectory)|指定されたディレクトリをサーバーから削除します。|
|[CFtpConnection:: Rename](#rename)|サーバー上のファイルの名前を変更します。|
|[CFtpConnection:: SetCurrentDirectory](#setcurrentdirectory)|現在の FTP ディレクトリを設定します。|

## <a name="remarks"></a>Remarks

FTP は、MFC WinInet クラスによって認識される3つのインターネットサービスの1つです。

FTP インターネットサーバーと通信するには、まず[CInternetSession](../../mfc/reference/cinternetsession-class.md)のインスタンスを作成し、次にオブジェクトを`CFtpConnection`作成する必要があります。 オブジェクトを`CFtpConnection`直接作成することはありません。代わりに、 [CInternetSession:: getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection) `CFtpConnection`を呼び出します。これにより、オブジェクトが作成され、ポインターが返されます。

が他の MFC インターネット`CFtpConnection`クラスと連携する方法の詳細については、「 [WinInet を使用したインターネットプログラミング](../../mfc/win32-internet-extensions-wininet.md)」を参照してください。 サポートされている他の2つのサービス (HTTP および gopher) との通信の詳細については、「 [CHttpConnection](../../mfc/reference/chttpconnection-class.md) and [CGopherConnection](../../mfc/reference/cgopherconnection-class.md)クラス」を参照してください。

## <a name="example"></a>例

  [CFtpFileFind](../../mfc/reference/cftpfilefind-class.md)クラスの概要の例を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)

`CFtpConnection`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

##  <a name="cftpconnection"></a>CFtpConnection:: CFtpConnection

このメンバー関数は、オブジェクトを`CFtpConnection`構築するために呼び出されます。

```
CFtpConnection(
    CInternetSession* pSession,
    HINTERNET hConnected,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext);

CFtpConnection(
    CInternetSession* pSession,
    LPCTSTR pstrServer,
    LPCTSTR pstrUserName = NULL,
    LPCTSTR pstrPassword = NULL,
    DWORD_PTR dwContext = 0,
    INTERNET_PORT nPort = INTERNET_INVALID_PORT_NUMBER,
    BOOL bPassive = FALSE);
```

### <a name="parameters"></a>パラメーター

*pSession*<br/>
関連する[CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトへのポインター。

*hConnected*<br/>
現在のインターネットセッションの Windows ハンドル。

*pstrServer*<br/>
FTP サーバー名を含む文字列へのポインターです。

*dwContext*<br/>
操作のコンテキスト識別子。 *dwContext*は、 [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)によって返される操作の状態情報を識別します。 既定値は1に設定されています。ただし、操作の特定のコンテキスト ID を明示的に割り当てることができます。 オブジェクトとそれが実行する作業は、そのコンテキスト ID に関連付けられます。

*pstrUserName*<br/>
ログインするユーザーの名前を指定する null で終わる文字列へのポインター。 NULL の場合、既定値は anonymous です。

*pstrPassword*<br/>
ログインに使用するパスワードを指定する null で終わる文字列へのポインター。 *PstrPassword*と*pstrUserName*の両方が NULL の場合、既定の匿名パスワードはユーザーの電子メール名になります。 *PstrPassword*が null (または空の文字列) であるにもかかわらず*pstrUserName*が null でない場合は、空白のパスワードが使用されます。 次の表では、 *pstrUserName*と*pstrPassword*の4つの設定の動作について説明します。

|*pstrUserName*|*pstrPassword*|FTP サーバーに送信されたユーザー名|FTP サーバーに送信されるパスワード|
|--------------------|--------------------|---------------------------------|---------------------------------|
|NULL または ""|NULL または ""|非同期|ユーザーの電子メール名|
|NULL 以外の文字列|NULL または ""|*pstrUserName*|" "|
|Null 以外の文字列|ERROR|ERROR||
|NULL 以外の文字列|NULL 以外の文字列|*pstrUserName*|*pstrPassword*|

*nPort*<br/>
サーバーで使用する TCP/IP ポートを識別する番号。

*bPassive*<br/>
この FTP セッションのパッシブモードまたはアクティブモードを指定します。 TRUE に設定すると、Win32 API *Dwflag*が INTERNET_FLAG_PASSIVE に設定されます。

### <a name="remarks"></a>Remarks

オブジェクトを`CFtpConnection`直接作成することはありません。 代わりに、 `CFptConnection`オブジェクトを作成する[CInternetSession:: getftpconnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)を呼び出します。

##  <a name="command"></a>CFtpConnection:: Command

FTP サーバーに直接コマンドを送信します。

```
CInternetFile* Command(
    LPCTSTR pszCommand,
    CmdResponseType eResponse = CmdRespNone,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*pszCommand*<br/>
送信されるコマンドが含まれている文字列へのポインター。

*eResponse*<br/>
FTP サーバーからの応答が必要かどうかを指定します。 次のいずれかの値になります。

- `CmdRespNone`応答は必要ありません。
- `CmdRespRead`応答が必要です。
- `CmdRespWrite`使用しません。

CmdResponseType は、 *afxinet.h*で定義されている CFtpConnection のメンバーです。

*dwFlags*<br/>
この関数を制御するフラグが含まれている値。 完全な一覧については、「 [Ftpcommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw)」を参照してください。

*dwContext*<br/>
コールバックでアプリケーションのコンテキストを識別するために使用されるアプリケーション定義の値が含まれている値へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [Ftpcommand](/windows/win32/api/wininet/nf-wininet-ftpcommandw)関数の機能をエミュレートします。

エラーが発生した場合、MFC は[CInternetException](../../mfc/reference/cinternetexception-class.md)型の例外をスローします。

##  <a name="createdirectory"></a>  CFtpConnection::CreateDirectory

接続されたサーバーにディレクトリを作成するには、このメンバー関数を呼び出します。

```
BOOL CreateDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>パラメーター

*pstrDirName*<br/>
作成するディレクトリの名前を格納している文字列へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Windows の関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

サーバー `GetCurrentDirectory`へのこの接続に使用する現在の作業ディレクトリを確認するには、を使用します。 リモートシステムがルートディレクトリに接続していることを想定しないでください。

パラメーター `pstrDirName`には、現在のディレクトリに対して相対的な部分的または完全修飾ファイル名を指定できます。 円記号 (\\) またはスラッシュ (/) は、いずれかの名前のディレクトリ区切り記号として使用できます。 `CreateDirectory`ディレクトリ名の区切り記号を使用する前に適切な文字に変換します。

##  <a name="getcurrentdirectory"></a>  CFtpConnection::GetCurrentDirectory

現在のディレクトリの名前を取得するには、このメンバー関数を呼び出します。

```
BOOL GetCurrentDirectory(CString& strDirName) const;

BOOL GetCurrentDirectory(
    LPTSTR pstrDirName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>パラメーター

*strDirName*<br/>
ディレクトリの名前を受け取る文字列への参照。

*pstrDirName*<br/>
ディレクトリの名前を受け取る文字列へのポインター。

*lpdwLen*<br/>
次の情報を含む DWORD へのポインター。

|||
|-|-|
|入力時|*PstrDirName*によって参照されるバッファーのサイズ。|
|戻るとき|*PstrDirName*に格納されている文字数。 メンバー関数が失敗し、ERROR_INSUFFICIENT_BUFFER が返された場合、 *lpdwLen*には、アプリケーションが文字列を受信するために割り当てる必要があるバイト数が含まれます。|

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

代わりに、URL としてディレクトリ名を取得するには、 [Getcurrentdirectoryasurl](#getcurrentdirectoryasurl)を呼び出します。

パラメーター *pstrDirName*または*strdirname*は、現在のディレクトリに対して相対的なファイル名または完全修飾名のいずれかにすることができます。 円記号 (\\) またはスラッシュ (/) は、いずれかの名前のディレクトリ区切り記号として使用できます。 `GetCurrentDirectory`ディレクトリ名の区切り記号を使用する前に適切な文字に変換します。

##  <a name="getcurrentdirectoryasurl"></a>  CFtpConnection::GetCurrentDirectoryAsURL

現在のディレクトリの名前を URL として取得するには、このメンバー関数を呼び出します。

```
BOOL GetCurrentDirectoryAsURL(CString& strDirName) const;

BOOL GetCurrentDirectoryAsURL(
    LPTSTR pstrName,
    LPDWORD lpdwLen) const;
```

### <a name="parameters"></a>パラメーター

*strDirName*<br/>
ディレクトリの名前を受け取る文字列への参照。

*pstrDirName*<br/>
ディレクトリの名前を受け取る文字列へのポインター。

*lpdwLen*<br/>
次の情報を含む DWORD へのポインター。

|||
|-|-|
|入力時|*PstrDirName*によって参照されるバッファーのサイズ。|
|戻るとき|*PstrDirName*に格納されている文字数。 メンバー関数が失敗し、ERROR_INSUFFICIENT_BUFFER が返された場合、 *lpdwLen*には、アプリケーションが文字列を受信するために割り当てる必要があるバイト数が含まれます。|

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

`GetCurrentDirectoryAsURL`[Getcurrentdirectory](#getcurrentdirectory)と同じように動作します。

*Strdirname*パラメーターは、現在のディレクトリまたは完全修飾名を基準とした、部分的に修飾されたファイル名のいずれかになります。 円記号 (\\) またはスラッシュ (/) は、いずれかの名前のディレクトリ区切り記号として使用できます。 `GetCurrentDirectoryAsURL`ディレクトリ名の区切り記号を使用する前に適切な文字に変換します。

##  <a name="getfile"></a>  CFtpConnection::GetFile

FTP サーバーからファイルを取得し、ローカルコンピューターに保存するには、このメンバー関数を呼び出します。

```
BOOL GetFile(
    LPCTSTR pstrRemoteFile,
    LPCTSTR pstrLocalFile,
    BOOL bFailIfExists = TRUE,
    DWORD dwAttributes = FILE_ATTRIBUTE_NORMAL,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*pstrRemoteFile*<br/>
FTP サーバーから取得するファイルの名前を格納している、null で終わる文字列へのポインター。

*pstrLocalFile*<br/>
ローカルシステム上に作成するファイルの名前を格納している、null で終わる文字列へのポインター。

*bFailIfExists*<br/>
ファイル名が既存のファイルで既に使用されている可能性があるかどうかを示します。 ローカルファイル名が既に存在し、このパラメーターが TRUE の`GetFile`場合、は失敗します。 それ以外`GetFile`の場合は、によってファイルの既存のコピーが削除されます。

*dwAttributes*<br/>
ファイルの属性を示します。 これは、次の FILE_ATTRIBUTE_ * フラグの任意の組み合わせにすることができます。

- FILE_ATTRIBUTE_ARCHIVE ファイルはアーカイブファイルです。 アプリケーションでは、この属性を使用して、バックアップまたは削除するファイルをマークします。

- FILE_ATTRIBUTE_COMPRESSED ファイルまたはディレクトリが圧縮されていることを示します。 ファイルの場合、圧縮とは、ファイル内のすべてのデータが圧縮されることを意味します。 ディレクトリの場合、新しく作成されたファイルおよびサブディレクトリの既定値は compression です。

- FILE_ATTRIBUTE_DIRECTORY ファイルはディレクトリです。

- FILE_ATTRIBUTE_NORMAL ファイルに他の属性が設定されていません。 この属性は、単独で使用した場合にのみ有効です。 その他のすべてのファイル属性は FILE_ATTRIBUTE_NORMAL をオーバーライドします。

- FILE_ATTRIBUTE_HIDDEN ファイルが非表示になっています。 通常のディレクトリの一覧に含めることはできません。

- FILE_ATTRIBUTE_READONLY ファイルは読み取り専用です。 アプリケーションはファイルを読み取ることができますが、書き込むことや削除することはできません。

- FILE_ATTRIBUTE_SYSTEM ファイルがの一部であるか、オペレーティングシステムによって排他的に使用されています。

- FILE_ATTRIBUTE_TEMPORARY ファイルが一時ストレージに使用されています。 アプリケーションは、絶対に必要な場合にのみファイルに書き込む必要があります。 ファイルはすぐに削除されるため、ファイルのデータのほとんどは、メディアにフラッシュされることなくメモリに残ります。

*dwFlags*<br/>
転送を実行する条件を指定します。 このパラメーターには、Windows SDK の[Ftpgetfile](/windows/win32/api/wininet/nf-wininet-ftpgetfilew)に記述されている任意の*dwFlags*値を指定できます。

*dwContext*<br/>
ファイル取得のコンテキスト識別子。 *DwContext*の詳細については、「**解説**」を参照してください。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

`GetFile`は、FTP サーバーからのファイルの読み取りおよびローカルでのファイルの保存に関連するすべてのオーバーヘッドを処理する、高レベルのルーチンです。 ファイルデータのみを取得するか、ファイル転送を制御する必要があるアプリケーションでは`OpenFile` 、と[CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read)を使用する必要があります。

*DwFlags*が FILE_TRANSFER_TYPE_ASCII の場合、ファイルデータの変換によって、制御文字と書式設定文字も Windows の同等のものに変換されます。 既定の転送はバイナリモードであり、ファイルはサーバーに格納されているのと同じ形式でダウンロードされます。

*PstrRemoteFile*と*pstrLocalFile*はどちらも、現在のディレクトリまたは完全修飾ファイルの相対ファイル名のいずれかになります。 円記号 (\\) またはスラッシュ (/) は、いずれかの名前のディレクトリ区切り記号として使用できます。 `GetFile`ディレクトリ名の区切り記号を使用する前に適切な文字に変換します。

*DwContext*の既定値をオーバーライドして、コンテキスト識別子を任意の値に設定します。 コンテキスト識別子は、その[CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトによって作成`CFtpConnection`されるオブジェクトのこの特定の操作に関連付けられます。 値は[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)に返され、識別された操作の状態が示されます。 インターネットの最初[の手順に関する記事を参照してください。WinInet](../../mfc/wininet-basics.md)の詳細については、「」を参照してください。

##  <a name="openfile"></a>  CFtpConnection::OpenFile

読み取りまたは書き込みのために FTP サーバー上にあるファイルを開くには、このメンバー関数を呼び出します。

```
CInternetFile* OpenFile(
    LPCTSTR pstrFileName,
    DWORD dwAccess = GENERIC_READ,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*pstrFileName*<br/>
開くファイルの名前を格納している文字列へのポインター。

*dwAccess*<br/>
ファイルへのアクセス方法を決定します。 GENERIC_READ または GENERIC_WRITE のいずれかを指定できますが、両方を指定することはできません。

*dwFlags*<br/>
後続の転送が発生する条件を指定します。 次の FTP_TRANSFER_ * 定数のいずれかを指定できます。

- FTP ASCII (Type A) 転送方法を使用してファイル転送を FTP_TRANSFER_TYPE_ASCII します。 コントロールと書式設定の情報を、それと等価なローカルのに変換します。

- FTP_TRANSFER_TYPE_BINARY ファイルは、FTP のイメージ (タイプ I) 転送方法を使用してデータを転送します。 ファイルは、データが存在する場合とまったく同じように転送されますが、変更はありません。 これは、既定の転送方法です。

*dwContext*<br/>
ファイルを開くためのコンテキスト識別子。 *DwContext*の詳細については、「**解説**」を参照してください。

### <a name="return-value"></a>戻り値

[CInternetFile](../../mfc/reference/cinternetfile-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

`OpenFile`は、次の状況で使用する必要があります。

- アプリケーションには、FTP サーバー上のファイルとして送信して作成する必要があるデータが含まれていますが、そのデータはローカルファイルにはありません。 ファイル`OpenFile`を開くと、アプリケーションは[CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write)を使用して FTP ファイルデータをサーバーに送信します。

- アプリケーションは、サーバーからファイルを取得し、それをディスクに書き込むのではなく、アプリケーションで制御されたメモリに配置する必要があります。 アプリケーションでは、を使用して`OpenFile`ファイルを開くと、 [CInternetFile:: Read](../../mfc/reference/cinternetfile-class.md#read)が使用されます。

- アプリケーションでは、ファイル転送を細かく制御する必要があります。 たとえば、アプリケーションでは、ファイルのダウンロード中にファイル転送ステータスの進行状況を示す進行状況コントロールを表示することができます。

`OpenFile` の呼び出しから `CInternetConnection::Close` の呼び出しまでの間にアプリケーションで呼び出すことができるのは、[CInternetFile::Read](../../mfc/reference/cinternetfile-class.md#read)、[CInternetFile::Write](../../mfc/reference/cinternetfile-class.md#write)、`CInternetConnection::Close`、または [CFtpFileFind::FindFile](../../mfc/reference/cftpfilefind-class.md#findfile) のみです。 同じ FTP セッションに対する他の FTP 関数の呼び出しは失敗し、エラーコードは FTP_ETRANSFER_IN_PROGRESS に設定されます。

*PstrFileName*パラメーターには、現在のディレクトリを基準とした、または完全に修飾された部分的なファイル名を指定できます。 円記号 (\\) またはスラッシュ (/) は、いずれかの名前のディレクトリ区切り記号として使用できます。 `OpenFile`ディレクトリ名の区切り記号を使用する前に、適切な文字に変換します。

*DwContext*の既定値をオーバーライドして、コンテキスト識別子を任意の値に設定します。 コンテキスト識別子は、その[CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトによって作成`CFtpConnection`されるオブジェクトのこの特定の操作に関連付けられます。 値は[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)に返され、識別された操作の状態が示されます。 インターネットの最初[の手順に関する記事を参照してください。WinInet](../../mfc/wininet-basics.md)の詳細については、「」を参照してください。

##  <a name="putfile"></a>  CFtpConnection::PutFile

FTP サーバーにファイルを格納するには、このメンバー関数を呼び出します。

```
BOOL PutFile(
    LPCTSTR pstrLocalFile,
    LPCTSTR pstrRemoteFile,
    DWORD dwFlags = FTP_TRANSFER_TYPE_BINARY,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*pstrLocalFile*<br/>
ローカルシステムから送信するファイルの名前を格納している文字列へのポインター。

*pstrRemoteFile*<br/>
FTP サーバー上に作成するファイルの名前を含む文字列へのポインターです。

*dwFlags*<br/>
ファイルの転送が発生する条件を指定します。 は、「 [OpenFile](#openfile)」で説明されている FTP_TRANSFER_ * 定数のいずれかになります。

*dwContext*<br/>
ファイルを配置するためのコンテキスト識別子。 *DwContext*の詳細については、「**解説**」を参照してください。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

`PutFile`は、FTP サーバーへのファイルの保存に関連するすべての操作を処理する、高レベルのルーチンです。 データを送信するか、ファイル転送をより細かく制御する必要があるアプリケーションは、 [OpenFile](#openfile)と[CInternetFile:: Write](../../mfc/reference/cinternetfile-class.md#write)を使用する必要があります。

`dwContext` の既定値をオーバーライドして、コンテキスト識別子を独自の値に設定します。 コンテキスト識別子は、その[CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトによって作成`CFtpConnection`されるオブジェクトのこの特定の操作に関連付けられます。 値は[CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)に返され、識別された操作の状態が示されます。 インターネットの最初[の手順に関する記事を参照してください。WinInet](../../mfc/wininet-basics.md)の詳細については、「」を参照してください。

##  <a name="remove"></a>  CFtpConnection::Remove

このメンバー関数を呼び出して、接続されているサーバーから指定されたファイルを削除します。

```
BOOL Remove(LPCTSTR pstrFileName);
```

### <a name="parameters"></a>パラメーター

*pstrFileName*<br/>
削除するファイル名を格納している文字列へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

*PstrFileName*パラメーターには、現在のディレクトリを基準とした、または完全に修飾された部分的なファイル名を指定できます。 円記号 (\\) またはスラッシュ (/) は、いずれかの名前のディレクトリ区切り記号として使用できます。 関数`Remove`は、使用される前に、ディレクトリ名の区切り記号を適切な文字に変換します。

##  <a name="removedirectory"></a>  CFtpConnection::RemoveDirectory

このメンバー関数を呼び出して、接続されているサーバーから指定したディレクトリを削除します。

```
BOOL RemoveDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>パラメーター

*pstrDirName*<br/>
削除するディレクトリを含む文字列へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

[Getcurrentdirectory](#getcurrentdirectory)を使用して、サーバーの現在の作業ディレクトリを特定します。 リモートシステムがルートディレクトリに接続していることを想定しないでください。

*PstrDirName*パラメーターには、現在のディレクトリを基準とした、部分的または完全に修飾されたファイル名を指定できます。 円記号 (\\) またはスラッシュ (/) は、いずれかの名前のディレクトリ区切り記号として使用できます。 `RemoveDirectory`ディレクトリ名の区切り記号を使用する前に適切な文字に変換します。

##  <a name="rename"></a>  CFtpConnection::Rename

接続されたサーバー上の指定したファイルの名前を変更するには、このメンバー関数を呼び出します。

```
BOOL Rename(
    LPCTSTR pstrExisting,
    LPCTSTR pstrNew);
```

### <a name="parameters"></a>パラメーター

*pstrExisting*<br/>
名前を変更するファイルの現在の名前を格納している文字列へのポインター。

*pstrNew*<br/>
ファイルの新しい名前を格納している文字列へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

*PstrExisting*パラメーターと*pstrNew*パラメーターには、現在のディレクトリを基準とした、または完全修飾されたファイル名のいずれかを指定できます。 円記号 (\\) またはスラッシュ (/) は、いずれかの名前のディレクトリ区切り記号として使用できます。 `Rename`ディレクトリ名の区切り記号を使用する前に適切な文字に変換します。

##  <a name="setcurrentdirectory"></a>  CFtpConnection::SetCurrentDirectory

このメンバー関数を呼び出して、FTP サーバー上の別のディレクトリに変更します。

```
BOOL SetCurrentDirectory(LPCTSTR pstrDirName);
```

### <a name="parameters"></a>パラメーター

*pstrDirName*<br/>
ディレクトリの名前を格納している文字列へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

*PstrDirName*パラメーターには、現在のディレクトリを基準とした、部分的または完全に修飾されたファイル名を指定できます。 円記号 (\\) またはスラッシュ (/) は、いずれかの名前のディレクトリ区切り記号として使用できます。 `SetCurrentDirectory`ディレクトリ名の区切り記号を使用する前に適切な文字に変換します。

[Getcurrentdirectory](#getcurrentdirectory)を使用して、FTP サーバーの現在の作業ディレクトリを特定します。 リモートシステムがルートディレクトリに接続していることを想定しないでください。

## <a name="see-also"></a>関連項目

[CInternetConnection クラス](../../mfc/reference/cinternetconnection-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection クラス](../../mfc/reference/cinternetconnection-class.md)<br/>
[CInternetSession クラス](../../mfc/reference/cinternetsession-class.md)
