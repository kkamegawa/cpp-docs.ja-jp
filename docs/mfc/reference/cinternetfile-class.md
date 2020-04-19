---
title: CInternetFile クラス
ms.date: 11/04/2016
f1_keywords:
- CInternetFile
- AFXINET/CInternetFile
- AFXINET/CInternetFile::CInternetFile
- AFXINET/CInternetFile::Abort
- AFXINET/CInternetFile::Close
- AFXINET/CInternetFile::Flush
- AFXINET/CInternetFile::GetLength
- AFXINET/CInternetFile::Read
- AFXINET/CInternetFile::ReadString
- AFXINET/CInternetFile::Seek
- AFXINET/CInternetFile::SetReadBufferSize
- AFXINET/CInternetFile::SetWriteBufferSize
- AFXINET/CInternetFile::Write
- AFXINET/CInternetFile::WriteString
- AFXINET/CInternetFile::m_hFile
helpviewer_keywords:
- CInternetFile [MFC], CInternetFile
- CInternetFile [MFC], Abort
- CInternetFile [MFC], Close
- CInternetFile [MFC], Flush
- CInternetFile [MFC], GetLength
- CInternetFile [MFC], Read
- CInternetFile [MFC], ReadString
- CInternetFile [MFC], Seek
- CInternetFile [MFC], SetReadBufferSize
- CInternetFile [MFC], SetWriteBufferSize
- CInternetFile [MFC], Write
- CInternetFile [MFC], WriteString
- CInternetFile [MFC], m_hFile
ms.assetid: 96935681-ee71-4a8d-9783-5abc7b3e6f10
ms.openlocfilehash: 68a0a0f35d1a1f4519401080f9f207bf76c87079
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505897"
---
# <a name="cinternetfile-class"></a>CInternetFile クラス

インターネットプロトコルを使用するリモートシステム上のファイルへのアクセスを許可します。

## <a name="syntax"></a>構文

```
class CInternetFile : public CStdioFile
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CInternetFile:: CInternetFile](#cinternetfile)|`CInternetFile` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CInternetFile::Abort](#abort)|すべての警告とエラーを無視して、ファイルを閉じます。|
|[CInternetFile:: Close](#close)|を`CInternetFile`閉じ、そのリソースを解放します。|
|[CInternetFile:: Flush](#flush)|書き込みバッファーの内容をフラッシュし、メモリ内のデータがターゲットコンピューターに書き込まれることを確認します。|
|[CInternetFile::GetLength](#getlength)|ファイルのサイズを返します。|
|[CInternetFile::Read](#read)|指定したバイト数を読み取ります。|
|[CInternetFile::ReadString](#readstring)|文字のストリームを読み取ります。|
|[CInternetFile:: Seek](#seek)|開いているファイル内のポインターを移動します。|
|[CInternetFile:: SetReadBufferSize](#setreadbuffersize)|データが読み取られるバッファーのサイズを設定します。|
|[CInternetFile:: SetWriteBufferSize](#setwritebuffersize)|データが書き込まれるバッファーのサイズを設定します。|
|[CInternetFile:: Write](#write)|指定したバイト数を書き込みます。|
|[CInternetFile::WriteString](#writestring)|Null で終わる文字列をファイルに書き込みます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CInternetFile:: operator HINTERNET](#operator_hinternet)|インターネットハンドルのキャスト演算子。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CInternetFile:: m_hFile](#m_hfile)|ファイルへのハンドル。|

## <a name="remarks"></a>Remarks

[CHttpFile](../../mfc/reference/chttpfile-class.md)および[CGopherFile](../../mfc/reference/cgopherfile-class.md)ファイルクラスの基本クラスを提供します。 オブジェクトを`CInternetFile`直接作成することはありません。 代わりに、 [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)または[CHttpConnection:: openrequest](../../mfc/reference/chttpconnection-class.md#openrequest)を呼び出して、派生クラスのいずれかのオブジェクトを作成します。 [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)を`CInternetFile`呼び出すことによって、オブジェクトを作成することもできます。

`CInternetFile`メンバー関数`Open` 、、`Duplicate`、およびは、に対し`CInternetFile`て実装されていません。 `UnlockRange` `LockRange` `CInternetFile`オブジェクトに対してこれらの関数を呼び出すと、 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)が得られます。

が他の MFC インターネット`CInternetFile`クラスと連携する方法の詳細については、「 [WinInet を使用したインターネットプログラミング](../../mfc/win32-internet-extensions-wininet.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

[CStdioFile](../../mfc/reference/cstdiofile-class.md)

`CInternetFile`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxinet.h

##  <a name="abort"></a>  CInternetFile::Abort

このオブジェクトに関連付けられているファイルを閉じて、読み取りまたは書き込みのためにファイルを使用できないようにします。

```
virtual void Abort();
```

### <a name="remarks"></a>Remarks

オブジェクトを破棄する前にファイルを閉じていない場合は、デストラクターによってファイルが閉じられます。

例外を処理する`Abort`場合、は、2つの重要な点で[Close](#close)とは異なります。 まず、関数`Abort`はエラーを無視してエラーを無視します。 2つ`Abort`目は、ファイルが開かれていないか、既に閉じられている場合には**アサート**しません。

##  <a name="cinternetfile"></a>CInternetFile:: CInternetFile

このメンバー関数は、 `CInternetFile`オブジェクトが作成されるときに呼び出されます。

```
CInternetFile(
    HINTERNET hFile,
    LPCTSTR pstrFileName,
    CInternetConnection* pConnection,
    BOOL bReadMode);

