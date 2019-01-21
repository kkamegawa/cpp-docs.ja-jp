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
ms.openlocfilehash: 8eb1b93aa55601125600b6c69d9bff3d9ca43aa3
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53626865"
---
# <a name="unaligned"></a>__unaligned

**Microsoft 固有の仕様**します。 マウス ポインターを宣言する場合、 **_ _unaligned**修飾子は、コンパイラはポインターがアラインされていないデータをアドレスします。 その結果、プラットフォームに適したコードでは、アラインされていない読み取りを処理するためが生成され、ポインターを書き込みます。

## <a name="remarks"></a>Remarks

この修飾子はポインターによってアドレス指定されたデータのアラインメントをについて説明しますポインター自体は、配置すると見なされます。

必要性、 **_ _unaligned**キーワードは、プラットフォームおよび環境によって異なります。 エラー データを適切にマークすると、パフォーマンスの低下からハードウェアの障害に至るまでの問題があります。 **_ _Unaligned**修飾子は無効です、x86 プラットフォーム。

以前のバージョンとの互換性のため **_unaligned**のシノニムです **_ _unaligned**しない限り、コンパイラ オプション[/Za\(言語拡張機能を無効にする)](../build/reference/za-ze-disable-language-extensions.md)指定します。

アラインメントの詳細については、次のトピックを参照してください。

- [align](../cpp/align-cpp.md)

- [__alignof 演算子](../cpp/alignof-operator.md)

- [pack](../preprocessor/pack.md)

- [/Zp (構造体メンバーの配置)](../build/reference/zp-struct-member-alignment.md)

- [構造体の配置例](../build/x64-software-conventions.md#examples-of-structure-alignment)

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)