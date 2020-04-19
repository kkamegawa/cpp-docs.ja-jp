---
title: COleLinkingDoc クラス
ms.date: 11/04/2016
f1_keywords:
- COleLinkingDoc
- AFXOLE/COleLinkingDoc
- AFXOLE/COleLinkingDoc::COleLinkingDoc
- AFXOLE/COleLinkingDoc::Register
- AFXOLE/COleLinkingDoc::Revoke
- AFXOLE/COleLinkingDoc::OnFindEmbeddedItem
- AFXOLE/COleLinkingDoc::OnGetLinkedItem
helpviewer_keywords:
- COleLinkingDoc [MFC], COleLinkingDoc
- COleLinkingDoc [MFC], Register
- COleLinkingDoc [MFC], Revoke
- COleLinkingDoc [MFC], OnFindEmbeddedItem
- COleLinkingDoc [MFC], OnGetLinkedItem
ms.assetid: 9f547f35-2f95-427f-b9c0-85c31940198b
ms.openlocfilehash: c5076ceef0c6626fac0232fadf6818edd78b4ccf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224367"
---
# <a name="colelinkingdoc-class"></a>COleLinkingDoc クラス

OLE コンテナー ドキュメントの基底クラスです。OLE コンテナー ドキュメントは、ドキュメントが保持する埋め込みアイテムへのリンクをサポートします。

## <a name="syntax"></a>構文

```
class COleLinkingDoc : public COleDocument
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleLinkingDoc::COleLinkingDoc](#colelinkingdoc)|`COleLinkingDoc` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleLinkingDoc::Register](#register)|OLE システム Dll をドキュメントを登録します。|
|[COleLinkingDoc::Revoke](#revoke)|ドキュメントの登録を取り消します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[COleLinkingDoc::OnFindEmbeddedItem](#onfindembeddeditem)|指定された埋め込み項目を検索します。|
|[COleLinkingDoc::OnGetLinkedItem](#ongetlinkeditem)|指定したリンク アイテムを検索します。|

## <a name="remarks"></a>Remarks

埋め込みアイテムへのリンクをサポートするコンテナー アプリケーションは「リンク コンテナー」と呼ばれる [OCLIENT](../../overview/visual-cpp-samples.md)サンプル アプリケーションは、リンクのコンテナーの例を示します。

リンクされた項目のソースは、別のドキュメント内の埋め込み項目が、埋め込まれた項目を編集するためにそのコンテナーのドキュメントを読み込む必要があります。 このため、リンクのコンテナーは、ユーザーがリンクされた項目のソースを編集するときに別のコンテナー アプリケーションを起動できる必要があります。 アプリケーションを使用する必要がありますも、 [COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)クラスのプログラムで起動すると、ドキュメントを作成できるようにします。

リンクのコンテナーをするために、コンテナーからドキュメント クラスを派生`COleLinkingDoc`の代わりに[COleDocument](../../mfc/reference/coledocument-class.md)します。 その他の OLE コンテナーと同様、アプリケーションのネイティブ データだけでなく埋め込みまたはリンクされた項目を格納するため、クラスを設計する必要があります。 また、ネイティブ データを格納するためのデータ構造を設計する必要があります。 定義する場合、 `CDocItem`-派生クラスをアプリケーションのネイティブ データによって定義されたインターフェイスを使用して`COleDocument`OLE データと、ネイティブのデータを格納します。

別のコンテナーをプログラムで起動するアプリケーションを許可するのには、宣言、`COleTemplateServer`オブジェクトのアプリケーションのメンバーとして`CWinApp`の派生クラス。

[!code-cpp[NVC_MFCOleContainer#23](../../mfc/codesnippet/cpp/colelinkingdoc-class_1.h)]

`InitInstance`のメンバー関数、 `CWinApp`-派生クラスでドキュメント テンプレートを作成し、指定、 `COleLinkingDoc`-ドキュメント クラスとクラスを派生します。

[!code-cpp[NVC_MFCOleContainer#24](../../mfc/codesnippet/cpp/colelinkingdoc-class_2.cpp)]

接続、`COleTemplateServer`オブジェクトを呼び出して、オブジェクトのドキュメント テンプレートに`ConnectTemplate`メンバー関数、およびすべてのクラス オブジェクトを呼び出すことによって OLE システムに登録`COleTemplateServer::RegisterAll`:

[!code-cpp[NVC_MFCOleContainer#25](../../mfc/codesnippet/cpp/colelinkingdoc-class_3.cpp)]

サンプルについては、 `CWinApp`-派生したクラスの定義と`InitInstance`関数、OCLIENT を参照してください。H および OCLIENT します。MFC サンプル CPP [OCLIENT](../../overview/visual-cpp-samples.md)します。

使用しての詳細については`COleLinkingDoc`、記事を参照して[コンテナー。コンテナーの実装](../../mfc/containers-implementing-a-container.md)と[コンテナー。機能の高度な](../../mfc/containers-advanced-features.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

`COleLinkingDoc`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxole.h

##  <a name="colelinkingdoc"></a>  COleLinkingDoc::COleLinkingDoc

構築、 `COleLinkingDoc` OLE システム Dll との通信を開始せずオブジェクト。

```
COleLinkingDoc();
```

### <a name="remarks"></a>Remarks

呼び出す必要があります、 `Register` OLE ドキュメントが開いていることを通知するメンバー関数。

##  <a name="onfindembeddeditem"></a>  COleLinkingDoc::OnFindEmbeddedItem

ドキュメントに指定した名前の埋め込み OLE アイテムが含まれるかどうかを確認するためにフレームワークによって呼び出されます。

```
virtual COleClientItem* OnFindEmbeddedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>パラメーター

