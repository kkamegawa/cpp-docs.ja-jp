---
title: class (C++)
ms.date: 11/04/2016
f1_keywords:
- class_cpp
helpviewer_keywords:
- class types [C++], class statements
- class keyword [C++]
ms.assetid: dd23c09f-6598-4069-8bff-69c7f2518b9f
ms.openlocfilehash: c4ef9690a41737147354ee0976f6912c4711ff67
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62331078"
---
# <a name="class-c"></a>class (C++)

**class**キーワードはクラス型を宣言またはクラス型のオブジェクトを定義します。

## <a name="syntax"></a>構文

```
[template-spec]
class [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[ class ] tag declarators;
```

#### <a name="parameters"></a>パラメーター

*template-spec*<br/>
テンプレートの指定 (省略可能)。 詳細についてを参照してください[テンプレート](templates-cpp.md)します。

*class*<br/>
**class**キーワード。

*ms-decl-spec*<br/>
ストレージ クラスの指定 (省略可能)。 詳細についてを参照してください、 [_ _declspec](../cpp/declspec.md)キーワード。

*タグ*<br/>
クラスに渡す型名。 タグは、クラスのスコープ内で予約語になります。 タグは省略できます。 省略した場合、匿名クラスが定義されます。 詳細については、次を参照してください。[匿名クラス型](../cpp/anonymous-class-types.md)します。

*base-list*<br/>
この構造体がメンバーを継承するクラスまたは構造体のオプション リスト。 詳細は [基本クラス](../cpp/base-classes.md)を参照してください。 アクセス指定子 ([public](../cpp/public-cpp.md)、[private](../cpp/private-cpp.md)、[protected](../cpp/protected-cpp.md))および [virtual](../cpp/virtual-cpp.md)キーワードが、各基本クラス名または構造体名の前に付きます。 詳細については、[メンバー アクセス コントロール](member-access-control-cpp.md)のメンバー アクセス テーブルを参照してください。

*member-list*<br/>
クラス メンバーのリスト。 参照してください[クラス メンバーの概要](../cpp/class-member-overview.md)詳細についてはします。

*declarators*<br/>
クラス型の 1 つ以上のインスタンスの名前を指定する宣言子リスト。 クラスのすべてのデータ メンバーがある場合、宣言子は初期化子リストを含めることができます**public**します。 これは、そのデータ メンバーは、構造の一般的な**public**よりも、既定でクラス。 参照してください[概要の宣言子](../cpp/overview-of-declarators.md)詳細についてはします。

## <a name="remarks"></a>Remarks

一般的なクラスの詳細については、次のトピックのいずれかを参照してください。

- [struct](../cpp/struct-cpp.md)

- [union](../cpp/unions.md)

- [_ _multiple_inheritance](../cpp/inheritance-keywords.md)

- [__single_inheritance](../cpp/inheritance-keywords.md)

- [__virtual_inheritance](../cpp/inheritance-keywords.md)

マネージ クラスと c++ 構造体について/cli および C++/cli CX を参照してください[クラスと構造体](../extensions/classes-and-structs-cpp-component-extensions.md)

## <a name="example"></a>例

```cpp
// class.cpp
// compile with: /EHsc
// Example of the class keyword
// Exhibits polymorphism/virtual functions.

#include <iostream>
#include <string>
#define TRUE = 1
using namespace std;

class dog
{
public:
   dog()
   {
      _legs = 4;
      _bark = true;
   }

   void setDogSize(string dogSize)
   {
      _dogSize = dogSize;
   }
   virtual void setEars(string type)      // virtual function
   {
      _earType = type;
   }

private:
   string _dogSize, _earType;
   int _legs;
   bool _bark;

};

class breed : public dog
{
public:
   breed( string color, string size)
   {
      _color = color;
      setDogSize(size);
   }

   string getColor()
   {
      return _color;
   }

   // virtual function redefined
   void setEars(string length, string type)
   {
      _earLength = length;
      _earType = type;
   }

protected:
   string _color, _earLength, _earType;
};

int main()
{
   dog mongrel;
   breed labrador("yellow", "large");
   mongrel.setEars("pointy");
   labrador.setEars("long", "floppy");
   cout << "Cody is a " << labrador.getColor() << " labrador" << endl;
}
```

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[クラスと構造体](../cpp/classes-and-structs-cpp.md)
