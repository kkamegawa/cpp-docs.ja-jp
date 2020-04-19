---
title: 含まれている Windows を使用します。
ms.date: 11/04/2016
helpviewer_keywords:
- ATL, windows
- windows [C++], ATL
- contained windows in ATL
ms.assetid: 7b3d79e5-b569-413f-9b98-df4f14efbe2b
ms.openlocfilehash: 2b9a36c6aac80a7c77cde102d6da93c51788e4e1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198604"
---
# <a name="using-contained-windows"></a>含まれている Windows を使用します。

ATL に含まれているウィンドウを実装する[CContainedWindowT](../atl/reference/ccontainedwindowt-class.md)します。 コンテナー内のウィンドウでは、そのメッセージを独自のクラスで処理することではなく、コンテナー オブジェクトをデリゲートするウィンドウを表します。

> [!NOTE]
>  クラスを派生する必要はありません`CContainedWindowT`含まれているウィンドウを使用するためにします。

含まれているウィンドウは、既存の Windows クラスまたは既存のウィンドウをサブクラス化に、いずれかのスーパークラスをできます。 ウィンドウをスーパークラス化する既存の Windows を作成するクラスで、最初のコンス トラクターで、既存のクラス名を指定、`CContainedWindowT`オブジェクト。 呼び出して`CContainedWindowT::Create`します。 既存のウィンドウをサブクラス化は、Windows のクラス名 (コンス トラクターに渡す NULL) を指定する必要はありません。 呼び出すだけで、`CContainedWindowT::SubclassWindow`サブクラス化されているウィンドウを識別するハンドルを持つメソッド。

通常、コンテナー クラスのデータ メンバーとして含まれているウィンドウを使用します。 コンテナーはウィンドウ以外である必要はありません。ただしから派生させる必要があります[CMessageMap](../atl/reference/cmessagemap-class.md)します。

コンテナー内のウィンドウでは、そのメッセージを処理するのに別のメッセージ マップを使用できます。 を 1 つ以上含まれているウィンドウがある場合は、いくつかの別のコンテナー内のウィンドウに対応するそれぞれのメッセージ マップを宣言する必要があります。

## <a name="example"></a>例

2 つ含まれているウィンドウを持つコンテナー クラスの例を次に示します。

[!code-cpp[NVC_ATL_Windowing#67](../atl/codesnippet/cpp/using-contained-windows_1.h)]

含まれているウィンドウの詳細については、次を参照してください。、 [SUBEDIT](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/SubEdit)サンプル。

## <a name="see-also"></a>関連項目

[ウィンドウ クラス](../atl/atl-window-classes.md)
