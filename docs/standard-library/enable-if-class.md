---
title: enable_if クラス
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::enable_if
helpviewer_keywords:
- enable_if class
- enable_if
ms.assetid: c6b8d41c-a18f-4e30-a39e-b3aa0e8fd926
ms.openlocfilehash: 6e6b8a286dca8c451e6920e7f25f07829d3b453f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454211"
---
# <a name="enableif-class"></a>enable_if クラス

SFINAE オーバーロード解決用のタイプのインスタンスを条件によって作成する 入れ子になっ`enable_if<Condition,Type>::type`た typedef は、 `Condition`が**true**の`Type`場合にのみ、のシノニムになります。

## <a name="syntax"></a>構文

```cpp
template <bool B, class T = void>
struct enable_if;
```

### <a name="parameters"></a>パラメーター

*B*\
結果の型の存在を定義する値。

*\T*\
*B*が true の場合にインスタンスを生成する型。

## <a name="remarks"></a>Remarks

*B*が true の場合`enable_if<B, T>` 、には、 *T*のシノニムである "type" という名前の入れ子になった typedef があります。

*B*が false の場合`enable_if<B, T>` 、は "type" という名前の入れ子になった typedef を持ちません。

このエイリアス テンプレートが提供されています。

```cpp
template <bool B, class T = void>
using enable_if_t = typename enable_if<B,T>::type;
```

