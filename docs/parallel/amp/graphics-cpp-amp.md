---
title: グラフィックス (C++ AMP)
ms.date: 11/04/2016
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
ms.openlocfilehash: 6e21c5af094ce90c8e4365ed4263198422ad1905
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449869"
---
# <a name="graphics-c-amp"></a>グラフィックス (C++ AMP)

C++ AMP にはでいくつかの Api が含まれています、 [concurrency::graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) Gpu のテクスチャのサポートへのアクセスに使用できる名前空間。 一般的なシナリオを次に示します。

- 使用することができます、[テクスチャ](../../parallel/amp/reference/texture-class.md)計算とエクスプロイトのデータ コンテナーとしてのクラス、*空間的局所性*のテクスチャ キャッシュと GPU ハードウェアのレイアウト。 空間的局所性は相互に物理的に近い場所に存在するデータ要素のプロパティです。

- ランタイムには、非計算シェーダーとの効率的な相互運用性が提供されます。 ピクセル、頂点、テセレーション、およびハルの各シェーダーは、C++ AMP 計算で使用できるテクスチャを頻繁に使用または生成します。

- C++ AMP のグラフィックス API には、サブワードがパックされたバッファーにアクセスするための別の方法が用意されています。 持つテクスチャ形式を表す*テクセル*(テクスチャ要素) を 8 ビットで構成、または 16 ビットのスカラーがこのようなパックされたデータ ストレージへのアクセスを許可します。

## <a name="the-norm-and-unorm-types"></a>norm 型および unorm 型

`norm`と`unorm`型は、スカラー型の範囲を制限する**float** ; の値と呼ばれます*クランプ*します。 これらの型は他のスカラー型から明示的に作成することができます。 キャストで、値が最初にキャスト**float**とし、norm [-1.0, 1.0] または unorm [0.0, 1.0] で許可されているそれぞれの領域にクランプします。 +/- 無限値からのキャストは +/-1 を返します。 NaN からキャストは未定義です。 norm は unorm から暗黙的に作成することができ、データは失われません。 float への暗黙の変換演算子がこれらの型に定義されます。 二項演算子がなどのこれらの型と他の組み込みスカラー型の間で定義された**float**と**int**: +、-、 \*、/、= =、! =、>、 \<、> =、< = です。 サポートされている複合代入演算子: + =、-=、 \*=、/、=。 単項否定演算子 (-) は、norm 型に定義されます。

## <a name="short-vector-library"></a>short ベクター ライブラリ

