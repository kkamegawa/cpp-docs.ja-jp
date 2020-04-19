---
title: 'テクニカル ノート 54: MFC DAO クラス使用中の DAO の直接呼び出し'
ms.date: 09/17/2019
helpviewer_keywords:
- MFC, DAO and
- passwords [MFC], calling DAO
- security [MFC], DAO
- DAO (Data Access Objects), calling directly
- DAO (Data Access Objects), security
- security [MFC]
- TN054
- DAO (Data Access Objects), and MFC
ms.assetid: f7de7d85-8d6c-4426-aa05-2e617c0da957
ms.openlocfilehash: 0eb9daf156f51ecb4eb1e6fdc721b34878a43351
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303416"
---
# <a name="tn054-calling-dao-directly-while-using-mfc-dao-classes"></a>テクニカル ノート 54: MFC DAO クラス使用中の DAO の直接呼び出し

> [!NOTE]
> DAO は Access データベースで使用され、Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。 ビジュアルC++環境とウィザードでは、dao はサポートされていません (dao クラスは含まれていますが、引き続き使用できます)。 新しいプロジェクトには、 [OLE DB テンプレート](../data/oledb/ole-db-templates.md)または[ODBC および MFC](../data/odbc/odbc-and-mfc.md)を使用することをお勧めします。 既存のアプリケーションを維持するには、DAO のみを使用する必要があります。

MFC DAO データベースクラスを使用する場合、DAO を直接使用する必要がある場合があります。 通常、これは当てはまりませんが、mfc クラスの使用と直接の DAO 呼び出しを組み合わせることによって、直接の DAO 呼び出しを容易にするためのヘルパーメカニズムが用意されています。 MFC で管理されている DAO オブジェクトのメソッドに対して直接の DAO 呼び出しを行う場合は、数行のコードを記述するだけで済みます。 MFC で管理されて*いない*DAO オブジェクトを作成して使用する必要がある場合は、実際にオブジェクトで `Release` を呼び出すことによって、もう少し作業を行う必要があります。 このテクニカルノートでは、DAO を直接呼び出す方法、MFC ヘルパーが行うことができること、および DAO OLE インターフェイスの使用方法について説明します。 最後に、dao のセキュリティ機能を使用して DAO を直接呼び出す方法を示すサンプル関数について説明します。

## <a name="when-to-make-direct-dao-calls"></a>直接の DAO 呼び出しを行う場合

直接の DAO 呼び出しを行う最も一般的な状況は、コレクションを更新する必要がある場合や、MFC でラップされていない機能を実装する場合に発生します。 MFC で公開されていない最も重要な機能はセキュリティです。 セキュリティ機能を実装する場合は、DAO ユーザーおよびグループオブジェクトを直接使用する必要があります。 セキュリティとは別に、MFC でサポートされていない DAO 機能が他にもいくつかあります。 これには、レコードセットの複製とデータベースレプリケーションの機能に加え、DAO へのいくつかの遅延追加が含まれます。

## <a name="a-brief-overview-of-dao-and-mfcs-implementation"></a>DAO と MFC の実装の概要

MFC が DAO をラップすることにより、多くの詳細を処理することで DAO を簡単に使用できるようになるため、ほとんどのことを心配する必要がありません。 これには、OLE の初期化、DAO オブジェクト (特にコレクションオブジェクト) の作成と管理、エラーチェック、厳密に型指定された単純なインターフェイス ( **VARIANT**または `BSTR` 引数なし) の提供が含まれます。 直接の DAO 呼び出しを行うことができますが、これらの機能は引き続き利用できます。 すべてのコードは、直接の DAO 呼び出しによって作成されたすべてのオブジェクトに対して `Release` を呼び出す必要があります。また、MFC が内部で使用するインターフェイスポインターを変更し*ません*。 たとえば、*すべて*の内部的な影響を理解している場合を除き、開いている `CDaoRecordset` オブジェクトの*m_pDAORecordset*メンバーを変更しないでください。 ただし、 *m_pDAORecordset*インターフェイスを使用して DAO を直接呼び出して、フィールドコレクションを取得することもできます。 この場合、 *m_pDAORecordset*メンバーは変更されません。 オブジェクトの操作が完了したら、Fields コレクションオブジェクトの `Release` を呼び出す必要があります。

