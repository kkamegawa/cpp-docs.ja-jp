---
title: CException クラス
ms.date: 11/04/2016
f1_keywords:
- CException
- AFX/CException
- AFX/CException::CException
- AFX/CException::Delete
- AFX/CException::ReportError
helpviewer_keywords:
- CException [MFC], CException
- CException [MFC], Delete
- CException [MFC], ReportError
ms.assetid: cfacf14d-bfe4-4666-a5c7-38b800512920
ms.openlocfilehash: 5942e636809e3758f34d209a3da80f0d903ab708
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450367"
---
# <a name="cexception-class"></a>CException クラス

MFC (Microsoft Foundation Class) ライブラリ内のすべての例外に関する基底クラスです。

## <a name="syntax"></a>構文

```
class AFX_NOVTABLE CException : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CException::CException](#cexception)|`CException` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CException::Delete](#delete)|削除、`CException`オブジェクト。|
|[CException::ReportError](#reporterror)|ユーザーにメッセージ ボックスに、エラー メッセージを報告します。|

## <a name="remarks"></a>Remarks

`CException`抽象基本クラスを作成することはできませんが、`CException`オブジェクトは直接の派生クラスのオブジェクトを作成する必要があります。 独自に作成する必要がある場合`CException`-クラスのスタイル設定、モデルとして上記の派生クラスのいずれかを使用します。 派生クラスにも使用`IMPLEMENT_DYNAMIC`します。

派生クラスとその説明を次に示します。

|||
|-|-|
|[CSimpleException](../../mfc/reference/csimpleexception-class.md)|リソース クリティカルな MFC 例外の基本クラス|
|[CInvalidArgException](../../mfc/reference/cinvalidargexception-class.md)|無効な引数の例外条件|
|[CMemoryException](../../mfc/reference/cmemoryexception-class.md)|メモリ不足の例外|
|[CNotSupportedException](../../mfc/reference/cnotsupportedexception-class.md)|サポートされていない操作の要求|
|[CArchiveException](../../mfc/reference/carchiveexception-class.md)|アーカイブ固有の例外|
|[CFileException](../../mfc/reference/cfileexception-class.md)|特定のファイルの例外|
|[CResourceException](../../mfc/reference/cresourceexception-class.md)|見つからないか、またはできない Windows リソース|
|[COleException](../../mfc/reference/coleexception-class.md)|OLE 例外|
|[CDBException](../../mfc/reference/cdbexception-class.md)|データベースの例外 (つまり、Open Database Connectivity に基づいて MFC データベース クラスの例外条件)|
|[COleDispatchException](../../mfc/reference/coledispatchexception-class.md)|OLE ディスパッチ (オートメーション) 例外|
|[CUserException](../../mfc/reference/cuserexception-class.md)|リソースが検出できなかったことを示す例外|
|[CDaoException](../../mfc/reference/cdaoexception-class.md)|データ アクセス オブジェクトの例外 (つまり、DAO クラスの例外条件)|
|[CInternetException](../../mfc/reference/cinternetexception-class.md)|インターネットの例外 (つまり、インターネット クラスの発生した例外条件)。|

これらの例外を使用するものでは、[THROW](exception-processing.md#throw)、 [THROW_LAST](exception-processing.md#throw_last)、[try](exception-processing.md#try)、[catch](exception-processing.md#catch)、 [and_catch](exception-processing.md#and_catch)、および[end_catch](exception-processing.md#end_catch)マクロ。 例外の詳細については、[例外の処理](exception-processing.md)」または「[例外処理 (MFC)](../exception-handling-in-mfc.md)を参照してください。

特定の例外をキャッチするには、適切な派生クラスを使用します。 すべての種類の例外を使用して`CException`、しを使用して[使うため](cobject-class.md#iskindof)を区別する`CException`-クラスを派生します。 なお`CObject::IsKindOf`で宣言されたクラスに対してのみ機能、 [IMPLEMENT_DYNAMIC](run-time-object-model-services.md#implement_dynamic)マクロは、動的な型チェックを活用するためにします。 すべて`CException`-作成する派生クラスを使用する必要があります、`IMPLEMENT_DYNAMIC`マクロ、すぎます。

呼び出すことによって、ユーザーに例外に関する詳細をレポートできます[GetErrorMessage](cfileexception-class.md#geterrormessage)または[ReportError](#reporterror)、2 つのメンバー関数のいずれかで使用できる`CException`のクラスを派生します。

マクロのいずれかで例外がキャッチされた場合、`CException`オブジェクトが自動的に削除されます。 削除しないでください、自分でします。 使用して、例外がキャッチされた場合、**catch**キーワードは自動的に削除されません。 記事をご覧ください[例外処理 (MFC)](../exception-handling-in-mfc.md)例外オブジェクトを削除するタイミングの詳細についてはします。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](cobject-class.md)

`CException`

## <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="cexception"></a>  CException::CException

このメンバー関数を作成、`CException`オブジェクト。

```
explicit CException(BOOL bAutoDelete);
```

### <a name="parameters"></a>パラメーター

*b_AutoDelete*<br/>
場合は TRUE を指定のメモリ、`CException`オブジェクトがヒープに割り当てられています。 これにより、`CException`ときに削除するオブジェクト、`Delete`例外を削除するメンバー関数が呼び出されます。 場合は FALSE を指定、`CException`オブジェクトがスタック上にまたはグローバル オブジェクトです。 ここで、`CException`オブジェクトができない場合に削除されます、`Delete`メンバー関数が呼び出されます。

### <a name="remarks"></a>Remarks

このコンス トラクターを直接呼び出す必要は通常ありません。 例外をスローする関数のインスタンスを作成する必要があります、 `CException`-クラスを派生し、コンス トラクターまたはそれを呼び出す必要があります、MFC のいずれかを使用してスロー関数など[AfxThrowFileException](exception-processing.md#afxthrowfileexception)、定義済みの型をスローします。 このドキュメントは、完全を期すためにのみ提供されます。

##  <a name="delete"></a>  CException::Delete

この関数をかどうかを確認します、 `CException` 、ヒープのオブジェクトが作成され、呼び出す場合は、**delete**演算子をオブジェクトにします。

```
void Delete();
```

### <a name="remarks"></a>Remarks

削除するときに、`CException`オブジェクトを使用して、`Delete`例外を削除するメンバー関数。 使用しないでください、**delete**演算子を直接ため、`CException`オブジェクトのグローバル オブジェクトがありますまたはスタック上に作成されています。

オブジェクトが作成されるときに、オブジェクトを削除するかどうかを指定することができます。 詳細については、次を参照してください。 [CException::CException](#cexception)します。

のみを呼び出す必要があります`Delete`、C++ を使用している場合**try**- **catch**メカニズム。 MFC マクロを使用している場合**TRY**と**CATCH**、これらのマクロはこの関数を自動的に呼び出します。

### <a name="example"></a>例

```cpp
CFile* pFile = NULL;
// Constructing a CFile object with this override may throw
// a CFile exception, and won't throw any other exceptions.
// Calling CString::Format() may throw a CMemoryException,
// so we have a catch block for such exceptions, too. Any
// other exception types this function throws will be
// routed to the calling function.
// Note that this example performs the same actions as the
// example for CATCH, but uses C++ try/catch syntax instead
// of using the MFC TRY/CATCH macros. This sample must use
// CException::Delete() to delete the exception objects
// before closing the catch block, while the CATCH example
// implicitly performs the deletion via the macros.
try
{
   pFile = new CFile(_T("C:\\WINDOWS\\SYSTEM.INI"),
      CFile::modeRead | CFile::shareDenyNone);
   ULONGLONG ullLength = pFile->GetLength();
   CString str;
   str.Format(_T("Your SYSTEM.INI file is %u bytes long."), ullLength);
   AfxMessageBox(str);
}
catch(CFileException* pEx)
{
   // Simply show an error message to the user.
   pEx->ReportError();
   pEx->Delete();
}
catch(CMemoryException* pEx)
{
   // We can't recover from this memory exception, so we'll
   // just terminate the app without any cleanup. Normally, an
   // an application should do everything it possibly can to
   // clean up properly and _not_ call AfxAbort().
   pEx->Delete();
   AfxAbort();
}
// If an exception occurrs in the CFile constructor,
// the language will free the memory allocated by new
// and will not complete the assignment to pFile.
// Thus, our clean-up code needs to test for NULL.
if (pFile != NULL)
{
   pFile->Close();
   delete pFile;
}
```

##  <a name="reporterror"></a>  CException::ReportError

ユーザーにメッセージ ボックスに、レポートのエラー テキストには、このメンバー関数を呼び出します。

```
virtual int ReportError(
    UINT nType = MB_OK,
    UINT nMessageID = 0);
