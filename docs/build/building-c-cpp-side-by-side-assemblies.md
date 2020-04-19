---
title: C/C++ side-by-side アセンブリのビルド
ms.date: 11/04/2016
helpviewer_keywords:
- side-by-side applications [C++]
ms.assetid: 7fa20b16-3737-4f76-a0b5-1dacea19a1e8
ms.openlocfilehash: 6e49ba72a397efb97437a2f7e6d721c782875c48
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493326"
---
# <a name="building-cc-side-by-side-assemblies"></a>C/C++ side-by-side アセンブリのビルド

[Side-by-side アセンブリ](/windows/win32/SbsCs/about-side-by-side-assemblies-)は、アプリケーションが実行時に使用できるリソース (dll のグループ、windows クラス、COM サーバー、タイプライブラリ、またはインターフェイス) のコレクションです。 アセンブリに Dll を再パッケージ化する主な利点は、複数のバージョンのアセンブリを同時にアプリケーションで使用できることと、更新プログラムのリリース時に現在インストールされているアセンブリに対してサービスを実行できることです。

C++アプリケーションでは、アプリケーションのさまざまな部分で1つまたは複数の dll を使用できます。 実行時には、Dll がメインプロセスに読み込まれ、必要なコードが実行されます。 アプリケーションは、要求された Dll を検索するためにオペレーティングシステムに依存しており、他の依存 Dll を読み込む必要があることを理解し、要求された DLL と一緒に読み込む必要があります。 Windows XP、Windows Server 2003、および Windows Vista より前のバージョンの Windows オペレーティングシステムでは、オペレーティングシステムローダーは、アプリケーションのローカルフォルダーまたはシステムパスで指定された別のフォルダーのいずれかで依存 Dll を検索します。 Windows XP、Windows Server 2003、および Windows Vista では、オペレーティングシステムローダーは、[マニフェスト](/windows/win32/sbscs/manifests)ファイルを使用して依存 dll を検索し、これらの dll が含まれている side-by-side アセンブリを検索することもできます。

既定では、Visual Studio でビルドされた DLL には、ID が2に等しい RT_MANIFEST リソースとして埋め込まれた[アプリケーションマニフェスト](/windows/win32/SbsCs/application-manifests)があります。 このマニフェストは、実行可能ファイルの場合と同様に、この DLL の依存関係を他のアセンブリに記述します。 これは、DLL が side-by-side アセンブリに含まれておらず、この DLL に依存しているアプリケーションがアプリケーションマニフェストを読み込んで使用するのではなく、オペレーティングシステムローダーに依存してシステムパスでこの DLL を検索することを前提としています。

> [!NOTE]
> DLL は、アプリケーションマニフェストを使用して、ID が2に等しいリソースとしてマニフェストを埋め込むことが重要です。 DLL が実行時に動的に読み込まれる場合 (たとえば、 [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw)関数を使用する場合)、オペレーティングシステムローダーは、dll のマニフェストで指定されている依存アセンブリを読み込みます。 Dll の外部アプリケーションマニフェストは、 `LoadLibrary`呼び出し中にチェックされません。 マニフェストが埋め込まれていない場合、ローダーは、正しくないバージョンのアセンブリを読み込もうとしたり、依存アセンブリを検索するために見つからなかったりすることがあります。

1つまたは複数の関連する Dll を、対応する[アセンブリマニフェスト](/windows/win32/SbsCs/assembly-manifests)と共に side-by-side アセンブリに再パッケージ化できます。これにより、アセンブリを形成するファイルと、他の side-by-side アセンブリでのアセンブリの依存関係が記述されます。

> [!NOTE]
> アセンブリに1つの DLL が含まれている場合は、アセンブリマニフェストをこの DLL に1と等しい ID を持つリソースとして埋め込み、プライベートアセンブリに DLL と同じ名前を付けることをお勧めします。 たとえば、dll の名前が mylibrary .dll の場合、マニフェストの\<assemblyIdentity > 要素で使用されている name 属性の値は、mylibrary でもかまいません。 場合によっては、ライブラリに .dll 以外の拡張子が付いている (たとえば、MFC ActiveX コントロールプロジェクトで .ocx ライブラリが作成される) と、外部アセンブリマニフェストを作成できます。 この場合、アセンブリとそのマニフェストの名前は、DLL の名前と異なる必要があります (たとえば、MyAssembly、MyAssembly、mylibrary .ocx など)。 ただし、このようなライブラリの名前を拡張子 .dll に変更し、マニフェストをリソースとして埋め込んで、このアセンブリの将来のメンテナンスコストを削減することもお勧めします。 オペレーティングシステムがプライベートアセンブリを検索する方法の詳細については、「[アセンブリの検索シーケンス](/windows/win32/SbsCs/assembly-searching-sequence)」を参照してください。

この変更により、対応する Dll をアプリケーションのローカルフォルダー内の[プライベートアセンブリ](/windows/win32/Msi/private-assemblies)として、または WinSxS アセンブリキャッシュ内の[共有アセンブリ](/windows/win32/Msi/shared-assemblies)として配置できます。 この新しいアセンブリの正しい実行時動作を実現するために、いくつかの手順に従う必要があります。これらの詳細については、「 [Side-by-side アセンブリを作成するためのガイドライン](/windows/win32/SbsCs/guidelines-for-creating-side-by-side-assemblies)」を参照してください。 アセンブリが正しく作成されると、共有アセンブリまたはプライベートアセンブリとして、またはそれに依存するアプリケーションと共に配置できます。 Side-by-side アセンブリを共有アセンブリとしてインストールする場合は、「 [WINDOWS XP でのサイドバイサイド共有のための Win32 アセンブリのインストール](/windows/win32/Msi/installing-win32-assemblies-for-side-by-side-sharing-on-windows-xp)」に記載されているガイドラインに従うか、または[マージモジュール](/windows/win32/msi/merge-modules)を使用することができます。 Side-by-side アセンブリをプライベートアセンブリとしてインストールする場合は、インストールプロセスの一部として、対応する DLL、リソース、およびアセンブリマニフェストをターゲットコンピューターのアプリケーションローカルフォルダーにコピーするだけで、このアセンブリが実行時にローダーによって検出されました (「[アセンブリ検索シーケンス](/windows/win32/SbsCs/assembly-searching-sequence)」を参照してください)。 もう1つの方法として、 [Windows インストーラー](/windows/win32/Msi/windows-installer-portal)を使用し、「Win32 アセンブリのインストール」で説明されているガイドラインに従って[、Windows XP でアプリケーションをプライベートに使用](/windows/win32/Msi/installing-win32-assemblies-for-the-private-use-of-an-application-on-windows-xp)します。

## <a name="see-also"></a>関連項目

[C/C++ 分離アプリケーションのビルド](building-c-cpp-isolated-applications.md)<br/>
[C/C++ 分離アプリケーションおよび side-by-side アセンブリのビルド](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
