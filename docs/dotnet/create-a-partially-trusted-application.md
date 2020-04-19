---
title: '方法: 部分的に信頼されたアプリケーションの作成 (C +/cli CLI)'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
ms.openlocfilehash: afdfb8ca11753d7def9d7da6f431082b1a90c345
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209123"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>方法: CRT ライブラリ DLL への依存関係を削除することで部分的に信頼されたアプリケーションを作成します。

このトピックでは、Visual C を使用して、msvcm90.dll との依存関係を削除することで、部分的に信頼された共通言語ランタイム アプリケーションを作成する方法について説明します。

Visual C アプリケーションで構築された **/clr** C ランタイム ライブラリの一部である msvcm90.dll との依存関係になります。 部分信頼環境で使用するアプリケーションを実行する場合に、特定のコード アクセス セキュリティ規則、DLL が CLR に適用されます。 そのため、msvcm90.dll とにはネイティブ コードが含まれていますとにコード アクセス セキュリティ ポリシーを適用することはできませんので、この依存関係を削除する必要があります。

使用する必要があります、アプリケーションは、C ランタイム ライブラリの機能は使用しないで、コードからこのライブラリの依存関係を削除したい場合は、**とき**リンカー オプションとリンクします。 これらのライブラリは、初期化と、アプリケーションの初期化解除用のオブジェクト ファイルを含めることが、例外クラスは、初期化コードで使用され、例外処理コードを管理します。 これらのライブラリのいずれかでリンクすると、msvcm90.dll との依存関係が削除されます。

> [!NOTE]
>  Ptrust ライブラリを使用するアプリケーションのアセンブリの初期化の順序が異なる場合があります。 通常のアプリケーションでは、アセンブリは通常は読み込まれますが、これは保証されませんが、逆の順序でアンロードします。 部分信頼アプリケーションでは、アセンブリは通常に読み込まれる順序と同じ順序でアンロードします。 これは、または保証されません。

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>部分的に信頼を作成するには、混合 (/clr) アプリケーション

1. Msvcm90.dll との依存関係を削除するを使用してこのライブラリを含めないようにリンカーに指定する必要があります、**とき**リンカー オプション。 この操作は、Visual Studio 開発環境を使用またはプログラムを参照してください。 方法について[/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md)します。

1. リンカー入力の依存関係を ptrustm ライブラリを追加できます。 リリース モードでアプリケーションを構築している場合は、ptrustm.lib を使用します。 デバッグ モードでは、ptrustmd.lib を使用します。 この操作は、Visual Studio 開発環境を使用またはプログラムを参照してください。 方法について[します。Lib ファイルをリンカー入力として](../build/reference/dot-lib-files-as-linker-input.md)します。

## <a name="see-also"></a>関連項目

[混在 (ネイティブおよびマネージド) アセンブリ](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[混在アセンブリの初期化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[混在アセンブリのためのライブラリ サポート](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (リンカーにオプションを渡す)](../build/reference/link-pass-options-to-linker.md)
