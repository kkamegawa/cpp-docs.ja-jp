---
title: キャスト演算子
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: e2ac8e9079b1d30dca077363bbb6cef35960902e
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345096"
---
# <a name="casting-operators"></a>キャスト演算子

C++ 言語には、固有のキャスト演算子がいくつかあります。 これらの演算子は、以前のスタイルの C 言語のキャストが持つあいまいさと危険性の一部を取り除くことを目的としています。 このような演算子を次に示します。

- [dynamic_cast](../cpp/dynamic-cast-operator.md)ポリモーフィックな型の変換に使用します。

- [static_cast](../cpp/static-cast-operator.md)非ポリモーフィックな型の変換に使用します。

- [const_cast](../cpp/const-cast-operator.md) を削除するために使用、 **const**、**volatile**、および **__unaligned**属性。

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md)ビットの単純な再解釈に使用します。

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md)で使用されるC++/CLI 検証可能な MSIL を生成するためにします。

使用**const_cast**と**reinterpret_cast**これらの演算子は、古いスタイルのキャストと同じ危険性を提示するので、最後の手段として。 それでも、これらは、以前のスタイルのキャストを完全に置き換えるために必要です。

## <a name="see-also"></a>関連項目

[キャスト](../cpp/casting.md)