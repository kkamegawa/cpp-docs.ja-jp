---
title: CShellManager クラス
ms.date: 11/04/2016
f1_keywords:
- CShellManager
- AFXSHELLMANAGER/CShellManager
- AFXSHELLMANAGER/CShellManager::CShellManager
- AFXSHELLMANAGER/CShellManager::BrowseForFolder
- AFXSHELLMANAGER/CShellManager::ConcatenateItem
- AFXSHELLMANAGER/CShellManager::CopyItem
- AFXSHELLMANAGER/CShellManager::CreateItem
- AFXSHELLMANAGER/CShellManager::FreeItem
- AFXSHELLMANAGER/CShellManager::GetItemCount
- AFXSHELLMANAGER/CShellManager::GetItemSize
- AFXSHELLMANAGER/CShellManager::GetNextItem
- AFXSHELLMANAGER/CShellManager::GetParentItem
- AFXSHELLMANAGER/CShellManager::ItemFromPath
helpviewer_keywords:
- CShellManager [MFC], CShellManager
- CShellManager [MFC], BrowseForFolder
- CShellManager [MFC], ConcatenateItem
- CShellManager [MFC], CopyItem
- CShellManager [MFC], CreateItem
- CShellManager [MFC], FreeItem
- CShellManager [MFC], GetItemCount
- CShellManager [MFC], GetItemSize
- CShellManager [MFC], GetNextItem
- CShellManager [MFC], GetParentItem
- CShellManager [MFC], ItemFromPath
ms.assetid: f15c4c1a-6fae-487d-9913-9b7369b33da0
ms.openlocfilehash: 8151550dafdd1bdf8593d555008af387cf548bc8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502624"
---
# <a name="cshellmanager-class"></a>CShellManager クラス

ID リストへのポインター (PIDL) を操作するためのさまざまなメソッドを実装します。

## <a name="syntax"></a>構文

```
class CShellManager : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CShellManager:: CShellManager](#cshellmanager)|`CShellManager` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CShellManager::BrowseForFolder](#browseforfolder)|ユーザーがシェルフォルダーを選択できるダイアログボックスを表示します。|
|[CShellManager:: ConcatenateItem](#concatenateitem)|2つの Pidl を連結します。|
|[CShellManager:: CopyItem](#copyitem)|新しい PIDL を作成し、指定された PIDL をその PIDL にコピーします。|
|[CShellManager:: CreateItem](#createitem)|指定したサイズの新しい PIDL を作成します。|
|[CShellManager:: FreeItem](#freeitem)|指定された PIDL を削除します。|
|[CShellManager:: GetItemCount](#getitemcount)|指定された PIDL 内の項目数を返します。|
|[CShellManager:: GetItemSize](#getitemsize)|指定された PIDL のサイズを返します。|
|[CShellManager:: GetNextItem](#getnextitem)|PIDL から次の項目を返します。|
|[CShellManager:: GetParentItem](#getparentitem)|指定された項目の親項目を取得します。|
|[CShellManager:: ItemFromPath](#itemfrompath)|指定されたパスによって識別される項目の PIDL を取得します。|

## <a name="remarks"></a>Remarks

`CShellManager`クラスのメソッドはすべて、pidl を処理します。 PIDL は、シェルオブジェクトの一意の識別子です。

オブジェクトを`CShellManager`手動で作成しないでください。 アプリケーションのフレームワークによって自動的に作成されます。 ただし、アプリケーションの初期化プロセスでは、 [CWinAppEx:: InitShellManager](../../mfc/reference/cwinappex-class.md#initshellmanager)を呼び出す必要があります。 アプリケーションのシェルマネージャーへのポインターを取得するには、 [CWinAppEx:: GetShellManager](../../mfc/reference/cwinappex-class.md#getshellmanager)を呼び出します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CShellManager](../../mfc/reference/cshellmanager-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxshellmanager

##  <a name="browseforfolder"></a>  CShellManager::BrowseForFolder

ユーザーがシェルフォルダーを選択できるダイアログボックスを表示します。

```
BOOL BrowseForFolder(
    CString& strOutFolder,
    CWnd* pWndParent = NULL,
    LPCTSTR lplszInitialFolder = NULL,
    LPCTSTR lpszTitle = NULL,
    UINT ulFlags = BIF_RETURNONLYFSDIRS,
    LPINT piFolderImage = NULL);
```

### <a name="parameters"></a>パラメーター

*strOutFolder*<br/>
入出力選択したフォルダーのパスを格納するためにメソッドによって使用される文字列。

*pWndParent*<br/>
から親ウィンドウへのポインター。

*lplszInitialFolder*<br/>
からダイアログボックスが表示されるときに既定で選択されるフォルダーを含む文字列。

*lpszTitle*<br/>
からダイアログボックスのタイトル。

*ulFlags*<br/>
からダイアログボックスのオプションを指定するフラグ。 詳細については、「 [BROWSEINFO](/windows/win32/api/shlobj_core/ns-shlobj_core-browseinfow) 」を参照してください。

*piFolderImage*<br/>
入出力メソッドが、選択したフォルダーのイメージインデックスを書き込む整数値へのポインター。

### <a name="return-value"></a>戻り値

ユーザーがダイアログボックスからフォルダーを選択した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメソッドを呼び出すと、アプリケーションによって、ユーザーがフォルダーを選択できるダイアログボックスが作成されて表示されます。 メソッドは、フォルダーのパスを*strOutFolder*パラメーターに書き込みます。

### <a name="example"></a>例

次の例は、 `CShellManager` `CWinAppEx::GetShellManager`メソッドを使用してオブジェクトへの参照を取得する方法と、 `BrowseForFolder`メソッドを使用する方法を示しています。 このコードスニペットは、エクスプローラーの[サンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_Explorer#6](../../mfc/reference/codesnippet/cpp/cshellmanager-class_1.cpp)]

##  <a name="concatenateitem"></a>CShellManager:: ConcatenateItem

2つの Pidl を含む新しいリストを作成します。

```
LPITEMIDLIST ConcatenateItem(
    LPCITEMIDLIST pidl1,
    LPCITEMIDLIST pidl2);
