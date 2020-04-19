---
title: コンパイラの警告 (レベル 3) C4398
ms.date: 11/04/2016
f1_keywords:
- C4398
helpviewer_keywords:
- C4398
ms.assetid: b6221432-9fed-4272-a547-a73f587904e6
ms.openlocfilehash: 4126a1267b41cdf9c0161c7e85a9057b2a301d77
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401970"
---
# <a name="compiler-warning-level-3-c4398"></a>コンパイラの警告 (レベル 3) C4398

> '*変数*': プロセスごとのグローバル オブジェクトは複数の appdomain と共に動作しない可能性があります、__declspec(appdomain) を使用してみてください。

## <a name="remarks"></a>Remarks

仮想関数と[_ _clrcall](../../cpp/clrcall.md)の作成をネイティブ型で規則を呼び出すと、アプリケーション ドメインの vtable ごと。 複数のアプリケーション ドメインで使用する場合は、このような変数が適切に修正されない場合があります。

この警告を解決するには、変数を明示的にマークすることによって`__declspec(appdomain)`します。 Visual Studio 2017 の前に Visual Studio のバージョンでは、この警告を解決でコンパイルする **/clr: 純粋な**、appdomain ごとのグローバル変数は既定では、これです。 **/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。

詳細については、次を参照してください。 [appdomain](../../cpp/appdomain.md)と[アプリケーション ドメインと Visual c](../../dotnet/application-domains-and-visual-cpp.md)します。

## <a name="example"></a>例

次の例では、C4398 が生成されます。

```cpp
// C4398.cpp
// compile with: /clr /W3 /c
struct S {
   virtual void f( System::String ^ );   // String^ parameter makes function __clrcall
};

S glob_s;   // C4398
__declspec(appdomain) S glob_s2;   // OK
```