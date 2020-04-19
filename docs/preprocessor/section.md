---
title: section プラグマ
ms.date: 08/29/2019
f1_keywords:
- section_CPP
- vc-pragma.section
helpviewer_keywords:
- pragmas, section
- section pragma
ms.assetid: c67215e9-2c4a-4b0f-b691-2414d2e2d96f
ms.openlocfilehash: 47ae2ff2503317e937e2b3a497357afbd5522a64
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216600"
---
# <a name="section-pragma"></a>section プラグマ

.obj ファイルにセクションを作成します。

## <a name="syntax"></a>構文

> **#pragma セクション (** "*section-name*" [ **,** *attributes* ] **)**

## <a name="remarks"></a>Remarks

この記事では、*セグメント*と*セクション*という用語は同じ意味を持ちます。

セクションを定義すると、そのセクションはそれ以降のコンパイルで有効になります。 ただし、 [__declspec (allocate)](../cpp/allocate.md)を使用する必要があります。または、セクションに何も配置されていません。

*section-name*は、セクションの名前になる必須パラメーターです。 標準セクション名と競合する名前は付けられません。 セクションを作成するときに使用しない名前の一覧については、「 [/SECTION](../build/reference/section-specify-section-attributes.md) 」を参照してください。

*attributes*は、セクションに割り当てる1つ以上のコンマ区切りの属性で構成される省略可能なパラメーターです。 使用できる*属性*は次のとおりです。

|属性|説明|
|-|-|
|**read**|データの読み取り操作を有効にします。|
|**write**|データの書き込み操作を有効にします。|
|**execute**|コードを実行できるようにします。|
|**shared**|イメージを読み込んだすべてのプロセス間でセクションを共有します。|
|**nopage**|セクションをページング不可としてマークします。 Win32 デバイスドライバーに便利です。|
|**nocache**|セクションをキャッシュ不可能としてマークします。 Win32 デバイスドライバーに便利です。|
|**discard**|セクションを破棄不可としてマークします。 Win32 デバイスドライバーに便利です。|
|**remove**|セクションをメモリ常駐ではないとしてマークします。 仮想デバイスドライバー (V*x*D) のみ。|

属性を指定しない場合、セクションには**読み取り**属性と**書き込み**属性があります。

## <a name="example"></a>例

この例では、最初のセクションのプラグマはセクションとその属性を識別します。 を使用`j` `mysec` して宣言されていないため、整数はに格納さ`__declspec(allocate)`れません。 代わりに、 `j`データセクションに移動します。 整数 `i` は、その `mysec` ストレージ クラス属性の結果として `__declspec(allocate)` に追加されます。

```cpp
// pragma_section.cpp
#pragma section("mysec",read,write)
int j = 0;

__declspec(allocate("mysec"))
int i = 0;

int main(){}
```

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
