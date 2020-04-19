---
title: ML および ML64 のコマンド ライン リファレンス
description: Microsoft MASM ML および ML64.EXE アセンブラのコマンドラインオプションに関するリファレンスガイドです。
ms.date: 02/09/2020
f1_keywords:
- ML
helpviewer_keywords:
- /W* MASM compiler option
- /c MASM compiler option
- /EP MASM compiler option
- /Fe MASM compiler option
- /Zp MASM compiler option
- /AT MASM compiler option
- /Zm MASM compiler option
- /Sf MASM compiler option
- /Sp MASM compiler option
- /w MASM compiler option
- /Fl MASM compiler option
- /coff MASM compiler option
- /St MASM compiler option
- /Cx MASM compiler option
- /Sl MASM compiler option
- /Cu MASM compiler option
- MASM (Microsoft Macro Assembler), ML command-line reference
- /FPi MASM compiler option
- /Zf MASM compiler option
- ML environment variable
- /Fr MASM compiler option
- /help MASM compiler option
- /Sa MASM compiler option
- /Zd MASM compiler option
- /I MASM compiler option
- /? MASM compiler option
- /Bl MASM compiler option
- /Fm MASM compiler option
- /Fo MASM compiler option
- command-line reference [ML]
- /Sn MASM compiler option
- /Gd MASM compiler option
- /D* MASM compiler option
- environment variables, ML
- /Gc MASM compiler option
- /F* MASM compiler option
- /Sc MASM compiler option
- /H MASM compiler option
- /Zs MASM compiler option
- /omf MASM compiler option
- /Sg MASM compiler option
- /Cp MASM compiler option
- /Zi MASM compiler option
- /nologo MASM compiler option
- /Sx MASM compiler option
- /WX MASM compiler option
- /Ss MASM compiler option
- command line, reference [ML]
- /Ta MASM compiler option
ms.assetid: 712623c6-f77e-47ea-a945-089e57c50b40
ms.openlocfilehash: b5c5a79417cb141da3d5cfe1c08aa39e02a9c7c2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257365"
---
# <a name="ml-and-ml64-command-line-reference"></a>ML および ML64 のコマンド ライン リファレンス

1つ以上のアセンブリ言語のソースファイルをアセンブルしてリンクします。 コマンドラインオプションでは大文字と小文字が区別されます。

Ml64.exe の詳細については、「 [MASM for x64 (ml64.exe)](masm-for-x64-ml64-exe.md)」を参照してください。

## <a name="syntax"></a>構文

> ML \[*オプション*] *filename* \[ \[*オプション*] *filename*]
>
> ML64.EXE \[*オプション*] *filename* \[ \[*オプション*] *filename*]... \[/link *link_options*]

### <a name="parameters"></a>パラメーター

*オプション*\
次の表に示すオプション。

