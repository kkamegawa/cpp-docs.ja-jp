---
title: CFile クラス
ms.date: 06/12/2018
f1_keywords:
- CFile
- AFX/CFile
- AFX/CFile::CFile
- AFX/CFile::Abort
- AFX/CFile::Close
- AFX/CFile::Duplicate
- AFX/CFile::Flush
- AFX/CFile::GetFileName
- AFX/CFile::GetFilePath
- AFX/CFile::GetFileTitle
- AFX/CFile::GetLength
- AFX/CFile::GetPosition
- AFX/CFile::GetStatus
- AFX/CFile::LockRange
- AFX/CFile::Open
- AFX/CFile::Read
- AFX/CFile::Remove
- AFX/CFile::Rename
- AFX/CFile::Seek
- AFX/CFile::SeekToBegin
- AFX/CFile::SeekToEnd
- AFX/CFile::SetFilePath
- AFX/CFile::SetLength
- AFX/CFile::SetStatus
- AFX/CFile::UnlockRange
- AFX/CFile::Write
- AFX/CFile::hFileNull
- AFX/CFile::m_hFile
- AFX/CFile::m_pTM
helpviewer_keywords:
- CFile [MFC], CFile
- CFile [MFC], Abort
- CFile [MFC], Close
- CFile [MFC], Duplicate
- CFile [MFC], Flush
- CFile [MFC], GetFileName
- CFile [MFC], GetFilePath
- CFile [MFC], GetFileTitle
- CFile [MFC], GetLength
- CFile [MFC], GetPosition
- CFile [MFC], GetStatus
- CFile [MFC], LockRange
- CFile [MFC], Open
- CFile [MFC], Read
- CFile [MFC], Remove
- CFile [MFC], Rename
- CFile [MFC], Seek
- CFile [MFC], SeekToBegin
- CFile [MFC], SeekToEnd
- CFile [MFC], SetFilePath
- CFile [MFC], SetLength
- CFile [MFC], SetStatus
- CFile [MFC], UnlockRange
- CFile [MFC], Write
- CFile [MFC], hFileNull
- CFile [MFC], m_hFile
- CFile [MFC], m_pTM
ms.assetid: b2eb5757-d499-4e67-b044-dd7d1abaa0f8
ms.openlocfilehash: a9161764f6c8646766a73add01c25cce5619ad19
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506579"
---
# <a name="cfile-class"></a>CFile クラス

ファイルに関する MFC の基底クラスです。

## <a name="syntax"></a>構文

