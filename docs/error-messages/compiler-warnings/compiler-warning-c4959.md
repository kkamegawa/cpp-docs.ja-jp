---
title: コンパイラの警告 C4959
ms.date: 11/04/2016
f1_keywords:
- C4959
helpviewer_keywords:
- C4959
ms.assetid: 3a128f3e-4d8a-4565-ba1a-5d32fdeb5982
ms.openlocfilehash: 646347dec7bc2bac7fa73c8f754d2f9549cb2ba6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388664"
---
# <a name="compiler-warning-c4959"></a>コンパイラの警告 C4959

> アンマネージ構造体を定義できません '*型*'/clr:safe で検証できないコードを生成するそのメンバーにアクセスするため、。

## <a name="remarks"></a>Remarks

アンマネージ型のメンバーにアクセスすると、検証不可能な (peverify.exe) イメージが生成されます。

詳細については、次を参照してください。[純粋で検証可能なコード (C +/cli CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md)します。

**/Clr:safe**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

この警告は、エラーとして表示されます。無効にするには、 [warning](../../preprocessor/warning.md) プラグマ、または [/wd](../../build/reference/compiler-option-warning-level.md) コンパイラ オプションを使用します。

## <a name="example"></a>例

次の例では C4959 が生成されます。

```cpp
// C4959.cpp
// compile with: /clr:safe

// Uncomment the following line to resolve.
// #pragma warning( disable : 4959 )
struct X {
   int data;
};

int main() {
   X x;
   x.data = 10;   // C4959
}
```