```

### <a name="parameters"></a>パラメーター

*nType*<br/>
メッセージ ボックスのスタイルを指定します。 任意の組み合わせを適用、[メッセージ ボックス スタイル](styles-used-by-mfc.md#message-box-styles)します。 このパラメーターを指定しない場合、既定値は MB_OK は。

*nMessageID*<br/>
例外オブジェクトには、エラー メッセージがない場合に表示するメッセージのリソース ID (文字列のテーブルのエントリ) を指定します。 0 の場合、メッセージ「エラー メッセージはありません」が表示されます。

### <a name="return-value"></a>戻り値

`AfxMessageBox`値はメッセージ ボックスを表示するための十分なメモリがない場合は 0。 参照してください[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)の戻り値。

### <a name="example"></a>例

使用例を次に示します`CException::ReportError`します。 別の例の例を参照してください。[キャッチ](exception-processing.md#catch)します。

```cpp
CFile fileInput;
CFileException ex;

// try to open a file for reading.
// The file will certainly not
// exist because there are too many explicit
// directories in the name.

// if the call to Open() fails, ex will be
// initialized with exception
// information.  the call to ex.ReportError() will
// display an appropriate
// error message to the user, such as
// "\Too\Many\Bad\Dirs.DAT contains an
// invalid path."  The error message text will be
// appropriate for the
// file name and error condition.

if (!fileInput.Open(_T("\\Too\\Many\\Bad\\Dirs.DAT"), CFile::modeRead, &ex))
{
  ex.ReportError();
}
else
{
  // the file was opened, so do whatever work
  // with fileInput we were planning...

  fileInput.Close();
}
```

## <a name="see-also"></a>関連項目

[CObject クラス](cobject-class.md)<br/>
[階層図](../hierarchy-chart.md)<br/>
[例外処理](exception-processing.md)<br/>
[How Do i:独自のカスタム例外クラスを作成します。](https://go.microsoft.com/fwlink/p/?linkid=128045)
