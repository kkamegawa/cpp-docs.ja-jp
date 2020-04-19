---
title: struct (C++ )
ms.date: 11/04/2016
f1_keywords:
- struct_cpp
helpviewer_keywords:
- struct constructors
ms.assetid: 3c6ba273-e248-4ff1-8c69-d2abcf1263c6
ms.openlocfilehash: e9ffd30dd0017e912fd7c196e2d3f0e987fb0810
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330584"
---
# <a name="struct-c"></a>struct (C++ )

**struct**キーワードは構造体型や構造体型の変数を定義します。

## <a name="syntax"></a>構文

```
[template-spec] struct [ms-decl-spec] [tag [: base-list ]]
{
   member-list
} [declarators];
[struct] tag declarators;
```

#### <a name="parameters"></a>パラメーター

*template-spec*<br/>
テンプレートの指定 (省略可能)。 詳細についてを参照してください[テンプレートの仕様](templates-cpp.md)します。

*struct*<br/>
**struct**キーワード。

*ms-decl-spec*<br/>
ストレージ クラスの指定 (省略可能)。 詳細についてを参照してください、 [_ _declspec](../cpp/declspec.md)キーワード。

*タグ*<br/>
構造体に渡す型名。 タグは構造体のスコープ内で予約語になります。 タグは省略できます。 省略した場合、匿名構造体が定義されます。 詳細については、次を参照してください。[匿名クラス型](../cpp/anonymous-class-types.md)します。

*base-list*<br/>
この構造体がメンバーを継承するクラスまたは構造体のオプション リスト 詳細は [基本クラス](../cpp/base-classes.md)を参照してください。 アクセス指定子 ([public](../cpp/public-cpp.md)、[private](../cpp/private-cpp.md)、[protected](../cpp/protected-cpp.md))および [virtual](../cpp/virtual-cpp.md)キーワードが、各基本クラス名または構造体名の前に付きます。 詳細については、[メンバー アクセス コントロール](member-access-control-cpp.md)のメンバー アクセス テーブルを参照してください。

*member-list*<br/>
構造体のメンバーのリスト。 参照してください[クラス メンバーの概要](../cpp/class-member-overview.md)詳細についてはします。 ここで唯一の違いは**struct**の代わりに使用が**class**します。

*declarators*<br/>
構造体の名前を指定する宣言リスト。 宣言子リストは構造体型の 1 つ以上のインスタンスを宣言します。 構造体のすべてのデータ メンバーがある場合、宣言子は初期化子リストを含めることができます**public**します。 データ メンバーがあるために、初期化子リストは構造体で一般的な**public**既定。  参照してください[概要の宣言子](../cpp/overview-of-declarators.md)詳細についてはします。

## <a name="remarks"></a>Remarks

構造体型はユーザー定義の複合データ型です。 この型は異なる型のフィールドやメンバーで構成されます。

C++ では、構造体はクラスと同じメンバーが実行される点を除いて**public**既定。

マネージ クラスと c++ 構造体について/cli CLI を参照してください[クラスと構造体](../extensions/classes-and-structs-cpp-component-extensions.md)します。

## <a name="using-a-structure"></a>構造体の使用

C では、明示的に使用する必要あります、**struct**キーワードを構造体を宣言します。 C++ では使用する必要はありません、**struct**キーワード、型が定義した後にします。

右中かっことセミコロンの間に 1 つ以上のコンマ区切りの変数名を挿入することで構造体型を定義している場合は、変数を宣言してもかまいません。

構造体の変数は初期化できます。 各変数の初期化は中かっこで囲む必要があります。

関連情報については、[class](../cpp/class-cpp.md)、[Unions](../cpp/unions.md)、および [列挙型](../cpp/enumerations-cpp.md)を参照してください。

## <a name="example"></a>例

```cpp
#include <iostream>
using namespace std;

struct PERSON {   // Declare PERSON struct type
    int age;   // Declare member types
    long ss;
    float weight;
    char name[25];
} family_member;   // Define object of type PERSON

struct CELL {   // Declare CELL bit field
    unsigned short character  : 8;  // 00000000 ????????
    unsigned short foreground : 3;  // 00000??? 00000000
    unsigned short intensity  : 1;  // 0000?000 00000000
    unsigned short background : 3;  // 0???0000 00000000
    unsigned short blink      : 1;  // ?0000000 00000000
} screen[25][80];       // Array of bit fields

int main() {
    struct PERSON sister;   // C style structure declaration
    PERSON brother;   // C++ style structure declaration
    sister.age = 13;   // assign values to members
    brother.age = 7;
    cout << "sister.age = " << sister.age << '\n';
    cout << "brother.age = " << brother.age << '\n';

    CELL my_cell;
    my_cell.character = 1;
    cout << "my_cell.character = " << my_cell.character;
}
// Output:
// sister.age = 13
// brother.age = 7
// my_cell.character = 1
```
