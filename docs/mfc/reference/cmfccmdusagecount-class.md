---
title: CMFCCmdUsageCount クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::AddCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::GetCount
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::HasEnoughInformation
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::IsFreqeuntlyUsedCmd
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Reset
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::Serialize
- AFXCMDUSAGECOUNT/CMFCCmdUsageCount::SetOptions
helpviewer_keywords:
- CMFCCmdUsageCount [MFC], AddCmd
- CMFCCmdUsageCount [MFC], GetCount
- CMFCCmdUsageCount [MFC], HasEnoughInformation
- CMFCCmdUsageCount [MFC], IsFreqeuntlyUsedCmd
- CMFCCmdUsageCount [MFC], Reset
- CMFCCmdUsageCount [MFC], Serialize
- CMFCCmdUsageCount [MFC], SetOptions
ms.assetid: 9c33b783-37c0-43ea-9f31-3c75e246c841
ms.openlocfilehash: b4ad9a60831feb6fa1147ea3f8bcfd5c6badd06c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403803"
---
# <a name="cmfccmdusagecount-class"></a>CMFCCmdUsageCount クラス

など、ユーザーがメニューから項目を選択すると、Windows メッセージの使用率カウントを追跡します。

## <a name="syntax"></a>構文

```
class CMFCCmdUsageCount : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|||
|-|-|
|名前|説明|
|`CMFCCmdUsageCount::CMFCCmdUsageCount`|既定のコンストラクターです。|
|`CMFCCmdUsageCount::~CMFCCmdUsageCount`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|名前|説明|
|[CMFCCmdUsageCount::AddCmd](#addcmd)|指定されたコマンドに関連付けられているカウンターを 1 つずつインクリメントされます。|
|[CMFCCmdUsageCount::GetCount](#getcount)|指定されたコマンド ID に関連付けられている使用率カウントを取得します。|
|[CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)|このオブジェクトが追跡データの最小量を収集するかどうかを判断します。|
|[CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)|指定したコマンドを頻繁に使用するかどうかを判断します。|
|[CMFCCmdUsageCount::Reset](#reset)|すべてのコマンドの使用率カウントをクリアします。|
|[CMFCCmdUsageCount::Serialize](#serialize)|アーカイブからこのオブジェクトを読み取りまたはアーカイブに書き込みます。 ( [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize)をオーバーライドします)。|
|[CMFCCmdUsageCount::SetOptions](#setoptions)|セットの値は共有`CMFCCmdUsageCount`クラスのデータ メンバー。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|名前|説明|
|`m_CmdUsage`|A`CMap`コマンドを使用状況カウントにマップするオブジェクト。|
|`m_nMinUsagePercentage`|頻繁に使用するコマンドの使用率の最小の割合。|
|`m_nStartCount`|このオブジェクトが追跡データの最小量を収集するかどうかを決定するために使用される開始カウンター。|
|`m_nTotalUsage`|すべての追跡コマンドの数。|

### <a name="remarks"></a>Remarks

`CMFCCmdUsageCount`クラスは、32 ビット符号なし整数のカウンターに各数値の Windows メッセージの識別子をマップします。 `CMFCToolBar` 頻繁に使用するツールバー項目を表示するのにには、このクラスを使用します。 詳細については`CMFCToolBar`を参照してください[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)します。

永続化することができます`CMFCCmdUsageCount`プログラムの実行の間のデータのクラスします。 使用して、 [CMFCCmdUsageCount::Serialize](#serialize)クラス メンバー データをシリアル化する方法と、 [CMFCCmdUsageCount::SetOptions](#setoptions)共有メンバー データを設定します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCmdUsageCount](../../mfc/reference/cmfccmdusagecount-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmdusagecount.h

##  <a name="addcmd"></a>  CMFCCmdUsageCount::AddCmd

指定されたコマンドに関連付けられているカウンターを 1 つずつインクリメントされます。

```
void AddCmd(UINT uiCmd);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*uiCmd*|[in]インクリメントするコマンドのカウンターを指定します。|

### <a name="remarks"></a>Remarks

このメソッドは、コマンドの数のマップの構造に新しいエントリを追加`m_CmdUsage`エントリが存在しない場合、します。

このメソッドでは、次のケースではありません。

- ツールバーのフレームワークはカスタマイズ モード (、 [CMFCToolBar::IsCustomizeMode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)メソッドは 0 以外の値を返します)。

- コマンドが、サブメニューで開くか、メニューの区切り記号を指す ( *uiCmd* equals 0 または-1)。

- *uiCmd*標準のコマンドを表します (グローバル`IsStandardCommand`関数は 0 以外の値を返します)。

##  <a name="getcount"></a>  CMFCCmdUsageCount::GetCount

指定されたコマンド ID に関連付けられている使用率カウントを取得します。

