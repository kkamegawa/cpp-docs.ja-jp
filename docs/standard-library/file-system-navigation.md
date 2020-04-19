---
title: ファイル システムのナビゲーション
ms.date: 11/04/2016
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: ea9bf44a11087180d3bd02c5dcd5d1acfa4b9e57
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518505"
---
# <a name="file-system-navigation"></a>ファイル システムのナビゲーション

\<filesystem> ヘッダーは、File System Technical Specification ISO/IEC TS 18822:2015 (最終ドラフト: [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)) を実装し、型および関数により、ファイル システムを移動するためのプラットフォームに依存しないコードを記述できます。 それはクロス プラットフォームなので、Windows システムに関連しない API が含まれます。 たとえば、これは `is_fifo(const path&)` が Windows で常に**false**を返すことを意味します。

## <a name="overview"></a>の概要

\<filesystem> API を次のタスクに使用します。

- 指定のパスの下のファイルとディレクトリを反復処理します。

- ファイルの作成時、サイズ、拡張子、およびルート ディレクトリなどに関するファイルの情報を取得します。

- パスの構成、分解、および比較

- ディレクトリの作成、コピー、および削除

- ファイルのコピーと削除

標準ライブラリを使用したファイル IO の詳細については、「[iostream プログラミング](../standard-library/iostream-programming.md)」を参照してください。

## <a name="paths"></a>パス

### <a name="constructing-and-composing-paths"></a>パスの構成および描画

(XP 以降の) Windows のパスは、ネイティブで Unicode で格納されます。 [path](../standard-library/path-class.md) クラスは、自動的にすべての必要な文字列の変換を実行します。 それはワイド文字とナロー文字の両方の配列の引数を受け入れ、UTF8 や UTF16 として書式設定された `std::string` や `std::wstring` 型も受け入れます。 `path` クラスは、パスの区切り記号も自動的に正規化します。 コンストラクターの引数のディレクトリの区切り記号として単一のスラッシュを使用することができます。 これにより、Windows と UNIX の両方の環境でのパスの格納に、同じ文字列を使用することができます。

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

2 つのパスを連結する際、オーバーロードされた `/` と `/=` 演算子を使用できますが、これは `+` および `+=` の `std::string` と `std::wstring`演算子と似ています。 `path` オブジェクトは、ユーザーが区切り文字を指定していない場合に、便利にそれを指定できます。

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>パスの確認

path クラスは、参照するファイル システム エンティティとは異なる、パス自体の様々な部分に関する情報を返すいくつかのメソッドを持っています。 ルート、相対パス、ファイル名、および、ファイル拡張子などを取得できます。 階層内のすべてのフォルダーを確認するために、パス オブジェクトで反復処理することができます。 次の例では (参照するディレクトリではなく) パスを繰り返し処理して、そのパーツに関する情報を取得する方法を示します。

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

wstring DisplayPathInfo()
{
    // This path may or may not refer to an existing file. We are
    // examining this path string, not file system objects.
    path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt ");

    wostringstream wos;
    int i = 0;
    wos << L"Displaying path info for: " << pathToDisplay << endl;
    for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr)
    {
        wos << L"path part: " << i++ << L" = " << *itr << endl;
    }

    wos << L"root_name() = " << pathToDisplay.root_name() << endl
        << L"root_path() = " << pathToDisplay.root_path() << endl
        << L"relative_path() = " << pathToDisplay.relative_path() << endl
        << L"parent_path() = " << pathToDisplay.parent_path() << endl
        << L"filename() = " << pathToDisplay.filename() << endl
        << L"stem() = " << pathToDisplay.stem() << endl
        << L"extension() = " << pathToDisplay.extension() << endl;

    return wos.str();
}

int main(int argc, char* argv[])
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

このコードでは、次の出力が生成されます:

```Output
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt
path part: 0 = C:
path part: 1 = \
path part: 2 = FileSystemTest
path part: 3 = SubDir3
path part: 4 = SubDirLevel2
path part: 5 = File2.txt
root_name() = C:
root_path() = C:\
relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt
parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2
filename() = File2.txt
stem() = File2
extension() = .txt
```

### <a name="comparing-paths"></a>パスの比較

`path` クラスは、 `std::string` および `std::wstring`と同じ比較演算子をオーバーロードします。 2 つのパスを比較したときに、区切り記号が正規化された後に、文字列の比較を実行します。 末尾のスラッシュ (または円記号) が不足している場合は追加されず、比較に影響します。 パスの値を比較する方法を次の例に示します。

```cpp
wstring ComparePaths()
{
    path p0(L"C:/Documents");                 // no trailing separator
    path p1(L"C:/Documents/");                // p0 < p1
    path p2(L"C:/Documents/2013/");           // p1 < p2
    path p3(L"C:/Documents/2013/Reports/");   // p2 < p3
    path p4(L"C:/Documents/2014/");           // p3 < p4
    path p5(L"D:/Documents/2013/Reports/");   // p4 < p5

    wostringstream wos;
    wos << boolalpha <<
        p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl <<
        p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl <<
        p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl <<
        p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl <<
        p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl;
    return wos.str();
}
```

```Output
C:\Documents < C:\Documents\: true
C:\Documents\ < C:\Documents\2013\: true
C:\Documents\2013\ < C:\Documents\2013\Reports\: true
C:\Documents\2013\Reports\ < C:\Documents\2014\: true
C:\Documents\2014\ < D:\Documents\2013\Reports\: true
```

このコードを実行するには、上記の完全なサンプル コードに貼り付けて、`main` でこれを呼び出す行をコメント解除します。

### <a name="converting-between-path-and-string-types"></a>パスと文字列型の間の変換

`path` オブジェクトは `std::wstring` または `std::string`に暗黙的に変換できます。 つまり、次の例に示すように、[wofstream::open](../standard-library/basic-ofstream-class.md#open) などの関数にパスを渡すことができます。

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::experimental::filesystem;

int main(int argc, char* argv[])
{
    wchar_t* p = L"C:/Users/Public/Documents";
    path filePath(p);

    filePath /= L"NewFile.txt";

    // Open, write to, and close the file.
    wofstream writeFile(filePath, ios::out);  // implicit conversion
    writeFile << L"Lorem ipsum\nDolor sit amet";
    writeFile.close();

    // Open, read, and close the file.
    wifstream readFile;
    wstring line;
    readFile.open(filePath);  // implicit conversions
    wcout << L"File " << filePath << L" contains:" << endl;
    while (readFile.good())
    {
        getline(readFile, line);
        wcout << line << endl;
    }
    readFile.close();

    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

```Output
File C:\Users\Public\Documents\NewFile.txt contains:
Lorem ipsum
Dolor sit amet

Press Enter to exit
```

## <a name="iterating-directories-and-files"></a>ディレクトリとファイルを反復する

\<filesystem> ヘッダーは、[directory_iterator](../standard-library/directory-iterator-class.md) 型を提供して、1 つのディレクトリを反復し、[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) クラスはディレクトリとサブディレクトリを再帰的に反復します。 `path` オブジェクトを渡して反復子を構成した後、反復子はパス内の最初の directory_entry を指します。 既定のコンストラクターを呼び出すことで、終了反復子を作成します。

ディレクトリを反復しているときに遭遇する可能性がある項目は、ディレクトリ、ファイル、シンボリック リンク、ソケット ファイルなどですが、これらに限定されません。 `directory_iterator` は、[directory_entry](../standard-library/directory-entry-class.md) オブジェクトとして項目を返します。