```
class CFile : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFile::CFile](#cfile)|パスまた`CFile`はファイルハンドルからオブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFile::Abort](#abort)|すべての警告とエラーを無視してファイルを閉じます。|
|[CFile::Close](#close)|ファイルを閉じて、オブジェクトを削除します。|
|[CFile::Duplicate](#duplicate)|このファイルに基づいて、重複するオブジェクトを構築します。|
|[CFile::Flush](#flush)|書き込まれていないデータをフラッシュします。|
|[CFile::GetFileName](#getfilename)|選択されたファイルのファイル名を取得します。|
|[CFile::GetFilePath](#getfilepath)|選択したファイルの完全なファイルパスを取得します。|
|[CFile::GetFileTitle](#getfiletitle)|選択したファイルのタイトルを取得します。|
|[CFile::GetLength](#getlength)|ファイルの長さを取得します。|
|[CFile::GetPosition](#getposition)|現在のファイルポインターを取得します。|
|[CFile::GetStatus](#getstatus)|開いているファイルの状態を取得します。または、静的なバージョンの場合は、指定されたファイル (静的、仮想関数) の状態を取得します。|
|[CFile::LockRange](#lockrange)|ファイル内のバイトの範囲をロックします。|
|[CFile::Open](#open)|エラーテストオプションを使用してファイルを安全に開きます。|
|[CFile::Read](#read)|現在のファイル位置にあるファイルからデータを読み取り (バッファリングされない)。|
|[CFile::Remove](#remove)|指定されたファイル (静的関数) を削除します。|
|[CFile::Rename](#rename)|指定されたファイルの名前を変更します (静的関数)。|
|[CFile::Seek](#seek)|現在のファイルポインターを配置します。|
|[CFile::SeekToBegin](#seektobegin)|ファイルの先頭に現在のファイルポインターを移動します。|
|[CFile::SeekToEnd](#seektoend)|ファイルの末尾に現在のファイルポインターを移動します。|
|[CFile::SetFilePath](#setfilepath)|選択したファイルの完全なファイルパスを設定します。|
|[CFile::SetLength](#setlength)|ファイルの長さを変更します。|
|[CFile::SetStatus](#setstatus)|指定されたファイルの状態 (静的、仮想関数) を設定します。|
|[CFile::UnlockRange](#unlockrange)|ファイル内のバイトの範囲をロック解除します。|
|[CFile::Write](#write)|ファイル内のデータを現在のファイル位置に書き込みます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CFile::operator HANDLE](#operator_handle)|`CFile`オブジェクトへのハンドル。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CFile::hFileNull](#hfilenull)|オブジェクトが有効`CFile`なハンドルを持っているかどうかを判断します。|
|[CFile::m_hFile](#m_hfile)|通常、にはオペレーティングシステムのファイルハンドルが含まれます。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CFile::m_pTM](#m_ptm)|オブジェクトへ`CAtlTransactionManager`のポインター。|

## <a name="remarks"></a>Remarks

このクラスは、バッファリングされていないバイナリディスク入出力サービスを直接提供し、派生クラスを通じてテキストファイルとメモリファイルを間接的にサポートします。 `CFile`は、クラスと連携`CArchive`して、Microsoft Foundation class オブジェクトのシリアル化をサポートします。

このクラスとその派生クラスの間の階層リレーションシップにより、プログラムはポリモーフィック`CFile`インターフェイスを介してすべてのファイルオブジェクトを操作できます。 たとえば、メモリファイルはディスクファイルのように動作します。

汎用`CFile`ディスク i/o には、とその派生クラスを使用します。 また`ofstream`はその他`iostream`の Microsoft クラスを使用して、フォーマットされたテキストをディスクファイルに送信します。

通常、ディスクファイルは構築時`CFile`に自動的に開かれ、破棄時に閉じられます。 静的メンバー関数を使用すると、ファイルを開かずにファイルの状態を問い合わせることができます。

の使用`CFile`方法の詳細については、「 [MFC の記事ファイル](../../mfc/files-in-mfc.md)」と「*ランタイムライブラリリファレンス*」の「[ファイル処理](../../c-runtime-library/file-handling.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CFile`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="abort"></a>  CFile::Abort

このオブジェクトに関連付けられているファイルを閉じて、読み取りまたは書き込みのためにファイルを使用できないようにします。

```
virtual void Abort();
```

### <a name="remarks"></a>Remarks

オブジェクトを破棄する前にファイルを閉じていない場合は、デストラクターによってファイルが閉じられます。

例外を処理する`CFile::Abort`場合、 `CFile::Close`は、2つの重要な点でとは異なります。 まず、で`Abort` `Abort`はエラーが無視されるため、関数はエラー発生時に例外をスローしません。 2番`Abort`目は、ファイルが開かれていない場合、または以前に閉じられた場合には**アサート**しません。

**New**を使用してヒープに`CFile`オブジェクトを割り当てる場合は、ファイルを閉じた後でそのオブジェクトを削除する必要があります。 `Abort`を`m_hFile` に`CFile::hFileNull`設定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#5](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_1.cpp)]

##  <a name="cfile"></a>CFile::CFile

`CFile` オブジェクトを構築して初期化します。

