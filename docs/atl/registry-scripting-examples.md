---
title: レジストリ スクリプトの例
ms.date: 11/04/2016
helpviewer_keywords:
- scripting, examples
- registrar scripts [ATL]
- scripts, Registrar scripts
- registry, Registrar
ms.assetid: b6df80e1-e08b-40ee-9243-9b381b172460
ms.openlocfilehash: dffdd111d33d6fbd845e1534cdef1d5c8e1749d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62275413"
---
# <a name="registry-scripting-examples"></a>レジストリ スクリプトの例

このトピックでは、スクリプトの例では、システム レジストリにキーを追加、レジストラーの COM サーバーを登録し、複数の解析ツリーを指定する方法を示します。

## <a name="add-a-key-to-hkeycurrentuser"></a>HKEY_CURRENT_USER にキーを追加します。

次の解析ツリーは、1 つのキーをシステム レジストリに追加する単純なスクリプトを示しています。 具体的には、スクリプトは、キーを追加します。`MyVeryOwnKey`を`HKEY_CURRENT_USER`します。 既定の文字列値を割り当てます`HowGoesIt`新しいキー。

```
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

このスクリプトは、複数のサブキーを次のように定義を簡単に拡張できます。

```
HKCU
{
    'MyVeryOwnKey' = s 'HowGoesIt'
    {
        'HasASubkey'
        {
            'PrettyCool' = d '55'
            val 'ANameValue' = s 'WithANamedValue'
        }
    }
}
```

ここで、スクリプトは、サブキーを追加します。`HasASubkey`を`MyVeryOwnKey`します。 追加どちらも、このサブキーに、`PrettyCool`サブキー (既定値は、 `DWORD` 55 の値)、`ANameValue`名前付きの値 (の文字列値を持つ`WithANamedValue`)。

##  <a name="_atl_register_the_registrar_com_server"></a> レジストラーは、COM サーバーを登録します。

次のスクリプトでは、レジストラーの COM サーバー自体を登録します。

```
HKCR
{
    ATL.Registrar = s 'ATL Registrar Class'
    {
        CLSID = s '{44EC053A-400F-11D0-9DCD-00A0C90391D3}'
    }
    NoRemove CLSID
    {
        ForceRemove {44EC053A-400F-11D0-9DCD-00A0C90391D3} = s 'ATL Registrar Class'
        {
            ProgID = s 'ATL.Registrar'
            InprocServer32 = s '%MODULE%'
            {
                val ThreadingModel = s 'Apartment'
            }
        }
    }
}
```

この解析ツリーを追加、実行時に、`ATL.Registrar`キー`HKEY_CLASSES_ROOT`します。 この新しいキーにし、it:

- 指定します`ATL Registrar Class`キーの既定の文字列値として。

- 追加`CLSID`サブキーとして。

- 指定します`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`の`CLSID`します。 (この値は、レジストラーで使用するための CLSID `CoCreateInstance`)。

`CLSID`は、共有、削除してはなりません登録解除のモードでします。 このステートメントでは、`NoRemove CLSID`であることを示す`CLSID`登録モードで開かれ、登録解除のモードでは無視する必要があります。

`ForceRemove`ステートメントは、キーを再作成する前に、キーとそのすべてのサブキーを削除することによって、ハウスキーピング機能を提供します。 サブキーの名前が変更された場合に便利なことができます。 このスクリプトの例では`ForceRemove`かどうかをチェック`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`既に存在します。 その場合、 `ForceRemove`:

- 再帰的に削除`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`とそのすべてのサブキー。

- 再作成`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`です。

- 追加`ATL Registrar Class`の既定の文字列値として`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`します。

解析ツリーを 2 つの新しいサブキー追加`{44EC053A-400F-11D0-9DCD-00A0C90391D3}`します。 最初のキー `ProgID`ProgID は、既定の文字列値を取得します。 2 番目のキー `InprocServer32`、既定の文字列値を取得します。`%MODULE%`はプリプロセッサ値についてのセクションで説明[置き換え可能パラメーターの使用 (レジストラーのプリプロセッサ)](../atl/using-replaceable-parameters-the-registrar-s-preprocessor.md)、この記事の。 `InprocServer32` 名前付きの値を取得また`ThreadingModel`の文字列値を持つ`Apartment`。

## <a name="specify-multiple-parse-trees"></a>複数の解析ツリーを指定します。

スクリプトでは、複数の解析ツリーを指定するには、別の最後に 1 つのツリーを配置します。 たとえば、次のスクリプトは、キーを追加します`MyVeryOwnKey`、両方の解析ツリーを`HKEY_CLASSES_ROOT`と`HKEY_CURRENT_USER`:。

```
HKCR
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
HKEY_CURRENT_USER
{
    'MyVeryOwnKey' = s 'HowGoesIt'
}
```

> [!NOTE]
> レジストラー スクリプトでは、4 K は、最大トークン サイズです。 (トークンは、構文内の認識可能な要素です)。前のスクリプトの例で`HKCR`、 `HKEY_CURRENT_USER`、 `'MyVeryOwnKey'`、および`'HowGoesIt'`すべてトークンです。

## <a name="see-also"></a>関連項目

[レジストラー スクリプトの作成](../atl/creating-registrar-scripts.md)
