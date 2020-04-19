---
title: ダブル サンキング (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- double thunks
- interop [C++], double thunking
- mixed assemblies [C++], double thunking
- /clr compiler option [C++], double thunking
- interoperability [C++], double thunking
ms.assetid: a85090b2-dc3c-498a-b40c-340db229dd6f
ms.openlocfilehash: f34af20ed3dd2c48659bdbf7794c443920dbb4e9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404482"
---
# <a name="double-thunking-c"></a>ダブル サンキング (C++)

ダブル サンキングは、Visual C マネージ関数とプログラム実行は、マネージ コンテキスト呼び出し内の関数呼び出しはマネージ関数を呼び出すために、関数のネイティブ エントリ ポイントを呼び出すときに発生することがパフォーマンスの低下を指します。 このトピックでは、ダブル サンキングが発生して、パフォーマンスを向上させることを回避する方法について説明します。

## <a name="remarks"></a>Remarks

使用してコンパイルした場合、既定 **/clr**、マネージ エントリ ポイントと、ネイティブ エントリ ポイントを生成するコンパイラがマネージ関数の定義。 これにより、マネージ関数をネイティブおよびマネージ呼び出しサイトから呼び出すことができます。 ただし、ネイティブ エントリ ポイントが存在する場合は、関数の呼び出しのすべてのエントリ ポイントをすることができます。 呼び出し元の関数が管理されている場合、ネイティブ エントリ ポイントは、マネージ エントリ ポイントを呼び出します。 実際には、2 つの呼び出しは、関数の呼び出しに必要な (したがって、ダブル サンキング)。 たとえば、仮想関数は常にネイティブ エントリ ポイントを介して呼び出されます。

1 つの解決、関数を使用して、管理対象のコンテキストからのみ呼び出されることをマネージ関数のネイティブ エントリ ポイントを生成しないようにコンパイラに指示するには、 [_ _clrcall](../cpp/clrcall.md)呼び出し規約。

同様に、エクスポートする場合 ([dllexport、dllimport](../cpp/dllexport-dllimport.md)) マネージ関数では、ネイティブ エントリ ポイントは生成され、インポートし、その関数を呼び出す関数はネイティブ エントリ ポイントを呼び出します。 このような状況でダブル サンキングを避けるため、使用しないネイティブのエクスポート/インポート セマンティクスです。使用してメタデータを参照するだけ`#using`(を参照してください[#using ディレクティブ](../preprocessor/hash-using-directive-cpp.md))。

ダブル サンキングの不要なため、コンパイラが更新されました。 たとえば、(戻り値の型を含む) のシグネチャのマネージド型の関数は暗黙的としてマークされます`__clrcall`します。

## <a name="example"></a>例

### <a name="description"></a>説明

次の例では、ダブル サンキングを示します。 ネイティブのコンパイル時に (せず **/clr**)、仮想関数への呼び出し`main`に 1 回の呼び出しが生成されます`T`のコンス トラクターとデストラクターの呼び出しを 1 つをコピーします。 仮想関数を宣言するときに同様の動作は実現 **/clr**と`__clrcall`します。 ただし、指定してコンパイル **/clr**、関数呼び出しには、コピー コンス トラクターの呼び出しが生成されますが、別の呼び出しをネイティブからマネージ サンクにより、コピー コンス トラクターがあります。

### <a name="code"></a>コード

```
// double_thunking.cpp
// compile with: /clr
#include <stdio.h>
struct T {
   T() {
      puts(__FUNCSIG__);
   }

   T(const T&) {
      puts(__FUNCSIG__);
   }

   ~T() {
      puts(__FUNCSIG__);
   }

   T& operator=(const T&) {
      puts(__FUNCSIG__);
      return *this;
   }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;

   printf("calling struct S\n");
   pS->f(t);
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>出力例

```
__thiscall T::T(void)
calling struct S
__thiscall T::T(const struct T &)
__thiscall T::T(const struct T &)
__thiscall T::~T(void)
__thiscall T::~T(void)
after calling struct S
__thiscall T::~T(void)
```

## <a name="example"></a>例

### <a name="description"></a>説明

前のサンプルには、ダブル サンキングの存在が示されています。 このサンプルでは、その効果を示します。 `for`ループは、仮想関数とプログラムのレポートの実行時間を呼び出します。 プログラムがコンパイルされるときに時間が最も遅いが報告された **/clr**します。 なしでコンパイル時に最短時間を報告 **/clr**と仮想関数が宣言されている場合、または`__clrcall`します。

### <a name="code"></a>コード

```
// double_thunking_2.cpp
// compile with: /clr
#include <time.h>
#include <stdio.h>

#pragma unmanaged
struct T {
   T() {}
   T(const T&) {}
   ~T() {}
   T& operator=(const T&) { return *this; }
};

struct S {
   virtual void /* __clrcall */ f(T t) {};
} s;

int main() {
   S* pS = &s;
   T t;
   clock_t start, finish;
   double  duration;
   start = clock();

   for ( int i = 0 ; i < 1000000 ; i++ )
      pS->f(t);

   finish = clock();
   duration = (double)(finish - start) / (CLOCKS_PER_SEC);
   printf( "%2.1f seconds\n", duration );
   printf("after calling struct S\n");
}
```

### <a name="sample-output"></a>出力例

```
4.2 seconds
after calling struct S
```

## <a name="see-also"></a>関連項目

[混在 (ネイティブおよびマネージド) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)
