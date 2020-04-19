---
title: /ALLOWISOLATION (マニフェスト検索)
ms.date: 11/04/2016
f1_keywords:
- /ALLOWISOLATION
- VC.Project.VCLinkerTool.AllowIsolation
helpviewer_keywords:
- -ALLOWISOLATION linker option
- /ALLOWISOLATION linker option
ms.assetid: 6d41851e-b3c1-4bdf-beaa-031773089d6f
ms.openlocfilehash: 7c799f3d44428643bccc2869255ffa4e9d194d70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493137"
---
# <a name="allowisolation-manifest-lookup"></a>/ALLOWISOLATION (マニフェスト検索)

マニフェスト検索の動作を指定します。

## <a name="syntax"></a>構文

```
/ALLOWISOLATION[:NO]
```

## <a name="remarks"></a>Remarks

または、 **[いいえ]** に設定すると、マニフェストがないかのように dll が読み込まれ、 `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION`リンカーによってオプションの`DllCharacteristics`ヘッダーのフィールドにビットが設定されます。

また、オペレーティングシステムはマニフェストの参照と読み込みを実行します。

これが既定値です。

実行可能ファイルの分離が無効になっている場合、Windows ローダーは、新しく作成されたプロセスのアプリケーションマニフェストの検索を試行しません。 新しいプロセスには、実行可能ファイル内にマニフェストがある場合や、実行可能ファイルという名前の実行可能ファイルと同じディレクトリに配置されている場合でも、既定のアクティベーションコンテキストがありません。

詳細については、「[マニフェストファイルリファレンス](/windows/win32/SbsCs/manifest-files-reference)」を参照してください。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ** > ] [**リンカー** > **マニフェストファイル**] プロパティページを選択します。

1. "**分離を許可する**" プロパティを変更します。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
