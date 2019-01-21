---
title: '方法: 例外と非例外的なコードの間のインターフェイスします。'
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: fd5bb4af-5665-46a1-a321-614b48d4061e
ms.openlocfilehash: e8ff92f965f48faa7954ae0364ec7877428e519c
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220627"
---
# <a name="how-to-interface-between-exceptional-and-non-exceptional-code"></a>方法: 例外と非例外的なコードの間のインターフェイスします。

ここでは、C++ モジュールで一貫した例外処理を実装する方法と、例外の境界でエラー コードとの間でそれらの例外を変換する方法を説明します。

C++ モジュールは、例外を使用しないコード (非例外コード) とのやり取りが必要な場合があります。 このようなインターフェイスと呼ばれる、*例外境界*します。 たとえば、C++ プログラム中で Win32 関数 `CreateFile` を呼び出すことが必要な場合があります。 `CreateFile` は例外をスローせず、`GetLastError` 関数で取得できるエラー コードを設定します。 作成する C++ プログラムが重要である場合、一貫した例外ベースのエラー処理ポリシーを適用するのが一般的です。 また、非例外コードとやり取りするというだけの理由から例外の使用をあきらめたり、例外ベースのエラー ポリシーと非例外ベースのエラー ポリシーを C++ モジュールで混在させないことが一般的です。

## <a name="calling-non-exceptional-functions-from-c"></a>C++ からの非例外関数の呼び出し

C++ から非例外関数を呼び出す場合、すべてのエラーを検出して例外をスローする C ++ 関数でその関数をラップします。 そのようなラッパー関数を設計するときは、まず提供する例外保証の種類 (no-throw、strong、basic) を決定します。 次に、例外がスローされるときにすべてのリソース (たとえばファイル ハンドル) が正しく解放されるように関数を設計します。 通常は、スマート ポインターなどのリソース マネージャー使用してリソースを所有することになります。 設計に関する考慮事項の詳細については、次を参照してください。[方法。例外安全性のための設計](../cpp/how-to-design-for-exception-safety.md)します。

### <a name="example"></a>例

次の例は、内部的に Win32 関数 `CreateFile` と `ReadFile` を使用して 2 個のファイルを開いて読み取る C++ 関数を示しています。  `File` クラスは、ファイル ハンドルの RAII (Resource Acquisition Is Initialization) ラッパーです。 そのコンストラクターは、"ファイルが見つからない" 状態を検出し、例外をスローして、C++ モジュールの呼び出し履歴の上方向 (この例では `main()` 関数) にエラーを伝達します。 `File` オブジェクトが完全に作成された後で例外がスローされる場合、デストラクターは自動的に `CloseHandle` を呼び出してファイル ハンドルを解放します  (この同じ目的のために ATL (Active Template Library) の `CHandle` クラスか、`unique_ptr` とカスタム削除子を使用することもできます)。Win32 と CRT の API を呼び出す関数は、エラーを検出し、ローカルに定義された `ThrowLastErrorIf` 関数を使用して C++ の例外をスローします。そこで `Win32Exception` クラスから派生した `runtime_error` クラスが使用されます。 この例のすべての関数は、strong 例外保証を提供します。つまり、これらの関数のどの場所で例外がスローされても、リソースがリークせず、プログラムの状態も変更されません。

```cpp
// compile with: /EHsc
#include <Windows.h>
#include <stdlib.h>
#include <vector>
#include <iostream>
#include <string>
#include <limits>
#include <stdexcept>

using namespace std;

string FormatErrorMessage(DWORD error, const string& msg)
{
    static const int BUFFERLENGTH = 1024;
    vector<char> buf(BUFFERLENGTH);
    FormatMessageA(FORMAT_MESSAGE_FROM_SYSTEM, 0, error, 0, buf.data(),
        BUFFERLENGTH - 1, 0);
    return string(buf.data()) + "   ("  + msg  + ")";
}

class Win32Exception : public runtime_error
{
private:
    DWORD m_error;
public:
    Win32Exception(DWORD error, const string& msg)
        : runtime_error(FormatErrorMessage(error, msg)), m_error(error) { }

    DWORD GetErrorCode() const { return m_error; }
};

void ThrowLastErrorIf(bool expression, const string& msg)
{
    if (expression) {
        throw Win32Exception(GetLastError(), msg);
    }
}

class File
{
private:
    HANDLE m_handle;

    // Declared but not defined, to avoid double closing.
    File& operator=(const File&);
    File(const File&);
public:
    explicit File(const string& filename)
    {
        m_handle = CreateFileA(filename.c_str(), GENERIC_READ, FILE_SHARE_READ,
            nullptr, OPEN_EXISTING, FILE_ATTRIBUTE_READONLY, nullptr);
        ThrowLastErrorIf(m_handle == INVALID_HANDLE_VALUE,
            "CreateFile call failed on file named " + filename);
    }

    ~File() { CloseHandle(m_handle); }

    HANDLE GetHandle() { return m_handle; }
};

size_t GetFileSizeSafe(const string& filename)
{
    File fobj(filename);
    LARGE_INTEGER filesize;

    BOOL result = GetFileSizeEx(fobj.GetHandle(), &filesize);
    ThrowLastErrorIf(result == FALSE, "GetFileSizeEx failed: " + filename);

    if (filesize.QuadPart < (numeric_limits<size_t>::max)()) {
        return filesize.QuadPart;
    } else {
        throw;
    }
}

vector<char> ReadFileVector(const string& filename)
{
    File fobj(filename);
    size_t filesize = GetFileSizeSafe(filename);
    DWORD bytesRead = 0;

    vector<char> readbuffer(filesize);

    BOOL result = ReadFile(fobj.GetHandle(), readbuffer.data(), readbuffer.size(),
        &bytesRead, nullptr);
    ThrowLastErrorIf(result == FALSE, "ReadFile failed: " + filename);

    cout << filename << " file size: " << filesize << ", bytesRead: "
        << bytesRead << endl;

    return readbuffer;
}

bool IsFileDiff(const string& filename1, const string& filename2)
{
    return ReadFileVector(filename1) != ReadFileVector(filename2);
}

#include <iomanip>

int main ( int argc, char* argv[] )
{
    string filename1("file1.txt");
    string filename2("file2.txt");

    try
    {
        if(argc > 2) {
            filename1 = argv[1];
            filename2 = argv[2];
        }

        cout << "Using file names " << filename1 << " and " << filename2 << endl;

        if (IsFileDiff(filename1, filename2)) {
            cout << "+++ Files are different." << endl;
        } else {
            cout<< "=== Files match." << endl;
        }
    }
    catch(const Win32Exception& e)
    {
        ios state(nullptr);
        state.copyfmt(cout);
        cout << e.what() << endl;
        cout << "Error code: 0x" << hex << uppercase << setw(8) << setfill('0')
            << e.GetErrorCode() << endl;
        cout.copyfmt(state); // restore previous formatting
    }
}
```

