---
title: コンパイラの警告 (レベル 1) C4743
ms.date: 05/13/2019
f1_keywords:
- C4743
helpviewer_keywords:
- C4743
ms.assetid: 2ee76ea3-77f3-4c2f-9a57-0751823c89fd
ms.openlocfilehash: 53ead0e34b55eca44399cee09f1947a12e1eadd3
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611831"
---
# <a name="compiler-warning-level-1-c4743"></a>コンパイラの警告 (レベル 1) C4743

'*型*'別のサイズが、'*file1*'と'*file2*':*数*と*数*バイト

または、参照される 2 つのファイルで定義されている外部変数が、それらのファイルのさまざまな種類と、コンパイラが決定される変数のサイズ*file1*内の変数のサイズと異なります*file2*.

## <a name="remarks"></a>Remarks

この警告を出力できるときに、重要なケースがあるC++します。 宣言が異なる場合、それらの宣言には、仮想関数が含まれている場合に 2 つの異なるファイルで同じ名前を持つ同じ型を宣言する場合、コンパイラは警告 C4744 仮想関数テーブルを生成できます。 警告が発生したは、同じ型の 2 つの異なるサイズの仮想関数テーブルがある、リンカーは、1 つを実行可能ファイルに組み込むことを選択する必要があります。  間違った仮想関数を呼び出して、プログラムでしまうことができます。

この警告を解決するには、同じ種類の定義を使用するか型または変数に対して異なる名前を使用します。

## <a name="example"></a>例

次の例では、C4743 が生成されます。 これをコンパイルするには、両方のファイルを同じフォルダーに配置し、実行  

```cmd
cl /EHsc /W1 /GL /O2 C4743a.cpp C4743b.cpp
```

```cpp
// C4743a.cpp
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
};

void C::f1(void) {}
void C::f2(void) {}
void C::f3(void) {}
C q;
```

```cpp
// C4743b.cpp
class C {
public:
    virtual void f1(void);
    virtual void f2(void);
    virtual void f3(void);
    virtual void f4(void);
    virtual void f5(void);
};

void C::f4(void) {}
void C::f5(void) {}
C x;

int main() {}
```
