---
title: CDaoWorkspace クラス
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspace
- AFXDAO/CDaoWorkspace
- AFXDAO/CDaoWorkspace::CDaoWorkspace
- AFXDAO/CDaoWorkspace::Append
- AFXDAO/CDaoWorkspace::BeginTrans
- AFXDAO/CDaoWorkspace::Close
- AFXDAO/CDaoWorkspace::CommitTrans
- AFXDAO/CDaoWorkspace::CompactDatabase
- AFXDAO/CDaoWorkspace::Create
- AFXDAO/CDaoWorkspace::GetDatabaseCount
- AFXDAO/CDaoWorkspace::GetDatabaseInfo
- AFXDAO/CDaoWorkspace::GetIniPath
- AFXDAO/CDaoWorkspace::GetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::GetLoginTimeout
- AFXDAO/CDaoWorkspace::GetName
- AFXDAO/CDaoWorkspace::GetUserName
- AFXDAO/CDaoWorkspace::GetVersion
- AFXDAO/CDaoWorkspace::GetWorkspaceCount
- AFXDAO/CDaoWorkspace::GetWorkspaceInfo
- AFXDAO/CDaoWorkspace::Idle
- AFXDAO/CDaoWorkspace::IsOpen
- AFXDAO/CDaoWorkspace::Open
- AFXDAO/CDaoWorkspace::RepairDatabase
- AFXDAO/CDaoWorkspace::Rollback
- AFXDAO/CDaoWorkspace::SetDefaultPassword
- AFXDAO/CDaoWorkspace::SetDefaultUser
- AFXDAO/CDaoWorkspace::SetIniPath
- AFXDAO/CDaoWorkspace::SetIsolateODBCTrans
- AFXDAO/CDaoWorkspace::SetLoginTimeout
- AFXDAO/CDaoWorkspace::m_pDAOWorkspace
helpviewer_keywords:
- CDaoWorkspace [MFC], CDaoWorkspace
- CDaoWorkspace [MFC], Append
- CDaoWorkspace [MFC], BeginTrans
- CDaoWorkspace [MFC], Close
- CDaoWorkspace [MFC], CommitTrans
- CDaoWorkspace [MFC], CompactDatabase
- CDaoWorkspace [MFC], Create
- CDaoWorkspace [MFC], GetDatabaseCount
- CDaoWorkspace [MFC], GetDatabaseInfo
- CDaoWorkspace [MFC], GetIniPath
- CDaoWorkspace [MFC], GetIsolateODBCTrans
- CDaoWorkspace [MFC], GetLoginTimeout
- CDaoWorkspace [MFC], GetName
- CDaoWorkspace [MFC], GetUserName
- CDaoWorkspace [MFC], GetVersion
- CDaoWorkspace [MFC], GetWorkspaceCount
- CDaoWorkspace [MFC], GetWorkspaceInfo
- CDaoWorkspace [MFC], Idle
- CDaoWorkspace [MFC], IsOpen
- CDaoWorkspace [MFC], Open
- CDaoWorkspace [MFC], RepairDatabase
- CDaoWorkspace [MFC], Rollback
- CDaoWorkspace [MFC], SetDefaultPassword
- CDaoWorkspace [MFC], SetDefaultUser
- CDaoWorkspace [MFC], SetIniPath
- CDaoWorkspace [MFC], SetIsolateODBCTrans
- CDaoWorkspace [MFC], SetLoginTimeout
- CDaoWorkspace [MFC], m_pDAOWorkspace
ms.assetid: 64f60de6-4df1-4d4a-a65b-c489b5257d52
ms.openlocfilehash: c1d235035cee9342c8c54c7aaa4e05a96d5a37e3
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303480"
---
# <a name="cdaoworkspace-class"></a>CDaoWorkspace クラス

シングル ユーザーによる名前付きの、パスワードで保護されたデータベース セッションのログインからログオフまでを管理します。 DAO は Office 2013 でサポートされています。 DAO 3.6 は最終バージョンであり、互換性のために残されているものと見なされます。

## <a name="syntax"></a>構文

