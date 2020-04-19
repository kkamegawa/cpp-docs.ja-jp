---
title: コンパイラの警告 (レベル 4) C4714
ms.date: 11/04/2016
f1_keywords:
- C4714
helpviewer_keywords:
- C4714
ms.assetid: 22c7fd0c-899d-4e9b-95f3-725b2c49fb46
ms.openlocfilehash: 8ea4212eaddf14546827728b31299063021a959f
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74989638"
---
# <a name="compiler-warning-level-4-c4714"></a>コンパイラの警告 (レベル 4) C4714

関数 ' function ' はインライン __forceinline としてマークされていません

指定された関数はインライン展開のために選択されましたが、コンパイラはインライン展開を実行しませんでした。

`__forceinline` は `__inline`よりもコンパイラの方が強力ですが、インライン展開はコンパイラの裁量で実行されますが、この関数をインライン展開する利点を判断するためのヒューリスティックは使用されません。

場合によっては、コンパイラが特定の関数を機械的にインライン化することはありません。 たとえば、コンパイラはインラインになりません。

- SEH とC++ EH の両方を混在させる場合の関数。

- コピーによって作成されたオブジェクトを含む一部の関数は、-GX/EHs/Ehs がオンのときに値によって渡されます。

- -GX/EHs/Ehs が on の場合、値によって unwindable オブジェクトを返す関数。

- -Og/を使用せずにコンパイルするときにインラインアセンブリを使用する関数。

- 可変個引数リストを持つ関数。

- **Try** (C++ exception 処理) ステートメントを含む関数。

次の例では、C4714 が生成されます。

```cpp
// C4714.cpp
// compile with: /Ob1 /GX /W4
__forceinline void func1()
{
   try
   {
   }
   catch (...)
   {
   }
}

void func2()
{
   func1();   // C4714
}

int main()
{
}
```
