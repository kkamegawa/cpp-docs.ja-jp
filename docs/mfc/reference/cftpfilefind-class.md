---
title: CFtpFileFind クラス
ms.date: 11/04/2016
f1_keywords:
- CFtpFileFind
- AFXINET/CFtpFileFind
- AFXINET/CFtpFileFind::CFtpFileFind
- AFXINET/CFtpFileFind::FindFile
- AFXINET/CFtpFileFind::FindNextFile
- AFXINET/CFtpFileFind::GetFileURL
helpviewer_keywords:
- CFtpFileFind [MFC], CFtpFileFind
- CFtpFileFind [MFC], FindFile
- CFtpFileFind [MFC], FindNextFile
- CFtpFileFind [MFC], GetFileURL
ms.assetid: 9667cf01-657f-4b11-b9db-f11e5a7b4e4c
ms.openlocfilehash: 2f4a394e29be135cac95edf6f504d8b066f53414
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506246"
---
# <a name="cftpfilefind-class"></a>CFtpFileFind クラス

FTP サーバーのインターネット ファイル検索を支援します。

## <a name="syntax"></a>構文

```
class CFtpFileFind : public CFileFind
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFtpFileFind::CFtpFileFind](#cftpfilefind)|`CFtpFileFind` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFtpFileFind::FindFile](#findfile)|FTP サーバー上のファイルを検索します。|
|[CFtpFileFind::FindNextFile](#findnextfile)|以前の[FindFile](#findfile)の呼び出しからファイル検索を続行します。|
|[CFtpFileFind::GetFileURL](#getfileurl)|検出されたファイルの URL (パスを含む) を取得します。|

## <a name="remarks"></a>Remarks

`CFtpFileFind`には、検索を開始し、ファイルを検索し、そのファイルについての URL またはその他の説明情報を返すメンバー関数が含まれています。

インターネット用に設計されたその他の MFC クラスと検索対象のローカルファイルには、 [CGopherFileFind](../../mfc/reference/cgopherfilefind-class.md)と[CFileFind](../../mfc/reference/cfilefind-class.md)があります。 これらの`CFtpFileFind`クラスは、と共に、サーバープロトコルまたはファイルの種類 (ローカルコンピューターまたはリモートサーバー) に関係なく、クライアントが特定のファイルを検索するためのシームレスなメカニズムを提供します。 Http では検索に必要な直接ファイル操作がサポートされていないため、HTTP サーバーを検索するための MFC クラスは存在しないことに注意してください。

とその他の wininet クラスの`CFtpFileFind`使用方法の詳細については、「 [wininet を使用したインターネットプログラミング](../../mfc/win32-internet-extensions-wininet.md)」を参照してください。

## <a name="example"></a>例

次のコードは、FTP サーバーの現在のディレクトリにあるすべてのファイルを列挙する方法を示しています。

[!code-cpp[NVC_MFCWinInet#8](../../mfc/codesnippet/cpp/cftpfilefind-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFileFind](../../mfc/reference/cfilefind-class.md)

`CFtpFileFind`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

##  <a name="cftpfilefind"></a>  CFtpFileFind::CFtpFileFind

このメンバー関数は、オブジェクトを`CFtpFileFind`構築するために呼び出されます。

```
explicit CFtpFileFind(
    CFtpConnection* pConnection,
    DWORD_PTR dwContext = 1);
```

### <a name="parameters"></a>パラメーター

*pConnection*<br/>
`CFtpConnection` オブジェクトへのポインター。 FTP 接続を取得するには、 [CInternetSession:: GetFtpConnection](../../mfc/reference/cinternetsession-class.md#getftpconnection)を呼び出します。

*dwContext*<br/>
`CFtpFileFind`オブジェクトのコンテキスト識別子。 このパラメーターの詳細については、「**解説**」を参照してください。

### <a name="remarks"></a>Remarks

*DwContext*の既定値は、 `CFtpFileFind` `CFtpFileFind`オブジェクトを作成した[CInternetSession](../../mfc/reference/cinternetsession-class.md)オブジェクトからオブジェクトに、MFC によって送信されます。 既定値を上書きして、コンテキスト識別子を任意の値に設定できます。 コンテキスト識別子は、 [CInternetSession:: OnStatusCallback](../../mfc/reference/cinternetsession-class.md#onstatuscallback)に返され、識別されたオブジェクトの状態を提供します。 インターネットの最初[の手順に関する記事を参照してください。WinInet](../../mfc/wininet-basics.md)の詳細については、「」を参照してください。

### <a name="example"></a>例

  このトピックで前述した「クラスの概要」の例を参照してください。

##  <a name="findfile"></a>  CFtpFileFind::FindFile

FTP ファイルを検索するには、このメンバー関数を呼び出します。

```
virtual BOOL FindFile(
    LPCTSTR pstrName = NULL,
    DWORD dwFlags = INTERNET_FLAG_RELOAD);