```
class CDaoWorkspace : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[CDaoWorkspace::CDaoWorkspace](#cdaoworkspace)|ワークスペースオブジェクトを構築します。 その後、`Create` または `Open`を呼び出します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[CDaoWorkspace:: Append](#append)|新しく作成されたワークスペースをデータベースエンジンのワークスペースコレクションに追加します。|
|[CDaoWorkspace:: BeginTrans](#begintrans)|新しいトランザクションを開始します。これは、ワークスペースで開いているすべてのデータベースに適用されます。|
|[CDaoWorkspace:: Close](#close)|ワークスペースとそれに含まれるすべてのオブジェクトを閉じます。 保留中のトランザクションはロールバックされます。|
|[CDaoWorkspace:: CommitTrans](#committrans)|現在のトランザクションを完了し、変更を保存します。|
|[CDaoWorkspace::CompactDatabase](#compactdatabase)|データベースを圧縮 (または複製) します。|
|[CDaoWorkspace:: Create](#create)|新しい DAO ワークスペースオブジェクトを作成します。|
|[CDaoWorkspace:: GetDatabaseCount](#getdatabasecount)|ワークスペースの Databases コレクションに含まれる DAO データベースオブジェクトの数を返します。|
|[CDaoWorkspace:: GetDatabaseInfo](#getdatabaseinfo)|ワークスペースの Databases コレクションで定義されている、指定された DAO データベースに関する情報を返します。|
|[CDaoWorkspace::GetIniPath](#getinipath)|Windows レジストリの Microsoft Jet データベースエンジンの初期化設定の場所を返します。|
|[CDaoWorkspace:: Getiを実行します。](#getisolateodbctrans)|データソースへの複数の接続を使用して、同じ ODBC データソースを含む複数のトランザクションが分離されているかどうかを示す値を返します。|
|[CDaoWorkspace:: GetLoginTimeout](#getlogintimeout)|ユーザーが ODBC データベースにログインしようとしたときにエラーが発生するまでの秒数を返します。|
|[CDaoWorkspace:: GetName](#getname)|ワークスペースオブジェクトのユーザー定義名を返します。|
|[CDaoWorkspace:: GetUserName](#getusername)|ワークスペースの作成時に指定されたユーザー名を返します。 これは、ワークスペースの所有者の名前です。|
|[CDaoWorkspace:: GetVersion](#getversion)|ワークスペースに関連付けられているデータベースエンジンのバージョンを含む文字列を返します。|
|[CDaoWorkspace::GetWorkspaceCount](#getworkspacecount)|データベースエンジンのワークスペースコレクション内の DAO ワークスペースオブジェクトの数を返します。|
|[CDaoWorkspace::GetWorkspaceInfo](#getworkspaceinfo)|データベースエンジンのワークスペースコレクションで定義されている、指定された DAO ワークスペースに関する情報を返します。|
|[CDaoWorkspace:: Idle](#idle)|データベースエンジンがバックグラウンドタスクを実行できるようにします。|
|[CDaoWorkspace:: IsOpen](#isopen)|ワークスペースが開いている場合は0以外の値を返します。|
|[CDaoWorkspace:: Open](#open)|DAO の既定のワークスペースに関連付けられているワークスペースオブジェクトを明示的に開きます。|
|[CDaoWorkspace::RepairDatabase](#repairdatabase)|破損したデータベースの修復を試みます。|
|[CDaoWorkspace:: Rollback](#rollback)|現在のトランザクションを終了します。変更は保存されません。|
|[CDaoWorkspace:: SetDefaultPassword](#setdefaultpassword)|特定のパスワードを指定せずにワークスペースオブジェクトを作成するときに、データベースエンジンが使用するパスワードを設定します。|
|[CDaoWorkspace:: SetDefaultUser](#setdefaultuser)|特定のユーザー名を指定せずにワークスペースオブジェクトを作成するときに、データベースエンジンが使用するユーザー名を設定します。|
|[CDaoWorkspace::SetIniPath](#setinipath)|Windows レジストリの Microsoft Jet データベースエンジンの初期化設定の場所を設定します。|
|[CDaoWorkspace:: Setiが Ateodbctrans](#setisolateodbctrans)|データソースへの複数の接続を強制することによって、同じ ODBC データソースを含む複数のトランザクションを分離するかどうかを指定します。|
|[CDaoWorkspace:: SetLoginTimeout](#setlogintimeout)|ユーザーが ODBC データソースにログインしようとしたときにエラーが発生するまでの秒数を設定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|Name|説明|
|----------|-----------------|
|[CDaoWorkspace:: m_pDAOWorkspace](#m_pdaoworkspace)|基になる DAO ワークスペースオブジェクトを指します。|

## <a name="remarks"></a>コメント

ほとんどの場合、複数のワークスペースは必要ありません。また、明示的なワークスペースオブジェクトを作成する必要はありません。データベースとレコードセットオブジェクトを開くと、DAO の既定のワークスペースが使用されます。 ただし、必要に応じて、追加のワークスペースオブジェクトを作成することによって、一度に複数のセッションを実行できます。 各ワークスペースオブジェクトには、独自のデータベースコレクション内の複数の開いているデータベースオブジェクトを含めることができます。 MFC では、ワークスペースは主にトランザクションマネージャーであり、開いているデータベースのセットをすべて同じ "トランザクション空間" で指定します。

> [!NOTE]
>  DAO データベースクラスは、Open Database Connectivity (ODBC) に基づく MFC データベースクラスとは異なります。 すべての DAO データベースクラス名には、"CDao" プレフィックスが付いています。 一般に、DAO に基づく MFC クラスは、ODBC に基づく MFC クラスよりも多くの機能を備えています。 DAO ベースのクラスは、ODBC ドライバーを含む Microsoft Jet データベースエンジンを介してデータにアクセスします。 また、DAO を直接呼び出すことなく、データベースの作成やテーブルやフィールドの追加など、データ定義言語 (DDL) 操作もサポートされています。

## <a name="capabilities"></a>機能

クラス `CDaoWorkspace` には、次のものがあります。

- 必要に応じて、データベースエンジンを初期化することによって作成された既定のワークスペースへの明示的なアクセス。 通常、DAO の既定のワークスペースは、データベースおよびレコードセットオブジェクトを作成することによって暗黙的に使用します。

- ワークスペースで開いているすべてのデータベースにトランザクションが適用されるトランザクション領域。 追加のワークスペースを作成して、個別のトランザクション領域を管理することができます。

- 基になる Microsoft Jet データベースエンジンの多くのプロパティに対するインターフェイス (静的メンバー関数を参照)。 ワークスペースを開いたり作成したり、開いたり作成したりする前に静的メンバー関数を呼び出すと、データベースエンジンが初期化されます。

- データベースエンジンのワークスペースコレクションにアクセスします。このコレクションには、追加されたすべてのアクティブなワークスペースが格納されます。 また、ワークスペースをコレクションに追加せずに作成および操作することもできます。

## <a name="security"></a>セキュリティ

MFC は、セキュリティ制御に使用される DAO のユーザーとグループのコレクションを実装していません。 DAO のこれらの側面が必要な場合は、DAO インターフェイスを直接呼び出すことによって自分でプログラミングする必要があります。 詳細については、「[テクニカルノート 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)」を参照してください。

## <a name="usage"></a>使用法

クラス `CDaoWorkspace` を使用すると、次のことができます。

- 既定のワークスペースを明示的に開きます。

   通常、既定のワークスペースは暗黙的に使用します。これは、新しい[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)オブジェクトまたは[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトを開くときに使用されます。 ただし、データベースエンジンのプロパティやワークスペースコレクションにアクセスするなど、明示的にアクセスする必要がある場合もあります。 下の「既定のワークスペースの暗黙的な使用」を参照してください。

- 新しいワークスペースを作成します。 ワークスペースコレクションに追加する場合は、 [Append](#append)を呼び出します。

- ワークスペースコレクション内の既存のワークスペースを開きます。

ワークスペースコレクションにまだ存在しない新しいワークスペースを作成する方法については、「 [Create](#create) member 関数」を参照してください。 ワークスペースオブジェクトは、database engine セッション間で保持されることはありません。 アプリケーションが MFC と静的にリンクしている場合は、アプリケーションを終了してデータベースエンジンを初期化前します。 アプリケーションが MFC と動的にリンクする場合、データベースエンジンは、MFC DLL がアンロードされるときに初期化されません。

既定のワークスペースを明示的に開くか、ワークスペースコレクション内の既存のワークスペースを開くと、 [Open](#open)メンバー関数の下に記述されます。

[Close](#close)メンバー関数を使用してワークスペースを閉じ、ワークスペースセッションを終了します。 まだ閉じていないすべてのデータベースを閉じる `Close`、コミットされていないトランザクションをロールバックします。

## <a name="transactions"></a>トランザクション

DAO は、ワークスペースレベルでトランザクションを管理します。このため、複数の開いているデータベースを持つワークスペース上のトランザクションは、すべてのデータベースに適用されます。 たとえば、2つのデータベースにコミットされていない更新プログラムがあり、 [CommitTrans](#committrans)を呼び出すと、すべての更新がコミットされます。 1つのデータベースにトランザクションを制限する場合は、そのデータベース用に別のワークスペースオブジェクトが必要です。

## <a name="implicit-use-of-the-default-workspace"></a>既定のワークスペースの暗黙的な使用

MFC では、次のような状況では、DAO の既定のワークスペースを暗黙的に使用します。

- 新しい `CDaoDatabase` オブジェクトを作成し、既存の `CDaoWorkspace` オブジェクトを使用しない場合は、DAO の既定のワークスペースに対応する一時ワークスペースオブジェクトが MFC によって作成されます。 複数のデータベースに対してこれを行う場合は、すべてのデータベースオブジェクトが既定のワークスペースに関連付けられます。 データベースのワークスペースにアクセスするには、`CDaoDatabase` データメンバーを使用します。

- 同様に、`CDaoDatabase` オブジェクトへのポインターを指定せずに `CDaoRecordset` オブジェクトを作成した場合、MFC は一時データベースオブジェクトを作成し、拡張子によって一時ワークスペースオブジェクトを作成します。 `CDaoRecordset` データメンバーを使用して、レコードセットのデータベース、およびそのワークスペースに間接的にアクセスできます。

## <a name="other-operations"></a>その他の操作

破損したデータベースの修復やデータベースの圧縮など、その他のデータベース操作も用意されています。

DAO の直接呼び出しと DAO セキュリティの詳細については、「[テクニカルノート 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDaoWorkspace`

