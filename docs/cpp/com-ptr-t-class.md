---
title: _com_ptr_t クラス
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t
helpviewer_keywords:
- _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
ms.openlocfilehash: ce19dbc5f55460bb4bdbdee17f4fbbbcc8c6fd60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154904"
---
# <a name="comptrt-class"></a>_com_ptr_t クラス

**Microsoft 固有の仕様**

A **_com_ptr_t**オブジェクトは COM インターフェイス ポインターをカプセル化し、「スマート」ポインターと呼びます。 このテンプレート クラスは管理リソースの割り当てと割り当て解除関数の呼び出しを通じて、`IUnknown`メンバー関数: `QueryInterface`、 `AddRef`、および`Release`します。

スマート ポインターは通常、_COM_SMARTPTR_TYPEDEF マクロによって提供される typedef 定義で参照されます。 このマクロが、インターフェイス名と IID を受け取りの特殊化を宣言します **_com_ptr_t**インターフェイスのサフィックスの名前を持つ`Ptr`します。 例えば:

```cpp
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));
```

宣言、 **_com_ptr_t**特殊化`IMyInterfacePtr`します。

一連の[関数テンプレート](../cpp/relational-function-templates.md)、このテンプレートのメンバー以外のクラス、比較演算子の右側にあるスマート ポインターと比較をサポートします。

### <a name="construction"></a>構築

|||
|-|-|
|[_com_ptr_t](../cpp/com-ptr-t-com-ptr-t.md)|構築、 **_com_ptr_t**オブジェクト。|

### <a name="low-level-operations"></a>低水準操作

|||
|-|-|
|[AddRef](../cpp/com-ptr-t-addref.md)|呼び出し、`AddRef`のメンバー関数`IUnknown`カプセル化されたインターフェイス ポインター。|
|[Attach](../cpp/com-ptr-t-attach.md)|このスマート ポインターの型の生のインターフェイス ポインターをカプセル化します。|
|[CreateInstance](../cpp/com-ptr-t-createinstance.md)|指定したオブジェクトの新しいインスタンスを作成、`CLSID`または`ProgID`します。|
|[Detach](../cpp/com-ptr-t-detach.md)|カプセル化されたインターフェイス ポインターを抽出して返します。|
|[GetActiveObject](../cpp/com-ptr-t-getactiveobject.md)|指定したオブジェクトの既存のインスタンスにアタッチ、`CLSID`または`ProgID`します。|
|[GetInterfacePtr](../cpp/com-ptr-t-getinterfaceptr.md)|カプセル化されたインターフェイス ポインターを返します。|
|[QueryInterface](../cpp/com-ptr-t-queryinterface.md)|呼び出し、`QueryInterface`のメンバー関数`IUnknown`カプセル化されたインターフェイス ポインター。|
|[Release](../cpp/com-ptr-t-release.md)|呼び出し、`Release`のメンバー関数`IUnknown`カプセル化されたインターフェイス ポインター。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator=](../cpp/com-ptr-t-operator-equal.md)|既存の新しい値を割り当てます **_com_ptr_t**オブジェクト。|
|[演算子 = =、! =、 \<、>、 \<=、> =](../cpp/com-ptr-t-relational-operators.md)|別のスマート ポインター、生のインターフェイス ポインターの場合は、スマート ポインター オブジェクトを比較または NULL。|
|[エクス トラクター](../cpp/com-ptr-t-extractors.md)|カプセル化された COM インターフェイス ポインターを抽出します。|

**Microsoft 固有の仕様はここまで**

## <a name="requirements"></a>必要条件

**ヘッダー:** \<comip.h >

**Lib:** comsuppw.lib または comsuppwd.lib (詳細は「[/Zc:wchar_t (wchar_t をネイティブ型として認識)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)」を参照してください)

## <a name="see-also"></a>関連項目

[コンパイラ COM サポート クラス](../cpp/compiler-com-support-classes.md)