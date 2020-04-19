---
title: embedded_idl import 属性
ms.date: 08/29/2019
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: 01948b171b20ad0a3bf3e7a41047f1fe3df185b0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216329"
---
# <a name="embedded_idl-import-attribute"></a>embedded_idl import 属性

**C++のみ**

属性によって生成されたコード`.tlh`が保存されているファイルにタイプライブラリを書き込むかどうかを指定します。

## <a name="syntax"></a>構文

> **#import***タイプライブラリ***embedded_idl**[ **(** { **"emitidl"**  |  **"no_emitidl"** } **)** ]

### <a name="parameters"></a>パラメーター

**emitidl**\
*タイプライブラリ*からインポートされた型情報は、属性付きプロジェクト用に生成された IDL に存在します。 この動作は既定値であり、に`embedded_idl`パラメーターを指定しない場合は有効です。

**"no_emitidl"** \
*タイプライブラリ*からインポートされた型情報が、属性付きプロジェクト用に生成された IDL に存在しません。

## <a name="example"></a>例

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

**特定C++の終了**

## <a name="see-also"></a>関連項目

[#import 属性](../preprocessor/hash-import-attributes-cpp.md)\
[#import ディレクティブ](../preprocessor/hash-import-directive-cpp.md)
