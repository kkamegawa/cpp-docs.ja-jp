---
title: クラス ファクトリとライセンス
ms.date: 11/04/2016
helpviewer_keywords:
- class factories [MFC], and licensing
ms.assetid: 53c4856a-4062-46db-9f69-dd4339f746b3
ms.openlocfilehash: 18d86122e57af056a50a4d94bac89d65a7b71c7d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855757"
---
# <a name="class-factories-and-licensing"></a>クラス ファクトリとライセンス

OLE コントロールのインスタンスを作成するために、コンテナーアプリケーションは、コントロールのクラスファクトリのメンバー関数を呼び出します。 コントロールは実際の OLE オブジェクトであるため、クラスファクトリはコントロールのインスタンスを作成します。 すべての OLE コントロールクラスには、クラスファクトリが必要です。

OLE コントロールのもう1つの重要な機能は、ライセンスを適用する機能です。 ControlWizard では、コントロールプロジェクトの作成時にライセンスを組み込むことができます。 コントロールのライセンスの詳細については、「 [Activex コントロール: ライセンスの Activex コントロール](../../mfc/mfc-activex-controls-licensing-an-activex-control.md)」を参照してください。

次の表に、コントロールのクラスファクトリを宣言して実装し、コントロールのライセンスを適用するために使用されるいくつかのマクロと関数を示します。

### <a name="class-factories-and-licensing"></a>クラス ファクトリとライセンス

|||
|-|-|
|[DECLARE_OLECREATE_EX](#declare_olecreate_ex)|OLE コントロールまたはプロパティページのクラスファクトリを宣言します。|
|[IMPLEMENT_OLECREATE_EX](#implement_olecreate_ex)|コントロールの `GetClassID` 関数を実装し、クラスファクトリのインスタンスを宣言します。|
|[BEGIN_OLEFACTORY](#begin_olefactory)|任意のライセンス関数の宣言を開始します。|
|[END_OLEFACTORY](#end_olefactory)|任意のライセンス関数の宣言を終了します。|
|[AfxVerifyLicFile](#afxverifylicfile)|コントロールが特定のコンピューターで使用するためにライセンスを付与されているかどうかを確認します。|

##  <a name="declare_olecreate_ex"></a>DECLARE_OLECREATE_EX

クラスファクトリと、コントロールクラスの `GetClassID` メンバー関数を宣言します。

```
DECLARE_OLECREATE_EX(class_name)
```

### <a name="parameters"></a>パラメーター

*class_name*<br/>
コントロールクラスの名前。

### <a name="remarks"></a>解説

ライセンスをサポートしないコントロールについては、コントロールクラスのヘッダーファイルでこのマクロを使用します。

このマクロは、次のコードサンプルと同じ目的で動作することに注意してください。

[!code-cpp[NVC_MFCAxCtl#14](../../mfc/reference/codesnippet/cpp/class-factories-and-licensing_1.h)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="implement_olecreate_ex"></a>IMPLEMENT_OLECREATE_EX

コントロールのクラスファクトリと、コントロールクラスの[GetClassID](../../mfc/reference/colecontrol-class.md#getclassid)メンバー関数を実装します。

```
IMPLEMENT_OLECREATE_EX(
   class_name,
    external_name,
    l,
    w1,
    w2,
    b1,
    b2,
    b3,
    b4,
    b5,
    b6,
    b7,
    b8)
```

### <a name="parameters"></a>パラメーター

*class_name*<br/>
コントロールプロパティページクラスの名前。

*external_name*<br/>
アプリケーションに公開されているオブジェクト名。

*l、w1、w2、b1、b2、b3、b4、b5、b6、b7、b8*<br/>
クラスの CLSID のコンポーネント。 これらのパラメーターの詳細については、 [IMPLEMENT_OLECREATE](run-time-object-model-services.md#implement_olecreate)の解説を参照してください。

### <a name="remarks"></a>解説

このマクロは、DECLARE_OLECREATE_EX マクロ、BEGIN_OLEFACTORY および END_OLEFACTORY マクロを使用するコントロールクラスの実装ファイルに記述されている必要があります。 外部名は、他のアプリケーションに公開されている OLE コントロールの識別子です。 コンテナーはこの名前を使用して、このコントロールクラスのオブジェクトを要求します。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="begin_olefactory"></a>BEGIN_OLEFACTORY

コントロールクラスのヘッダーファイル内のクラスファクトリの宣言を開始します。

```
BEGIN_OLEFACTORY(class_name)
```

### <a name="parameters"></a>パラメーター

*class_name*<br/>
クラスファクトリを持つコントロールクラスの名前を指定します。

### <a name="remarks"></a>解説

クラスファクトリライセンス関数の宣言は、BEGIN_OLEFACTORY の直後に開始する必要があります。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="end_olefactory"></a>END_OLEFACTORY

コントロールのクラスファクトリの宣言を終了します。

```
END_OLEFACTORY(class_name)
```

### <a name="parameters"></a>パラメーター

*class_name*<br/>
クラスファクトリを持つコントロールクラスの名前。

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

##  <a name="afxverifylicfile"></a>AfxVerifyLicFile

`pszLicFileName` によって指定されたライセンスファイルが OLE コントロールに対して有効であることを確認するには、この関数を呼び出します。

```
BOOL AFXAPI AfxVerifyLicFile(
    HINSTANCE  hInstance,
    LPCTSTR  pszLicFileName,
    LPOLESTR  pszLicFileContents,
    UINT cch = -1);
```

### <a name="parameters"></a>パラメーター

*hInstance*<br/>
ライセンスされたコントロールに関連付けられている DLL のインスタンスハンドル。

*Pszファイル名*<br/>
は、ライセンスファイル名を含む null で終わる文字列を指します。

*pszLicFileContents*<br/>
は、ライセンスファイルの先頭で見つかったシーケンスと一致する必要があるバイトシーケンスを指します。

*cch*<br/>
*PszLicFileContents*の文字数。

### <a name="return-value"></a>戻り値

ライセンスファイルが存在し、 *pszLicFileContents*の文字シーケンスで始まる場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

*Cch*が-1 の場合、この関数は次を使用します。

[!code-cpp[NVC_MFC_Utilities#36](../../mfc/codesnippet/cpp/class-factories-and-licensing_2.cpp)]

### <a name="requirements"></a>必要条件

  **ヘッダー** afxctl.h

## <a name="see-also"></a>参照

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
