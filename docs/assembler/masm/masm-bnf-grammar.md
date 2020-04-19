---
title: Microsoft マクロアセンブラー BNF 文法
description: BNF x64 用 MASM の説明。
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), BNF reference
ms.openlocfilehash: 29eae0b110f99f1f417e153f18aa2ac3aff5c69b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75322824"
---
# <a name="microsoft-macro-assembler-bnf-grammar"></a>Microsoft マクロアセンブラー BNF 文法

このページには、MASM 文法の BNF の説明が含まれています。 参照トピックへの補足として提供されており、完全であるとは限りません。 キーワード、パラメーター、操作などの詳細については、リファレンストピックを参照してください。

BNF の使用方法を示すために、次の図は、非終端要素*Typedefdir*で始まる TYPEDEF ディレクティブの定義を示しています。

![MASM BNF の例](media/bnf.png)

各水平中かっこの下のエントリは、さらに定義できる端末 ( **NEAR16**、 **NEAR32**、 **FAR16**、 **FAR32**など) または非終端 (*修飾子*、 *qualifiedType*、*距離*、 *protoSpec*など) です。 *Typedefdir*定義で斜体になっている各非終端要素は、BNF 内のエントリでもあります。 3つの縦線は、非終端要素の分岐定義を示しています。わかりやすくするために、この図は説明しません。

BNF 文法では、再帰的な定義が許可されます。 たとえば、文法では、qualifiedType の定義として qualifiedType を使用します。これは、修飾子の定義のコンポーネントでもあります。 "|" 記号は、代替式から選択を指定します (例: *Endofline* | *comment*)。 二重中かっこでは、省略可能なパラメーターを指定します (⟦*マクロ Parmlist* ⟧など)。 角かっこは、実際にはソースコードには表示されません。

## <a name="masm-nonterminals"></a>MASM Nonterminals

*;;* \
&nbsp;&nbsp;&nbsp;&nbsp;*Endofline* | *コメント*

*= Dir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* = *immExpr* ;;

*Addop*\
&nbsp;&nbsp;&nbsp;&nbsp;+ |-

*Aexpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*用語* | *aexpr* && *term*

*Altid*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;*charList*

*asmInstruction*\
&nbsp;&nbsp;&nbsp;&nbsp;*ニーモニック*⟦ *exprlist* ⟧

*assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;を**想定**して*assumeList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| **何も想定**していません。

*assumeList*\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeRegister* | *assumeList* 、 *assumeRegister*\

*assumeReg*\
&nbsp;&nbsp;&nbsp;&nbsp;*レジスタ*: *assumeVal*

*assumeRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;*assumeSegReg* | *assumeReg*

*assumeSegReg*\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentRegister* : *assumeSegVal*

*assumeSegVal*\
&nbsp;&nbsp;&nbsp;&nbsp;*フレーム式* | **NOTHING** | **エラー**

*assumeVal*\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedType* | **NOTHING** | **エラー**

*Bcdconst*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *sign* ⟧ *decnumber*

*Binaryop*\
&nbsp;&nbsp;&nbsp;&nbsp;= = |! = |> = |< = |> |< |&

*Bitdef*\
&nbsp;&nbsp;&nbsp;&nbsp;*bitfieldid* : *bitfieldid* ⟦ = *constExpr* ⟧

*Bitdeflist*\
&nbsp;&nbsp;&nbsp;&nbsp;*Bitdef* | *bitdeflist* , ⟦;;⟧ *Bitdef*

*bitfieldid*
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*Bitfieldsize*\
&nbsp;&nbsp;&nbsp;*constExpr* &nbsp;

*Blockstatements*の\
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。続行** **します。** *Cexpr* ⟧ \ の場合
&nbsp;&nbsp;&nbsp;&nbsp;|  **。** ⟦**を中断します。** *Cexpr* ⟧の場合

*bool*\
&nbsp;&nbsp;&nbsp;&nbsp;**TRUE** | **FALSE**

*byteRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;AL |AH |CL |CH |DL |DH |BL |BH |R8B |R9B |R10B |R11B |R12B |R13B |R14B |R15B

*Cexpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*aexpr* | *Cexpr* || *aexpr*

*文字*\
&nbsp;&nbsp;&nbsp;は、改行 (10) を除く 0 ~ 255 の範囲の序数を持つ任意の文字を &nbsp;します。

*charList*\
&nbsp;&nbsp;&nbsp;&nbsp;*文字* | *charList*文字

*className*\
&nbsp;&nbsp;&nbsp;&nbsp;*文字列*

*Commdecl*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *nearfar* ⟧⟦ *langType* ⟧ *id* : *commtype*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦: *constExpr* ⟧

*Commdir*\
&nbsp;&nbsp;&nbsp;&nbsp;**通信**\
&nbsp;&nbsp;&nbsp;&nbsp;*Commlist* ;;

*コメント*\
&nbsp;&nbsp;&nbsp;&nbsp;;*text* ;;

*コメントディレクトリ*\
&nbsp;&nbsp;&nbsp;&nbsp;**コメント***区切り記号*\
&nbsp;&nbsp;&nbsp;&nbsp;*テキスト*\
&nbsp;&nbsp;&nbsp;&nbsp;*テキスト* *区切り* *文字;;*

*Commlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*commdecl* | *commdecl* 、 *commdecl*

*Commtype*\
&nbsp;&nbsp;&nbsp;&nbsp;*型* | *constExpr*

