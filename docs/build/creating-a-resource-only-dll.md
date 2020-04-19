---
title: リソースのみの DLL の作成
description: Visual Studio でリソースのみの DLL を作成する方法。
ms.date: 01/27/2020
helpviewer_keywords:
- resource-only DLLs [C++], creating
- DLLs [C++], creating
ms.assetid: e6b1d4da-7275-467f-a58c-a0a8a5835199
no-loc:
- noentry
ms.openlocfilehash: ef79de77e35cbef6acd4af1cec82a4edc1b7d105
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821344"
---
# <a name="creating-a-resource-only-dll"></a>リソースのみの DLL の作成

リソースのみの DLL とは、リソース以外のものを一切含まず、アイコン、ビットマップ、文字列、ダイアログ ボックスだけを含む DLL です。 リソースのみの DLL は、複数のプログラム間でリソース群を共有するのに適しています。 また、複数の言語用にローカライズされたリソースをアプリケーションに提供するのにも適しています。 詳細については、「 [MFC アプリケーションのローカライズされたリソース: サテライト dll](localized-resources-in-mfc-applications-satellite-dlls.md)」を参照してください。

## <a name="create-a-resource-only-dll"></a>リソースのみの DLL を作成する

リソースのみの DLL を作成するには、新しい Windows DLL (MFC 以外の) プロジェクトを作成し、リソースをプロジェクトに追加します。

::: moniker range="vs-2015"

1. **[新しいプロジェクト]** ダイアログボックスで **[Win32 プロジェクト]** を選択します。 プロジェクトとソリューションの名前を入力し、[ **OK]** を選択します。

1. **Win32 アプリケーションウィザード**で、 **[アプリケーションの設定]** を選択します。 **DLL**の**アプリケーションの種類**を選択します。 **[追加のオプション]** の **[空のプロジェクト]** を選択します。 **[完了]** を選択してプロジェクトを作成します。

1. DLL のリソース (文字列やメニューなど) を含む新しいリソーススクリプトを作成します。 `.rc` ファイルを保存します。

1. **[プロジェクト]** メニューの **[既存項目の追加]** をクリックし、新しい `.rc` ファイルをプロジェクトに挿入します。

1. [/NOENTRY](reference/noentry-no-entry-point.md)リンカーオプションを指定します。 `/NOENTRY` は、リンカーが `_main` への参照を DLL にリンクできないようにします。このオプションは、リソースのみの DLL を作成するために必要です。

1. DLL をビルドします。

::: moniker-end
::: moniker range=">=vs-2017"

1. **[新しいプロジェクト]** ダイアログボックスの **[Windows デスクトップウィザード]** を選択し、 **[次へ]** をクリックします。 **[新しいプロジェクトの構成]** ページで、プロジェクトとソリューションの名前を入力し、 **[作成]** を選択します。

1. **[Windows デスクトッププロジェクト]** ダイアログボックスで、 **[ダイナミックリンクライブラリ]** の**アプリケーションの種類**を選択します。 **[追加のオプション]** の **[空のプロジェクト]** を選択します。 **[OK]** を選択してプロジェクトを作成します。

1. DLL のリソース (文字列やメニューなど) を含む新しいリソーススクリプトを作成します。 `.rc` ファイルを保存します。

1. **[プロジェクト]** メニューの **[既存項目の追加]** をクリックし、新しい `.rc` ファイルをプロジェクトに挿入します。

1. [/NOENTRY](reference/noentry-no-entry-point.md)リンカーオプションを指定します。 `/NOENTRY` は、リンカーが `_main` への参照を DLL にリンクできないようにします。このオプションは、リソースのみの DLL を作成するために必要です。

1. DLL をビルドします。

::: moniker-end

## <a name="use-a-resource-only-dll"></a>リソースのみの DLL を使用する

リソースのみの DLL を使用するアプリケーションは、DLL に明示的にリンクするために、 [LoadLibraryEx](loadlibrary-and-afxloadlibrary.md)または関連する関数を呼び出す必要があります。 リソースにアクセスするには、任意の種類のリソースで動作するジェネリック関数 `FindResource` および `LoadResource`を呼び出します。 または、次のリソース固有の関数のいずれかを呼び出します。

- `FormatMessage`

- `LoadAccelerators`

- `LoadBitmap`

- `LoadCursor`

- `LoadIcon`

- `LoadMenu`

- `LoadString`

アプリケーションは、リソースの使用が終了したら `FreeLibrary` を呼び出す必要があります。

## <a name="see-also"></a>関連項目

[リソース ファイルの操作](../windows/working-with-resource-files.md)\
[Visual Studio での C/C++ Dll の作成](dlls-in-visual-cpp.md)