|オプション|操作|
|------------|------------|
|**/AT**|最小メモリモデルのサポートを有効にします。 .Com フォーマットファイルの要件に違反するコードコンストラクターのエラーメッセージを有効にします。 このオプションは、とは等価ではありません[。モデル](dot-model.md)の**小さな**ディレクティブ。<br /><br /> Ml64.exe では使用できません。|
|**/Bl** *ファイル名*|代替リンカーを選択します。|
|**/c**|アセンブルのみ。 リンクは行われません。|
|**/coff**|オブジェクトモジュールの Common Object File Format (COFF) 型を生成します。 Win32 アセンブリ言語の開発に必要です。<br /><br /> Ml64.exe では使用できません。|
|**/Cp**|すべてのユーザー識別子の大文字と小文字を保持します。|
|**/Cu**|すべての識別子を大文字にマップします (既定)。<br /><br /> Ml64.exe では使用できません。|
|**/Cx**|Public および extern シンボルの大文字と小文字を保持します。|
|**/D** *シンボル*⟦ =*値*⟧|指定された名前のテキストマクロを定義します。 *値が指定*されていない場合は空白になります。 スペースで区切られた複数のトークンは、引用符で囲む必要があります。|
|**/EP**|プリプロセスされたソースリスティング (STDOUT に送信) を生成します。 「 **/Sf**」を参照してください。|
|**/ERRORREPORT** [ **NONE** &#124; **PROMPT** &#124; QUEUE &#124; **SEND** ]| 非推奨。 エラー報告は、 [Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。 |
|**/F** *hexnum*|スタックサイズを*hexnum*バイト ( **/link/STACK**:*number*と同じ) に設定します。 値は16進表記で表現する必要があります。 **/F**と*hexnum*の間にはスペースが必要です。|
|**/Fe** *ファイル名*|実行可能ファイルの名前をにします。|
|**/Fl**⟦*ファイル名*⟧|アセンブルされたコードリストを生成します。 「 **/Sf**」を参照してください。|
|**/Fm**⟦*filename*⟧|リンカーマップファイルを作成します。|
|**/Fo** *ファイル名*|オブジェクトファイルに名前を付いています。 詳細については、「[解説](#remarks)」をご覧ください。|
|**/FPi**|浮動小数点演算 (混合言語のみ) のエミュレーター修正を生成します。<br /><br /> Ml64.exe では使用できません。|
|**/Fr**⟦*filename*⟧|ソースブラウザーの .sbr ファイルを生成します。|
|**/Fr**⟦*filename*⟧|ソースブラウザーの .sbr ファイルの拡張形式を生成します。|
|**/Gc**|FORTRAN または Pascal 形式の関数の呼び出しと名前付け規則を使用することを指定します。 **オプション言語と同じ: PASCAL**。<br /><br /> Ml64.exe では使用できません。|
|**/Gd**|C スタイルの関数呼び出しと名前付け規則の使用を指定します。 **オプション言語: C**と同じです。<br /><br /> Ml64.exe では使用できません。|
|**/GZ**|__Stdcall 関数の呼び出しと名前付け規則の使用を指定します。  **オプション言語: STCALL**と同じです。<br /><br /> Ml64.exe では使用できません。|
|**/H** *番号*|外部名を有効な文字数に制限します。 既定値は31文字です。<br /><br /> Ml64.exe では使用できません。|
|**/help**|ML に関するヘルプを表示するには、QuickHelp を呼び出します。|
|**/I** *パス名*|インクルードファイルのパスを設定します。 最大で10個の **/i**オプションを指定できます。|
|**/nologo**|正常に完了したアセンブリのメッセージを抑制します。|
|**/omf**|オブジェクトモジュールのオブジェクトモジュールファイル形式 (OMF) 型を生成します。  **/omf**は **/c**を意味します。ML は、OMF オブジェクトのリンクをサポートしていません。<br /><br /> Ml64.exe では使用できません。|
|**/Sa**|利用可能なすべての情報の一覧を表示します。|
|**/safeseh**|例外ハンドラーを含まない、またはで宣言されているすべての例外ハンドラーを含むオブジェクトとしてマークし[ます。SAFESEH](dot-safeseh.md)。<br /><br /> Ml64.exe では使用できません。|
|**/Sf**|リストファイルに先頭パスの一覧を追加します。|
|**/Sl** *幅*|ソースリストの線の幅を1行あたりの文字数で設定します。 範囲は 60 ~ 255 または0です。 既定値は 0 です。 [ページ](page.md)の幅と同じです。|
|**/Sn**|リストを生成するときにシンボルテーブルをオフにします。|
|**Qfe また**の*長さ*|ソースリストのページの長さをページごとの行数で設定します。 範囲は 10 ~ 255 または0です。 既定値は 0 です。 [ページ](page.md)長と同じです。|
|**/S** *テキスト*|ソースリストのテキストを指定します。 [サブタイトル](subtitle.md)テキストと同じです。|
|**/St** *テキスト*|ソースリストのタイトルを指定します。 [タイトル](title.md)テキストと同じです。|
|**/Sx**|リスト内の false 条件をオンにします。|
|**/Ta** *ファイル名*|名前が .asm 拡張子で終わらないソースファイルをアセンブルします。|
|**/w**|**/W0/WX**と同じです。|
|**/W** *レベル*|警告レベルを設定します。 *level* = 0、1、2、または3です。|
|**/WX**|警告が生成された場合は、エラーコードを返します。|
|**/X**|インクルード環境のパスを無視します。|
|**/Zd**|オブジェクトファイルに行番号情報を生成します。|
|**/Zf**|すべてのシンボルをパブリックにします。|
|**/Zi**|オブジェクトファイルに CodeView 情報を生成します。|
|**/Zm**|MASM 5.1 との互換性を最大限に保つために**M510**オプションを有効にします。<br /><br /> Ml64.exe では使用できません。|
|**/Zp**⟦*alignment*⟧|構造体を指定されたバイト境界でパックします。 *配置*には、1、2、または4を指定できます。|
|**/Zs**|構文チェックのみを実行します。|
|**/?**|ML コマンドライン構文の概要を表示します。|

*ファイル名*\
ファイルの名前です。

*link_options*\
リンクオプション。 詳細については、「[リンカー オプション](../../build/reference/linker-options.md)」を参照してください。

## <a name="remarks"></a>コメント

ML および ML64.EXE の一部のコマンドラインオプションは、配置に依存します。 たとえば、ML と ML64.EXE はいくつかの **/c**オプションを受け入れることができるため、対応する **/fo**オプションは **/c**の前に指定する必要があります。 次のコマンドラインの例では、アセンブリファイルの指定ごとにオブジェクトファイルを指定しています。

```cmd
ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm
```

## <a name="environment-variables"></a>環境変数

|[Variable]|説明|
|--------------|-----------------|
|INCLUDE|インクルードファイルの検索パスを指定します。|
|ML|既定のコマンドラインオプションを指定します。|
|TMP|一時ファイルのパスを指定します。|

## <a name="see-also"></a>参照

[ML エラーメッセージ](ml-error-messages.md)\
[Microsoft Macro Assembler リファレンス](microsoft-macro-assembler-reference.md)
