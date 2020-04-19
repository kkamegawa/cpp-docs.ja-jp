---
title: __alignof 演算子
ms.date: 12/17/2018
f1_keywords:
- alignas_cpp
- __alignof_cpp
- alignof_cpp
- __alignof
- _alignof
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
ms.openlocfilehash: 96c85db83c133af6f1712baa8597ed3360277854
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258253"
---
# <a name="__alignof-operator"></a>__alignof 演算子

C++ 11 で、 **alignof**演算子を指定した型のバイト単位で、配置を返します。 移植性を最大にするため、Microsoft 固有の __alignof 演算子ではなく、alignof 演算子を使用してください。

**Microsoft 固有の仕様**

型の値を返します`size_t`型のアラインメント要件であります。

## <a name="syntax"></a>構文

```cpp
  __alignof( type )
```

## <a name="remarks"></a>Remarks

例:

|正規表現|[値]|
|----------------|-----------|
|**__alignof( char )**|1|
|**__alignof( short )**|2|
|**__alignof( int )**|4|
|**__alignof( \__int64 )**|8|
|**__alignof( float )**|4|
|**__alignof( double )**|8|
|**__alignof( char\* )**|4|

**_ _alignof**値は、の値として同じ`sizeof`の基本型。 ただし、次の例を検討します。

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

ここで、 **_ _alignof**値は、構造内の最大の要素のアラインメント要件。

同様に、

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` と `32` が等価です。

用途の 1 つ **_ _alignof**独自のメモリ割り当てルーチンのいずれかのパラメーターとしてになります。 たとえば、次の定義済みの構造体 `S` を指定して、`aligned_malloc` という名前のメモリ割り当てルーチンを呼び出し、特定の配置境界にメモリを割り当てることができます。

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

以前のバージョンとの互換性のため **_alignof**のシノニムです **_ _alignof**しない限り、コンパイラ オプション[/Za\(言語拡張機能を無効にする)](../build/reference/za-ze-disable-language-extensions.md)は指定します。

配置の変更の詳細については、次を参照してください。

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp (構造体メンバーの配置)](../build/reference/zp-struct-member-alignment.md)

- [構造体の配置例](../build/x64-software-conventions.md#examples-of-structure-alignment)(x64 固有)

x86 と x64 用のコード内の配置の違いの詳細については、

- [x86 コンパイラとの競合](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[単項演算子を含む式](../cpp/expressions-with-unary-operators.md)<br/>
[キーワード](../cpp/keywords-cpp.md)