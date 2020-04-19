---
title: コンパイラ エラー C3862
ms.date: 11/04/2016
f1_keywords:
- C3862
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
ms.openlocfilehash: 2ba130862b1debbe2991ca7cbcae50192f900cd8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62302315"
---
# <a name="compiler-error-c3862"></a>コンパイラ エラー C3862

> '*関数*':/clr でアンマネージ関数をコンパイルすることはできません:/clr:pure または/clr:safe

## <a name="remarks"></a>Remarks

**/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

使用してコンパイル **/clr: 純粋な**または **/clr:safe** MSIL のみイメージなしのネイティブ (アンマネージ) コードを持つイメージが生成されます。  そのため、使用することはできません、`unmanaged`のプラグマを **/clr: 純粋な**または **/clr:safe**コンパイルします。

詳細については、次を参照してください。 [/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)と[マネージ、アンマネージ](../../preprocessor/managed-unmanaged.md)します。

## <a name="example"></a>例

次の例では、C3862 が生成されます。

```cpp
// C3862.cpp
// compile with: /clr:pure /c
#pragma unmanaged
void f() {}   // C3862
```