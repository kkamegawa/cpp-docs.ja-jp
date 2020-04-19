---
title: CComObject、CComAggObject、ccompolyobject の実装
ms.date: 11/04/2016
helpviewer_keywords:
- CComPolyObject class, implementing
- CreateInstance method
- CComAggObject class
- CComObject class, implementing
ms.assetid: 5aabe938-104d-492e-9c41-9f7fb1c62098
ms.openlocfilehash: e2413c8fb9f5722f0245883c947067387838e57f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62261788"
---
# <a name="implementing-ccomobject-ccomaggobject-and-ccompolyobject"></a>CComObject、CComAggObject、ccompolyobject の実装

テンプレート クラス[CComObject](../atl/reference/ccomobject-class.md)、 [CComAggObject](../atl/reference/ccomaggobject-class.md)、および[CComPolyObject](../atl/reference/ccompolyobject-class.md)継承チェーンの最派生クラスでは常にします。 すべてのメソッドで処理する責任が`IUnknown`: `QueryInterface`、 `AddRef`、および`Release`します。 さらに、`CComAggObject`と`CComPolyObject`(集計オブジェクトの使用) する場合、特殊な参照カウントを提供し、`QueryInterface`内部の不明なのために必要なセマンティクスです。

かどうか`CComObject`、 `CComAggObject`、または`CComPolyObject`される以下のマクロの 1 つ (または none) を宣言するかどうかによって異なります。

|マクロ|効果|
|-----------|------------|
|DECLARE_NOT_AGGREGATABLE|常に使用`CComObject`します。|
|DECLARE_AGGREGATABLE|使用して`CComAggObject`集約オブジェクトの場合と`CComObject`でない場合。 `CComCoClass` このマクロを含む場合、DECLARE_ いずれ * _AGGREGATABLE マクロがクラスでは、宣言はこの既定値になります。|
|DECLARE_ONLY_AGGREGATABLE|常に使用`CComAggObject`します。 オブジェクトが集計されない場合は、エラーを返します。|
|DECLARE_POLY_AGGREGATABLE|ATL のインスタンスを作成する**CComPolyObject\<CYourClass >** とき`IClassFactory::CreateInstance`が呼び出されます。 作成時に、不明な外部の値がチェックされます。 NULL の場合`IUnknown`の非集計オブジェクトに実装されます。 不明な外部が NULL でない場合`IUnknown`集約オブジェクトに実装されます。|

使用する利点`CComAggObject`と`CComObject`の実装は`IUnknown`作成されるオブジェクトの種類は最適化されています。 たとえば、非集計オブジェクトだけで済みます、参照カウントを集計オブジェクトには、内部の不明な参照カウントと不明な外部へのポインターの両方が必要があります。

使用する利点`CComPolyObject`は両方を持つように`CComAggObject`と`CComObject`集計データおよび非集計のケースを処理するモジュールでします。 1 つ`CComPolyObject`オブジェクトは両方のケースを処理します。 つまり、モジュールで、vtable の 1 つだけのコピーと、関数の 1 つのコピーが存在します。 Vtable が大きい場合、モジュールのサイズが大幅に減りこのことができます。 ただし、vtable が小さい場合を使用して`CComPolyObject`には、集計または非集約オブジェクトは、最適化されていないために、モジュールのサイズを少し大きめにつながるは`CComAggObject`と`CComObject`します。

## <a name="see-also"></a>関連項目

[ATL COM オブジェクトの基礎](../atl/fundamentals-of-atl-com-objects.md)<br/>
[集計とクラス ファクトリに関するマクロ](../atl/reference/aggregation-and-class-factory-macros.md)
