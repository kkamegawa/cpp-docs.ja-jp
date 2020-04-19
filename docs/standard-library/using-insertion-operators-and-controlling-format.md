---
title: 挿入演算子と制御形式の使用
ms.date: 11/04/2016
helpviewer_keywords:
- insertion operators
ms.assetid: cdefe986-6548-4cd1-8a67-b431d7d36a1c
ms.openlocfilehash: 2cf399501c0eab32e8bee80dfcb98d870c0193cb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458022"
---
# <a name="using-insertion-operators-and-controlling-format"></a>挿入演算子と制御形式の使用

このトピックでは、独自のクラスに対して書式を制御する方法と挿入演算子を作成する方法について説明します。 すべての標準 C++ のデータ型であらかじめプログラミングされている挿入 ( **<<** ) 演算子は、出力ストリーム オブジェクトにバイトを送信します。 挿入演算子は定義済み "マニピュレーター" と共に機能します。マニピュレーターとは、整数引数の既定の書式を変更する要素です。

次のオプションを使用して、書式を制御できます。

- [出力幅](#vclrfoutputwidthanchor3)

- [アラインメント](#vclrfalignmentanchor4)

- [精度](#vclrfprecisionanchor5)

- [基数](#vclrfradixanchor6)

## <a name="vclrfoutputwidthanchor3"></a> 出力幅

出力を配置するには、 `setw`マニピュレーターをストリームに配置するか、 `width`メンバー関数を呼び出すことによって、各項目の出力幅を指定します。 この例では、列に値を 10 文字の幅に右揃えで出力します。

```cpp
// output_width.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main( )
{
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };
   for( int i = 0; i < 4; i++ )
   {
      cout.width(10);
      cout << values[i] << '\n';
   }
}
```

```Output
      1.23
     35.36
     653.7
   4358.24
```

10 文字の幅に満たない値に対しては先頭に空白文字が追加されます。

フィールドを埋め込むには、 `fill`メンバー関数を使用します。この関数は、幅が指定されているフィールドの埋め込み文字の値を設定します。 既定では、空白文字です。 数値の列を埋めるのにアスタリスクを使用する場合は、前の **for** ループを次のように変更します。

```cpp
for (int i = 0; i <4; i++)
{
    cout.width(10);
    cout.fill('*');
    cout << values[i] << endl;
}
```

`endl` マニピュレーターは、改行文字 (`'\n'`) を置換します。 出力は次のようになります。

```Output
******1.23
*****35.36
*****653.7
***4358.24
```

同じ行のデータ要素に幅を指定するには、`setw` マニピュレーターを使用します。

```cpp
// setw.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

int main( )
{
   double values[] = { 1.23, 35.36, 653.7, 4358.24 };
   char *names[] = { "Zoot", "Jimmy", "Al", "Stan" };
   for( int i = 0; i < 4; i++ )
      cout << setw( 7 )  << names[i]
           << setw( 10 ) << values[i] << endl;
}
```

この`width`メンバー関数は、iostream \<> で宣言されています。 `setw` または他の引数付きのマニピュレーターを使用する場合は、\<iomanip> をインクルードする必要があります。 出力では、文字列は 6 桁の幅のフィールドに、整数は 10 桁の幅のフィールドに出力されます。

```Output
   Zoot      1.23
  Jimmy     35.36
     Al     653.7
   Stan   4358.24
```

`setw` また`width`は値の切り捨てを行いません。 書式付き出力がこの幅を超えた場合、ストリームの精度の設定に従い、値全体が出力されます。 `setw` と`width`は、次のフィールドのみに影響します。 フィールドが 1 つ出力されると、フィールドの幅は既定の動作 (既定の幅) に戻ります。 ただし、その他のストリームの形式オプションは変更されるまで有効です。

## <a name="vclrfalignmentanchor4"></a> アラインメント

出力ストリームは、既定で右揃えのテキストになります。 前の例のように名前を左揃えにし、数値を右揃えにするには、**for** ループを次のように置き換えます。

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6) << names[i]
         << resetiosflags(ios::left)
         << setw(10) << values[i] << endl;
```

出力は次のようになります。

```Output
Zoot        1.23
Jimmy      35.36
Al         653.7
Stan     4358.24
```

[setiosflags](../standard-library/iomanip-functions.md#setiosflags) マニピュレーターと `left` 列挙子を使用して、left-align フラグを設定します。 この列挙子は、[ios](../standard-library/basic-ios-class.md) クラス内で定義されるため、その参照には、**ios::** プレフィックスをインクルードする必要があります。 [resetiosflags](../standard-library/iomanip-functions.md#resetiosflags) マニピュレーターは、left-align フラグをオフにします。 と`width` `setiosflags` `resetiosflags`とは異なり、との効果は永続的です。 `setw`

## <a name="vclrfprecisionanchor5"></a> 精度

浮動小数点の精度の既定値は、6 桁です。 たとえば、3466.9768 という数値は 3466.98 と出力されます。 この値を出力する方法を変更するには、[setprecision](../standard-library/iomanip-functions.md#setprecision) マニピュレーターを使用します。 このマニピュレーターには [fixed](../standard-library/ios-functions.md#fixed) と [scientific](../standard-library/ios-functions.md#scientific) の 2 つのフラグがあります。 [fixed](../standard-library/ios-functions.md#fixed) が設定されている場合、数値は、3466.976800 と出力されます。 が`scientific`設定されている場合は、3.4669773 + 003 として出力されます。

有効桁 1 桁で[アライン](#vclrfalignmentanchor4)された浮動小数点数値を表示するには、**for** ループを次のように置き換えます。

```cpp
for (int i = 0; i <4; i++)
    cout << setiosflags(ios::left)
         << setw(6)
         << names[i]
         << resetiosflags(ios::left)
         << setw(10)
         << setprecision(1)
         << values[i]
         << endl;
```

プログラムは次のようにリストを出力します。

```Output
Zoot          1
Jimmy     4e+01
Al        7e+02
Stan      4e+03
```

指数表記を削除するには、**for** ループの前に次のステートメントを挿入します。

```cpp
cout << setiosflags(ios::fixed);
```

固定小数点表記では、小数点以下 1 桁まで出力されます。

```Output
Zoot         1.2
Jimmy       35.4
Al         653.7
Stan      4358.2
```

`ios::fixed`フラグをに変更すると`ios::scientific`、プログラムによって次のように出力されます。

```cpp
Zoot    1.2e+00
Jimmy   3.5e+01
Al      6.5e+02
Stan    4.4e+03
```

この場合も、小数点以下 1 桁まで出力されます。 `ios::fixed` また`ios::scientific`はが設定されている場合、有効桁数の値によって小数点の後の桁数が決まります。 どちらのフラグも設定されていない場合、精度の値は、全体の有効桁数を決定します。 `resetiosflags` マニピュレーターは、これらのフラグをオフにします。

## <a name="vclrfradixanchor6"></a> 基数

、 `dec` 、`oct`および`hex`マニピュレーターは、入力と出力の既定の基数を設定します。 たとえば、マニピュレーターを`hex`出力ストリームに挿入すると、オブジェクトは整数の内部データ表現を16進数の出力形式に正しく変換します。 数値は、[uppercase](../standard-library/ios-functions.md#uppercase) フラグがオフの場合 (既定)、a から f 桁が小文字で表示されます。それ以外の場合は、大文字で表示されます。 既定の基数は`dec` (decimal) です。

## <a name="quoted-strings-c14"></a>引用符で囲まれた文字列 (C++14)

ストリームに文字列を挿入するときに、stringstream::str() メンバー関数を呼び出すことで、同じ文字列を簡単に取得できます。 ただし、抽出演算子を使用して、後でストリームを新しい文字列に挿入する場合、>> 演算子は、既定では最初の空白文字に遭遇すると停止するため、予期しない結果が生じる可能性があります。

```cpp
std::stringstream ss;
std::string inserted = "This is a sentence.";
std::string extracted;

ss << inserted;
ss >> extracted;

std::cout << inserted;     //  This is a sentence.
std::cout << extracted;    //  This
```

この動作は手動で克服できますが、文字列のラウンドトリップをより簡単にするために`std::quoted` 、c++ 14 \<では iomanip > にストリームマニピュレーターが追加されます。 `quoted()` は、挿入時に文字列を区切り記号 (既定では二重引用符 (")) で囲み、抽出時に終わりの区切り記号までのすべての文字を抽出するストリームを操作します。 埋め込まれた引用符は、エスケープ文字 (既定では '\\\\') でエスケープされます。

区切り記号はストリームオブジェクト内にのみ存在します。抽出された文字列には存在しませんが、 [basic_stringstream:: str](../standard-library/basic-stringstream-class.md#str)によって返される文字列に含まれています。

挿入演算子と抽出演算子の空白の処理は、コード内での文字列の表記方法に依存しません。そのため、入力文字列が未加工の文字列リテラルであるか、標準の文字列であるかにかかわらず、quoted 演算子は便利です。 埋め込みの引用符、改行、タブなどが含まれる入力文字列は、書式にかかわらず、quoted() マニピュレーターで保持されます。

詳細および完全なコード例については、「[引用符付き](../standard-library/iomanip-functions.md#quoted)」を参照してください。

## <a name="see-also"></a>関連項目

[出力ストリーム](../standard-library/output-streams.md)
