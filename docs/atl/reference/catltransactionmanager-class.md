---
title: CAtlTransactionManager クラス
ms.date: 11/04/2016
f1_keywords:
- CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::CAtlTransactionManager
- ATLTRANSACTIONMANAGER/ATL::Close
- ATLTRANSACTIONMANAGER/ATL::Commit
- ATLTRANSACTIONMANAGER/ATL::Create
- ATLTRANSACTIONMANAGER/ATL::CreateFile
- ATLTRANSACTIONMANAGER/ATL::DeleteFile
- ATLTRANSACTIONMANAGER/ATL::FindFirstFile
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::GetFileAttributesEx
- ATLTRANSACTIONMANAGER/ATL::GetHandle
- ATLTRANSACTIONMANAGER/ATL::IsFallback
- ATLTRANSACTIONMANAGER/ATL::MoveFile
- ATLTRANSACTIONMANAGER/ATL::RegCreateKeyEx
- ATLTRANSACTIONMANAGER/ATL::RegDeleteKey
- ATLTRANSACTIONMANAGER/ATL::RegOpenKeyEx
- ATLTRANSACTIONMANAGER/ATL::Rollback
- ATLTRANSACTIONMANAGER/ATL::SetFileAttributes
- ATLTRANSACTIONMANAGER/ATL::m_bFallback
- ATLTRANSACTIONMANAGER/ATL::m_hTransaction
helpviewer_keywords:
- CAtlTransactionManager class
ms.assetid: b01732dc-1d16-4b42-bfac-b137fca2b740
ms.openlocfilehash: d72867eaa449a20e676d4eddc4c94c02090334e5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497719"
---
# <a name="catltransactionmanager-class"></a>CAtlTransactionManager クラス

