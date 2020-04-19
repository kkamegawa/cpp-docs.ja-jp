---
title: '[HLSL] プロパティ ページ'
ms.date: 07/24/2019
ms.assetid: 0c65f5ec-a2a5-4f5b-8d4c-fa57113a5a1d
f1_keywords:
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.SuppressStartupBanner
- VC.Project.FXCompilerTool.EntryPointName
- VC.Project.FXCompilerTool.TreatWarningAsError
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.AllResourcesBound
- VC.Project.FXCompilerTool.EnableUnboundedDescriptorTables
- VC.Project.FXCompilerTool.SetRootSignature
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.AdditionalOptionsPage
- VC.Project.FXCompilerTool.VariableName
- VC.Project.FXCompilerTool.HeaderFileOutput
- VC.Project.FXCompilerTool.ObjectFileOutput
- VC.Project.FXCompilerTool.AssemblerOutput
- VC.Project.FXCompilerTool.AssemblerOutputFile
- VC.Project.FXCompilerTool.CompileD2DCustomEffect
- VC.Project.FXCompilerTool.MultiProcFXC
ms.openlocfilehash: a45ae433e5adaa8aeaf32215d4af7ad0a247af04
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606401"
---
# <a name="hlsl-compiler-property-pages"></a>HLSL コンパイラプロパティページ

