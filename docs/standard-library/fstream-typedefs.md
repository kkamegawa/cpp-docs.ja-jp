---
title: '&lt;fstream&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- fstream/std::filebuf
- fstream/std::fstream
- fstream/std::ifstream
- fstream/std::ofstream
- fstream/std::wfilebuf
- fstream/std::wfstream
- fstream/std::wifstream
- fstream/std::wofstream
ms.assetid: 8dddef2d-7f17-42a6-ba08-6f6f20597d23
ms.openlocfilehash: 3f4104b28f5becfdbf62ede16faa81e855fcac8c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689654"
---
# <a name="ltfstreamgt-typedefs"></a>&lt;fstream&gt; typedefs

||||
|-|-|-|
|[filebuf](#filebuf)|[fstream](#fstream)|[ifstream](#ifstream)|
|[ofstream](#ofstream)|[wfilebuf](#wfilebuf)|[wfstream](#wfstream)|
|[wifstream](#wifstream)|[wofstream](#wofstream)|

## <a name="filebuf"></a>  filebuf

**Char**テンプレートパラメーターに特化された型 `basic_filebuf`。

```cpp
typedef basic_filebuf<char, char_traits<char>> filebuf;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_filebuf](../standard-library/basic-filebuf-class.md)のシノニムで、既定の文字の特性を持つ**char**型の要素に対して特殊化されています。

## <a name="fstream">fstream</a>

**Char**テンプレートパラメーターに特化された型 `basic_fstream`。

```cpp
typedef basic_fstream<char, char_traits<char>> fstream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_fstream](../standard-library/basic-fstream-class.md)のシノニムで、既定の文字の特性を持つ**char**型の要素に対して特殊化されています。

## <a name="ifstream"></a>  ifstream

ファイルから 1 バイト文字のデータを順番に読み取るために使用するストリームを定義します。 `ifstream` は、 **char**のクラステンプレート `basic_ifstream` を特殊化する typedef です。

また、`basic_ifstream` を特殊化して**wchar_t** double 文字を読み取ることを専門とする typedef `wifstream` もあります。 詳細については、「[wifstream](../standard-library/fstream-typedefs.md#wifstream)」を参照してください。

```cpp
typedef basic_ifstream<char, char_traits<char>> ifstream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_ifstream](../standard-library/basic-ifstream-class.md)のシノニムで、既定の文字の特性を持つ char 型の要素に対して特殊化されています。 次に例を示します。

```cpp
using namespace std;

ifstream infile("existingtextfile.txt");

if (!infile.bad())
{
    // Dump the contents of the file to cout.
    cout << infile.rdbuf();infile.close();
}
```

## <a name="ofstream"></a>  ofstream

**Char**テンプレートパラメーターに特化された型 `basic_ofstream`。

```cpp
typedef basic_ofstream<char, char_traits<char>> ofstream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_ofstream](../standard-library/basic-ofstream-class.md)のシノニムで、既定の文字の特性を持つ**char**型の要素に対して特殊化されています。

## <a name="wfstream"></a>  wfstream

**Wchar_t**テンプレートパラメーターに特殊化された型 `basic_fstream`。

```cpp
typedef basic_fstream<wchar_t, char_traits<wchar_t>> wfstream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_fstream](../standard-library/basic-fstream-class.md)のシノニムで、既定の文字の特性を持つ**wchar_t**型の要素に対して特殊化されています。

## <a name="wifstream"></a>  wifstream

**Wchar_t**テンプレートパラメーターに特殊化された型 `basic_ifstream`。

```cpp
typedef basic_ifstream<wchar_t, char_traits<wchar_t>> wifstream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_ifstream](../standard-library/basic-ifstream-class.md)のシノニムで、既定の文字の特性を持つ**wchar_t**型の要素に対して特殊化されています。

## <a name="wofstream"></a>  wofstream

**Wchar_t**テンプレートパラメーターに特殊化された型 `basic_ofstream`。

```cpp
typedef basic_ofstream<wchar_t, char_traits<wchar_t>> wofstream;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_ofstream](../standard-library/basic-ofstream-class.md)のシノニムで、既定の文字の特性を持つ**wchar_t**型の要素に対して特殊化されています。

## <a name="wfilebuf"></a>  wfilebuf

**Wchar_t**テンプレートパラメーターに特殊化された型 `basic_filebuf`。

```cpp
typedef basic_filebuf<wchar_t, char_traits<wchar_t>> wfilebuf;
```

### <a name="remarks"></a>Remarks

この型はクラステンプレート[basic_filebuf](../standard-library/basic-filebuf-class.md)のシノニムで、既定の文字の特性を持つ**wchar_t**型の要素に対して特殊化されています。

## <a name="see-also"></a>関連項目

[\<fstream >](../standard-library/fstream.md)
