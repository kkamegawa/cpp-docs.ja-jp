---
title: CDockState クラス
ms.date: 11/04/2016
f1_keywords:
- CDockState
- AFXADV/CDockState
- AFXADV/CDockState::Clear
- AFXADV/CDockState::GetVersion
- AFXADV/CDockState::LoadState
- AFXADV/CDockState::SaveState
- AFXADV/CDockState::m_arrBarInfo
helpviewer_keywords:
- CDockState [MFC], Clear
- CDockState [MFC], GetVersion
- CDockState [MFC], LoadState
- CDockState [MFC], SaveState
- CDockState [MFC], m_arrBarInfo
ms.assetid: 09e7c10b-3abd-4cb2-ad36-42420fe6bc36
ms.openlocfilehash: b8c4b80d7182795d8919adb64491d506325976ef
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391180"
---
# <a name="cdockstate-class"></a>CDockState クラス

いくつかのドッキング コントロール バーの状態を 2 次メモリ (ファイル) で読み込み、アンロード、またはクリアするシリアル化された `CObject` クラスです。

## <a name="syntax"></a>構文

```
class CDockState : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDockState::Clear](#clear)|ドッキング状態情報をクリアします。|
|[CDockState::GetVersion](#getversion)|格納されているのバージョン番号を取得します。 バーの状態。|
|[CDockState::LoadState](#loadstate)|レジストリからの情報の状態を取得しますか。INI ファイルです。|
|[後](#savestate)|状態情報をレジストリまたは INI ファイルに保存します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDockState::m_arrBarInfo](#m_arrbarinfo)|格納されているへのポインターの配列では、それぞれのコントロール バーの 1 つのエントリに状態情報をドッキングします。|

## <a name="remarks"></a>Remarks

ドッキング状態には、バーとドッキングされているかどうかの位置とサイズが含まれています。 ドッキング状態が格納されているを取得するときに`CDockState`バーのチェック位置と、バーが、現在の画面の設定で表示されない場合`CDockState`バーの位置が表示されるようにします。 主な目的`CDockState`を保存するには、その状態を許可するのには、さまざまなコントロール バーの全体の状態を保持して、レジストリに、アプリケーションのいずれかが読み込まれます。INI ファイル、またはバイナリ形式の一部として、`CArchive`オブジェクトの内容。

バーは、任意のドッキング可能なコントロール バー、ツールバー、ステータス バー、またはダイアログ バーを含むです。 `CDockState` オブジェクトが書き込まれ、する、またはを使用してファイルから読み取る、`CArchive`オブジェクト。

[CFrameWnd::GetDockState](../../mfc/reference/cframewnd-class.md#getdockstate)フレーム ウィンドウのすべての状態情報を取得`CControlBar`オブジェクトを配置に、`CDockState`オブジェクト。 内容を記述することができますし、`CDockState`オブジェクトを使用してストレージに[Serialize](../../mfc/reference/cobject-class.md#serialize)または[後](#savestate)します。 後で、フレーム ウィンドウにコントロール バーの状態を復元する場合での状態を読み込むことができます`Serialize`または[CDockState::LoadState](#loadstate)を使用して[CFrameWnd::SetDockState](../../mfc/reference/cframewnd-class.md#setdockstate)保存されたを適用するにはフレーム ウィンドウのコントロール バーの状態です。

ドッキング コントロール バーの詳細については、記事をご覧ください。[コントロール バー](../../mfc/control-bars.md)、[ツールバー。ドッキングとフローティング](../../mfc/docking-and-floating-toolbars.md)、および[Windows フレーム](../../mfc/frame-windows.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CDockState`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxadv.h

##  <a name="clear"></a>  CDockState::Clear

格納されているすべてのドッキング情報をクリアするには、この関数を呼び出し、`CDockState`オブジェクト。

```
void Clear();
```

### <a name="remarks"></a>Remarks

これには、表示されているかどうかを示すだけでなく、バーがドッキングされているか、バーのサイズと位置があるかどうかとが含まれます。

##  <a name="getversion"></a>  CDockState::GetVersion

格納されているのバージョン番号を取得するには、この関数を呼び出すバーの状態。

```
DWORD GetVersion();
```

### <a name="return-value"></a>戻り値

1 の場合、格納されているバー情報が現在の状態バーより古い場合は 2 ストアド バー情報は、現在と同じ状態のバーします。

### <a name="remarks"></a>Remarks

バージョン サポートでは、新しい永続的なプロパティを追加しを検出し、以前のバージョンのバーによって作成された永続的な状態の読み込みができる変更後のバーができます。

##  <a name="loadstate"></a>  CDockState::LoadState

レジストリから状態情報を取得するには、この関数を呼び出すか。INI ファイルです。

```
void LoadState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
初期化ファイルの状態情報が格納されている Windows レジストリのキーのセクションの名前を指定する null で終わる文字列へのポインター。

### <a name="remarks"></a>Remarks

プロファイル名は、アプリケーションのセクションを示します。INI ファイル、またはバーの状態情報を含むレジストリ。 コントロール バーの状態情報をレジストリに保存できますか。INI ファイルを`SaveState`します。

##  <a name="m_arrbarinfo"></a>  CDockState::m_arrBarInfo

A`CPtrArray`ストアド コントロール バー情報の状態の情報が保存される各コントロール バーへのポインターの配列であるオブジェクトを`CDockState`オブジェクト。

```
CPtrArray m_arrBarInfo;
```

##  <a name="savestate"></a>  CDockState::SaveState

状態情報をレジストリに保存するには、この関数を呼び出すか。INI ファイルです。

```
void SaveState(LPCTSTR lpszProfileName);
```

### <a name="parameters"></a>パラメーター

*lpszProfileName*<br/>
初期化ファイルの状態情報が格納されている Windows レジストリのキーのセクションの名前を指定する null で終わる文字列へのポインター。

### <a name="remarks"></a>Remarks

プロファイル名は、アプリケーションのセクションを示します。INI ファイルまたはレジストリを含むコントロール バーの状態情報。 `SaveState` また、現在の画面サイズを保存します。 コントロール バーの情報をレジストリから取得することができますか。INI ファイルを`LoadState`します。

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
