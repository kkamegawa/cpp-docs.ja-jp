---
title: コンパイラ エラー C2370
ms.date: 11/04/2016
f1_keywords:
- C2370
helpviewer_keywords:
- C2370
ms.assetid: 03403e8f-f393-47c4-bd25-5c1c7ea7d5cd
ms.openlocfilehash: ab7b19799925f9aa02f67ffdbec181628391e495
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745656"
---
# <a name="compiler-error-c2370"></a>コンパイラ エラー C2370

'identifier' : 再定義 ; 異なるストレージ クラスです。

識別子は、異なるストレージ クラスで既に宣言されています。

## <a name="example"></a>使用例

次の例では C2370 が生成されます。

```cpp
// C2370.cpp
// compile with: /Za /c
extern int i;
static int i;   // C2370
int i;   // OK
```

## <a name="example"></a>使用例

次の例では C2370 が生成されます。

```cpp
// C2370b.cpp
#define Thread __declspec( thread )
extern int tls_i;
int Thread tls_i;   // C2370 declaration and the definition differ
int tls_i;   // OK
```
