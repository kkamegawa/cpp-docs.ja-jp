---
title: 引数の渡し規則と名前付け規則
ms.date: 12/17/2018
helpviewer_keywords:
- argument passing [C++], conventions
- arguments [C++], widening
- coding conventions, arguments
- arguments [C++], passing
- registers, return values
- thiscall keyword [C++]
- naming conventions [C++], arguments
- arguments [C++], naming
- passing arguments [C++], conventions
- conventions [C++], argument names
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
ms.openlocfilehash: ca09d31d3d8d50ca94543c5e02262edd7b2deefc
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627242"
---
# <a name="argument-passing-and-naming-conventions"></a>引数の渡し規則と名前付け規則

**Microsoft 固有の仕様**

Visual C++ コンパイラでは、関数と呼び出し元の間の、引数と戻り値の受け渡しに関する規約を指定することができます。 サポートされるすべてのプラットフォームですべての規約がサポートされるわけではありません。また、一部の規約は、プラットフォーム固有の実装を使用します。 ほとんどの場合、特定のプラットフォームでサポートされていない規約を指定するキーワードやコンパイラ スイッチは無視され、プラットフォームの既定の規約が使用されます。

x86 プラットフォームでは、すべての引数は渡されたときに 32 ビットに拡大変換されます。 EDX:EAX レジスタ ペアに返される 8 バイトの構造体を除き、戻り値も 32 ビットに拡張され、EAX レジスタに返されます。 より大きな構造体は、非表示の戻り値の構造体へのポインターとして EAX レジスタに返されます。 パラメーターは、スタックに右から左へプッシュされます。 POD ではない構造体はレジスタ内では返されません。

コンパイラは、関数で ESI、EDI、EBX、および EBP レジスタが使用されている場合、それらを保存および復元するためにプロローグ コードとエピローグ コードを生成します。

> [!NOTE]
> 構造体、共用体、またはクラスが値渡しで関数から戻される場合は、型のすべての定義が同じである必要があります。そうでないと、実行時にプログラムが失敗することがあります。

独自の関数プロローグおよびエピローグ コードを定義する方法については、次を参照してください。 [Naked 関数の呼び出し](../cpp/naked-function-calls.md)します。

ターゲットが x64 プラットフォームでは、「コードで呼び出し規則については、既定[x64 呼び出し規則](../build/x64-calling-convention.md)します。 ARM プラットフォームを対象とするコードの呼び出し規約の問題については、次を参照してください。[一般的な Visual c ARM の移行に関する問題](../build/common-visual-cpp-arm-migration-issues.md)します。

次の呼び出し規則は Visual C/C++ コンパイラでサポートされます。

|キーワード|スタック クリーンアップ|パラメーター渡し|
|-------------|-------------------|-----------------------|
|[__cdecl](../cpp/cdecl.md)|Caller|パラメーターをスタックに逆の順序で (右から左に) プッシュする|
|[__clrcall](../cpp/clrcall.md)|N/A|CLR 式スタックに順に (左から右に) パラメーターを読み込む|
|[__stdcall](../cpp/stdcall.md)|Callee|パラメーターをスタックに逆の順序で (右から左に) プッシュする|
|[__fastcall](../cpp/fastcall.md)|Callee|レジスタに格納されてから、スタックにプッシュされる|
|[__thiscall](../cpp/thiscall.md)|Callee|スタックにプッシュされます。**この**ECX に格納されているポインター|
|[__vectorcall](../cpp/vectorcall.md)|Callee|レジスタに格納されてから、スタックに逆の順序で (右から左に) プッシュされる|

関連情報については、次を参照してください。[廃止された呼び出し規則](../cpp/obsolete-calling-conventions.md)します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[呼び出し規約](../cpp/calling-conventions.md)