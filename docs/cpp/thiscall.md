---
title: __thiscall
ms.date: 11/04/2016
f1_keywords:
- __thiscall
- __thiscall_cpp
helpviewer_keywords:
- __thiscall keyword [C++]
ms.assetid: a6a22dd2-0101-4885-b33b-22f6057965df
ms.openlocfilehash: e51879ae62b2881e0adadbe59859605f6cc58947
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221914"
---
# <a name="__thiscall"></a>__thiscall

**Microsoft 固有の仕様**

**_ _Thiscall**呼び出し規約はメンバー関数で使用し、呼び出し規約を使用して既定値は、C++メンバー関数を可変個の引数を使用しないでください。 **_ _Thiscall**、呼び出し先のことはできませんが、スタックを消去する`vararg`関数。 右から左への引数をスタックにプッシュは、**this**ポインター レジスタ ECX、および、x86 上で、スタックに渡されるアーキテクチャ。

使用する理由の 1 つ **_ _thiscall**クラス メンバー関数が使用されて`__clrcall`既定。 使用する場合、 **_ _thiscall**個々 のメンバーの関数をネイティブ コードから呼び出すことにします。

コンパイルするときに[/clr: 純粋な](../build/reference/clr-common-language-runtime-compilation.md)、すべての関数および関数ポインターは`__clrcall`それ以外の場合に指定されていない場合。 **/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

Visual Studio 2005 では、以前のリリースで、 **_ _thiscall**呼び出し規約がいない明示的に指定するプログラムでは、ため **_ _thiscall**がキーワードではありません。

`vararg` メンバー関数の使用、 **_ _cdecl**呼び出し規約。 すべての関数の引数はで、スタックにプッシュされます、**this**ポインターはスタックに最後に配置

この呼び出し規則は C++ だけに適用されるため、C の名前の装飾スキームはありません。

ARM と x64 マシン **_ _thiscall**が受け入れられるし、コンパイラによって無視されます。

静的でないクラス関数がアウトオブラインで宣言されている場合、アウトオブラインの宣言で呼び出し規則の修飾子を指定する必要はありません。 つまり、クラスの静的でないメンバー メソッドの場合は、宣言時に指定された呼び出し規則が定義の時点で仮定されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[引数の渡し規則と名前付け規則](../cpp/argument-passing-and-naming-conventions.md)