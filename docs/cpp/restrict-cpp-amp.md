---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 3609e3f0541cfd8a8af8559d8d49e6a77c00d91c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403387"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

制限指定子は、関数宣言およびラムダ宣言に適用できます。 制限は、関数のコードに適用され、また、C++ Accelerated Massive Parallelism (C++ AMP) ランタイムを使用するアプリケーションの関数の動作に適用されます。

> [!NOTE]
>  については、**restrict**キーワードの一部である、 **__declspec**ストレージ クラス属性を参照してください[restrict](../cpp/restrict.md)します。

**restrict**句では、次の種類。

|句|説明|
|------------|-----------------|
|`restrict(cpu)`|関数は C++ 言語をフルに使用できます。 restrict (cpu) 関数を使用して宣言された他の関数だけがこの関数を呼び出すことができます。|
|`restrict(amp)`|関数は C++ AMP で高速化できる C++ 言語のサブセットのみを使用できます。|
|連続した `restrict(cpu)` と `restrict(amp)`|関数は `restrict(cpu)` と `restrict(amp)` の両方の制約に従う必要があります。 関数は `restrict(cpu)`、`restrict(amp)`、`restrict(cpu, amp)`、または `restrict(amp, cpu)` を使用して宣言した関数から呼び出すことができます。<br /><br /> `restrict(A) restrict(B)` という形式は `restrict(A,B)` と書くことができます。|

## <a name="remarks"></a>Remarks

**restrict**キーワードは、コンテキスト キーワードです。 制限指定子の `cpu` と `amp` は予約語ではありません。 指定子の数を増やすことはできません。 ない関数、**restrict**句がある関数と同じ、`restrict(cpu)`句。

`restrict(amp)` 句を持つ関数には次の制限があります。

- 関数は `restrict(amp)` 句を持つ関数のみを呼び出すことができます。

- 関数はインライン化できる必要があります。

- 関数でのみ宣言できます**int**、**unsigned int**、 **float**、および**double**変数、およびクラスおよびのみを含む構造体これらの型。 **bool**も許可する必要があります 4 バイト境界、複合型で使用する場合。

- ラムダ関数は、参照によってキャプチャできず、また、ポインターをキャプチャできません。

- 参照と単一間接ポインターは、ローカル変数、関数の引数、戻り値の型としてのみサポートされています。

- 以下は使用できません。

   - 再帰

   - [volatile](../cpp/volatile-cpp.md)キーワードで宣言された変数。

   - 仮想関数

   - 関数へのポインター

   - メンバー関数へのポインター

   - 構造体へのポインター

   - ポインターへのポインター

   - **goto**ステートメント

   - ラベル付きステートメント

   - **try**、**catch**、または**throw**ステートメント

   - グローバル変数

   - 静的変数 [tile_static キーワード](../cpp/tile-static-keyword.md)代わりに使用します。

   - **dynamic_cast**キャスト

   - **Typeid**演算子

   - asm 宣言

   - 可変個引数

関数の制限事項の詳細については、次を参照してください。 [restrict（amp）制限](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/)します。

## <a name="example"></a>例

次の例は、使用する方法を示します、`restrict(amp)`句。

```cpp
void functionAmp() restrict(amp) {}
void functionNonAmp() {}

void callFunctions() restrict(amp)
{
    // int is allowed.
    int x;
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.
    // long long int y;

    // Calling an amp-restricted function is allowed.
    functionAmp();

    // Calling a non-amp-restricted function is not allowed.
    // functionNonAmp();
}
```

## <a name="see-also"></a>関連項目

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)
