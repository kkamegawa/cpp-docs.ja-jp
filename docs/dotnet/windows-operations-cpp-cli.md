---
title: Windows の操作 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- Windows [C++], Windows-specific tasks
- .NET Framework [C++], Windows operations
- Visual C++, Windows operations
- Windows operations [C++]
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
- Visual C++, user interactive state
- user interactive state
- Visual C++, reading from Windows Registry
- registry, reading
- performance counters
- performance counters, reading Windows performance counters
- performance monitoring, Windows performance counters
- performance, counters
- counters, reading Windows performance counters
- performance
- performance monitoring
- text, retrieving from Clipboard
- Clipboard, retrieving text
- current user names
- user names, retrieving
- UserName string
- .NET Framework, version
- Version property, retrieving .NET Framework version
- computer name, retrieving
- machine name, retrieving
- computer name
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
- text, storing in Clipboard
- Clipboard, storing text
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: b9a75cb4-0589-4d5b-92cb-5e8be42b4ac0
ms.openlocfilehash: 413ccc3b66d76f8779861d4d65eb262ee8640725
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384376"
---
# <a name="windows-operations-ccli"></a>Windows の操作 (C++/CLI)

Windows SDK を使用して Windows に固有のさまざまなタスクを示します。

次のトピックでは、Visual C を使用して Windows SDK で実行されるさまざまな Windows の操作を示します。

## <a name="determine_shutdown"></a> シャット ダウンが開始されたかどうかの判断します。

次のコード例では、アプリケーションまたは .NET Framework が終了して現在あるかどうかを判断する方法を示します。 これは、ため、シャット ダウン中、これらのコンストラクトは、システムによって完了処理され、確実に使用することはできません、.NET Framework での静的な要素にアクセスするため便利です。 チェックして、<xref:System.Environment.HasShutdownStarted%2A>プロパティ最初に、これらの要素にアクセスするいないと、潜在的な障害を回避できます。

### <a name="example"></a>例

```cpp
// check_shutdown.cpp
// compile with: /clr
using namespace System;
int main()
{
   if (Environment::HasShutdownStarted)
      Console::WriteLine("Shutting down.");
   else
      Console::WriteLine("Not shutting down.");
   return 0;
}
```

## <a name="determine_user"></a> ユーザーの対話型の状態を確認します。

次のコード例では、コードがユーザー対話型のコンテキストで実行されているかどうかを判断する方法を示します。 場合<xref:System.Environment.UserInteractive%2A>サービス プロセスとしてコードが実行されているかから、Web アプリケーション内でこの場合しないでユーザーと対話するには、false にします。

### <a name="example"></a>例

```cpp
// user_interactive.cpp
// compile with: /clr
using namespace System;

int main()
{
   if ( Environment::UserInteractive )
      Console::WriteLine("User interactive");
   else
      Console::WriteLine("Noninteractive");
   return 0;
}
```

## <a name="read_registry"></a> Windows レジストリからデータを読み取る

<xref:Microsoft.Win32.Registry.CurrentUser> キーを使用して、Windows レジストリからデータを読み込む方法を次のコード例に示します。 最初に、サブキー列挙を使用して、<xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A>メソッドし Identities サブキーを使用してを開くが、<xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A>メソッド。 ルート キー同様、各サブキーは <xref:Microsoft.Win32.RegistryKey> クラスで表されます。 最後に、新しい <xref:Microsoft.Win32.RegistryKey> オブジェクトを使用してキーと値のペアが一覧表示されます。

### <a name="example"></a>例

```cpp
// registry_read.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main( )
{
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );

   Console::WriteLine("Subkeys within CurrentUser root key:");
   for (int i=0; i<key->Length; i++)
   {
      Console::WriteLine("   {0}", key[i]);
   }

   Console::WriteLine("Opening subkey 'Identities'...");
   RegistryKey^ rk = nullptr;
   rk = Registry::CurrentUser->OpenSubKey("Identities");
   if (rk==nullptr)
   {
      Console::WriteLine("Registry key not found - aborting");
      return -1;
   }

   Console::WriteLine("Key/value pairs within 'Identities' key:");
   array<String^>^ name = rk->GetValueNames( );
   for (int i=0; i<name->Length; i++)
   {
      String^ value = rk->GetValue(name[i])->ToString();
      Console::WriteLine("   {0} = {1}", name[i], value);
   }

   return 0;
}
```

