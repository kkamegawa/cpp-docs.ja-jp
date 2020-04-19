---
title: 予測実行のサイド チャネルの C++ の開発者ガイド
ms.date: 07/10/2018
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
- Spectre
- CVE-2017-5753
- Speculative Execution
ms.openlocfilehash: b3895cdb060d45d3f75c75f75c930e868b3654b2
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448611"
---
# <a name="c-developer-guidance-for-speculative-execution-side-channels"></a>予測実行のサイド チャネルの C++ の開発者ガイド

この記事にはとを識別して、C++ のソフトウェアの予測実行サイド チャネルのハードウェア脆弱性の軽減に役立つ開発者向けのガイダンスが含まれています。 これらの脆弱性は、信頼の境界を越えて機密情報を開示することができ、命令の予測、順番に実行をサポートするプロセッサで実行されるソフトウェアに影響を与えることができます。 このクラスの脆弱性が 2018 年 1 月で説明されている最初と追加の背景情報とガイダンスが記載[マイクロソフトのセキュリティ アドバイザリ](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)します。

この記事のガイダンスは、上の脆弱性によって表されるクラスに関連します。

1. CVE-2017-5753 に対する、Spectre variant 1 とも呼ばれます。 このハードウェアの脆弱性のクラスに関連する側のチャネルの条件分岐 misprediction 結果として発生する予測の実行によって発生することができます。 Microsoft C++ (バージョン 15.5.5 以降)、Visual Studio 2017 でのコンパイラにはサポートが含まれています、`/Qspectre`限られた可能性がある脆弱性のあるコーディング パターンのコンパイル時の軽減策を提供するスイッチに関連する CVE 2017-5753 に対する。 `/Qspectre`を通じて Visual Studio 2015 Update 3 で使用可能なスイッチも[KB 4338871](https://support.microsoft.com/help/4338871)します。 ドキュメント、 [/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre)フラグの効果と使用状況の詳細を提供します。

2. CVE-2018-3639 とも呼ばれます[投機的なストア バイパス (SSB)](https://aka.ms/sescsrdssb)します。 このハードウェアの脆弱性のクラスに関連する側のチャネルの結果としてメモリ アクセスの misprediction 依存ストアより負荷の予測の実行によって発生することができます。

アクセス可能な予測実行のサイド チャネルの脆弱性の概要については「プレゼンテーションのあります[ケースの Spectre や Meltdown](https://www.youtube.com/watch?v=_4O0zMW-Zu4)をこれらの問題を検出する research チームの 1 つ。

## <a name="what-are-speculative-execution-side-channel-hardware-vulnerabilities"></a>予測実行のサイド チャネルのハードウェアの脆弱性とは

最新の Cpu して高いレベルのパフォーマンスを実現する手順についての予測と順序の実行を使用します。 たとえば、多くの場合、これは、CPU を投機的予測分岐対象のデータベースに命令の実行を開始できるブランチ (条件付きおよび間接) のターゲットを予測することで、実際の分岐のターゲットになるまで、停止を避ける解決します。 イベントで後で、CPU は、misprediction が発生したことを検出、投機的に計算されたマシンの状態をすべて破棄されます。 これにより、リタイアメント推理のアーキテクチャの表示の効果はありません。

予測実行は、アーキテクチャの表示状態に影響しませんは、CPU によって使用されるさまざまなキャッシュなどのアーキテクチャではない状態に残存痕跡を残すことことができます。 これらの残存トレースのサイド チャネルの脆弱性に上昇を与えることが予測の実行することをお勧めします。 これを理解、CVE 2017-5753 (境界チェックのバイパス) の例を提供する次のコード フラグメントを考慮してください。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

この例で`ReadByte`はそのバッファーにバッファー、バッファー サイズ、およびインデックスを指定します。 指定したとおり、インデックス パラメーター `untrusted_index`、小なりによって提供される、管理者以外のプロセスなど、特権コンテキスト。 場合`untrusted_index`がより小さい`buffer_size`からインデックス位置に文字を読み取る`buffer`によって参照されるメモリの共有領域を使用するインデックスと`shared_buffer`します。

アーキテクチャの観点からこのコード シーケンスは完全に安全なことが保証されます`untrusted_index`は常により小さい`buffer_size`します。 ただし、予測の実行が存在する場合は、CPU が、条件付き分岐予測ミスし、if の本体は実行が可能な場合であってもステートメント`untrusted_index`がより大きいまたは等しい`buffer_size`します。 このため、CPU、読み取ることができます投機的境界の外部からのバイト`buffer`(シークレットがなることがあります) を使用して、そのバイト値から後続の負荷のアドレスを計算および`shared_buffer`します。

残存の副作用を境界から外に読み取られたバイトの値に関する情報を表示する CPU キャッシュに残る可能性があります、CPU には、この misprediction 検出最終的には、中に`buffer`します。 これらの副作用は小で検出できる特権コンテキストがどの程度の速度を調査して、システムで実行されている各キャッシュ行`shared_buffer`にアクセスします。 これを実現するために使用できる手順は次のとおりです。

1. **呼び出す`ReadByte`で複数回`untrusted_index`中より小さい`buffer_size`** します。 攻撃のコンテキストを呼び出す対象のコンテキストが発生することができます`ReadByte`(RPC) 経由などとして not 取得するブランチ予測子であるようなトレーニングを受けた`untrusted_index`がより小さい`buffer_size`します。

2. **内のすべてのキャッシュ行をフラッシュ`shared_buffer`** します。 攻撃のコンテキストには、すべてのキャッシュ行によって参照されるメモリの共有の領域でフラッシュする必要があります`shared_buffer`します。 これは簡単ですしなどの組み込み関数を使用して実現できますメモリ領域が共有されるため`_mm_clflush`します。

3. **呼び出す`ReadByte`で`untrusted_index`よりも大きい`buffer_size`** します。 攻撃のコンテキストにより、対象のコンテキストを呼び出す`ReadByte`正しく予測しない分岐が実行しないようにします。 このエラーの原因の場合は、の本文を投機的に実行するプロセッサがブロック`untrusted_index`よりも大きい`buffer_size`、そのため、境界外読み取りを先頭の`buffer`します。 その結果、`shared_buffer`なり、CPU によって読み込まれるそれぞれのキャッシュ ラインに境界の外では、読み取られた可能性があるシークレット値を使用してインデックスが作成されます。

4. **場合は、各キャッシュ行を読み取り`shared_buffer`これが最もすばやくアクセスする**します。 攻撃のコンテキストでのキャッシュの各行を読み取ることができます`shared_buffer`他よりも大幅に高速に読み込まれるキャッシュ ラインを検出します。 これは、手順 3 取り込まれました可能性があるキャッシュ ラインです。 この例では、バイトの値とキャッシュ ラインの間に 1 対 1 の関係があるため、これにより、攻撃者が範囲外に読み取られたバイトの実際の値を推測します。

上記の手順では、悪用 CVE 2017-5753 に対するのインスタンスと組み合わせてフラッシュ + 再読み込みと呼ばれる手法を使用する例を提供します。

## <a name="what-software-scenarios-can-be-impacted"></a>どのようなソフトウェアのシナリオの影響を受けることができますか。

ようなプロセスを使用してセキュリティで保護されたソフトウェアの開発、 [Security Development Lifecycle](https://www.microsoft.com/sdl/) (SDL) には、通常、アプリケーション内に存在する信頼の境界を識別するために開発者が必要です。 信頼境界は、アプリケーションがシステム上の別のプロセスまたはカーネル モード デバイス ドライバーの場合、管理者以外のユーザー モード プロセスなど、信頼度の低いコンテキストによって提供されるデータを対話の場所に存在します。 予測実行のサイド チャネルに関連する脆弱性の新しいクラスでは、コードと、デバイス上のデータを分離する既存のソフトウェア セキュリティ モデル内の信頼境界の多くに関連します。

次の表では、開発者が発生しているこれらの脆弱性について心配する必要があります、ソフトウェアのセキュリティ モデルの概要を示します。

|信頼の境界|説明|
|----------------|----------------|
|仮想マシンの境界|危険にさらされて別の仮想マシンから信頼されていないデータを受け取る別の仮想マシンのワークロードを分離するアプリケーションがあります。|
|カーネルの境界|管理者以外のユーザー モード プロセスから信頼されていないデータを受信するカーネル モード デバイス ドライバーは、危険にさらさ可能性があります。|
|プロセスの境界|を通じて、リモート プロシージャ コール (RPC)、共有メモリ、またはその他のプロセス間通信 (IPC) メカニズムが危険にさらされる可能性がありますなど、ローカルのシステムで実行されている別のプロセスから信頼されていないデータを受信するアプリケーション。|
|エンクレーブの境界|危険にさらされてから、エンクレーブの外部の信頼されていないデータを受信する (Intel SGX) などのセキュリティで保護されたエンクレーブ内で実行されるアプリケーションがあります。|
|言語境界|アプリケーションを解釈または Just-In-Time (JIT) コンパイルしてで記述された、信頼されていないコードを実行しますより高度な言語が危険にさらされる可能性があります。|

攻撃対象領域の公開、上記のいずれかの信頼境界は攻撃対象領域を特定し、可能なインスタンスの予測実行のサイド チャネルの脆弱性を軽減するためのコードを確認する必要がありますのあるアプリケーション。 予測実行のサイド チャネルの脆弱性を危険にさらされるをリモートのネットワーク プロトコルなどのリモートの攻撃対象領域に公開されている信頼の境界が示されたしないことに注意する必要があります。

## <a name="potentially-vulnerable-coding-patterns"></a>可能性のある脆弱性のあるコーディング パターン

予測実行のサイド チャネルの脆弱性は、複数のコーディング パターンの結果として発生します。 このセクションの可能性のある脆弱性のあるコーディング パターンについて説明し、それぞれの例を示しますが、これらのテーマのバリエーションが存在することが認識される必要があります。 そのため、開発者はすべての可能性のある脆弱性のあるコーディング パターンの排他的リストではなく、例として、これらのパターンをお勧めします。 今すぐソフトウェアに存在可能なメモリの安全性の脆弱性のと同じクラスは、予測に沿ったもあり、バッファー オーバーランなど、実行の順序のパスが境界外アクセス、初期化されていないメモリの使用、型を配列混乱では、という具合です。 アーキテクチャのパスに沿ったメモリの安全性の脆弱性を悪用する攻撃者が使用できる同じプリミティブは可能性があります投機的なパスにも適用されます。

一般に、予測実行のサイド チャネルに関連する条件付き分岐 misprediction が条件式は、制御または信頼性の低いコンテキストによって影響を受けるデータに対して動作するときに発生します。 たとえば、これで使用される条件付きの式を含めることができます`if`、 `for`、 `while`、 `switch`、または 3 項ステートメントです。 これらのステートメントごとに、コンパイラは、CPU が実行時の分岐のターゲットを予測可能性がありますし、条件付き分岐を生成できます。

各例では、「推論バリア」という句でコメントが挿入を緩和するためのバリアを開発者が起こる可能性があります。 これについては、緩和策のセクションで詳しく説明します。

## <a name="speculative-out-of-bounds-load"></a>範囲外の予測を読み込む

このカテゴリのコーディング パターンは、範囲外の予測につながる条件分岐 misprediction メモリへのアクセス。

### <a name="array-out-of-bounds-load-feeding-a-load"></a>範囲外の配列は、負荷を供給することを読み込む

このコーディング パターンは、CVE 2017-5753 (境界チェックのバイパス) を最初に説明されている脆弱性のあるコーディング パターンです。 この記事の「バック グラウンドでは、このパターンの詳細について説明します。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        // SPECULATION BARRIER
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

同様に、その終了を超えるループと組み合わせて負荷が発生する境界外配列は、misprediction のために条件します。 この例で、条件付き分岐の実行に関連付けられた、`x < buffer_size`式が予測ミスの可能性があり、投機的の本体は実行、`for`ときにループ`x`がより大きいまたは等しい`buffer_size`、そのため、予測の結果として得られる境界外を読み込みます。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadBytes(unsigned char *buffer, unsigned int buffer_size) {
    for (unsigned int x = 0; x < buffer_size; x++) {
        // SPECULATION BARRIER
        unsigned char value = buffer[x];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="array-out-of-bounds-load-feeding-an-indirect-branch"></a>範囲外の配列が間接の分岐を供給を読み込む

このコーディング パターンは、大文字と小文字する条件付き分岐 misprediction 可能性があります、されるアドレスをターゲットに間接の分岐に生じる関数ポインターの配列へのアクセスが範囲外に読み取られた範囲外です。 次のスニペットでは、これを実証する例を示します。

もないときに、この例では、信頼されていないメッセージ id が提供されている、`untrusted_message_id`パラメーター。 場合`untrusted_message_id`がより小さい`MAX_MESSAGE_ID`には、関数ポインターの配列にインデックスを付けるし、分岐を使用し、対応するブランチ ターゲット。 このコードがアーキテクチャ上も安全ですでもある場合は、CPU では、条件付きのブランチ予測ミス、`DispatchTable`によってインデックスが作成される`untrusted_message_id`ときにその値より大きいまたは等しい`MAX_MESSAGE_ID`したがって市場をリードする、境界外アクセスします。 これは、結果、投機的に実行されるコードによって情報の漏えいを招く可能性がある配列の境界を超えて派生した分岐のターゲット アドレスからの予測実行します。

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    if (untrusted_message_id < MAX_MESSAGE_ID) {
        // SPECULATION BARRIER
        DispatchTable[untrusted_message_id](buffer, buffer_size);
    }
}
```

配列の範囲外の場合と負荷の供給するために別の負荷にこの条件が、misprediction によりその終了条件を超えるループと組み合わせても発生します。

### <a name="array-out-of-bounds-store-feeding-an-indirect-branch"></a>配列範囲外に保存、間接的なブランチを供給

可能性も前の例は、間接的な分岐のターゲットに影響を与える負荷を投機的な境界外の方法で、中に、関数ポインターまたは戻り値のアドレスなど、間接的なブランチ ターゲットを変更する境界外に格納します。 これは、可能性がある可能性があります予測実行を攻撃者が指定したアドレスから。

この例では、信頼されていないインデックスは渡さ、`untrusted_index`パラメーター。 場合`untrusted_index`がの要素の数より小さい、`pointers`配列 (256 要素) 後で指定されたポインター値`ptr`に書き込まれる、`pointers`配列。 このコードがアーキテクチャ上も安全ですでもある場合は、CPU では、条件付きのブランチ予測ミス、`ptr`スタック割り当ての境界を超えて書き込む投機的`pointers`配列。 戻り値のアドレスの予測が破損する可能性が`WriteSlot`します。 場合は、攻撃者がの値を制御できます`ptr`、任意の予測が実行できる場合がある場合の対処`WriteSlot`投機的なパスを返します。

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
}
```

同様に場合という名前の関数ポインター ローカル変数`func`投機的アドレスを変更することができますし、スタックに割り当てられたを`func`条件分岐 misprediction が発生したときを参照します。 これには、関数ポインターがを通じて呼び出されたとき任意のアドレスからの予測の実行になる可能性があります。

```cpp
unsigned char WriteSlot(unsigned int untrusted_index, void *ptr) {
    void *pointers[256];
    void (*func)() = &callback;
    if (untrusted_index < 256) {
        // SPECULATION BARRIER
        pointers[untrusted_index] = ptr;
    }
    func();
}
```

これらの例の両方に間接的なブランチのスタックに割り当てられたポインターを投機的な変更が含まれることに注意する必要があります。 グローバル変数、ヒープに割り当てられたメモリ、およびいくつかの Cpu での読み取り専用メモリが偶数の可能性もあります投機的な変更することができます。 スタックに割り当てられたメモリを Microsoft のC++コンパイラは投機的などバッファー セキュリティに隣接して配置されるように、ローカル変数を並べ替えることで、間接的なブランチのスタック割り当てのターゲットを変更することがより困難にする手順を既に取得cookie の一部として、 [/GS](https://docs.microsoft.com/cpp/build/reference/gs-buffer-security-check)コンパイラ セキュリティの機能です。

## <a name="speculative-type-confusion"></a>混乱の予測の種類

このカテゴリは、コーディングを投機的な種類の混乱を上昇を可能にするパターンを処理します。 これは、アーキテクチャではないパスの型が正しくないを使用して、予測の実行中にメモリにアクセスするときに発生します。 条件付き分岐 misprediction と投機的なストア バイパスの両方を招く予測型の混乱を。

投機的なストアのバイパスをコンパイラが複数の種類の変数のスタックの場所を再利用のシナリオでこれが発生する可能性があります。 ため、これは、アーキテクチャのストア型の変数の`A`バイパス可能性がありますので、型のロード`A`投機的変数が割り当てられる前に実行します。 以前に格納された変数が異なる型の場合は、予測の種類の混乱の条件を作成これできます。

条件付き分岐の misprediction を記述する次のコード スニペットが使用されますを投機的な型の混乱を与えることができるさまざまな条件が増加します。

```cpp
enum TypeName {
    Type1,
    Type2
};

class CBaseType {
public:
    CBaseType(TypeName type) : type(type) {}
    TypeName type;
};

class CType1 : public CBaseType {
public:
    CType1() : CBaseType(Type1) {}
    char field1[256];
    unsigned char field2;
};

class CType2 : public CBaseType {
public:
    CType2() : CBaseType(Type2) {}
    void (*dispatch_routine)();
    unsigned char field2;
};

// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ProcessType(CBaseType *obj)
{
    if (obj->type == Type1) {
        // SPECULATION BARRIER
        CType1 *obj1 = static_cast<CType1 *>(obj);

        unsigned char value = obj1->field2;

        return shared_buffer[value * 4096];
    }
    else if (obj->type == Type2) {
        // SPECULATION BARRIER
        CType2 *obj2 = static_cast<CType2 *>(obj);

        obj2->dispatch_routine();

        return obj2->field2;
    }
}
```

### <a name="speculative-type-confusion-leading-to-an-out-of-bounds-load"></a>予測の種類の混乱につながる、範囲外の読み込み

このコーディング パターンが予測の種類の混乱がされることがケースでは、範囲外または型混乱フィールドへのアクセスが読み込まれた値が後続の読み込みアドレスをフィードします。 配列の範囲外のコーディング パターンに似ていますが、代わりに上記のように、シーケンスをコーディングで、示されています。 攻撃のコンテキストには、この例では、対象のコンテキストを実行する可能性があります`ProcessType`型のオブジェクトで複数回`CType1`(`type`フィールドと等しい`Type1`)。 最初の条件付き分岐のトレーニングの効果があります`if`ステートメントを作成した予測できません。 攻撃のコンテキストとの対象コンテキストを実行することができます、`ProcessType`型のオブジェクトで`CType2`します。 これにより、予測の種類の混乱の場合は、条件式は、最初の分岐`if`ステートメントを選択し、予測ミスの本文を実行、`if`ステートメントでは、そのため型のオブジェクトをキャスト`CType2`に`CType1`します。 `CType2`よりも小さい`CType1`へのメモリ アクセス`CType1::field2`結果、予測の境界外が読み込まれますシークレット可能性のあるデータの。 この値がからの読み込みで使用し、`shared_buffer`配列と同様、監視可能な副作用を作成する境界外の例は前に説明しました。

### <a name="speculative-type-confusion-leading-to-an-indirect-branch"></a>予測型の混乱が間接の分岐につながる

このコーディング パターンには、予測型混乱により、unsafe の間接的なブランチ予測の実行中に大文字と小文字が含まれます。 攻撃のコンテキストには、この例では、対象のコンテキストを実行する可能性があります`ProcessType`型のオブジェクトで複数回`CType2`(`type`フィールドと等しい`Type2`)。 最初の条件付き分岐のトレーニングの効果があります`if`ステートメントを実行して、`else if`ステートメントを実行できません。 攻撃のコンテキストとの対象コンテキストを実行することができます、`ProcessType`型のオブジェクトで`CType1`します。 これにより、予測の種類の混乱の場合は、条件式は、最初の分岐`if`ステートメントの予測実行と`else if`ステートメントを実行しない、予測の本体を実行するため、 `else if` 型のオブジェクトをキャストと`CType1`に`CType2`します。 以降、`CType2::dispatch_routine`フィールドと重複しています、`char`配列`CType1::field1`、意図しない分岐のターゲットに投機的な間接的なブランチをこの可能性があります。 攻撃のコンテキスト内のバイト値を制御できるかどうか、`CType1::field1`配列がありますブランチ ターゲット アドレスを制御します。

## <a name="speculative-uninitialized-use"></a>予測の初期化されていない使用

このカテゴリ コーディング パターンにはでは、可能性があります予測実行の初期化されていないメモリ アクセス置かれ後続のロードまたは間接のブランチのフィードを使用して、シナリオが含まれます。 攻撃されるこれらのコーディング パターン、攻撃者を制御または明確にで使用されるコンテキストによって初期化されずに使用されるメモリの内容が影響を与えることができる必要があります。

### <a name="speculative-uninitialized-use-leading-to-an-out-of-bounds-load"></a>予測の初期化されていない使用につながる、範囲外の読み込み

投機的な初期化されていない使用は、する可能性がある可能性を攻撃者が制御値を使用して境界外ロードします。 値以下の例で`index`が割り当てられている`trusted_index`のアーキテクチャのすべてのパスと`trusted_index`を以下にすると見なされます`buffer_size`します。 ただし、コンパイラによって生成されたコードによっては投機的なストア バイパスではからの負荷を発生する可能性があります`buffer[index]`と事前に割り当てを実行する依存式`index`します。 このような場合に初期化されていない値を`index`位置をオフセットとして使用される`buffer`範囲外の機密情報を読み取るし、の依存負荷による側チャネルでこれを伝えるために、攻撃者を有効にするでした`shared_buffer`.

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

void InitializeIndex(unsigned int trusted_index, unsigned int *index) {
    *index = trusted_index;
}

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int trusted_index) {
    unsigned int index;

    InitializeIndex(trusted_index, &index); // not inlined

    // SPECULATION BARRIER
    unsigned char value = buffer[index];
    return shared_buffer[value * 4096];
}
```

### <a name="speculative-uninitialized-use-leading-to-an-indirect-branch"></a>間接の分岐につながる、投機的な初期化されていない使用

投機的な初期化されていない使用は可能性のある、分岐のターゲットが攻撃者によって制御されている間接の分岐につながります。 次の例で`routine`いずれかに割り当てられている`DefaultMessageRoutine1`または`DefaultMessageRoutine`の値に応じて`mode`します。 アーキテクチャのパスにその結果が`routine`間接ブランチより常に初期化されます。 ただし、コンパイラによって生成されたコードによって投機的なストアのバイパスが発生するを通じて間接的なブランチを許可する`routine`への割り当てを事前に実行される投機的`routine`します。 このような場合、攻撃者があります投機的に、任意のアドレスから実行できるように、攻撃者が影響を与えるまたはコントロールの初期化されていない値を想定`routine`します。

```cpp
#define MAX_MESSAGE_ID 16

typedef void (*MESSAGE_ROUTINE)(unsigned char *buffer, unsigned int buffer_size);

const MESSAGE_ROUTINE DispatchTable[MAX_MESSAGE_ID];
extern unsigned int mode;

void InitializeRoutine(MESSAGE_ROUTINE *routine) {
    if (mode == 1) {
        *routine = &DefaultMessageRoutine1;
    }
    else {
        *routine = &DefaultMessageRoutine;
    }
}

void DispatchMessage(unsigned int untrusted_message_id, unsigned char *buffer, unsigned int buffer_size) {
    MESSAGE_ROUTINE routine;

    InitializeRoutine(&routine); // not inlined

    // SPECULATION BARRIER
    routine(buffer, buffer_size);
}
```

## <a name="mitigation-options"></a>軽減策の選択肢

ソース コードを変更することは、予測実行のサイド チャネルの脆弱性を軽減できます。 追加することで、脆弱性の特定のインスタンスなど、問題を緩和するこれらの変更が伴うことができます、*推論バリア*、または機密情報がアクセスできないように予測へのアプリケーションのデザインを変更すること実行します。

### <a name="speculation-barrier-via-manual-instrumentation"></a>手動によるインストルメンテーションを使用して、推論バリア

A*推論バリア*アーキテクチャではないパスに沿って進むから予測の実行を防ぐために、開発者によって手動で挿入することができます。 いずれか (条件付き分岐) の後のブロックの先頭で、条件付きブロックの本体で、開発者が危険なコーディング パターンの前に推論バリアを挿入するなど、または問題では、最初の読み込み前にします。 これにより、危険なコードを非アーキテクチャのパスの実行をシリアル化して実行を条件付き分岐 misprediction ができなくなります。 憶測バリアのシーケンスは、次の表で説明されているようハードウェア アーキテクチャによって異なります。

|アーキテクチャ|CVE 2017-5753 に対する組み込み推論バリア|推論バリア CVE-2018-3639 の組み込み|
|----------------|----------------|----------------|
|x86 または x64|_mm_lfence()|_mm_lfence()|
|ARM|現在使用できません|__dsb(0)|
|ARM64|現在使用できません|__dsb(0)|

使用して、次のコード パターンを軽減するなど、`_mm_lfence`次に示す組み込み。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        _mm_lfence();
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="speculation-barrier-via-compiler-time-instrumentation"></a>コンパイラにインストルメンテーションを使用して、推論バリア

Microsoft C++ (バージョン 15.5.5 以降)、Visual Studio 2017 でのコンパイラにはサポートが含まれています、`/Qspectre`限られた可能性がある脆弱性のあるコーディング パターン推論バリアを自動的に挿入するスイッチに関連するにはCVE-2017-5753 します。 ドキュメント、 [/Qspectre](https://docs.microsoft.com/cpp/build/reference/qspectre)フラグの効果と使用状況の詳細を提供します。 このフラグが可能性のある脆弱性のあるコーディング パターンのすべてに対応することはできませんとよう開発者に依存しないでください、このクラスの脆弱性を包括的な緩和するために重要です。

### <a name="masking-array-indices"></a>配列のインデックスのマスク

場所を投機的な境界外を読み込む場合に発生し、配列インデックス厳密に制限できますアーキテクチャと非アーキテクチャの両方のパスの配列インデックスを明示的にバインドするためのロジックを追加することで。 たとえば場合は、配列は、2 の累乗に揃えされたサイズに割り当てられることができます、し、単純なマスクを導入できます。 ここにその仮定の下のサンプルに示す`buffer_size`は 2 の累乗に配置されます。 これにより`untrusted_index`は常により小さい`buffer_size`条件分岐 misprediction が発生した場合でも、および`untrusted_index`より大きいまたは等しいを値と共に渡された`buffer_size`。

ここで実行されるインデックスのマスクでした、コンパイラによって生成されるコードに応じて投機的なストアのバイパスを受けることに注意してください。

```cpp
// A pointer to a shared memory region of size 1MB (256 * 4096)
unsigned char *shared_buffer;

unsigned char ReadByte(unsigned char *buffer, unsigned int buffer_size, unsigned int untrusted_index) {
    if (untrusted_index < buffer_size) {
        untrusted_index &= (buffer_size - 1);
        unsigned char value = buffer[untrusted_index];
        return shared_buffer[value * 4096];
    }
}
```

### <a name="removing-sensitive-information-from-memory"></a>機密情報をメモリから削除します。

予測実行のサイド チャネルの脆弱性を軽減するために使用できる別の手法では、メモリから機密情報を削除します。 ソフトウェア開発者は、予測の実行中に機密情報にアクセスできないように、アプリケーションをリファクタリングする機会を確認できます。 これは、個別のプロセスに機密情報を分離するアプリケーションの設計をリファクタリングすることにより実現できます。 たとえば、web ブラウザー アプリケーションは、web オリジンごとに、1 つのプロセスが予測実行でクロス オリジンのデータにアクセスできるように、個別のプロセスに関連付けられたデータの分離を試行できます。

## <a name="see-also"></a>関連項目

[予測実行のサイド チャネルの脆弱性を軽減するためのガイダンス](https://portal.msrc.microsoft.com/security-guidance/advisory/ADV180002)<br/>
[予測実行のサイド チャネル ハードウェア脆弱性を軽減します。](https://blogs.technet.microsoft.com/srd/2018/03/15/mitigating-speculative-execution-side-channel-hardware-vulnerabilities/)