CInternetFile(
    HINTERNET hFile,
    HINTERNET hSession,
    LPCTSTR pstrFileName,
    LPCTSTR pstrServer,
    DWORD_PTR dwContext,
    BOOL bReadMode);
```

### <a name="parameters"></a>パラメーター

*hFile*<br/>
インターネットファイルへのハンドル。

*pstrFileName*<br/>
ファイル名を格納している文字列へのポインター。

*pConnection*<br/>
[CInternetConnection](../../mfc/reference/cinternetconnection-class.md)オブジェクトへのポインター。

*bReadMode*<br/>
ファイルが読み取り専用かどうかを示します。

*hSession*<br/>
インターネットセッションを処理するハンドル。

*pstrServer*<br/>
サーバーの名前を格納している文字列へのポインター。

*dwContext*<br/>
`CInternetFile`オブジェクトのコンテキスト識別子。 コンテキスト識別子の詳細については、「 [WinInet の基本](../../mfc/wininet-basics.md)」を参照してください。

### <a name="remarks"></a>Remarks

オブジェクトを`CInternetFile`直接作成することはありません。 代わりに、 [CGopherConnection:: OpenFile](../../mfc/reference/cgopherconnection-class.md#openfile)または[CHttpConnection:: openrequest](../../mfc/reference/chttpconnection-class.md#openrequest)を呼び出して、派生クラスのいずれかのオブジェクトを作成します。 [CFtpConnection:: OpenFile](../../mfc/reference/cftpconnection-class.md#openfile)を`CInternetFile`呼び出すことによって、オブジェクトを作成することもできます。

##  <a name="close"></a>  CInternetFile::Close

を`CInternetFile`閉じ、そのリソースを解放します。

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

ファイルが書き込み用に開かれている場合は、バッファー内のすべてのデータがホストに書き込まれるように、[フラッシュ](#flush)への暗黙的な呼び出しが行われます。 ファイルの使用`Close`が完了したら、を呼び出す必要があります。

##  <a name="flush"></a>CInternetFile:: Flush

このメンバー関数を呼び出して、書き込みバッファーの内容をフラッシュします。

```
virtual void Flush();
```

### <a name="remarks"></a>Remarks

を`Flush`使用して、メモリ内のすべてのデータが実際にターゲットコンピューターに書き込まれたことを確認し、ホストコンピューターとのトランザクションが完了したことを保証します。 `Flush`は、書き込み用`CInternetFile`に開かれたオブジェクトに対してのみ有効です。

##  <a name="getlength"></a>  CInternetFile::GetLength

ファイルのサイズを返します。

```
virtual ULONGLONG GetLength() const;
```

##  <a name="m_hfile"></a>  CInternetFile::m_hFile

このオブジェクトに関連付けられているファイルへのハンドル。

```
HINTERNET m_hFile;
```

##  <a name="operator_hinternet"></a>CInternetFile:: operator HINTERNET

現在のインターネットセッションの Windows ハンドルを取得するには、この演算子を使用します。

```
operator HINTERNET() const;
```

##  <a name="read"></a>  CInternetFile::Read

このメンバー関数を呼び出して、 *lpvBuf*から、指定したバイト数 ( *nCount*) を開始位置として、指定されたメモリに読み込みます。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>パラメーター

*lpBuf*<br/>
ファイル データを読み込むメモリ アドレスへのポインター。

*nCount*<br/>
書き込むバイト数。

### <a name="return-value"></a>戻り値

バッファーに転送するバイト数。 ファイルの末尾に到達した場合、戻り値は*nCount*より小さくなることがあります。

### <a name="remarks"></a>Remarks

関数は、実際に読み取られたバイト数を返します。ファイルが終了した場合、数値は*nCount*より小さくなる可能性があります。 ファイルの読み取り中にエラーが発生した場合、関数は、エラーを説明する[CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクトをスローします。 ファイルの末尾を越える読み取りはエラーとは見なされず、例外がスローされないことに注意してください。

すべてのデータが取得されるようにするには、メソッド`CInternetFile::Read`が0を返すまで、アプリケーションはメソッドを呼び出す必要があります。

##  <a name="readstring"></a>  CInternetFile::ReadString

改行文字が見つかるまで文字のストリームを読み取るには、このメンバー関数を呼び出します。

```
virtual BOOL ReadString(CString& rString);

