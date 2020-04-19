---
title: CStdioFile クラス
ms.date: 08/29/2019
f1_keywords:
- CStdioFile
- AFX/CStdioFile
- AFX/CStdioFile::CStdioFile
- AFX/CStdioFile::Open
- AFX/CStdioFile::ReadString
- AFX/CStdioFile::Seek
- AFX/CStdioFile::WriteString
- AFX/CStdioFile::m_pStream
helpviewer_keywords:
- CStdioFile [MFC], CStdioFile
- CStdioFile [MFC], Open
- CStdioFile [MFC], ReadString
- CStdioFile [MFC], Seek
- CStdioFile [MFC], WriteString
- CStdioFile [MFC], m_pStream
ms.assetid: 88c2274c-4f0e-4327-882a-557ba4b3ae15
ms.openlocfilehash: 4b667f4121d92863335befda3a7beef74f29ad1a
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177483"
---
# <a name="cstdiofile-class"></a>CStdioFile クラス

ランタイム関数[fopen](../../c-runtime-library/reference/fopen-wfopen.md)によって開かれた C ランタイムストリームファイルを表します。

## <a name="syntax"></a>構文

```
class CStdioFile : public CFile
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CStdioFile::CStdioFile](#cstdiofile)|パスまた`CStdioFile`はファイルポインターからオブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CStdioFile::Open](#open)|オーバーロードされます。 Open は、既定`CStdioFile`のコンストラクターで使用するように設計されています ( [CFile:: Open](../../mfc/reference/cfile-class.md#open)をオーバーライドします)。|
|[CStdioFile::ReadString](#readstring)|1行のテキストを読み取ります。|
|[CStdioFile::Seek](#seek)|現在のファイルポインターを配置します。|
|[CStdioFile::WriteString](#writestring)|1行のテキストを書き込みます。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CStdioFile::m_pStream](#m_pstream)|開いているファイルへのポインターを格納します。|

## <a name="remarks"></a>Remarks

ストリームファイルはバッファーされ、テキストモード (既定) またはバイナリモードで開くことができます。

テキストモードでは、復帰とラインフィードのペアに対して特別な処理を行います。 ラインフィード (改行) 文字 (0x0a) をテキストモード`CStdioFile`オブジェクトに書き込むと、バイトペア (0x0D、0x0a) がファイルに送信されます。 を読み取ると、バイトペア (0x0D、0x0A) が1つの0x0A バイトに変換されます。

[CFile](../../mfc/reference/cfile-class.md)関数[Duplicate](../../mfc/reference/cfile-class.md#duplicate)、 [LockRange](../../mfc/reference/cfile-class.md#lockrange)、および[UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)は、で`CStdioFile`はサポートされていません。

でこれらの関数`CStdioFile`を呼び出すと、 [CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)が得られます。

の使用`CStdioFile`方法の詳細については、「 [MFC の記事ファイル](../../mfc/files-in-mfc.md)」と「*ランタイムライブラリリファレンス*」の「[ファイル処理](../../c-runtime-library/file-handling.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CFile](../../mfc/reference/cfile-class.md)

`CStdioFile`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="cstdiofile"></a>CStdioFile::CStdioFile

`CStdioFile` オブジェクトを構築して初期化します。

```
CStdioFile();
CStdioFile(CAtlTransactionManager* pTM);
CStdioFile(FILE* pOpenStream);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags);

CStdioFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CAtlTransactionManager* pTM);
```

### <a name="parameters"></a>パラメーター

*pOpenStream*<br/>
C ランタイム関数[fopen](../../c-runtime-library/reference/fopen-wfopen.md)への呼び出しによって返されるファイルポインターを指定します。

*lpszFileName*<br/>
目的のファイルへのパスを表す文字列を指定します。 相対パスと絶対パスのどちらでも構いません。

*Noペンフラグ*<br/>
ファイルの作成、ファイル共有、およびファイルアクセスモードのオプションを指定します。 複数のオプションを指定するには、ビットごと **|** の or () 演算子を使用します。

1つのファイルアクセスモードオプションが必要です。その他のモードは省略可能です。 モードオプションとその他のフラグの一覧については、「 [cfile:: cfile](../../mfc/reference/cfile-class.md#cfile) 」を参照してください。 MFC バージョン3.0 以降では、共有フラグが許可されています。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

既定のコンストラクターでは、ファイルは`CStdioFile`オブジェクトにアタッチされません。 このコンストラクターを使用する場合は、 `CStdioFile::Open`メソッドを使用してファイルを開き、 `CStdioFile`オブジェクトにアタッチする必要があります。

1つのパラメーターを持つコンストラクターは、開いている`CStdioFile`ファイルストリームをオブジェクトにアタッチします。 使用できるポインター値には、事前定義された入力/出力ファイルポインター *stdin*、 *stdout*、または*stderr*が含まれます。

2つのパラメーターを持つコンストラクター `CStdioFile`は、オブジェクトを作成し、指定されたパスを持つ対応するファイルを開きます。

*Popenstream*または*LPSZFILENAME*に NULL を渡すと、コンストラクターはを`CInvalidArgException*`スローします。

ファイルを開くことも作成することもできない場合、 `CFileException*`コンストラクターはをスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#37](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_1.cpp)]

##  <a name="m_pstream"></a>  CStdioFile::m_pStream

データメンバーは、C ランタイム関数`fopen`によって返される開いているファイルへのポインターです。 `m_pStream`

```
FILE* m_pStream;
```

### <a name="remarks"></a>Remarks

ファイルが開かれたことがない場合、または閉じられた場合は NULL になります。

##  <a name="open"></a>  CStdioFile::Open

オーバーロードされます。 Open は、既定`CStdioFile`のコンストラクターで使用するように設計されています。

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
目的のファイルへのパスを表す文字列。 相対パスと絶対パスのどちらでも構いません。

*Noペンフラグ*<br/>
共有とアクセスモード。 ファイルを開くときに実行するアクションを指定します。 ビットごとの OR (&#124;) 演算子を使用して、オプションを組み合わせることができます。 1つのアクセス許可と1つの共有オプションが必要です。modeCreate モードと modeNoInherit モードは省略可能です。

*pError*<br/>
失敗した操作の状態を受け取る既存のファイル例外オブジェクトへのポインター。

*pTM*<br/>
オブジェクトへの`CAtlTransactionManager`ポインター。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="readstring"></a>  CStdioFile::ReadString

`CStdioFile`オブジェクトに関連付けられているファイルから、 *n1 日*文字の制限まで、テキストデータをバッファーに読み込みます。

```
virtual LPTSTR ReadString(
    LPTSTR lpsz,
    UINT nMax);

virtual BOOL ReadString(CString& rString);
```

### <a name="parameters"></a>パラメーター

*lpsz*<br/>
Null で終わるテキスト文字列を受け取るユーザー指定のバッファーへのポインターを指定します。

*N1 日*<br/>
読み取る文字の最大数を指定します。終端の null 文字は含まれません。

*rString*<br/>
関数が返され`CString`たときに文字列を格納するオブジェクトへの参照。

### <a name="return-value"></a>戻り値

テキストデータを格納しているバッファーへのポインター。 データを読み取らずにファイルの終わりに到達した場合は NULL です。ブール値の場合は、データを読み取らずにファイルの終わりに到達した場合は FALSE になります。

### <a name="remarks"></a>Remarks

読み取りは、最初の改行文字によって停止されます。 この場合、 *n1 日*文字が読み取られていない場合は、改行文字がバッファーに格納されます。 どちらの場合も、null 文字 (' \ 0 ') が追加されます。

[CFile:: Read](../../mfc/reference/cfile-class.md#read)は、テキストモード入力でも使用できますが、復帰とラインフィードのペアで終了しません。

> [!NOTE]
>  この`CString`関数のバージョンでは、 `'\n'`存在する場合、が削除されます。 LPTSTR のバージョンでは削除されません。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#38](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_2.cpp)]

##  <a name="seek"></a>  CStdioFile::Seek

以前に開いたファイル内のポインターを再配置します。

```
virtual ULONGLONG Seek(
    LONGLONG lOff,
    UINT nFrom);
