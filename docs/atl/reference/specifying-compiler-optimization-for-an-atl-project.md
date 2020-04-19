---
title: ATL プロジェクトのコンパイラ最適化の指定
ms.date: 08/19/2019
f1_keywords:
- vc.appwiz.ATL.optimization
- vc.appwiz.ATL.vtable
helpviewer_keywords:
- ATL_DISABLE_NO_VTABLE macro
- ATL projects, compiler optimization
- ATL_NO_VTABLE macro
ms.assetid: 7f379318-66d5-43dd-a53d-530758d3a228
ms.openlocfilehash: c3b00823cb33be952451c3cc9e370c99140acc3c
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630613"
---
# <a name="specifying-compiler-optimization-for-an-atl-project"></a>ATL プロジェクトのコンパイラ最適化の指定

既定では、 [ATL コントロールウィザード](../../atl/reference/atl-control-wizard.md)では、次のように ATL_NO_VTABLE マクロを使用して新しいクラスが生成されます。

```
class ATL_NO_VTABLE CProjName
{
...
};
```

ATL では、次のように _ATL_NO_VTABLE を定義します。

```
#ifdef _ATL_DISABLE_NO_VTABLE
#define ATL_NO_VTABLE
#else
#define ATL_NO_VTABLE __declspec(novtable)
#endif
```

_ATL_DISABLE_NO_VTABLE を定義しない場合、ATL_NO_VTABLE マクロはに`declspec(novtable)`展開されます。 クラス`declspec(novtable)`宣言でを使用すると、vtable ポインターがクラスコンストラクターとデストラクターで初期化されるのを防ぐことができます。 プロジェクトをビルドすると、vtable が指す vtable とすべての関数がリンカーによって除去されます。

ATL_NO_VTABLE を使用する必要があり`declspec(novtable)`、その結果、直接作成できない基本クラスのみを使用する必要があります。 このクラス (通常`declspec(novtable)`は[CComObject](../../atl/reference/ccomobject-class.md)、 [CComAggObject](../../atl/reference/ccomaggobject-class.md)、または[CComPolyObject](../../atl/reference/ccompolyobject-class.md)) がプロジェクトの vtable ポインターを初期化するため、プロジェクト内で最も派生クラスでを使用することはできません。

を使用`declspec(novtable)`するすべてのオブジェクトのコンストラクターから仮想関数を呼び出すことはできません。 これらの呼び出しは、 [FinalConstruct](ccomobjectrootex-class.md#finalconstruct)メソッドに移動する必要があります。

`declspec(novtable)`修飾子を使用する必要があるかどうかわからない場合は、任意のクラス定義から ATL_NO_VTABLE マクロを削除するか、を指定してグローバルに無効にすることができます。

```
#define _ATL_DISABLE_NO_VTABLE
```

*.pch* (Visual Studio 2017 以前の場合は*stdafx.h* ) で、他のすべての ATL ヘッダーファイルが含まれる前。

## <a name="see-also"></a>関連項目

[ATL プロジェクト ウィザード](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio の C++ プロジェクトの種類](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL および C ランタイム コードによるプログラミング](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[ATL COM オブジェクトの基礎](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[novtable](../../cpp/novtable.md)<br/>
[ATL プロジェクトの既定の構成](../../atl/reference/default-atl-project-configurations.md)
