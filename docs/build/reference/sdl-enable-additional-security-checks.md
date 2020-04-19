---
title: /sdl (追加のセキュリティ チェックの有効化)
ms.date: 11/26/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SDLCheck
ms.assetid: 3dcf86a0-3169-4240-9f29-e04a9f535826
ms.openlocfilehash: 0618b796d492395c3e0e5413047ac0260082baff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318447"
---
# <a name="sdl-enable-additional-security-checks"></a>/sdl (追加のセキュリティ チェックの有効化)

推奨される Security Development Lifecycle (SDL) のチェックを追加します。 これらのチェックには、エラーとしての追加のセキュリティ関連の警告、および追加の安全なコード生成機能が含まれます。

## <a name="syntax"></a>構文

```
/sdl[-]
```

## <a name="remarks"></a>Remarks

**/sdl**によって提供されるベースライン セキュリティ チェックのスーパー セットの有効[/GS](gs-buffer-security-check.md)と上書き **/GS-** します。 既定では、 **/sdl**はオフです。 **/sdl-** 追加のセキュリティ チェックを無効にします。

## <a name="compile-time-checks"></a>コンパイル時のチェック

**/sdl**により、これらの警告をエラーとして。

|/sdl で有効になる警告|同等のコマンド ラインスイッチ|説明|
|------------------------------|-------------------------------------|-----------------|
|[C4146](../../error-messages/compiler-warnings/compiler-warning-level-2-c4146.md)|/we4146|単項マイナス演算子が符号なしの型に適用され、符号なしの結果になります。|
|[C4308](../../error-messages/compiler-warnings/compiler-warning-level-2-c4308.md)|/we4308|負の整数定数が符号なしの型に変換されて、多くの場合は意味のない結果になります。|
|[C4532](../../error-messages/compiler-warnings/compiler-warning-level-1-c4532.md)|/we4532|使用`continue`、`break`または`goto`内のキーワード、 `__finally` / `finally`ブロックが異常終了時の動作を定義されていません。|
|[C4533](../../error-messages/compiler-warnings/compiler-warning-level-1-c4533.md)|/we4533|変数の初期化コードが実行されません。|
|[C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|/we4700|初期化されていないローカル変数が使用されます。|
|[C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|/we4703|初期化されていない可能性のあるローカル ポインター変数が使用されます。|
|[C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|/we4789|特定の C ランタイム (CRT) 関数の使用時にバッファー オーバーランが発生します。|
|[C4995](../../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)|/we4995|プラグマでマークされた関数を使用[非推奨とされます](../../preprocessor/deprecated-c-cpp.md)します。|
|[C4996](../../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)|/we4996|としてマークされている関数を使用[非推奨とされます](../../cpp/deprecated-cpp.md)します。|

## <a name="runtime-checks"></a>実行時のチェック

ときに **/sdl**が有効にすると、コンパイラは実行時にこれらのチェックを実行するコードが生成されます。

- Strict モードを有効に **/GS**実行時バッファー オーバーランの検出、使用したコンパイルと同じ`#pragma strict_gs_check(push, on)`します。

- 制限付きでポインターのサニタイズを行います。 逆参照がない式でも、ユーザー定義のデストラクターがない型でも、ポインターの参照は、`delete` の呼び出し後、無効なアドレスに設定されます。 これは、古いポインター参照の再使用を防止するために役立ちます。

- クラス メンバーのポインターの初期化を実行します。 自動的にポインター型へのメンバーのクラスを初期化します**nullptr** (コンス トラクターの実行) する前に、オブジェクトのインスタンス化します。 これは、コンス トラクターが明示的に初期化しない初期化されていないポインターの使用を回避できます。 コンパイラで生成されたメンバーのポインターの初期化と呼ばれる限り、します。

  - オブジェクトがカスタム (ユーザー定義) を使用して割り当てられていません `operator new`

  - 配列の一部として、オブジェクトが割り当てられていない (たとえば`new A[x]`)

  - クラスは管理されている、またはインポートされていません

  - クラスには、ユーザー定義の既定のコンス トラクターがあります。

  コンパイラによって生成されたクラスの初期化関数で初期化するには、メンバーは、ポインターでない、プロパティまたは定数になければなりません。

## <a name="remarks"></a>Remarks

詳細については、次を参照してください。[警告、/sdl、および初期化されていない変数の検出の向上](https://cloudblogs.microsoft.com/microsoftsecure/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)します。

#### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、 **C/C++** フォルダー。

1. **全般**からオプションを選択 ページで、 **SDL チェック**ドロップダウン リスト。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
