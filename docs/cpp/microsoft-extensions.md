---
title: Microsoft 拡張機能
ms.date: 11/04/2016
helpviewer_keywords:
- Microsoft extensions to C/C++
ms.assetid: 68654516-24ef-4f33-aae2-175f86cc1979
ms.openlocfilehash: d8104c2df2335e11dcb711108d566e0fdd069762
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62301774"
---
# <a name="microsoft-extensions"></a>Microsoft 拡張機能

*asm ステートメント*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm**  *assembly-instruction* **;**<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__asm {**  *assembly-instruction-list*  **} ;**<sub>opt</sub>

*アセンブリの命令リスト*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **;**<sub>opt</sub> <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assembly-instruction* **;** *assembly-instruction-list* **;**<sub>opt</sub>

*ms-modifier-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ms-modifier* *ms-modifier-list*<sub>opt</sub>

*ms-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__cdecl**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ _fastcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ _stdcall**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ _syscall** (今後の実装の予約済み)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ _oldcall** (今後の実装の予約済み)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**_ _unaligned** (今後の実装の予約済み)<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*ベースの修飾子*

*ベース修飾子*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__based (** *based-type* **)**

*ベース型*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*名*