*定数*\
&nbsp;&nbsp;&nbsp;&nbsp;*数字*⟦*放射 xoverride* ⟧

*constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

*Contextdir*\
&nbsp;&nbsp;&nbsp;&nbsp;**Pushcontext** *contextItemList* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;**Popcontext** *contextItemList* ;;

*contextItem*\
&nbsp;&nbsp;&nbsp;&nbsp;**は |  | ** **CPU** | **すべて**を**一覧表**示して**い**ます。

*contextItemList*\
&nbsp;&nbsp;&nbsp;&nbsp;*contextItem* | *contextItemList* 、 *contextItem*

*Controlblock*\
&nbsp;&nbsp;&nbsp;&nbsp;時*ブロック* | *repeatblock*

*Controldir*\
&nbsp;&nbsp;&nbsp;&nbsp;*controlIf* | *controlblock*

*Controlelseif*\
&nbsp;&nbsp;&nbsp;&nbsp; **。ELSEIF** &nbsp;&nbsp;&nbsp;&nbsp;*cexpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Controlelseif* ⟧

*controlIf*\
&nbsp;&nbsp;&nbsp;&nbsp; **。&nbsp;&nbsp;** &nbsp;&nbsp;*cexpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Controlelseif* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ **。その他**;; \
&nbsp;&nbsp;&nbsp;&nbsp;[*directiveList*⟧ \
&nbsp;&nbsp;&nbsp;&nbsp; **。ENDIF** ;;

*コプロセッサ*\
&nbsp;&nbsp;&nbsp;&nbsp;. 8087 |. 287 |. 387 |。NO87

*Crefdir*\
&nbsp;&nbsp;&nbsp;&nbsp;*Crefoption* ;;

*Crefoption*\
&nbsp;&nbsp;&nbsp;&nbsp; **。CREF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。XCREF** ⟦ *idlist* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。NOCREF** ⟦ *idlist* ⟧

*Cxzexpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*\
&nbsp;&nbsp;&nbsp;&nbsp;|! *expr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* = = expr \
&nbsp;&nbsp;&nbsp;&nbsp;| *expr* ! = expr

*dataDecl*\
&nbsp;&nbsp;&nbsp;&nbsp;DB |DW |DD |DF |DQ |DT |*データ型* | *typeId*

*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *id* ⟧ *dataItem* ;;

*dataItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*dataDecl* *scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeId* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag* *structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Recordtag* *recordinstlist*

*データ型*\
&nbsp;&nbsp;&nbsp;&nbsp;BYTE |SBYTE |WORD |ソード |DWORD |SDWORD |FWORD |QWORD |SQWORD |T バイト |OWORD |REAL4 |REAL8 |REAL10 |MMWORD |XMMWORD |YMMWORD

*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;0 |1 |2 |3 |4 |5 |6 |7 |8 |ませ

*Decnumber*\
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Decnumber* *decnumber*

*区切り記号*\
*whiteSpaceCharacter*を除く任意の文字 &nbsp;&nbsp;&nbsp;&nbsp;

\*数字*
&nbsp;&nbsp;&nbsp;&nbsp;*decdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;| *桁*の*桁*\
&nbsp;&nbsp;&nbsp; *&nbsp;| hexdigit*

*ディレクティブ*の\
&nbsp;&nbsp;&nbsp;&nbsp;*全般ディレクトリ* | *segmentDef*

*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;*ディレクティブ* | *directiveList* *ディレクティブ*

*距離*\
&nbsp;&nbsp;&nbsp;&nbsp;*nearfar* | **NEAR16** | **NEAR32** | **FAR16** | **FAR32**

*e01*\
&nbsp;&nbsp;&nbsp;&nbsp;e01 *Orop* *e02* | *e02*

*e02*\
&nbsp;&nbsp;&nbsp;&nbsp;e02**と** *e03* | *e03*

*e03*\
&nbsp;&nbsp; **&nbsp;&nbsp;** *e04* | *e04*

*e04*\
&nbsp;&nbsp;&nbsp;&nbsp;*e04* *relop* *e05* | *e05*

*e05*\
&nbsp;&nbsp;&nbsp;&nbsp;*e05* *addop* *e06* | *e06*

*e06*\
&nbsp;&nbsp;&nbsp;&nbsp;*e06* *mulop* *e07* | *e06* *ftop* *e07* | *e07*

*e07*\
&nbsp;&nbsp;&nbsp;&nbsp;*e07* *addop* *e08* | *e08*

*e08*\
&nbsp;&nbsp;&nbsp;&nbsp;**HIGH** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **LOW** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Highword** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Lowword** *e09*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e09*

*e09*\
&nbsp;&nbsp;&nbsp;&nbsp;**OFFSET** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SEG** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Lroffset** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| **型** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;**この** *e10* | 
&nbsp;&nbsp;&nbsp;&nbsp;| *e09* **PTR** *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e09* : *e10*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e10*

*e10*\
&nbsp;&nbsp;&nbsp;&nbsp;*e10* 。 *e11*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e10* ⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *e11*

*e11*\
&nbsp;&nbsp;&nbsp;&nbsp;( *expr* ) \
&nbsp;&nbsp;&nbsp;&nbsp;|⟦ *expr* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **幅** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **マスク** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **サイズ** *siz氏*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SIZEOF** *siz氏 g*\
&nbsp;&nbsp;&nbsp;&nbsp;| **長さ** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Id* **の長さ**\
&nbsp;&nbsp;&nbsp;&nbsp;| *Recordconst*\
&nbsp;&nbsp;&nbsp;&nbsp;| *文字列*\
&nbsp;&nbsp;&nbsp;&nbsp;| *定数*\
&nbsp;&nbsp;&nbsp;&nbsp;*型*| 
&nbsp;&nbsp;&nbsp;&nbsp;| *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **$**\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;| *登録*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ST**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ST** ( *expr* )

*echoDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**ECHO**\
&nbsp;&nbsp;&nbsp;&nbsp;*arbitraryText* ;; \
%**OUT** *arbitraryText* ;; \

*elseifBlock*\
&nbsp;&nbsp;&nbsp;&nbsp;*elseifStatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \

*elseifStatement*\
&nbsp;&nbsp;&nbsp;&nbsp;**ELSEIF** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFE** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFB** *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNB** *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFNDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIF** *textitem* 、 *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFDIFI** *textitem* 、 *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDN** *textitem* 、 *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIFIDNI** *textitem* 、 *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **ELSEIF2**

*Enddir*\
&nbsp;&nbsp;&nbsp;&nbsp;**END** ⟦ *immExpr* ⟧;;

*Endpdir*\
&nbsp;&nbsp;&nbsp;&nbsp;% *id* **endp** ;;

*Endsdir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*が**終了**します;;

\ の*数式*
&nbsp;&nbsp;&nbsp;&nbsp;*Textマクロ id* **等しい**の*種類*;;

\ の*種類*
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr* | *textliteral*

*Errordir*\
&nbsp;&nbsp;&nbsp;&nbsp;*Erroropt* ;;

*Erroropt*\
&nbsp;&nbsp;&nbsp;&nbsp; **。ERR** ⟦ *textitem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRE** *constExpr* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRNZ** *constExpr* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRB** *textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRNB** *textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRDEF** *id* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRNDEF** *id* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERRDIF** *textitem* 、 *textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRDIFI** *textitem* 、 *textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRIDN** *textitem* 、 *textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERRIDNI** *textitem* 、 *textitem* ⟦ *opttext* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。ERR1** ⟦ *textitem* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **.ERR2** ⟦ *textitem* ⟧

*Exitdir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。EXIT** &nbsp;&nbsp;&nbsp;&nbsp;⟦ *expr* ⟧;;

*exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;: EXITM |EXITM *Textitem*

*指数*\
&nbsp;&nbsp;&nbsp;&nbsp;E ⟦ *sign* ⟧ *decnumber*

*expr*\
&nbsp;&nbsp;&nbsp;&nbsp;**SHORT** *e05*\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。「** E01 \」と入力します。
&nbsp;&nbsp;&nbsp;&nbsp;| **Opattr** *e01*\
&nbsp;&nbsp;&nbsp;&nbsp;| *e01*

*Exprlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* | *exprlist* 、 *expr*

*externDef*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langType* ⟧ *Id* ⟦ ( *Altid* ) ⟧: *externType*

*externDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*externKey* *externList* ;;

*externKey*\
&nbsp;&nbsp;&nbsp;&nbsp;**Extrn** | **EXTERN** | **EXTERNDEF**

*externList*\
&nbsp;&nbsp;&nbsp;&nbsp;*externDef* | *externList* 、⟦;;⟧ *externDef*

*externType*\
&nbsp;&nbsp;&nbsp;&nbsp;**ABS** | *qualifiedType*

*Fieldalign*\
&nbsp;&nbsp;&nbsp;*constExpr* &nbsp;

*fieldInit*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Initvalue* ⟧ |*structInstance*

*fieldInitList*\
&nbsp;&nbsp;&nbsp;&nbsp;*fieldInit* | *fieldInitList* 、⟦;;⟧ *fieldInit*

*fileChar*\
&nbsp;&nbsp;&nbsp;&nbsp;*区切り記号*

*Filecharlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*fileChar* | *FilfileChar arlist*

*fileSpec*\
&nbsp;&nbsp;&nbsp;&nbsp;*Fil一括 Arlist* | *textliteral*

*Flagname*\
&nbsp;&nbsp;&nbsp;&nbsp;**0?** | を受けてい**ますか?****オーバーフロー  | ますか?** | **署名しますか?** | **パリティですか?**

*floatNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *sign* ⟧ *decnumber* 。 ⟦ *Decnumber* ⟧⟦*指数*⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| *数字*R |r の*数字*

*Forcdir*\
&nbsp;&nbsp;&nbsp;&nbsp;**Forc** | **irpc**

*Fordir*\
 | **IRP** **の**&nbsp;&nbsp;&nbsp;&nbsp;

*forParm*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* ⟦: *forParmType* ⟧

*forParmType*\
&nbsp;&nbsp;&nbsp;&nbsp;**REQ** |= *Textliteral*

*Fpuregister*\
&nbsp;&nbsp;&nbsp;&nbsp;**ST** *expr*

*フレーム式*の\
&nbsp;&nbsp;&nbsp;&nbsp;**SEG** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Dgroup** : *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segmentRegister* : *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| *id*

*一般ディレクトリ*\
&nbsp;&nbsp;&nbsp;&nbsp;*Modeldir* | *segOrderDir* | *nameDir*\
&nbsp;&nbsp;&nbsp; *&nbsp;| * *コメントディレクトリ* | 
&nbsp;&nbsp;&nbsp;&nbsp;| *Groupdir* | *assumeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *structDir* | *Recorddir* | *typedefdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *externDir* | *Publicdir* | *commdir* | *protoTypeDir*\
&nbsp;&nbsp;&nbsp; *&nbsp;| の*= Dir |*Textdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Contextdir* | *Optiondir* | *processordir*\
&nbsp;&nbsp;&nbsp;&nbsp;| の*Xdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *タイトルディレクトリ* | *PageDir* | *listdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Crefdir* | *echoDir*\
&nbsp;&nbsp;&nbsp;| *ifdir* | *Errordir* | *includedir*\ &nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;| *マクロ dir* | *マクロ呼び出し* | *macroRepeat* | *purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp; *| マクロに* | *マクロにマクロ* *を* | します。
&nbsp;&nbsp;&nbsp;&nbsp;| *エイリアスディレクトリ*

*gpRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;AX |EAX |CX |ECX |DX |EDX |BX |EBX |DI |EDI |SI |ESI |BP |EBP |SP |ESP |RSP |R8W |R8D |R9W |R9D |R12D |R13W |R13D |R14W |R14D

*Groupdir*\
&nbsp;&nbsp;&nbsp;&nbsp;*groupId* **グループ** *segIdList*

*groupId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*hexdigit*\
&nbsp;&nbsp;&nbsp;&nbsp;|b |c |d |e |f ||B |C |D |E |F

*id*\
&nbsp;&nbsp;&nbsp;&nbsp;識別子の最初の文字は、大文字または小文字の英字 (`[A–Za-z]`) または次の4文字のいずれかになります。 `@ _ $ ?` 残りの文字は、これらの同じ文字または10進数字 (`[0–9]`) のいずれかになります。 最大長は247文字です。

*Idlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* | *idlist* 、 *id*

*Ifdir*\
&nbsp;&nbsp;&nbsp;&nbsp;*Ifstatement* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *elseifBlock* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ **ELSE** ;;\
&nbsp;&nbsp;&nbsp;&nbsp;*directiveList* ⟧;; \

*Ifstatement*\
*constExpr*\ の**場合**、&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;| **Ife** *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFB** *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Ifnb** *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFNDEF** *id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IFDIF** *textitem* 、 *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Ifdifi** *textitem* 、 *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Ifidn** *textitem* 、 *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Ifidni** *textitem* 、 *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF1**\
&nbsp;&nbsp;&nbsp;&nbsp;| **IF2**

*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr*

*Includedir*\
&nbsp;&nbsp;&nbsp;&nbsp;に*fileSpec*を**含め**ます。

\ の*インクルード*
&nbsp;&nbsp;&nbsp;&nbsp;を**インクルード***します。*

*Initvalue*\
&nbsp;&nbsp;&nbsp;&nbsp;*immExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;| *文字列*\
&nbsp;&nbsp;&nbsp;&nbsp;|? \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *scalarInstList* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| *floatNumber*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Bcdconst*

*inSegDir*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Labeldef* ⟧ *inSegmentDir*

*inSegDirList*\
&nbsp;&nbsp;&nbsp;&nbsp;*inSegDir* | *inSegDirList* *inSegDir*

*inSegmentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*命令*\
&nbsp;&nbsp;&nbsp;&nbsp;| *dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Controldir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Startupdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Exitdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Labeldir*\
&nbsp;&nbsp;&nbsp;&nbsp;|  *⟦* *localdirlist* ⟧⟦ *inSegDirList* ⟧ *endpdir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Invokedir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *全般ディレクトリ*

*instrPrefix*\
&nbsp;&nbsp;&nbsp;&nbsp;**REP** | **Repe** | **REPZ** | **Repnz** | **repnz** | **ロック**

*命令*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *instrPrefix* ⟧ *asmInstruction*

*Invokearg*\
&nbsp;&nbsp;&nbsp;&nbsp;*register* :: *register* | *expr* | **ADDR** *expr*

*Invokedir*\
&nbsp;&nbsp;&nbsp;&nbsp;**INVOKE** *expr* ⟦, ⟦;;⟧ *Invokelist* ⟧;;

*Invokelist*\
&nbsp;&nbsp;&nbsp;&nbsp;*Invokearg* | *invokearg* 、⟦;;⟧ *Invokearg*

*キーワード*\
予約語 &nbsp;&nbsp;&nbsp;を &nbsp;します。

*Keywordlist リスト*\
&nbsp;&nbsp;&nbsp;&nbsp;*キーワード* | *キーワード* *keywordlist リスト*

*Labeldef*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* : |*id* :: |@@:

*Labeldir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* **ラベル** *qualifiedType* ;;

*langType*\
&nbsp;&nbsp;&nbsp;&nbsp;**C** | **PASCAL** | **FORTRAN** | **BASIC** | **SYSCALL** | **STDCALL**

*Listdir*\
&nbsp;&nbsp;&nbsp;&nbsp;*Listoption* ;;

*Listoption*\
&nbsp;&nbsp;&nbsp;&nbsp; **。リスト**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。NOLIST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。XLIST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。LISTALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LISTIF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.LFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.NOLISTIF**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.SFCOND**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。TFCOND**
&nbsp;&nbsp;&nbsp;&nbsp;|  **。LISTマクロ ALL** |  **。LALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。NOLISTMACRO** |  **。SALL**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **。LISTMACRO** |  **。XALL**\

*Localdef*\
&nbsp;&nbsp;&nbsp;&nbsp;**ローカル** *idlist* ;;

*Localdir*\
&nbsp;&nbsp;&nbsp;&nbsp;**ローカル** *parmlist* ;;

*Localdirlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*localdir* | *localdirlist* *localdir*

*Locallist*\
&nbsp;&nbsp;&nbsp;&nbsp;*localdef* | *localdef* *localdef*

*マクロ arg*\
 % *constExpr*\
&nbsp;&nbsp;&nbsp;&nbsp;|%*Textマクロ id*\
&nbsp;&nbsp;&nbsp;&nbsp;|%*マクロ*の場合 id (*マクロの arglist* ) \
&nbsp;&nbsp;&nbsp;&nbsp;| *文字列*\
&nbsp;&nbsp;&nbsp;&nbsp;| *arbitraryText*\
&nbsp;&nbsp;&nbsp;&nbsp;|< *arbitraryText* >

*マクロの arglist*\
&nbsp;&nbsp;&nbsp;&nbsp;*マクロ arg* | *マクロ arglist* 、*マクロ arg*

*マクロ本文*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *Locallist* ⟧ *macroStmtList*

*マクロ呼び出し*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* *マクロ arglist* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *id* (*マクロ arglist* )

*マクロディレクトリ*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* **マクロ⟦マクロ** *parmlist* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*マクロ本文*\
&nbsp;&nbsp;&nbsp;&nbsp;**Endm** ;;

\*のマクロ*
&nbsp;&nbsp;&nbsp;&nbsp;*Fordir* *ForParm* 、<*マクロ arglist* >;; \
&nbsp;&nbsp;&nbsp;&nbsp;*マクロ本文*\
&nbsp;&nbsp;&nbsp;&nbsp;**Endm** ;;

*マクロ Forc*\
&nbsp;&nbsp;&nbsp;&nbsp;*Forcdir* *id* 、 *textliteral* ;、\
&nbsp;&nbsp;&nbsp;&nbsp;*マクロ本文*\
&nbsp;&nbsp;&nbsp;&nbsp;**Endm** ;;

*マクロ*の\ id
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*マクロ id*\
&nbsp;&nbsp;&nbsp;&nbsp;*マクロの id* | *マクロの id*

*マクロ Id リスト*\
&nbsp;&nbsp;&nbsp;&nbsp;*マクロ id* | *マクロ idlist* 、*マクロ id*

*マクロラベル*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*macroParm*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* ⟦: *parmType* ⟧

*マクロ Parmlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*macroParm* | *マクロ parmlist* 、⟦;;⟧ *macroParm*

*マクロの id*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*macroRepeat*\
&nbsp;&nbsp;&nbsp;&nbsp;*Repeatdir* *constExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*マクロ本文*\
&nbsp;&nbsp;&nbsp;&nbsp;**Endm** ;;

*マクロ stmt*\
&nbsp;&nbsp;&nbsp;&nbsp;*ディレクティブ* \
&nbsp;&nbsp;&nbsp;&nbsp;| *exitmDir*\
&nbsp;&nbsp;&nbsp;&nbsp;|:*マクロラベル*\
&nbsp;&nbsp;&nbsp;&nbsp;| **GOTO**\
&nbsp;&nbsp;&nbsp;&nbsp;*マクロラベル*

*macroStmtList*\
&nbsp;&nbsp;&nbsp;&nbsp;*マクロ stmt* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *macroStmtList* *マクロ stmt* ;; \

\*中のマクロ*
&nbsp; **&nbsp;&nbsp;&nbsp;** *constExpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*マクロ本文*\
&nbsp;&nbsp;&nbsp;&nbsp;**Endm** ;;

*Maptype*\
&nbsp;&nbsp;&nbsp;&nbsp;**すべて** | **なし** | **notpublic**

*Memoption*\
&nbsp;&nbsp; **&nbsp;&nbsp;** 小さい | **小さい** | **中** | **非常**に**大きい** | 大きな | **フラット**

*ニーモニック*\
&nbsp;&nbsp;&nbsp;&nbsp;命令名を指定します。

*Modeldir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。モデル**\
&nbsp;&nbsp;&nbsp;&nbsp;*Memoption* ⟦、 *Modeloptlist* ⟧;;

*Modelopt*\
&nbsp;&nbsp;&nbsp;&nbsp;*langType* | *stackoption*

*Modeloptlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*modelopt* | *Modeloptlist* 、 *modelopt*

*モジュール*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *directiveList* ⟧ *enddir*

*Mulop*\
&nbsp;&nbsp;&nbsp;&nbsp;\* |/ |**MOD**

*nameDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**名**\
&nbsp;&nbsp;&nbsp;&nbsp;*id* ;; \

*nearfar*\
&nbsp;&nbsp;&nbsp;&nbsp;**遠く** | **近く**

*Nestedstruct*\
&nbsp;&nbsp;&nbsp;&nbsp;*structHdr* ⟦ *id* ⟧;; \
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;**終了**、; \

*offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*offsetDirType* ;;

*offsetDirType*\
&nbsp;&nbsp;&nbsp;&nbsp; | **組織** *immExpr* | **均等**に⟦ *constExpr* ⟧に**配置**します。

*offsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;**グループ** | **セグメント** | **フラット**

*oldRecordFieldList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* ⟧ |*oldRecordFieldList* 、⟦ *constExpr* ⟧

*オプションディレクトリ*\
&nbsp;&nbsp;&nbsp;&nbsp;**オプションオプション**の*一覧*;;

*オプション項目*\
&nbsp;&nbsp;&nbsp;&nbsp;**Casemap** : *maptype*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Dotname** | **nodotname**\
&nbsp;&nbsp;&nbsp;&nbsp;| **エミュレーター** | **noemulator**\
&nbsp;&nbsp;&nbsp;&nbsp;| **エピローグ**:*マクロ id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **EXPR16** | **EXPR32**\
&nbsp;&nbsp;&nbsp;&nbsp;| **言語**: *langType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Ljmp**
| **noljmp**\
&nbsp;&nbsp;&nbsp;&nbsp;| **M510** | **NOM510**\
&nbsp;&nbsp;&nbsp;&nbsp;| **Nokeyword** : < *keywordlist リスト* >\
&nbsp;&nbsp;&nbsp;&nbsp;| **Nosignextend**\
&nbsp;&nbsp;&nbsp;&nbsp;| **オフセット**: *offsetType*\
&nbsp;&nbsp;&nbsp;&nbsp;| **Oldmacros** | **nooldmacros**\
&nbsp;&nbsp;&nbsp;&nbsp;| **oldstructs** | **nooldstructs**\
&nbsp;&nbsp;&nbsp;&nbsp;| **PROC** : *ovisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;| **プロローグ**:*マクロ id*\
&nbsp;&nbsp;&nbsp;&nbsp;| **READONLY** | **NOREADONLY**\
&nbsp;&nbsp;&nbsp;&nbsp;**スコープ**| **noscoped** | 
&nbsp;&nbsp;&nbsp;&nbsp;| **セグメント**: *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SETIF2** : bool

*オプションの一覧*\
&nbsp;&nbsp;&nbsp;&nbsp;*Optionitem* | *optionitem* 、⟦;;⟧ *Optionitem*

*Opttext*\
&nbsp;&nbsp;&nbsp;&nbsp;、 *Textitem*

*Orop*\
&nbsp;&nbsp;&nbsp;&nbsp;**または** **XOR** | 

*Ovisibility*\
&nbsp;&nbsp;&nbsp;&nbsp;**パブリック** | **プライベート** | **エクスポート**

*pageDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**ページ**⟦ *pageexpr* ⟧;;

*Pageexpr*\
&nbsp;&nbsp;&nbsp;&nbsp;\+ |⟦ *pageLength* ⟧⟦、 *pagewidth* ⟧

*pageLength*\
&nbsp;&nbsp;&nbsp;*constExpr* &nbsp;

*Pagewidth*\
&nbsp;&nbsp;&nbsp;*constExpr* &nbsp;

*parm*\
&nbsp;&nbsp;&nbsp;&nbsp;*Parmid* ⟦: *qualifiedType* ⟧ |*Parmid* ⟦ *constExpr* ⟧⟦: *qualifiedType* ⟧

*Parmid*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*Parmlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*parm* | *parmlist* 、⟦;;⟧ *parm*

*parmType*\
&nbsp;&nbsp;&nbsp;&nbsp;**REQ** |= *Textliteral* | **VARARG**

*pOptions*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *distance* ⟧⟦ *LangType* ⟧⟦ *ovisibility* ⟧

*プライマリ*\
&nbsp;&nbsp;&nbsp;&nbsp;*expr* *Binaryop* *expr* | *flagname* | *expr*

*\*
&nbsp;&nbsp;&nbsp;&nbsp;処理*id* **PROC**\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *pOptions* ⟧⟦ <*マクロ arglist* > ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *usesRegs* ⟧⟦⟧ *parmlist*

*プロセッサ*\
&nbsp;&nbsp;&nbsp;&nbsp;|. 386 |. 386p |. 486 |. 486P \
&nbsp;&nbsp;&nbsp;&nbsp;|. 586 |. 586P |. 686 |. 686P | 387

*Processordir*\
&nbsp;&nbsp;&nbsp;&nbsp;*プロセッサ*、; \
&nbsp;&nbsp;&nbsp;&nbsp;| *コプロセッサ*;;

*プロセッサ id*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*プロセッサ項目*の\
&nbsp;&nbsp;&nbsp;&nbsp;*instrPrefix* | *DataDir* | *Labeldir* | *offsetDir* | *全般ディレクトリ*

*プロセッサ一覧*の\
&nbsp;&nbsp;&nbsp;&nbsp;⟦、⟦;;⟧ *Parmlist* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦、⟦;;⟧ *Parmid* : VARARG ⟧

*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *id* ⟧: *qualifiedType*

*protoArgList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦、⟦;;⟧ *protoList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦、⟦;;⟧⟦ *id* ⟧: VARARG ⟧

*protoList*\
&nbsp;&nbsp;&nbsp;&nbsp;*protoArg*\
&nbsp;&nbsp;&nbsp;&nbsp;| *protoList* 、⟦;;⟧ *protoArg*

*protoSpec*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *distance* ⟧⟦ *langType* *⟧⟦ protoArgList* ⟧ |*typeId*

*protoTypeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* **プロトコル** *protoSpec*

*Pubdef*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *langType* ⟧ *id*

*Publicdir*\
&nbsp;&nbsp;&nbsp;&nbsp;**パブリック** *publist* ;;

*Publist*\
&nbsp;&nbsp;&nbsp;&nbsp;*Pubdef* | *pubdef* , ⟦;;⟧ *Pubdef*

*purgeDir*\
&nbsp;&nbsp;&nbsp;&nbsp;**PURGE** *マクロ idlist*

*qualifiedType*\
&nbsp;&nbsp;&nbsp;&nbsp;*種類*|⟦ *distance* ⟧ **PTR** ⟦ *qualifiedType* ⟧

*修飾子*\
&nbsp;&nbsp;&nbsp;&nbsp;*qualifiedType* | **PROTO** *protoSpec*

*引用*\
&nbsp;&nbsp;&nbsp;&nbsp;"|"

*Qwordregister*\
&nbsp;&nbsp;&nbsp;&nbsp;RAX |RCX |RDX |RBX |RDI |RSI |RBP |R8 |R9 |R10 |R11 |R12 |R13 |R14 |R15

*放射 Xdir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。基数** *constExpr* ;;

\ の*放射 Xoverride*
&nbsp;&nbsp;&nbsp;&nbsp;h |o |q |t |y |H |O |Q |T |前年

*Recordconst*\
&nbsp;&nbsp;&nbsp;&nbsp;*Recordtag* { *oldRecordFieldList* } |*Recordtag* < *oldRecordFieldList* >

*Recorddir*\
&nbsp;&nbsp;&nbsp;&nbsp;*Recordtag* **レコード**の*bitdeflist* ;;

*recordFieldList*\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *constExpr* ⟧ |*recordFieldList* , ⟦;;⟧⟦ *constExpr* ⟧

*Recordinstance*\
 {⟦;; ⟧ *recordFieldList* ⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;|< *oldRecordFieldList* >\
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *recordinstance* )

*Recordinstlist*\
&nbsp;&nbsp;&nbsp;&nbsp;*Recordinstance* | *recordinstlist* 、⟦;;⟧ *Recordinstance*

*Recordtag*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

\ の*登録*
&nbsp;&nbsp;&nbsp;&nbsp;*特殊レジスタ* | *gpRegister* | *byteRegister* | *Qwordregister* |  *fpuregister* |  *segmentRegister*

*Reglist*\
&nbsp;&nbsp;&nbsp;&nbsp;*登録* | *reglist* *レジスタ*

*\ の*再読み込み
&nbsp;&nbsp;&nbsp;&nbsp;EQ |NE |LT |LE |GT |GE

*Repeatblock*\
&nbsp;&nbsp;&nbsp;&nbsp; **。REPEAT** ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*Blockstatements* ;;Dir;、

*Repeatdir*\
&nbsp;&nbsp;&nbsp;&nbsp;**繰り返し** | **ます**。

*scalarInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*Initvalue* | *scalarInstList* , ⟦;;⟧ *Initvalue*

*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;**バイト** | **WORD** | **DWORD** | **段落** | **ページ**

*segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;**パブリック** | **スタック** | *ConstExpr* | **プライベート** **で** | **メモリ** | **共通**

*segDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。コード**\
&nbsp;&nbsp;&nbsp;&nbsp;⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。データ**\
&nbsp;&nbsp;&nbsp;&nbsp;|   **。データ?** \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。CONST**\
&nbsp;&nbsp;&nbsp;&nbsp;|  **.FARDATA**⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|   **.FARDATA?** ⟦ *segId* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;|  **。STACK** ⟦ *constExpr* ⟧

*segId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*segIdList*\
&nbsp;&nbsp;&nbsp;&nbsp;*segId*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segIdList* 、 *segId*

*segmentDef*\
&nbsp;&nbsp;&nbsp;&nbsp;*segmentDir* ⟦ *inSegDirList* ⟧ *endsdir* | *SimpleSegDir* ⟦ *inSegDirList* ⟧⟦ *endsdir* ⟧

*segmentDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*segId* **SEGMENT** ⟦ *segOptionList* ⟧;;

*segmentRegister*\
&nbsp;&nbsp;&nbsp;&nbsp;**CS** | **DS** | **ES** | **FS** | **GS** | **SS**

*segOption*\
&nbsp;&nbsp;&nbsp;&nbsp;*segAlign*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segAttrib*\
&nbsp;&nbsp;&nbsp;&nbsp;| *segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;| *className*

*segOptionList*\
&nbsp;&nbsp;&nbsp;&nbsp;*segOption* | *segOptionList* *segOption*

*segOrderDir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。アルファ** |  **。SEQ** |  **.DOSSEG** |  **.dosseg**

*segRO*\
&nbsp;&nbsp;&nbsp;&nbsp;**読み取り専用**

*segSize*\
&nbsp;&nbsp;&nbsp;&nbsp;**USE16** | **USE32** | **FLAT**

*上位*の\
&nbsp;&nbsp;&nbsp;&nbsp;**SHR** | **shl**

*署名*\
 - |+

\ の*簡略化*
&nbsp;&nbsp;&nbsp;&nbsp;MM0 |MM1 |MM2 |MM3 |MM4 |MM5 |MM6 |MM7 |xmmRegister |YMM0 ~ YMM5 |YMM1 |YMM2 |YMM3 |YMM4 |ある場合い |YMM6 |YMM7 |YMM8 |YMM9 |YMM10 |YMM11 |YMM12 |YMM13 |YMM14 |YMM15

*Simpleexpr*\
 ( *Cexpr* ) |*プライマリ*

*simpleSegDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*segDir* ;;

*\*
&nbsp;&nbsp;&nbsp;&nbsp;*id* | *型* | *e10*

*特殊文字*\
 : | . |⟦ |⟧ |( | )|< |> |{ | }\
&nbsp;&nbsp;&nbsp;&nbsp;|+ |- |/ |* |& |% | !\
&nbsp;&nbsp;&nbsp;&nbsp;||\ |= | ; |, |"\
&nbsp;&nbsp;&nbsp;&nbsp;| *whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Endofline*

*特殊レジスタ*\
&nbsp;&nbsp;&nbsp;&nbsp;CR0 レジスタ |CR2 |CR3 |DR0 |DR1 |DR2 |DR3 |DR6 |DR7 |TR3 |TR4 |TR5 |TR6 |TR7

*Stackoption*\
&nbsp;&nbsp;&nbsp;&nbsp;**NEARSTACK** | **FARSTACK**

*Startupdir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。スタートアップ**;;

*stext*\
&nbsp;&nbsp;&nbsp;&nbsp;*stringchar* | *stext* *stringchar*

*string*\
&nbsp;&nbsp;&nbsp;&nbsp;*quote* ⟦ *stext* ⟧ *quote*

*Stringchar*\
&nbsp;&nbsp;&nbsp;&nbsp;*引用* *引用符*|引用符以外の任意の文字。

*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structItem* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;| *structBody* *structItem* ;;

*structDir*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag* *structHdr* ⟦ *fieldalign* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;⟦、**一意**でない⟧;、\
&nbsp;&nbsp;&nbsp;&nbsp;*structBody*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;**終了**。

*structHdr*\
&nbsp;&nbsp;&nbsp;&nbsp;**STRUC** | **STRUCT** | **UNION**

*structInstance*\
 < ⟦ *fieldInitList* ⟧ > \
&nbsp;&nbsp;&nbsp;&nbsp;|{⟦;; ⟧⟦ *fieldInitList* ⟧⟦;; ⟧} \
&nbsp;&nbsp;&nbsp;&nbsp;| *constExpr* **DUP** ( *structInstList* ) \

*structInstList*\
&nbsp;&nbsp;&nbsp;&nbsp;*structInstance* | *structInstList* 、⟦;;⟧ *structInstance*

*structItem*\
&nbsp;&nbsp;&nbsp;&nbsp;*dataDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *全般ディレクトリ*\
&nbsp;&nbsp;&nbsp;&nbsp;| *offsetDir*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Nestedstruct*

*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*用語*の\
&nbsp;&nbsp;&nbsp;&nbsp;*Simpleexpr* |! *simpleExpr*

*text*\
&nbsp;&nbsp;&nbsp;&nbsp;*Textliteral* | *テキスト*文字 |! *文字* *テキスト* | *character* |!*文字*

*Textdir*\
&nbsp;&nbsp;&nbsp;&nbsp;*id* *textマクロ dir* ;;

*Textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;*Textliteral* | *textliteral id* |% *constExpr*

*Textlen*\
&nbsp;&nbsp;&nbsp;*constExpr* &nbsp;

*textList*\
&nbsp;&nbsp;&nbsp;&nbsp;*Textitem* | *textList* , ⟦;;⟧ *Textitem*

*Textliteral*\
&nbsp;&nbsp;&nbsp;&nbsp;< *テキスト*>;;

*Textマクロディレクトリ*\
&nbsp;&nbsp;&nbsp;&nbsp;**Catstr** ⟦ *textList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **TEXTEQU** ⟦ *textList* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **SIZESTR** *textitem*\
&nbsp;&nbsp;&nbsp;&nbsp;| **SUBSTR** *textitem* 、 *Textstart* ⟦、 *textstart* ⟧ \
&nbsp;&nbsp;&nbsp;&nbsp;| **INSTR** ⟦ *textstart* 、⟧ *textitem* 、 *textitem*

*Textマクロ id*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*Textstart*\
&nbsp;&nbsp;&nbsp;*constExpr* &nbsp;

*タイトルのディレクトリ*\
&nbsp;&nbsp;&nbsp;&nbsp;*タイトルの種類* *arbitraryText* ;;

*タイトルの種類*\
&nbsp;&nbsp;&nbsp;&nbsp;**タイトル** | **サブタイトル** | **subttl**

*type*\
&nbsp;&nbsp;&nbsp;&nbsp;*structTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *unionTag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *Recordtag*\
&nbsp;&nbsp;&nbsp;&nbsp;| *距離*\
&nbsp;&nbsp;&nbsp;&nbsp;| *データ型*\
&nbsp;&nbsp;&nbsp;&nbsp;| *typeId*

*Typedefdir*\
&nbsp;&nbsp;&nbsp;&nbsp;*typeId* **TYPEDEF**修飾子

*typeId*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*unionTag*\
&nbsp;&nbsp;&nbsp;&nbsp;*id*

*dir*\
&nbsp;&nbsp;&nbsp;&nbsp; **。まで** *cexpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **。CXZ** ⟦ *cxzexpr* ⟧;;

*usesRegs*\
&nbsp;&nbsp;&nbsp;&nbsp;**使用**している*reglist*

時*ブロック*\
&nbsp;&nbsp;&nbsp;&nbsp; **。\**
&nbsp;&nbsp;&nbsp;&nbsp;*Cexpr* ;; \
&nbsp;&nbsp;&nbsp;&nbsp;*Blockstatements* ;; \
&nbsp;&nbsp;&nbsp;&nbsp; **。ENDW**

*whiteSpaceCharacter*\
&nbsp;&nbsp;&nbsp;&nbsp;ASCII 8、9、11-13、26、32

*Xmmregister*\
&nbsp;&nbsp;&nbsp;&nbsp;XMM0 |XMM1 |XMM2 |XMM3 |XMM4 |XMM5 |XMM6 |XMM7 |XMM8 |XMM9 |XMM10 |XMM11 |XMM12 |XMM13 |XMM14 |XMM15\

