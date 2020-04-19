---
title: プロバイダーでのフリー スレッドのサポート
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB providers, multithreaded
- threading [C++], providers
ms.assetid: a91270dc-cdf9-4855-88e7-88a54be7cbe8
ms.openlocfilehash: a2afb7354dd0447375ee6205b7c5d9a4755aa4b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404495"
---
# <a name="supporting-free-threading-in-your-provider"></a>プロバイダーでのフリー スレッドのサポート

OLE DB プロバイダーのすべてのクラスは、スレッド セーフであると、レジストリ エントリを適宜設定されます。 高レベルのマルチ ユーザー環境でのパフォーマンスを確保するためのフリー スレッドをサポートすることをお勧めします。 スレッド セーフである、プロバイダーに保つためには、コードが正常にブロックされていることを確認する必要があります。 書き込みまたはデータを格納するたびに、クリティカル セクションを使用してアクセスをブロックする必要があります。

各 OLE DB プロバイダー テンプレート オブジェクトには、独自の重要なセクションがあります。 作成する新しい各クラスが親クラスのテンプレート クラスをするブロッキングを簡単にするために、引数として名前。

次の例では、コードをブロックする方法を示します。

```cpp
template <class T>
class CMyObject<T> : public...

HRESULT MyObject::MyMethod(void)
{
   T* pT = (T*)this;      // this gets the parent class

// You don't need to do anything if you are only reading information

// If you want to write information, do the following:
   pT->Lock();         // engages critical section in the object
   ...;                // write whatever information you wish
   pT->Unlock();       // disengages the critical section
}
```

クリティカル セクションを保護する方法の詳細についての`Lock`と`Unlock`を参照してください[マルチ スレッド。同期クラスの使用方法](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)します。

オーバーライドするメソッドを確認します (など`Execute`) スレッド セーフです。

## <a name="see-also"></a>関連項目

[OLE DB プロバイダー テンプレートの操作](../../data/oledb/working-with-ole-db-provider-templates.md)