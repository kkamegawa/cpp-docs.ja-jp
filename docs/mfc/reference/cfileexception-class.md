---
title: CFileException クラス
ms.date: 11/04/2016
f1_keywords:
- CFileException
- AFX/CFileException
- AFX/CFileException::CFileException
- AFX/CFileException::ErrnoToException
- AFX/CFileException::GetErrorMessage
- AFX/CFileException::OsErrorToException
- AFX/CFileException::ThrowErrno
- AFX/CFileException::ThrowOsError
- AFX/CFileException::m_cause
- AFX/CFileException::m_lOsError
- AFX/CFileException::m_strFileName
helpviewer_keywords:
- CFileException [MFC], CFileException
- CFileException [MFC], ErrnoToException
- CFileException [MFC], GetErrorMessage
- CFileException [MFC], OsErrorToException
- CFileException [MFC], ThrowErrno
- CFileException [MFC], ThrowOsError
- CFileException [MFC], m_cause
- CFileException [MFC], m_lOsError
- CFileException [MFC], m_strFileName
ms.assetid: f6491bb9-bfbc-42fd-a952-b33f9b62323f
ms.openlocfilehash: a3514c76d4136fe2bc0b096cc382e6f7f4dd3392
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62205937"
---
# <a name="cfileexception-class"></a>CFileException クラス

ファイルに関連した例外状態を表します。

## <a name="syntax"></a>構文

```
class CFileException : public CException
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CFileException::CFileException](#cfileexception)|`CFileException` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CFileException::ErrnoToException](#errnotoexception)|原因の実行時のエラー番号に対応するコードを返します。|
|[CFileException::GetErrorMessage](#geterrormessage)|例外を説明するメッセージを取得します。|
|[CFileException::OsErrorToException](#oserrortoexception)|オペレーティング システム エラー コードに対応する原因のコードを返します。|
|[CFileException::ThrowErrno](#throwerrno)|ランタイム エラーの数に基づいて、ファイルの例外をスローします。|
|[CFileException::ThrowOsError](#throwoserror)|オペレーティング システム エラー数に基づくファイルの例外をスローします。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CFileException::m_cause](#m_cause)|例外の原因に対応する移植可能なコードが含まれています。|
|[CFileException::m_lOsError](#m_loserror)|関連するオペレーティング システム エラー番号が含まれています。|
|[CFileException::m_strFileName](#m_strfilename)|この例外は、ファイルの名前が含まれています。|

## <a name="remarks"></a>Remarks

`CFileException`クラスには、移植可能な原因のコードとオペレーティング システム固有のエラー番号を保持するパブリック データ メンバーが含まれています。 クラスは、ファイルの例外をスローして、両方のオペレーティング システム エラーおよび C ランタイム エラーの原因のコードを返すためにも静的メンバー関数を提供します。

`CFileException` オブジェクトが構築されでスローされた`CFile`メンバー関数と派生クラスのメンバー関数。 これらのオブジェクトのスコープ内にアクセスすることができます、**キャッチ**式。 移植性の原因コードのみを使用して、例外の理由を取得します。 例外の詳細については、記事を参照してください。[例外処理 (MFC)](../../mfc/exception-handling-in-mfc.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CException](../../mfc/reference/cexception-class.md)

`CFileException`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="cfileexception"></a>  CFileException::CFileException

構築、`CFileException`原因コードとオペレーティング システムのコードをオブジェクトに格納するオブジェクトです。

```
CFileException(
    int cause = CFileException::none,
    LONG lOsError = -1,
    LPCTSTR lpszArchiveName = NULL);
```

### <a name="parameters"></a>パラメーター

*cause*<br/>
例外の理由を示す列挙型の変数。 参照してください[については、「](#m_cause)使用可能な値の一覧についてはします。

*lOsError*<br/>
使用可能な場合は、例外のオペレーティング システム固有理由。 *LOsError*パラメーターより多くの情報を提供します。*原因*は。

*lpszArchiveName*<br/>
名前を含む文字列の指す、`CFile`例外を発生させるオブジェクト。

### <a name="remarks"></a>Remarks

このコンス トラクターを直接使用されませんではなく、グローバル関数を呼び出す[AfxThrowFileException](exception-processing.md#afxthrowfileexception)します。

> [!NOTE]
>  変数*lOsError*にのみ適用されます`CFile`と`CStdioFile`オブジェクト。 `CMemFile`クラスは、このエラー コードを処理しません。

##  <a name="errnotoexception"></a>  CFileException::ErrnoToException

特定のランタイム ライブラリのエラー値に変換を`CFileException`エラー値を列挙します。

```
static int PASCAL ErrnoToException(int nErrno);
```

### <a name="parameters"></a>パラメーター

*nErrno*<br/>
整数エラー コードは実行時のインクルード ファイル ERRNO で定義されています。H.

### <a name="return-value"></a>戻り値

特定のランタイム ライブラリのエラー値に対応する列挙値。

### <a name="remarks"></a>Remarks

参照してください[については、「](#m_cause)に対して一連の可能な列挙値。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#26](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_1.cpp)]

##  <a name="geterrormessage"></a>  CFileException::GetErrorMessage

例外を記述するテキストを取得します。

```
virtual BOOL GetErrorMessage(
    LPTSTR lpszError,
    UINT nMaxError,
    PUINT pnHelpContext = NULL) const;
