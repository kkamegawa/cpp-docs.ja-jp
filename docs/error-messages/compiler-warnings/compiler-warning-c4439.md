---
title: コンパイラの警告 C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: 7cab2e55fca640438051fbb79ac933e83d5f3cbb
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73623658"
---
# <a name="compiler-warning-c4439"></a>コンパイラの警告 C4439

' function ': シグネチャのマネージ型を持つ関数定義には、__clrcall 呼び出し規約が必要です

コンパイラは、呼び出し規約を[__clrcall](../../cpp/clrcall.md)に暗黙的に置き換えました。 この警告を解決するには、`__cdecl` または `__stdcall` 呼び出し規約を削除します。

C4439 は常にエラーとして発行されます。 この警告は、`#pragma warning` または **/wd**で無効にすることができます。詳細については、「 [warning](../../preprocessor/warning.md)または[/w、/W0、/W1、/W2、/W3、/W4、/W1、/W2、](../../build/reference/compiler-option-warning-level.md) /W3、/W4、/Wall、/wd、/we、/WO、/Wv、/wx (警告レベル)」を参照してください。

## <a name="example"></a>例

次の例では、C4439 が生成されます。

```cpp
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```