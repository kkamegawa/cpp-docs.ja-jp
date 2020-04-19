---
title: コンパイラ エラー C3904
ms.date: 11/04/2016
f1_keywords:
- C3904
helpviewer_keywords:
- C3904
ms.assetid: 08297605-e4f2-4c6c-b637-011f1fd40631
ms.openlocfilehash: 1861810f4598fa81d1b7662a57651b1648de1317
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749049"
---
# <a name="compiler-error-c3904"></a>コンパイラ エラー C3904

' property_accessor ': 数値パラメーターを指定しなければなりません

`get` のパラメーターの数を確認し、プロパティディメンションに対してメソッドを `set` します。

- `get` メソッドのパラメーターの数は、プロパティの次元数と同じであるか、インデックスが設定されていないプロパティの場合は0である必要があります。

- `set` メソッドのパラメーターの数は、プロパティの次元数より1つ多くする必要があります。

詳細については、「 [property](../../extensions/property-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3904 が生成されます。

```cpp
// C3904.cpp
// compile with: /clr /c
ref class X {
   property int P {
      // set
      void set();   // C3904
      // try the following line instead
      // void set(int);

      // get
      int get(int, int);   // C3904
      // try the following line instead
      // int get();
   };
};
```

## <a name="example"></a>使用例

次の例では、C3904 が生成されます。

```cpp
// C3904b.cpp
// compile with: /clr /c
ref struct X {
   property int Q[double, double, float, float, void*, int] {
      // set
      void set(double, void*);   // C3904
      // try the following line instead
      // void set(double, double, float, float, void*, int, int);

      // get
      int get();   // C3904
      // try the following line instead
      // int get(double, double, float, float, void*, int);
   }
};
```
