---
title: CreatorMap 構造体
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::CreatorMap
- implements/Microsoft::WRL::Details::CreatorMap
- module/Microsoft::WRL::Details::CreatorMap::activationId
- module/Microsoft::WRL::Details::CreatorMap::factoryCache
- module/Microsoft::WRL::Details::CreatorMap::factoryCreator
- module/Microsoft::WRL::Details::CreatorMap::serverName
helpviewer_keywords:
- Microsoft::WRL::Details::CreatorMap structure
- Microsoft::WRL::Details::CreatorMap::activationId data member
- Microsoft::WRL::Details::CreatorMap::factoryCache data member
- Microsoft::WRL::Details::CreatorMap::factoryCreator data member
- Microsoft::WRL::Details::CreatorMap::serverName data member
ms.assetid: 94e40927-90c3-4107-bca3-3ad2dc4beda9
ms.openlocfilehash: 44d06f317661059bea92d8c6f27955606a964bb7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398616"
---
# <a name="creatormap-structure"></a>CreatorMap 構造体

Windows ランタイム C++ テンプレート ライブラリのインフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
struct CreatorMap;
```

## <a name="remarks"></a>Remarks

初期化し登録、およびオブジェクトの登録を解除する方法についてを説明します。

`CreatorMap`には次の情報が含まれます。

- 初期化し登録、およびオブジェクトの登録を解除する方法。

- 従来の COM または Windows ランタイムのファクトリによってライセンス認証データを比較する方法。

- インターフェイスのファクトリ キャッシュおよびサーバー名について説明します。

## <a name="members"></a>メンバー

### <a name="public-data-members"></a>パブリック データ メンバー

名前                                          | 説明
--------------------------------------------- | ------------------------------------------------------------------------------------------------------
[CreatorMap::activationId](#activationid)     | クラシック COM クラスの ID または Windows ランタイムの名前によって識別されるオブジェクト ID を表します。
[CreatorMap::factoryCache](#factorycache)     | 工場出荷時のキャッシュへのポインターを格納、`CreatorMap`します。
[CreatorMap::factoryCreator](#factorycreator) | 指定したファクトリを作成します`CreatorMap`します。
[CreatorMap::serverName](#servername)         | サーバー名を格納、`CreatorMap`します。

## <a name="inheritance-hierarchy"></a>継承階層

`CreatorMap`

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::WRL::Details

## <a name="activationid"></a>Creatormap::activationid

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
union {
   const IID* clsid;
   const wchar_t* (*getRuntimeName)();
} activationId;
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
インターフェイス ID。

*getRuntimeName*<br/>
オブジェクトの Windows ランタイムの名前を取得する関数。

### <a name="remarks"></a>Remarks

クラシック COM クラスの ID または Windows ランタイムの名前によって識別されるオブジェクト ID を表します。

## <a name="factorycache"></a>CreatorMap::factoryCache

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
FactoryCache* factoryCache;
```

### <a name="remarks"></a>Remarks

工場出荷時のキャッシュへのポインターを格納、`CreatorMap`します。

## <a name="factorycreator"></a>CreatorMap::factoryCreator

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
HRESULT (*factoryCreator)(
   unsigned int* currentflags,
   const CreatorMap* entry,
   REFIID iidClassFactory,
IUnknown** factory);
```

### <a name="parameters"></a>パラメーター

*currentflags*<br/>
1 つ、 [RuntimeClassType](runtimeclasstype-enumeration.md)列挙子。

*entry*<br/>
CreatorMap は。

*iidClassFactory*<br/>
クラス ファクトリのインターフェイス ID。

*ファクトリ*<br/>
操作が完了時は、クラス ファクトリのアドレス。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

### <a name="remarks"></a>Remarks

指定した CreatorMap のファクトリを作成します。

## <a name="servername"></a>CreatorMap::serverName

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
const wchar_t* serverName;
```

### <a name="remarks"></a>Remarks

CreatorMap のサーバー名を格納します。
