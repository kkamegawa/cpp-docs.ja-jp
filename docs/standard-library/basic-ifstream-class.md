---
title: basic_ifstream クラス
ms.date: 11/04/2016
f1_keywords:
- fstream/std::basic_ifstream
- fstream/std::basic_ifstream::close
- fstream/std::basic_ifstream::is_open
- fstream/std::basic_ifstream::open
- fstream/std::basic_ifstream::rdbuf
- fstream/std::basic_ifstream::swap
helpviewer_keywords:
- std::basic_ifstream [C++]
- std::basic_ifstream [C++], close
- std::basic_ifstream [C++], is_open
- std::basic_ifstream [C++], open
- std::basic_ifstream [C++], rdbuf
- std::basic_ifstream [C++], swap
ms.assetid: 366cd9a7-efc4-4b7f-ba10-c8271e47ffcf
ms.openlocfilehash: 1e5e22c837ca2d6389591cec6d2cdd256ca50b1a
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455513"
---
# <a name="basic_ifstream-class"></a>basic_ifstream クラス

`Elem` 型の要素を含む [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> クラスのストリーム バッファーからの要素とエンコードされたオブジェクトの抽出を制御するオブジェクトを記述します。この型の特性は、`Tr` クラスによって決定されます。

## <a name="syntax"></a>構文

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_ifstream : public basic_istream<Elem, Tr>
```

### <a name="parameters"></a>パラメーター

*Elem*\
ファイル バッファーの基本要素。

*Tr*\
ファイル バッファーの基本要素の特徴 (通常は `char_traits`< `Elem`>)。

## <a name="remarks"></a>Remarks

このオブジェクトは、クラス `basic_filebuf`< `Elem`, `Tr`> のオブジェクトを格納します。

## <a name="example"></a>例

次の例は、ファイルからテキストを読み取る方法を示しています。

```cpp
// basic_ifstream_class.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_class.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="input-basic_ifstream_classtxt"></a>入力: basic_ifstream_class.txt

```cpp
This is the contents of basic_ifstream_class.txt.
```

## <a name="output"></a>Output

```cpp
This is the contents of basic_ifstream_class.txt.
```

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[basic_ifstream](#basic_ifstream)|`basic_ifstream` オブジェクトの新しいインスタンスを初期化します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[close](#close)|ファイルを閉じます。|
|[is_open](#is_open)|ファイルが開いているかどうかを判断します。|
|[open](#open)|ファイルを開きます。|
|[rdbuf](#rdbuf)|格納されたストリーム バッファーのアドレスを返します。|
|[swap](#swap)|この `basic_ifstream` の内容を、指定された `basic_ifstream` の内容と交換します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_eq)|このストリーム オブジェクトの内容を割り当てます。 これは、`rvalue` が関係する移動代入で、コピーを残しません。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<fstream>

**名前空間:** std

## <a name="basic_ifstream"></a>  basic_ifstream::basic_ifstream

`basic_ifstream` 型のオブジェクトを構築します。

```cpp
basic_ifstream();

explicit basic_ifstream(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

explicit basic_ifstream(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

basic_ifstream(basic_ifstream&& right);
```

### <a name="parameters"></a>パラメーター

*ファイル名 (_d)* \
開くファイルの名前。

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) の列挙値のうちの 1 つ。

*_Prot*\
[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) の `shflag` パラメーターと同等の既定のファイル保護。

### <a name="remarks"></a>Remarks

最初のコンストラクターは、[basic_istream](../standard-library/basic-istream-class.md)( `sb`) を呼び出すことで基底クラスを初期化します。ここで、`sb` はクラス [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> の格納されているオブジェクトです。 また、`basic_filebuf`< `Elem`, `Tr`> を呼び出すことで `sb` の初期化もします。

2 番目と 3 番目のコンストラクターは、`basic_istream`( `sb`) を呼び出すことで基底クラスを初期化します。 また、`sb` も、[basic_filebuf](../standard-library/basic-filebuf-class.md#basic_filebuf)< `Elem`, `Tr`> を呼び出した後に `sb`. [open](../standard-library/basic-filebuf-class.md#open)( `_Filename`, `_Mode` &#124; `ios_base::in`) を呼び出すことで初期化します。 後者の関数が Null ポインターを返す場合、コンストラクターは **setstate**( `failbit`). を呼び出します。

4 番目のコンストラクターは、右辺値参照として扱われる `right` のコンテンツでオブジェクトを初期化します。

### <a name="example"></a>例

次の例は、ファイルからテキストを読み取る方法を示しています。 ファイルを作成するには、[basic_ofstream::basic_ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) の例を参照してください。

```cpp
// basic_ifstream_ctor.cpp
// compile with: /EHsc

#include <fstream>
#include <iostream>

using namespace std;

int main(int argc, char **argv)
{
    ifstream ifs("basic_ifstream_ctor.txt");
    if (!ifs.bad())
    {
        // Dump the contents of the file to cout.
        cout << ifs.rdbuf();
        ifs.close();
    }
}
```

## <a name="close"></a>  basic_ifstream::close

ファイルを閉じます。

```cpp
void close();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、 [rdbuf](#rdbuf) **->** [close](../standard-library/basic-filebuf-class.md#close)を呼び出します。

### <a name="example"></a>例

`close` の使用例については、「[basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)」を参照してください。

## <a name="is_open"></a>  basic_ifstream::is_open

ファイルが開いているかどうかを判断します。

```cpp
bool is_open() const;
```

### <a name="return-value"></a>戻り値

ファイルが開いている場合は **true**、それ以外の場合は **false**。

### <a name="remarks"></a>Remarks

このメンバー関数は、 [rdbuf](#rdbuf) **->** [is_open](../standard-library/basic-filebuf-class.md#is_open)を返します。

### <a name="example"></a>例

`is_open` の使用例については、「[basic_filebuf::is_open](../standard-library/basic-filebuf-class.md#is_open)」を参照してください。

## <a name="open"></a>  basic_ifstream::open

ファイルを開きます。

```cpp
void open(
    const char* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const char* _Filename,
    ios_base::openmode _Mode);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode = ios_base::in,
    int _Prot = (int)ios_base::_Openprot);

void open(
    const wchar_t* _Filename,
    ios_base::openmode _Mode);
```

### <a name="parameters"></a>パラメーター

*ファイル名 (_d)* \
開くファイルの名前。

*_Mode*\
[ios_base::openmode](../standard-library/ios-base-class.md#openmode) の列挙値のうちの 1 つ。

*_Prot*\
[_fsopen、_wfsopen](../c-runtime-library/reference/fsopen-wfsopen.md) の `shflag` パラメーターと同等の既定のファイル保護。

### <a name="remarks"></a>Remarks

メンバー関数は、[rdbuf](#rdbuf) **->** [open](../standard-library/basic-filebuf-class.md#open)(_ *Filename*, `_Mode` &#124; **ios_base::in**) を呼び出します。 Open が失敗した場合、関数は`failbit`[setstate](../standard-library/basic-ios-class.md#setstate) () を呼び出します。これにより、ios_base:: failure 例外がスローされる可能性があります。

### <a name="example"></a>例

の使用`open`例については、「 [basic_filebuf:: open](../standard-library/basic-filebuf-class.md#open) 」を参照してください。

## <a name="op_eq"></a>  basic_ifstream::operator=

このストリーム オブジェクトの内容を割り当てます。 これは、右辺値が関係する移動代入で、コピーを残しません。

```cpp
basic_ifstream& operator=(basic_ifstream&& right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
`basic_ifstream` オブジェクトへの右辺値参照。

### <a name="return-value"></a>戻り値

`*this` を返します。

### <a name="remarks"></a>Remarks

メンバー演算子は、右辺値参照として扱われる*right*の内容を使用して、オブジェクトの内容を置き換えます。 詳細については、「[左辺値と右辺値](../cpp/lvalues-and-rvalues-visual-cpp.md)」を参照してください。

## <a name="rdbuf"></a>  basic_ifstream::rdbuf

格納されたストリーム バッファーのアドレスを返します。

```cpp
basic_filebuf<Elem, Tr> *rdbuf() const
```

### <a name="return-value"></a>戻り値

格納されているストリーム バッファーを表す [basic_filebuf](../standard-library/basic-filebuf-class.md) オブジェクトへのポインター。

### <a name="example"></a>例

`rdbuf` の使用例については、「[basic_filebuf::close](../standard-library/basic-filebuf-class.md#close)」を参照してください。

## <a name="swap"></a>  basic_ifstream::swap

2 つの `basic_ifstream` オブジェクトの内容を交換します。

```cpp
void swap(basic_ifstream& right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
別のストリーム バッファーへの参照。

### <a name="remarks"></a>Remarks

このメンバー関数は、このオブジェクトの内容を*右*の内容と交換します。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream プログラミング](../standard-library/iostream-programming.md)\
[iostreams の規則](../standard-library/iostreams-conventions.md)