C++ では、テンプレート パラメーターの置き換えの失敗は、それ自体はエラーではありません。これは *SFINAE* (substitution failure is not an error: 置き換えの失敗はエラーではない) と呼ばれます。 一般的に、`enable_if` はオーバーロード解決から候補を外す (つまりオーバーロード セットを除外する) ために使用します。一方を優先させて他方の定義が拒否されることもあります。 これは、SFINAE の動作に適合します。 SFINAE の詳細については、Wikipedia の「[Substitution failure is not an error](https://go.microsoft.com/fwlink/p/?linkid=394798)」を参照してください。

次に、4 つのシナリオの例を示します。

- シナリオ 1:関数の戻り値の型をラップしています。

```cpp
    template <your_stuff>
typename enable_if<your_condition, your_return_type>::type
    yourfunction(args) {// ...
}
// The alias template makes it more concise:
    template <your_stuff>
enable_if_t<your_condition, your_return_type>
yourfunction(args) {// ...
}
```

- 例 2:既定の引数を持つ関数パラメーターを追加すると、次のようになります。

```cpp
    template <your_stuff>
your_return_type_if_present
    yourfunction(args, enable_if_t<your condition, FOO> = BAR) {// ...
}
```

- 例 3:既定の引数を持つテンプレートパラメーターを追加すると、次のようになります。

```cpp
    template <your_stuff, typename Dummy = enable_if_t<your_condition>>
rest_of_function_declaration_goes_here
```

- シナリオ 4:関数に非テンプレート引数がある場合は、その型をラップできます。

```cpp
    template <typename T>
void your_function(const T& t,
    enable_if_t<is_something<T>::value, const string&>
s) {// ...
}
```

シナリオ 1 は、コンストラクターおよび変換演算子では機能しません。それらは戻り値の型を持たないためです。

シナリオ 2 では、パラメーターは名前がないままです。 `::type Dummy = BAR` とすることもできますが、名前`Dummy` は重要ではなく、名前を付けることは "未参照のパラメーター" 警告をトリガーする可能性があります。 関数パラメーターの型 `FOO`、および既定の引数`BAR` を選択する必要があります。  **Int**と`0`を指定することもできますが、コードのユーザーは、無視される余分な整数を誤って関数に渡すことができます。 代わりに、との`void **`いずれか`0`または**nullptr**を使用することをお勧めし`void **`ます。これは、ほとんど何も変換できないためです。

```cpp
template <your_stuff>
your_return_type_if_present
yourfunction(args, typename enable_if<your_condition, void **>::type = nullptr) {// ...
}
```

シナリオ 2 は通常のコンストラクターでも機能します。  ただし、変換演算子は追加のパラメーターをとることができないため、シナリオ 2 は変換演算子では機能しません。  また、[variadic](../cpp/ellipses-and-variadic-templates.md) コンストラクターでも機能しません。追加パラメーターを付加することによって、関数のパラメーターは非推定コンテキストをパックするため、`enable_if` の目的は達成できないからです。

シナリオ 3 は、`Dummy` という名前を使用しますが、これは任意です。 単に "`typename = typename`" だけで機能しますが、少し変に見えるかもしれないので、"dummy" という名前を使用できます。関数定義で使用される可能性のある名前は使用しないでください。 `enable_if` に型を指定しない場合、既定値は void になります。ユーザーは `Dummy` が何かを気にしなくていないため、これは非常に理にかなっています。 これは、変換演算子や [variadic](../cpp/ellipses-and-variadic-templates.md) コンストラクターなど、すべてにおいて機能します。

シナリオ 4 は、戻り値の型を持たないコンストラクターで機能するため、シナリオ 1 のラッピングの制約を解決します。  ただし、シナリオ 4 は非テンプレート関数の引数に限定されますが、このような引数は必ず利用できるわけではありません  (テンプレート関数の引数でシナリオ 4 を使用すると、テンプレート引数の推定が機能しません)。

`enable_if` は強力ですが、誤って使用すると危険です。  enable_if の目的はオーバーロードの解決前に候補を除外することなので、誤って使用すると、その影響によって混乱が生じます。  次に、いくつか推奨例を示します。

- コンパイル時に実装を選択するのに、`enable_if` を使用しないでください。 1 つの `enable_if` を `CONDITION` に対して記述し、別の enable_if を `!CONDITION` に記述しないでください。  代わりに、*タグ ディスパッチ* パターン (たとえば、反復子で与えられる強さによって実装を選択するアルゴリズム) を使用してください。

- `enable_if` を使用して要件を強制しないでください。  テンプレート パターンを検証しようとして検証に失敗し、他の実装を選択する代わりにエラーが生じた場合は、[static_assert](../cpp/static-assert.md) を使用します。

- 他の方法では、優れたコードが曖昧になってしまうようなオーバーロード セットがある場合には、`enable_if` を使用します。  ほとんどの場合、これは暗黙に変換されるコンストラクターで発生します。

## <a name="example"></a>例

この例では、C++ 標準ライブラリのテンプレート関数 [std::make_pair()](../standard-library/utility-functions.md#make_pair) が `enable_if` をどのように利用するかを示しています。

```cpp
void func(const pair<int, int>&);

void func(const pair<string, string>&);

func(make_pair("foo", "bar"));
```

この例では、`make_pair("foo", "bar")` は `pair<const char *, const char *>` を返します。 オーバーロード解決では、どの `func()` が必要かを決定する必要があります。 `pair<A, B>` は、`pair<X, Y>` から暗黙に変換されるコンストラクターを持っています。  これは新しいものではなく、C++98 にありました。 ただし C++98/03 では、暗黙に変換されるコンストラクターのシグネチャは、`pair<int, int>(const pair<const char *, const char *>&)` の場合でも必ず存在します。  オーバーロードの解決では、コンストラクター `const char *`をインスタンス化しようとしても、暗黙的に**int**に変換することはできません。これは、関数定義がインスタンス化される前に、シグネチャを確認するだけです。  そのため、この例のコードは曖昧です。シグネチャは、`pair<const char *, const char *>` を `pair<int, int>` と `pair<string, string>` の両方に変換するために存在するからです。

C++11 は、`enable_if` を使用してこの曖昧さを解決しました。`pair<A, B>(const pair<X, Y>&)` が、以下の場合**のみ**、つまり `const X&` が `A` に暗黙に変換され、`const Y&` が `B` に暗黙に変換される場合のみ存在するようにしています。  これにより、オーバーロード解決は、`pair<const char *, const char *>` が `pair<int, int>` に変換されないこと、および `pair<string, string>` となるオーバーロードが実行可能であることを決定できます。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<type_traits>

**名前空間:** std

## <a name="see-also"></a>関連項目

[<type_traits>](../standard-library/type-traits.md)