```
CFile();
CFile(CAtlTransactionManager* pTM);
CFile(HANDLE hFile);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags);

CFile(
LPCTSTR lpszFileName,
UINT nOpenFlags,
CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>パラメーター

*hFile*<br/>
`CFile` オブジェクトにアタッチするためのファイル ハンドル。

*lpszFileName*<br/>
`CFile` オブジェクトにアタッチするための相対パスまたは完全パス。

*Noペンフラグ*<br/>
指定されたファイルのファイル アクセス オプションのビットごとの組み合わせ (OR)。 使用できるオプションについては、「解説」を参照してください。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

次の5つの表は、Noの*flags*パラメーターで使用可能なオプションを示しています。

次のファイル アクセス モード オプションから 1 つのみ選択します。 既定のファイル アクセス モードは `CFile::modeRead` であり、これは読み取り専用です。

|[値]|説明|
|-----------|-----------------|
|`CFile::modeRead`|読み取りアクセスのみを要求します。|
|`CFile::modeWrite`|書き込みアクセスのみを要求します。|
|`CFile::modeReadWrite`|読み取りおよび書き込みアクセスを要求します。|

次の文字モード オプションのいずれかを選択します。

|[値]|説明|
|-----------|-----------------|
|`CFile::typeBinary`|バイナリ モードを設定します (派生クラスのみで使用されます)。|
|`CFile::typeText`|復帰とラインフィードのペアに対して特別な処理を行うテキストモードを設定します (派生クラスでのみ使用されます)。|
|`CFile::typeUnicode`|Unicode モードを設定します (派生クラスのみで使用されます)。 アプリケーションが Unicode 構成でビルドされた場合、テキストは Unicode 形式でファイルに書き込まれます。 BOM はファイルに書き込まれません。|

次のファイル共有モード オプションから 1 つのみ選択します。 既定のファイル共有モードは `CFile::shareExclusive` であり、これは排他的です。

|[値]|説明|
|-----------|-----------------|
|`CFile::shareDenyNone`|共有の制限はありません。|
|`CFile::shareDenyRead`|他のすべての読み取りアクセスを拒否します。|
|`CFile::shareDenyWrite`|他のすべての書き込みアクセスを拒否します。|
|`CFile::shareExclusive`|他のすべての読み取りおよび書き込みアクセスを拒否します。|

次のファイル作成モード オプションから最初のオプションまたは両方を選択します。 既定の作成モードは `CFile::modeNoTruncate` であり、これは既存を開くです。

|[値]|説明|
|-----------|-----------------|
|`CFile::modeCreate`|ファイルが存在しない場合は、新しいファイルを作成します。 ファイルが既に存在する場合は、上書きされ、最初は長さが0に設定されます。|
|`CFile::modeNoTruncate`|ファイルが存在しない場合は、新しいファイルを作成します。それ以外の場合、ファイルが既に存在する場合は`CFile` 、オブジェクトにアタッチされます。|

説明に従って次のファイル キャッシュ オプションを選択します。 既定では、オプションとして使用できない汎用のキャッシュスキームがシステムによって使用されます。

|値|説明|
|-----------|-----------------|
|`CFile::osNoBuffer`|システムは、ファイルの中間キャッシュを使用しません。 このオプションを選択すると、次の 2 つのオプションは取り消されます。|
|`CFile::osRandomAccess`|ファイル キャッシュはランダム アクセスに対して最適化されます。 このオプションと順次スキャンオプションの両方を使用しないでください。|
|`CFile::osSequentialScan`|ファイル キャッシュは順次アクセスに対して最適化されます。 このオプションとランダムアクセスオプションの両方を使用しないでください。|
|`CFile::osWriteThrough`|書き込み操作は遅延なしで実行されます。|

ファイル ハンドルが継承されないようにするために、次のセキュリティ オプションを選択します。 既定では、新しい子プロセスはファイル ハンドルを使用できます。

|[値]|説明|
|-----------|-----------------|
|`CFile::modeNoInherit`|子プロセスがファイル ハンドルを使用できないようにします。|

既定のコンストラクターはメンバーを初期化しますが、 `CFile`オブジェクトにはファイルをアタッチしません。 このコンストラクターを使用した後、 [CFile::open](#open)メソッドを使用してファイルを開き、 `CFile`オブジェクトにアタッチします。

1 つのパラメーターを持つコンストラクターでは、メンバーは初期化され、既存のファイルが `CFile` オブジェクトにアタッチされます。

2 つのパラメーターを持つコンストラクターでは、メンバーは初期化され、指定されたファイルを開くことが試行されます。 このコンストラクターによって、指定されたファイルが正常に開かれると、ファイルは `CFile` オブジェクトにアタッチされます。それ以外の場合は、このコンストラクターによって `CInvalidArgException` オブジェクトへのポインターがスローされます。 例外の処理方法の詳細については、「[例外](../../mfc/exception-handling-in-mfc.md)」を参照してください。

指定されたファイルが正常に開かれた場合、オブジェクトが破棄さ`CFile`れると、このファイルは自動的に閉じられます。それ以外の場合は、 `CFile`オブジェクトにアタッチされなくなった後に、ファイルを明示的に閉じる必要があります。 `CFile`

### <a name="example"></a>例

`CFile` の使用例を次のコードに示します。

[!code-cpp[NVC_MFCFiles#4](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_2.cpp)]

##  <a name="close"></a>CFile::Close

このオブジェクトに関連付けられているファイルを閉じて、読み取りまたは書き込みのためにファイルを使用できないようにします。

```
virtual void Close();
```

### <a name="remarks"></a>Remarks

オブジェクトを破棄する前にファイルを閉じていない場合は、デストラクターによってファイルが閉じられます。

**New**を使用してヒープに`CFile`オブジェクトを割り当てる場合は、ファイルを閉じた後でそのオブジェクトを削除する必要があります。 `Close`を`m_hFile` に`CFile::hFileNull`設定します。

### <a name="example"></a>例

[Cfile::cfile](#cfile)の例を参照してください。

##  <a name="duplicate"></a>CFile::Duplicate

指定され`CFile`たファイルの重複するオブジェクトを構築します。

```
virtual CFile* Duplicate() const;
```

### <a name="return-value"></a>戻り値

重複`CFile`するオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

この関数は、C ランタイム関数`_dup`に相当します。

##  <a name="flush"></a>CFile::Flush

ファイルバッファー内の残りのデータを強制的にファイルに書き込みます。

```
virtual void Flush();
```

### <a name="remarks"></a>Remarks

を使用`Flush`すると、バッファーの`CArchive`フラッシュは保証されません。 アーカイブを使用している場合は、最初に[CArchive::Flush](../../mfc/reference/carchive-class.md#flush)を呼び出します。

### <a name="example"></a>例

[CFile::SetFilePath](#setfilepath)の例を参照してください。

##  <a name="getfilename"></a>  CFile::GetFileName

このメンバー関数を呼び出して、指定したファイルの名前を取得します。

```
virtual CString GetFileName() const;
```

### <a name="return-value"></a>戻り値

ファイルの名前です。

### <a name="remarks"></a>Remarks

たとえば、を呼び出し`GetFileName`てファイルに関するメッセージをユーザーに生成すると、ファイル`c:\windows\write\myfile.wri`名`myfile.wri`が返されます。

名前を含むファイルのパス全体を取得するには、 [Getfilepath](#getfilepath)を呼び出します。 ファイルのタイトル ( `myfile`) を返すには、 [GetFileTitle](#getfiletitle)を呼び出します。

### <a name="example"></a>例

このコード片では、システムが開きます。WINDOWS ディレクトリに INI ファイルを作成します。 見つかった場合、この例では、[出力] に示されているように、名前とパス、およびタイトルが出力されます。

[!code-cpp[NVC_MFCFiles#6](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_3.cpp)]

##  <a name="getfilepath"></a>  CFile::GetFilePath

このメンバー関数を呼び出して、指定したファイルの完全パスを取得します。

```
virtual CString GetFilePath() const;
```

### <a name="return-value"></a>戻り値

指定されたファイルの完全パス。

### <a name="remarks"></a>Remarks

たとえば、を呼び出し`GetFilePath`て、ファイル`c:\windows\write\myfile.wri`に関するメッセージをユーザーに生成すると、ファイルパス`c:\windows\write\myfile.wri`が返されます。

ファイル (`myfile.wri`) の名前だけを取得するには、 [getfilename](#getfilename)を呼び出します。 ファイルのタイトル (`myfile`) を返すには、 [GetFileTitle](#getfiletitle)を呼び出します。

### <a name="example"></a>例

[Getfilename](#getfilename)の例を参照してください。

##  <a name="getfiletitle"></a>  CFile::GetFileTitle

ファイルのファイルタイトル (表示名) を取得するには、このメンバー関数を呼び出します。

```
virtual CString GetFileTitle() const;
```

### <a name="return-value"></a>戻り値

基になるファイルのタイトル。

### <a name="remarks"></a>Remarks

このメソッドは、 [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew)を呼び出して、ファイルのタイトルを取得します。 成功した場合、メソッドは、ユーザーにファイル名を表示するためにシステムが使用する文字列を返します。 それ以外の場合、メソッドは[Pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew)を呼び出して、基になるファイルのファイル名 (ファイル拡張子を含む) を取得します。 つまり、返されたファイルのタイトル文字列にファイル拡張子が必ず含まれているわけではありません。 詳細については、Windows SDK の「 [GetFileTitle](/windows/win32/api/commdlg/nf-commdlg-getfiletitlew)と[pathfindfilename](/windows/win32/api/shlwapi/nf-shlwapi-pathfindfilenamew) 」を参照してください。

名前を含むファイルのパス全体を取得するには、 [Getfilepath](#getfilepath)を呼び出します。 ファイル名のみを返すには、 [Getfilename](#getfilename)を呼び出します。

### <a name="example"></a>例

[Getfilename](#getfilename)の例を参照してください。

##  <a name="getlength"></a>  CFile::GetLength

ファイルの現在の論理長をバイト単位で取得します。

```
virtual ULONGLONG GetLength() const;
```

### <a name="return-value"></a>戻り値

ファイルの長さ。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#7](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_4.cpp)]

##  <a name="getposition"></a>  CFile::GetPosition

ファイルポインターの現在の値を取得します。これは、後でを`Seek`呼び出すときに使用できます。

```
virtual ULONGLONG GetPosition() const;
```

### <a name="return-value"></a>戻り値

ファイルポインター。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#8](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_5.cpp)]

##  <a name="getstatus"></a>CFile::GetStatus

このメソッドは、指定さ`CFile`れたオブジェクトインスタンスまたは指定されたファイルパスに関連するステータス情報を取得します。

```
BOOL GetStatus(CFileStatus& rStatus) const;