## <a name="description-of-helpers-to-make-dao-calls-easier"></a>DAO 呼び出しを容易にするヘルパーの説明

DAO の呼び出しを容易にするために用意されているヘルパーは、MFC DAO データベースクラスで内部的に使用されるヘルパーと同じです。 これらのヘルパーは、直接の DAO 呼び出しを行うとき、デバッグ出力をログに記録するとき、予想されるエラーをチェックし、必要に応じて適切な例外をスローするときに、リターンコードを確認するために使用されます。 2つの基になるヘルパー関数と、これら2つのヘルパーのいずれかにマップされる4つのマクロがあります。 最も簡単な説明は、単にコードを読むことです。 AFXDAO の「 **DAO_CHECK**、 **DAO_CHECK_ERROR**、 **DAO_CHECK_MEM**、および**DAO_TRACE** 」を参照してください。マクロを表示するには、「 **AfxDaoCheck** and **AfxDaoTrace** in da」を参照してください.CPP.

## <a name="using-the-dao-ole-interfaces"></a>DAO OLE インターフェイスの使用

DAO オブジェクト階層内の各オブジェクトの OLE インターフェイスは、ヘッダーファイル DBDAOINT で定義されています。H。これは、Visual Studio .NET 2003 \ VC7\include ディレクトリにあります。 これらのインターフェイスには、DAO 階層全体を操作できるメソッドが用意されています。

DAO インターフェイスの多くのメソッドでは、`BSTR` オブジェクト (OLE オートメーションで使用される長さのプレフィックスが付けられた文字列) を操作する必要があります。 `BSTR` オブジェクトは、通常、**バリアント**データ型内にカプセル化されます。 MFC クラス `COleVariant` 自体は、 **VARIANT**データ型から継承されます。 ANSI または Unicode 用にプロジェクトをビルドするかどうかによって、DAO インターフェイスは ANSI または Unicode `BSTR`s を返します。 V_BSTR と V_BSTRT の2つのマクロは、必要な型の `BSTR` を DAO インターフェイスが確実に取得できるようにするために役立ちます。

V_BSTR は、`COleVariant`の*Bstrval*メンバーを抽出します。 このマクロは、通常、`COleVariant` の内容を DAO インターフェイスのメソッドに渡す必要がある場合に使用します。 次のコード片は、V_BSTR マクロを利用する DAO DAOUser インターフェイスの2つのメソッドの宣言と実際の使用方法を示しています。

```cpp
COleVariant varOldName;
COleVariant varNewName(_T("NewUser"), VT_BSTRT);

// Code to assign pUser to a valid value omitted DAOUser *pUser = NULL;

// These method declarations were taken from DBDAOINT.H
// STDMETHOD(get_Name) (THIS_ BSTR FAR* pbstr) PURE;
// STDMETHOD(put_Name) (THIS_ BSTR bstr) PURE;
DAO_CHECK(pUser->get_Name(&V_BSTR (&varOldName)));
DAO_CHECK(pUser->put_Name(V_BSTR (&varNewName)));
```

上の `COleVariant` コンストラクターで指定された `VT_BSTRT` 引数によって、ANSI バージョンのアプリケーションをビルドする場合は `COleVariant` に ANSI `BSTR` が使用され、アプリケーションの Unicode バージョンでは Unicode `BSTR` が使用されることに注意してください。 これは、DAO が期待するものです。

もう1つのマクロである V_BSTRT は、ビルドの種類 (ANSI または Unicode) に応じて、`COleVariant` の ANSI または Unicode の*Bstrval*メンバーを抽出します。 次のコードは、`COleVariant` から `CString`に `BSTR` 値を抽出する方法を示しています。

```cpp
COleVariant varName(_T("MyName"), VT_BSTRT);
CString str = V_BSTRT(&varName);
```