```

### <a name="parameters"></a>パラメーター

*lOff*<br/>
ポインターを移動するバイト数。

*n*<br/>
ポインターの移動モード。 次のいずれかの値を指定する必要があります。

- `CFile::begin`:ファイルポインターをファイルの先頭から*lOff*バイト前に移動します。

- `CFile::current`:ファイルポインターをファイルの現在位置から*lOff*バイトに移動します。

- `CFile::end`:ファイルポインターをファイルの末尾から*lOff*バイトに移動します。 既存のファイルを検索するには、 *lOff*に負の値を指定する必要があることに注意してください。正の値は、ファイルの末尾を越えてシークします。

### <a name="return-value"></a>戻り値

要求された位置が有効`Seek`な場合は、ファイルの先頭からの新しいバイトオフセットを返します。 それ以外の場合、戻り値は未定義`CFileException`となり、オブジェクトがスローされます。

### <a name="remarks"></a>Remarks

関数`Seek`は、ポインターを指定された量 (完全または相対的) に移動することによって、ファイルの内容にランダムにアクセスできるようにします。 シーク中にデータが実際に読み取られることはありません。 要求された位置がファイルのサイズより大きい場合、ファイルの長さはその位置まで拡張され、例外はスローされません。

ファイルが開かれると、ファイルポインターは、ファイルの先頭であるオフセット0に位置します。

の`Seek`この実装は、ランタイムライブラリ (CRT) 関数`fseek`に基づいています。 テキストモードで開かれたストリームで`Seek`のの使用にはいくつかの制限があります。 詳細については、「 [fseek、_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)」を参照してください。

### <a name="example"></a>例

次の例は、を使用`Seek`して、ポインターを`cfile`ファイルの先頭から1000バイト移動する方法を示しています。 はデータ`Seek`を読み取らないことに注意してください。そのため、後で[CStdioFile:: ReadString](#readstring)を呼び出してデータを読み取る必要があります。

[!code-cpp[NVC_MFCFiles#39](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_3.cpp)]

##  <a name="writestring"></a>  CStdioFile::WriteString

バッファーから`CStdioFile`オブジェクトに関連付けられたファイルにデータを書き込みます。

```
virtual void WriteString(LPCTSTR lpsz);
```

### <a name="parameters"></a>パラメーター

*lpsz*<br/>
Null で終わる文字列を含むバッファーへのポインターを指定します。

### <a name="remarks"></a>Remarks

終端の null 文字 ( `\0`) は、ファイルに書き込まれません。 このメソッドは、キャリッジリターンとラインフィードのペアとして、 *lpsz*内の改行文字をファイルに書き込みます。

Null で終了しないデータをファイルに書き込む場合は、または`CStdioFile::Write` [CFile:: write](../../mfc/reference/cfile-class.md#write)を使用します。

Lpsz パラメーターに NULL `CInvalidArgException*`を指定した場合、このメソッドはをスローします。

このメソッドは、 `CFileException*`ファイルシステムエラーに応答してをスローします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#40](../../atl-mfc-shared/reference/codesnippet/cpp/cstdiofile-class_4.cpp)]

## <a name="see-also"></a>関連項目

[CFile クラス](../../mfc/reference/cfile-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CFile クラス](../../mfc/reference/cfile-class.md)<br/>
[CFile::Duplicate](../../mfc/reference/cfile-class.md#duplicate)<br/>
[CFile::LockRange](../../mfc/reference/cfile-class.md#lockrange)<br/>
[CFile::UnlockRange](../../mfc/reference/cfile-class.md#unlockrange)<br/>
[CNotSupportedException クラス](../../mfc/reference/cnotsupportedexception-class.md)
