---
title: コンパイラの警告 (レベル 1) C4917
ms.date: 11/04/2016
f1_keywords:
- C4917
helpviewer_keywords:
- C4917
ms.assetid: c05e2610-4a5d-4f4b-a99b-c15fd7f1d5f1
ms.openlocfilehash: 97f6f0a08c8ef292d81471cb5d0d94e359466933
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393494"
---
# <a name="compiler-warning-level-1-c4917"></a>コンパイラの警告 (レベル 1) C4917

'declarator': GUID はクラス、インターフェイスまたは名前空間に関連付けできます。

ユーザー定義構造体以外の[クラス](../../cpp/class-cpp.md)、[インターフェイス](../../cpp/interface.md)、または[名前空間](../../cpp/namespaces-cpp.md)GUID を含めることはできません。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

## <a name="example"></a>例

次のコード サンプルでは、C4917 が生成されます。

```cpp
// C4917.cpp
// compile with: /W1
#pragma warning(default : 4917)
__declspec(uuid("00000000-0000-0000-0000-000000000001")) struct S
{
} s;   // C4917, don't put uuid on a struct

int main()
{
}
```