```

### <a name="parameters"></a>パラメーター

*pstrName*<br/>
検索するファイルの名前を格納している文字列へのポインター。 NULL の場合、呼び出しはワイルドカード検索 (*) を実行します。

*dwFlags*<br/>
このセッションの処理方法を説明するフラグ。 これらのフラグは、ビットごとの OR 演算子 (&#124;) と組み合わせることができ、次のようになります。

- INTERNET_FLAG_RELOAD は、ローカルにキャッシュされている場合でも、ネットワークからデータを取得します。 これは既定のフラグです。

- INTERNET_FLAG_DONT_CACHE は、ローカルまたはどのゲートウェイにもデータをキャッシュしません。

- INTERNET_FLAG_RAW_DATA RAW データ (FTP の[WIN32_FIND_DATA](/windows/win32/api/minwinbase/ns-minwinbase-win32_find_dataw)構造体) を返すように既定値をオーバーライドします。

- INTERNET_FLAG_SECURE は、Secure Sockets Layer または PCT でネットワーク上のトランザクションをセキュリティで保護します。 このフラグは、HTTP 要求にのみ適用されます。

- INTERNET_FLAG_EXISTING_CONNECT 可能な場合は、要求ごとに新しいセッションを作成`FindFile`するのではなく、新しい要求に対してサーバーへの既存の接続を再利用します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 拡張されたエラー情報を取得するには、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出します。

### <a name="remarks"></a>Remarks

を呼び出し`FindFile`て最初の ftp ファイルを取得した後、 [FindNextFile](#findnextfile)を呼び出して、後続の ftp ファイルを取得できます。

### <a name="example"></a>例

  このトピックの前の例を参照してください。

##  <a name="findnextfile"></a>  CFtpFileFind::FindNextFile

[FindFile](#findfile)メンバー関数の呼び出しで開始されたファイル検索を続行するには、このメンバー関数を呼び出します。

```
virtual BOOL FindNextFile();
```

### <a name="return-value"></a>戻り値

他のファイルがある場合は0以外。見つかったファイルがディレクトリ内の最後のファイルであるか、エラーが発生した場合は0。 拡張されたエラー情報を取得するには、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出します。 見つかったファイルがディレクトリ内の最後のファイルである場合、または一致するファイルが見つからない`GetLastError`場合、関数は ERROR_NO_MORE_FILES を返します。

### <a name="remarks"></a>Remarks

属性関数を呼び出す前に、この関数を少なくとも1回呼び出す必要があります (「 [CFileFind:: FindNextFile](../../mfc/reference/cfilefind-class.md#findnextfile)」を参照してください)。

`FindNextFile`Win32 関数[FindNextFile](/windows/win32/api/fileapi/nf-fileapi-findnextfilew)をラップします。

### <a name="example"></a>例

  このトピックの前半の例を参照してください。

##  <a name="getfileurl"></a>  CFtpFileFind::GetFileURL

このメンバー関数を呼び出して、指定したファイルの URL を取得します。

```
CString GetFileURL() const;
```

### <a name="return-value"></a>戻り値

ユニバーサルリソースロケーター (URL) のファイルとパス。

### <a name="remarks"></a>Remarks

`GetFileURL`は、という形式`ftp://moose/dir/file.txt`の URL を返す点を除いて、メンバー関数[CFileFind:: getfilepath](../../mfc/reference/cfilefind-class.md#getfilepath)に似ています。

## <a name="see-also"></a>関連項目

[CFileFind クラス](../../mfc/reference/cfilefind-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CGopherFileFind クラス](../../mfc/reference/cgopherfilefind-class.md)<br/>
[CInternetFile クラス](../../mfc/reference/cinternetfile-class.md)<br/>
[CGopherFile クラス](../../mfc/reference/cgopherfile-class.md)<br/>
[CHttpFile クラス](../../mfc/reference/chttpfile-class.md)