virtual LPTSTR ReadString(
    LPTSTR pstr,
    UINT nMax);
```

### <a name="parameters"></a>パラメーター

*pstr*<br/>
読み取られる行を受け取る文字列へのポインター。

*N1 日*<br/>
読み取る最大文字数。

*rString*<br/>
読み取り行を受け取る[CString](../../atl-mfc-shared/reference/cstringt-class.md)オブジェクトへの参照。

### <a name="return-value"></a>戻り値

[CInternetFile](../../mfc/reference/cinternetfile-class.md)オブジェクトから取得されたプレーンデータを格納しているバッファーへのポインター。 このメソッドに渡されたバッファーのデータ型に関係なく、データに対する操作 (Unicode への変換など) は実行されません。そのため、 **void** <strong>\*</strong>型がの場合と同様に、返されたデータを想定した構造にマップする必要があります。結果.

データを読み取らずにファイルの終わりに到達した場合は NULL です。または、ブール値の場合は、データを読み取らずにファイルの終わりに到達した場合は FALSE になります。

### <a name="remarks"></a>Remarks

関数は、結果として得られる行を*pstr*パラメーターによって参照されるメモリに配置します。 *N1 日*で指定された最大文字数に達すると、文字の読み取りを停止します。 バッファーは、常に終端の null 文字を受け取ります。

最初に`ReadString` [setreadbuffersize](#setreadbuffersize)を呼び出さずにを呼び出すと、4096バイトのバッファーが取得されます。

##  <a name="seek"></a>CInternetFile:: Seek

このメンバー関数を呼び出して、以前に開いたファイル内のポインターの位置を変更します。

```
virtual ULONGLONG Seek(
    LONGLONG lOffset,
    UINT nFrom);
