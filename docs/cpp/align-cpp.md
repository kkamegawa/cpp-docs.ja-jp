---
title: align (C++)
ms.date: 12/17/2018
f1_keywords:
- align_cpp
helpviewer_keywords:
- align __declspec keyword
- __declspec keyword [C++], align
ms.assetid: 9cb63f58-658b-4425-ac47-af8eabfc5878
ms.openlocfilehash: 1bfe6e7a4646be8cea622078b4d85f20f458e1c5
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627333"
---
# <a name="align-c"></a>align (C++)

Visual Studio 2015 以降では、c++ 11 標準を使用して、`alignas`コントロールの配置を指定子。 詳細については、次を参照してください。[配置](../cpp/alignment-cpp-declarations.md)します。

**Microsoft 固有の仕様**

ユーザー定義データ (関数の静的割り当てや自動データなど) のアラインメントを正確に制御するには、`__declspec(align(#))` を使用します。

## <a name="syntax"></a>構文

> **__declspec( align(** *#* **) )** *declarator*

## <a name="remarks"></a>Remarks

最新のプロセッサ命令を使用するアプリケーションの記述では、いくつかの新しい制約や問題があります。 特に、多くの新しい命令では、データを 16 バイト境界にアラインする必要があります。 また、頻繁に使用されるデータを特定のプロセッサのキャッシュ ラインのサイズにアラインすることで、キャッシュ パフォーマンスが向上します。 たとえば、サイズが 32 バイト未満の構造体を定義する場合、その構造体型のオブジェクトが効率的にキャッシュされるように、その構造体を 32 バイトにアラインできます。

\# アラインメント値です。 有効なエントリは、1 ～ 8192 (バイト) の 2 の整数乗 (2、4、8、16、32、64 など) です。 `declarator` は、aligned として宣言するデータです。

型の値を返す方法については`size_t`型のアラインメント要件を参照してください[_ _alignof](../cpp/alignof-operator.md)します。 64 ビット プロセッサを対象とするときにアラインされていないポインターを宣言する方法については、次を参照してください。 [_ _unaligned](../cpp/unaligned.md)します。

使用することができます`__declspec(align(#))`を定義するとき、**構造体**、**共用体**、または**クラス**変数を宣言する場合またはします。

コンパイラは、コピーまたはデータ変換の処理中に、データのアラインメント属性の保持を保証したり、保持しようとしません。 たとえば、 [memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)で宣言された構造体をコピーできます`__declspec(align(#))`任意の場所にします。 通常に注意してくださいアロケーター — たとえば、 [malloc](../c-runtime-library/reference/malloc.md)、C++ [new 演算子](new-operator-cpp.md)、および Win32 アロケーター — は通常、適切にアラインされないのメモリを返す`__declspec(align(#))`構造体や配列の構造体。 コピーまたはデータの変換操作のコピー先が正しく整列されていることを保証するには使用[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)、または独自のアロケーターを記述します。

関数パラメーターのアラインメントは指定できません。 アラインメント属性を持つデータがスタック上で値によって渡されるときに、そのアラインメントは呼び出し規約によって制御されます。 呼び出された関数でデータのアラインメントが重要な場合は、使用する前にパラメーターを正常にアラインされたメモリにコピーします。

せず`__declspec(align(#))`コンパイラは一般にターゲット プロセッサと最大で 32 ビットのプロセッサで 4 バイト境界、データのサイズに基づいて、自然な境界と 64 ビット プロセッサ、8 バイト境界上のデータを配置します。 クラスまたは構造体のデータは、自然なアラインメントと現在のパッキング設定 (#pragma `pack` または `/Zp` コンパイラ オプションから) のうちの最小値でクラスまたは構造体内でアラインされます。

`__declspec(align(#))` を使用する例を次に示します。

```cpp
__declspec(align(32)) struct Str1{
   int a, b, c, d, e;
};
```

この型には、32 バイト アラインメント属性が設定されました。 これは、すべての静的および自動インスタンスが 32 バイト境界で開始されることを意味します。 この種類のメンバーとして宣言されている追加の構造体の型がこの型のアラインメント属性を保持する、構造体は、`Str1`ように、少なくとも 32 のアラインメント属性を持つ要素。

`sizeof(struct Str1)` が 32 と等しいことに注意してください。 このため、Str1 オブジェクトの配列が作成されて、配列のベース アドレスが 32 バイトでアラインされる場合、配列の各メンバーも 32 バイトでアラインされます。 動的メモリでは、ベースが正しくアラインされた配列を作成するには、使用[_aligned_malloc](../c-runtime-library/reference/aligned-malloc.md)、または独自のアロケーターを記述します。

構造体の `sizeof` 値は、最後のメンバーのオフセットにメンバーのサイズを加え、最大サイズのメンバーのアラインメント値の倍数か、構造体全体のアラインメント値のどちらか大きい方に切り上げた値です。

コンパイラは、構造体のアラインメントにこれらの規則を使用します。

- `__declspec(align(#))` でオーバーライドしない限り、スカラー構造体のメンバーのアラインメントは、そのサイズと現在のパッキング設定の最小値になります。

- `__declspec(align(#))` でオーバーライドされない限り、構造体のアラインメントは、そのメンバーの個々のアラインメントの最大値になります。

- 構造体のメンバーが配置される、親の構造体の先頭からのオフセットは、アラインメントの最小倍数であり、かつ前のメンバーの最後のオフセットに等しいかそれよりも大きくなります。

- 構造体のサイズは、アラインメントの最小倍数であり、かつ最後のメンバーの最後のオフセットに等しいかそれよりも大きくなります。

`__declspec(align(#))` では、単にアラインメントの制限が多くなることがあります。

詳細については次を参照してください:

- [align の例](#vclrfalignexamples)

- [__Declspec(align(#)) と新しい型を定義します。](#vclrf_declspecaligntypedef)

- [スレッド ローカル ストレージにデータの整列](#vclrfthreadlocalstorageallocation)

- [Align のデータのパッキングでの動作](#vclrfhowalignworkswithdatapacking)

- [構造体の配置例](../build/x64-software-conventions.md#examples-of-structure-alignment)(x64 固有)

## <a name="vclrfalignexamples"></a> align の例

次の例では、`__declspec(align(#))` がデータ構造体のサイズとアラインメントにどのような影響を与えるかを示します。 この例では、次の定義を前提とします。

```cpp
#define CACHE_LINE  32
#define CACHE_ALIGN __declspec(align(CACHE_LINE))
```

次の例では、`S1` 構造体は `__declspec(align(32))` を使用して定義されます。 変数定義または他の型宣言で `S1` を使用すると、すべて 32 バイトでアラインされます。 `sizeof(struct S1)` は 32 を返し、`S1` では 4 つの整数の保持に必要な 16 バイトの後に 16 バイトのパディングが挿入されます。 各**int**メンバーには、4 バイトのアラインメントが必要ですが、構造体自体のアラインメントは 32 として宣言されています。 そのため、全体的なアラインメントは 32 になります。

```cpp
struct CACHE_ALIGN S1 { // cache align all instances of S1
   int a, b, c, d;
};
struct S1 s1;   // s1 is 32-byte cache aligned
```

次の例では、`sizeof(struct S2)` は 16 を返します。これはメンバーのサイズの合計と一致します。この値が最大アラインメント要件の倍数 (8 の倍数) になっているためです。

```cpp
__declspec(align(8)) struct S2 {
   int a, b, c, d;
};
```

次の例では、`sizeof(struct S3)` は 64 を返します。

```cpp
struct S3 {
   struct S1 s1;   // S3 inherits cache alignment requirement
                  // from S1 declaration
   int a;         // a is now cache aligned because of s1
                  // 28 bytes of trailing padding
};
```

次の例では、`a` で自然なアラインメントが行われる (この場合は 4 バイトにアラインされる) ことに注意してください。 ただし、`S1` は 32 バイトでアラインする必要があります。 `a` がオフセット 32 で開始するように、`s1` の次の 28 バイトがパディングされます。 次に、`S4` は `S1` のアラインメント要件を継承します。そのアラインメントが構造体に必要な最大アラインメントであるためです。 `sizeof(struct S4)` は 64 を返します。

```cpp
struct S4 {
   int a;
   // 28 bytes padding
    struct S1 s1;      // S4 inherits cache alignment requirement of S1
};
```

次の 3 つの変数宣言も `__declspec(align(#))` を使用します。 それぞれの場合で、変数は 32 バイトでアラインする必要があります。 配列の場合、配列の各メンバーではなく、配列のベース アドレスが 32 バイトでアラインされます。 配列の各メンバーの `sizeof` 値は `__declspec(align(#))` の使用による影響を受けません。

```cpp
CACHE_ALIGN int i;
CACHE_ALIGN int array[128];
CACHE_ALIGN struct s2 s;
```

配列の各メンバーをアラインするには、次のようなコードを使用する必要があります。

```cpp
typedef CACHE_ALIGN struct { int a; } S5;
S5 array[10];
```

次の例では、構造体自体のアラインメントと最初の要素のアラインメントによる影響が同じであることに注意してください。

```cpp
CACHE_ALIGN struct S6 {
   int a;
   int b;
};

struct S7 {
   CACHE_ALIGN int a;
               int b;
};
```

`S6` と `S7` では、アラインメント、割り当て、サイズの属性が同じです。

次の例では、a、b、c、および d の開始アドレスのアラインメントは、それぞれ 4、1、4、および 1 です。

```cpp
void fn() {
   int a;
   char b;
   long c;
   char d[10]
}
```

メモリがヒープ上に割り当てられる場合のアラインメントは、どの割り当て関数が呼び出されるかによって異なります。  たとえば、`malloc` を使用する場合、結果はオペランドのサイズによって決まります。 場合*arg* > = 8、8 バイトでアラインするが、メモリが返されます。 場合*arg* < 8、返されるメモリのアラインメントは、最初の 2 の累乗より小さい*arg*します。 たとえば、malloc(7) を使用すると、アラインメントは 4 バイトになります。

## <a name="vclrf_declspecaligntypedef"></a> __Declspec(align(#)) と新しい型を定義します。

型のアラインメントを定義できます。

たとえば、定義、`struct`のアラインメント値このように。

```cpp
struct aType {int a; int b;};
typedef __declspec(align(32)) struct aType bType;
```

ここで、`aType`と`bType`は同じサイズ (8 バイト) が型の変数`bType`32 バイトでアラインされます。

## <a name="vclrfthreadlocalstorageallocation"></a> スレッド ローカル ストレージにデータの整列

`__declspec(thread)` 属性を使用して作成され、イメージ内の TLS セクションに配置された静的なスレッド ローカル ストレージ (TLS: Thread-Local Storage) は、通常の静的データとまったく同じようにアラインメントされます。 TLS データを作成するために、オペレーティング システムは、TLS セクションのサイズのメモリを割り当て、TLS セクションのアラインメント属性に従います。

次の例では、アラインされたデータをスレッド ローカル ストレージに配置するさまざまな方法を示します。

```cpp
// put an aligned integer in TLS
__declspec(thread) __declspec(align(32)) int a;

// define an aligned structure and put a variable of the struct type
// into TLS
__declspec(thread) __declspec(align(32)) struct F1 { int a; int b; } a;

// create an aligned structure
struct CACHE_ALIGN S9 {
   int a;
   int b;
};
// put a variable of the structure type into TLS
__declspec(thread) struct S9 a;
```

## <a name="vclrfhowalignworkswithdatapacking"></a> Align のデータのパッキングでの動作

`/Zp`コンパイラ オプションおよび`pack`プラグマ構造体と共用体のメンバーのデータ パッキングの効果があります。この例ではどのように`/Zp`と`__declspec(align(#))`連携。

```cpp
struct S {
   char a;
   short b;
   double c;
   CACHE_ALIGN double d;
   char e;
   double f;
};
```

次の表に、さまざまな `/Zp` (または #pragma `pack`) 値での各メンバーのオフセットと共に、それらの値とオフセットの関係を示します。

|変数|/Zp1|/Zp2|/Zp4|/Zp8|
|--------------|-----------|-----------|-----------|-----------|
|a|0|0|0|0|
|b|1|2|2|2|
|c|3|4|4|8|
|d|32|32|32|32|
|e|40|40|40|40|
|f|41|42|44|48|
|sizeof(S)|64|64|64|64|

詳細については、「[/Zp (構造体メンバーの配置)](../build/reference/zp-struct-member-alignment.md)」を参照してください。

オブジェクトのオフセットは、前のオブジェクトのオフセットと現在のパッキング設定に基づきます。ただし、オブジェクトに `__declspec(align(#))` 属性が設定されていない場合です。その場合は、アラインメントは前のオブジェクトのオフセットとオブジェクトの `__declspec(align(#))` 値に基づきます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__declspec](../cpp/declspec.md)<br/>
[ARM ABI 規則の概要](../build/overview-of-arm-abi-conventions.md)<br/>
[x64 ソフトウェア規約](../build/x64-software-conventions.md)