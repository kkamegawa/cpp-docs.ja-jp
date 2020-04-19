---
title: キャスト
ms.date: 11/19/2018
helpviewer_keywords:
- casting [C++]
- coercion [C++]
- virtual functions [C++], in derived classes [C++]
- static cast operator
- dynamic cast operator
- polymorphic classes [C++]
- classes [C++], polymorphism
ms.assetid: 3dbeb06e-2f4b-4693-832d-624bc8ec95de
ms.openlocfilehash: 02ade663ee92d3a301fda95bb385c3ffa48ead12
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345071"
---
# <a name="casting"></a>キャスト

C++ 言語では、仮想関数を含む基底クラスからクラスが派生している場合は、その基底クラスの型へのポインターを使用して、派生クラス オブジェクトに存在する仮想関数の実装を呼び出すことができると規定されています。 仮想関数を含むクラスは、"ポリモーフィックなクラス" と呼ばれます。

派生クラスには派生元のすべての基底クラスの定義が完全に含まれるため、ポインターをクラスの階層構造の任意の基底クラスにキャストしても、安全です。 基底クラスへのポインターの場合は、下の階層にポインターを安全にキャストできる場合もあります。 ポイントされているオブジェクトが実際に基底クラスから派生した型である場合は、安全です。 この場合、実際のオブジェクトは "完全なオブジェクト" と呼ばれます。 基底クラスへのポインターは完全なオブジェクトの "サブオブジェクト" をポイントすると表現されます。 たとえば、次の図に示すクラスの階層構造を考えます。

![クラス階層](../cpp/media/vc38zz1.gif "クラス階層") <br/>
クラスの階層構造

`C` 型のオブジェクトは、次の図に示すように視覚化できます。

![Sub を持つクラス C&#45;オブジェクト B と A](../cpp/media/vc38zz2.gif "sub 持つクラス C&#45;オブジェクト B と A") <br/>
B サブオブジェクトと A サブオブジェクトを持つクラス C

`C` クラスのインスタンスには、`B` サブオブジェクトと `A` サブオブジェクトがあります。 `C` サブオブジェクトと `A` サブオブジェクトを含む `B` のインスタンスは、「完全なオブジェクト」です。

実行時の型情報を使用すると、ポインターが実際に完全なオブジェクトをポイントしていて、階層内の別のオブジェクトをポイントするように安全にキャストできるかどうかを調べることができます。 [Dynamic_cast](../cpp/dynamic-cast-operator.md)演算子は、これらの型のキャストを使用できます。 また、操作を安全にするために必要なランタイム チェックも実行します。

非ポリモーフィックな型の変換で使用することができます、 [static_cast](../cpp/static-cast-operator.md)演算子 (このトピックには、各を使用する適切なタイミングと、静的および動的なキャスト変換の間の差がについて説明します)。

ここでは、次のトピックについて説明します。

- [キャスト演算子](../cpp/casting-operators.md)

- [実行時の型情報](../cpp/run-time-type-information.md)

## <a name="see-also"></a>関連項目

[式](../cpp/expressions-cpp.md)