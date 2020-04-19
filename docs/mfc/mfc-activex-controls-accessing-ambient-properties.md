---
title: MFC ActiveX コントロール:アンビエント プロパティへのアクセス
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: 585ec8720a654bbcb728330d70ddb914f2543e41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239740"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC ActiveX コントロール:アンビエント プロパティへのアクセス

この記事では、ActiveX コントロールを使用して、コントロール コンテナーのアンビエント プロパティにアクセスする方法について説明します。

コントロールでは、コンテナーのアンビエント プロパティにアクセスして、コンテナーに関する情報を取得できます。 これらのプロパティは、コンテナーの背景色、かどうか、コンテナーは現在のユーザー モードまたはデザイナー モードなど、コンテナー、および運用上の特性で使用される現在のフォントなどの視覚的特性を公開します。 コントロールの外観と動作が埋め込まれている特定のコンテナーを調整するのにアンビエント プロパティを使用できます。 ただし、コントロールでは、そのコンテナーがすべてのアンビエント プロパティをサポートする必要があります考えないでください。 実際には、一部のコンテナーでは、アンビエント プロパティがまったくサポートしない可能性があります。 アンビエント プロパティがない場合は、コントロールは、適切な既定値を想定してください。

アンビエント プロパティにアクセスするへの呼び出しを行い[COleControl::GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty)します。 この関数は、最初のパラメーター (ファイルとして使用アンビエント プロパティのディスパッチ ID が必要でします。H 定義アンビエント プロパティの一連の標準のディスパッチ Id)。

パラメーター、`GetAmbientProperty`関数は、ディスパッチ ID を想定されるプロパティの種類とメモリへのポインターを示すバリアント型のタグ値を返す必要があります。 このポインターが参照するデータの種類は、バリアントのタグによって異なります。 関数を返します**TRUE**コンテナーにプロパティがサポートしている場合を返します**FALSE**します。

次のコード例は、「ユーザー モードです。」と呼ばれるアンビエント プロパティの値を取得します。 かどうか、プロパティは、コンテナーの既定値ではサポートされません**TRUE**と見なされます。

[!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

便宜上、`COleControl`一般的に使用されるアンビエント プロパティの多くにアクセスし、プロパティが使用できない場合は、適切な既定値を返すヘルパー関数を提供します。 これらのヘルパー関数は次のとおりです。

- [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  呼び出し元が呼び出す必要があります`Release( )`返されるフォント。

- [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)

(いくつかの操作によって、コンテナーの)、アンビエント プロパティの値が変更された場合、`OnAmbientPropertyChanged`コントロールのメンバー関数が呼び出されます。 このような通知を処理するには、このメンバー関数をオーバーライドします。 パラメーターを`OnAmbientPropertyChanged`は影響を受けるアンビエント プロパティのディスパッチ ID です。 このディスパッチ ID の値は、1 つまたは複数のアンビエント プロパティが変更されたことを示す、DISPID_UNKNOWN にありますが、影響を受けたプロパティに関する情報をご利用いただけません。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)
