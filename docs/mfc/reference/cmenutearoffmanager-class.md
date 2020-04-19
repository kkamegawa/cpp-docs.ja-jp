---
title: CMenuTearOffManager クラス
ms.date: 10/18/2018
f1_keywords:
- CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::CMenuTearOffManager
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Build
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::GetRegPath
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Initialize
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::IsDynamicID
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Parse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::Reset
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetInUse
- AFXMENUTEAROFFMANAGER/CMenuTearOffManager::SetupTearOffMenus
helpviewer_keywords:
- CMenuTearOffManager [MFC], CMenuTearOffManager
- CMenuTearOffManager [MFC], Build
- CMenuTearOffManager [MFC], GetRegPath
- CMenuTearOffManager [MFC], Initialize
- CMenuTearOffManager [MFC], IsDynamicID
- CMenuTearOffManager [MFC], Parse
- CMenuTearOffManager [MFC], Reset
- CMenuTearOffManager [MFC], SetInUse
- CMenuTearOffManager [MFC], SetupTearOffMenus
ms.assetid: ab7ca272-ce42-4678-95f7-6ad75038f5a0
ms.openlocfilehash: 8b92ddad9d3a6de41cf6914dee268f6e54b5d420
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62163709"
---
# <a name="cmenutearoffmanager-class"></a>CMenuTearOffManager クラス

ティアオフ メニューを管理します。 ティアオフ メニューはメニュー バー上のメニューの一種です。 ユーザーは、ティアオフ メニューをメニュー バーから外して、フローティング メニューにすることができます。

   詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

## <a name="syntax"></a>構文

```
class CMenuTearOffManager : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMenuTearOffManager::CMenuTearOffManager](#cmenutearoffmanager)|`CMenuTearOffManager` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMenuTearOffManager::Build](#build)||
|[CMenuTearOffManager::GetRegPath](#getregpath)||
|[CMenuTearOffManager::Initialize](#initialize)|初期化します、`CMenuTearOffManager`オブジェクト。|
|[CMenuTearOffManager::IsDynamicID](#isdynamicid)||
|[CMenuTearOffManager::Parse](#parse)||
|[CMenuTearOffManager::Reset](#reset)||
|[CMenuTearOffManager::SetInUse](#setinuse)||
|[CMenuTearOffManager::SetupTearOffMenus](#setuptearoffmenus)||

## <a name="remarks"></a>Remarks

必要がありますが、アプリケーションでティアオフ メニューを使用するには、`CMenuTearOffManager`オブジェクト。 ほとんどの場合に、作成または初期化するしません、`CMenuTearOffManager`オブジェクトに直接します。 これは自動的に処理を呼び出すとき、 [CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)関数。

## <a name="example"></a>例

次の例では、作成して初期化する方法、`CMenuTearOffManager`オブジェクトを呼び出すことによって、`CWinAppEX::EnableTearOffMenus`メソッド。 このコード スニペットは、 [Word パッド サンプル](../../overview/visual-cpp-samples.md)の一部です。

[!code-cpp[NVC_MFC_WordPad#12](../../mfc/reference/codesnippet/cpp/cmenutearoffmanager-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CMenuTearOffManager`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxmenutearoffmanager.h

##  <a name="build"></a>  CMenuTearOffManager::Build

```
void Build(
    UINT uiTearOffBarID,
    CString& strText);
```

### <a name="parameters"></a>パラメーター

[in]*uiTearOffBarID*<br/>

[in] *strText*<br/>

### <a name="remarks"></a>Remarks

##  <a name="cmenutearoffmanager"></a>  CMenuTearOffManager::CMenuTearOffManager

構築、 [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)オブジェクト。

```
CMenuTearOffManager();
```

### <a name="remarks"></a>Remarks

ほとんどの場合、作成しないようにする、`CMenuTearOffManager`手動でします。 アプリケーションのフレームワークを作成、`CMenuTearOffManager`オブジェクトを呼び出すと[CWinAppEx::EnableTearOffMenus](../../mfc/reference/cwinappex-class.md#enabletearoffmenus)します。

##  <a name="getregpath"></a>  CMenuTearOffManager::GetRegPath

```
LPCTSTR GetRegPath() const;
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="initialize"></a>  CMenuTearOffManager::Initialize

初期化します、 [CMenuTearOffManager](../../mfc/reference/cmenutearoffmanager-class.md)オブジェクト。

```
BOOL Initialize(
    LPCTSTR lpszRegEntry,
    UINT uiTearOffMenuFirst,
    UINT uiTearOffMenuLast);
```

### <a name="parameters"></a>パラメーター

*lpszRegEntry*<br/>
[in]レジストリ エントリのパスを含む文字列。 アプリケーションには、このレジストリ エントリでティアオフ バーの設定が格納されます。

*uiTearOffMenuFirst*<br/>
[in]ティアオフ メニューの最初のメニューの ID。

*uiTearOffMenuLast*<br/>
[in]ティアオフ メニューの最後のメニューの ID。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

メニュー Id の範囲*uiTearOffMenuFirst*に*uiTearOffMenuLast*継続的な間隔である必要があります。 間隔は、ティアオフ メニュー アプリケーションで同時に表示できる数を定義します。

##  <a name="isdynamicid"></a>  CMenuTearOffManager::IsDynamicID

```
BOOL IsDynamicID(UINT uiID) const;
```

### <a name="parameters"></a>パラメーター

[in]*uiID*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="parse"></a>  CMenuTearOffManager::Parse

```
UINT Parse(CString& str);
```

### <a name="parameters"></a>パラメーター

[in]*str*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="reset"></a>  CMenuTearOffManager::Reset

```
void Reset(HMENU hmenu);
```

### <a name="parameters"></a>パラメーター

[in]*hmenu*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setinuse"></a>  CMenuTearOffManager::SetInUse

```
void SetInUse(
    UINT uiCmdId,
    BOOL bUse = TRUE);
```

### <a name="parameters"></a>パラメーター

[in] *uiCmdId*<br/>

[in]*bUse*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setuptearoffmenus"></a>  CMenuTearOffManager::SetupTearOffMenus

```
void SetupTearOffMenus(HMENU hMenu);
```

### <a name="parameters"></a>パラメーター

[in]*hMenu*<br/>

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CWinAppEx クラス](../../mfc/reference/cwinappex-class.md)
