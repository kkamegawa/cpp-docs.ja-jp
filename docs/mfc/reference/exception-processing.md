---
title: 例外処理
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], exception handling
- DAO (Data Access Objects), exceptions [MFC]
- OLE exceptions [MFC], MFC functions
- exceptions [MFC], processing
- exception macros [MFC]
- termination functions, MFC
- MFC, exceptions
- exceptions [MFC], MFC throwing functions
ms.assetid: 26d4457c-8350-48f5-916e-78f919787c30
ms.openlocfilehash: d33da7a9bc81f9733df840a87fbbbeca1e02cc04
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502553"
---
# <a name="exception-processing"></a>例外処理

プログラムを実行すると、多くの異常な状態と "例外" と呼ばれるエラーが発生する可能性があります。 これには、メモリ不足、リソース割り当てエラー、およびファイルの検索エラーが含まれます。

この Microsoft Foundation Class ライブラリでは、のC++ANSI 標準委員会によって提案されたものの後でモデル化された例外処理スキームを使用します。 異常な状況が発生する可能性のある関数を呼び出す前に、例外ハンドラーを設定する必要があります。 関数で異常な状態が発生した場合、例外がスローされ、制御が例外ハンドラーに渡されます。

Microsoft Foundation Class ライブラリに含まれるいくつかのマクロでは、例外ハンドラーが設定されます。 他の多くのグローバル関数は、必要に応じて、特殊な例外をスローしたり、プログラムを終了したりするのに役立ちます。 これらのマクロとグローバル関数は、次のカテゴリに分類されます。

- 例外ハンドラーを構成する例外マクロ。

- 例外スロー関数)。特定の型の例外を生成します。

- 終了関数。これにより、プログラムが終了します。

例と詳細については、[例外処理](../../mfc/exception-handling-in-mfc.md) を参照してください。

### <a name="exception-macros"></a>例外マクロ

