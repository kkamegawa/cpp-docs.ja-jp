---
title: C/C++ 分離アプリケーションおよび side-by-side アセンブリのトラブルシューティング
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
ms.openlocfilehash: 1bd0d7638a8e7f2e3c671229e1f8d118d681e6f4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492572"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>C/C++ 分離アプリケーションおよび side-by-side アセンブリのトラブルシューティング

依存するライブラリが見つからない場合は、C/C++ アプリケーションの読み込みに失敗する場合があります。 ここでは、C/C++ アプリケーションの読み込みに失敗するいくつかの一般的な理由について説明し、問題を解決する手順を提示します。

side-by-side アセンブリに対する依存関係を指定するマニフェストがアプリケーションに含まれていて、そのアセンブリが実行可能ファイルと同じフォルダーにも %WINDIR%\WinSxS\ フォルダーのネイティブ アセンブリ キャッシュにもプライベート アセンブリとしてインストールされていないことが原因でアプリケーションが読み込みに失敗した場合、アプリケーションを実行しようとしている Windows のバージョンに応じて、次のいずれかのエラー メッセージが表示されることがあります。

- アプリケーションを正しく初期化できませんでした (0xc0000135)。

- アプリケーション構成が正しくないため、このアプリケーションの開始に失敗しました。 アプリケーションを再度インストールすることにより問題が解決する場合があります。

- 指定されたプログラムを実行できません。

アプリケーションにマニフェストが含まれておらず、Windows が一般的な検索場所で見つけることができない DLL にアプリケーションが依存している場合、次のようなエラー メッセージが表示されることがあります。

- *必要な DLL*が見つからなかったため、このアプリケーションを開始できませんでした。 アプリケーションをインストールし直すとこの問題は解決される場合があります。

Visual Studio がインストールされていないコンピューターにアプリケーションが配置されていて、上記と似たエラー メッセージでアプリケーションがクラッシュした場合は、次の点を確認してください。

1. 「[ビジュアルC++アプリケーションの依存関係について](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md)」で説明されている手順に従います。 Dependency Walker では、アプリケーションまたは DLL のほとんどの依存関係を表示できます。 表示されていない DLL がある場合は、アプリケーションを実行するコンピューターにその DLL をインストールしてください。

1. オペレーティング システム ローダーは、アプリケーション マニフェストを使用してアプリケーションが依存するアセンブリを読み込みます。 マニフェストは、リソースとしてバイナリに埋め込むことも、個別のファイルとしてアプリケーション フォルダーにインストールすることもできます。 マニフェストがバイナリに埋め込まれているかどうかを確認するには、Visual Studio でバイナリを開き、リソースの一覧で RT_MANIFEST を探します。 埋め込みマニフェストが見つからない場合は、アプリケーションフォルダーで < binary_name > のような名前のファイルを探します。\<拡張子 > .manifest。

1. アプリケーションが side-by-side アセンブリに依存していて、マニフェストが存在しない場合は、リンカーにプロジェクトのマニフェストを生成させる必要があります。 プロジェクトの **[プロジェクトのプロパティ]** ダイアログボックスで、リンカーオプション **[マニフェストの生成]** をオンにします。

1. マニフェストがライブラリ内に埋め込まれている場合は、RT_MANIFEST の ID がこのタイプのバイナリに適した ID であることを確認します。 使用するリソース ID の詳細については、「 [Side-by-side アセンブリをリソースとして使用する (Windows)](/windows/win32/SbsCs/using-side-by-side-assemblies-as-a-resource)」を参照してください。 マニフェストが個別ファイルの場合は、XML エディターまたはテキスト エディターで開きます。 マニフェストと配置の規則の詳細については、「[マニフェスト](/windows/win32/sbscs/manifests)」を参照してください。

   > [!NOTE]
   > 埋め込みマニフェストと個別マニフェスト ファイルの両方が存在する場合、オペレーティング システム ローダーは埋め込みマニフェストを使用し、個別ファイルは無視します。 ただし、Windows XP ではその反対です。つまり、個別マニフェスト ファイルが使用され、埋め込みマニフェストは無視されます。

1. DLL が `LoadLibrary` 呼び出しによって読み込まれるときには外部マニフェストは無視されるため、すべての DLL にマニフェストを埋め込むことをお勧めします。 詳細については、「[アセンブリマニフェスト](/windows/win32/SbsCs/assembly-manifests)」を参照してください。

1. マニフェストに列挙されているすべてのアセンブリがコンピューターに正しくインストールされていることを確認します。 各アセンブリは、名前、バージョン番号、およびプロセッサ アーキテクチャでマニフェストに指定されます。 アプリケーションが side-by-side アセンブリに依存している場合は、これらのアセンブリがコンピューターに正しくインストールされていることを確認します。これにより、「[アセンブリの検索シーケンス](/windows/win32/SbsCs/assembly-searching-sequence)」で説明されているように、オペレーティングシステムローダーが検出できるようになります。 64 ビット アセンブリは、32 ビット プロセスで読み込んだり、32 ビット オペレーティング システムで実行したりできないことに注意してください。