V_BSTRT マクロと、`COleVariant`に格納されている他の型を開くためのその他の手法については、「DAOVIEW のサンプル」で説明されています。 具体的には、この変換は `CCrack::strVARIANT` メソッドで実行されます。 このメソッドは、可能であれば、`COleVariant` の値を `CString`のインスタンスに変換します。

## <a name="simple-example-of-a-direct-call-to-dao"></a>DAO の直接呼び出しの簡単な例

状況によっては、基になる DAO コレクションオブジェクトを更新する必要がある場合に発生することがあります。 通常、この操作は必要ありませんが、必要に応じて簡単な手順です。 コレクションを更新する必要がある場合の例として、複数のユーザーが新しいテーブルテーブルを作成するマルチユーザー環境で動作する場合が挙げられます。 この場合、テーブルのコレクションが古くなる可能性があります。 コレクションを更新するには、特定のコレクションオブジェクトの `Refresh` メソッドを呼び出して、エラーをチェックするだけです。

```cpp
DAO_CHECK(pMyDaoDatabase->m_pDAOTableDefs->Refresh());
```

現時点では、すべての DAO コレクションオブジェクトインターフェイスは、MFC DAO データベースクラスの実装の詳細には記載されていないことに注意してください。

## <a name="using-dao-directly-for-dao-security-features"></a>Dao のセキュリティ機能に直接 DAO を使用する

MFC DAO データベースクラスは、DAO のセキュリティ機能をラップしません。 Dao のセキュリティ機能を使用するには、DAO インターフェイスのメソッドを呼び出す必要があります。 次の関数は、システムデータベースを設定し、ユーザーのパスワードを変更します。 この関数は、その後定義される3つの他の関数を呼び出します。

```cpp
void ChangeUserPassword()
{
    // Specify path to the Microsoft Access *// system database
    CString strSystemDB =
        _T("c:\\Program Files\\MSOffice\\access\\System.mdw");

    // Set system database before MFC initilizes DAO
    // NOTE: An MFC module uses only one instance
    // of a DAO database engine object. If you have
    // called a DAO object in your application prior
    // to calling the function below, you must call
    // AfxDaoTerm to destroy the existing database
    // engine object. Otherwise, the database engine
    // object already in use will be reused, and setting
    // a system datbase will have no effect.
    //
    // If you have used a DAO object prior to calling
    // this function it is important that DAO be
    // terminated with AfxDaoTerm since an MFC
    // module only gets one copy of the database engine
    // and that engine will be reused if it hasn't been
    // terminated. In other words, if you do not call
    // AfxDaoTerm and there is currently a database
    // initialized, setting the system database will
    // have no effect.
    SetSystemDB(strSystemDB);

    // User name and password manually added
    // by using Microsoft Access
    CString strUserName = _T("NewUser");
    CString strOldPassword = _T("Password");
    CString strNewPassword = _T("NewPassword");

    // Set default user so that MFC will be able
    // to log in by default using the user name and
    // password from the system database
    SetDefaultUser(strUserName, strOldPassword);

    // Change the password. You should be able to
    // call this function from anywhere in your
    // MFC application
    ChangePassword(strUserName, strOldPassword, strNewPassword);

    // ...
}
```

次の4つの例では、次の方法を示します。

- システム DAO データベース () を設定します.MDW ファイル)。

- 既定のユーザーとパスワードを設定します。

- ユーザーのパスワードを変更します。

- のパスワードを変更します。MDB ファイル。

### <a name="setting-the-system-database"></a>システムデータベースの設定

次に示すのは、アプリケーションで使用されるシステムデータベースを設定する関数の例です。 他の DAO 呼び出しを行う前に、この関数を呼び出す必要があります。

```cpp
// Set the system database that the
// DAO database engine will use

void SetSystemDB(CString& strSystemMDB)
{
    COleVariant varSystemDB(strSystemMDB, VT_BSTRT);

    // Initialize DAO for MFC
    AfxDaoInit();
    DAODBEngine* pDBEngine = AfxDaoGetEngine();

    ASSERT(pDBEngine != NULL);

    // Call put_SystemDB method to set the *// system database for DAO engine
    DAO_CHECK(pDBEngine->put_SystemDB(varSystemDB.bstrVal));
}
```

