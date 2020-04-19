---
title: /SAFESEH (安全な例外ハンドラーがあるイメージ)
ms.date: 11/04/2016
f1_keywords:
- /SAFESEH
helpviewer_keywords:
- /SAFESEH linker option
- -SAFESEH linker option
- SAFESEH linker option
ms.assetid: 7722ff99-b833-4c65-a855-aaca902ffcb7
ms.openlocfilehash: 62784933cbecd4f312c52ae98cab7d232b893f35
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318642"
---
# <a name="safeseh-image-has-safe-exception-handlers"></a>/SAFESEH (安全な例外ハンドラーがあるイメージ)

```
/SAFESEH[:NO]
```

ときに **/SAFESEH**リンカーはイメージの安全な例外ハンドラーのテーブルも生成できる場合、イメージ生成のみを指定します。 このテーブルは、どの例外ハンドラーがイメージに対して有効であるかをオペレーティング システムに指定します。

**/SAFESEH**は x86 をリンクするときにのみ有効なターゲット。 **/SAFESEH**例外ハンドラーが既に存在するプラットフォームはサポートされていません。 たとえば、x64 と ARM では、すべての例外ハンドラーは PDATA にコメントされています。 ML64.exe には、コメントを追加して SEH 情報 (XDATA および PDATA) をイメージに出力する機能をサポートしているため、ml64 関数からのアンワインドが可能です。 参照してください[x64 用 MASM (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md)詳細についてはします。

場合 **/SAFESEH**が指定されていない、すべてのモジュールに安全な例外処理機能と互換性がある場合、リンカーで安全な例外ハンドラーのテーブルを使用したイメージは生成します。 いずれかのモジュールに安全な例外処理機能との互換性がない場合、生成されるイメージには安全な例外ハンドラーのテーブルが含まれません。 場合[/SUBSYSTEM](subsystem-specify-subsystem.md) WINDOWSCE または efi _ *、オプションのいずれかを指定するサブシステムのどちらでもないことと、リンカーはイメージと安全な例外のハンドラーのテーブルを生成を試行しません情報を使用します。

場合 **/SAFESEH:NO**を指定すると、すべてのモジュールは、安全な例外処理機能と互換性がある場合でも、リンカーを安全な例外ハンドラーのテーブルを持つイメージ生成しません。

リンカーがイメージを生成できない最も一般的な理由は、リンカーへの入力ファイル (モジュール) の 1 つ以上に、安全な例外ハンドラー機能との互換性がないためです。 モジュールに安全な例外ハンドラーとの互換性がない一般的な理由は、以前のバージョンの Visual C++ のコンパイラでそのモジュールが作成されているためです。

使用して、構造化例外ハンドラーとして関数を登録することも[します。SAFESEH](../../assembler/masm/dot-safeseh.md)します。

既存のバイナリを、安全な例外ハンドラーがある、または例外ハンドラーがないものとしてマークすることはできません。安全な例外処理の情報は、ビルド時に追加する必要があります。

リンカーが安全な例外ハンドラーのテーブルを生成できるかどうかは、C ランタイム ライブラリを使用しているアプリケーションによって決まります。 リンクしている場合[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)を安全な例外ハンドラーのテーブルに読み込み構成構造体 (loadcfg.c CRT ソース ファイルで見つかるなど) を指定する必要がある Visual C に対して定義されているすべてのエントリを格納しています。 例:

```
#include <windows.h>
extern DWORD_PTR __security_cookie;  /* /GS security cookie */

/*
* The following two names are automatically created by the linker for any
* image that has the safe exception table present.
*/

extern PVOID __safe_se_handler_table[]; /* base of safe handler entry table */
extern BYTE  __safe_se_handler_count;  /* absolute symbol whose address is
                                           the count of table entries */
typedef struct {
    DWORD       Size;
    DWORD       TimeDateStamp;
    WORD        MajorVersion;
    WORD        MinorVersion;
    DWORD       GlobalFlagsClear;
    DWORD       GlobalFlagsSet;
    DWORD       CriticalSectionDefaultTimeout;
    DWORD       DeCommitFreeBlockThreshold;
    DWORD       DeCommitTotalFreeThreshold;
    DWORD       LockPrefixTable;            // VA
    DWORD       MaximumAllocationSize;
    DWORD       VirtualMemoryThreshold;
    DWORD       ProcessHeapFlags;
    DWORD       ProcessAffinityMask;
    WORD        CSDVersion;
    WORD        Reserved1;
    DWORD       EditList;                   // VA
    DWORD_PTR   *SecurityCookie;
    PVOID       *SEHandlerTable;
    DWORD       SEHandlerCount;
} IMAGE_LOAD_CONFIG_DIRECTORY32_2;

const IMAGE_LOAD_CONFIG_DIRECTORY32_2 _load_config_used = {
    sizeof(IMAGE_LOAD_CONFIG_DIRECTORY32_2),
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    0,
    &__security_cookie,
    __safe_se_handler_table,
    (DWORD)(DWORD_PTR) &__safe_se_handler_count
};
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**リンカー**フォルダー。

1. 選択、**コマンドライン**プロパティ ページ。

1. オプションを入力して、**追加オプション**ボックス。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