|||
|-|-|
|[TRY](#try)|例外処理のコードブロックを指定します。|
|[CATCH](#catch)|前の **TRY** ブロックから例外をキャッチするためのコードのブロックを指定します。|
|[CATCH_ALL](#catch_all)|上記からのすべての例外をキャッチするためのコードのブロックを指定**TRY**ブロックします。|
|[AND_CATCH](#and_catch)|上記から追加の例外の種類をキャッチするためのコードのブロックを指定**TRY**ブロックします。|
|[AND_CATCH_ALL](#and_catch_all)|他のすべての直前に追加の例外の種類をキャッチするためのコードのブロックを指定**TRY**ブロックします。|
|[END_CATCH](#end_catch)|最後の終了**CATCH**または**AND_CATCH**コード ブロックです。|
|[END_CATCH_ALL](#end_catch_all)|最後の**CATCH_ALL**コードブロックを終了します。|
|[THROW](#throw)|指定された例外をスローします。|
|[THROW_LAST](#throw_last)|現在処理されている例外を次の外部ハンドラーにスローします。|

### <a name="exception-throwing-functions"></a>例外スロー関数

|||
|-|-|
|[AfxThrowArchiveException](#afxthrowarchiveexception)|アーカイブの例外をスローします。|
|[AfxThrowFileException](#afxthrowfileexception)|ファイル例外をスローします。|
|[AfxThrowInvalidArgException](#afxthrowinvalidargexception)|無効な引数の例外をスローします。|
|[AfxThrowMemoryException](#afxthrowmemoryexception)|メモリ例外をスローします。|
|[AfxThrowNotSupportedException](#afxthrownotsupportedexception)|サポートされていない例外をスローします。|
|[AfxThrowResourceException](#afxthrowresourceexception)|Windows リソース-検出されない例外をスローします。|
|[AfxThrowUserException](#afxthrowuserexception)|ユーザーが開始したプログラムアクションで例外をスローします。|

MFC には、OLE 例外専用の次の2つの例外スロー関数が用意されています。

### <a name="ole-exception-functions"></a>OLE 例外関数

|||
|-|-|
|[AfxThrowOleDispatchException](#afxthrowoledispatchexception)|OLE オートメーション関数内で例外をスローします。|
|[AfxThrowOleException](#afxthrowoleexception)|OLE 例外をスローします。|

データベースの例外をサポートするために、データベースクラスには`CDBException` 、 `CDaoException`とという2つの例外クラスと、例外の種類をサポートするためのグローバル関数が用意されています。

### <a name="dao-exception-functions"></a>DAO 例外関数

|||
|-|-|
|[AfxThrowDAOException](#afxthrowdaoexception)|独自のコードから[CDaoException](../../mfc/reference/cdaoexception-class.md)をスローします。|
|[AfxThrowDBException](#afxthrowdbexception)|独自のコードから[CDBException](../../mfc/reference/cdbexception-class.md)をスローします。|

MFC には、次の終了関数が用意されています。

### <a name="termination-functions"></a>終了関数

|||
|-|-|
|[AfxAbort](#afxabort)|致命的なエラーが発生したときにアプリケーションを終了するために呼び出されます。|

##  <a name="try"></a>  TRY

設定、**TRY**ブロックします。

```
TRY
```

### <a name="remarks"></a>Remarks

**TRY**ブロックが例外をスローするコードのブロックを識別します。 これらの例外は、次に**CATCH**と**AND_CATCH**ブロックします。 再帰が許可されている: 例外が外部に渡される**TRY**を無視するか、THROW_LAST マクロを使用して、ブロック。 終了、**TRY**END_CATCH または END_CATCH_ALL マクロを使用してブロックします。

詳細については、[例外処理](../../mfc/exception-handling-in-mfc.md)を参照してください。

### <a name="example"></a>例

[CATCH](#catch)の例を参照してください。

### <a name="requirements"></a>必要条件

ヘッダー: afx.h

##  <a name="catch"></a>CATCH

最初に、上記でスローされた例外の種類をキャッチするコードのブロックを定義します**TRY**ブロックします。

```
CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>パラメーター

*exception_class*<br/>
テストする例外の種類を指定します。 標準の例外クラスの一覧については、「クラス[CException](../../mfc/reference/cexception-class.md)」を参照してください。

*exception_object_pointer_name*<br/>
マクロによって作成される例外オブジェクトポインターの名前を指定します。 内の例外オブジェクトにアクセスするポインターの名前を使用することができます、**CATCH**ブロックします。 この変数は、ユーザーに対して宣言されます。

### <a name="remarks"></a>Remarks

例外処理コードは、必要に応じて例外オブジェクトを問い合わせて、例外の特定の原因に関する詳細情報を取得することができます。 THROW_LAST マクロを呼び出して、処理を次の外側の例外フレームにシフトします。 終了、**TRY**END_CATCH マクロを使用してブロックします。

*Exception_class*がクラス`CException`の場合は、すべての例外の種類がキャッチされます。 使用することができます、[CObject::IsKindOf](../../mfc/reference/cobject-class.md#iskindof)メンバー関数を決定する特定の例外がスローされました。 複数の種類の例外をキャッチするより優れた方法は、それぞれが異なる例外の種類を持つシーケンシャルな**AND_CATCH**ステートメントを使用することです。

例外オブジェクトのポインターはマクロによって作成されます。 自分で宣言する必要はありません。

> [!NOTE]
>  **CATCH**ブロックは、中かっこで囲まれたC++スコープとして定義されます。 このスコープで変数を宣言すると、そのスコープ内でのみアクセスできます。 これにも当てはまります*exception_object_pointer_name*にも適用されます。

例外とキャッチのマクロの詳細については、[例外処理](../../mfc/exception-handling-in-mfc.md)を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCExceptions#26](../../mfc/codesnippet/cpp/exception-processing_1.cpp)]

##  <a name="catch_all"></a>CATCH_ALL

上記でスローされたすべての例外の種類をキャッチするコードのブロックを定義します**TRY**ブロックします。

```
CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>パラメーター

*exception_object_pointer_name*<br/>
マクロによって作成される例外オブジェクトポインターの名前を指定します。 ポインター名を使用して、 `CATCH_ALL`ブロック内の例外オブジェクトにアクセスできます。 この変数は、ユーザーに対して宣言されます。

### <a name="remarks"></a>Remarks

例外処理コードは、必要に応じて例外オブジェクトを問い合わせて、例外の特定の原因に関する詳細情報を取得することができます。 マクロを`THROW_LAST`呼び出して、処理を次の外側の例外フレームにシフトします。 使用する場合**CATCH_ALL**、終了、**TRY**END_CATCH_ALL マクロを使用してブロックします。

> [!NOTE]
>  **CATCH_ALL**ブロックは、中かっこでC++囲まれたスコープとして定義されます。 このスコープで変数を宣言すると、そのスコープ内でのみアクセスできます。

例外の詳細については、[例外処理](../../mfc/exception-handling-in-mfc.md)」を参照してください。

### <a name="example"></a>例

[CFile::Abort](../../mfc/reference/cfile-class.md#abort) の例を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="and_catch"></a>AND_CATCH

直前に追加の例外の種類をキャッチするためのコードのブロックを定義します**TRY**ブロックします。

```
AND_CATCH(exception_class, exception_object_pointer_name)
```

### <a name="parameters"></a>パラメーター

*exception_class*<br/>
テストする例外の種類を指定します。 標準の例外クラスの一覧については、「クラス[CException](../../mfc/reference/cexception-class.md)」を参照してください。

*exception_object_pointer_name*<br/>
マクロによって作成される例外オブジェクトポインターの名前。 ポインター名を使用して、 **AND_CATCH**ブロック内の例外オブジェクトにアクセスできます。 この変数は、ユーザーに対して宣言されます。

### <a name="remarks"></a>Remarks

CATCH マクロの 1 つの例外タイプをキャッチする AND_CATCH マクロを使用します。 終了、**TRY**END_CATCH マクロを使用してブロックします。

例外処理コードは、必要に応じて、例外の原因を特定に関する詳細を取得する場合、例外オブジェクトを問い合わせることができます。 内で THROW_LAST マクロを呼び出し、 **AND_CATCH** shift キーを押し、次のフレームの外側の例外を処理するブロックします。 **AND_CATCH** 、上記の終了をマーク**CATCH**または**AND_CATCH**ブロックします。

> [!NOTE]
>  **AND_CATCH**ブロックは、C++として定義されます（中かっこで区切られます）。 このスコープで変数を宣言する場合、そのスコープ内でのみアクセス可能であることに注意してください。 これは*exception_object_pointer_name*変数にも適用されます。

### <a name="example"></a>例

[CATCH](#catch)の例を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx
##  <a name="and_catch_all"></a>AND_CATCH_ALL

直前に追加の例外の種類をキャッチするためのコードのブロックを定義します**TRY**ブロックします。

```
AND_CATCH_ALL(exception_object_pointer_name)
```

### <a name="parameters"></a>パラメーター

*exception_object_pointer_name*<br/>
マクロによって作成される例外オブジェクトポインターの名前。 ポインター名を使用して、 **AND_CATCH_ALL**ブロック内の例外オブジェクトにアクセスできます。 この変数は、ユーザーに対して宣言されます。

### <a name="remarks"></a>Remarks

使用して、**CATCH**マクロを 1 つの例外の種類をキャッチし、AND_CATCH_ALL マクロの他のすべての後続の種類をキャッチします。 AND_CATCH_ALL を使用する場合は、終了、**TRY** END_CATCH_ALL マクロを使用してブロックします。

例外処理コードは、必要に応じて、例外の原因を特定に関する詳細を取得する場合、例外オブジェクトを問い合わせることができます。 内で THROW_LAST マクロを呼び出し、 **AND_CATCH_ALL** shift キーを押し、次のフレームの外側の例外を処理するブロックします。 **AND_CATCH_ALL** 、上記の終了をマーク**CATCH**または**AND_CATCH_ALL**ブロックします。

> [!NOTE]
>  **AND_CATCH_ALL**ブロックは、C++スコープとして定義されます（中かっこで囲まれています）。 このスコープで変数を宣言する場合、そのスコープ内でのみアクセス可能であることに注意してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="end_catch"></a>END_CATCH

最後の終了をマーク**CATCH**または**AND_CATCH**ブロックします

```
END_CATCH
```

### <a name="remarks"></a>Remarks

END_CATCH マクロの詳細については、[例外処理](../../mfc/exception-handling-in-mfc.md) を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="end_catch_all"></a>END_CATCH_ALL

最後の終了をマーク**CATCH_ALL88** または **AND_CATCH_ALL**ブロックします。

```
END_CATCH_ALL
```

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="throw"></a>THROW (MFC)

指定された例外をスローします。

```
THROW(exception_object_pointer)
```

### <a name="parameters"></a>パラメーター

*exception_object_pointer*<br/>
から`CException`派生した例外オブジェクトを指します。

### <a name="remarks"></a>Remarks

**スロー**プログラムに関連付けられているコントロールを渡して、実行に割り込みます**CATCH**でプログラムをブロックします。 提供されていない場合、**CATCH**ブロック、エラーが出力メッセージを終了する Microsoft Foundation Class ライブラリ モジュールに制御が渡されます。

詳細については、[例外処理](../../mfc/exception-handling-in-mfc.md)を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="throw_last"></a>THROW_LAST

次に戻り、例外をスロー外部**CATCH**ブロックします。

```
THROW_LAST()
```

### <a name="remarks"></a>Remarks

このマクロを使用すると、ローカルで作成された例外をスローすることができます。 キャッチした例外をスローしようとする場合は、通常はスコープ外に移動され、削除されます。 **THROW_LAST**、[次へ] を正常に渡された例外**CATCH**ハンドラー。

詳細については、[例外処理](../../mfc/exception-handling-in-mfc.md)を参照してください。

### <a name="example"></a>例

[CFile::Abort](../../mfc/reference/cfile-class.md#abort) の例を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="afxthrowarchiveexception"></a>  AfxThrowArchiveException

アーカイブの例外をスローします。

```
void  AfxThrowArchiveException(int cause, LPCTSTR lpszArchiveName);
```

### <a name="parameters"></a>パラメーター

*cause*<br/>
例外の原因を示す整数を指定します。 使用可能な値の一覧については、「 [Cアーカイブ例外:: m_cause](../../mfc/reference/carchiveexception-class.md#m_cause)」を参照してください。

*lpszArchiveName*<br/>
例外の原因となった`CArchive`オブジェクトの名前を含む文字列を指します (使用可能な場合)。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="afxthrowfileexception"></a>  AfxThrowFileException

ファイル例外をスローします。

```
void AfxThrowFileException(
    int cause,
    LONG lOsError = -1,
    LPCTSTR lpszFileName = NULL);
```

### <a name="parameters"></a>パラメーター

*cause*<br/>
例外の原因を示す整数を指定します。 使用可能な値については、[CFileException::m_cause](../../mfc/reference/cfileexception-class.md#m_cause)を参照してください。

*lOsError*<br/>
例外の原因を示すオペレーティングシステムエラー番号 (使用可能な場合) が含まれます。 エラーコードの一覧については、オペレーティングシステムのマニュアルを参照してください。

*lpszFileName*<br/>
例外の原因となったファイルの名前を含む文字列を指します (使用可能な場合)。

### <a name="remarks"></a>Remarks

オペレーティングシステムのエラーコードに基づいて、原因を特定する責任があります。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

## <a name="afxthrowinvalidargexception"></a>AfxThrowInvalidArgException

無効な引数の例外をスローします。

### <a name="syntax"></a>構文

```
void AfxThrowInvalidArgException( );
```

### <a name="remarks"></a>Remarks

無効な引数が使用されると、この関数が呼び出されます。

### <a name="requirements"></a>必要条件

**ヘッダー:** afx.h

##  <a name="afxthrowmemoryexception"></a>AfxThrowMemoryException

メモリ例外をスローします。

```
void AfxThrowMemoryException();
```

### <a name="remarks"></a>Remarks

基になるシステムメモリアロケーター ( **malloc**や[GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) Windows 関数など) への呼び出しが失敗した場合に、この関数を呼び出します。 新しいを呼び出す必要はありません。これは、メモリ割り当てが失敗した場合に、**新しい**がメモリ例外を自動的にスローするためです。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="afxthrownotsupportedexception"></a>  AfxThrowNotSupportedException

サポートされていない機能に対する要求の結果である例外をスローします。

```
void AfxThrowNotSupportedException();
```

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="afxthrowresourceexception"></a>  AfxThrowResourceException

リソース例外をスローします。

```
void  AfxThrowResourceException();
```

### <a name="remarks"></a>Remarks

通常、この関数は、Windows リソースを読み込むことができないときに呼び出されます。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="afxthrowuserexception"></a>AfxThrowUserException

エンドユーザーの操作を停止する例外をスローします。

```
void AfxThrowUserException();
```

### <a name="remarks"></a>Remarks

通常、この関数は、が`AfxMessageBox`ユーザーにエラーを報告した直後に呼び出されます。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="afxthrowoledispatchexception"></a>  AfxThrowOleDispatchException

OLE オートメーション関数内で例外をスローするには、この関数を使用します。

```
void AFXAPI AfxThrowOleDispatchException(
    WORD wCode ,
    LPCSTR lpszDescription,
    UINT nHelpID = 0);

void AFXAPI AfxThrowOleDispatchException(
    WORD wCode,
    UINT nDescriptionID,
    UINT nHelpID = -1);
```

### <a name="parameters"></a>パラメーター

*wCode*<br/>
アプリケーション固有のエラーコード。

*lpszDescription*<br/>
エラーの説明。

*nDescriptionID*<br/>
音声エラーの説明のリソース ID。

*nHelpID*<br/>
アプリケーションのヘルプのヘルプコンテキスト (.HLP) ファイル。

### <a name="remarks"></a>Remarks

この関数に提供される情報は、運転アプリケーション (Microsoft Visual Basic またはその他の OLE オートメーションクライアントアプリケーション) によって表示できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCExceptions#25](../../mfc/codesnippet/cpp/exception-processing_2.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="afxthrowoleexception"></a>AfxThrowOleException

型`COleException`のオブジェクトを作成し、例外をスローします。

```
void AFXAPI AfxThrowOleException(SCODE sc);
void AFXAPI AfxThrowOleException(HRESULT hr);
```

### <a name="parameters"></a>パラメーター

*sc*<br/>
例外の理由を示す OLE ステータスコード。

*hr*<br/>
例外の理由を示す結果コードを処理します。

### <a name="remarks"></a>Remarks

引数として HRESULT を受け取るバージョンは、その結果コードを対応する SCODE に変換します。 HRESULT と SCODE の詳細については、「Windows SDK の[COM エラーコードの構造](/windows/win32/com/structure-of-com-error-codes)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdao

##  <a name="afxthrowdaoexception"></a>AfxThrowDaoException

独自のコードから[CDaoException](../../mfc/reference/cdaoexception-class.md)型の例外をスローするには、この関数を呼び出します。

```
void AFXAPI AfxThrowDaoException(
    int nAfxDaoError = NO_AFX_DAO_ERROR,
    SCODE scode = S_OK);
```

### <a name="parameters"></a>パラメーター

*nAfxDaoError*<br/>
DAO 拡張エラーコードを表す整数値。 [CDaoException:: m_nAfxDaoError](../../mfc/reference/cdaoexception-class.md#m_nafxdaoerror)の下に一覧表示されている値のいずれかを指定できます。

*scode*<br/>
型 SCODE の DAO からの OLE エラーコード。 詳細については、「 [CDaoException:: m_scode](../../mfc/reference/cdaoexception-class.md#m_scode)」を参照してください。

### <a name="remarks"></a>Remarks

フレームワークも `AfxThrowDaoException` を呼び出します。 ユーザーからの呼び出しでは、パラメータのどちらか一方または両方を渡します。 たとえば、 **CDaoException:: nAfxDaoError**  で定義されているエラーの 1 つを発生させるときにパラメータ *scode* が必要ない場合は、パラメータ *nAfxDaoError* に有効な値を渡し、 *scode* は既定の値を受け入れます。

MFC DAO クラスに関連した例外の詳細については、 `CDaoException` クラスを参照してください。さらに、[例外処理 :データベースの例外](../../mfc/exceptions-database-exceptions.md) を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxdb.h

##  <a name="afxthrowdbexception"></a>  AfxThrowDBException

独自のコードから型`CDBException`の例外をスローするには、この関数を呼び出します。

```
void AfxThrowDBException(
    RETCODE nRetCode,
    CDatabase* pdb,
    HSTMT hstmt);
```

### <a name="parameters"></a>パラメーター

*nRetCode*<br/>
例外をスローする原因となったエラーの型を定義した RETCODE 型の値を指定します。

*pdb*<br/>
`CDatabase` オブジェクトへのポインタ。このオブジェクトは、例外に関連するデータ ソース接続を表します。

*hstmt*<br/>
ODBC HSTMT ハンドルです。このハンドルは、例外に関連するステートメント ハンドルを指定します。

### <a name="remarks"></a>Remarks

フレームワークは、ODBC API 関数の呼び出しから ODBC RETCODE を受け取ると、`AfxThrowDBException` を呼び出し、RETCODE を予期されるエラーではなく例外条件として解釈します。 たとえば、ディスク読み取りエラーが原因でデータ アクセス操作が失敗する場合があります。

ODBC によって定義された RETCODE 値については、『Windows SDK』の第 8 章「Retrieving Status and Error Information」を参照してください。 これらのコードの MFC 拡張機能については、「[CDBException クラス](../../mfc/reference/cdbexception-class.md)」を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

##  <a name="afxabort"></a>AfxAbort

MFC によって提供される既定の終了関数。

```
void  AfxAbort();
```

### <a name="remarks"></a>Remarks

`AfxAbort`は、キャッチできない例外などの致命的なエラーが発生した場合に、MFC メンバー関数によって内部的に呼び出されます。 を復元でき`AfxAbort`ない致命的なエラーが発生した場合は、まれにを呼び出すことができます。

### <a name="example"></a>例

[CATCH](#catch)の例を参照してください。

### <a name="requirements"></a>必要条件

  **ヘッダー** afx

## <a name="see-also"></a>関連項目

[マクロとグローバル](mfc-macros-and-globals.md)<br/>
[CException クラス](cexception-class.md)<br/>
[CInvalidArgException クラス](cinvalidargexception-class.md)
