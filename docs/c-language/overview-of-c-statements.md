---
title: "C ステートメントの概要 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- semicolon, in C statements
- statements, C
- semicolon
- statements, about statements
- Visual C, statements
ms.assetid: 0d49837a-5399-4881-b60c-af5f4e9720de
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: c47620477da286e8592c6742ceee6efb90143ec2
ms.lasthandoff: 02/24/2017

---
# <a name="overview-of-c-statements"></a>C ステートメントの概要
C ステートメントは、トークン、式、および他のステートメントで構成されます。 別のステートメントの構成要素となるステートメントは、外側のステートメントの "本体" と呼ばれます。 このセクションでは、次の構文で示されたステートメントの種類それぞれについて説明します。  
  
## <a name="syntax"></a>構文  
 *statement*:  
 [labeled-statement](../c-language/goto-and-labeled-statements-c.md)  
  
 [compound-statement](../c-language/compound-statement-c.md)  
  
 [expression-statement](../c-language/expression-statement-c.md)  
  
 [selection-statement](../c-language/if-statement-c.md)  
  
 [iteration-statement](../c-language/do-while-statement-c.md)  
  
 [jump-statement](../c-language/break-statement-c.md)  
  
 [try-except-statement](../c-language/try-except-statement-c.md)  
  
 /* Microsoft 固有の仕様 \*/[try-finally-statement](../c-language/try-finally-statement-c.md) /\* Microsoft 固有の仕様 \*/  
  
 ステートメント本体が "複合ステートメント" であることはよくあります。 複合ステートメントは、キーワードも含めて、他のステートメントで構成されます。 複合ステートメントは、中かっこ (**{ }**) で区切られます。 他の C ステートメントはすべてセミコロン (**;**) で終了します。 セミコロンはステートメントの終端記号です。  
  
 式ステートメントは、「[式と代入](../c-language/expressions-and-assignments.md)」で説明されている算術演算子または論理演算子を含むことができる C 式を含みます。 null ステートメントは空のステートメントです。  
  
 どの C ステートメントも、名前とコロンで構成される識別ラベルを先頭に置くことができます。 ステートメント ラベルを認識するのは `goto` ステートメントだけであるため、ステートメント ラベルについては `goto` と一緒に説明しています。 詳細については、「[goto ステートメントとラベル付きステートメント](../c-language/goto-and-labeled-statements-c.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ステートメント](../c-language/statements-c.md)