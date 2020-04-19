---
title: /Zc:wchar_t (wchar_t をネイティブ型として認識)
ms.date: 03/01/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.TreatWChar_tAsBuiltInType
- VC.Project.VCCLCompilerTool.TreatWChar_tAsBuiltInType
- /Zc:wchar_t
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- wchar_t type
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: b0de5a84-da72-4e5a-9a4e-541099f939e0
ms.openlocfilehash: 962bb2aaa2f05ad0dc4c9c86cd5cc9694cfad98b
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446162"
---
# <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t をネイティブ型として認識)

`wchar_t` を、C++ 標準に従って組み込み型として解析します。

## <a name="syntax"></a>構文

> **/Zc:wchar_t**[**-**]

## <a name="remarks"></a>Remarks

場合 **/Zc:wchar_t** 、`wchar_t`としてコンパイルされたコードで組み込みの整数型のキーワードは、C++します。 場合 **/Zc:wchar_t-** (マイナス記号) で指定された、またはコードで C としてコンパイルされた、`wchar_t`組み込み型ではありません。 代わりに、`wchar_t`として定義されている場合は、`typedef`の`unsigned short`標準ヘッダー stddef.h でします。 (Microsoft による実装を定義、stddef.h に含まれているもう 1 つのヘッダーとその他の標準ヘッダー。)

お勧めしません **/Zc:wchar_t-** ため、C++標準である必要があります`wchar_t`組み込み型を指定します。 `typedef` バージョンを使用すると、移植性の問題が発生することがあります。 Visual Studio の以前のバージョンからアップグレードし、コンパイラ エラーが発生したかどうかは[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)コードが暗黙的に変換しようとしているため、`wchar_t`に`unsigned short`エラーを修正するコードを変更することをお勧めします。設定ではなく **/Zc:wchar_t-** します。

**/Zc:wchar_t**オプションが既定では  C++ 、コンパイル、C のコンパイルでは無視されます。 [/Permissive -](permissive-standards-conformance.md)オプションには影響しません **/Zc:wchar_t**します。

Microsoft では、`wchar_t` が 2 バイトの符号なしの値として実装されます。 Microsoft 固有のネイティブ型にマップされます`__wchar_t`します。 詳細については`wchar_t`を参照してください[データ型の範囲](../../cpp/data-type-ranges.md)と[基本的な型](../../cpp/fundamental-types-cpp.md)します。

まだ使用する古いコードの相互運用する新しいコードを記述する場合、`typedef`版`wchar_t`、両方のオーバー ロードを行うことができます、`unsigned short`と`__wchar_t`のバリエーション`wchar_t`と、コードをリンクすることができるように、コードをコンパイル **/Zc:wchar_t**またはなしでコンパイルされたコード。 それ以外の場合でとなしのライブラリの 2 つの異なるビルドを提供する必要が **/Zc:wchar_t**を有効にします。 この場合も、以前のコードのビルドには、新しいコードをコンパイルするときに使用するコンパイラを使用することをお勧めします。 さまざまなコンパイラでコンパイルされたバイナリを混在させないでください。

ときに **/Zc:wchar_t**が指定されている **\_WCHAR\_T\_定義**と**\_ネイティブ\_WCHAR\_T\_定義**シンボルが定義されます。 詳細については、「 [Predefined Macros](../../preprocessor/predefined-macros.md)」を参照してください。

に、コードがコンパイラ COM グローバル関数を使用する場合 **/Zc:wchar_t**は既定では、お勧め comsupp.lib への明示的な参照を変更するようになりました (のいずれかから、[コメント プラグマ](../../preprocessor/comment-c-cpp.md)か、または、コマンド ライン) comsuppw.lib または comsuppwd.lib のいずれかにします。 (指定してコンパイルする必要がある場合 **/Zc:wchar_t-** comsupp.lib を使用します)。comdef.h のヘッダー ファイルを含めると、適切なライブラリが自動的に指定されます。 コンパイラ COM サポートについては、次を参照してください。[コンパイラ COM サポート](../../cpp/compiler-com-support.md)します。

`wchar_t` C コードをコンパイルするときに、組み込み型がサポートされていません。 Visual C の準拠の問題の詳細については、次を参照してください。[非標準動作](../../cpp/nonstandard-behavior.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **言語**ページ。

1. 変更、 **wchar_t をビルトイン型として扱う**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.TreatWChar_tAsBuiltInType%2A>

## <a name="see-also"></a>関連項目

[/Zc (準拠)](zc-conformance.md)<br/>
