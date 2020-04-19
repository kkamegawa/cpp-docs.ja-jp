---
title: トークンの概要
ms.date: 11/04/2016
ms.assetid: 2978cbf6-e66e-46fc-9938-caa052f2ccf7
ms.openlocfilehash: 4fdc1cf4c4e5a89cc9ecf029e64b6eb5422cd6a3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149116"
---
# <a name="summary-of-tokens"></a>トークンの概要

*token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*keyword*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*punctuator*

*preprocessing-token*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*header-name*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*character-constant*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*string-literal*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*operator punctuator*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;上記のいずれでもない空白以外の各文字

*header-name*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**\<**  *path-spec*  **>**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**"**  *path spec*  **"**

*path-spec*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;有効なファイル パス

*pp-number*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**.** *digit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *digit* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **e**  *sign*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **E**  *sign*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pp-number*  **.**

## <a name="see-also"></a>関連項目

[字句文法](../c-language/lexical-grammar.md)
