---
title: クラス テンプレート
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], operating on type
- class templates
- templates, class templates
ms.assetid: 633a53c8-24ee-4c23-8c88-e7c3cb0b7ac3
ms.openlocfilehash: 1bf384967af9d6d639e11df882751bbdaf1b0aa6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62188396"
---
# <a name="class-templates"></a>クラス テンプレート

このトピックでは、C++ クラス テンプレートに固有の規則を説明します。

## <a name="member-functions-of-class-templates"></a>クラス テンプレートのメンバー関数

メンバー関数はクラス テンプレートの内側でも外側でも定義できます。 クラス テンプレートの外側で定義されている場合は、関数テンプレートと同様に定義されます。

```cpp
// member_function_templates1.cpp
template<class T, int i> class MyStack
{
    T*  pStack;
    T StackBuffer[i];
    static const int cItems = i * sizeof(T);
public:
    MyStack( void );
    void push( const T item );
    T& pop( void );
};

template< class T, int i > MyStack< T, i >::MyStack( void )
{
};

template< class T, int i > void MyStack< T, i >::push( const T item )
{
};

template< class T, int i > T& MyStack< T, i >::pop( void )
{
};

int main()
{
}
```

テンプレート クラス メンバー関数と同様、クラスのコンストラクター メンバー関数の定義には、テンプレート引数リストが 2 回含まれることに注意してください。

メンバー関数は、それ自体で関数テンプレートになり、次の例のように、追加パラメーターを指定します。

```cpp
// member_templates.cpp
template<typename T>
class X
{
public:
   template<typename U>
   void mf(const U &u);
};

template<typename T> template <typename U>
void X<T>::mf(const U &u)
{
}

int main()
{
}
```

## <a name="nested-class-templates"></a>入れ子になったクラス テンプレート

テンプレートはクラスまたはクラス テンプレート内で定義できます。その場合、メンバー テンプレートと呼ばれます。 クラスであるメンバー テンプレートは、入れ子になったクラス テンプレートと呼ばれます。 関数であるメンバー テンプレートは、後ほど[メンバー関数テンプレート](../cpp/member-function-templates.md)します。

入れ子になったクラス テンプレートは、外部クラスのスコープ内のクラス テンプレートとして宣言されます。 外側のクラス内外で定義できます。

次のコードは、通常のクラス内の入れ子になったクラス テンプレートを示します。

```cpp
// nested_class_template1.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

class X
{

   template <class T>
   struct Y
   {
      T m_t;
      Y(T t): m_t(t) { }
   };

   Y<int> yInt;
   Y<char> yChar;

public:
   X(int i, char c) : yInt(i), yChar(c) { }
   void print()
   {
      cout << yInt.m_t << " " << yChar.m_t << endl;
   }
};

int main()
{
   X x(1, 'a');
   x.print();
}
```

```cpp
// nested_class_template2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
class X
{
   template <class U> class Y
   {
      U* u;
   public:
      Y();
      U& Value();
      void print();
      ~Y();
   };

   Y<int> y;
public:
   X(T t) { y.Value() = t; }
   void print() { y.print(); }
};

template <class T>
template <class U>
X<T>::Y<U>::Y()
{
   cout << "X<T>::Y<U>::Y()" << endl;
   u = new U();
}

template <class T>
template <class U>
U& X<T>::Y<U>::Value()
{
   return *u;
}

template <class T>
template <class U>
void X<T>::Y<U>::print()
{
   cout << this->Value() << endl;
}

template <class T>
template <class U>
X<T>::Y<U>::~Y()
{
   cout << "X<T>::Y<U>::~Y()" << endl;
   delete u;
}

int main()
{
   X<int>* xi = new X<int>(10);
   X<char>* xc = new X<char>('c');
   xi->print();
   xc->print();
   delete xi;
   delete xc;
}

//Output:
X<T>::Y<U>::Y()
X<T>::Y<U>::Y()
10
99
X<T>::Y<U>::~Y()
X<T>::Y<U>::~Y()
```

ローカル クラスはメンバー テンプレートを持つことができません。

## <a name="template-friends"></a>テンプレートのフレンド

クラス テンプレートを持つことができます[友人](friend-cpp.md)します。 クラスまたはクラス テンプレート、関数または関数テンプレートは、テンプレート クラスへのフレンドにできます。 フレンドは、クラス テンプレートまたは関数テンプレートの特殊化でもかまいませんが、部分的特殊化は許されません。

次の例では、フレンド関数は、クラス テンプレート内の関数テンプレートとして定義されます。 このコードは、テンプレートのすべてのインスタンス化のフレンド関数版を生成します。 この構成は、フレンド関数がクラスと同じテンプレート パラメーターに依存している場合に便利です。

