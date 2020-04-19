---
title: 既定のクラス ファクトリと集計モデルの変更
ms.date: 11/04/2016
helpviewer_keywords:
- CComClassFactory class, making the default
- aggregation [C++], using ATL
- aggregation [C++], aggregation models
- defaults [C++], aggregation model in ATL
- default class factory
- class factories, changing default
- CComCoClass class, default class factory and aggregation model
- default class factory, ATL
- defaults [C++], class factory
ms.assetid: 6e040e95-0f38-4839-8a8b-c9800dd47e8c
ms.openlocfilehash: 94f9ecd85e09cb3916b518d71b904961042142e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62223158"
---
# <a name="changing-the-default-class-factory-and-aggregation-model"></a>既定のクラス ファクトリと集計モデルの変更

ATL を使用して[CComCoClass](../atl/reference/ccomcoclass-class.md)オブジェクトの既定のクラス ファクトリと集計モデルを定義します。 `CComCoClass` 次の 2 つのマクロを指定します。

- [DECLARE_CLASSFACTORY](reference/aggregation-and-class-factory-macros.md#declare_classfactory)宣言をクラス ファクトリ[CComClassFactory](../atl/reference/ccomclassfactory-class.md)します。

- [DECLARE_AGGREGATABLE](reference/aggregation-and-class-factory-macros.md#declare_aggregatable)オブジェクトを集計できることを宣言します。

これらの既定値のいずれかのクラスの定義で別のマクロを指定することによってオーバーライドできます。 たとえば、使用する[CComClassFactory2](../atl/reference/ccomclassfactory2-class.md)の代わりに`CComClassFactory`、指定、 [DECLARE_CLASSFACTORY2](reference/aggregation-and-class-factory-macros.md#declare_classfactory2)マクロ。

[!code-cpp[NVC_ATL_COM#2](../atl/codesnippet/cpp/changing-the-default-class-factory-and-aggregation-model_1.h)]

クラス ファクトリを定義するその他の 2 つのマクロは[DECLARE_CLASSFACTORY_AUTO_THREAD](reference/aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)と[DECLARE_CLASSFACTORY_SINGLETON](reference/aggregation-and-class-factory-macros.md#declare_classfactory_singleton)します。

ATL を使用しても、 **typedef**既定の動作を実装するためのメカニズムです。 たとえば、DECLARE_AGGREGATABLE マクロを使用して**typedef**と呼ばれる型を定義する`_CreatorClass`、ATL. 全体で参照されているが、 派生クラスで、 **typedef** 、基本クラスの同じ名前を使用して**typedef** ATL の定義を使用して、既定の動作をオーバーライドする結果します。

## <a name="see-also"></a>関連項目

[ATL COM オブジェクトの基礎](../atl/fundamentals-of-atl-com-objects.md)<br/>
[集計とクラス ファクトリに関するマクロ](../atl/reference/aggregation-and-class-factory-macros.md)
