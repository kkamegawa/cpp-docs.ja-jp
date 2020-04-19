---
title: リソース識別子 (シンボル) (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.symbol.identifiers
helpviewer_keywords:
- symbols [C++], resource identifiers
- symbols [C++], creating
- resource symbols
- symbols [C++], editing
- resource editors [C++], resource symbols
ms.assetid: 8fccc09a-0237-4a65-b9c4-57d60c59e324
ms.openlocfilehash: 0b19ff0d1c709616868d47c172ff4cf8c6931b82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387878"
---
# <a name="resource-identifiers-symbols-c"></a>リソース識別子 (シンボル) (C++)

シンボルは、リソース識別子 (ID) の 2 つの部分で構成されるなどのシンボル値 (整数) にマップされているシンボル名 (文字列) を示します。

```
IDC_EDITNAME = 5100
```

シンボル名は一般的に、識別子と呼ばれます。

シンボルは、ソース コード内で、およびリソース エディターで作業している間に、リソースおよびユーザー インターフェース オブジェクトを参照するためのわかりやすい手段を提供します。 シンボルは [[リソース シンボル] ダイアログ ボックス](../windows/viewing-resource-symbols.md)を使用して、都合の良い 1 箇所に表示して操作することができます。

アプリケーションのサイズが大きくなり、複雑になるにつれ、リソースとシンボルの数も増えます。 いくつかのファイルに散在する大量のシンボルを追跡することは困難な場合があります。 **リソース シンボル** ダイアログ ボックスは、できる中心的なツールを提供することでシンボルの管理を簡略化されます。

- [シンボルを作成します。](../windows/creating-new-symbols.md)

- [シンボルを管理します。](../windows/changing-a-symbol-or-symbol-name-id.md)

- [定義済みシンボル ID の表示](../windows/predefined-symbol-ids.md)

新しいリソースやリソース オブジェクトを作成する際、 [リソース エディター](../windows/resource-editors.md) は、リソースの既定の名前 (たとえば `IDC_RADIO1`) を提供し、値をそれに割り当てます。 名前値の定義に格納されます、`Resource.h`ファイル。

> [!NOTE]
> リソースやリソース オブジェクトを 1 つの .rc ファイルから別のファイルにコピーする際、Visual C++ は、転送されるリソースのシンボル値、またはシンボル名と値を変更する可能性があります。これは、既存のファイルのシンボル名や値との競合を回避するためです。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[リソース ファイルの操作](../windows/working-with-resource-files.md)<br/>
[リソース ファイル](../windows/resource-files-visual-studio.md)<br/>
[リソース エディター](../windows/resource-editors.md)<br/>