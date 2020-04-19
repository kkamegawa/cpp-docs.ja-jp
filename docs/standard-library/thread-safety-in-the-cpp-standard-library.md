---
title: C++ 標準ライブラリ内のスレッド セーフ
ms.date: 11/04/2016
helpviewer_keywords:
- thread safety
- C++ Standard Library, thread safety
- thread safety, C++ Standard Library
ms.assetid: 9351c8fb-4539-4728-b0e9-226e2ac4284b
ms.openlocfilehash: 4ac029a119a77fa87c6cd004fece9c4e6b382026
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68460062"
---
# <a name="thread-safety-in-the-c-standard-library"></a>C++ 標準ライブラリ内のスレッド セーフ

次のスレッド セーフの規則は C++ 標準ライブラリのすべてのクラスに適用されます。これには、次に示すように `shared_ptr` が含まれます。  以下に示すような標準の iostream オブジェクトや、[\<atomic>](../standard-library/atomic.md) 内の型のようなマルチスレッド専用の型などでは、より強い保証が用意されています。

オブジェクトは、複数のスレッドからの読み取りに対してスレッド セーフです。 たとえば、オブジェクト A が指定された場合、スレッド 1 とスレッド 2 から A の同時読み取りを安全に行うことができます。

あるオブジェクトに対して 1 つのスレッドが書き込みを行っている場合、同じスレッドまたは別のスレッドでのそのオブジェクトに対する読み取りと書き込みはすべて保護される必要があります。 たとえば、オブジェクト A が指定され、スレッド 1 が A に書き込みを行っている場合、スレッド 2 で A の読み取りや書き取りを行えないようにする必要があります。

ある型の 1 つのインスタンスに対して読み取りや書き込みを行うのが安全です。これは、別のスレッドが同じ型の別のインスタンスに対して読み取りまたは書き込みを行っている場合でもそうです。 たとえば、同じ型のオブジェクト A と B が指定されている場合、A がスレッド 1 で書き込まれ、B がスレッド 2 で読み取られている場合は安全です。

## <a name="sharedptr"></a>shared_ptr

複数のスレッドで異なる [shared_ptr](../standard-library/shared-ptr-class.md) オブジェクト (所有権を共有するコピーである場合も含めて) に対する読み取りと書き込みを同時に行うことができます。

## <a name="iostream"></a>iostream

標準の iostream オブジェクト `cin`、`cout`、`cerr`、`clog`、`wcin`、`wcout`、`wcerr`、および `wclog` は、他のクラスと同じ規則に従いますが、例外として、複数のスレッドからオブジェクトに安全に書き込むことができます。 たとえば、スレッド 1 はスレッド 2 と同時に [cout](../standard-library/iostream.md#cout) に書き込むことができます。 ただし、2 つのスレッドからの出力が混ざる可能性があります。

> [!NOTE]
> ストリーム バッファーからの読み取りは、読み取り操作とは見なされません。 その代わりに、クラスの状態が変わるため、書き込み操作と見なされます。

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリの概要](../standard-library/cpp-standard-library-overview.md)