### <a name="setting-the-default-user-and-password"></a>既定のユーザーとパスワードの設定

システムデータベースの既定のユーザーとパスワードを設定するには、次の関数を使用します。

```cpp
void SetDefaultUser(CString& strUserName,
    CString& strPassword)
{
    COleVariant varUserName(strUserName, VT_BSTRT);
    COleVariant varPassword(strPassword, VT_BSTRT);

    DAODBEngine* pDBEngine = AfxDaoGetEngine();
    ASSERT(pDBEngine != NULL);

    // Set default user:
    DAO_CHECK(pDBEngine->put_DefaultUser(varUserName.bstrVal));

    // Set default password:
    DAO_CHECK(pDBEngine->put_DefaultPassword(varPassword.bstrVal));
}
```

### <a name="changing-a-users-password"></a>ユーザーのパスワードを変更する

ユーザーのパスワードを変更するには、次の関数を使用します。

```cpp
void ChangePassword(CString &strUserName,
    CString &strOldPassword,
    CString &strNewPassword)
{
    // Create (open) a workspace
    CDaoWorkspace wsp;
    CString strWspName = _T("Temp Workspace");

    wsp.Create(strWspName, strUserName, strOldPassword);
    wsp.Append();

    // Determine how many objects there are *// in the Users collection
    short nUserCount;
    short nCurrentUser;
    DAOUser *pUser = NULL;
    DAOUsers *pUsers = NULL;

    // Side-effect is implicit OLE AddRef()
    // on DAOUser object:
    DAO_CHECK(wsp.m_pDAOWorkspace->get_Users(&pUsers));

    // Side-effect is implicit OLE AddRef()
    // on DAOUsers object
    DAO_CHECK(pUsers->getcount(&nUserCount));

    // Traverse through the list of users
    // and change password for the userid
    // used to create/open the workspace
    for(nCurrentUser = 0; nCurrentUser <nUserCount; nCurrentUser++)
    {
        COleVariant varIndex(nCurrentUser, VT_I2);
        COleVariant varName;

        // Retrieve information for user nCurrentUser
        DAO_CHECK(pUsers->get_Item(varIndex, &pUser));

        // Retrieve name for user nCurrentUser
        DAO_CHECK(pUser->get_Name(&V_BSTR(&varName)));

        CString strTemp = V_BSTRT(&varName);

        // If there is a match, change the password
        if (strTemp == strUserName)
        {
            COleVariant varOldPwd(strOldPassword, VT_BSTRT);
            COleVariant varNewPwd(strNewPassword, VT_BSTRT);

            DAO_CHECK(pUser->NewPassword(V_BSTR(&varOldPwd),
                V_BSTR(&varNewPwd)));

            TRACE("\t Password is changed\n");
        }
    }
    // Clean up: decrement the usage count
    // on the OLE objects
    pUser->Release();
    pUsers->Release();
    wsp.Close();
}
```

### <a name="changing-the-password-of-an-mdb-file"></a>のパスワードを変更します。MDB ファイル

のパスワードを変更します。MDB ファイルで、次の関数を使用します。

```cpp
void SetDBPassword(LPCTSTR pDB,
    LPCTSTR pszOldPassword,
    LPCTSTR pszNewPassword)
{
    CDaoDatabase db;
    CString strConnect(_T(";pwd="));

    // the database must be opened as exclusive
    // to set a password
    db.Open(pDB, TRUE, FALSE, strConnect + pszOldPassword);

    COleVariant NewPassword(pszNewPassword, VT_BSTRT),
                OldPassword(pszOldPassword, VT_BSTRT);

    DAO_CHECK(db.m_pDAODatabase->NewPassword(V_BSTR(&OldPassword),
        V_BSTR(&NewPassword)));

    db.Close();
}
```

## <a name="see-also"></a>参照

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