## <a name="requirements"></a>要件

**ヘッダー:** afxdao

##  <a name="append"></a>CDaoWorkspace:: Append

[Create](#create)を呼び出した後に、このメンバー関数を呼び出します。

```
virtual void Append();
```

### <a name="remarks"></a>コメント

`Append`、新しく作成されたワークスペースオブジェクトをデータベースエンジンのワークスペースコレクションに追加します。 ワークスペースはデータベースエンジンセッション間で保持されません。ディスク上ではなくメモリにのみ格納されます。 ワークスペースを追加する必要はありません。そうでない場合は、引き続き使用できます。

追加されたワークスペースは、 [Close](#close)メンバー関数を呼び出すまでは、アクティブ状態、オープン状態のワークスペースコレクションに残ります。

関連情報については、DAO ヘルプのトピック「Append メソッド」を参照してください。

##  <a name="begintrans"></a>CDaoWorkspace:: BeginTrans

トランザクションを開始するには、このメンバー関数を呼び出します。

```
void BeginTrans();
```

### <a name="remarks"></a>コメント

`BeginTrans`を呼び出した後、データまたはデータベース構造に対して行った更新は、トランザクションをコミットするときに有効になります。 ワークスペースは1つのトランザクション空間を定義するため、トランザクションはワークスペース内の開いているすべてのデータベースに適用されます。 トランザクションを完了するには、次の2つの方法があります。

- [CommitTrans](#committrans)メンバー関数を呼び出して、トランザクションをコミットし、変更をデータソースに保存します。

- または、 [Rollback](#rollback)メンバー関数を呼び出して、トランザクションをキャンセルします。

トランザクションが保留中の間、ワークスペースオブジェクトまたはデータベースオブジェクトを閉じると、保留中のすべてのトランザクションがロールバックされます。

ある ODBC データソースのトランザクションを、別の ODBC データソースのデータソースから分離する必要がある場合は、 [Setiの Ateodbctrans](#setisolateodbctrans)メンバー関数を参照してください。

##  <a name="cdaoworkspace"></a>CDaoWorkspace::CDaoWorkspace

`CDaoWorkspace` オブジェクトを構築します。

```
CDaoWorkspace();
```

### <a name="remarks"></a>コメント

C++オブジェクトを構築した後、次の2つのオプションがあります。

- オブジェクトの[open](#open)メンバー関数を呼び出して、既定のワークスペースを開くか、ワークスペースコレクション内の既存のオブジェクトを開きます。

- または、オブジェクトの[create](#create) member 関数を呼び出して、新しい DAO ワークスペースオブジェクトを作成します。 これにより、新しいワークスペースセッションが明示的に開始されます。これは、`CDaoWorkspace` オブジェクトを介して参照できます。 `Create`を呼び出した後、データベースエンジンのワークスペースコレクションにワークスペースを追加する場合は、 [Append](#append)を呼び出すことができます。

`CDaoWorkspace` オブジェクトを明示的に作成する必要がある場合の詳細については、「 [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)のクラスの概要」を参照してください。 通常は、ワークスペースを指定せずに[CDaoDatabase](../../mfc/reference/cdaodatabase-class.md)オブジェクトを開いたとき、またはデータベースオブジェクトを指定せずに[CDaoRecordset](../../mfc/reference/cdaorecordset-class.md)オブジェクトを開いたときに、暗黙的に作成されたワークスペースを使用します。 この方法で作成された MFC DAO オブジェクトは、DAO の既定のワークスペースを使用します。このワークスペースは、一度作成されて再利用されます。

ワークスペースとそれに含まれるオブジェクトを解放するには、ワークスペースオブジェクトの[Close](#close)メンバー関数を呼び出します。

##  <a name="close"></a>CDaoWorkspace:: Close

このメンバー関数を呼び出して、ワークスペースオブジェクトを閉じます。

```
virtual void Close();
```

### <a name="remarks"></a>コメント

開いているワークスペースオブジェクトを閉じると、基になる DAO オブジェクトが解放されます。ワークスペースがワークスペースコレクションのメンバーである場合は、そのオブジェクトをコレクションから削除します。 `Close` を呼び出すことをお勧めします。

> [!CAUTION]
>  ワークスペースオブジェクトを閉じると、ワークスペース内の開いているデータベースがすべて閉じられます。 その結果、閉じられているデータベースでもレコードセットが開かれ、保留中の編集や更新がロールバックされます。 関連情報については、「 [CDaoDatabase:: close](../../mfc/reference/cdaodatabase-class.md#close)、 [CDaoRecordset:: close](../../mfc/reference/cdaorecordset-class.md#close)、 [CDaoTableDef:: close](../../mfc/reference/cdaotabledef-class.md#close)、および[CDaoQueryDef:: close](../../mfc/reference/cdaoquerydef-class.md#close)メンバー関数」を参照してください。

ワークスペースオブジェクトは永続的ではありません。それらの参照が存在する場合にのみ存在します。 これは、データベースエンジンセッションが終了したときに、ワークスペースとそのデータベースコレクションが保持されないことを意味します。 もう一度ワークスペースとデータベースを開いて、次のセッション用に再作成する必要があります。

関連情報については、DAO ヘルプの「Close メソッド」を参照してください。

##  <a name="committrans"></a>CDaoWorkspace:: CommitTrans

トランザクションをコミットするには、このメンバー関数を呼び出します。編集や更新のグループをワークスペース内の1つ以上のデータベースに保存します。

```
void CommitTrans();
```

### <a name="remarks"></a>コメント

トランザクションは、データベースのデータまたはその構造に対する一連の変更で構成されます。これは、 [BeginTrans](#begintrans)の呼び出しから始まります。 トランザクションを完了したら、 [Rollback](#rollback)を使用してトランザクションをコミットするか、ロールバックする (変更をキャンセルする) 必要があります。 既定では、トランザクションを使用しない場合、レコードの更新はすぐにコミットされます。 `BeginTrans` を呼び出すと、`CommitTrans`を呼び出すまで更新のコミットメントが遅延されます。

> [!CAUTION]
>  1つのワークスペース内では、トランザクションは常にワークスペースに対してグローバルであり、1つのデータベースまたはレコードセットに限定されません。 ワークスペーストランザクション内の複数のデータベースまたはレコードセットに対して操作を実行すると、`CommitTrans` はすべての保留中の更新をコミットし、`Rollback` それらのデータベースおよびレコードセットに対するすべての操作を復元します。

保留中のトランザクションを含むデータベースまたはワークスペースを閉じると、すべてのトランザクションがロールバックされます。

> [!NOTE]
>  これは、2フェーズコミットメカニズムではありません。 1つの更新がコミットに失敗した場合でも、他の更新はコミットされます。

##  <a name="compactdatabase"></a>CDaoWorkspace::CompactDatabase

このメンバー関数を呼び出して、指定した Microsoft Jet () を圧縮します。MDB) データベース。

```
static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale = dbLangGeneral,
    int nOptions = 0);

static void PASCAL CompactDatabase(
    LPCTSTR lpszSrcName,
    LPCTSTR lpszDestName,
    LPCTSTR lpszLocale,
    int nOptions,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>パラメーター

*lpszSrcName*<br/>
既存の閉じているデータベースの名前。 "C:\\\MYDB." のように、完全なパスとファイル名を指定できます。MDB "。 ファイル名に拡張子がある場合は、それを指定する必要があります。 ネットワークで汎用名前付け規則 (UNC) がサポートされている場合は、ネットワークパスを指定することもできます。たとえば、"\\\\\\\MYSHARE\\\MYDIR\\\\\MYDB.MDB "。 パス文字列には二重の円記号が必要です。これは、 C++ "\\" がエスケープ文字であるためです。

*lpszDestName*<br/>
作成する最適化されたデータベースの完全パスです。 また、 *Lpszsrcname*と同じようにネットワークパスを指定することもできます。 *Lpszdestname*引数を使用して、同じデータベースファイルを*lpszsrcname*として指定することはできません。

*lpszPassword*<br/>
パスワードで保護されたデータベースを圧縮するときに使用するパスワードです。 パスワードを受け取る `CompactDatabase` のバージョンを使用する場合は、すべてのパラメーターを指定する必要があることに注意してください。 また、これは connect パラメーターであるため、次のように特殊な書式設定が必要です。PWD = *Lpszpassword*。 たとえば、次のようになります。PWD = "ハッピー"。 (先頭にセミコロンが必要です)。

*lpszLocale*<br/>
*Lpszdestname*を作成するための照合順序を指定するために使用される文字列式。 `dbLangGeneral` の既定値 (下記参照) を受け入れてこの引数を省略した場合、新しいデータベースのロケールは古いデータベースのロケールと同じになります。 指定できる値は次のとおりです。

- `dbLangGeneral` 英語、ドイツ語、フランス語、ポルトガル語、イタリア語、および現代のスペイン語

- `dbLangArabic` アラビア語

- `dbLangCyrillic` ロシア語

- `dbLangCzech` チェコ語

- `dbLangDutch` オランダ語

- `dbLangGreek` ギリシャ語

- `dbLangHebrew` ヘブライ語

- `dbLangHungarian` ハンガリー語

- `dbLangIcelandic` アイスランド語

- 北欧言語 `dbLangNordic` (Microsoft Jet データベースエンジンバージョン1.0 のみ)

- `dbLangNorwdan` ノルウェー語とデンマーク語

- `dbLangPolish` ポーランド語

- `dbLangSpanish` 従来のスペイン語

- `dbLangSwedfin` スウェーデン語およびフィンランド語

- `dbLangTurkish` トルコ語

*nOptions*<br/>
ターゲットデータベース ( *Lpszdestname*) に対して1つ以上のオプションを示します。 既定値を受け入れてこの引数を省略した場合、 *Lpszdestname*の暗号化と同じバージョンが*lpszsrcname*と同じになります。 `dbEncrypt` または `dbDecrypt` オプションは、ビットごとの OR 演算子を使用して、いずれかのバージョンオプションと組み合わせることができます。 データベースエンジンのバージョンではなく、データベース形式を指定できる値は次のとおりです。

- 圧縮中にデータベースを暗号化 `dbEncrypt` ます。

- 圧縮中にデータベースの暗号化を解除 `dbDecrypt` ます。

- 圧縮中に Microsoft Jet データベースエンジンバージョン1.0 を使用するデータベースを作成 `dbVersion10` ます。

- 圧縮中に Microsoft Jet データベースエンジンバージョン1.1 を使用するデータベースを作成 `dbVersion11` ます。

- 圧縮中に Microsoft Jet データベースエンジンバージョン2.0 を使用するデータベースを作成 `dbVersion20` ます。

- 圧縮中に Microsoft Jet データベースエンジンバージョン3.0 を使用するデータベースを作成 `dbVersion30` ます。

`dbEncrypt` または `dbDecrypt` を使用して、データベースを圧縮するときに暗号化または復号化するかどうかを指定できます。 暗号化定数を省略した場合、または `dbDecrypt` と `dbEncrypt`の両方を含めた場合、 *Lpszdestname*の暗号化は*lpszsrcname*と同じになります。 [オプション] 引数のいずれかのバージョン定数を使用すると、圧縮されたデータベースのデータ形式のバージョンを指定できます。 この定数は、 *Lpszdestname*のデータ形式のバージョンにのみ影響します。 指定できるバージョン定数は1つだけです。 バージョン定数を省略した場合、 *Lpszdestname*のバージョンは*lpszsrcname*と同じになります。 *Lpszdestname*は、 *lpszsrcname*と同じかそれ以降のバージョンにのみ圧縮できます。

> [!CAUTION]
>  データベースが暗号化されていない場合は、ユーザーまたはパスワードのセキュリティを実装している場合でも、データベースを構成するバイナリディスクファイルを直接読み取ることができます。

### <a name="remarks"></a>コメント

データベース内のデータを変更すると、データベースファイルが断片化し、必要以上のディスク領域を使用できるようになります。 データベースファイルを最適化するには、定期的にデータベースを圧縮する必要があります。 通常、圧縮されたデータベースは小さくなります。 また、データベースをコピーして圧縮するときに、照合順序、暗号化、またはデータ形式のバージョンを変更することもできます。

> [!CAUTION]
>  `CompactDatabase` メンバー関数は、完全な Microsoft Access データベースをあるバージョンから別のバージョンに正しく変換しません。 データ形式のみが変換されます。 フォームやレポートなど、Microsoft Access によって定義されたオブジェクトは変換されません。 ただし、データは正しく変換されます。

> [!TIP]
>  また、`CompactDatabase` を使用してデータベースファイルをコピーすることもできます。

データベースの圧縮の詳細については、DAO ヘルプの「CompactDatabase メソッド」を参照してください。

##  <a name="create"></a>CDaoWorkspace:: Create

このメンバー関数を呼び出して、新しい DAO ワークスペースオブジェクトを作成し、それを MFC `CDaoWorkspace` オブジェクトに関連付けます。

```
virtual void Create(
    LPCTSTR lpszName,
    LPCTSTR lpszUserName,
    LPCTSTR lpszPassword);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
新しいワークスペースオブジェクトに一意の名前を付けた最大14文字の文字列。 名前を指定する必要があります。 関連情報については、DAO ヘルプの「Name プロパティ」を参照してください。

*lpszUserName*<br/>
ワークスペースの所有者のユーザー名。 要件については、 [setdefaultuser](#setdefaultuser)メンバー関数の*lpszdefaultuser*パラメーターを参照してください。 関連情報については、DAO ヘルプの「UserName プロパティ」を参照してください。

*lpszPassword*<br/>
新しいワークスペースオブジェクトのパスワードです。 パスワードの長さは最大14文字で、ASCII 0 (null) 以外の任意の文字を含めることができます。 パスワードでは大文字と小文字が区別されます。 関連情報については、DAO ヘルプの「Password プロパティ」を参照してください。

### <a name="remarks"></a>コメント

全体的な作成プロセスは次のとおりです。

1. [CDaoWorkspace](#cdaoworkspace)オブジェクトを構築します。

1. オブジェクトの `Create` メンバー関数を呼び出して、基になる DAO ワークスペースを作成します。 ワークスペース名を指定する必要があります。

1. データベースエンジンのワークスペースコレクションにワークスペースを追加する場合は、必要に応じて[Append](#append)を呼び出します。 追加せずに、ワークスペースを操作できます。

`Create` を呼び出すと、ワークスペースオブジェクトはオープン状態になり、使用できるようになります。 `Create`後に `Open` を呼び出すことはできません。 ワークスペースコレクションにワークスペースが既に存在する場合、`Create` は呼び出されません。 アプリケーションに対してデータベースエンジンがまだ初期化されていない場合は、`Create` によって初期化されます。

##  <a name="getdatabasecount"></a>CDaoWorkspace:: GetDatabaseCount

このメンバー関数を呼び出して、ワークスペースの Databases コレクション内の DAO データベースオブジェクトの数 (ワークスペース内の開いているデータベースの数) を取得します。

```
short GetDatabaseCount();
```

### <a name="return-value"></a>戻り値

ワークスペース内の開いているデータベースの数。

### <a name="remarks"></a>コメント

`GetDatabaseCount` は、ワークスペースの Databases コレクション内で定義されているすべてのデータベースをループ処理する必要がある場合に便利です。 コレクション内の特定のデータベースに関する情報を取得するには、「 [Getdatabaseinfo](#getdatabaseinfo)」を参照してください。 一般的な使用方法としては、開いているデータベースの数に対して `GetDatabaseCount` を呼び出し、次にその番号をループインデックスとして使用して `GetDatabaseInfo`を繰り返し呼び出します。

##  <a name="getdatabaseinfo"></a>CDaoWorkspace:: GetDatabaseInfo

このメンバー関数を呼び出して、ワークスペースで開いているデータベースに関するさまざまな種類の情報を取得します。

```
void GetDatabaseInfo(
    int nIndex,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetDatabaseInfo(
    LPCTSTR lpszName,
    CDaoDatabaseInfo& dbinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
インデックスによる検索のために、ワークスペースの Databases コレクション内にあるデータベースオブジェクトの0から始まるインデックスです。

*dbinfo*<br/>
要求された情報を返す[CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)オブジェクトへの参照。

*オプション*<br/>
取得するデータベースに関する情報を指定するオプション。 使用可能なオプションは、関数が返す原因と共にここに表示されます。

- AFX_DAO_PRIMARY_INFO (既定) 名前、更新可能、トランザクション

- プライマリ情報に加えて、バージョン、照合順序、クエリタイムアウトを AFX_DAO_SECONDARY_INFO します。

- プライマリとセカンダリの情報に加えて、接続 AFX_DAO_ALL_INFO

*lpszName*<br/>
名前で参照するデータベースオブジェクトの名前。 名前は、最大14文字の文字列で、新しいワークスペースオブジェクトに一意の名前を付けます。

### <a name="remarks"></a>コメント

関数の1つのバージョンでは、インデックスを使用してデータベースを検索できます。 もう1つのバージョンでは、データベースを名前で検索できます。

*Dbinfo*で返される情報の説明については、 [CDaoDatabaseInfo](../../mfc/reference/cdaodatabaseinfo-structure.md)構造体を参照してください。 この構造体には、前に説明した情報の項目に対応するメンバーが含まれ*ています。* 1つのレベルで情報を要求すると、以前のレベルについても情報が得られます。

##  <a name="getinipath"></a>CDaoWorkspace::GetIniPath

Windows レジストリで Microsoft Jet データベースエンジンの初期化設定の場所を取得するには、このメンバー関数を呼び出します。

```
static CString PASCAL GetIniPath();
```

### <a name="return-value"></a>戻り値

レジストリの場所を格納している[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>コメント

この場所を使用して、データベースエンジンの設定に関する情報を取得できます。 返される情報は、実際にはレジストリサブキーの名前です。

関連情報については、DAO ヘルプの「IniPath プロパティ」および「データアクセスのための Windows レジストリ設定のカスタマイズ」を参照してください。

##  <a name="getisolateodbctrans"></a>CDaoWorkspace:: Getiを実行します。

このメンバー関数を呼び出して、ワークスペースの DAO IsolateODBCTrans プロパティの現在の値を取得します。

```
BOOL GetIsolateODBCTrans();
```

### <a name="return-value"></a>戻り値

ODBC トランザクションが分離されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>コメント

場合によっては、同じ ODBC データベースで複数の同時トランザクションが保留されている必要があります。 これを行うには、トランザクションごとに個別のワークスペースを開く必要があります。 各ワークスペースはデータベースに対して独自の ODBC 接続を持つことができるので、システムのパフォーマンスが低下することに注意してください。 トランザクションの分離は通常必要ではないため、同じユーザーが開いている複数のワークスペースオブジェクトからの ODBC 接続は、既定で共有されます。

Microsoft SQL Server などの一部の ODBC サーバーでは、単一の接続で同時トランザクションを使用することはできません。 このようなデータベースに対して保留中の複数のトランザクションを同時に実行する必要がある場合は、各ワークスペースの IsolateODBCTrans プロパティを [TRUE] に設定します。 これにより、ワークスペースごとに個別の ODBC 接続が強制的に実行します。

関連情報については、DAO ヘルプの「IsolateODBCTrans プロパティ」を参照してください。

##  <a name="getlogintimeout"></a>CDaoWorkspace:: GetLoginTimeout

このメンバー関数を呼び出して、ワークスペースの DAO LoginTimeout プロパティの現在の値を取得します。

```
static short PASCAL GetLoginTimeout();
```

### <a name="return-value"></a>戻り値

ODBC データベースにログインしようとしたときにエラーが発生するまでの秒数。

### <a name="remarks"></a>コメント

この値は、ODBC データベースにログインしようとしたときにエラーが発生するまでの秒数を表します。 LoginTimeout の既定値は20秒です。 LoginTimeout が0に設定されている場合、タイムアウトは発生せず、データソースとの通信が応答を停止する可能性があります。

Microsoft SQL Server などの ODBC データベースにログインしようとすると、ネットワークエラーが発生したか、サーバーが実行されていないため、接続が失敗することがあります。 既定の20秒間の接続を待機するのではなく、データベースエンジンがエラーを生成するまでの待機時間を指定できます。 サーバーへのログインは、外部サーバーデータベースに対するクエリの実行など、さまざまなイベントの一部として暗黙的に行われます。

関連情報については、DAO ヘルプの「LoginTimeout プロパティ」を参照してください。

##  <a name="getname"></a>CDaoWorkspace:: GetName

このメンバー関数を呼び出して、`CDaoWorkspace` オブジェクトの基になる DAO ワークスペースオブジェクトのユーザー定義名を取得します。

```
CString GetName();
```

### <a name="return-value"></a>戻り値

DAO ワークスペースオブジェクトのユーザー定義名を格納している[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>コメント

名前は、データベースエンジンのワークスペースコレクション内の DAO ワークスペースオブジェクトに名前でアクセスする場合に便利です。

関連情報については、DAO ヘルプの「Name プロパティ」を参照してください。

##  <a name="getusername"></a>CDaoWorkspace:: GetUserName

このメンバー関数を呼び出して、ワークスペースの所有者の名前を取得します。

```
CString GetUserName();
```

### <a name="return-value"></a>戻り値

ワークスペースオブジェクトの所有者を表す[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>コメント

ワークスペースの所有者のアクセス許可を取得または設定するには、直接 DAO を呼び出して Permissions プロパティの設定を確認します。これにより、ユーザーが持つアクセス許可が決まります。 アクセス許可を操作するには、システムが必要です。MDA ファイル。

DAO を直接呼び出す方法については、「[テクニカルノート 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)」を参照してください。 関連情報については、DAO ヘルプの「UserName プロパティ」を参照してください。

##  <a name="getversion"></a>CDaoWorkspace:: GetVersion

このメンバー関数を呼び出して、使用されている Microsoft Jet データベースエンジンのバージョンを確認します。

```
static CString PASCAL GetVersion();
```

### <a name="return-value"></a>戻り値

オブジェクトに関連付けられているデータベースエンジンのバージョンを示す[CString](../../atl-mfc-shared/reference/cstringt-class.md) 。

### <a name="remarks"></a>コメント

返される値は、"major. minor" という形式のバージョン番号を表します。たとえば、"3.0" のようになります。 製品バージョン番号 (3.0 など) は、バージョン番号 (3)、ピリオド、およびリリース番号 (0) で構成されます。

関連情報については、DAO ヘルプの「バージョンプロパティ」を参照してください。

##  <a name="getworkspacecount"></a>CDaoWorkspace::GetWorkspaceCount

このメンバー関数を呼び出して、データベースエンジンのワークスペースコレクション内の DAO ワークスペースオブジェクトの数を取得します。

```
short GetWorkspaceCount();
```

### <a name="return-value"></a>戻り値

ワークスペースコレクション内の開いているワークスペースの数。

### <a name="remarks"></a>コメント

この数には、コレクションに追加されていない開いているワークスペースは含まれません。 `GetWorkspaceCount` は、ワークスペースコレクション内で定義されているすべてのワークスペースをループ処理する必要がある場合に便利です。 コレクション内の特定のワークスペースに関する情報を取得するには、「 [GetWorkspaceInfo](#getworkspaceinfo)」を参照してください。 一般的な使用方法としては、開いているワークスペースの数に対して `GetWorkspaceCount` を呼び出してから、その番号をループインデックスとして使用して `GetWorkspaceInfo`を繰り返し呼び出します。

##  <a name="getworkspaceinfo"></a>CDaoWorkspace::GetWorkspaceInfo

このメンバー関数を呼び出して、セッションで開いているワークスペースに関するさまざまな種類の情報を取得します。

```
void GetWorkspaceInfo(
    int nIndex,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);

void GetWorkspaceInfo(
    LPCTSTR lpszName,
    CDaoWorkspaceInfo& wkspcinfo,
    DWORD dwInfoOptions = AFX_DAO_PRIMARY_INFO);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
インデックスによる検索のために、ワークスペースコレクション内のデータベースオブジェクトの0から始まるインデックス。

*wkspcinfo*<br/>
要求された情報を返す[CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)オブジェクトへの参照。

*オプション*<br/>
取得するワークスペースに関する情報を指定するオプション。 使用可能なオプションは、関数が返す原因と共にここに表示されます。

- AFX_DAO_PRIMARY_INFO (既定) 名

- AFX_DAO_SECONDARY_INFO のプライマリ情報とユーザー名

- プライマリとセカンダリの情報を AFX_DAO_ALL_INFO と、ODBCTrans を分離します。

*lpszName*<br/>
名前で検索するためのワークスペースオブジェクトの名前。 名前は、最大14文字の文字列で、新しいワークスペースオブジェクトに一意の名前を付けます。

### <a name="remarks"></a>コメント

*Wkspcinfo*で返される情報の説明については、 [CDaoWorkspaceInfo](../../mfc/reference/cdaoworkspaceinfo-structure.md)構造体を参照してください。 この構造体には、前に説明した情報の項目に対応するメンバーが含まれ*ています。* 1つのレベルで情報を要求すると、以前のレベルについても情報が得られます。

##  <a name="idle"></a>CDaoWorkspace:: Idle

`Idle` を呼び出して、大量のデータ処理によって、最新ではない可能性があるバックグラウンドタスクを実行する機会をデータベースエンジンに提供します。

```
static void PASCAL Idle(int nAction = dbFreeLocks);
```

### <a name="parameters"></a>パラメーター

*N 操作*<br/>
アイドル処理中に実行するアクション。 現在、有効なアクションは `dbFreeLocks`のみです。

### <a name="remarks"></a>コメント

これは、多くの場合、マルチユーザー、マルチタスク環境では、レコードセット内のすべてのレコードを最新の状態に保つために十分なバックグラウンド処理時間がないためです。

> [!NOTE]
>  バージョン3.0 の Microsoft Jet データベースエンジンで作成されたデータベースでは、`Idle` を呼び出す必要はありません。 `Idle` は、以前のバージョンで作成されたデータベースに対してのみ使用してください。

通常、読み取りロックは削除され、ローカルのダイナセット型の recordset オブジェクトのデータは、他の操作 (マウスの移動を含む) が発生していない場合にのみ更新されます。 `Idle`を定期的に呼び出す場合は、不要な読み取りロックを解除することによって、バックグラウンド処理タスクをキャッチアップする時間をデータベースエンジンに提供します。 `dbFreeLocks` 定数を引数として指定すると、すべての読み取りロックが解放されるまで処理が遅延されます。

このメンバー関数は、アプリケーションの複数のインスタンスが実行されている場合を除き、シングルユーザー環境では必要ありません。 `Idle` メンバー関数では、データベースエンジンによってデータがディスクにフラッシュされ、メモリのロックが解放されるため、マルチユーザー環境でのパフォーマンスが向上する場合があります。 トランザクションの一部を操作することによって、読み取りロックを解除することもできます。

関連情報については、DAO ヘルプの「Idle メソッド」を参照してください。

##  <a name="isopen"></a>CDaoWorkspace:: IsOpen

このメンバー関数を呼び出して、`CDaoWorkspace` オブジェクトが開いているかどうかを確認します。つまり、 [open](#open)または[Create](#create)の呼び出しによって MFC オブジェクトが初期化されているかどうかを判断します。

```
BOOL IsOpen() const;
```

### <a name="return-value"></a>戻り値

ワークスペースオブジェクトが開いている場合は0以外。それ以外の場合は0です。

### <a name="remarks"></a>コメント

オープン状態のワークスペースのメンバー関数を呼び出すことができます。

##  <a name="m_pdaoworkspace"></a>CDaoWorkspace:: m_pDAOWorkspace

基になる DAO ワークスペースオブジェクトへのポインター。

### <a name="remarks"></a>コメント

基になる DAO オブジェクトに直接アクセスする必要がある場合は、このデータメンバーを使用します。 このポインターを使用して、DAO オブジェクトのインターフェイスを呼び出すことができます。

DAO オブジェクトへの直接アクセスの詳細については、「[テクニカルノート 54](../../mfc/tn054-calling-dao-directly-while-using-mfc-dao-classes.md)」を参照してください。

##  <a name="open"></a>CDaoWorkspace:: Open

DAO の既定のワークスペースに関連付けられているワークスペースオブジェクトを明示的に開きます。

```
virtual void Open(LPCTSTR lpszName = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
開く DAO ワークスペースオブジェクトの名前。ワークスペースに一意の名前を付けて、最大14文字の文字列を指定します。 既定値の NULL をそのまま使用して、既定のワークスペースを明示的に開きます。 名前付けの要件については、「[作成](#create)用の*lpszname*パラメーター」を参照してください。 関連情報については、DAO ヘルプの「Name プロパティ」を参照してください。

### <a name="remarks"></a>コメント

`CDaoWorkspace` オブジェクトを構築した後、このメンバー関数を呼び出して、次のいずれかの操作を行います。

- 既定のワークスペースを明示的に開きます。 *Lpszname*に NULL を渡します。

- 名前を指定して、ワークスペースコレクションのメンバーである既存の `CDaoWorkspace` オブジェクトを開きます。 既存のワークスペースオブジェクトの有効な名前を渡してください。

`Open` は、ワークスペースオブジェクトをオープン状態にし、アプリケーションに対してまだ初期化されていない場合はデータベースエンジンも初期化します。

多くの `CDaoWorkspace` メンバー関数は、ワークスペースを開いた後にのみ呼び出すことができますが、データベースエンジンに対して動作する次のメンバー関数はC++ 、オブジェクトの構築後、`Open`の呼び出しの前に使用できます。

||||
|-|-|-|
|[生成](#create)|[GetVersion](#getversion)|[SetDefaultUser](#setdefaultuser)|
|[GetIniPath](#getinipath)|[退席](#idle)|[SetIniPath](#setinipath)|
|[GetLoginTimeout](#getlogintimeout)|[SetDefaultPassword](#setdefaultpassword)|[SetLoginTimeout](#setlogintimeout)|

##  <a name="repairdatabase"></a>CDaoWorkspace::RepairDatabase

Microsoft Jet データベースエンジンにアクセスする破損したデータベースを修復する必要がある場合は、このメンバー関数を呼び出します。

```
static void PASCAL RepairDatabase(LPCTSTR lpszName);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
既存の Microsoft Jet エンジンデータベースファイルのパスとファイル名。 パスを省略した場合は、現在のディレクトリだけが検索されます。 システムで汎用名前付け規則 (UNC) がサポートされている場合は、次のようなネットワークパスを指定することもできます。たとえば、"\\\\\\\\\MYSHARE\\\MYDIR\\\MYDB.MDB "。 パス文字列には二重のC++円記号が必要です。これは、"\\" がエスケープ文字であるためです。

### <a name="remarks"></a>コメント

修復する前に、 *Lpszname*で指定されたデータベースを閉じる必要があります。 マルチユーザー環境では、他のユーザーは、修復中に*Lpszname*を開くことはできません。 *Lpszname*が閉じられていないか、排他的に使用できない場合は、エラーが発生します。

このメンバー関数は、不完全な書き込み操作によって破損している可能性があるとマークされたデータベースの修復を試みます。 これは、Microsoft Jet データベースエンジンを使用しているアプリケーションが、停電またはコンピューターのハードウェアの問題のために予期せず終了した場合に発生する可能性があります。 操作を完了して[Close](../../mfc/reference/cdaodatabase-class.md#close)メンバー関数を呼び出すか、通常の方法でアプリケーションを終了すると、データベースは破損しているとマークされません。

> [!NOTE]
>  データベースを修復した後、 [CompactDatabase](#compactdatabase)メンバー関数を使用してファイルを最適化し、ディスク領域を回復することもお勧めします。

データベースの修復の詳細については、DAO ヘルプの「RepairDatabase メソッド」を参照してください。

##  <a name="rollback"></a>CDaoWorkspace:: Rollback

このメンバー関数を呼び出して、現在のトランザクションを終了し、ワークスペース内のすべてのデータベースをそのトランザクションが開始される前の状態に復元します。

```
void Rollback();
```

### <a name="remarks"></a>コメント

> [!CAUTION]
>  1つのワークスペースオブジェクト内では、トランザクションは常にワークスペースに対してグローバルであり、1つのデータベースまたはレコードセットに限定されません。 ワークスペーストランザクション内の複数のデータベースまたはレコードセットに対して操作を実行する場合、`Rollback` は、これらのすべてのデータベースおよびレコードセットに対するすべての操作を復元します。

保留中のトランザクションを保存またはロールバックせずにワークスペースオブジェクトを閉じると、トランザクションは自動的にロールバックされます。 最初に[BeginTrans](#begintrans)を呼び出さずに[CommitTrans](#committrans)または `Rollback` を呼び出すと、エラーが発生します。

> [!NOTE]
>  トランザクションを開始すると、データベースエンジンは、ワークステーションの TEMP 環境変数で指定されたディレクトリに保持されているファイルにその操作を記録します。 トランザクションログファイルが一時ドライブの使用可能なストレージを使い果たすと、データベースエンジンによって、MFC によって `CDaoException` がスローされます (DAO エラー 2004)。 この時点で、`CommitTrans`を呼び出すと、不確定な操作の数がコミットされますが、残りの未完了の操作は失われ、操作を再起動する必要があります。 `Rollback` を呼び出すと、トランザクションログが解放され、トランザクション内のすべての操作がロールバックされます。

##  <a name="setdefaultpassword"></a>CDaoWorkspace:: SetDefaultPassword

特定のパスワードを指定せずにワークスペースオブジェクトを作成するときにデータベースエンジンが使用する既定のパスワードを設定するには、このメンバー関数を呼び出します。

```
static void PASCAL SetDefaultPassword(LPCTSTR lpszPassword);
```

### <a name="parameters"></a>パラメーター

*lpszPassword*<br/>
既定のパスワードです。 パスワードの長さは最大14文字で、ASCII 0 (null) 以外の任意の文字を含めることができます。 パスワードでは大文字と小文字が区別されます。

### <a name="remarks"></a>コメント

設定した既定のパスワードは、通話後に作成する新しいワークスペースに適用されます。 後続のワークスペースを作成する場合、 [create](#create)呼び出しでパスワードを指定する必要はありません。

このメンバー関数を使用するには:

1. `CDaoWorkspace` オブジェクトを構築しますが、`Create`を呼び出しません。

1. `SetDefaultPassword` を呼び出し、必要に応じて[Setdefaultuser](#setdefaultuser)を呼び出します。

1. パスワードを指定せずに、このワークスペースオブジェクトまたはそれ以降のオブジェクトの `Create` を呼び出します。

既定では、DefaultUser プロパティは "admin" に設定され、Defaultuser プロパティは空の文字列 ("") に設定されます。

セキュリティの詳細については、DAO ヘルプの「Permissions プロパティ」を参照してください。 関連情報については、DAO ヘルプの「DefaultPassword プロパティ」と「Defaultpassword プロパティ」を参照してください。

##  <a name="setdefaultuser"></a>CDaoWorkspace:: SetDefaultUser

特定のユーザー名を指定せずにワークスペースオブジェクトを作成するときに、データベースエンジンが使用する既定のユーザー名を設定するには、このメンバー関数を呼び出します。

```
static void PASCAL SetDefaultUser(LPCTSTR lpszDefaultUser);
```

### <a name="parameters"></a>パラメーター

*lpszDefaultUser*<br/>
既定のユーザー名。 ユーザー名は、長さが 1-20 文字で、アルファベット文字を含めることができます。アクセントが付いている文字、数字、スペース、記号: "(引用符)、/(スラッシュ)、\ (円記号)、\[ \] (角かっこ&#124; )、: (コロン)、(パイプ)、\< (小なり記号)、> (大なり記号)、+ (正符号)、= (等号)、;(セミコロン)、、(コンマ)、(疑問符)、\* (アスタリスク)、先頭のスペース、および制御文字 (ASCII 00 から ASCII 31)。 関連情報については、DAO ヘルプの「UserName プロパティ」を参照してください。

### <a name="remarks"></a>コメント

設定した既定のユーザー名は、の呼び出し後に作成する新しいワークスペースに適用されます。 後続のワークスペースを作成する場合、 [create](#create)呼び出しでユーザー名を指定する必要はありません。

このメンバー関数を使用するには:

1. `CDaoWorkspace` オブジェクトを構築しますが、`Create`を呼び出しません。

1. `SetDefaultUser` を呼び出し、必要に応じて[Setdefaultpassword](#setdefaultpassword)を呼び出します。

1. ユーザー名を指定せずに、このワークスペースオブジェクトまたはそれ以降のオブジェクトの `Create` を呼び出します。

既定では、DefaultUser プロパティは "admin" に設定され、Defaultuser プロパティは空の文字列 ("") に設定されます。

関連情報については、DAO ヘルプの「DefaultUser プロパティ」と「Defaultuser プロパティ」を参照してください。

##  <a name="setinipath"></a>CDaoWorkspace::SetIniPath

Microsoft Jet データベースエンジンの Windows レジストリ設定の場所を指定するには、このメンバー関数を呼び出します。

```
static void PASCAL SetIniPath(LPCTSTR lpszRegistrySubKey);
```

### <a name="parameters"></a>パラメーター

*lpszRegistrySubkey*<br/>
Microsoft Jet データベースエンジン設定の場所またはインストール可能な ISAM データベースに必要なパラメーターの Windows レジストリサブキーの名前を含む文字列。

### <a name="remarks"></a>コメント

特別な設定を指定する必要がある場合にのみ `SetIniPath` を呼び出します。 詳細については、DAO ヘルプの「IniPath プロパティ」を参照してください。

> [!NOTE]
>  アプリケーションのインストール時に、アプリケーションの実行時ではなく `SetIniPath` を呼び出します。 ワークスペース、データベース、またはレコードセットを開く前に `SetIniPath` を呼び出す必要があります。それ以外の場合、MFC は例外をスローします。

このメカニズムを使用すると、ユーザー指定のレジストリ設定を使用してデータベースエンジンを構成できます。 この属性のスコープはアプリケーションに限定されており、アプリケーションを再起動しなくても変更できません。

##  <a name="setisolateodbctrans"></a>CDaoWorkspace:: Setiが Ateodbctrans

このメンバー関数を呼び出して、ワークスペースの DAO IsolateODBCTrans プロパティの値を設定します。

```
void SetIsolateODBCTrans(BOOL bIsolateODBCTrans);
```

### <a name="parameters"></a>パラメーター

*bIsolateODBCTrans*<br/>
ODBC トランザクションの分離を開始する場合は TRUE を渡します。 ODBC トランザクションの分離を停止する場合は、FALSE を渡します。

### <a name="remarks"></a>コメント

場合によっては、同じ ODBC データベースで複数の同時トランザクションが保留されている必要があります。 これを行うには、トランザクションごとに個別のワークスペースを開く必要があります。 各ワークスペースはデータベースに対して独自の ODBC 接続を持つことができますが、システムのパフォーマンスが低下します。 トランザクションの分離は通常必要ではないため、同じユーザーが開いている複数のワークスペースオブジェクトからの ODBC 接続は、既定で共有されます。

Microsoft SQL Server などの一部の ODBC サーバーでは、単一の接続で同時トランザクションを使用することはできません。 このようなデータベースに対して保留中の複数のトランザクションを同時に実行する必要がある場合は、各ワークスペースの IsolateODBCTrans プロパティを [TRUE] に設定します。 これにより、ワークスペースごとに個別の ODBC 接続が強制的に実行します。

##  <a name="setlogintimeout"></a>CDaoWorkspace:: SetLoginTimeout

このメンバー関数を呼び出して、ワークスペースの DAO LoginTimeout プロパティの値を設定します。

```
static void PASCAL SetLoginTimeout(short nSeconds);
```

### <a name="parameters"></a>パラメーター

*nSeconds*<br/>
ODBC データベースにログインしようとしたときにエラーが発生するまでの秒数。

### <a name="remarks"></a>コメント

この値は、ODBC データベースにログインしようとしたときにエラーが発生するまでの秒数を表します。 LoginTimeout の既定値は20秒です。 LoginTimeout が0に設定されている場合、タイムアウトは発生せず、データソースとの通信が応答を停止する可能性があります。

Microsoft SQL Server などの ODBC データベースにログインしようとすると、ネットワークエラーが発生したか、サーバーが実行されていないため、接続が失敗することがあります。 既定の20秒間の接続を待機するのではなく、データベースエンジンがエラーを生成するまでの待機時間を指定できます。 サーバーへのログオンは、外部サーバーデータベースに対するクエリの実行など、さまざまなイベントの一部として暗黙的に行われます。 タイムアウト値は、LoginTimeout プロパティの現在の設定によって決まります。

関連情報については、DAO ヘルプの「LoginTimeout プロパティ」を参照してください。

## <a name="see-also"></a>参照

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDaoDatabase クラス](../../mfc/reference/cdaodatabase-class.md)<br/>
[CDaoRecordset クラス](../../mfc/reference/cdaorecordset-class.md)<br/>
[CDaoTableDef クラス](../../mfc/reference/cdaotabledef-class.md)<br/>
[CDaoQueryDef クラス](../../mfc/reference/cdaoquerydef-class.md)<br/>
[CDaoException クラス](../../mfc/reference/cdaoexception-class.md)
