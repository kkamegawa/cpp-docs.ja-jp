---
title: CWaitCursor クラス
ms.date: 11/04/2016
f1_keywords:
- CWaitCursor
- AFXWIN/CWaitCursor
- AFXWIN/CWaitCursor::CWaitCursor
- AFXWIN/CWaitCursor::Restore
helpviewer_keywords:
- CWaitCursor [MFC], CWaitCursor
- CWaitCursor [MFC], Restore
ms.assetid: 5dfae2ff-d7b6-4383-b0ad-91e0868c67b3
ms.openlocfilehash: 87ac87019f127d3956caf959a28fc889fdecad50
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450811"
---
# <a name="cwaitcursor-class"></a>CWaitCursor クラス

時間がかかる処理を実行している最中に、通常は砂時計として表示される待機カーソルを表示する 1 つの方法を提供します。

## <a name="syntax"></a>構文

```
class CWaitCursor
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CWaitCursor::CWaitCursor](#cwaitcursor)|構築、`CWaitCursor`オブジェクトし、待機カーソルを表示します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CWaitCursor::Restore](#restore)|変更された後に待機カーソルを復元します。|

## <a name="remarks"></a>Remarks

`CWaitCursor` 基本クラスはありません。

適切な Windows のプログラミングでは、かなりの時間のかかる操作を実行しているときに待機カーソルを表示することが必要です。

待機カーソルを表示する定義だけを`CWaitCursor`時間のかかる操作を実行するコードの前に変数。 オブジェクトのコンス トラクターは、自動的に表示される待機カーソルをによりします。

オブジェクトがスコープから外れたときに (をブロックの最後に、`CWaitCursor`オブジェクトが宣言されている)、デストラクターを以前のカーソル、カーソルを設定します。 つまり、オブジェクトを自動的に必要なクリーンアップを実行します。

> [!NOTE]
>  コンス トラクターとデストラクターの動作のため`CWaitCursor`オブジェクトは常にローカル変数として宣言、グローバル変数として宣言もで割り当てられている**新しい**します。

カーソルが、メッセージ ボックスまたはダイアログ ボックスで、呼び出しを表示するなど、変更する操作を実行する場合、[復元](#restore)に待機カーソルを復元するメンバー関数。 呼び出すことが`Restore`待機カーソルが表示されている場合でもです。

待機カーソルを表示する別の方法は、の組み合わせを使用する[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)、 [CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)、そして[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor). ただし、`CWaitCursor`時間のかかる操作を完了すると、以前のカーソルにカーソルを設定する必要がないために使用する方が簡単です。

> [!NOTE]
>  MFC を設定し、カーソルを使用して、復元、 [CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)仮想関数。 カスタム動作を提供するには、この関数をオーバーライドすることができます。

## <a name="inheritance-hierarchy"></a>継承階層

`CWaitCursor`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#62](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_1.cpp)]

##  <a name="cwaitcursor"></a>  CWaitCursor::CWaitCursor

待機カーソルを表示する宣言するだけ、`CWaitCursor`時間のかかる操作を実行するコードの前にオブジェクト。

```
CWaitCursor();
```

### <a name="remarks"></a>Remarks

コンス トラクターは、自動的に表示される待機カーソルをによりします。

オブジェクトがスコープから外れたときに (をブロックの最後に、`CWaitCursor`オブジェクトが宣言されている)、デストラクターを以前のカーソル、カーソルを設定します。 つまり、オブジェクトを自動的に必要なクリーンアップを実行します。

事実、関数の一部のみで待機カーソルをアクティブにする (が関数の終了前にあります)、ブロックの最後に、デストラクターが呼び出されることを利用できます。 この手法は、次の 2 つ目の例に示します。

> [!NOTE]
>  コンス トラクターとデストラクターの動作のため`CWaitCursor`オブジェクトは常にローカル変数として宣言など、グローバル変数として宣言もで割り当てられている**新しい**します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#63](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_2.cpp)]

##  <a name="restore"></a>  CWaitCursor::Restore

待機カーソルを復元するには、メッセージ ボックスまたは待機カーソルを別のカーソルに変わる可能性のあるダイアログ ボックスを表示するなどの操作を実行した後、この関数を呼び出します。

```
void Restore();
```

### <a name="remarks"></a>Remarks

呼び出すには、[ok] を`Restore`待機カーソルが表示されている場合でもです。

1 つ以外の関数の中に待機カーソルを復元する必要がある場合、`CWaitCursor`を呼び出して、オブジェクトが宣言されている[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#64](../../mfc/reference/codesnippet/cpp/cwaitcursor-class_3.cpp)]

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget::BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)<br/>
[CCmdTarget::EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)<br/>
[CCmdTarget::RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)<br/>
[CWinApp::DoWaitCursor](../../mfc/reference/cwinapp-class.md#dowaitcursor)<br/>
[How Do i:Microsoft Foundation クラスのアプリケーションでマウス カーソルを変更します。](https://go.microsoft.com/fwlink/p/?linkid=128044)
