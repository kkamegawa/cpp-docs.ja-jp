---
title: "String Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.string.F1"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "String editor"
  - "string tables"
  - "string tables, String editor"
  - "string editing"
  - "string editing, string tables"
  - "resource editors, String editor"
  - "strings [C++], editing"
ms.assetid: f71ab8de-3068-4e29-8e28-5a33d18dd416
caps.latest.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# String Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

文字列テーブルは、アプリケーションのすべての文字列の ID、値、キャプションの一覧が含まれる Windows リソースです。 たとえば、文字列テーブルにはステータス バーのプロンプトがあります。  
  
 アプリケーションの開発中、いくつかの文字列テーブルを使用できます \(各言語または条件ごとに 1 つ\)。 しかし、実行可能モジュールには、文字列テーブルは 1 つしかありません。 実行中のアプリケーションは、テーブルを異なる DLL に置く場合、複数の文字列テーブルを参照することができます。  
  
 文字列テーブルにより、簡単にアプリケーションを異なる言語にローカライズできるようになります。 すべての文字列が文字列テーブルにある場合、ソース コードを変更せずに、文字列 \(およびその他のリソース\) を変換することにより、アプリケーションをローカライズすることができます。 これは通常、ソース ファイルの各種文字列を手動で検索および置換するよりも望ましい方法です。  
  
 文字列エディターを使用して、次の作業を行えます。  
  
-   [1 つ以上の文字列を検索する](../mfc/finding-a-string.md)。  
  
-   文字列テーブルに素早く[新しいエントリを挿入する](../mfc/adding-or-deleting-a-string.md)。  
  
-   [リソース ファイルから別のリソース ファイルへの文字列の移動](../mfc/moving-a-string-from-one-resource-file-to-another.md)  
  
-   [ID、Value、Caption プロパティのインプレース編集を使用し](../mfc/changing-the-properties-of-a-string.md)、変更をすぐに表示します。  
  
-   [複数の文字列の Caption プロパティの変更](../mfc/changing-the-caption-property-of-multiple-strings.md)  
  
-   [文字列への書式指定文字または特殊文字の追加](../mfc/adding-formatting-or-special-characters-to-a-string.md)  
  
    > [!NOTE]
    >  Windows では、空の文字列テーブルを作成することができません。 エントリなしの文字列テーブルを作成する場合、そのテーブルはリソース ファイルの保存時に自動的に削除されます。  
  
 マネージ プロジェクト \(共通言語ランタイムを対象とするプロジェクト\) にリソースを追加する方法については、『*.NET Framework 開発者ガイド*』の「[アプリケーションのリソース](../Topic/Resources%20in%20Desktop%20Apps.md)」を参照してください。マネージ プロジェクトにリソース ファイルを手動で追加する方法、リソースへのアクセス方法、静的なリソースの表示方法、リソース文字列をプロパティに割り当てる方法については、「[チュートリアル : Windows フォームのローカリゼーション](http://msdn.microsoft.com/ja-jp/9a96220d-a19b-4de0-9f48-01e5d82679e5)」および「[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)」をご覧ください。  
  
## 要件  
 Win32  
  
## 参照  
 [Resource Editors](../mfc/resource-editors.md)   
 [文字列](http://msdn.microsoft.com/library/windows/desktop/ms646979.aspx)   
 [文字列の概要](http://msdn.microsoft.com/library/windows/desktop/ms647465.aspx)