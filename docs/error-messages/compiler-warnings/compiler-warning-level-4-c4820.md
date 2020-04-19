---
title: コンパイラの警告 (レベル 4) C4820
ms.date: 11/04/2016
f1_keywords:
- C4820
helpviewer_keywords:
- C4820
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
ms.openlocfilehash: ac97a943e6a8178e930d93a097071b0e3da09773
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989054"
---
# <a name="compiler-warning-level-4-c4820"></a>コンパイラの警告 (レベル 4) C4820

'バイト' : 'バイト' バイトのパディングを 'コンスラクト' 'member_name' の後に追加しました。

要素の型と順序により、コンパイラは構造体の末尾にパディングを追加しました。 構造体の埋め込みの詳細については、「 [align](../../cpp/align-cpp.md) 」を参照してください。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

次の例では、C4820 が生成されます。

```cpp
// C4820.cpp
// compile with: /W4 /c
#pragma warning(default : 4820)

// Delete the following 4 lines to resolve.
__declspec(align(2)) struct MyStruct {
   char a;
   int i;   // C4820
};

// OK
#pragma pack(1)
__declspec(align(1)) struct MyStruct2 {
   char a;
   int i;
};
```
