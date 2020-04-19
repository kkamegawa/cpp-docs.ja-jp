---
title: 継承 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
ms.openlocfilehash: 0180a2f7b41e3169bc9e25d8b598dbe2b84be088
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184581"
---
# <a name="inheritance--c"></a>継承 (C++)

このセクションでは、派生クラスを使用して拡張可能プログラムを生成する方法について説明します。

## <a name="overview"></a>概要

新しいクラスを「継承」というメカニズムを使用して既存のクラスから派生させることができます (始まる情報を参照してください。[単一継承](../cpp/single-inheritance.md))。 派生に使用されるクラスは、特定の派生クラスの "基底クラス" と呼ばれます。 派生クラスは、次の構文を使用して宣言します。

```cpp
class Derived : [virtual] [access-specifier] Base
{
   // member list
};
class Derived : [virtual] [access-specifier] Base1,
   [virtual] [access-specifier] Base2, . . .
{
   // member list
};
```

クラスのタグ (名前) の後ろにコロンを指定し、その後ろに基本指定のリストが続きます。  したがって、基底クラスは、あらかじめ宣言しておく必要があります。  基本仕様は、キーワードのいずれかである、アクセス指定子を含めることができます**public**、**protected**または**private**します。  これらのアクセス指定子は、基底クラス名の前に指定され、その基底クラスにのみ適用されます。  これらの指定子は、派生クラスで基底クラスのメンバーに対して使用されるアクセス許可を制御します。  参照してください[メンバー アクセス コントロール](../cpp/member-access-control-cpp.md)基底クラス メンバーへのアクセスについて。  アクセス指定子を省略すると、その基底クラスへのアクセスと見なされます**private**します。  基本仕様は、キーワードを含めることができます**virtual**仮想継承を示します。  このキーワードがある場合は、アクセス指定子の前または後に指定されます。  仮想継承を使用する場合、基底クラスは、仮想基底クラスと呼ばれます。

複数の基底クラスをコンマで区切って指定できます。  継承モデルは、1 つの基本クラスが指定されている場合[単一継承](../cpp/single-inheritance.md)します。1 つ以上の基底クラスを指定すると、継承モデルが呼び出されます[多重継承](../cpp/multiple-base-classes.md)します。

ここでは、次のトピックについて説明します。

- [単一継承](../cpp/single-inheritance.md)

- [複数の基底クラス](../cpp/multiple-base-classes.md)

- [仮想関数](../cpp/virtual-functions.md)

- [明示的なオーバーライド](../cpp/explicit-overrides-cpp.md)

- [抽象クラス](../cpp/abstract-classes-cpp.md)

- [スコープ規則の概要](../cpp/summary-of-scope-rules.md)

[_ _Super](../cpp/super.md)と[_ _interface](../cpp/interface.md)キーワードがここに記載されています。

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)