Short ベクター ライブラリは、いくつかの機能の[ベクター型](https://go.microsoft.com/fwlink/p/?linkid=248500)は HLSL で定義され、テクセルの定義に通常使用します。 short ベクターは同じ型の 1 ～ 4 つの値を保持するデータ構造体です。 サポートされる種類は**double**、 **float**、 **int**、 `norm`、 `uint`、および`unorm`します。 次の表に型名を示します。 種類ごとにある対応も**typedef**名にアンダー スコアが含まれない。 アンダー スコアを含む型が、 [concurrency::graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md)します。 アンダー スコアがない型が、 [Concurrency::graphics::direct3d Namespace](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md)が明確に区別同様にという名前の基本型からなどように **_ _int8**と **_ _int16**します。

||長さ 2|長さが 3|長さ 4|
|-|--------------|--------------|--------------|
|二重線|double_2<br /><br /> double2|double_3<br /><br /> double3|double_4<br /><br /> double4|
|フローティング|float_2<br /><br /> float2|float_3<br /><br /> float3|float_4<br /><br /> float4|
|int|int_2<br /><br /> int2|int_3<br /><br /> int3|int_4<br /><br /> int4|
|norm|norm_2<br /><br /> norm2|norm_3<br /><br /> norm3|norm_4<br /><br /> norm4|
|uint|uint_2<br /><br /> uint2|uint_3<br /><br /> uint3|uint_4<br /><br /> uint4|
|unorm|unorm_2<br /><br /> unorm2|unorm_3<br /><br /> unorm3|unorm_4<br /><br /> unorm4|

### <a name="operators"></a>演算子

演算子が 2 つの short ベクターの間で定義されている場合、その演算子は short ベクターとスカラーの間でも定義されます。 また、これらのどちらかが TRUE である必要があります。

- スカラーの型は short ベクターの要素型と同じである必要があります。

- スカラーの型は、1 つのユーザー定義の変換のみを使用してベクターの要素型に暗黙的に変換できます。

操作は short ベクターの各コンポーネントとスカラーの間でコンポーネントごとに実行されます。 次に有効な演算子を示します。

|演算子の型|有効な型|
|-------------------|-----------------|
|バイナリ演算子|すべての型で有効: +、-、 \*、/、<br /><br /> 整数型で有効: %、^、 &#124;、&、<\<、>><br /><br /> 2 つのベクターは同じサイズである必要があり、結果は同じサイズの 1 つのベクターになる。|
|関係演算子|すべての型で有効: ==、!=|
|複合代入演算子|すべての型で有効: + =、-=、 \*=、/、=<br /><br /> 整数型で有効: % =、^ =、 &#124;=、& =、<\<=、>> =|
|インクリメント演算子およびデクリメント演算子|すべての型で有効: ++、--<br /><br /> 前置と後置の両方が有効。|
|ビットごとの NOT 演算子 (~)|整数型で有効。|
|単項 - 演算子|`unorm` と `uint` を除くすべての型で有効。|

### <a name="swizzling-expressions"></a>スウィズリング式

short ベクター ライブラリは、short ベクターのコンポーネントにアクセスする `vector_type.identifier` アクセサー構成体をサポートします。 `identifier`と呼ばれ、*スウィズ リング式*ベクターのコンポーネントを指定します。 式は左辺値または右辺値のいずれかになります。 識別子の個々 の文字があります。 x、y、z、および w です。または r、g、b とします。 "x"と"r"、ゼロ番目のコンポーネント、"y"と"g"は 1 のコンポーネントとのことを意味します。 ("x" と "r" は同じ識別子で使用できないことに注意してください。)したがって、"rgba" と "xyzw" は同じ結果を返します。 "x" と "y" のような単一コンポーネント アクセサーはスカラー値型です。 複数コンポーネント アクセサーは short ベクター型です。 たとえば、`int_4` という名前で、値 2、4、6、8 を持つ `fourInts` ベクターを作成すると、`fourInts.y` は整数 4 を返し、`fourInts.rg` は値 2 および 4 を持つ `int_2` オブジェクトを返します。

## <a name="texture-classes"></a>テクスチャのクラス

多くの GPU には、ピクセルとテクセルをフェッチし、イメージとテクスチャを表示するために最適化されたハードウェアとキャッシュがあります。 [テクスチャ\<T, N >](../../parallel/amp/reference/texture-class.md)テクセル オブジェクトのコンテナー クラスである、クラスは、これらの Gpu のテクスチャ機能を公開します。 テクセルは次のようになります。

- **Int**、 `uint`、 **float**、**double**、 `norm`、または`unorm`スカラー。

- 2 つまたは 4 つのコンポーネントを持つ short ベクター。 許可されない唯一の例外は `double_4` です。

`texture` オブジェクトは、1、2、または 3 のランクになります。 `texture` オブジェクトは `parallel_for_each` の呼び出しのラムダの参照によってのみキャプチャできます。 テクスチャは、Direct3D テクスチャ オブジェクトとして GPU に格納されます。 テクスチャおよびテクセル Direct3D の詳細については、次を参照してください。 [direct3d11 のテクスチャの概要](https://go.microsoft.com/fwlink/p/?linkid=248502)します。

使用するテクセル型が、グラフィックス プログラミングで使用される多くのテクスチャ形式の 1 つになっている場合があります。 たとえば、RGBA 形式は、R、G、B、A のスカラー要素に対してそれぞれ 8 ビットで、32 ビットを使用できます。 グラフィックス カードのテクスチャ ハードウェアは、形式に基づいて個々の要素にアクセスできます。 たとえば、RGBA 形式を使用すると、テクスチャ ハードウェアは各 8 ビット要素を 32 ビット形式に復元できます。 C++ AMP では、ビット シフトを使用しないでコードの個々のスカラー要素に自動的にアクセスできるように、テクセルのスカラー要素ごとにビットを設定できます。

### <a name="instantiating-texture-objects"></a>テクスチャ オブジェクトのインスタンス化

初期化せずにテクスチャ オブジェクトを宣言することができます。 次のコード例では、複数のテクスチャ オブジェクトを宣言しています。

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextures() {
    // Create a 16-texel texture of int.
    texture<int, 1> intTexture1(16);
    texture<int, 1> intTexture2(extent<1>(16));

    // Create a 16 x 32 texture of float_2.
    texture<float_2, 2> floatTexture1(16, 32);
    texture<float_2, 2> floatTexture2(extent<2>(16, 32));

    // Create a 2 x 4 x 8 texture of uint_4.
    texture<uint_4, 3> uintTexture1(2, 4, 8);
    texture<uint_4, 3> uintTexture2(extent<3>(2, 4, 8));
}
```

また、`texture` オブジェクトを宣言および初期化するにはコンストラクターを使用することもできます。 次のコード例では、`texture` オブジェクトのベクターから `float_4` オブジェクトをインスタンス化しています。 スカラー要素ごとのビットは既定値に設定されます。 スカラー要素ごとの既定のビットがないため、`norm`、`unorm`、`norm`、および `unorm` の short ベクターを持つコンストラクターを使用することはできません。

```cpp
#include <amp.h>
#include <amp_graphics.h>
#include <vector>
using namespace concurrency;
using namespace concurrency::graphics;

void initializeTexture() {
    std::vector<int_4> texels;
    for (int i = 0; i < 768 * 1024; i++) {
        int_4 i4(i, i, i, i);
        texels.push_back(i4);
    }

    texture<int_4, 2> aTexture(768, 1024, texels.begin(), texels.end());
}
```

また、ソース データ、バイト単位のソース データのサイズ、およびスカラー要素ごとのビットへのポインターを受け取るコンストラクター オーバーロードを使用して `texture` オブジェクトを宣言および初期化することもできます。

```cpp
void createTextureWithBPC() { // Create the source data.
    float source[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        source[i] = (float)i;
    }
    // Initialize the texture by using the size of source in bytes // and bits per scalar element.
    texture<float_2, 1> floatTexture(1024, source, (unsigned int)sizeof(source), 32U);
}
```

これらの例のテクスチャは、既定のアクセラレータの既定のビューに作成されます。 `accelerator_view` オブジェクトを指定するには、コンストラクターの他のオーバーロードを使用できます。 CPU アクセラレータにテクスチャ オブジェクトを作成することはできません。

次の表に示すように、`texture` オブジェクトの各次元のサイズには制限があります。 制限を超えるとランタイム エラーが生成されます。

|テクスチャ|各次元のサイズの制限|
|-------------|---------------------|
|テクスチャ\<T 1 >|16384|
|テクスチャ\<2、T >|16384|
|テクスチャ\<T、3 >|2048|

### <a name="reading-from-texture-objects"></a>テクスチャ オブジェクトからの読み取り

読み取ることができます、`texture`オブジェクトを使用して[texture:\[\]](reference/texture-class.md#operator_at)、 [texture::operator() 演算子](reference/texture-class.md#operator_call)、または[texture::get メソッド](reference/texture-class.md#get). 2 つの演算子は、参照ではなく、値を返します。 したがって、`texture` を使用して `texture::operator\[\]` オブジェクトに書き込むことはできません。

```cpp
void readTexture() {
    std::vector<int_2> src;
    for (int i = 0; i <16 *32; i++) {
        int_2 i2(i, i);

        src.push_back(i2);
    }

    std::vector<int_2> dst(16* 32);

    array_view<int_2, 2> arr(16, 32, dst);

    arr.discard_data();

    const texture<int_2, 2> tex9(16, 32, src.begin(), src.end());

    parallel_for_each(tex9.extent, [=, &tex9] (index<2> idx) restrict(amp) { // Use the subscript operator.
        arr[idx].x += tex9[idx].x; // Use the function () operator.
        arr[idx].x += tex9(idx).x; // Use the get method.
        arr[idx].y += tex9.get(idx).y; // Use the function () operator.
        arr[idx].y += tex9(idx[0], idx[1]).y;
    });

    arr.synchronize();
}
```

次のコード例では、short ベクターにテクスチャ チャネルを格納し、short ベクターのプロパティとして個々のスカラー要素にアクセスする方法を説明します。

```cpp
void UseBitsPerScalarElement() { // Create the image data. // Each unsigned int (32-bit) represents four 8-bit scalar elements(r,g,b,a values).
    const int image_height = 16;
    const int image_width = 16;
    std::vector<unsigned int> image(image_height* image_width);

    extent<2> image_extent(image_height, image_width);

    // By using uint_4 and 8 bits per channel, each 8-bit channel in the data source is // stored in one 32-bit component of a uint_4.
    texture<uint_4, 2> image_texture(image_extent, image.data(), image_extent.size()* 4U,  8U);

    // Use can access the RGBA values of the source data by using swizzling expressions of the uint_4.
    parallel_for_each(image_extent,
        [&image_texture](index<2> idx) restrict(amp)
        { // 4 bytes are automatically extracted when reading.
            uint_4 color = image_texture[idx];
            unsigned int r = color.r;
            unsigned int g = color.g;
            unsigned int b = color.b;
            unsigned int a = color.a;
        });
}
```

次の表は、各 short ベクター型のチャネルごとの有効なビットを示します。

|テクスチャ データ型|スカラー要素ごとの有効なビット|
|-----------------------|-----------------------------------|
|int、int_2、int_4<br /><br /> uint、uint_2、uint_4|8, 16, 32|
|int_3、uint_3|32|
|float、float_2、float_4|16, 32|
|float_3|32|
|double、double_2|64|
|norm、norm_2、norm_4<br /><br /> unorm、unorm_2、unorm_4|8, 16|

### <a name="writing-to-texture-objects"></a>テクスチャ オブジェクトへの書き込み

使用して、 [texture::set](reference/texture-class.md#set)メソッドへの書き込みを`texture`オブジェクト。 テクスチャ オブジェクトは読み取り専用または読み取り/書き込み可能にすることができます。 読み取り/書き込み可能なテクスチャ オブジェクトについては、次の条件が満たされている必要があります。

- T にあるのは 1 つのスカラー コンポーネントのみです。 (short ベクターは使用できません。)

- T でない**double**、 `norm`、または`unorm`します。

- `texture::bits_per_scalar_element` プロパティは 32 です。

3 つすべてが満たされない場合、`texture` オブジェクトは読み取り専用です。 最初の 2 つの条件は、コンパイル中にチェックされます。 `readonly` テクスチャ オブジェクトに書き込もうとするコードがあると、コンパイル エラーが生成されます。 条件は、`texture::bits_per_scalar_element`が、実行時に検出されると、ランタイムによって生成、 [unsupported_feature](../../parallel/amp/reference/unsupported-feature-class.md) 、読み取り専用に書き込もうとする場合は例外`texture`オブジェクト。

次のコード例では、値をテクスチャ オブジェクトに書き込みます。

```cpp
void writeTexture() {
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {
        tex1.set(idx, 0);
    });
}
```

### <a name="copying-texture-objects"></a>テクスチャ オブジェクトをコピーする

使用してテクスチャ オブジェクト間でコピーすることができます、[コピー](reference/concurrency-namespace-functions-amp.md#copy)関数または[copy_async](reference/concurrency-namespace-functions-amp.md#copy_async)関数は、次のコード例に示すようにします。

```cpp
void copyHostArrayToTexture() { // Copy from source array to texture object by using the copy function.
    float floatSource[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        floatSource[i] = (float)i;
    }
    texture<float_2, 1> floatTexture(1024);

    copy(floatSource, (unsigned int)sizeof(floatSource), floatTexture);

    // Copy from source array to texture object by using the copy function.
    char charSource[16* 16];
    for (int i = 0; i <16* 16; i++) {
        charSource[i] = (char)i;
    }
    texture<int, 2> charTexture(16, 16, 8U);

    copy(charSource, (unsigned int)sizeof(charSource), charTexture);
    // Copy from texture object to source array by using the copy function.
    copy(charTexture, charSource, (unsigned int)sizeof(charSource));
}
```

コピーすることも 1 つのテクスチャから間を使用して、 [texture::copy_to](reference/texture-class.md#copy_to)メソッド。 2 つのテクスチャは異なる accelerator_views に置くことができます。 `writeonly_texture_view` オブジェクトにコピーすると、データは基になる `texture` オブジェクトにコピーされます。 スカラー要素ごとのビットおよび範囲はコピー元とコピー先の `texture` オブジェクトで同じにする必要があります。 これらの条件が満たされない場合、ランタイムは例外をスローします。

## <a name="texture-view-classes"></a>テクスチャ ビューのクラス

C++AMP が導入されています、 [texture_view クラス](../../parallel/amp/reference/texture-view-class.md)Visual Studio 2013 でします。 テクスチャ ビューは、同じテクセル型とランクとしてをサポート、 [texture クラス](../../parallel/amp/reference/texture-class.md)が、テクスチャとは異なり、テクスチャ サンプリングや mipmap などの追加のハードウェア機能へのアクセスを提供します。 テクスチャ ビューは基になるテクスチャ データへの読み取り専用、書き込み専用、読み取り/書き込みアクセスをサポートします。

- 読み取り専用アクセスは `texture_view<const T, N>` テンプレートの特殊化によって提供されます。これは 1、2、または 4 つのコンポーネント、テクスチャ サンプリング、およびビューをインスタンス化するときに決定される MIPMAP レベルの範囲への動的アクセスを持つ要素をサポートします。

- 書き込み専用アクセスは、特殊化されていないテンプレート クラス `texture_view<T, N>` によって提供されます。これは 2 つまたは 4 つのコンポーネントを持ち、ビューをインスタンス化するときに決定される 1 つの MIPMAP レベルにアクセスできる要素をサポートします。 サンプリングはサポートされません。

- 読み取り/書き込みアクセスは、特殊化されていないテンプレート クラス `texture_view<T, N>` によって提供されます。これはテクスチャのように、コンポーネントを 1 つだけ持つ要素をサポートし、ビューはインスタンス化されるときに決定される 1 つの MIPMAP レベルにアクセスできます。 サンプリングはサポートされません。

テクスチャ ビューは、配列のビューに似ていますは得られません。 データの自動管理および移動機能を、 [array_view クラス](../../parallel/amp/reference/array-view-class.md)比べ、 [array クラス](../../parallel/amp/reference/array-class.md)します。 `texture_view` は、基になるテクスチャ データが存在するアクセラレータ ビューにのみアクセスできます。

### <a name="writeonly_texture_view-deprecated"></a>使用されない writeonly_texture_view

Visual Studio 2013 でC++AMP サンプリングや mipmap でサポートされていませんでしたなどのハードウェア テクスチャ機能に対する優れたサポートが導入されています、 [writeonly_texture_view クラス](../../parallel/amp/reference/writeonly-texture-view-class.md)します。 最近導入された `texture_view` クラスは `writeonly_texture_view` の機能のスーパーセットをサポートしており、その結果、`writeonly_texture_view` は使用されません。

少なくとも新しいコードについては、以前は `texture_view` によって提供された機能へのアクセスに `writeonly_texture_view` を使用することをお勧めします。 2 つのコンポーネント (int_2) を持つテクスチャ オブジェクトに書き込む、次の 2 つのコード例を比較します。 どちらのケースでも、ビュー `wo_tv4` はラムダ式の値でキャプチャされる必要があることに注意してください。 新しい `texture_view` クラスを使用する例を次に示します。

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

使用されていない `writeonly_texture_view` クラスを次に示します。

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

おわかりのように、2 つのコード例は、プライマリ MIPMAP レベルに書き込んでいるだけである場合にはほぼ同じです。 既存のコードで `writeonly_texture_view` を使用し、そのコードを拡張するつもりがない限り、変更する必要はありません。 ただし、そのコードをさらに改善するつもりであるなら、その中で機能を強化すると新しいハードウェア テクスチャ機能をサポートできるため、`texture_view` を使用できるように書き直すことをお勧めします。 これらの新しい機能の詳細については、以下をお読みください。

廃止の詳細については`writeonly_texture_view`を参照してください[で C++ AMP テクスチャ ビュー デザインの概要](https://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/25/overview-of-the-texture-view-design-in-c-amp.aspx)ネイティブ コードのブログでの並列プログラミングします。

### <a name="instantiating-texture-view-objects"></a>テクスチャ ビュー オブジェクトのインスタンス化

宣言を`texture_view`宣言に似ています、`array_view`関連付けられている、**配列**します。 次のコード例では、複数の `texture` オブジェクトとそれらに関連付けられた `texture_view` オブジェクトを宣言しています。

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextureViews()
{
    // Create a 16-texel texture of int, with associated texture_views.
    texture<int, 1> intTexture(16);
    texture_view<const int, 1> intTextureViewRO(intTexture);  // read-only
    texture_view<int, 1> intTextureViewRW(intTexture);        // read-write

    // Create a 16 x 32 texture of float_2, with associated texture_views.
    texture<float_2, 2> floatTexture(16, 32);
    texture_view<const float_2, 2> floatTextureViewRO(floatTexture);  // read-only
    texture_view<float_2, 2> floatTextureViewRO(floatTexture);        // write-only

    // Create a 2 x 4 x 8 texture of uint_4, with associated texture_views.
    texture<uint_4, 3> uintTexture(2, 4, 8);
    texture_view<const uint_4, 3> uintTextureViewRO(uintTexture);  // read-only
    texture_view<uint_4, 3> uintTextureViewWO(uintTexture);        // write-only
}
```

要素型が非定数で 1 つのコンポーネントを持つテクスチャ ビューは読み取り/書き込みで、要素型は非定数であるが複数のコンポーネントを持つテクスチャ ビューは書き込み専用であることに注意してください。 定数要素型のテクスチャ ビューは常に読み取り専用ですが、要素型が非定数である場合は、要素内のコンポーネント数によって読み取り/書き込み可能 (1 コンポーネント) か書き込み専用 (複数のコンポーネント) かが決定されます。

`texture_view` の要素型 (定数であるかどうかとそのコンポーネントの数) も、ビューがテクスチャ サンプリングをサポートするかどうかおよび MIPMAP レベルへのアクセス方法の決定に役割を果たします。

|型|コンポーネント|読み取り|Write|サンプリング|MIPMAP アクセス|
|----------|----------------|----------|-----------|--------------|-------------------|
|texture_view\<const T, N >|1, 2, 4|[はい]|いいえ (1)|[はい]|○、インデックス可能。 範囲はインスタンス化時に決定。|
|Texture_view\<T, N >|1<br /><br /> 2, 4|[はい]<br /><br /> いいえ (2)|[はい]<br /><br /> [はい]|いいえ (1)<br /><br /> いいえ (1)|○、1 レベル。 レベルはインスタンス化時に決定。<br /><br /> ○、1 レベル。 レベルはインスタンス化時に決定。|

このテーブルから、読み取り専用のテクスチャ ビューはビューに書き込めない代わりに新しい機能を完全にサポートすることを確認できます。 書き込み可能なテクスチャ ビューは 1 つの MIPMAP レベルにのみアクセスできるように制限されています。 読み取り/書き込みテクスチャ ビューは書き込み可能なテクスチャ ビューよりもさらに特殊化されています。これはテクスチャ ビューの要素型が 1 つのコンポーネントのみを持っているという要件が追加されているためです。 これは読み取り指向の操作であるため、サンプリングは書き込み可能テクスチャ ビューではサポートされないことに注意してください。

### <a name="reading-from-texture-view-objects"></a>テクスチャ ビュー オブジェクトからの読み取り

テクスチャ ビューでのサンプル化されていないテクスチャ データの読み取りは、テクスチャ自体からのデータの読み取りと同じです。ただし、テクスチャ ビューは値によってキャプチャされますが、テクスチャは参照によってキャプチャされます。 次の 2 つのコード例では、まず、`texture` のみを使用する場合を示します。

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {
        tex_data.set(idx, int_2(1, 1));
    });
}
```

そして、`texture_view` クラスを使用する以外は同じである場合を示します。

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        tex_view.set(idx, int_2(1, 1));
    });
}
```

