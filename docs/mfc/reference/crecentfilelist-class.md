---
title: CRecentFileList クラス
ms.date: 11/04/2016
f1_keywords:
- CRecentFileList
- AFXADV/CRecentFileList
- AFXADV/CRecentFileList::CRecentFileList
- AFXADV/CRecentFileList::Add
- AFXADV/CRecentFileList::GetDisplayName
- AFXADV/CRecentFileList::GetSize
- AFXADV/CRecentFileList::ReadList
- AFXADV/CRecentFileList::Remove
- AFXADV/CRecentFileList::UpdateMenu
- AFXADV/CRecentFileList::WriteList
helpviewer_keywords:
- CRecentFileList [MFC], CRecentFileList
- CRecentFileList [MFC], Add
- CRecentFileList [MFC], GetDisplayName
- CRecentFileList [MFC], GetSize
- CRecentFileList [MFC], ReadList
- CRecentFileList [MFC], Remove
- CRecentFileList [MFC], UpdateMenu
- CRecentFileList [MFC], WriteList
ms.assetid: a77f0524-7584-4582-849a-7e97b76d186e
ms.openlocfilehash: 30536d91d057de4e551b5a28200dd903e12713b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62372180"
---
# <a name="crecentfilelist-class"></a>CRecentFileList クラス

MRU ファイル リストのコントロールをサポートします。

## <a name="syntax"></a>構文

```
class CRecentFileList
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CRecentFileList::CRecentFileList](#crecentfilelist)|`CRecentFileList` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRecentFileList::Add](#add)|MRU ファイル リストにファイルを追加します。|
|[CRecentFileList::GetDisplayName](#getdisplayname)|MRU ファイル名のメニューの表示の表示名を提供します。|
|[CRecentFileList::GetSize](#getsize)|MRU ファイル リスト内のファイルの数を取得します。|
|[CRecentFileList::ReadList](#readlist)|レジストリから MRU ファイル リストを読み込みますか。INI ファイルです。|
|[CRecentFileList::Remove](#remove)|MRU ファイル リストからファイルを削除します。|
|[CRecentFileList::UpdateMenu](#updatemenu)|MRU ファイル リストのメニューの表示を更新します。|
|[CRecentFileList::WriteList](#writelist)|レジストリから MRU ファイル リストを書き込みますか。INI ファイルです。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CRecentFileList::operator \[ \]](#operator_at)|返します、`CString`指定した位置にあるオブジェクト。|

## <a name="remarks"></a>Remarks

ファイルの一覧の読み取りまたはレジストリに書き込まれることができますが、ファイルを追加または MRU ファイル リストから削除できますか。INI ファイル、および MRU ファイル リストを表示するメニューを更新することができます。

## <a name="inheritance-hierarchy"></a>継承階層

`CRecentFileList`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxadv.h

##  <a name="add"></a>  CRecentFileList::Add

最近使用した (MRU) ファイルの一覧にファイルを追加します。

```
virtual void Add(LPCTSTR lpszPathName);

virtual void Add(
    LPCTSTR lpszPathName,
    LPCTSTR lpszAppID);

void Add(
    IShellItem* pItem,
    LPCTSTR lpszAppID);

void Add(
    IShellLink* pLink,
    LPCTSTR lpszAppID);

void Add(
    PIDLIST_ABSOLUTE pidl,
    LPCTSTR lpszAppID);
```

### <a name="parameters"></a>パラメーター

*lpszPathName*<br/>
一覧に追加するパス名を指定します。

*lpszAppID*<br/>
アプリケーションのアプリケーション ユーザー モデル ID を指定します。

*pItem*<br/>
一覧に追加するシェル項目へのポインターを指定します。

*pLink*<br/>
一覧に追加するシェル リンクへのポインターを指定します。

*pidl*<br/>
最近使ったドキュメント フォルダーに追加する必要がありますシェル項目の IDLIST を指定します。

### <a name="remarks"></a>Remarks

ファイル名を MRU 一覧の先頭に追加されます。 MRU 一覧にファイル名が既に存在する場合は、先頭に移動されます。

##  <a name="crecentfilelist"></a>  CRecentFileList::CRecentFileList

`CRecentFileList` オブジェクトを構築します。

```
CRecentFileList(
    UINT nStart,
    LPCTSTR lpszSection,
    LPCTSTR lpszEntryFormat,
    int nSize,
    int nMaxDispLen = AFX_ABBREV_FILENAME_LEN);
