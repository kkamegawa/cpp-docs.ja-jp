---
title: コンパイラの警告 (レベル 4) C4266
ms.date: 11/04/2016
f1_keywords:
- C4266
helpviewer_keywords:
- C4266
ms.assetid: 90ec5f5b-3451-4c16-bb1b-c30a626bdaa0
ms.openlocfilehash: eeca693e03751245d9b031d6f64751f0372bbb69
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991347"
---
# <a name="compiler-warning-level-4-c4266"></a>コンパイラの警告 (レベル 4) C4266

' function ': ベース ' type ' から仮想メンバー関数に使用できるオーバーライドはありません。関数は非表示です

派生クラスは、仮想関数のすべてのオーバーロードをオーバーライドしませんでした。

既定では、この警告はオフに設定されています。  詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

次の例では、C4266 が生成されます。

```cpp
// C4266.cpp
// compile with: /W4 /c
#pragma warning (default : 4266)
class Engine {
public:
   virtual void OnException(int&,int);
   virtual void OnException(int&,int&,int);
};

class LocalBinding : private Engine {
   virtual void OnException(int&,int);
};   // C4266
```

解決方法:

```cpp
// C4266b.cpp
// compile with: /W4 /c
#pragma warning (default : 4266)
class Engine {
public:
   virtual void OnException(int&,int);
   virtual void OnException(int&,int&,int);
};

class LocalBinding : private Engine {
   virtual void OnException(int&,int);
   virtual void OnException(int&, int&, int);
};
```
