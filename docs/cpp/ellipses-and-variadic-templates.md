---
title: 楕円および可変値引数テンプレート
ms.date: 11/04/2016
ms.assetid: f20967d9-c967-4fd2-b902-2bb1d5ed87e3
ms.openlocfilehash: 387cf4478192cb9470804c219eee8046f8e47abe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392220"
---
# <a name="ellipses-and-variadic-templates"></a>楕円および可変値引数テンプレート

ここでは、C++ の可変個引数テンプレートを使用して省略記号 (`...`) を指定する方法を示します。 省略記号は、C および C++ で多くの用途にしました。 たとえば、関数の可変個引数リストなどです。 C ランタイム ライブラリの `printf()` 関数は、最も一般的な例の 1 つです。

A*可変個引数テンプレート*は任意の数の引数をサポートするクラスまたは関数テンプレートです。 この機構はクラス テンプレートと関数テンプレートの両方に適用でき、それによって広範なタイプ セーフと非自明の機能や柔軟性が提供されるため、C++ ライブラリの開発者に特に役立ちます。

## <a name="syntax"></a>構文

可変個引数テンプレートでは、省略記号が 2 とおりの方法で使用されます。 パラメーター名の左側のそのことを示します、*パラメーター パック*パラメーター名の右側に別個の名前に、パラメーター パックを展開します。

基本的な例を次に示します*可変個引数テンプレート クラス*定義の構文。

```cpp
template<typename... Arguments> class classname;
```

パラメーター パックとその展開のいずれの場合でも、次の例に示すように、必要に応じて省略記号の前後に空白を追加できます。

```cpp
template<typename ...Arguments> class classname;
```

または: 

```cpp
template<typename ... Arguments> class classname;
```

この記事では最初の例に示している規約を使用する (省略記号を `typename` に接続する) ことに注目してください。

上記の例で*引数*はパラメーター パックです。 `classname` クラスには、次の例のように、可変個の引数を指定できます。

```cpp
template<typename... Arguments> class vtclass;

vtclass< > vtinstance1;
vtclass<int> vtinstance2;
vtclass<float, bool> vtinstance3;
vtclass<long, std::vector<int>, std::string> vtinstance4;
```

可変個引数テンプレート クラス定義を使用して、1 つ以上のパラメーターを要求することもできます。

```cpp
template <typename First, typename... Rest> class classname;
```

基本的な例を次に示します*可変個引数テンプレート関数*構文。

```cpp
template <typename... Arguments> returntype functionname(Arguments... args);
```

*引数*を使用するは、次のセクションで示すようにパラメーター パックを展開し、**可変個引数テンプレートを理解する**します。

可変個引数テンプレート関数の構文は、他の形式を使用することもできます。いくつかの例を次に示します。

```cpp
template <typename... Arguments> returntype functionname(Arguments&... args);
template <typename... Arguments> returntype functionname(Arguments&&... args);
template <typename... Arguments> returntype functionname(Arguments*... args);
```

などの指定子**const**も許可されます。

```cpp
template <typename... Arguments> returntype functionname(const Arguments&... args);
```

可変個引数テンプレート クラス定義を使用して、1 つ以上のパラメーターを要求する関数を作成することができます。

```cpp
template <typename First, typename... Rest> returntype functionname(const First& first, const Rest&... args);
```

可変個引数テンプレートでは、`sizeof...()` 演算子が使用されます (従来の `sizeof()` 演算子とは無関係です)。

```cpp
template<typename... Arguments>
void tfunc(const Arguments&... args)
{
    constexpr auto numargs{ sizeof...(Arguments) };

    X xobj[numargs]; // array of some previously defined type X

    helper_func(xobj, args...);
}
```

## <a name="more-about-ellipsis-placement"></a>省略記号の配置の詳細

以前にこの記事で、パラメーター パックとその展開を定義する省略記号の配置について、パラメーター名の左に配置すると、パラメーター パックを意味し、パラメーター名の右に配置すると、パラメーター パックの展開を意味する (パラメーター パックが個々の名前に展開される) と説明しました。 これは技術的には事実ですが、コードへの変換の点では混乱することがあります。 次の例を考えてみましょう。

- テンプレート パラメーター リスト (`template <parameter-list>`)、`typename...`テンプレート パラメーター パックが導入されています。

- パラメーター宣言句 (`func(parameter-list)`)、「トップレベル」の省略記号には、関数パラメーター パックが導入されていて、省略記号の位置は重要です。

    ```cpp
    // v1 is NOT a function parameter pack:
    template <typename... Types> void func1(std::vector<Types...> v1);

    // v2 IS a function parameter pack:
    template <typename... Types> void func2(std::vector<Types>... v2);
    ```

- 省略記号がパラメーター名の直後にある場合、パラメーター パックの展開を示します。

## <a name="example"></a>例

可変個引数テンプレート関数の機構について説明するには、これを使用して `printf` の機能の一部を変更するのが最も適切です。

```cpp
#include <iostream>

using namespace std;

void print() {
    cout << endl;
}

template <typename T> void print(const T& t) {
    cout << t << endl;
}

template <typename First, typename... Rest> void print(const First& first, const Rest&... rest) {
    cout << first << ", ";
    print(rest...); // recursive call using pack expansion syntax
}

int main()
{
    print(); // calls first overload, outputting only a newline
    print(1); // calls second overload

    // these call the third overload, the variadic template,
    // which uses recursion as needed.
    print(10, 20);
    print(100, 200, 300);
    print("first", 2, "third", 3.14159);
}
```

## <a name="output"></a>出力

```Output
1
10, 20
100, 200, 300
first, 2, third, 3.14159
```

> [!NOTE]
>  可変個引数テンプレート関数を組み込むほとんどの実装を使用して、何らかの形式の再帰呼び出しは、従来の再帰が若干異なる。  従来の再帰には、同じシグネチャを使用して自身を呼び出す関数が含まれます。 (オーバーロードまたはテンプレート宣言できますが、毎回、同じシグネチャが選択されます)。可変個引数テンプレートの再帰では、異なる数の引数 (ほとんどの場合、徐々に減少) を使用して可変個引数関数テンプレートを呼び出します。したがって、毎回、異なるシグネチャを押すことになります。 "基本ケース" が必要なのは同じですが、再帰の性質は異なります。