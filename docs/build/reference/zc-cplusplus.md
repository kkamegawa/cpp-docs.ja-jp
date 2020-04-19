---
title: /Zc:__cplusplus (更新された __cplusplus マクロの有効化)
ms.date: 05/16/2019
f1_keywords:
- /Zc:__cplusplus
helpviewer_keywords:
- -Zc:__cplusplus compiler option (C++)
- __cplusplus macro (C++)
ms.openlocfilehash: 43392438eabc7cc7f6decb1349d112a0ce5bd0f5
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837553"
---
# <a name="zccplusplus-enable-updated-cplusplus-macro"></a>/Zc:__cplusplus (更新された __cplusplus マクロの有効化)

**/Zc:__cplusplus** コンパイラ オプションでは、サポートされる最近の C++ 言語標準の更新値を通知する **\_\_cplusplus** プリプロセッサ マクロを有効にします。 Visual Studio は、 **\_\_cplusplus** プリプロセッサ マクロに対して、既定で常に "199711L" 値を返します。

## <a name="syntax"></a>構文

> **/Zc:__cplusplus**[ **-** ]

## <a name="remarks"></a>解説

**\_\_cplusplus** プリプロセッサ マクロは、特定のバージョンの C++ 標準をサポートしているかどうかを通知するために一般に使用されます。 既存のコードの多くは、このマクロの値が "199711L" に一致することに依存しているようなので、明示的に **/Zc:__cplusplus** コンパイラ オプションの使用をオプトインしない限り、コンパイラではこのマクロの値を変更しません。 **/Zc:__cplusplus** オプションは、Visual Studio 2017 バージョン 15.7 以降で使用でき、既定ではオフになっています。 Visual Studio の以前のバージョンでは、既定で、または **/Zc:__cplusplus-** が指定されている場合、 **\_\_cplusplus** プリプロセッサ マクロに対して "199711L" の値を返します。 [/permissive-](permissive-standards-conformance.md) オプションでは、 **/Zc:__cplusplus** は有効になりません。

**/Zc:__cplusplus** オプションが有効な場合、 **\_\_cplusplus** マクロが通知する値は、[/std](std-specify-language-standard-version.md) バージョンのスイッチ設定に依存します。 この表では、このマクロに可能な値を示します。

|/Zc:__cplusplus スイッチ|/std:c++ スイッチ|__cplusplus 値|
|-|-|-|
Zc:__cplusplus|/std:c++14 (既定)|201402L
Zc:__cplusplus|/std:c++17|201703L
Zc:__cplusplus|/std:c++latest|201704L
Zc:__cplusplus- (無効)|任意の値|199711L
指定なし|任意の値|199711L

コンパイラでは、C++98、C++03 または C++11 の標準スイッチをサポートしていません。

コンパイラのツールセットの変更をより詳細に検出するには、定義済みの [_MSC_VER](../../preprocessor/predefined-macros.md) マクロを使用します。 この組み込みのマクロの値は、Visual Studio 2017 以降のバージョンのツールセットが更新されるたびに増分されます。 [_MSVC_LANG](../../preprocessor/predefined-macros.md) の定義済みのマクロでは、 **/Zc:__cplusplus** オプションが有効でも無効でも、標準のバージョンを通知します。 **/Zc:__cplusplus** が有効な場合は `__cplusplus == _MSVC_LANG` となります。

### <a name="to-set-this-compiler-option-in-visual-studio"></a>このコンパイラ オプションを Visual Studio で使用するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成プロパティ]**  >  **[C/C++]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. **[追加オプション]** ウィンドウに **/Zc:__cplusplus** または **/Zc:__cplusplus-** を追加します。

## <a name="see-also"></a>関連項目

- [/Zc (準拠)](zc-conformance.md)
- [/std (言語の標準バージョンの指定)](std-specify-language-standard-version.md)
- [定義済みマクロ](../../preprocessor/predefined-macros.md)
