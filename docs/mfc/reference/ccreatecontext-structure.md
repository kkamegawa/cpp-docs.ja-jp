---
title: CCreateContext 構造体
ms.date: 11/04/2016
f1_keywords:
- CCreateContext
helpviewer_keywords:
- CCreateContext structure [MFC]
ms.assetid: 337a0e44-d910-49a8-afc0-c7207666a9dc
ms.openlocfilehash: 795b20cba41eeca8cc1a32e312edf065b718f364
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347143"
---
# <a name="ccreatecontext-structure"></a>CCreateContext 構造体

フレームワークを使用して、`CCreateContext`フレーム ウィンドウとドキュメントに関連付けられているビューの作成時に構造体します。

## <a name="syntax"></a>構文

```
struct CCreateContext
```

## <a name="remarks"></a>Remarks

`CCreateContext` 構造体であり、基底クラスではありません。

ウィンドウを作成するときに、この構造体の値は、そのデータのビューに、ドキュメントのコンポーネントを接続するための情報を提供します。 使用しなければ`CCreateContext`作成プロセスの一部をオーバーライドする場合。

A`CCreateContext`構造体には、ドキュメント、フレーム ウィンドウ、ビュー、およびドキュメント テンプレートへのポインターが含まれています。 ポインターも含まれています、`CRuntimeClass`を作成するビューの種類を識別します。 ランタイム クラス情報と現在のドキュメントのポインターは、新しいビューを動的に作成に使用されます。 次の表に、推奨方法とタイミング各`CCreateContext`メンバーを使用する場合があります。

|メンバー|型|何が|
|------------|----------|--------------------|
|`m_pNewViewClass`|`CRuntimeClass*`|`CRuntimeClass` 新しいビューを作成します。|
|`m_pCurrentDoc`|`CDocument*`|新しいビューに関連する既存のドキュメント。|
|`m_pNewDocTemplate`|`CDocTemplate*`|新しい MDI フレーム ウィンドウの作成に関連するドキュメント テンプレート。|
|`m_pLastView`|`CView*`|元のビューでは、する追加のビューは、モデル化、分割ウィンドウのビューの作成や、ドキュメント上の 2 つ目のビューの作成のようにします。|
|`m_pCurrentFrame`|`CFrameWnd*`|フレーム ウィンドウを追加のフレーム ウィンドウは、モデル化、2 つ目のフレーム ウィンドウにドキュメントの作成のようにします。|

格納された情報を検証するドキュメント テンプレートでは、ドキュメントとその関連コンポーネントを作成するとき、`CCreateContext`構造体。 たとえば、存在しないドキュメントのビューを作成できません必要があります。

> [!NOTE]
>  すべてのポインターの`CCreateContext`はオプションであり、`NULL`指定されていないか不明な場合。

`CCreateContext` 下に表示するメンバー関数によって使用される「も参照してください」。 これらをオーバーライドする場合に、特定の情報をこれらの関数の説明についてを参照してください。

次に、いくつかの一般的なガイドラインを示します。

- ウィンドウの作成の引数として渡されるときに`CWnd::Create`、 `CFrameWnd::Create`、および`CFrameWnd::LoadFrame`作成のコンテキストでは、どのような新しいウィンドウへの接続を指定します。 ほとんどの windows では、全体の構造は省略可能、`NULL`ポインターを渡すことができます。

- オーバーライド可能なメンバー関数の場合など、 `CFrameWnd::OnCreateClient`、`CCreateContext`引数は省略可能です。

- メンバー関数の関連するビューでの作成、入力してください、ビューを作成するのに十分な情報。 たとえば、分割ウィンドウで最初に表示に、クラスの情報を表示し、現在のドキュメントを指定する必要があります。

一般に、フレームワークの既定値を使用する場合は無視できます`CCreateContext`します。 高度な変更、Microsoft Foundation Class ライブラリのソース コードまたは VIEWEX など、サンプル プログラムを試行する場合は、するでは説明します。 必要なパラメーターを忘れると、フレームワークのアサーションされ、何を忘れた場合が示されます。

詳細については`CCreateContext`、MFC のサンプルを参照して[VIEWEX](../../overview/visual-cpp-samples.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** afxext.h

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CFrameWnd::Create](../../mfc/reference/cframewnd-class.md#create)<br/>
[CFrameWnd::LoadFrame](../../mfc/reference/cframewnd-class.md#loadframe)<br/>
[CFrameWnd::OnCreateClient](../../mfc/reference/cframewnd-class.md#oncreateclient)<br/>
[CSplitterWnd::Create](../../mfc/reference/csplitterwnd-class.md#create)<br/>
[CSplitterWnd::CreateView](../../mfc/reference/csplitterwnd-class.md#createview)<br/>
[CWnd::Create](../../mfc/reference/cwnd-class.md#create)