```

### <a name="parameters"></a>パラメーター

*pidl1*<br/>
から最初の項目。

*pidl2*<br/>
から2番目の項目。

### <a name="return-value"></a>戻り値

関数が成功した場合は、新しい項目のリストへのポインター。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

このメソッドは、 *pidl1*と*pidl2*の両方を格納するのに十分な大きさの新しい[itemidlist](/windows/win32/api/shtypes/ns-shtypes-itemidlist)を作成します。 次に、 *pidl1*と*pidl2*を新しいリストにコピーします。

##  <a name="copyitem"></a>  CShellManager::CopyItem

項目リストをコピーします。

```
LPITEMIDLIST CopyItem(LPCITEMIDLIST pidlSource);
```

### <a name="parameters"></a>パラメーター

*pidlSource*<br/>
から元の項目リスト。

### <a name="return-value"></a>戻り値

成功した場合は、新しく作成された項目リストへのポインター。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

新しく作成されたアイテムの一覧は、ソースアイテムの一覧と同じサイズになります。

##  <a name="createitem"></a>CShellManager:: CreateItem

新しい PIDL を作成します。

```
LPITEMIDLIST CreateItem(UINT cbSize);
```

### <a name="parameters"></a>パラメーター

*cbSize*<br/>
から項目リストのサイズ。

### <a name="return-value"></a>戻り値

成功した場合は、作成された項目リストへのポインター。それ以外の場合は NULL。

##  <a name="cshellmanager"></a>CShellManager:: CShellManager

`CShellManager` オブジェクトを構築します。

```
CShellManager();
```

### <a name="remarks"></a>Remarks

ほとんどの場合、を`CShellManager`直接作成する必要はありません。 既定では、フレームワークによって作成されます。 への`CShellManager`ポインターを取得するには、 [CWinAppEx:: getshellmanager](../../mfc/reference/cwinappex-class.md#getshellmanager)を呼び出します。 を`CShellManager`手動で作成する場合は、 [CWinAppEx:: initshellmanager](../../mfc/reference/cwinappex-class.md#initshellmanager)メソッドを使用して初期化する必要があります。

##  <a name="freeitem"></a>CShellManager:: FreeItem

項目リストを削除します。

```
void FreeItem(LPITEMIDLIST pidl);
```

### <a name="parameters"></a>パラメーター

*pidl*<br/>
から削除する項目リスト。

##  <a name="getitemcount"></a>  CShellManager::GetItemCount

項目リスト内の項目の数を返します。

```
UINT GetItemCount(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>パラメーター

*pidl*<br/>
から項目リストへのポインター。

### <a name="return-value"></a>戻り値

項目リスト内の項目の数。

##  <a name="getitemsize"></a>CShellManager:: GetItemSize

項目リストのサイズを返します。

```
UINT GetItemSize(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>パラメーター

*pidl*<br/>
から項目リストへのポインター。

### <a name="return-value"></a>戻り値

項目リストのサイズ。

##  <a name="getnextitem"></a>  CShellManager::GetNextItem

項目識別子リスト (PIDL) へのポインターから次の項目を取得します。

```
LPITEMIDLIST GetNextItem(LPCITEMIDLIST pidl);
```

### <a name="parameters"></a>パラメーター

*pidl*<br/>
から反復処理する項目のリスト。

### <a name="return-value"></a>戻り値

リスト内の次の項目へのポインター。

### <a name="remarks"></a>Remarks

リストに他の項目がない場合、このメソッドは NULL を返します。

##  <a name="getparentitem"></a>  CShellManager::GetParentItem

項目識別子リスト (PIDL) へのポインターの親を取得します。

```
int GetParentItem(
    LPCITEMIDLIST lpidl,
    LPITEMIDLIST& lpidlParent);
```

### <a name="parameters"></a>パラメーター

*lpidl*<br/>
から親を取得する PIDL。

*lpidlParent*<br/>
入出力メソッドが結果を格納する PIDL への参照。

### <a name="return-value"></a>戻り値

親の PIDL のレベル。

### <a name="remarks"></a>Remarks

PIDL のレベルは、デスクトップに対する相対パスです。 デスクトップの PIDL のレベルは0であると見なされます。

##  <a name="itemfrompath"></a>  CShellManager::ItemFromPath

文字列パスによって識別される項目から項目識別子リスト (PIDL) へのポインターを取得します。

```
HRESULT ItemFromPath(
    LPCTSTR lpszPath,
    LPITEMIDLIST& pidl);
```

### <a name="parameters"></a>パラメーター

*lpszPath*<br/>
から項目のパスを指定する文字列。

*pidl*<br/>
入出力PIDL への参照。 メソッドは、この PIDL を使用して、戻り値へのポインターを格納します。

### <a name="return-value"></a>戻り値

成功した場合、NOERROR を返します。OLE 定義エラー値です。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
