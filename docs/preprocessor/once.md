---
title: once プラグマ
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.once
- once_CPP
helpviewer_keywords:
- once pragma
- pragmas, once
ms.assetid: c7517556-6403-4b16-8898-f2aa0a6f685f
ms.openlocfilehash: 643ad83b672f7b632925383972751a966256eb41
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220543"
---
# <a name="once-pragma"></a>once プラグマ

ソースコードファイルをコンパイルするときに、コンパイラがヘッダーファイルを1回だけインクルードすることを指定します。

## <a name="syntax"></a>構文

> **一度 #pragma**

## <a name="remarks"></a>Remarks

を使用`#pragma once`すると、ビルド時間を短縮できます。これは、変換単位の最初`#include`のファイルの後にコンパイラが開かず、ファイルを再度読み取るためです。 これは、*複数インクルードの最適化*と呼ばれます。 これは、*インクルードガード*表現に似ています。これは、プリプロセッサマクロ定義を使用して、ファイルの内容が複数インクルードされないようにします。 また、 *1 つの定義規則*に違反しないようにすることもできます。これは、すべてのテンプレート、型、関数、およびオブジェクトがコード内で定義を1つしか持たないという要件です。

例えば:

```cpp
// header.h
#pragma once
// Code placed here is included only once per translation unit
```

新しいコードには `#pragma once` ディレクティブを使用することをお勧めします。これを使えば、プリプロセッサ シンボルによるグローバル名前空間のポリューションが発生しないためです。 これには、入力が少なく、混乱が少なく、*シンボルの競合*を発生させることはできません。異なるヘッダーファイルで、ガード値と同じプリプロセッサシンボルが使用されていると、エラーが発生します。 これはC++標準の一部ではありませんが、いくつかの一般的なコンパイラによって移植に実装されています。

インクルードガード表現とを`#pragma once`同じファイル内に使用する利点はありません。 コンパイラはインクルードガード表現を認識し、非コメントコードまたはプリプロセッサディレクティブが標準形式`#pragma once`の表現の前または後にある場合、ディレクティブと同じ方法で複数インクルードの最適化を実装します。

```cpp
// header.h
// Demonstration of the #include guard idiom.
// Note that the defined symbol can be arbitrary.
#ifndef HEADER_H_     // equivalently, #if !defined HEADER_H_
#define HEADER_H_
// Code placed here is included only once per translation unit
#endif // HEADER_H_
```

`#pragma once`ディレクティブを実装しないコンパイラにコードを移植する必要がある場合、既存のコードとの一貫性を維持する場合、または複数インクルードの最適化が不可能な場合は、ガード表現を含めることをお勧めします。 複雑なプロジェクトでは、ファイルシステムの別名またはエイリアスインクルードパスを使用すると、コンパイラが正規のパスによって同一のインクルードファイルを識別できなくなる場合があります。

を使用`#pragma once`しないようにするか、複数回含めるように設計されたヘッダーファイルにガード表現を含めることは、その効果を制御するためにプリプロセッサシンボルを使用することに注意してください。 この設計の例については、 \<「assert > ヘッダーファイル」を参照してください。 また、インクルードファイルへの複数のパスを作成しないように、インクルードパスを慎重に管理してください。これにより、 `#pragma once`ガードとの両方に対して複数インクルードの最適化を無効にすることができます。

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
