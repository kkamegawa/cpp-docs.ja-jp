---
title: __unaligned
ms.date: 12/17/2018
f1_keywords:
- __unaligned_cpp
- __unaligned
- _unaligned
helpviewer_keywords:
- __unaligned keyword [C++]
ms.assetid: 0cd83aad-1840-47e3-ad33-59bfcbe6375b
ms.openlocfilehash: 1090a0f3345f749a2afbd80566a9af7b9ea32d53
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857256"
---
# <a name="__unaligned"></a>__unaligned

**Microsoft 固有**。 **__Unaligned**修飾子を使用してポインターを宣言すると、コンパイラは、アラインされていないデータをポインターが指すと見なします。 その結果、プラットフォームに適したコードが生成され、ポインターを介して、整列されていない読み取りと書き込みが処理されます。

## <a name="remarks"></a>Remarks

この修飾子は、ポインターによってアドレス指定されるデータの配置を表します。ポインター自体は、固定されていると見なされます。

**__Unaligned**キーワードの必要性は、プラットフォームと環境によって異なります。 データを適切にマークしないと、パフォーマンスの低下からハードウェア障害まで、問題が発生する可能性があります。 **__Unaligned**修飾子は、x86 プラットフォームでは無効です。

以前のバージョンとの互換性のために、コンパイラオプション[/za \(無効になっている言語拡張)](../build/reference/za-ze-disable-language-extensions.md)が指定されていない場合、 **_unaligned**は **__unaligned**のシノニムになります。

アラインメントの詳細については、次のトピックを参照してください。

- [align](../cpp/align-cpp.md)

- [__alignof 演算子](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (構造体メンバーの配置)](../build/reference/zp-struct-member-alignment.md)

- [構造体の配置例](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>参照

[キーワード](../cpp/keywords-cpp.md)