HLSL コンパイラ (fxc.exe) プロパティ ページを使用すると、個々の HLSL シェーダー ファイルがどのようにビルドされるのかを構成することができます。 また、 **[コマンドライン]** プロパティページの **[追加のオプション]** プロパティを使用して、HLSL コンパイラのコマンドライン引数を指定することもできます。これには、HLSL プロパティページの他のプロパティを使用して構成できない引数が含まれます。 HLSL コンパイラの情報については、「[エフェクト コンパイラ ツール](https://go.microsoft.com/fwlink/p/?LinkID=258285&clcid=0x409)」を参照してください。

## <a name="hlsl-general-property-page"></a>[HLSL 全般] プロパティページ

### <a name="additional-include-directories"></a>追加のインクルード ディレクトリ

インクルード パスに追加するディレクトリを 1 つ以上指定します。複数指定する場合には、セミコロンで区切ってください。 (/I [パス])

### <a name="entrypoint-name"></a>Entrypoint 名

シェーダーのエントリポイントの名前を指定します (/E [名前])

### <a name="disable-optimizations"></a>最適化を無効にする

最適化を有効にする場合は **[はい (/Od)]** 、それ以外の場合は **[いいえ]** です。 既定値は、**デバッグ**構成の場合は **[はい (/Od)]** 、**リリース**構成の場合は **[いいえ]** です。

HLSL コンパイラに対して **/Od** コマンド ライン引数を指定すると **/Gfp** コマンド ライン引数が暗黙的に適用されますが、その出力は、 **/Od** と **/Gfp** 両方のコマンド ライン引数を明示的に渡すことによって生成される出力と同じでない場合があります。

### <a name="enable-debugging-information"></a>デバッグ情報を有効にする

デバッグ情報を有効にする場合は **[はい (/Zi)]** 、それ以外の場合は **[いいえ]** です。 既定値は、**デバッグ**構成の場合は **[はい (/Zi)]** 、**リリース**構成の場合は **[いいえ]** です。

### <a name="shader-type"></a>シェーダーの種類

シェーダーの種類を指定します。 異なる種類のシェーダーは、グラフィックス パイプラインの異なる部分を実装します。 一部のシェーダーの種類は、新しいシェーダー モデル ( **[シェーダー モデル]** プロパティで指定されています) でのみ使用できます。たとえば、計算シェーダーはシェーダー モデル 5 で導入されました。

このプロパティは、HLSL コンパイラに対する **/T \[type]_\[model]** コマンド ライン引数の **\[type]** 部分に対応します。 **[シェーダー モデル]** プロパティは、引数の **[model]** 部分を指定します。

**いずれ**

- **効果**
- **頂点シェーダー**
- **ピクセル シェーダー**
- **ジオメトリ シェーダー**
- **ハルシェーダー**
- **ドメインシェーダー**
- **計算シェーダー**
- **Library**
- **ルート署名オブジェクトの生成**

### <a name="shader-model"></a>シェーダーモデル

シェーダー モデルを指定します。 シェーダー モデルが異なると、機能が異なります。 一般に、シェーダー モデルが新しいほど機能は拡張されていますが、シェーダー コードを実行するにはより新しいグラフィックス ハードウェアが必要です。 一部のシェーダーの種類 ( **[シェーダーの種類]** プロパティで指定されています) は、新しいシェーダー モデルでのみ使用できます。たとえば、計算シェーダーはシェーダー モデル 5 で導入されました。

このプロパティは、HLSL コンパイラに対する **/T \[type]_\[model]** コマンド ライン引数の **\[model]** 部分に対応します。 **[シェーダーの種類]** プロパティは、引数の **[type]** 部分を指定します。

### <a name="all-resources-bound"></a>すべてのリソースがバインドされました

コンパイラは、シェーダーが参照できるすべてのリソースがバインドされていて、シェーダーの実行中に良好な状態にあると想定します。 シェーダー モデル 5.1 以降で利用できます。

### <a name="enable-unbounded-descriptor-tables"></a>非バインド記述子テーブルを有効にする

シェーダーに無制限の範囲 (/enable_unbounded_descriptor_tables) を持つリソース配列の宣言が含まれている可能性があることをコンパイラに通知します。 シェーダー モデル 5.1 以降で利用できます。

### <a name="set-root-signature"></a>ルート署名の設定

ルートシグネチャをシェーダーバイトコード (/setrootsignature) にアタッチします。 Shader Model 5.0 以上で使用できます。

### <a name="preprocessor-definitions"></a>プリプロセッサの定義

HLSL のソース コード ファイルに適用する 1 つ以上のプリプロセッサ シンボル定義を追加します。 シンボル定義を区切るにはセミコロンを使います。

このプロパティは、HLSL コンパイラに対する **/D \[definitions]** コマンド ライン引数に対応します。

### <a name="compile-a-direct2d-custom-pixel-shader-effect"></a>Direct2D カスタムピクセルシェーダー効果をコンパイルする

ピクセル シェーダーを含む Direct2D カスタム効果をコンパイルします。 頂点に対して使ったり、カスタム効果を計算したりしないでください。

### <a name="multi-processor-compilation"></a>マルチプロセッサのコンパイル

複数のインスタンスを同時に実行します。

## <a name="advanced-property-page"></a>[詳細設定] プロパティページ

### <a name="suppress-startup-banner"></a>著作権情報の非表示

著作権情報と情報メッセージを表示しません。 /nologo

### <a name="treat-warnings-as-errors"></a>警告をエラーとして扱う

コンパイラ警告をすべてエラーとして扱います。 新しいプロジェクトの場合、すべてのコンパイルで /WX を使用することをお勧めします。すべての警告を解決することで、コードの欠陥を見逃す可能性が低くなります。

## <a name="output-files-property-page"></a>[出力ファイル] プロパティページ

### <a name="header-variable-name"></a>ヘッダー変数名

ヘッダーファイル内の変数名の名前を指定します (/Vn [名前])

### <a name="header-file-name"></a>ヘッダーファイル名

オブジェクト コードを含むヘッダー ファイル名を指定します。 (/Fh [名前])

### <a name="object-file-name"></a>オブジェクト ファイル名

オブジェクト ファイル名を指定します。 (/Fo [名前])

### <a name="assembler-output"></a>アセンブラ出力

アセンブリ言語の出力ファイルの内容を指定します。 (/Fc、/Fx)

**いずれ**

- **リスティング**がありません。一覧はありません。
- **アセンブリのみのリスティング**-アセンブリコードファイル
- **アセンブリコードと16進**アセンブリコードと16進数リスティングファイル

### <a name="assembler-output-file"></a>アセンブラー出力ファイル

アセンブリコードリスティングファイルのファイル名を指定します

## <a name="see-also"></a>関連項目

[C++プロジェクトプロパティページのリファレンス](property-pages-visual-cpp.md)<br>
[[コマンド ライン] プロパティ ページ](command-line-property-pages.md)<br>
[シェーダーのコンパイル](https://go.microsoft.com/fwlink/p/?LinkID=258284&clcid=0x409)
