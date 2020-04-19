---
title: コンパイラの警告 (レベル 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: 042eab1c125f2b98fd36257dfd8971262015ab92
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990680"
---
# <a name="compiler-warning-level-4-c4564"></a>コンパイラの警告 (レベル 4) C4564

クラス ' class ' のメソッド ' method ' で、サポートされていない既定のパラメーター ' parameter ' が定義されています

コンパイラは、既定値を持つ1つ以上のパラメーターを持つメソッドを検出しました。 パラメーターの既定値は、メソッドが呼び出されるときに無視されます。これらのパラメーターの値を明示的に指定します。 これらのパラメーターの値を明示的に指定しなかっC++た場合は、コンパイラによってエラーが生成されます。

次の .dll を Visual Basic で作成した場合、メソッドの引数に既定のパラメーターを使用できます。

```vb
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

次C++の例では、Visual Basic で作成された .dll を使用しています。

```cpp
// C4564.cpp
// compile with: /clr /W4 /WX
#using <C4564.dll>

int main() {
   TestClass ^ myx = gcnew TestClass();   // C4564
   myx->MyMethod(9);
   // try the following line instead, to avoid an error
   // myx->MyMethod(9, 1);
}
```