### <a name="remarks"></a>Remarks

<xref:Microsoft.Win32.Registry> クラスは、<xref:Microsoft.Win32.RegistryKey> の静的インスタンスの単なるコンテナーです。 各インスタンスは、ルート レジストリ ノードを表します。 インスタンスは、<xref:Microsoft.Win32.Registry.ClassesRoot>、<xref:Microsoft.Win32.Registry.CurrentConfig>、<xref:Microsoft.Win32.Registry.CurrentUser>、<xref:Microsoft.Win32.Registry.LocalMachine>、および <xref:Microsoft.Win32.Registry.Users> です。

<xref:Microsoft.Win32.Registry> クラスのオブジェクトは、静的オブジェクトであるだけでなく、読み取り専用です。 さらに、レジストリ オブジェクトのコンテンツにアクセスするために作成される <xref:Microsoft.Win32.RegistryKey> クラスのインスタンスも読み取り専用です。 この動作をオーバーライドする方法の例は、次を参照してください。[方法。Windows レジストリにデータを書き込む (C +/cli CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)します。

<xref:Microsoft.Win32.Registry> クラスには、さらに <xref:Microsoft.Win32.Registry.DynData> と <xref:Microsoft.Win32.Registry.PerformanceData> の 2 つのオブジェクトがあります。 この 2 つのオブジェクトは両方とも <xref:Microsoft.Win32.RegistryKey> クラスのインスタンスです。 <xref:Microsoft.Win32.Registry.DynData>オブジェクトには、し、Windows 98 および Windows me でのみサポートされている動的レジストリ情報が含まれています。 <xref:Microsoft.Win32.Registry.PerformanceData> オブジェクトを使用すると、Windows パフォーマンス モニター システムを使用するアプリケーションのパフォーマンス カウンター情報にアクセスできます。 <xref:Microsoft.Win32.Registry.PerformanceData>ノードが表す情報をレジストリに実際に格納されていないと、そのため、Regedit.exe を使用すると表示されることはできません。

## <a name="read_performance"></a> Windows パフォーマンス カウンターを読み取る

一部のアプリケーションおよび Windows サブシステムは、Windows のパフォーマンス システムのパフォーマンス データを公開します。 これらのカウンターを使用してアクセスできる、<xref:System.Diagnostics.PerformanceCounterCategory>と<xref:System.Diagnostics.PerformanceCounter>内に存在するクラス、<xref:System.Diagnostics?displayProperty=fullName>名前空間。

次のコード例では、これらのクラスを使用して取得し、プロセッサがビジー時間の割合を示すために Windows によって更新されるカウンターを表示します。

> [!NOTE]
>  この例では、Windows Vista を管理者権限で実行する必要があります。

### <a name="example"></a>例

```cpp
// processor_timer.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Threading;
using namespace System::Diagnostics;
using namespace System::Timers;

ref struct TimerObject
{
public:
   static String^ m_instanceName;
   static PerformanceCounter^ m_theCounter;

public:
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)
   {
      try
      {
         Console::WriteLine("CPU time used: {0,6} ",
          m_theCounter->NextValue( ).ToString("f"));
      }
      catch(Exception^ e)
      {
         if (dynamic_cast<InvalidOperationException^>(e))
         {
            Console::WriteLine("Instance '{0}' does not exist",
                  m_instanceName);
            return;
         }
         else
         {
            Console::WriteLine("Unknown exception... ('q' to quit)");
            return;
         }
      }
   }
};

int main()
{
   String^ objectName = "Processor";
   String^ counterName = "% Processor Time";
   String^ instanceName = "_Total";

   try
   {
      if ( !PerformanceCounterCategory::Exists(objectName) )
      {
         Console::WriteLine("Object {0} does not exist", objectName);
         return -1;
      }
   }
   catch (UnauthorizedAccessException ^ex)
   {
      Console::WriteLine("You are not authorized to access this information.");
      Console::Write("If you are using Windows Vista, run the application with ");
      Console::WriteLine("administrative privileges.");
      Console::WriteLine(ex->Message);
      return -1;
   }

   if ( !PerformanceCounterCategory::CounterExists(
          counterName, objectName) )
   {
      Console::WriteLine("Counter {0} does not exist", counterName);
      return -1;
   }

   TimerObject::m_instanceName = instanceName;
   TimerObject::m_theCounter = gcnew PerformanceCounter(
          objectName, counterName, instanceName);

   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);
   aTimer->Interval = 1000;
   aTimer->Enabled = true;
   aTimer->AutoReset = true;

   Console::WriteLine("reporting CPU usage for the next 10 seconds");
   Thread::Sleep(10000);
   return 0;
}
```

## <a name="retrieve_text"></a> クリップボードからテキストを取得します。

次のコード例では、<xref:System.Windows.Forms.Clipboard.GetDataObject%2A>をへのポインターを返すメンバー関数、<xref:System.Windows.Forms.IDataObject>インターフェイス。 このインターフェイスをデータの形式のクエリを実行し、実際のデータを取得するために使用できます。

### <a name="example"></a>例

```cpp
// read_clipboard.cpp
// compile with: /clr
#using <system.dll>
#using <system.Drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main( )
{
   IDataObject^ data = Clipboard::GetDataObject( );

   if (data)
   {
      if (data->GetDataPresent(DataFormats::Text))
      {
         String^ text = static_cast<String^>
           (data->GetData(DataFormats::Text));
         Console::WriteLine(text);
      }
      else
         Console::WriteLine("Nontext data is in the Clipboard.");
   }
   else
   {
      Console::WriteLine("No data was found in the Clipboard.");
   }

   return 0;
}
```

## <a name="retrieve_current"></a> 現在のユーザー名を取得します。

次のコード例では、現在のユーザー名 (Windows にログインしたユーザーの名前) の取得を示します。 名前が格納されている、 <xref:System.Environment.UserName%2A> 、文字列で定義されている、<xref:System.Environment>名前空間。

### <a name="example"></a>例

```cpp
// username.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);
   return 0;
}
```

## <a name="retrieve_dotnet"></a> .NET Framework のバージョンを取得します。

次のコード例は、現在インストールされている .NET Framework のバージョンを確認する方法を示します、<xref:System.Environment.Version%2A>ポインターであるプロパティを<xref:System.Version>バージョン情報を含むオブジェクト。

### <a name="example"></a>例

```cpp
// dotnet_ver.cpp
// compile with: /clr
using namespace System;
int main()
{
   Version^ version = Environment::Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write(".NET Framework version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
            build, major, minor, revision);
   }
   return 0;
}
```

## <a name="retrieve_local"></a> ローカル コンピューター名を取得します。

次のコード例は、ローカル コンピューター名の取得を示します (ネットワーク上のコンピューターの名前が表示されます)。 これを実現するには作業を<xref:System.Environment.MachineName%2A>、文字列で定義されている、<xref:System.Environment>名前空間。

### <a name="example"></a>例

```cpp
// machine_name.cpp
// compile with: /clr
using namespace System;

int main()
{
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);
   return 0;
}
```

## <a name="retrieve_version"></a> Windows のバージョンを取得します。

次のコード例では、現在のオペレーティング システムのプラットフォームとバージョン情報を取得する方法を示します。 この情報が格納されている、<xref:System.Environment.OSVersion%2A?displayProperty=fullName>プロパティ広い意味での Windows のバージョンを表す列挙体で構成されると、<xref:System.Environment.Version%2A>オペレーティング システムの正確なビルドを含むオブジェクト。

### <a name="example"></a>例

```cpp
// os_ver.cpp
// compile with: /clr
using namespace System;

int main()
{
   OperatingSystem^ osv = Environment::OSVersion;
   PlatformID id = osv->Platform;
   Console::Write("Operating system: ");

   if (id == PlatformID::Win32NT)
      Console::WriteLine("Win32NT");
   else if (id == PlatformID::Win32S)
      Console::WriteLine("Win32S");
   else if (id == PlatformID::Win32Windows)
      Console::WriteLine("Win32Windows");
   else
      Console::WriteLine("WinCE");

   Version^ version = osv->Version;
   if (version)
   {
      int build = version->Build;
      int major = version->Major;
      int minor = version->Minor;
      int revision = Environment::Version->Revision;
      Console::Write("OS Version: ");
      Console::WriteLine("{0}.{1}.{2}.{3}",
                   build, major, minor, revision);
   }

   return 0;
}
```

## <a name="retrieve_time"></a> 開始されてから経過時間を取得

次のコード例は、ティック数を確認する方法を示します。 または Windows から経過したミリ秒数が開始します。 この値は、<xref:System.Environment.TickCount%2A?displayProperty=fullName>メンバーと、32 ビット値であるため、ゼロにリセットすべて続けたします。

### <a name="example"></a>例

```cpp
// startup_time.cpp
// compile with: /clr
using namespace System;

int main( )
{
   Int32 tc = Environment::TickCount;
   Int32 seconds = tc / 1000;
   Int32 minutes = seconds / 60;
   float hours = static_cast<float>(minutes) / 60;
   float days = hours / 24;

   Console::WriteLine("Milliseconds since startup: {0}", tc);
   Console::WriteLine("Seconds since startup: {0}", seconds);
   Console::WriteLine("Minutes since startup: {0}", minutes);
   Console::WriteLine("Hours since startup: {0}", hours);
   Console::WriteLine("Days since startup: {0}", days);

   return 0;
}
```

## <a name="store_text"></a> クリップボードのテキストを格納します。

次のコード例では、<xref:System.Windows.Forms.Clipboard>オブジェクトで定義されている、<xref:System.Windows.Forms>文字列を格納する名前空間。 このオブジェクトには 2 つのメンバー関数:<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>と<xref:System.Windows.Forms.Clipboard.GetDataObject%2A>します。 派生したオブジェクトを送信することによってデータがクリップボードに格納されている<xref:System.Object>に<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>します。

### <a name="example"></a>例

```cpp
// store_clipboard.cpp
// compile with: /clr
#using <System.dll>
#using <System.Drawing.dll>
#using <System.Windows.Forms.dll>

using namespace System;
using namespace System::Windows::Forms;

[STAThread] int main()
{
   String^ str = "This text is copied into the Clipboard.";

   // Use 'true' as the second argument if
   // the data is to remain in the clipboard
   // after the program terminates.
   Clipboard::SetDataObject(str, true);

   Console::WriteLine("Added text to the Clipboard.");

   return 0;
}
```

## <a name="write_data"></a> Windows レジストリにデータを書き込む

次のコード例では、<xref:Microsoft.Win32.Registry.CurrentUser>の書き込み可能インスタンスを作成するキー、<xref:Microsoft.Win32.RegistryKey>に対応するクラス、**ソフトウェア**キー。 その後、<xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> メソッドを使用して、新しいキーを作成し、キーと値のペアを追加します。

### <a name="example"></a>例

```cpp
// registry_write.cpp
// compile with: /clr
using namespace System;
using namespace Microsoft::Win32;

int main()
{
   // The second OpenSubKey argument indicates that
   // the subkey should be writable.
   RegistryKey^ rk;
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);
   if (!rk)
   {
      Console::WriteLine("Failed to open CurrentUser/Software key");
      return -1;
   }

   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");
   if (!nk)
   {
      Console::WriteLine("Failed to create 'NewRegKey'");
      return -1;
   }

   String^ newValue = "NewValue";
   try
   {
      nk->SetValue("NewKey", newValue);
      nk->SetValue("NewKey2", 44);
   }
   catch (Exception^)
   {
      Console::WriteLine("Failed to set new values in 'NewRegKey'");
      return -1;
   }

   Console::WriteLine("New key created.");
   Console::Write("Use REGEDIT.EXE to verify ");
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");
   return 0;
}
```

### <a name="remarks"></a>Remarks

レジストリにアクセスする .NET Framework を使用することができます、<xref:Microsoft.Win32.Registry>と<xref:Microsoft.Win32.RegistryKey>では、どちらも、クラスが定義されている、<xref:Microsoft.Win32>名前空間。 **レジストリ**クラスは、の静的インスタンスのコンテナー、<xref:Microsoft.Win32.RegistryKey>クラス。 各インスタンスは、ルート レジストリ ノードを表します。 インスタンスは、<xref:Microsoft.Win32.Registry.ClassesRoot>、<xref:Microsoft.Win32.Registry.CurrentConfig>、<xref:Microsoft.Win32.Registry.CurrentUser>、<xref:Microsoft.Win32.Registry.LocalMachine>、および <xref:Microsoft.Win32.Registry.Users> です。

## <a name="related-sections"></a>関連項目

<xref:System.Environment>

## <a name="see-also"></a>関連項目

[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
