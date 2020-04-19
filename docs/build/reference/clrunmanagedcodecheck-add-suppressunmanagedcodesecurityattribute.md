---
title: /CLRUNMANAGEDCODECHECK (SuppressUnmanagedCodeSecurityAttribute の削除)
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.openlocfilehash: ecc560673a8e98752289ef0e0f89d3abfc1938e4
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837238"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (SuppressUnmanagedCodeSecurityAttribute の削除)

**/CLRUNMANAGEDCODECHECK** では、マネージド コードからネイティブ DLL への、リンカーによって生成された `PInvoke` 呼び出しに対して、リンカーで <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> を適用しないことを指定します。

## <a name="syntax"></a>構文

> **/CLRUNMANAGEDCODECHECK** **[:NO]**

## <a name="remarks"></a>解説

既定では、リンカーによって生成された `PInvoke` 呼び出しに対して、リンカーで **SuppressUnmanagedCodeSecurityAttribute** が適用されます。 **/CLRUNMANAGEDCODECHECK** が有効である場合、**SuppressUnmanagedCodeSecurityAttribute** は削除されます。 リンカーによって生成された `PInvoke` 呼び出しに対して **SuppressUnmanagedCodeSecurityAttribute** を明示的に適用するには、 **/CLRUNMANAGEDCODECHECK:NO** を使用します。

この属性は、リンカーにより、 **/clr** または **/clr:pure** を使用してコンパイルされたオブジェクトに対してのみ追加されます。 ただし、 **/clr:pure** コンパイラ オプションは Visual Studio 2015 では非推奨とされており、Visual Studio 2017 以降ではサポートされていません。

リンカーで、マネージド呼び出し元からの参照を満たすマネージド シンボルを見つけることができないが、その参照を満たすネイティブ シンボルを見つけることができる場合、リンカーによって `PInvoke` 呼び出しが生成されます。 `PInvoke` の詳細については、「[マネージド コードからのネイティブ関数の呼び出し](../../dotnet/calling-native-functions-from-managed-code.md)」を参照してください。

コードで <xref:System.Security.AllowPartiallyTrustedCallersAttribute> を使用する場合は、**SuppressUnmanagedCodeSecurity** を削除するよう **/CLRUNMANAGEDCODECHECK** 属性を明示的に設定する必要があります。 イメージに **SuppressUnmanagedCodeSecurity** 属性と **AllowPartiallyTrustedCallers** 属性の両方が含まれている場合は、潜在的なセキュリティの脆弱性となります。

**SuppressUnmanagedCodeSecurityAttribute** の使用による影響の詳細については、「[アンマネージド コードの安全なコーディングのガイドライン](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)」を参照してください。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成プロパティ]** ノードを展開します。

1. **[リンカー]** ノードを展開します。

1. **[詳細]** プロパティ ページを選択します。

1. **[CLR アンマネージド コード チェック]** プロパティを変更します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>

## <a name="see-also"></a>関連項目

- [MSVC リンカーのリファレンス](linking.md)
- [MSVC リンカー オプション](linker-options.md)