## <a name="example"></a>例

ビジュアルC++を使用してビルドされたアプリケーション appl.exe があるとします。 アプリケーション マニフェストは、ID が 1 のバイナリ リソース RT_MANIFEST として appl.exe 内に埋め込まれているか、個別ファイル appl.exe.manifest として格納されています。 このマニフェストの内容は次のようになります。

```
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <dependency>
    <dependentAssembly>
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>
    </dependentAssembly>
  </dependency>
</assembly>
```

このマニフェストは、オペレーティング システム ローダーに対して、appl.exe が、32 ビットの x86 プロセッサ アーキテクチャ用にビルドされた Fabrikam.SxS.Library という名前のバージョン 2.0.20121.0 のアセンブリに依存していることを通知します。 依存 side-by-side アセンブリは、共有アセンブリまたはプライベート アセンブリとしてインストールできます。

共有アセンブリのアセンブリ マニフェストは、%WINDIR%\WinSxS\Manifests\ フォルダーにインストールされます。 また、アセンブリを識別して、その内容 (アセンブリに含まれる DLL) を一覧表示します。

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
   <noInheritable/>
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>
</assembly>
```

Side-by-side アセンブリでは、[発行元の構成ファイル](/windows/win32/SbsCs/publisher-configuration-files)(ポリシーファイルとも呼ばれます) を使用して、同じアセンブリの別のバージョンではなく、side-by-side アセンブリの1つのバージョンを使用するようにアプリケーションとアセンブリをグローバルにリダイレクトすることもできます。 共有アセンブリのポリシーは、%WINDIR%\WinSxS\Policies\ フォルダーで確認できます。 ポリシー ファイルの例を次に示します。

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">

   <assemblyIdentity type="win32-policy" name="policy.2.0.Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <dependency>
      <dependentAssembly>
         <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
         <bindingRedirect oldVersion="2.0.10000.0-2.0.20120.99" newVersion="2.0.20121.0"/>
      </dependentAssembly>
   </dependency>
</assembly>
```

このポリシー ファイルは、アプリケーションまたはアセンブリが、このアセンブリのバージョン 2.0.10000.0 を要求する場合は、代わりにシステムに現在インストールされているバージョン 2.0.20121.0 を使用するように指定しています。 アプリケーションのマニフェストで示されたアセンブリのバージョンがポリシー ファイルに指定されている場合、ローダーは、マニフェストで指定されたバージョンのアセンブリを、%WINDIR%\WinSxS\ フォルダーで探します。このバージョンがインストールされていない場合、読み込みは失敗します。 バージョン 2.0.20121.0 のアセンブリがインストールされていない場合、バージョン 2.0.10000.0 のアセンブリを要求するアプリケーションで読み込みが失敗します。

ただし、アセンブリは、インストールされたアプリケーションのフォルダーにプライベート side-by-side アセンブリとしてインストールされている可能性もあります。 オペレーティング システムは、共有アセンブリとしてのアセンブリの検出に失敗した場合、そのアセンブリをプライベート アセンブリとして次の順序で検索します。

1. アプリケーションフォルダーで、assemblyName > マニフェストという名前\<のマニフェストファイルがあるかどうかを確認します。 この例では、ローダーは、appl.exe が格納されているフォルダーで Fabrikam.SxS.Library.manifest を検索します。 マニフェストが見つかった場合、ローダーはアプリケーション フォルダーからアセンブリを読み込みます。 アセンブリが見つからない場合、読み込みは失敗します。

1. Appl.exe が格納さ\\れて\>いるフォルダーで < assemblyname \ フォルダーを開き、assemblyname\>\ が\\< 場合は、assemblyname > という名前\<のマニフェストファイルを読み込もうとします。このフォルダーからのマニフェスト。 マニフェストが見つかった場合、ローダーは\\< assemblyName\>\ フォルダーからアセンブリを読み込みます。 アセンブリが見つからない場合、読み込みは失敗します。

ローダーが依存アセンブリを検索する方法の詳細については、「[アセンブリの検索シーケンス](/windows/win32/SbsCs/assembly-searching-sequence)」を参照してください。 ローダーがプライベート アセンブリとしての依存アセンブリの検出に失敗した場合、読み込みは失敗し、"指定されたプログラムを実行できません。" というメッセージが表示されます。 このエラーを解決するには、依存アセンブリとそれを構成する DLL をプライベート アセンブリまたは共有アセンブリとしてコンピューターにインストールする必要があります。

## <a name="see-also"></a>関連項目

[分離アプリケーションおよび side-by-side アセンブリの概念](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[C/C++ 分離アプリケーションおよび side-by-side アセンブリのビルド](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
