---
title: 厳密名アセンブリ (アセンブリ署名) (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
ms.openlocfilehash: ac46d069ece3c75af93f93497169d054b45267d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384583"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>厳密名アセンブリ (アセンブリ署名) (C++/CLI)

このトピックでは、アセンブリに厳密な名前を与えると呼ばれます、アセンブリに署名する方法について説明します。

## <a name="remarks"></a>Remarks

Visual C を使用する場合は、アセンブリの署名の CLR 属性に関連する問題を回避するために、アセンブリに署名するリンカー オプションを使用します。

- <xref:System.Reflection.AssemblyDelaySignAttribute>

- <xref:System.Reflection.AssemblyKeyFileAttribute>

- <xref:System.Reflection.AssemblyKeyNameAttribute>

属性を使用しない理由には、キー名がアセンブリのメタデータは、ファイル名には、機密情報が含まれている場合、セキュリティが脅かされることができますに表示されることが含まれます。 また、Visual C の開発環境で使用されるビルド プロセスには、アセンブリに署名されている CLR 属性を使用して、アセンブリに厳密な名前を指定し、アセンブリの後処理 mt.exe のようなツールを実行すると、キーが無効になります。

コマンドラインでビルドして、リンカー オプションを使用して、アセンブリに署名し、(mt.exe) のような処理後のツールを実行しての場合は、sn.exe を使用してアセンブリを再署名する必要があります。 または、ビルド、アセンブリに遅延署名し、処理後のツールを実行した後、署名を完了します。

Sn.exe を明示的に呼び出すことによってアセンブリに署名する場合は、開発環境で構築するときに署名属性を使用すると、正常にできます ([Sn.exe (厳密名ツール)](/dotnet/framework/tools/sn-exe-strong-name-tool)) でビルド後のイベント。 詳細については、「[ビルド イベントの指定](../build/specifying-build-events.md)」を参照してください。 属性、およびリンカー オプションを使用する場合に比べて、ビルド後イベントを使用する場合は、ビルド時間は以下で指定できます。

次のリンカー オプションは、アセンブリの署名をサポートします。

- [/DELAYSIGN (アセンブリの部分署名)](../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE (アセンブリに署名するためのキーまたはキー ペアの指定)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER (アセンブリに署名するためのキー コンテナーの指定)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

厳密なアセンブリの詳細については、次を参照してください。[の作成と using strong-named Assemblies](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)します。

## <a name="see-also"></a>関連項目

[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