```

### <a name="parameters"></a>パラメーター

*lpszError*<br/>
[入力、出力]エラー メッセージを受信するバッファーへのポインター。

*nMaxError*<br/>
[in]指定したバッファーが保持できる文字の最大数。 これには、終端の null 文字が含まれます。

*pnHelpContext*<br/>
[入力、出力]ヘルプ コンテキスト ID を受信する符号なし整数へのポインター 場合`NULL`ID は返されません。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

指定したバッファーが小さすぎる場合は、エラー メッセージが切り捨てられます。

### <a name="example"></a>例

次の例では`CFileException::GetErrorMessage`します。

[!code-cpp[NVC_MFCExceptions#22](../../mfc/codesnippet/cpp/cfileexception-class_2.cpp)]

##  <a name="m_cause"></a>  CFileException::m_cause

`CFileException` 列挙型によって定義された値が含まれます。

```
int m_cause;
```

### <a name="remarks"></a>Remarks

このデータ メンバーが型のパブリック変数**int**します。列挙子とその意味は次のとおりです。

- `CFileException::none` 0:エラーはありません。

- `CFileException::genericException` 1:未指定のエラーが発生しました。

- `CFileException::fileNotFound` 2:ファイルが見つかりませんでした。

- `CFileException::badPath` 3:パスのすべてまたは一部が無効です。

- `CFileException::tooManyOpenFiles` 4:開いているファイルの許容数を超えました。

- `CFileException::accessDenied` 5:ファイルにアクセスできませんでした。

- `CFileException::invalidFile` 6:無効なファイル ハンドルを使用しようとしましたがあります。

- `CFileException::removeCurrentDir` 7:現在の作業ディレクトリを削除できません。

- `CFileException::directoryFull` 8:ディレクトリ エントリがあります。

- `CFileException::badSeek` 9:ファイル ポインターを設定しようとしてエラーが発生しました。

- `CFileException::hardIO` 10:ハードウェア エラーが発生しました。

- `CFileException::sharingViolation` 11:共有。EXE が読み込まれていない、または共有の領域がロックされました。

- `CFileException::lockViolation` 12:既にロックされている領域をロックしようとしましたがあります。

- `CFileException::diskFull` 14:ディスクがいっぱいです。

- `CFileException::endOfFile` 15:ファイルの末尾に達しました。

    > [!NOTE]
    >  これらの `CFileException` 原因列挙子は、`CArchiveException` 原因列挙子とは異なります。

    > [!NOTE]
    > `CArchiveException::generic` は使用されなくなりました。 代わりに、`genericException` を使用してください。 場合**ジェネリック**アプリケーションで使用され、結果の構文エラーを簡単に解読は、/clr でビルドしました。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#30](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_3.cpp)]

##  <a name="m_loserror"></a>  CFileException::m_lOsError

この例外は、オペレーティング システム エラー コードが含まれています。

```
LONG m_lOsError;
```

### <a name="remarks"></a>Remarks

エラー コードの一覧については、オペレーティング システム技術マニュアルを参照してください。 このデータ メンバーは、LONG 型のパブリック変数です。

##  <a name="m_strfilename"></a>  CFileException::m_strFileName

この例外の状態のファイルの名前が含まれています。

```
CString m_strFileName;
```

##  <a name="oserrortoexception"></a>  CFileException::OsErrorToException

対応する列挙子を返します、指定された*lOsError*値。 エラー コードは、不明としている場合、関数を返します`CFileException::generic`します。

```
static int PASCAL OsErrorToException(LONG lOsError);
```

### <a name="parameters"></a>パラメーター

*lOsError*<br/>
オペレーティング システム固有のエラー コード。

### <a name="return-value"></a>戻り値

指定したオペレーティング システムのエラー値に対応する列挙値。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#27](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_4.cpp)]

##  <a name="throwerrno"></a>  CFileException::ThrowErrno

構築、`CFileException`に対応するオブジェクトを指定した*nErrno*値、その後、例外をスローします。

```
static void PASCAL ThrowErrno(int nErrno, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>パラメーター

*nErrno*<br/>
整数エラー コードは実行時のインクルード ファイル ERRNO で定義されています。H.

*lpszFileName*<br/>
ファイルの名前を含む文字列へのポインターの原因となった例外、使用可能な場合。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#28](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_5.cpp)]

##  <a name="throwoserror"></a>  CFileException::ThrowOsError

スローされます、`CFileException`に対応する、指定された*lOsError*値。 エラー コードは、不明としている場合、関数としてコード化された例外をスローする`CFileException::generic`します。

```
static void PASCAL ThrowOsError(LONG lOsError, LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>パラメーター

*lOsError*<br/>
オペレーティング システム固有のエラー コード。

*lpszFileName*<br/>
ファイルの名前を含む文字列へのポインターの原因となった例外、使用可能な場合。

### <a name="example"></a>例

[!code-cpp[NVC_MFCFiles#29](../../atl-mfc-shared/reference/codesnippet/cpp/cfileexception-class_6.cpp)]

## <a name="see-also"></a>関連項目

[CException クラス](../../mfc/reference/cexception-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[例外処理](../../mfc/reference/exception-processing.md)
