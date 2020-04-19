---
title: ATL オブジェクトを作成できないをこと
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.objects
helpviewer_keywords:
- noncreatable ATL objects
- ATL projects, noncreatable objects
ms.assetid: 80d0bca2-dea0-4801-9a85-6243124437f6
ms.openlocfilehash: 5b259a677fdf3013ae1be6073afaf34f76a6e2fd
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221052"
---
# <a name="making-an-atl-object-noncreatable"></a>ATL オブジェクトを作成できないをこと

ATL ベースの COM オブジェクトの属性を変更するには、クライアントからオブジェクトを直接作成することはできませんようにします。 この場合、オブジェクトが別のオブジェクトのメソッドの呼び出しによって返されるのではなく直接作成します。

## <a name="to-make-an-object-noncreatable"></a>オブジェクトを作成できないようにするには

1. 削除、 [OBJECT_ENTRY_AUTO](object-map-macros.md#object_entry_auto)オブジェクト。 Noncreatable が登録するコントロール オブジェクトを実行する場合に、置換と OBJECT_ENTRY_AUTO[役立つ](object-map-macros.md#object_entry_non_createable_ex_auto)します。

1. 追加、 [noncreatable](../../windows/noncreatable.md) .idl ファイルのコクラスの属性します。 例:

    ```
    [uuid(A1992E3D-3CF0-11D0-826F-00A0C90F2851),
    helpstring("MyObject"),
    noncreatable]
    coclass MyObject
    {
        [default] interface IMyInterface;
    }
    ```

## <a name="see-also"></a>関連項目

[ATL プロジェクト ウィザード](../../atl/reference/atl-project-wizard.md)<br/>
[C++Visual Studio でプロジェクトの種類](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL および C ランタイム コードによるプログラミング](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM オブジェクトの基礎](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[ATL プロジェクトの既定の構成](../../atl/reference/default-atl-project-configurations.md)
