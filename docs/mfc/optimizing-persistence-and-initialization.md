---
title: 永続化と初期化の最適化
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- optimizing performance, ActiveX controls
ms.assetid: e821e19e-b9eb-49ab-b719-0743420ba80b
ms.openlocfilehash: 294d9c43f5f767329c04932c574485d7dca704e9
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342129"
---
# <a name="optimizing-persistence-and-initialization"></a>永続化と初期化の最適化

既定では、によって永続化とコントロールの初期化を処理します。、`DoPropExchange`メンバー関数。 この関数には、一般的なコントロールには、いくつかの呼び出しが含まれています**px _** 関数 (`PX_Color`、`PX_Font`など) の各プロパティのいずれか。

この方法の利点を 1 つ`DoPropExchange`初期化、バイナリ形式で永続化およびいくつかのコンテナーで使用される、いわゆる「プロパティ バッグ」形式で永続化の実装を使用できます。 この 1 つの関数は、プロパティと 1 か所で既定値に関するすべての情報を提供します。

ただし、この効率は低下します。 **Px _** 関数取得マルチレイヤーの実装では、本質的にでは柔軟性がより直接的が、柔軟性のアプローチよりも効率的です。 さらに、コントロールに既定値を渡す場合、 **px _** 関数は、既定値にする必要があります、既定値が必ずしも使用がいない場合であっても、毎回が提供することです。 場合、既定値を生成する、重要なタスク (たとえば、値がアンビエント プロパティから取得したとき)、追加、不要な処理は既定値が使用されていない場合に行われます。

コントロールのオーバーライドすることで、コントロールのバイナリの永続化のパフォーマンスを向上できます`Serialize`関数。 このメンバー関数の既定の実装への呼び出し、`DoPropExchange`関数。 これをオーバーライドすることでは、バイナリの持続性のより直接的な実装を行うことができます。 たとえば、このことを検討`DoPropExchange`関数。

[!code-cpp[NVC_MFC_AxOpt#1](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_1.cpp)]

このコントロールのバイナリの永続化のパフォーマンスを向上させるのには、オーバーライド、`Serialize`次のように機能します。

[!code-cpp[NVC_MFC_AxOpt#2](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_2.cpp)]

`dwVersion`ローカル変数は、バージョン コントロールの永続的な状態の読み込みまたは保存を検出するために使用することができます。 この変数を使用して、呼び出す代わりに[CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion)します。

永続的な形式で、小さい領域を保存する、 **BOOL**プロパティ (、によって生成される形式との互換性を保つ`PX_Bool`)、としてプロパティを格納することができます、**バイト**、次のように。

[!code-cpp[NVC_MFC_AxOpt#3](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_3.cpp)]

キャストするのではなく、負荷の場合、一時変数の使用をし、その値が割り当てられている、 *m_boolProp*を**バイト**参照。 キャストの手法の 1 バイトだけになる*m_boolProp*変更される、初期化されていない残りのバイトします。

同じコントロールの場合は、オーバーライドすることでコントロールの初期化を最適化できます[COleControl::OnResetState](../mfc/reference/colecontrol-class.md#onresetstate)次のようにします。

[!code-cpp[NVC_MFC_AxOpt#4](../mfc/codesnippet/cpp/optimizing-persistence-and-initialization_4.cpp)]

`Serialize`と`OnResetState`オーバーライドされている、`DoPropExchange`関数おく必要があるそのままプロパティ バッグ形式で永続化をまだ使用されています。 どの永続性に関係なく、コンテナーのメカニズムを使用してのコントロールがそのプロパティを一貫した管理することを確認するこれらの関数の 3 つすべてを維持するために重要です。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール: 最適化](../mfc/mfc-activex-controls-optimization.md)