## <a name="calling-exceptional-code-from-non-exceptional-code"></a>非例外コードからの例外コードの呼び出し

"extern C" と宣言された C++ の関数は C プログラムから呼び出すことができます。 C++ COM サーバーは、さまざまな言語で記述されたコードで使用できます。 非例外コードから呼び出される、例外に対応した C++ のパブリック関数を実装する場合、C++ の関数は、例外が呼び出し元に伝達されないようにする必要があります。 したがって、C++ の関数は、対処方法がわかっているすべての例外を明示的にキャッチし、呼び出し元が理解できるエラー コードに適宜変換する必要があります。 発生する可能性があるすべての例外が不明な場合は、C++ の関数の最後のハンドラーとして `catch(...)` ブロックを記述します。 その場合、プログラムが不明な状態になる可能性があるため、呼び出し元に致命的なエラーを報告することをお勧めします。

次の例に示す関数では、スローされる例外が、Win32Exception か、`std::exception` から派生した例外の種類であることを仮定しています。 関数は、これらの種類の例外をすべてキャッチし、Win32 エラー コードとして呼び出し元にエラー情報を伝達します。

```cpp
BOOL DiffFiles2(const string& file1, const string& file2)
{
    try
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return FALSE;
        }
        return TRUE;
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }

    catch(std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return FALSE;
}
```

例外からエラー コードに変換するとき、考えられる 1 つの問題は、例外に格納できるような豊富な情報がエラー コードに含まれていないことが多いということです。 これに対処を行うことができます、**キャッチ**がスローされ、エラー コードに変換される前に、例外の詳細を記録するログ記録を実行する特定の例外の種類ごとにブロックします。 複数の関数すべての同じセットを使用する場合、このアプローチは、たくさんの繰り返しのコードを作成できます**キャッチ**ブロックします。 コードの繰り返しを回避するために適切な方法は、それらのブロックを実装する 1 つのプライベート ユーティリティ関数にリファクタリングすることにより、**お試しください**と**キャッチ**をブロックし、で呼び出される関数オブジェクトを受け取ります**お試しください**ブロックします。 各パブリック関数では、ラムダ式としてユーティリティ関数にコードを渡します。

```cpp
template<typename Func>
bool Win32ExceptionBoundary(Func&& f)
{
    try
    {
        return f();
    }
    catch(Win32Exception& e)
    {
        SetLastError(e.GetErrorCode());
    }
    catch(const std::exception& e)
    {
        SetLastError(MY_APPLICATION_GENERAL_ERROR);
    }
    return false;
}
```

次の例は、ファンクタを定義するラムダ式を記述する方法を示しています。 ラムダ式を使用して "インライン" でファンクタを定義すると、多くの場合、名前付きの関数オブジェクトとして記述するよりも理解しやすくなります。

```cpp
bool DiffFiles3(const string& file1, const string& file2)
{
    return Win32ExceptionBoundary([&]() -> bool
    {
        File f1(file1);
        File f2(file2);
        if (IsTextFileDiff(f1, f2))
        {
            SetLastError(MY_APPLICATION_ERROR_FILE_MISMATCH);
            return false;
        }
        return true;
    });
}
```

ラムダ式について詳しくは、「[ラムダ式](../cpp/lambda-expressions-in-cpp.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[エラーと例外の処理 (Modern C++)](../cpp/errors-and-exception-handling-modern-cpp.md)<br/>
[方法: 例外安全性のための設計](../cpp/how-to-design-for-exception-safety.md)<br/>
