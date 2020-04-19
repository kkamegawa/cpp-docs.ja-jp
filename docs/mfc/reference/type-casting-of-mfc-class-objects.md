---
title: MFC クラス オブジェクトの型キャスト
ms.date: 11/04/2016
helpviewer_keywords:
- macros [MFC], type casting
- pointers [MFC], type casting
- type casts [MFC]
- casting types [MFC]
- macros [MFC], casting pointers
ms.assetid: e138465e-c35f-4e84-b788-bd200ccf2f0e
ms.openlocfilehash: c7586f3c3f3aefd78fa868cc847df27e8aac58ab
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65611651"
---
# <a name="type-casting-of-mfc-class-objects"></a>MFC クラス オブジェクトの型キャスト

型キャストのマクロは、指定されたポインター、キャストが正しくことのチェックの有無の特定のクラスのオブジェクトを指すポインターをキャストする方法を提供します。

次の表では、MFC の型のキャスト マクロを示します。

### <a name="macros-that-cast-pointers-to-mfc-class-objects"></a>MFC クラス オブジェクトへのポインターのキャスト マクロ

|||
|-|-|
|[DYNAMIC_DOWNCAST](#dynamic_downcast)|キャストが有効かどうかを確認中に、クラスのオブジェクトへのポインターへのポインターにキャストします。|
|[STATIC_DOWNCAST](#static_downcast)|ポインターに関連する型の 1 つのクラスからオブジェクトへのポインターにキャストします。 デバッグ ビルドでは、assert、オブジェクトがない場合、対象の型「の種類」です。|

##  <a name="dynamic_downcast"></a>  DYNAMIC_DOWNCAST

キャストが有効かどうかを確認中に、クラスのオブジェクトへのポインターへのポインターをキャストする便利な方法を提供します。

```
DYNAMIC_DOWNCAST(class, pointer)
```

### <a name="parameters"></a>パラメーター

*class*<br/>
クラスの名前。

*pointer*<br/>
型のオブジェクトへのポインターにキャストへのポインター*クラス*します。

### <a name="remarks"></a>Remarks

マクロはキャスト、*ポインター*パラメーターのオブジェクトへのポインターを*クラス*パラメーターの型。

マウス ポインターによって参照されるオブジェクトがある場合、特定のクラス「の種類」マクロは、適切なポインターを返します。 有効なキャストされていない場合、マクロは、NULL を返します。

##  <a name="static_downcast"></a>  STATIC_DOWNCAST

キャスト*pobject*へのポインターを*class_name*オブジェクト。

```
STATIC_DOWNCAST(class_name, pobject)
```

### <a name="parameters"></a>パラメーター

*class_name*<br/>
キャストされているクラスの名前。

*pobject*<br/>
ポインターにキャストへのポインターを*class_name*オブジェクト。

### <a name="remarks"></a>Remarks

*pobject*する必要がありますか、null の場合、またはオブジェクトの直接派生するクラスまたはから間接的に指す*class_name*します。 _DEBUG プリプロセッサ シンボルを定義、アプリケーションのビルドで、マクロはアサート場合*pobject*が NULL でないでないオブジェクトを指している場合やで指定されたクラス「の種類」、 *class_name*パラメーター (を参照してください[使うため](../../mfc/reference/cobject-class.md#iskindof))。 以外で **_DEBUG**ビルドでは、マクロが型チェックを行わず、キャストを実行します。

指定したクラス、 *class_name*パラメーターから派生する必要があります`CObject`DECLARE_DYNAMIC と IMPLEMENT_DYNAMIC、DECLARE_DYNCREATE とする場合、または DECLARE_SERIAL と IMPLEMENT_ を使用する必要がありますこの記事で説明されているシリアル マクロとして[CObject クラス。CObject からクラスを派生する](../../mfc/deriving-a-class-from-cobject.md)します。

たとえばへのポインターをキャストする場合があります`CMyDoc`という`pMyDoc`へのポインターに`CDocument`この式を使用して。

[!code-cpp[NVC_MFCDocView#197](../../mfc/codesnippet/cpp/type-casting-of-mfc-class-objects_1.cpp)]

場合`pMyDoc`から直接または間接的に派生したオブジェクトを指していない`CDocument`マクロがアサートされます。

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
