---
title: "wmain の使用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "wmain 関数"
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# wmain の使用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 固有の仕様 →**  
  
 Unicode プログラミング モデルでは、**main** 関数のワイド文字バージョンを定義できます。  Unicode プログラミング モデルに準拠した移植性のあるコードを作成する場合は、**main** ではなく **wmain** を使用します。  
  
## 構文  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
## 解説  
 **wmain** に渡す仮引数は、**main** に渡す際の形式に準拠して宣言します。  さらに、ワイド文字の引数と、必要であればワイド文字環境ポインターもプログラムに渡すことができます。  **wmain** の `argv` パラメーターおよび `envp` パラメーターは `wchar_t*` 型です。  次に例を示します。  
  
 プログラムが **main** 関数を使用している場合、マルチバイト文字環境は、プログラムの起動時にランタイム ライブラリが作成します。  マルチバイト文字環境で使われるワイド文字のコピーは、必要に応じて作成されます \(たとえば、`_wgetenv` 関数や `_wputenv` 関数が呼び出されたとき\)。  `_wputenv` を最初に呼び出すとき、または MBCS 環境が既に存在する場合に `_wgetenv` を最初に呼び出すとき、対応するワイド文字列環境が作成され、その後は作成されたワイド文字列環境が `_wenviron` グローバル変数 \(`_environ` グローバル変数のワイド文字バージョン\) によって参照されます。  この時点までで、2 つの環境のコピー \(MBCS および Unicode\) が同時に存在していることになるわけですが、両方ともプログラムが消滅するまでオペレーティング システムによって保持されます。  
  
 プログラムが **wmain** 関数を使っている場合は、ワイド文字環境がプログラムの起動時に作成され、また `_wenviron` グローバル変数によって環境のアドレスが示されます。  MBCS \(ASCII\) 環境は、`_putenv` または `getenv` を初めて呼び出したときに作成され、`_environ` グローバル変数によってアドレスが示されます。  
  
 MBCS 環境の詳細については、「*ランタイム ライブラリ リファレンス*」の「[国際化](../c-runtime-library/internationalization.md)」を参照してください。  
  
 **END Microsoft 固有の仕様**  
  
## 参照  
 [main 関数とプログラム実行](../c-language/main-function-and-program-execution.md)