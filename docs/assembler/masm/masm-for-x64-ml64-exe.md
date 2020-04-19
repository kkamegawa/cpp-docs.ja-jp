---
title: x64 用 MASM (ml64.exe)
ms.date: 12/17/2019
helpviewer_keywords:
- ml64
- ml64.exe
- masm for x64
ms.assetid: 89059103-f372-4968-80ea-0c7f90bb9c91
ms.openlocfilehash: 5e324414a0d4d7e74bb28d54c1d858ef6fb9793c
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312743"
---
# <a name="masm-for-x64-ml64exe"></a>x64 用 MASM (ml64.exe)

Visual Studio には、x64 コードをターゲットにするために、32ビットおよび64ビットの Microsoft アセンブラ (MASM) の両方のバージョンが含まれています。 Ml64.exe という名前を付けます。これは、x64 アセンブラ言語を受け入れるアセンブラーです。 MASM コマンドラインツールは、Visual Studio のインストール中にC++ワークロードを選択したときにインストールされます。 MASM ツールは、個別にダウンロードすることはできません。 Visual Studio のコピーをダウンロードしてインストールする方法については、「 [Visual studio のインストール](/visualstudio/install/install-visual-studio)」を参照してください。 完全な Visual Studio IDE をインストールするのではなく、コマンドラインツールのみが必要な場合は、 [Build tools For Visual studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)をダウンロードしてください。

MASM を使用して x64 ターゲットのコードをコマンドラインでビルドするには、x64 ターゲット用の開発者コマンドプロンプトを使用する必要があります。これにより、必要なパスとその他の環境変数が設定されます。 開発者コマンドプロンプトを起動する方法の詳細については、「[コマンドラインでのC++ C/コードのビルド](../../build/building-on-the-command-line.md)」を参照してください。

Ml64.exe コマンドラインオプションの詳細については、「 [ML および Ml64.exe コマンドラインリファレンス](ml-and-ml64-command-line-reference.md)」を参照してください。

インラインアセンブラーまたは ASM キーワードの使用は、x64 ターゲットまたは ARM ターゲットではサポートされていません。 インラインアセンブラーを使用する x86 コードを x64 または ARM に移植するには、コードをC++に変換するか、コンパイラの組み込みを使用するか、アセンブラー言語のソースファイルを作成します。 Microsoft C++コンパイラは、可能な限りクロスプラットフォーム方式に近い形で、特殊な関数命令 (privileged、bit scan/test、インタロックなど) を使用できるようにするための組み込みをサポートしています。 使用可能な組み込みの詳細については、「[コンパイラの組み込み](../../intrinsics/compiler-intrinsics.md)」を参照してください。

## <a name="add-an-assembler-language-file-to-a-visual-studio-c-project"></a>アセンブラー言語ファイルを Visual Studio C++プロジェクトに追加する

Visual Studio プロジェクトシステムでは、 C++プロジェクトで MASM を使用してビルドされたアセンブラ言語ファイルがサポートされています。 X64 を完全にサポートする MASM を使用して、x64 アセンブラー言語のソースファイルを作成し、それらをオブジェクトファイルに組み込むことができます。 これらのオブジェクトファイルを、x64 ターゲット用C++にビルドされたコードにリンクすることができます。 これは、x64 インラインアセンブラーの欠如を克服するための1つの方法です。

### <a name="to-add-an-assembler-language-file-to-an-existing-visual-studio-c-project"></a>既存の Visual Studio C++プロジェクトにアセンブラー言語ファイルを追加するには

1. **ソリューション エクスプローラー**でプロジェクトを選択します。 メニューバーで、 **[プロジェクト]** 、 **[ビルドのカスタマイズ]** の順に選択します。

1. **[Visual C++ビルドカスタマイズファイル]** ダイアログボックスで、 **masm (.targets,. props)** の横にあるチェックボックスをオンにします。 **[OK]** を選択して選択内容を保存し、ダイアログボックスを閉じます。

1. メニューバーで、 **[プロジェクト]** 、 **[新しい項目の追加]** の順に選択します。

1. **[新しい項目の追加]** ダイアログボックスで、中央のウィンドウの **[ C++ファイル (.cpp)]** を選択します。 **[名前]** エディットコントロールで、.cpp ではなく、拡張子が **.asm**の新しいファイル名を入力します。 **[追加]** を選択して、ファイルをプロジェクトに追加し、ダイアログボックスを閉じます。

追加した .asm ファイルにアセンブラー言語コードを作成します。 ソリューションをビルドすると、MASM アセンブラーが呼び出され、その後、プロジェクトにリンクされるオブジェクトファイルに .asm ファイルがアセンブルされます。 シンボルへのアクセスを容易にするには、アセンブラー言語のC++ソースファイルで名前のC++装飾規則を使用するのではなく、アセンブラー関数をソースコードで `extern "C"` として宣言します。

## <a name="ml64-specific-directives"></a>ml64.exe 固有のディレクティブ

X64 を対象とするアセンブラー言語のソースコードでは、次の ml64.exe 固有のディレクティブを使用できます。

- [.ALLOCSTACK](dot-allocstack.md)

- [.ENDPROLOG](dot-endprolog.md)

- [.PUSHFRAME](dot-pushframe.md)

- [.PUSHREG](dot-pushreg.md)

- [.SAVEREG](dot-savereg.md)

- [.SAVEXMM128](dot-savexmm128.md)

- [.SETFRAME](dot-setframe.md)

さらに、ml64.exe で使用できるように[PROC](proc.md)ディレクティブが更新されました。

## <a name="32-bit-address-mode-address-size-override"></a>32-ビットアドレスモード (アドレスサイズのオーバーライド)

MASM は、メモリオペランドに32ビットレジスタが含まれている場合、0x67 アドレスサイズオーバーライドを出力します。 たとえば、次の例では、アドレスサイズのオーバーライドが生成されます。

```asm
mov rax, QWORD PTR [ecx]
mov eax, DWORD PTR [ecx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10d+0100h]
prefetch [eax]
movnti rax, QWORD PTR [r8d]
```

MASM では、32ビットの変位がメモリオペランドとしてのみ表示される場合、64ビットのアドレス指定が想定されていることを前提としています。 現在、このようなオペランドを使用した32ビットアドレス指定はサポートされていません。

最後に、次のコードに示すように、メモリオペランド内にレジスタサイズを混在させると、エラーが生成されます。

```asm
mov eax, DWORD PTR [rcx*2+r10d]
mov eax, DWORD PTR [ecx*2+r10+0100h]
```

## <a name="see-also"></a>関連項目

[Microsoft Macro Assembler リファレンス](microsoft-macro-assembler-reference.md)