```

### <a name="parameters"></a>パラメーター

*nStart*<br/>
MRU (最近使用された) ファイル リストのメニュー表示内の番号のオフセットします。

*lpszSection*<br/>
レジストリのアプリケーションのセクションの名前を指します。INI ファイル MRU ファイル リストの読み取りや書き込みの位置。

*lpszEntryFormat*<br/>
レジストリまたはアプリケーションの格納されているエントリの名前に使用する書式指定文字列を指します。INI ファイルです。

*nSize*<br/>
MRU ファイル リスト内のファイルの最大数。

*nMaxDispLen*<br/>
MRU ファイル リスト内のファイル名のメニューの表示に使用できる文字数の最大長。

### <a name="remarks"></a>Remarks

書式指定文字列が指す*lpszEntryFormat* "%d"MRU の各項目のインデックスの置換に使用されるを含める必要があります。 たとえば、書式指定文字列は`"file%d"`エントリの名前が付けられますし、 `file0`、`file1`など。

##  <a name="getdisplayname"></a>  CRecentFileList::GetDisplayName

MRU 一覧の表示 メニューで使用するため、MRU ファイル リスト内のファイルの表示名を取得します。

```
virtual BOOL GetDisplayName(
    CString& strName,
    int nIndex,
    LPCTSTR lpszCurDir,
    int nCurDir,
    BOOL bAtLeastName = TRUE) const;
```

### <a name="parameters"></a>パラメーター

*strName*<br/>
名前は、MRU ファイルのメニューの一覧に表示されるファイルの完全パス。

*nIndex*<br/>
MRU ファイル リスト内のファイルの 0 から始まるインデックス。

*lpszCurDir*<br/>
現在のディレクトリを保持している文字列。

*nCurDir*<br/>
現在のディレクトリの文字列の長さ。

*bAtLeastName*<br/>
0 以外の場合を示します、ファイルの基本名を返すことを最大表示の長さを超えている場合でも (として渡される、 *nMaxDispLen*パラメーターを`CRecentFileList`コンス トラクター)。

### <a name="return-value"></a>戻り値

**FALSE**かどうかはファイル名指定したインデックス位置で最近使用した (MRU) ファイルの一覧。

### <a name="remarks"></a>Remarks

ファイルが現在のディレクトリ内にある場合は、関数は、ディレクトリ、ディスプレイの電源を残します。 ファイル名が長すぎる場合は、ディレクトリと拡張機能は削除されます。 しない限り、空の文字列に表示名を設定する場合は、ファイル名が長すぎるも*bAtLeastName*が 0 以外。

##  <a name="getsize"></a>  CRecentFileList::GetSize

MRU ファイル リスト内のファイルの数を取得します。

```
int GetSize() const;
```

### <a name="return-value"></a>戻り値

現在のファイルの数は、最近 (MRU) ファイルの一覧を使用します。

##  <a name="operator_at"></a>  CRecentFileList::operator [ ]

オーバー ロードされた添字 (`[]`) 演算子は、1 つを返します`CString`内の 0 から始まるインデックスによって指定された*nIndex*します。

```
CString& operator[ ](int nindex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
0 から始まるインデックス、`CString`一連の`CString`秒。

##  <a name="readlist"></a>  CRecentFileList::ReadList

最近使用した (MRU) からレジストリまたはアプリケーションのファイルの一覧を読み取ります。INI ファイルです。

```
virtual void ReadList();
```

##  <a name="remove"></a>  CRecentFileList::Remove

MRU ファイル リストからファイルを削除します。

```
virtual void Remove(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
最近使用した (MRU) ファイルの一覧から削除するファイルの 0 から始まるインデックス。

##  <a name="updatemenu"></a>  CRecentFileList::UpdateMenu

MRU ファイル リストのメニューの表示を更新します。

```
virtual void UpdateMenu(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>パラメーター

*pCmdUI*<br/>
ポインター、 [CCmdUI](../../mfc/reference/ccmdui-class.md)最近使用した (MRU) ファイルのリスト メニューのオブジェクト。

##  <a name="writelist"></a>  CRecentFileList::WriteList

最もレジストリまたはアプリケーションの最近使用した (MRU) ファイルの一覧を書き込みます。INI ファイルです。

```
virtual void WriteList();
```

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)
