---
title: ファイル処理と I/o (C +/cli CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- .NET Framework [C++], file handling
- files [C++], .NET Framework and
- I/O [C++], .NET Framework applications
- .NET Framework [C++], I/O
- files [C++], listing files
- directories [C++], listing files
- monitoring file system events
- FileSystemWatcher class, examples
- examples [C++], monitoring file system changes
- events [C++], monitoring
- file system events [C++]
- files [C++], binary
- binary files, reading in C++
- reading text files
- text files, reading
- files [C++], retrieving information about
- FileInfo class
- binary files, writing in C++
- files [C++], binary
- files [C++], text
- text files, writing in C++
ms.assetid: 3296fd59-a83a-40d4-bd4a-6096cc13101b
ms.openlocfilehash: 7009c0b017c403c3f0108aa84b8ddb25a1d1564f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325001"
---
# <a name="file-handling-and-io-ccli"></a>ファイル処理と I/O (C++/CLI)

.NET Framework を使ったさまざまなファイル操作について説明します。

次のトピックでは、<xref:System.IO> 名前空間で定義されたクラスを使用してさまざまなファイル操作を実行する方法について説明します。

## <a name="enumerate"></a> ディレクトリ内のファイルを列挙します。

ディレクトリ内のファイル リストを取得する方法を次のコード例に示します。 また、サブディレクトリも列挙します。 <xref:System.IO.Directory.GetFiles%2A><xref:System.IO.Directory.GetFiles%2A> メソッドと <xref:System.IO.Directory.GetDirectories%2A> メソッドを使用して、C:\Windows ディレクトリの内容を表示する方法を次のコード例に示します。

### <a name="example"></a>例

```cpp
// enum_files.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ folder = "C:\\";
   array<String^>^ dir = Directory::GetDirectories( folder );
   Console::WriteLine("--== Directories inside '{0}' ==--", folder);
   for (int i=0; i<dir->Length; i++)
      Console::WriteLine(dir[i]);

   array<String^>^ file = Directory::GetFiles( folder );
   Console::WriteLine("--== Files inside '{0}' ==--", folder);
   for (int i=0; i<file->Length; i++)
      Console::WriteLine(file[i]);

   return 0;
}
```

## <a name="monitor"></a> ファイル システムの変更の監視

次のコード例では<xref:System.IO.FileSystemWatcher>作成、変更、削除、または名前が変更されたファイルに対応するイベントを登録します。 ディレクトリのファイルへの変更を定期的にポーリングするには、代わりに使用することができます、<xref:System.IO.FileSystemWatcher>変更が検出されたときにイベントを発生させるクラス。

### <a name="example"></a>例

```cpp
// monitor_fs.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::IO;

ref class FSEventHandler
{
public:
    void OnChanged (Object^ source, FileSystemEventArgs^ e)
    {
        Console::WriteLine("File: {0} {1}",
               e->FullPath, e->ChangeType);
    }
    void OnRenamed(Object^ source, RenamedEventArgs^ e)
    {
        Console::WriteLine("File: {0} renamed to {1}",
                e->OldFullPath, e->FullPath);
    }
};

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();

   if(args->Length < 2)
   {
      Console::WriteLine("Usage: Watcher.exe <directory>");
      return -1;
   }

   FileSystemWatcher^ fsWatcher = gcnew FileSystemWatcher( );
   fsWatcher->Path = args[1];
   fsWatcher->NotifyFilter = static_cast<NotifyFilters>
              (NotifyFilters::FileName |
               NotifyFilters::Attributes |
               NotifyFilters::LastAccess |
               NotifyFilters::LastWrite |
               NotifyFilters::Security |
               NotifyFilters::Size );

    FSEventHandler^ handler = gcnew FSEventHandler();
    fsWatcher->Changed += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Created += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Deleted += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Renamed += gcnew RenamedEventHandler(
            handler, &FSEventHandler::OnRenamed);

    fsWatcher->EnableRaisingEvents = true;

    Console::WriteLine("Press Enter to quit the sample.");
    Console::ReadLine( );
}
```

## <a name="read_binary"></a> バイナリ ファイルを読み込む

次のコード例では、<xref:System.IO?displayProperty=fullName> の名前空間の 2 つのクラス <xref:System.IO.FileStream> と <xref:System.IO.BinaryReader> を使用して、ファイルからバイナリ データを読み取る方法を示します。 <xref:System.IO.FileStream> は実際のファイルを表し、 <xref:System.IO.BinaryReader> はバイナリへのアクセスを可能にするストリームへのインターフェイスを提供します。

このコード例は、data.bin という名前のファイルを読み取り、整数をバイナリ形式で含めます。 この種類のファイルについては、次を参照してください。[方法。バイナリ ファイルを書き込む (C +/cli CLI)](../dotnet/how-to-write-a-binary-file-cpp-cli.md)します。

### <a name="example"></a>例

```cpp
// binary_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "data.bin";
   try
   {
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);
      BinaryReader^ br = gcnew BinaryReader(fs);

      Console::WriteLine("contents of {0}:", fileName);
      while (br->BaseStream->Position < br->BaseStream->Length)
         Console::WriteLine(br->ReadInt32().ToString());

      fs->Close( );
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("File '{0}' not found", fileName);
      else
         Console::WriteLine("Exception: ({0})", e);
      return -1;
   }
   return 0;
}
```

## <a name="read_text"></a> テキスト ファイルを読み込む

<xref:System.IO.StreamReader> クラスを使用して、テキスト ファイルを一度に 1 行ずつ開いて読み取る方法を次の例に示します。このクラスは、<xref:System.IO?displayProperty=fullName> 名前空間で定義されています。 このクラスのインスタンスを使用してテキスト ファイルを開いてから、<xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> メソッドを使用して各行を取得します。

このコード例では、テキストが含まれる textfile.txt というファイルを読み取ります。 この種類のファイルについては、次を参照してください。[方法。テキスト ファイルを書き込む (C +/cli CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md)します。

### <a name="example"></a>例

```cpp
// text_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";
   try
   {
      Console::WriteLine("trying to open file {0}...", fileName);
      StreamReader^ din = File::OpenText(fileName);

      String^ str;
      int count = 0;
      while ((str = din->ReadLine()) != nullptr)
      {
         count++;
         Console::WriteLine("line {0}: {1}", count, str );
      }
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("file '{0}' not found", fileName);
      else
         Console::WriteLine("problem reading file '{0}'", fileName);
   }

   return 0;
}
```

## <a name="retrieve"></a> ファイル情報を取得します。

<xref:System.IO.FileInfo> クラスのコード例を次に示します。 ファイル名がわかっている場合、このクラスを使用して、ファイル サイズ、ディレクトリ、完全名、ファイルの作成日時や最終更新日時などのファイル情報を取得できます。

このコードは、Notepad.exe 用のファイル情報を取得します。

### <a name="example"></a>例

```cpp
// file_info.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();
   if (args->Length < 2)
   {
      Console::WriteLine("\nUSAGE : file_info <filename>\n\n");
      return -1;
   }

   FileInfo^ fi = gcnew FileInfo( args[1] );

   Console::WriteLine("file size: {0}", fi->Length );

   Console::Write("File creation date:  ");
   Console::Write(fi->CreationTime.Month.ToString());
   Console::Write(".{0}", fi->CreationTime.Day.ToString());
   Console::WriteLine(".{0}", fi->CreationTime.Year.ToString());

   Console::Write("Last access date:  ");
   Console::Write(fi->LastAccessTime.Month.ToString());
   Console::Write(".{0}", fi->LastAccessTime.Day.ToString());
   Console::WriteLine(".{0}", fi->LastAccessTime.Year.ToString());

   return 0;
}
```

## <a name="write_binary"></a> バイナリ ファイルを書き込む

バイナリ データをファイルに書き込む方法を次のコード例に示します。 <xref:System.IO> 名前空間の 2 つのクラス、<xref:System.IO.FileStream> と <xref:System.IO.BinaryWriter> が使用されます。 <xref:System.IO.FileStream> は実際のファイルを表し、<xref:System.IO.BinaryWriter> はバイナリへのアクセスを可能にするストリームへのインターフェイスを提供します。

バイナリ形式の整数を含むファイルを書き込む方法を次のコード例に示します。 内のコードでこのファイルを読み取れる[方法。バイナリ ファイルの読み取り (C +/cli CLI)](../dotnet/how-to-read-a-binary-file-cpp-cli.md)します。

### <a name="example"></a>例

```cpp
// binary_write.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   array<Int32>^ data = {1, 2, 3, 10000};

   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);
   BinaryWriter^ w = gcnew BinaryWriter(fs);

   try
   {
      Console::WriteLine("writing data to file:");
      for (int i=0; i<data->Length; i++)
      {
         Console::WriteLine(data[i]);
         w->Write(data[i]);
      }
   }
   catch (Exception^)
   {
     Console::WriteLine("data could not be written");
     fs->Close();
     return -1;
   }

   fs->Close();
   return 0;
}
```

## <a name="write_text"></a> テキスト ファイルを書き込む

テキスト ファイルを作成し、<xref:System.IO.StreamWriter> クラスを使用してそのファイルにテキストを書き込む方法を次の例に示します。このクラスは、<xref:System.IO> 名前空間で定義されています。 <xref:System.IO.StreamWriter> コンストラクターは、作成されるファイル名を受け取ります。 ファイルが存在する場合、そのファイルに上書きされます (ただし、2 番目の <xref:System.IO.StringWriter> コンストラクター引数として True を渡す場合は例外です)。

次に、<xref:System.IO.StreamWriter.Write%2A> 関数と <xref:System.IO.TextWriter.WriteLine%2A> 関数を使用してファイルが保存されます。

### <a name="example"></a>例

```cpp
// text_write.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";

   StreamWriter^ sw = gcnew StreamWriter(fileName);
   sw->WriteLine("A text file is born!");
   sw->Write("You can use WriteLine");
   sw->WriteLine("...or just Write");
   sw->WriteLine("and do {0} output too.", "formatted");
   sw->WriteLine("You can also send non-text objects:");
   sw->WriteLine(DateTime::Now);
   sw->Close();
   Console::WriteLine("a new file ('{0}') has been written", fileName);

   return 0;
}
```

## <a name="see-also"></a>関連項目

[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[ファイルおよびストリーム入出力](/dotnet/standard/io/index)<br/>
[System.IO 名前空間](/dotnet/api/system.io)