```

### <a name="parameters"></a>パラメーター

*lOffset*<br/>
ファイル内の読み取り/書き込みポインターを移動するバイト単位のオフセット。

*n*<br/>
オフセットの相対参照。 次のいずれかの値を指定する必要があります。

- `CFile::begin`ファイルポインターをファイルの先頭から*lOff*バイト前に移動します。

- `CFile::current`ファイルポインターをファイルの現在位置から*lOff*バイトに移動します。

- `CFile::end`ファイルポインターをファイルの末尾から*lOff*バイトに移動します。 既存のファイルを検索するには、 *lOff*に負の値を指定する必要があります。正の値は、ファイルの末尾を越えてシークします。

### <a name="return-value"></a>戻り値

要求された位置が有効な場合は、ファイルの先頭からの新しいバイトオフセット。それ以外の場合、値は未定義で、 [CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクトがスローされます。

### <a name="remarks"></a>Remarks

関数`Seek`は、ポインターを指定された量 (完全または相対的) に移動することによって、ファイルの内容にランダムにアクセスできるようにします。 シーク中にデータが実際に読み取られることはありません。

現時点では、このメンバー関数の呼び出しは、オブジェクトに`CHttpFile`関連付けられたデータに対してのみサポートされています。 FTP または gopher 要求ではサポートされていません。 これらのサポート`Seek`されていないサービスのいずれかに対してを呼び出すと、Win32 エラーコード ERROR_INTERNET_INVALID_OPERATION に戻されます。

ファイルが開かれると、ファイルポインターはオフセット0のファイルの先頭にあります。

> [!NOTE]
>  を`Seek`使用すると、暗黙的な呼び出しが[フラッシュ](#flush)される可能性があります。

### <a name="example"></a>例

  基本クラスの実装 ( [CFile:: Seek](../../mfc/reference/cfile-class.md#seek)) の例を参照してください。

##  <a name="setreadbuffersize"></a>CInternetFile:: SetReadBufferSize

このメンバー関数を呼び出して、 `CInternetFile`から派生したオブジェクトによって使用される一時読み取りバッファーのサイズを設定します。

```
BOOL SetReadBufferSize(UINT nReadSize);
```

### <a name="parameters"></a>パラメーター

*nReadSize*<br/>
バイト単位のバッファー サイズ。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

基になる WinInet Api はバッファー処理を実行しないため、読み取るデータ量に関係なく、アプリケーションがデータを効率的に読み取ることができるバッファーサイズを選択します。 [読み取り](#read)を呼び出すたびに、大規模な aount データ (4 kb など) が含まれている場合は、バッファーは必要ありません。 ただし、を呼び出し`Read`て少量のデータチャンクを取得した場合、または、1回に1行を読み取るために[ReadString](#readstring)を使用した場合、アプリケーションのパフォーマンスが向上します。

既定では、 `CInternetFile`オブジェクトは読み取り用のバッファリングを提供しません。 このメンバー関数を呼び出す場合は、ファイルが読み取りアクセス用に開かれていることを確認する必要があります。

バッファーサイズはいつでも増やすことができますが、バッファーの圧縮による影響はありません。 最初にを呼び`SetReadBufferSize`出さずに [ReadString](#readstring) を呼び出すと、4096バイトのバッファーが取得されます。

##  <a name="setwritebuffersize"></a>CInternetFile:: SetWriteBufferSize

このメンバー関数を呼び出して、 `CInternetFile`から派生したオブジェクトによって使用される一時的な書き込みバッファーのサイズを設定します。

```
BOOL SetWriteBufferSize(UINT nWriteSize);
```

### <a name="parameters"></a>パラメーター

*nWriteSize*<br/>
バッファーのサイズ (バイト単位)。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。 呼び出しが失敗した場合は、Win32 関数[GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を呼び出してエラーの原因を特定することができます。

### <a name="remarks"></a>Remarks

基になる WinInet Api はバッファー処理を実行しないため、書き込まれるデータの量に関係なく、アプリケーションがデータを効率的に書き込むことができるようにバッファーサイズを選択します。 通常、[書き込み](#write)の各呼び出しに大量のデータが含まれている場合 (たとえば、4 kb 以上の kb)、バッファーは必要ありません。 ただし、 [write](#write)を呼び出して少量のデータを書き込むと、書き込みバッファーによってアプリケーションのパフォーマンスが向上します。

既定では、 `CInternetFile`オブジェクトは書き込み用のバッファーを提供しません。 このメンバー関数を呼び出す場合は、ファイルが書き込みアクセス用に開かれていることを確認する必要があります。 書き込みバッファーのサイズはいつでも変更できますが、これを行うと、暗黙的な呼び出しが[フラッシュ](#flush)されます。

##  <a name="write"></a>  CInternetFile::Write

このメンバー関数を呼び出して、指定されたメモリ、 *lpvBuf*、指定されたバイト数、 *nCount*に書き込みます。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>パラメーター

*lpBuf*<br/>
書き込む最初のバイトへのポインター。

*nCount*<br/>
書き込むバイト数を指定します。

### <a name="remarks"></a>Remarks

データの書き込み中にエラーが発生した場合、関数はエラーを説明する[CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクトをスローします。

##  <a name="writestring"></a>  CInternetFile::WriteString

この関数は、null で終わる文字列を、関連付けられているファイルに書き込みます。

```
virtual void WriteString(LPCTSTR pstr);
```

### <a name="parameters"></a>パラメーター

*pstr*<br/>
書き込むコンテンツを格納している文字列へのポインター。

### <a name="remarks"></a>Remarks

データの書き込み中にエラーが発生した場合、関数はエラーを説明する[CInternetException](../../mfc/reference/cinternetexception-class.md)オブジェクトをスローします。

## <a name="see-also"></a>関連項目

[CStdioFile クラス](../../mfc/reference/cstdiofile-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CInternetConnection クラス](../../mfc/reference/cinternetconnection-class.md)
