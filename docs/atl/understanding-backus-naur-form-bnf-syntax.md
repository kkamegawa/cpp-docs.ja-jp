---
title: ATL レジストラーと Backus-Naur form (BNF) 構文
ms.date: 05/14/2019
helpviewer_keywords:
- BNF notation
- Backus-Naur form (BNF) syntax
ms.assetid: 994bbef0-9077-4aa8-bdfe-b7e830af9acc
ms.openlocfilehash: 77f0fa6fef8e517e5714d1da6c61d0e310e0718c
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65709182"
---
# <a name="understanding-backus-naur-form-bnf-syntax"></a>Backus-Naur form (BNF) 構文を理解する

ATL レジストラーで使用されるスクリプトは、このトピックでは BNF 構文を使用して記述されています。つまり、次の表に示されている表記を使用しています。

|規則/シンボル|説明|
|------------------------|-------------|
|::=|同等の表記|
|&#124;|OR|
|X+|1 つ以上の X。|
|\[X]|X は省略可能です。 省略可能な区切り記号は \[] で示されています。|
|すべての**太字**テキスト|文字列リテラル。|
|すべての*斜体*テキスト|文字列リテラルを作成する方法。|

上記の表に示されているように、レジストラー スクリプトでは文字列リテラルが使用されます。 これらの値は、スクリプトに表示する必要がある実際のテキストです。 次の表で、ATL レジストラー スクリプトで使用される文字列リテラルについて説明します。

|リテラル文字列|アクション|
|--------------------|------------|
|**ForceRemove**|次のキー (存在する場合) を完全に削除してから再作成します。|
|**NoRemove**|登録解除時に次のキーを削除しません。|
|**val**|`<Key Name>` が実際には名前付きの値であることを指定します。|
|**削除**|登録時に次のキーを削除します。|
|**s**|次の値が文字列 (REG_SZ) であることを指定します。|
|**d**|次の値がダブルワード (REG_DWORD) であることを指定します。|
|**m**|次の値が複数行文字列 (REG_MULTI_SZ) であることを指定します。|
|**b**|次の値がバイナリ値 (REG_BINARY) であることを指定します。|

## <a name="bnf-syntax-examples"></a>BNF 構文例

ATL レジストラー スクリプトで表記と文字列リテラルがどのように機能するかを理解するのに役立つ構文例をいくつか示します。

### <a name="syntax-example-1"></a>構文例 1

```
<registry expression> ::= <Add Key>
```

`registry expression` が `Add Key` と等しいことを指定します。

### <a name="syntax-example-2"></a>構文例 2

```
<registry expression> ::= <Add Key> | <Delete Key>
```

`registry expression` が `Add Key` または `Delete Key` と等しいことを指定します。

### <a name="syntax-example-3"></a>構文例 3

```
<Key Name> ::= '<AlphaNumeric>+'
```

`Key Name` が 1 つ以上の `AlphaNumerics` と等しいことを指定します。

### <a name="syntax-example-4"></a>構文例 4

```
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name>
```

`Add Key` が `Key Name` と等しく、文字列リテラル、`ForceRemove`、`NoRemove`、および `val` が省略可能であることを指定します。

### <a name="syntax-example-5"></a>構文例 5

```
<AlphaNumeric> ::= any character not NULL, that is, ASCII 0
```

`AlphaNumeric` が任意の NULL 以外の文字と等しいことを指定します。

### <a name="syntax-example-6"></a>構文例 6

```
val 'testmulti' = m 'String 1\0String 2\0'
```

キー名 `testmulti` が `String 1` と `String 2` で構成される複数行文字列の値であることを指定します。

### <a name="syntax-example-7"></a>構文例 7

```
val 'testhex' = d '&H55'
```

キー名 `testhex` が 16 進数の 55 (10 進数の 85) に設定されたダブルワード値であることを指定します。 この形式は、Visual Basic 仕様に記載されている **&H** 表記に準拠していることに注意してください。

## <a name="see-also"></a>関連項目

[レジストラー スクリプトの作成](../atl/creating-registrar-scripts.md)
