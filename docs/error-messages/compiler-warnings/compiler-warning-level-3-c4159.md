---
title: コンパイラの警告 (レベル 3) C4159
ms.date: 11/04/2016
f1_keywords:
- C4159
helpviewer_keywords:
- C4159
ms.assetid: e2cf964e-f4b8-4b2c-9569-1abb94307232
ms.openlocfilehash: e898af8f109ed23bd1784df7b39c174bbed675f2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402282"
---
# <a name="compiler-warning-level-3-c4159"></a>コンパイラの警告 (レベル 3) C4159

> #<a name="pragma-pragmapop--has-popped-previously-pushed-identifier-identifier"></a>プラグマ pragma(pop,...): 以前にプッシュされた識別子がポップ '*識別子*'

## <a name="remarks"></a>Remarks

ソース コードに含まれる、**プッシュ**プラグマの識別子で命令が続く、 **pop**識別子のない命令。 その結果、*識別子*の表示された場合は、以降の使用は、*識別子*予期しない動作が発生する可能性があります。

## <a name="example"></a>例

この警告を回避するで識別子を指定、 **pop**命令。 例:

```cpp
// C4159.cpp
// compile with: /W3
#pragma pack(push, f)
#pragma pack(pop)   // C4159

// using the identifier resolves the warning
// #pragma pack(pop, f)

int main()
{
}
```