static BOOL PASCAL GetStatus(
    LPCTSTR lpszFileName,
    CFileStatus& rStatus,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*rStatus*<br/>
ステータス情報を受け取るユーザー指定`CFileStatus`の構造体への参照。 `CFileStatus`構造体には、次のフィールドがあります。

- `CTime m_ctime`ファイルが作成された日付と時刻。

- `CTime m_mtime`ファイルが最後に変更された日付と時刻。

- `CTime m_atime`ファイルが読み取り用に最後にアクセスされた日付と時刻。

- `ULONGLONG m_size`DIR コマンドによって報告されたファイルの論理サイズ (バイト単位)。

- `BYTE m_attribute`ファイルの属性バイト。

- `char m_szFullName[_MAX_PATH]`Windows 文字セットの絶対ファイル名。

*lpszFileName*<br/>
Windows 文字セット内の、目的のファイルへのパスを表す文字列。 相対パスまたは絶対パスを指定することも、ネットワークパス名を含めることもできます。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

指定したファイルのステータス情報が正常に取得された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

非静的バージョンの`GetStatus`は、指定さ`CFile`れたオブジェクトに関連付けられている開いているファイルのステータス情報を取得します。  の`GetStatus`静的バージョンでは、ファイルを実際に開くことなく、指定されたファイルパスからファイルの状態を取得します。 このバージョンは、ファイルの存在とアクセス権のテストに役立ちます。

構造`CFileStatus`体のメンバーは`m_attribute` 、ファイル属性セットを参照します。 クラス`CFile`は、ファイル属性をシンボルとして指定できるように、**属性**の列挙型を提供します。

```
enum Attribute {
    normal =    0x00,
    readOnly =  0x01,
    hidden =    0x02,
    system =    0x04,
    volume =    0x08,
    directory = 0x10,
    archive =   0x20
    };
```

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#10](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_6.cpp)]

##  <a name="hfilenull"></a>  CFile::hFileNull

`CFile`オブジェクトの有効なファイルハンドルが存在するかどうかを判断します。

```
static AFX_DATA const HANDLE hFileNull;
```

### <a name="remarks"></a>Remarks

この定数は、 `CFile`オブジェクトに有効なファイルハンドルがあるかどうかを判断するために使用されます。

この操作の例を次に示します。

[!code-cpp[NVC_MFCFiles#22](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_7.cpp)]

##  <a name="lockrange"></a>  CFile::LockRange

開いているファイルのバイト範囲をロックし、ファイルが既にロックされている場合は例外をスローします。

```
virtual void LockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>パラメーター

*dwPos*<br/>
ロックするバイト範囲の先頭のバイトオフセット。

*dwCount*<br/>
ロックする範囲内のバイト数。

### <a name="remarks"></a>Remarks

ファイル内のバイトをロックすると、他のプロセスがそれらのバイトにアクセスできなくなります。 ファイルの複数の領域をロックすることはできますが、重複する領域は許可されません。

`UnlockRange`メンバー関数を使用して領域のロックを解除する場合、バイト範囲は、以前にロックされていた領域と正確に対応している必要があります。 関数`LockRange`は隣接する領域を結合しません。 2つのロックされた領域が隣接している場合は、各領域を個別にロック解除する必要があります。

> [!NOTE]
>  この関数は、派生クラス`CMemFile`では使用できません。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="m_hfile"></a>  CFile::m_hFile

開いているファイルのオペレーティングシステムファイルハンドルを格納します。

```
HANDLE m_hFile;
```

### <a name="remarks"></a>Remarks

`m_hFile`UINT 型のパブリック変数です。 これに`CFile::hFileNull`は、ハンドルが割り当てられていない場合に、オペレーティングシステムに依存しない空のファイルインジケーターが含まれます。

メンバーの`m_hFile`意味は派生クラスに依存しているため、の使用は推奨されていません。 `m_hFile`は、クラスの非ポリモーフィックな使用をサポートするために、パブリックメンバーになりました。

##  <a name="m_ptm"></a>  CFile::m_pTM

オブジェクトへの`CAtlTransactionManager`ポインター。

```
CAtlTransactionManager* m_pTM;
```

### <a name="remarks"></a>Remarks

##  <a name="open"></a>  CFile::Open

オーバーロードされます。 `Open`は、既定`CFile`のコンストラクターで使用するように設計されています。

```
virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError = NULL);

virtual BOOL Open(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM,
    CFileException* pError = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszFileName*<br/>
目的のファイルへのパスを含む文字列。 パスには、相対パス、絶対パス、またはネットワーク名 (UNC) を指定できます。

*Noペンフラグ*<br/>
ファイルの共有モードとアクセスモードを定義する UINT。 ファイルを開くときに実行するアクションを指定します。 ビットごとの OR ( **&#124;** ) 演算子を使用して、オプションを組み合わせることができます。 1つのアクセス許可と1つの共有オプションが必要です。モード`modeCreate` と`modeNoInherit`モードは省略可能です。 モードオプションの一覧については、「 [CFile](#cfile)コンストラクター」を参照してください。

*pError*<br/>
失敗した操作の状態を受け取る既存のファイル例外オブジェクトへのポインター。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

開いたが成功した場合は0以外の。それ以外の場合は0です。 このパラメーターは、0が返された場合にのみ意味があります。

### <a name="remarks"></a>Remarks

2つ`Open`の関数は、ファイルを開くための "安全な" メソッドであり、エラーが通常の予期される条件になります。

コンストラクターは`CFile`エラー条件で例外をスローしますが`Open` 、エラー状態の場合は FALSE を返します。 `Open`でも、エラーを説明するために[CFileException](../../mfc/reference/cfileexception-class.md)オブジェクトを初期化することはできます。 パラメーターを指定しない場合、またはの場合に NULL を渡すと`Open` 、は FALSE を返し、 `CFileException`をスローしません。 `CFileException`既存`Open`のにポインターを渡し、エラーが発生した場合、関数はそのエラーを説明する情報を入力します。 `Open`どちらの場合も、例外はスローされません。

次の表では、の`Open`考えられる結果について説明します。

|`pError`|エラーが発生しました|戻り値|CFileException コンテンツ|
|--------------|------------------------|------------------|----------------------------|
|NULL|いいえ|true|N/A|
|ptr`CFileException`|いいえ|true|変更なし|
|NULL|[はい]|false|N/A|
|ptr`CFileException`|[はい]|false|エラーを記述するように初期化されました|

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#13](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_9.cpp)]

[!code-cpp[NVC_MFCFiles#14](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_10.cpp)]

##  <a name="operator_handle"></a>CFile::operator HANDLE

この演算子を使用して、`CFile` オブジェクトへのハンドルを、`HANDLE` を想定する [ReadFileEx](/windows/win32/api/fileapi/nf-fileapi-readfileex) や[getfiletime](/windows/win32/api/fileapi/nf-fileapi-getfiletime)などの関数に渡します。

```
operator HANDLE() const;
```

##  <a name="read"></a>  CFile::Read

`CFile`オブジェクトに関連付けられているファイルからバッファーにデータを読み取ります。

```
virtual UINT Read(
    void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>パラメーター

*lpBuf*<br/>
ファイルから読み取ったデータを受信するための、ユーザーが指定したバッファーへのポインター。

*nCount*<br/>
ファイルから読み取る最大バイト数です。 テキストモードファイルの場合、キャリッジリターンラインフィードのペアは単一の文字としてカウントされます。

### <a name="return-value"></a>戻り値

バッファーに転送するバイト数。 すべて`CFile`のクラスについて、ファイルの末尾に到達した場合、戻り値は*nCount*より小さくなることがあります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#15](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_11.cpp)]

別の例については、「 [CFile::Open](#open)」を参照してください。

##  <a name="remove"></a>  CFile::Remove

この静的関数は、パスで指定されたファイルを削除します。

```
static void PASCAL Remove(
    LPCTSTR lpszFileName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszFileName*<br/>
目的のファイルへのパスを表す文字列。 パスは、相対パスまたは絶対パスにすることができ、ネットワーク名を含めることができます。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

`Remove`ディレクトリは削除されません。

接続`Remove`されたファイルが開いている場合、またはファイルを削除できない場合、メンバー関数は例外をスローします。 この関数は、DEL コマンドに相当します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#17](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_12.cpp)]

##  <a name="rename"></a>  CFile::Rename

この静的関数は、指定されたファイルの名前を変更します。

```
static void PASCAL Rename(
    LPCTSTR lpszOldName,
    LPCTSTR lpszNewName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszOldName*<br/>
古いパス。

*lpszNewName*<br/>
新しいパス。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

ディレクトリの名前を変更することはできません。 この関数は、REN コマンドに相当します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#18](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_13.cpp)]

##  <a name="seek"></a>CFile::Seek

開いているファイル内のファイルポインターを移動します。

```
virtual ULONGLONG Seek(
LONGLONG lOff,
UINT nFrom);
```

### <a name="parameters"></a>パラメーター

*lOff*<br/>
ファイルポインターを移動するバイト数。 正の値は、ファイルポインターをファイルの末尾に移動します。負の値を指定すると、ファイルポインターがファイルの先頭に移動します。

*n*<br/>
シークする位置。 使用可能な値については、「解説」を参照してください。

### <a name="return-value"></a>戻り値

メソッドが正常に実行された場合は、ファイルポインターの位置。それ以外の場合、戻り値は未定義で、 `CFileException`例外へのポインターがスローされます。

### <a name="remarks"></a>Remarks

次の表に、 *Nfrom*パラメーターに使用できる値を示します。

|[値]|説明|
|-----------|-----------------|
|`CFile::begin`|ファイルの先頭からシークします。|
|`CFile::current`|ファイルポインターの現在の場所からシークします。|
|`CFile::end`|ファイルの末尾からシークします。|

ファイルが開かれると、ファイルポインターはファイルの先頭の0に位置します。

ファイルポインターは、ファイルの末尾を越える位置に設定できます。 この場合、ファイルに書き込むまでファイルのサイズは増加しません。

このメソッドの例外ハンドラーは、例外が処理された後に例外オブジェクトを削除する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#9](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_14.cpp)]

##  <a name="seektobegin"></a>CFile::SeekToBegin

ファイルポインターの値をファイルの先頭に設定します。

```
void SeekToBegin();
```

### <a name="remarks"></a>Remarks

`SeekToBegin()` は `Seek( 0L, CFile::begin )` と同じです。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="seektoend"></a>CFile::SeekToEnd

ファイルポインターの値をファイルの論理上の末尾に設定します。

```
ULONGLONG SeekToEnd();
```

### <a name="return-value"></a>戻り値

ファイルの長さをバイト単位で返します。

### <a name="remarks"></a>Remarks

`SeekToEnd()` は `CFile::Seek( 0L, CFile::end )` と同じです。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#19](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_15.cpp)]

##  <a name="setfilepath"></a>  CFile::SetFilePath

ファイルのパスを指定するには、この関数を呼び出します。 たとえば、 [CFile](../../mfc/reference/cfile-class.md)オブジェクトが構築されたときにファイルのパスを使用できない場合`SetFilePath`は、を呼び出して指定します。

```
virtual void SetFilePath(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>パラメーター

*lpszNewName*<br/>
新しいパスを指定する文字列へのポインター。

### <a name="remarks"></a>Remarks

> [!NOTE]
> `SetFilePath`ファイルを開いたり、ファイルを作成したりすることはありません。単にオブジェクトを`CFile`パス名に関連付けることにより、そのオブジェクトを使用できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#20](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_16.cpp)]

##  <a name="setlength"></a>  CFile::SetLength

ファイルの長さを変更するには、この関数を呼び出します。

```
virtual void SetLength(ULONGLONG dwNewLen);
```

### <a name="parameters"></a>パラメーター

*dwNewLen*<br/>
ファイルの必要な長さ (バイト単位)。 この値は、ファイルの現在の長さより大きいか小さくすることができます。 ファイルは、必要に応じて拡張または切り捨てられます。

### <a name="remarks"></a>Remarks

> [!NOTE]
>  で`CMemFile`は、この関数はオブジェクト`CMemoryException`をスローする可能性があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#11](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_17.cpp)]

##  <a name="setstatus"></a>CFile::SetStatus

このファイルの場所に関連付けられているファイルの状態を設定します。

```
static void PASCAL SetStatus(
    LPCTSTR lpszFileName,
    const CFileStatus& status,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszFileName*<br/>
目的のファイルへのパスを表す文字列。 パスは、相対パスまたは絶対パスにすることができ、ネットワーク名を含めることができます。

*status*<br/>
新しいステータス情報を格納しているバッファー。 メンバー関数を呼び出して、現在の`CFileStatus`値で構造体を事前に設定し、必要に応じて変更を行います。 `GetStatus` 値が0の場合、対応するステータス項目は更新されません。 `CFileStatus`構造体の説明については、 [GetStatus](#getstatus)メンバー関数を参照してください。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

時刻を設定するには、 `m_mtime` *状態*のフィールドを変更します。

ファイルの属性のみを変更`SetStatus`しようと`m_mtime`してを呼び出したときに、ファイル状態構造体のメンバーが0以外の場合は、属性も影響を受ける可能性があります (タイムスタンプを変更すると、属性に副作用が生じる可能性があります)。 ファイルの属性のみを変更する場合は、まず、ファイル状態構造`m_mtime`体のメンバーを0に設定してから、を`SetStatus`呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#21](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_18.cpp)]

##  <a name="unlockrange"></a>  CFile::UnlockRange

開いているファイルのバイト範囲をロック解除します。

```
virtual void UnlockRange(
    ULONGLONG dwPos,
    ULONGLONG dwCount);
```

### <a name="parameters"></a>パラメーター

*dwPos*<br/>
ロックを解除するバイト範囲の先頭のバイトオフセット。

*dwCount*<br/>
ロックを解除する範囲内のバイト数。

### <a name="remarks"></a>Remarks

詳細については、 [LockRange](#lockrange)メンバー関数の説明を参照してください。

> [!NOTE]
>  この関数は、 `CMemFile`派生クラスでは使用できません。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#12](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_8.cpp)]

##  <a name="write"></a>CFile::Write

バッファーから`CFile`オブジェクトに関連付けられたファイルにデータを書き込みます。

```
virtual void Write(
    const void* lpBuf,
    UINT nCount);
```

### <a name="parameters"></a>パラメーター

*lpBuf*<br/>
ファイルに書き込まれるデータを格納する、ユーザーが指定したバッファーへのポインター。

*nCount*<br/>
バッファーから転送されるバイト数。 テキストモードファイルの場合、キャリッジリターンラインフィードのペアは単一の文字としてカウントされます。

### <a name="remarks"></a>Remarks

`Write`では、ディスク全体の条件など、いくつかの条件に応じて例外がスローされます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#16](../../atl-mfc-shared/reference/codesnippet/cpp/cfile-class_19.cpp)]

また、 [cfile::cfile](#cfile)と[Cfile::Open](#open)の例も参照してください。

## <a name="see-also"></a>関連項目

[MFC のサンプル DRAWCLI](../../overview/visual-cpp-samples.md)<br/>
[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CStdioFile クラス](../../mfc/reference/cstdiofile-class.md)<br/>
[CMemFile クラス](../../mfc/reference/cmemfile-class.md)
