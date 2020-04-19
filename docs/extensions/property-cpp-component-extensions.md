---
title: property (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- property_cpp
- property
helpviewer_keywords:
- property keyword [C++]
ms.assetid: cc79d2b2-f013-4d81-8252-eece97a18704
ms.openlocfilehash: 8ec76db37cffb1b3d15447165300bedf1a8771c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516507"
---
# <a name="property--ccli-and-ccx"></a>property (C++/CLI および C++/CX)

"*プロパティ*" を宣言します。これは、データ メンバーや配列要素と同様に機能し、アクセスできるメンバー関数です。

## <a name="all-runtimes"></a>すべてのランタイム

次のいずれかの種類のプロパティを宣言できます。

"*シンプル プロパティ*"<br/>
既定では、プロパティ値を割り当てる "*set アクセサー*"、プロパティ値を取得する "*get アクセサー*"、およびプロパティ値を含むプライベート データ メンバー (コンパイラにより生成) を作成します。

"*プロパティ ブロック*"<br/>
これを使用して、ユーザー定義の get アクセサーまたは set アクセサーを作成します。 get アクセサーおよび set アクセサーの両方が定義されている場合、プロパティの読み取りと書き込みを実行できます。get アクセサーのみが定義されている場合、プロパティは読み取り専用です。set アクセサーのみが定義されている場合、プロパティは書き込み専用です。

プロパティ値を格納するデータ メンバーを明示的に宣言する必要があります。

"*インデックス プロパティ*"<br/>
1 つ以上のインデックスで指定されるプロパティの値を取得し設定するために使用できるプロパティ ブロック。

ユーザー定義のプロパティ名または "*既定の*" プロパティ名を持つインデックス プロパティを作成できます。 既定のインデックス プロパティの名前は、プロパティが定義されているクラスの名前です。 既定のプロパティを宣言するには、プロパティ名ではなく **default** キーワードを指定します。

プロパティ値を格納するデータ メンバーを明示的に宣言する必要があります。 通常、インデックス プロパティの場合、データ メンバーは配列またはコレクションになります。

### <a name="syntax"></a>構文

```cpp
property type property_name;

property type property_name {
   access-modifier type get() inheritance-modifier {property_body};
   access-modifier void set(type value) inheritance-modifier {property_body};
}

property type property_name[index_list] {
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}

property type default[index_list] {
   access-modifier type get(index_list) inheritance-modifier {property_body};
   access-modifier void set(index_list, value) inheritance-modifier {property_body};
}
```

### <a name="parameters"></a>パラメーター

*type*<br/>
プロパティ値のデータ型、つまりプロパティ自体です。

*property_name*<br/>
プロパティの名前。

*access-modifier*<br/>
アクセス修飾子。 有効な修飾子は **static** と **virtual** です。

get アクセサーまたは set アクセサーの **virtual** 修飾子は一致する必要はありませんが、**static** 修飾子は一致する必要があります。

*inheritance-modifier*<br/>
継承修飾子。 有効な修飾子は **abstract** と **sealed** です。

*index_list*<br/>
1 つ以上のインデックスのコンマ区切りのリスト。 各インデックスは、インデックスの型と、プロパティ メソッドの本文で使用できる識別子 (省略可能) で構成されます。

*value*<br/>
set 操作でプロパティに代入される値、または get 操作で取得される値。

*property_body*<br/>
set アクセサーまたは get アクセサーのプロパティ メソッドの本体。 *property_body* では、*index_list* を、基になるプロパティ データ メンバーにアクセスするために使用するか、ユーザー定義処理のパラメーターとして使用できます。

## <a name="windows-runtime"></a>Windows ランタイム

詳細については、「[プロパティ (C++/CX)](https://msdn.microsoft.com/library/windows/apps/hh755807.aspx)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

### <a name="syntax"></a>構文

```cpp
modifier property type property_name;

modifier property type property_name {
   modifier void set(type);
   modifier type get();
}
modifier property type property_name[index-list, value] {
   modifier void set(index-list, value);
   modifier type get(index-list);

modifier property type default[index];
}
```

### <a name="parameters"></a>パラメーター

*modifier*<br/>
プロパティの宣言または get/set アクセサー メソッドで使用できる修飾子。 可能な値は **static** と **virtual** です。

*type*<br/>
プロパティで表される値の型。

*property_name*<br/>
raise メソッドのパラメーター。デリゲートのシグネチャと一致する必要があります。

*index_list*<br/>
1 つ以上のインデックスのリスト (コンマ区切り)。角かっこ (添字演算子 []) で囲んで指定します。 各インデックスについて型を指定し、さらに必要に応じてプロパティ メソッドの本文で使用できる識別子も指定します。

### <a name="remarks"></a>解説

最初の構文例では、"*シンプル プロパティ*" を示します。ここでは `set` メソッドと `get` メソッドの両方を暗黙的に宣言しています。 コンパイラは自動的にプロパティの値を格納するためのプライベート フィールドを作成します。

2 つ目の構文例では、"*プロパティ ブロック*" を示します。ここでは `set` メソッドと `get` メソッドの両方を明示的に宣言しています。

3 つ目の構文例では、ユーザー定義の "*インデックス プロパティ*" を示します。 インデックス プロパティは、設定または取得する値だけでなくパラメーターも受け取ります。 プロパティに名前を指定する必要があります。 シンプル プロパティとは異なり、インデックス プロパティの `set` メソッドと `get` メソッドは明示的に定義する必要があり、さらにプロパティの名前も指定する必要があります

4 つ目の構文例では、型のインスタンスに対して配列と同様にアクセスできるようにする、"*既定の*" プロパティを示します。 **default** キーワードは、既定のプロパティを指定するためにのみ使用されます。 既定のプロパティの名前は、プロパティが定義されている型の名前です。

**property** キーワードは、クラス、インターフェイス、または値の型で使用できます。 プロパティには get 関数 (読み取り専用)、set 関数 (書き込み専用)、またはその両方 (読み取り/書き込み) を定義できます。

プロパティ名は、それ自身が含まれるマネージド クラスの名前と同じにすることはできません。 getter 関数の戻り値の型は、対応する setter 関数の最後のパラメーターの型と一致する必要があります。

クライアント コードに対しては、プロパティは通常のデータ メンバーと同じように扱うことができ、データ メンバーと同じ構文を使用して書き込みまたは読み取りを実行できます。

get メソッドと set メソッドの**virtual** 修飾子は一致する必要はありません。

get メソッドと set メソッドのアクセシビリティが異なっていても問題ありません。

プロパティ メソッドの定義は、通常のメソッドと同様に、クラスの本文の外でも表示できます。

プロパティの get メソッドと set メソッドの **static** 修飾子は一致している必要があります。

プロパティの get メソッドと set メソッドが次の説明に適合している場合、そのプロパティはスカラーです。

- get メソッドにはパラメーターがなく、戻り値の型は `T` です。

- set メソッドには `T` 型のパラメーターがあり、戻り値の型は **void** です。

同じ ID のスコープ内では、1 つのスカラー プロパティしか宣言できません。 スカラー プロパティはオーバーロードできません。

プロパティ データ メンバーを宣言すると、コンパイラはクラスにデータ メンバーを挿入します。このデータ メンバーは "バッキング ストア" とも呼ばれます。 ただし、このデータ メンバーの名前は、外側のクラスの実際のデータ メンバーであるかのように、ソース内のメンバーを参照できないような形式になっています。 型のメタデータを表示し、プロパティのバッキング ストアに対してコンパイラが生成した名前を確認するには、ildasm.exe を使用します。

プロパティ ブロック内のアクセサー メソッドについては、異なるアクセシビリティが許容されます。  つまり、set メソッドをパブリックに、get メソッドをプライベートにすることができます。  ただし、アクセサー メソッドのアクセシビリティが、プロパティ自体の宣言でのアクセシビリティよりも制限が少ない場合、エラーになります。

**property** は状況依存キーワードです。  詳細については、「[状況依存キーワード](context-sensitive-keywords-cpp-component-extensions.md)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次の例は、プロパティのデータ メンバーとプロパティ ブロックの宣言方法と使用方法を示しています。  これにより、プロパティ アクセサーがクラスから定義できることもわかります。

```cpp
// mcppv2_property.cpp
// compile with: /clr
using namespace System;
public ref class C {
   int MyInt;
public:

   // property data member
   property String ^ Simple_Property;

   // property block
   property int Property_Block {

      int get();

      void set(int value) {
         MyInt = value;
      }
   }
};

int C::Property_Block::get() {
   return MyInt;
}

int main() {
   C ^ MyC = gcnew C();
   MyC->Simple_Property = "test";
   Console::WriteLine(MyC->Simple_Property);

   MyC->Property_Block = 21;
   Console::WriteLine(MyC->Property_Block);
}
```

```Output
test

21
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)