---
title: "/Gs (スタック チェック呼び出しの制御) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/GS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/GS コンパイラ オプション [C++]"
  - "無効化 (スタック プローブを)"
  - "GS コンパイラ オプション [C++]"
  - "-GS コンパイラ オプション [C++]"
  - "スタック チェック呼び出し"
  - "スタック プローブ"
  - "スタック, スタック プローブ"
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 17
---
# /Gs (スタック チェック呼び出しの制御)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

スタック プローブを制御します。  
  
## 構文  
  
```  
/Gs[size]  
```  
  
## 引数  
 `size`  
 \(オプション\) スタック プローブが開始される前にローカル変数が占有することのできるバイト数。  **\/Gs** オプションが `size` 引数なしで指定された場合、**\/Gs0** を指定するのと同じことになります。  
  
## 解説  
 スタック プローブとは、コンパイラがすべての関数呼び出しに挿入するコードのシーケンスのことです。  スタック プローブを開始すると、関数のローカル変数を保存するのに必要なスペースの量に応じてメモリに作用します。  
  
 関数でローカル変数用に `size` バイトを超えるスタック領域が必要な場合、スタック プローブが開始されます。  既定で、関数に 1 ページを超えるスタック領域が必要な場合、コンパイラはスタック プローブを開始するコードを生成します。  これは、x86 の **\/Gs4096**、[!INCLUDE[vcprx64](../Token/vcprx64_md.md)]、および ARM プラットフォームのコンパイラ オプションと同等です。  この値により、アプリケーションと Windows メモリ マネージャーは、実行時に動的にプログラム スタックにコミットされるメモリの量を増やすことができます。  
  
> [!NOTE]
>  **\/Gs4096** の既定値により、Windows のアプリケーションのプログラム スタックは実行時に正常に増加することができます。  既定値は、変更理由が明確でない限り変えないことをお勧めします。  
  
 仮想デバイス ドライバーなど一部のプログラムでは、この既定のスタック増加メカニズムは必要ありません。  そのような場合、スタック プローブは必要ではありません。コンパイラがそれらを生成しないようにするには、ローカル変数ストレージでどの関数が必要とする値よりも `size` の値を大きく設定します。  **\/Gs** と `size` の間には空白を入れられません。  
  
 **\/Gs0** は、ローカル変数のストレージが必要なすべての関数呼び出しでスタック プローブをアクティベートします。  これはパフォーマンスに対して悪影響を及ぼす可能性があります。  
  
 スタック プローブの有効\/無効は、[check\_stack](../../preprocessor/check-stack.md) で切り替えることができます。  **\/Gs** および `check_stack` プラグマは標準 C ライブラリ ルーチンに影響を及ぼしません。コンパイルする関数にのみ影響します。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ ページ\]** ダイアログ ボックスを開きます。  詳細については、「[方法 : プロジェクト プロパティ ページを開く](../../misc/how-to-open-project-property-pages.md)」を参照してください。  
  
2.  **\[C\/C\+\+\]** フォルダーを選択します。  
  
3.  **\[コマンド ライン\]** プロパティ ページを選択します。  
  
4.  \[追加のオプション\]ボックスにコンパイラ オプションを入力します。  
  
### このコンパイラ オプションをコードから設定するには  
  
-   「<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>」を参照してください。  
  
## 参照  
 [コンパイラ オプション](../../build/reference/compiler-options.md)   
 [コンパイラ オプションの設定](../Topic/Setting%20Compiler%20Options.md)