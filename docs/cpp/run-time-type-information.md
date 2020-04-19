---
title: ランタイム型情報
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- RTTI compiler option
- run-time type information
- run time, type checking
- type information, run-time type checking
- run-time checks, type checking
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
ms.openlocfilehash: 1d11ee3ea472f935120c59f0faefee905361ee97
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267403"
---
# <a name="run-time-type-information"></a>ランタイム型情報

実行時型情報 (RTTI: Run-Time Type Information) は、プログラムの実行中にオブジェクトの型を決定するための機能です。 クラス ライブラリの多くのベンダーがこの機能を独自に実装していたことから、RTTI が C++ 言語に追加されましたが、 これによってライブラリの間に非互換性が発生しました。 したがって、実行時型情報を言語レベルでサポートする必要があります。

RTTI についてわかりやすく説明するため、ここでは対象をポインターに限定しています。 ただし、ここで説明する概念は参照にも適用されます。

C++ 言語には、実行時型情報を扱う 3 つの主要要素があります。

- [Dynamic_cast](../cpp/dynamic-cast-operator.md)演算子。

   ポリモーフィック型を変換します。

- [Typeid](../cpp/typeid-operator.md)演算子。

   オブジェクトの正確な型を特定します。

- [Type_info](../cpp/type-info-class.md)クラス。

   によって返される型情報を保持するために使用される、 **typeid**演算子。

## <a name="see-also"></a>関連項目

[キャスト](../cpp/casting.md)