```cpp
// template_friend1.cpp
// compile with: /EHsc

#include <iostream>
using namespace std;

template <class T> class Array {
   T* array;
   int size;

public:
   Array(int sz): size(sz) {
      array = new T[size];
      memset(array, 0, size * sizeof(T));
   }

   Array(const Array& a) {
      size = a.size;
      array = new T[size];
      memcpy_s(array, a.array, sizeof(T));
   }

   T& operator[](int i) {
      return *(array + i);
   }

   int Length() { return size; }

   void print() {
      for (int i = 0; i < size; i++)
         cout << *(array + i) << " ";

      cout << endl;
   }

   template<class T>
   friend Array<T>* combine(Array<T>& a1, Array<T>& a2);
};

template<class T>
Array<T>* combine(Array<T>& a1, Array<T>& a2) {
   Array<T>* a = new Array<T>(a1.size + a2.size);
   for (int i = 0; i < a1.size; i++)
      (*a)[i] = *(a1.array + i);

   for (int i = 0; i < a2.size; i++)
      (*a)[i + a1.size] = *(a2.array + i);

   return a;
}

int main() {
   Array<char> alpha1(26);
   for (int i = 0 ; i < alpha1.Length() ; i++)
      alpha1[i] = 'A' + i;

   alpha1.print();

   Array<char> alpha2(26);
   for (int i = 0 ; i < alpha2.Length() ; i++)
      alpha2[i] = 'a' + i;

   alpha2.print();
   Array<char>*alpha3 = combine(alpha1, alpha2);
   alpha3->print();
   delete alpha3;
}
//Output:
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z
a b c d e f g h i j k l m n o p q r s t u v w x y z
A B C D E F G H I J K L M N O P Q R S T U V W X Y Z a b c d e f g h i j k l m n o p q r s t u v w x y z
```

次の例では、テンプレート特殊化を持つフレンドを呼び出します。 関数テンプレートの特殊化は、元の関数テンプレートがフレンドの場合は自動的にフレンドです。

次のコードのフレンド宣言の前のコメントが示すように、フレンドとしてテンプレートの特殊化バージョンのみを宣言することもできます。 この場合、テンプレート クラスの外側にフレンド テンプレートの特殊化の定義を配置します。

```cpp
// template_friend2.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
class Array;

template <class T>
void f(Array<T>& a);

template <class T> class Array
{
    T* array;
    int size;

public:
    Array(int sz): size(sz)
    {
        array = new T[size];
        memset(array, 0, size * sizeof(T));
    }
    Array(const Array& a)
    {
        size = a.size;
        array = new T[size];
        memcpy_s(array, a.array, sizeof(T));
    }
    T& operator[](int i)
    {
        return *(array + i);
    }
    int Length()
    {
        return size;
    }
    void print()
    {
        for (int i = 0; i < size; i++)
        {
            cout << *(array + i) << " ";
        }
        cout << endl;
    }
    // If you replace the friend declaration with the int-specific
    // version, only the int specialization will be a friend.
    // The code in the generic f will fail
    // with C2248: 'Array<T>::size' :
    // cannot access private member declared in class 'Array<T>'.
    //friend void f<int>(Array<int>& a);

    friend void f<>(Array<T>& a);
};

// f function template, friend of Array<T>
template <class T>
void f(Array<T>& a)
{
    cout << a.size << " generic" << endl;
}

// Specialization of f for int arrays
// will be a friend because the template f is a friend.
template<> void f(Array<int>& a)
{
    cout << a.size << " int" << endl;
}

int main()
{
    Array<char> ac(10);
    f(ac);

    Array<int> a(10);
    f(a);
}
//Output:
10 generic
10 int
```

次の例は、クラス テンプレート内で宣言されたフレンド クラス テンプレートを示します。 クラス テンプレートは、フレンド クラスのテンプレート引数として使用されます。 フレンド クラス テンプレートは、宣言されているクラス テンプレートの外部で定義する必要があります。 フレンド テンプレートの特殊化や部分的特殊化も、元のクラス テンプレートのフレンドです。

```cpp
// template_friend3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

template <class T>
class X
{
private:
   T* data;
   void InitData(int seed) { data = new T(seed); }
public:
   void print() { cout << *data << endl; }
   template <class U> friend class Factory;
};

template <class U>
class Factory
{
public:
   U* GetNewObject(int seed)
   {
      U* pu = new U;
      pu->InitData(seed);
      return pu;
   }
};

int main()
{
   Factory< X<int> > XintFactory;
   X<int>* x1 = XintFactory.GetNewObject(65);
   X<int>* x2 = XintFactory.GetNewObject(97);

   Factory< X<char> > XcharFactory;
   X<char>* x3 = XcharFactory.GetNewObject(65);
   X<char>* x4 = XcharFactory.GetNewObject(97);
   x1->print();
   x2->print();
   x3->print();
   x4->print();
}
//Output:
65
97
A
a
```

## <a name="reuse-of-template-parameters"></a>テンプレート パラメーターの再利用

テンプレート パラメーターは、テンプレート パラメーター リスト内で再利用できます。 たとえば、次のようなコードを記述できます。

```cpp
// template_specifications2.cpp

class Y
{
};
template<class T, T* pT> class X1
{
};
template<class T1, class T2 = T1> class X2
{
};

Y aY;

X1<Y, &aY> x1;
X2<int> x2;

int main()
{
}
```

## <a name="see-also"></a>関連項目

[テンプレート](../cpp/templates-cpp.md)