*lpszItemName*<br/>
埋め込み OLE アイテムの名前へのポインター。

### <a name="return-value"></a>戻り値

指定された項目へのポインター項目が見つからない場合は NULL です。

### <a name="remarks"></a>Remarks

既定の実装では、指定した名前 (名前の比較では大文字小文字を区別) を持つ項目の埋め込まれた項目の一覧を検索します。 格納や埋め込み OLE アイテムの名前を付け、独自のメソッドがある場合は、この関数をオーバーライドします。

##  <a name="ongetlinkeditem"></a>  COleLinkingDoc::OnGetLinkedItem

ドキュメントに指定した名前のリンク サーバーの項目が含まれているかどうか確認するためにフレームワークによって呼び出されます。

```
virtual COleServerItem* OnGetLinkedItem(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>パラメーター

*lpszItemName*<br/>
リンクされた OLE アイテムの名前へのポインター。

### <a name="return-value"></a>戻り値

指定された項目へのポインター項目が見つからない場合は NULL です。

### <a name="remarks"></a>Remarks

既定の`COleLinkingDoc`実装は常に NULL が返されます。 この関数は、派生クラスでオーバーライドされた`COleServerDoc`(名前の比較では大文字小文字を区別) 指定した名前のリンクされた項目の OLE サーバー項目の一覧を検索します。 保存したり、リンク サーバーの項目を取得したり、独自のメソッドを実装している場合は、この関数をオーバーライドします。

##  <a name="register"></a>  COleLinkingDoc::Register

ドキュメントが開かれている OLE システム Dll を通知します。

```
BOOL Register(
    COleObjectFactory* pFactory,
    LPCTSTR lpszPathName);
```

### <a name="parameters"></a>パラメーター

*pFactory*<br/>
(NULL を指定できます) OLE ファクトリ オブジェクトへのポインター。

*lpszPathName*<br/>
コンテナー ドキュメントの完全修飾パスへのポインター。

### <a name="return-value"></a>戻り値

ドキュメントが正常に登録されている場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

作成または OLE システム Dll でドキュメントを登録する名前付きのファイルを開くときは、この関数を呼び出します。 ドキュメントが埋め込まれた項目を表す場合は、この関数を呼び出す必要はありません。

使用する場合`COleTemplateServer`アプリケーションでは、`Register`によって呼び出されますが`COleLinkingDoc`の実装の`OnNewDocument`、 `OnOpenDocument`、および`OnSaveDocument`します。

##  <a name="revoke"></a>  COleLinkingDoc::Revoke

OLE システム Dll、ドキュメントが開いていないことを通知します。

```
void Revoke();
```

### <a name="remarks"></a>Remarks

OLE システム Dll のドキュメントの登録を取り消すには、この関数を呼び出します。

名前付きのファイルを閉じるときに、この関数を呼び出す必要がありますが、通常必要はありません直接呼び出せるようにします。 `Revoke` によって呼び出されますが`COleLinkingDoc`の実装の`OnCloseDocument`、 `OnNewDocument`、 `OnOpenDocument`、および`OnSaveDocument`します。

## <a name="see-also"></a>関連項目

[MFC サンプルの OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[COleDocument クラス](../../mfc/reference/coledocument-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CDocTemplate クラス](../../mfc/reference/cdoctemplate-class.md)