```
UINT GetCount(UINT uiCmd) const;
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*uiCmd*|[in]取得するコマンドのカウンターの ID。|

### <a name="return-value"></a>戻り値

指定されたコマンド ID に関連付けられている使用率カウント

##  <a name="hasenoughinformation"></a>  CMFCCmdUsageCount::HasEnoughInformation

このオブジェクトが追跡データの最小量を受信したかどうかを判断します。

```
BOOL HasEnoughInformation() const;
```

### <a name="return-value"></a>戻り値

このオブジェクトが最小量の追跡データを受信した場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

場合、このメソッドは 0 以外の値を返します、総数`m_nTotalUsage`、追跡されているすべてのコマンドは最初の数以上`m_nStartCount`します。 既定では、フレームワークは、0 の最初の数を設定します。 使用して、この値を上書きすることができます、 [CMFCCmdUsageCount::SetOptions](#setoptions)メソッド。

このメソッドによって使用されます[CMFCMenuBar::IsShowAllCommands](../../mfc/reference/cmfcmenubar-class.md#isshowallcommands)をすべて使用可能なメニュー コマンドを表示するかどうかを判断します。

##  <a name="isfreqeuntlyusedcmd"></a>  CMFCCmdUsageCount::IsFreqeuntlyUsedCmd

指定したコマンドを頻繁に使用するかどうかを判断します。

```
BOOL IsFreqeuntlyUsedCmd(UINT uiCmd) const;
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*uiCmd*|[in]チェックするには、コマンドを指定します。|

### <a name="return-value"></a>戻り値

コマンドが頻繁に使用する場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

このメソッドは、場合に 0 を返します合計コマンドの使用方法、`m_nTotalUsage`は 0 です。 それ以外の場合、このメソッドが、指定したコマンドを使用する割合が最小の割合よりも大きい場合は 0 以外を返します`m_nMinUsagePercentage`します。 既定では、フレームワークは最小の割合を 5 に設定します。 使用して、この値を上書きすることができます、 [CMFCCmdUsageCount::SetOptions](#setoptions)メソッド。 最小の割合が 0 の場合は、このメソッドは、指定されたコマンド数が 0 より大きい場合、0 以外の値を返します。

[CMFCToolBar::IsCommandRarelyUsed](../../mfc/reference/cmfctoolbar-class.md#iscommandrarelyused)このメソッドを使用して、コマンドはほとんど使用されているかどうかを判断します。

##  <a name="reset"></a>  CMFCCmdUsageCount::Reset

すべてのコマンドの使用率カウントをクリアします。

```
void Reset();
```

### <a name="remarks"></a>Remarks

コマンドの数のマップの構造からすべてのエントリをクリアするには、このメソッドを呼び出す`m_CmdUsage`、およびコマンドの合計使用量をリセットするため`m_nTotalUsage`、カウンターを 0 にします。

##  <a name="serialize"></a>  CMFCCmdUsageCount::Serialize

アーカイブからこのオブジェクトを読み取りまたはアーカイブに書き込みます。

```
virtual void Serialize(CArchive& ar);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*ar*|[in]A`CArchive`をシリアル化するオブジェクト。|

### <a name="remarks"></a>Remarks

このメソッドは、コマンドの数のマップの構造体をシリアル化します`m_CmdUsage`、および合計コマンドの使用法、 `m_nTotalUsage`、または指定されたアーカイブするカウンター。

シリアル化の例については、次を参照してください。[シリアル化します。オブジェクトのシリアル化](../../mfc/serialization-serializing-an-object.md)します。

##  <a name="setoptions"></a>  CMFCCmdUsageCount::SetOptions

セットの値は共有`CMFCCmdUsageCount`クラスのデータ メンバー。

```
static BOOL __stdcall SetOptions(
    UINT nStartCount,
    UINT nMinUsagePercentage);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*nStartCount*|[in]すべての追跡コマンドの新しい最初の数。|
|*nMinUsagePercentage*|[in]新しい使用率の最小割合。|

### <a name="return-value"></a>戻り値

メソッドが成功した場合、FALSE 場合は TRUE、 *nMinUsagePercentage*よりも大きいか、または 100 になります。

### <a name="remarks"></a>Remarks

このメソッドは、共有設定`CMFCCmdUsageCount`クラスのデータ メンバー`m_nStartCount`と`m_nMinUsagePercentage`に*nStartCount*と*nMinUsagePercentage*、それぞれします。 `m_nStartCount` 使って、 [CMFCCmdUsageCount::HasEnoughInformation](#hasenoughinformation)メソッドをこのオブジェクトが追跡データの最小量を収集するかどうかを決定します。 `m_nMinUsagePercentage` 使って、 [CMFCCmdUsageCount::IsFreqeuntlyUsedCmd](#isfreqeuntlyusedcmd)する特定のコマンドを頻繁に使用するかどうかを判断するメソッド。

場合はデバッグ ビルドでこのメソッドが、アサーション エラーを生成、 *nMinUsagePercentage*よりも大きいか、または 100 になります。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)
