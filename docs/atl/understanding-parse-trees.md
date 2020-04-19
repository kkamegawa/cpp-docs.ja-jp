---
title: ATL レジストラーと解析ツリー
ms.date: 11/04/2016
helpviewer_keywords:
- parse trees
ms.assetid: 668ce2dd-a1c3-4ca0-8135-b25267cb6a85
ms.openlocfilehash: e1aea573e78e6f6a9a86bc4e3987ee448815f329
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62196169"
---
# <a name="understanding-parse-trees"></a>パース ツリーについて

次の形式である各解析ツリー、レジストラー スクリプトでは、1 つまたは複数の解析ツリーを定義できます。

```
<root key>{<registry expression>}+
```

それぞれの文字について以下に説明します。

```
<root key> ::= HKEY_CLASSES_ROOT | HKEY_CURRENT_USER |
    HKEY_LOCAL_MACHINE | HKEY_USERS |
    HKEY_PERFORMANCE_DATA | HKEY_DYN_DATA |
    HKEY_CURRENT_CONFIG | HKCR | HKCU |
    HKLM | HKU | HKPD | HKDD | HKCC
<registry expression> ::= <Add Key> | <Delete Key>
<Add Key> ::= [ForceRemove | NoRemove | val]<Key Name> [<Key Value>][{<Add Key>}]
<Delete Key> ::= Delete<Key Name>
<Key Name> ::= '<AlphaNumeric>+'
<AlphaNumeric> ::= any character not NULL, i.e. ASCII 0
<Key Value> ::== <Key Type><Key Name>
<Key Type> ::= s | d
<Key Value> ::= '<AlphaNumeric>'
```

> [!NOTE]
> `HKEY_CLASSES_ROOT` `HKCR`は同等です。`HKEY_CURRENT_USER`と`HKCU`は同等; で、これをします。

解析ツリーは、複数のキーとサブキーを追加できます、\<ルート キー >。 そのため、そのサブキーのハンドルを開いたままパーサーのすべてのサブキーの解析が完了するまで。 このアプローチは、次の例に示すように、一度に 1 つのキーで動作しているよりも効率的です。

```
HKEY_CLASSES_ROOT
{
    'MyVeryOwnKey'
    {
        'HasASubKey'
        {
            'PrettyCool'
        }
    }
}
```

レジストラーが最初に開くここでは、(作成)`HKEY_CLASSES_ROOT\MyVeryOwnKey`します。 認識し、`MyVeryOwnKey`サブキーがあります。 キーを閉じるのではなく`MyVeryOwnKey`、レジストラーが、ハンドルを保持し、開きます (作成)`HasASubKey`この親ハンドルを使用します。 (システム レジストリできます低速親ハンドルが開いていない場合) です。ため、開いて`HKEY_CLASSES_ROOT\MyVeryOwnKey`を開くと`HasASubKey`で`MyVeryOwnKey`親は開始よりも高速`MyVeryOwnKey`終了、 `MyVeryOwnKey`、して開く`MyVeryOwnKey\HasASubKey`します。

## <a name="see-also"></a>関連項目

[レジストラー スクリプトの作成](../atl/creating-registrar-scripts.md)
