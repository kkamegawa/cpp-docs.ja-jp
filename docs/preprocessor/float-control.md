---
title: float_control プラグマ
description: Float_control プラグマディレクティブの使用法と効果について説明します。 Float_control ディレクティブは、実行時の浮動小数点の正確なセマンティクスと例外セマンティクスの状態を制御します。
ms.date: 11/18/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 5f907bfeb3f92f788fe951854ddc32accc83ae03
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78166785"
---
# <a name="float_control-pragma"></a>float_control プラグマ

関数の浮動小数点動作を指定します。

## <a name="syntax"></a>構文

> **#pragma float_control**\
> **#pragma float_control (正確、** { **on** | **off** } **[, push]** **)** \
> **#pragma float_control (except、** { **on** | **off** } **[, push]** **)** \
> **#pragma float_control (** { **push** | **pop** } **)**

## <a name="options"></a>オプション

**正確**、**オン** | **オフ**、**プッシュ**\
正確な浮動小数点セマンティクスを有効 (**on**) または無効 (**オフ**) にするかどうかを指定します。 **/Fp: 精密**コンパイラオプションとの違いについては、「解説」を参照してください。 オプションの**push**トークンは、 **float_control**の現在の設定を内部コンパイラスタックにプッシュします。

**except**、 **on** | **off**、 **push**\
浮動小数点例外セマンティクスを有効 (**on**) または無効 (**オフ**) にするかどうかを指定します。 オプションの**push**トークンは、 **float_control**の現在の設定を内部コンパイラスタックにプッシュします。

**except**は on にも設定**されて** **いる場合に**のみ **、on に**設定できます。

**プッシュ**\
現在の**float_control**設定を内部コンパイラスタックにプッシュします。

**pop**\
内部コンパイラスタックの一番上から**float_control**設定を削除し、新しい**float_control**設定を行います。

## <a name="remarks"></a>解説

**Float_control**プラグマには、 [/fp](../build/reference/fp-specify-floating-point-behavior.md)コンパイラオプションと同じ動作はありません。 **Float_control**プラグマは、浮動小数点動作の一部のみを制御します。 **/Fp**コンパイラオプションを再作成するには、 [fp_contract](../preprocessor/fp-contract.md)および[fenv_access](../preprocessor/fenv-access.md)プラグマと組み合わせる必要があります。 次の表は、各コンパイラオプションの同等のプラグマ設定を示しています。

| | float_control (正確、\*) | float_control (except、\*) | fp_contract (\*) | fenv_access (\*) |
|-|-|-|-|-|
| /fp: strict             | on  | on  | オフ | on  |
| /fp: 正確            | on  | オフ | on  | オフ |
| /fp: fast               | オフ | オフ | on  | オフ |

言い換えると、複数のプラグマを組み合わせて使用して、 **/fp: fast**、 **/fp: 精密**、および **/fp: strict**の各コマンドラインオプションをエミュレートすることが必要になる場合があります。

**Float_control**と**fenv_access**浮動小数点プラグマを組み合わせて使用する方法には、次のような制限があります。

- 正確なセマンティクスが有効になっている場合は、 **float_control**のみを使用し**てを on** **に設定でき**ます。 正確なセマンティクスを有効にするには、 **float_control**プラグマを使用するか、 **/fp: 精密**または **/fp: strict**コンパイラオプションを使用します。

- **Float_control**プラグマまたは **/fp: except**コンパイラオプションによって例外のセマンティクスが有効になっている場合に、 **float_control**を使用して**正確**にオフにすることはできません。

- **Float_control**プラグマまたはコンパイラオプションによって、正確なセマンティクスが有効になっている場合を除き、 **fenv_access**を有効にすることはできません。

- **Fenv_access**を有効にすると、 **float_control**を使用して**正確**にオフにすることはできません。

これらの制限は、一部の浮動小数点プラグマの順序が重要であることを意味します。 プラグマを使用して高速モデルから厳密なモデルに移行するには、次のコードを使用します。

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

**Float_control**プラグマを使用して厳密なモデルから高速モデルに移行するには、次のコードを使用します。

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // enable contractions
```

オプションが指定されていない場合、 **float_control**は効果がありません。

## <a name="example"></a>例

次の例は、プラグマ**float_control**を使用して、オーバーフロー浮動小数点例外をキャッチする方法を示しています。

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>参照

[プラグマディレクティブと __pragma キーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[fenv_access](../preprocessor/fenv-access.md)\
[fp_contract](../preprocessor/fp-contract.md)