たとえば、float、float_2、または float_4 などの、浮動小数点型に基づく要素のテクスチャ ビューは、さまざまなフィルター処理モードおよびアドレッシング モードに対するハードウェア サポートを利用するにテクスチャ サンプリングを使用して読み取ることもできます。 C++ AMP は計算シナリオで最も一般的な 2 つのフィルター処理モード (ポイント フィルタリング (ニアレストネイバー) およびリニア フィルタリング (加重平均))、および 4 つのアドレッシング モード (wrapped、mirrored、clamped、border) をサポートしています。 アドレッシング モードの詳細については、次を参照してください。 [address_mode 列挙型](reference/concurrency-graphics-namespace-enums.md#address_mode)します。

C++ AMP が直接サポートするモードに加えて、プラットフォーム API を直接使用して作成されたテクスチャ サンプラーを採用する相互運用 API を使用して、基になるプラットフォームの他のフィルター処理モードとアドレッシング モードにアクセスすることができます。 たとえば、Direct3D は異方性フィルタリングなどの他のフィルター処理モードをサポートし、テクスチャの大きさごとに別のアドレッシング モードを適用できます。 座標が垂直方向にラップされ、水平方向にミラー化され、Direct3D API を使用した異方性フィルタリングでサンプル化されるテクスチャ サンプラーを作成し、`make_sampler` 相互運用 API を使用して C++ AMP コードでサンプラーを利用することができます。 詳細については、次を参照してください。[で C++ AMP テクスチャ サンプリング](https://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/18/texture-sampling-in-c-amp.aspx)ネイティブ コードのブログでの並列プログラミングします。

また、テクスチャ ビューは MIPMAP の読み取りをサポートします。 定数要素型である読み取り専用のテクスチャ ビューは最も高い柔軟性を備えています。これはインスタンス化で決定された MIPMAP レベルの範囲が動的にサンプル化され、1、2、または 4 つのコンポーネントを持つ要素がサポートされるためです。 また、1 つのコンポーネントを持つ要素がある読み取り/書き込みテクスチャ ビューも MIPMAP をサポートしますが、インスタンス化で決定されたレベルのみです。 詳細については、次を参照してください。 [Mipmap を使用してテクスチャ](https://blogs.msdn.com/b/nativeconcurrency/archive/2013/08/22/texture-with-mipmaps.aspx)ネイティブ コードのブログでの並列プログラミングします。

### <a name="writing-to-texture-view-objects"></a>テクスチャ ビュー オブジェクトへの書き込み

使用して、 [texture_view::get メソッド](reference/texture-view-class.md#get)には、基になる書き込めません`texture`を通じて、`texture_view`オブジェクト。 テクスチャ ビューは読み取り専用、読み取り/書き込み、または書き込み専用のいずれかです。 書き込み可能なテクスチャ ビューは非定数である要素型を持つ必要があり、読み取り/書き込み可能なテクスチャ ビューの要素型は、1 つのコンポーネントのみを持つ必要があります。 それ以外の場合、テクスチャ ビューは読み取り専用です。 テクスチャ ビューで一度にテクスチャの 1 つの MIPMAP レベルにのみアクセスでき、ビューがインスタンス化されるときにレベルが指定されます。

この例では、4 つの MIPMAP レベルを持つテクスチャの 2 番目に詳細な MIPMAP レベルに書き込む方法を示します。 最も詳細な MIPMAP レベルはレベル 0 です。

```cpp
// Create a texture that has 4 mipmap levels : 16x16, 8x8, 4x4, 2x2
texture<int, 2> tex(extent<2>(16, 16), 16U, 4);

// Create a writable texture view to the second mipmap level :4x4
texture_view<int, 2> w_view(tex, 1);

parallel_for_each(w_view.extent, [=](index<2> idx) restrict(amp)
{
    w_view.set(idx, 123);
});
```

## <a name="interoperability"></a>相互運用性

C++ AMP ランタイム間の相互運用をサポートしている`texture<T,1>`と[ID3D11Texture1D インターフェイス](https://go.microsoft.com/fwlink/p/?linkId=248503)間に、`texture<T,2>`と[ID3D11Texture2D インターフェイス](https://go.microsoft.com/fwlink/p/?linkId=255317)間および`texture<T,3>`と[ID3D11Texture3D インターフェイス](https://go.microsoft.com/fwlink/p/?linkId=255377)します。 [Get_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture)メソッドは、`texture`オブジェクトを返します、`IUnknown`インターフェイス。 [Make_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture)メソッドは、`IUnknown`インターフェイスと`accelerator_view`オブジェクトを返します、`texture`オブジェクト。

## <a name="see-also"></a>関連項目

[double_2 クラス](../../parallel/amp/reference/double-2-class.md)<br/>
[double_3 クラス](../../parallel/amp/reference/double-3-class.md)<br/>
[double_4 クラス](../../parallel/amp/reference/double-4-class.md)<br/>
[float_2 クラス](../../parallel/amp/reference/float-2-class.md)<br/>
[float_3 クラス](../../parallel/amp/reference/float-3-class.md)<br/>
[float_4 クラス](../../parallel/amp/reference/float-4-class.md)<br/>
[int_2 クラス](../../parallel/amp/reference/int-2-class.md)<br/>
[int_3 クラス](../../parallel/amp/reference/int-3-class.md)<br/>
[int_4 クラス](../../parallel/amp/reference/int-4-class.md)<br/>
[norm_2 クラス](../../parallel/amp/reference/norm-2-class.md)<br/>
[norm_3 クラス](../../parallel/amp/reference/norm-3-class.md)<br/>
[norm_4 クラス](../../parallel/amp/reference/norm-4-class.md)<br/>
[short_vector 構造体](../../parallel/amp/reference/short-vector-structure.md)<br/>
[short_vector_traits 構造体](../../parallel/amp/reference/short-vector-traits-structure.md)<br/>
[uint_2 クラス](../../parallel/amp/reference/uint-2-class.md)<br/>
[uint_3 クラス](../../parallel/amp/reference/uint-3-class.md)<br/>
[uint_4 クラス](../../parallel/amp/reference/uint-4-class.md)<br/>
[unorm_2 クラス](../../parallel/amp/reference/unorm-2-class.md)<br/>
[unorm_3 クラス](../../parallel/amp/reference/unorm-3-class.md)<br/>
[unorm_4 クラス](../../parallel/amp/reference/unorm-4-class.md)
