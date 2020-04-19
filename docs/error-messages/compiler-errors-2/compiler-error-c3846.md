---
title: コンパイラ エラー C3846
ms.date: 11/04/2016
f1_keywords:
- C3846
helpviewer_keywords:
- C3846
ms.assetid: c470f8a5-106b-4efb-b8dc-e1319e04130f
ms.openlocfilehash: a4c51ccfc724cf8309044812b287677f0f1a2ff0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754902"
---
# <a name="compiler-error-c3846"></a>コンパイラ エラー C3846

' symbol ': ' assembly2 ' からシンボルをインポートできません: ' symbol ' は既に別のアセンブリ ' assembly1 ' からインポートされています

参照されたアセンブリからシンボルをインポートできませんでした。このシンボルは、参照アセンブリから既にインポートされています。

## <a name="example"></a>使用例

次の例では、C3846 が生成されます。

```cpp
// C3846a.cpp
// compile with: /LD /clr
public ref struct G
{
};
```

その後、次のようにコンパイルします。

```cpp
// C3846b.cpp
// compile with: /clr
#using "c3846a.dll"
#using "c3846a.obj"   // C3846

int main()
{
}
```
