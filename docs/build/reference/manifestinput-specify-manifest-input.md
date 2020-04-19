---
title: /MANIFESTINPUT (マニフェスト入力の指定)
ms.date: 07/24/2019
ms.assetid: a0b0c21e-1f9b-4d8c-bb3f-178f57fa7f1b
ms.openlocfilehash: 7b7bd54f98003d9158276fcf75fd61ffb5348585
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606467"
---
# <a name="manifestinput-specify-manifest-input"></a>/MANIFESTINPUT (マニフェスト入力の指定)

マニフェスト入力ファイルをイメージに埋め込まれたマニフェストに含めるように指定します。

## <a name="syntax"></a>構文

```
/MANIFESTINPUT:filename
```

### <a name="parameters"></a>パラメーター

*ファイル名*<br/>
埋め込みマニフェストに含めるマニフェスト ファイル。

## <a name="remarks"></a>Remarks

**/Manifestinput**オプションは、実行可能イメージに埋め込まれたマニフェストを作成するために使用する入力ファイルのパスを指定します。 複数のマニフェスト入力ファイルがある場合は、スイッチを複数回使用します (入力ファイルごとに 1 回)。 マニフェスト入力ファイルは埋め込みマニフェストを作成するためにマージされます。 このオプションには、 **/MANIFEST: EMBED**オプションが必要です。

このオプションは、Visual Studio で直接設定することはできません。 代わりに、プロジェクトの "**追加のマニフェストファイル**" プロパティを使用して、追加のマニフェストファイルを含めるように指定します。 詳細については、「[マニフェストツールのプロパティページ](manifest-tool-property-pages.md)」を参照してください。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