CAtlTransactionManager クラスには、カーネルトランザクションマネージャー (KTM) 関数のラッパーが用意されています。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CAtlTransactionManager;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[~ CAtlTransactionManager](#dtor)|CAtlTransactionManager デストラクター。|
|[CAtlTransactionManager](#catltransactionmanager)|CAtlTransactionManager コンストラクター。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[閉じる](#close)|1つのトランザクションハンドルを閉じます。|
|[貢献](#commit)|トランザクションがコミットされることを要求します。|
|[作成](#create)|トランザクションハンドルを作成します。|
|[CreateFile](#createfile)|ファイル、ファイルストリーム、またはディレクトリをトランザクション操作として作成または開きます。|
|[DeleteFile](#deletefile)|トランザクション操作として既存のファイルを削除します。|
|[れる findfirstfile](#findfirstfile)|ファイルまたはサブディレクトリをトランザクション操作として検索します。|
|[GetFileAttributes](#getfileattributes)|トランザクション操作として、指定したファイルまたはディレクトリのファイルシステム属性を取得します。|
|[GetFileAttributesEx](#getfileattributesex)|トランザクション操作として、指定したファイルまたはディレクトリのファイルシステム属性を取得します。|
|[GetHandle](#gethandle)|トランザクションハンドルを返します。|
|[IsFallback](#isfallback)|フォールバック呼び出しが有効かどうかを判断します。|
|[My.computer.filesystem.movefile](#movefile)|既存のファイルまたはディレクトリ (子を含む) をトランザクション操作として移動します。|
|[RegCreateKeyEx](#regcreatekeyex)|指定されたレジストリキーを作成し、トランザクションに関連付けます。 キーが既に存在する場合は、関数によって開かれます。|
|[RegDeleteKey](#regdeletekey)|トランザクション操作として、指定したプラットフォーム固有のレジストリビューからサブキーとその値を削除します。|
|[Regopenkeyex が](#regopenkeyex)|指定されたレジストリキーを開き、それをトランザクションに関連付けます。|
|[ロールバック](#rollback)|トランザクションがロールバックされることを要求します。|
|[SetFileAttributes](#setfileattributes)|ファイルまたはディレクトリの属性をトランザクション操作として設定します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[m_bFallback](#m_bfallback)|フォールバックがサポートされている場合は TRUE。それ以外の場合は FALSE。|
|[m_hTransaction](#m_htransaction)|トランザクションハンドル。|

## <a name="remarks"></a>Remarks

## <a name="inheritance-hierarchy"></a>継承階層

[ATL:: CAtlTransactionManager](../../atl/reference/catltransactionmanager-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** atltransactionmanager. h

##  <a name="dtor"></a>~ CAtlTransactionManager

CAtlTransactionManager デストラクター。

```
virtual ~CAtlTransactionManager();
```

### <a name="remarks"></a>Remarks

通常の処理では、トランザクションは自動的にコミットされて閉じられます。 例外のアンワインド中にデストラクターが呼び出されると、トランザクションはロールバックされて閉じられます。

##  <a name="catltransactionmanager"></a>CAtlTransactionManager

CAtlTransactionManager コンストラクター。

```
CAtlTransactionManager(BOOL bFallback = TRUE, BOOL bAutoCreateTransaction = TRUE);
```

### <a name="parameters"></a>パラメーター

*bFallback*<br/>
TRUE は、サポートフォールバックを示します。 トランザクション関数が失敗した場合、クラスは自動的に "非トランザクション" 関数を呼び出します。 FALSE は、"フォールバック" 呼び出しがないことを示します。

*bAutoCreateTransaction*<br/>
TRUE は、トランザクションハンドラーがコンストラクターに自動的に作成されることを示します。 FALSE は、そうでないことを示します。

### <a name="remarks"></a>Remarks

##  <a name="close"></a>Ok

トランザクションハンドルを閉じます。

```
inline BOOL Close();
```

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このラッパーは、 `CloseHandle`関数を呼び出します。 メソッドは、デストラクターで自動的に呼び出されます。

##  <a name="commit"></a>貢献

トランザクションがコミットされることを要求します。

```
inline BOOL Commit();
```

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このラッパーは、 `CommitTransaction`関数を呼び出します。 メソッドは、デストラクターで自動的に呼び出されます。

##  <a name="create"></a>生成

トランザクションハンドルを作成します。

```
inline BOOL Create();
```

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このラッパーは、 `CreateTransaction`関数を呼び出します。 確認する対象

##  <a name="createfile"></a>CreateFile

ファイル、ファイルストリーム、またはディレクトリをトランザクション操作として作成または開きます。

```
inline HANDLE CreateFile(
    LPCTSTR lpFileName,
    DWORD dwDesiredAccess,
    DWORD dwShareMode,
    LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    DWORD dwCreationDisposition,
    DWORD dwFlagsAndAttributes,
    HANDLE hTemplateFile);
```

### <a name="parameters"></a>パラメーター

*lpFileName*<br/>
作成または開くオブジェクトの名前。

*dwDesiredAccess*<br/>
オブジェクトへのアクセス。読み取り、書き込み、またはその両方 (ゼロ) としてまとめることができます。 最もよく使用される値は、GENERIC_READ、GENERIC_WRITE、または both です。GENERIC_READ &#124; GENERIC_WRITE。

*dwShareMode*<br/>
オブジェクトの共有モード。読み取り、書き込み、両方、削除、これらすべて、またはなしを指定できます。0、FILE_SHARE_DELETE、FILE_SHARE_READ、FILE_SHARE_WRITE。

*lpSecurityAttributes*<br/>
オプションのセキュリティ記述子を格納している SECURITY_ATTRIBUTES 構造体へのポインター。また、返されたハンドルを子プロセスが継承できるかどうかも決定します。 パラメーターには NULL を指定できます。

*Dwの廃棄*<br/>
存在し、存在しないファイルに対して実行するアクション。 このパラメーターには、次のいずれかの値を指定する必要があります。これらを組み合わせることはできません。CREATE_ALWAYS、CREATE_NEW、OPEN_ALWAYS、OPEN_EXISTING、または TRUNCATE_EXISTING。

*dwFlagsAndAttributes*<br/>
ファイルの属性とフラグ。 このパラメーターには、使用可能なファイル属性 (FILE_ATTRIBUTE_ *) の任意の組み合わせを含めることができます。 その他のすべてのファイル属性は、FILE_ATTRIBUTE_NORMAL をオーバーライドします。 このパラメーターには、バッファー動作、アクセスモード\*、およびその他の特殊な目的フラグを制御するためのフラグ (FILE_FLAG_) の組み合わせを含めることもできます。 これらは、任意の\* FILE_ATTRIBUTE_ 値と結合されます。

*hTemplateFile*<br/>
GENERIC_READ アクセス権を持つテンプレートファイルへの有効なハンドル。 テンプレートファイルには、作成するファイルのファイル属性と拡張属性が用意されています。 このパラメーターには NULL を指定できます。

### <a name="return-value"></a>戻り値

オブジェクトへのアクセスに使用できるハンドルを返します。

### <a name="remarks"></a>Remarks

このラッパーは、 `CreateFileTransacted`関数を呼び出します。

##  <a name="deletefile"></a>  DeleteFile

トランザクション操作として既存のファイルを削除します。

```
inline BOOL DeleteFile(LPCTSTR lpFileName);
```

### <a name="parameters"></a>パラメーター

*lpFileName*<br/>
削除するファイルの名前。

### <a name="remarks"></a>Remarks

このラッパーは、 `DeleteFileTransacted`関数を呼び出します。

##  <a name="findfirstfile"></a>れる findfirstfile

ファイルまたはサブディレクトリをトランザクション操作として検索します。

```
inline HANDLE FindFirstFile(
    LPCTSTR lpFileName,
    WIN32_FIND_DATA* pNextInfo);
```

### <a name="parameters"></a>パラメーター

*lpFileName*<br/>
ディレクトリまたはパス、および検索するファイル名。 このパラメーターには、アスタリスク (*) や疑問符 () などのワイルドカード文字を含めることができます。

*pNextInfo*<br/>
検出されたファイルまたはサブディレクトリに関する情報を受け取る WIN32_FIND_DATA 構造体へのポインター。

### <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は、または`FindNextFile` `FindClose`への後続の呼び出しで使用される検索ハンドルになります。 関数が失敗するか、 *Lpfilename*パラメーターの検索文字列からファイルを見つけることができない場合、戻り値は INVALID_HANDLE_VALUE です。

### <a name="remarks"></a>Remarks

このラッパーは、 `FindFirstFileTransacted`関数を呼び出します。

##  <a name="getfileattributes"></a>GetFileAttributes

トランザクション操作として、指定したファイルまたはディレクトリのファイルシステム属性を取得します。

```
inline DWORD GetFileAttributes(LPCTSTR lpFileName);
```

### <a name="parameters"></a>パラメーター

*lpFileName*<br/>
ファイルまたはディレクトリの名前。

### <a name="remarks"></a>Remarks

このラッパーは、 `GetFileAttributesTransacted`関数を呼び出します。

##  <a name="getfileattributesex"></a>GetFileAttributesEx

トランザクション操作として、指定したファイルまたはディレクトリのファイルシステム属性を取得します。

```
inline BOOL GetFileAttributesEx(
    LPCTSTR lpFileName,
    GET_FILEEX_INFO_LEVELS fInfoLevelId,
    LPVOID lpFileInformation);
```

### <a name="parameters"></a>パラメーター

*lpFileName*<br/>
ファイルまたはディレクトリの名前。

*Finを*<br/>
取得する属性情報のレベル。

*lpFileInformation*<br/>
属性情報を受け取るバッファーへのポインター。 このバッファーに格納されている属性情報の型は、Finの値によって決まります。 FinGetFileExInfoStandard *Ev d*パラメーターが指定されている場合、このパラメーターは WIN32_FILE_ATTRIBUTE_DATA 構造体を指します。

### <a name="remarks"></a>Remarks

このラッパーは、 `GetFileAttributesTransacted`関数を呼び出します。

##  <a name="gethandle"></a>GetHandle

トランザクションハンドルを返します。

```
HANDLE GetHandle() const;
```

### <a name="return-value"></a>戻り値

クラスのトランザクションハンドルを返します。 `CAtlTransactionManager`がハンドルにアタッチされていない場合は NULL を返します。

### <a name="remarks"></a>Remarks

##  <a name="isfallback"></a>  IsFallback

フォールバック呼び出しが有効かどうかを判断します。

```
BOOL IsFallback() const;
```

### <a name="return-value"></a>戻り値

クラスがフォールバック呼び出しをサポートしている場合に TRUE を返します。 それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="m_bfallback"></a>  m_bFallback

フォールバックがサポートされている場合は TRUE。それ以外の場合は FALSE。

```
BOOL m_bFallback;
```

### <a name="remarks"></a>Remarks

##  <a name="m_htransaction"></a>m_hTransaction

トランザクションハンドル。

```
HANDLE m_hTransaction;
```

### <a name="remarks"></a>Remarks

##  <a name="movefile"></a>My.computer.filesystem.movefile

既存のファイルまたはディレクトリ (子を含む) をトランザクション操作として移動します。

```
inline BOOL MoveFile(LPCTSTR lpOldFileName, LPCTSTR lpNewFileName);
```

### <a name="parameters"></a>パラメーター

*lpOldFileName*<br/>
ローカルコンピューター上の既存のファイルまたはディレクトリの現在の名前。

*lpNewFileName*<br/>
ファイルまたはディレクトリの新しい名前。 この名前は既に存在していてはなりません。 新しいファイルが別のファイルシステムまたはドライブに存在する可能性があります。 新しいディレクトリは、同じドライブ上にある必要があります。

### <a name="remarks"></a>Remarks

このラッパーは、 `MoveFileTransacted`関数を呼び出します。

##  <a name="regcreatekeyex"></a>  RegCreateKeyEx

指定されたレジストリキーを作成し、トランザクションに関連付けます。 キーが既に存在する場合は、関数によって開かれます。

```
inline LSTATUS RegCreateKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD dwReserved,
    LPTSTR lpClass,
    DWORD dwOptions,
    REGSAM samDesired,
    CONST LPSECURITY_ATTRIBUTES lpSecurityAttributes,
    PHKEY phkResult,
    LPDWORD lpdwDisposition);
```

### <a name="parameters"></a>パラメーター

*hKey*<br/>
開いているレジストリキーを処理するハンドル。

*lpSubKey*<br/>
この関数が開いたり作成したりするサブキーの名前。

*dwReserved*<br/>
このパラメーターは予約されており、ゼロにする必要があります。

*lpClass*<br/>
このキーのユーザー定義クラス。 このパラメーターは無視してもかまいません。 このパラメーターには NULL を指定できます。

*dwOptions*<br/>
このパラメーターには、次のいずれかの値を指定できます。REG_OPTION_BACKUP_RESTORE、REG_OPTION_NON_VOLATILE、または REG_OPTION_VOLATILE。

*samDesired*<br/>
キーのアクセス権を指定するマスク。

*lpSecurityAttributes*<br/>
返されたハンドルを子プロセスが継承できるかどうかを決定する SECURITY_ATTRIBUTES 構造体へのポインター。 *Lpsecurityattributes*が NULL の場合、ハンドルを継承することはできません。

*phkResult*<br/>
開かれたキーまたは作成されたキーへのハンドルを受け取る変数へのポインター。 キーが定義済みのレジストリキーのいずれでもない場合は`RegCloseKey` 、ハンドルの使用が終了した後で関数を呼び出します。

*lpdwDisposition*<br/>
次のいずれかのディスポジション値を受け取る変数へのポインター。REG_CREATED_NEW_KEY または REG_OPENED_EXISTING_KEY。

### <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は ERROR_SUCCESS です。 関数が失敗した場合、戻り値は Winerror.h で定義されている0以外のエラーコードになります。

### <a name="remarks"></a>Remarks

このラッパーは、 `RegCreateKeyTransacted`関数を呼び出します。

##  <a name="regdeletekey"></a>  RegDeleteKey

トランザクション操作として、指定したプラットフォーム固有のレジストリビューからサブキーとその値を削除します。

```
inline LSTATUS RegDeleteKeyEx(HKEY hKey, LPCTSTR lpSubKey);
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*hKey*|開いているレジストリキーを処理するハンドル。|
|*lpSubKey*|削除するキーの名前。|

### <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は ERROR_SUCCESS です。 関数が失敗した場合、戻り値は Winerror.h で定義されている0以外のエラーコードになります。

### <a name="remarks"></a>Remarks

このラッパーは、 `RegDeleteKeyTransacted`関数を呼び出します。

##  <a name="regopenkeyex"></a>Regopenkeyex が

指定されたレジストリキーを開き、それをトランザクションに関連付けます。

```
inline LSTATUS RegOpenKeyEx(
    HKEY hKey,
    LPCTSTR lpSubKey,
    DWORD ulOptions,
    REGSAM samDesired,
    PHKEY phkResult);
```

### <a name="parameters"></a>パラメーター

*hKey*<br/>
開いているレジストリキーを処理するハンドル。

*lpSubKey*<br/>
開くレジストリサブキーの名前。

*ulOptions*<br/>
このパラメーターは予約されており、ゼロにする必要があります。

*samDesired*<br/>
キーのアクセス権を指定するマスク。

*phkResult*<br/>
開かれたキーまたは作成されたキーへのハンドルを受け取る変数へのポインター。 キーが定義済みのレジストリキーのいずれでもない場合は`RegCloseKey` 、ハンドルの使用が終了した後で関数を呼び出します。

### <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は ERROR_SUCCESS です。 関数が失敗した場合、戻り値は Winerror.h で定義されたゼロ以外のエラーコードになります。

### <a name="remarks"></a>Remarks

このラッパーは、 `RegOpenKeyTransacted`関数を呼び出します。

##  <a name="rollback"></a>ロールバック

トランザクションがロールバックされることを要求します。

```
inline BOOL Rollback();
```

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このラッパーは、 `RollbackTransaction`関数を呼び出します。

##  <a name="setfileattributes"></a>SetFileAttributes

ファイルまたはディレクトリの属性をトランザクション操作として設定します。

```
inline BOOL SetFileAttributes(LPCTSTR lpFileName, DWORD dwAttributes);
```

### <a name="parameters"></a>パラメーター

*lpFileName*<br/>
ファイルまたはディレクトリの名前。

*dwAttributes*<br/>
ファイルに設定するファイル属性。 詳細については、「 [SetFileAttributesTransacted](/windows/win32/api/winbase/nf-winbase-setfileattributestransactedw)」を参照してください。

### <a name="remarks"></a>Remarks

このラッパーは、 `SetFileAttributesTransacted`関数を呼び出します。

## <a name="see-also"></a>関連項目

[ATL COM デスクトップ コンポーネント](../../atl/atl-com-desktop-components.md)
