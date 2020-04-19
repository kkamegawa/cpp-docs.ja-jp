---
title: コンパイラ警告 (C4600 - C4799)
ms.date: 04/21/2019
f1_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
helpviewer_keywords:
- C4609
- C4658
- C4671
- C4676
- C4689
- C4695
- C4696
- C4719
- C4720
- C4721
- C4728"
- C4732
- C4751
- C4752
- C4755
- C4757
- C4767
- C4770
ms.assetid: 22bd4392-f3be-445c-9f23-6126aebac901
ms.openlocfilehash: 3df17b115797f4d68621854d072c41aca14a0fd8
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857565"
---
# <a name="compiler-warnings-c4600-through-c4799"></a>コンパイラ警告 (C4600 - C4799)

ドキュメントのこのセクションの記事では、コンパイラによって生成される警告メッセージのサブセットについて説明します。

[!INCLUDE[error-boilerplate](../../error-messages/includes/error-boilerplate.md)]

## <a name="warning-messages"></a>警告メッセージ

|警告|メッセージ|
|-------------|-------------|
|[コンパイラの警告 (レベル 1) C4600](../../error-messages/compiler-warnings/compiler-warning-level-1-c4600.md)|#pragma 'macro name': 無効な空でない文字列が必要です|
|[コンパイラの警告 (レベル 1) C4602](compiler-warning-level-1-c4602.md)|#pragma pop_macro: 'macro name' no previous #pragma push_macro for this identifier|
|[コンパイラの警告 (レベル 1) C4603](compiler-warning-level-1-c4603.md)|'*識別子*': マクロが定義されていないか、プリコンパイル済みヘッダーを使用している定義とは異なります|
|コンパイラの警告 (レベル 1) C4604|'*型*': ネイティブとマネージの境界を越えて引数を値渡しには、有効なコピー コンス トラクターが必要です。 それ以外の場合、実行時の動作は定義されていません|
|コンパイラの警告 (レベル 1) C4605|'/D*マクロ*' 現在のコマンドラインで指定しますが、プリコンパイル済みヘッダーを構築したときに指定されませんでした|
|[コンパイラの警告 (レベル 1) C4606](../../error-messages/compiler-warnings/compiler-warning-level-1-c4606.md)|#pragma 警告: '警告番号' を無視する場合コード分析の警告が警告レベルに関連付けられていません。|
|[コンパイラの警告 (レベル 3) C4608](../../error-messages/compiler-warnings/compiler-warning-level-3-c4608.md)|'union_member' は既に初期化子リスト 'union_member' 内の他の共用体メンバーにより初期化されています。|
|コンパイラの警告 (レベル 3 では、エラー) C4609|'*type1*'既定のインターフェイスから派生した'*インターフェイス*'type' で*type2*'。 別の既定のインターフェイスを使用して '*type1*'、または基本/派生リレーションシップを中断します。|
|[コンパイラの警告 (レベル 4) C4610](../../error-messages/compiler-warnings/compiler-warning-level-4-c4610.md)|'class' のオブジェクトをインスタンス化することはありません - ユーザーに必要なコンス トラクターが定義されています。|
|[コンパイラの警告 (レベル 4) C4611](../../error-messages/compiler-warnings/compiler-warning-level-4-c4611.md)|'function' と C++ オブジェクト デストラクション間の相互作用はポータブルでないです。|
|[コンパイラの警告 (レベル 1) C4612](compiler-warning-level-1-c4612.md)|インクルード ファイル名にエラーがあります|
|[コンパイラの警告 (レベル 1) C4613](compiler-warning-level-1-c4613.md)|'*シンボル*': セグメントのクラスを変更することはできません|
|[コンパイラの警告 (レベル 1) C4615](../../error-messages/compiler-warnings/compiler-warning-level-1-c4615.md)|#pragma warning: 不明な警告型|
|[コンパイラの警告 (レベル 1) C4616](../../error-messages/compiler-warnings/compiler-warning-level-1-c4616.md)|#pragma warning: 警告番号 'number' 有効なコンパイラ警告ではありません|
|[コンパイラの警告 (レベル 1) C4618](../../error-messages/compiler-warnings/compiler-warning-level-1-c4618.md)|プラグマのパラメーターに空の文字列。プラグマを無視|
|[コンパイラの警告 (レベル 3) C4619](../../error-messages/compiler-warnings/compiler-warning-level-3-c4619.md)|#pragma warning: 警告番号 'number' がありません。|
|[コンパイラの警告 (レベル 1) C4620](compiler-warning-level-1-c4620.md)|型 'type' に対して後置形式の 'operator ++' は見つかりません。前置形式を使用します|
|[コンパイラの警告 (レベル 1) C4621](../../error-messages/compiler-warnings/compiler-warning-level-1-c4621.md)|'operator--' の型 'type'、前置形式を使用していない後置形式|
|[コンパイラの警告 (レベル 3) C4622](compiler-warning-level-3-c4622.md)|オブジェクト ファイルでプリコンパイル済みヘッダーの作成中にデバッグ情報を上書きされました: 'file'|
|[コンパイラの警告 (レベル 4) C4623](../../error-messages/compiler-warnings/compiler-warning-level-4-c4623.md)|'derived class': 基底クラスの既定のコンス トラクターがアクセスできないか削除されたため、削除、既定のコンス トラクターが暗黙的に定義|
|[コンパイラの警告 (レベル 1) C4624](../../error-messages/compiler-warnings/compiler-warning-level-1-c4624.md)|'derived class': 基底クラスのデストラクターがアクセスできないか削除されたため、削除、デストラクターは暗黙的に定義|
|[コンパイラの警告 (レベル 4) C4625](../../error-messages/compiler-warnings/compiler-warning-level-4-c4625.md)|'derived class': 基底クラスのコピー コンス トラクターがアクセスできないか削除されたため、削除、コピー コンス トラクターが暗黙的に定義|
|[コンパイラの警告 (レベル 4) C4626](../../error-messages/compiler-warnings/compiler-warning-level-4-c4626.md)|'derived class': 基底クラスの代入演算子がアクセスできないか削除されたため、削除、代入演算子が暗黙的に定義|
|[コンパイラの警告 (レベル 1) C4627](../../error-messages/compiler-warnings/compiler-warning-level-1-c4627.md)|'\<識別子 >': プリコンパイル済みヘッダーの使用を検索するときにスキップ|
|[コンパイラの警告 (レベル 1) C4628](../../error-messages/compiler-warnings/compiler-warning-level-1-c4628.md)|digraphs は -Ze でサポートされていません。 文字のシーケンス 'digraph' は '%s' の代替トークンとして解釈されません。|
|[コンパイラの警告 (レベル 4) C4629](compiler-warning-level-4-c4629.md)|digraph が使用されました。文字のシーケンス 'digraph' はトークン 'char' として解釈されます。(これが意図でない場合は、2 文字の間にスペースを挿入してください)|
|[コンパイラの警告 (レベル 1) C4630](../../error-messages/compiler-warnings/compiler-warning-level-1-c4630.md)|'symbol': 'extern' storage-class specifier illegal on member definition|
|コンパイラの警告 (レベル 2) C4631|MSXML または XPath は使用できません。XML ドキュメント コメントは処理されません。 理由|
|[コンパイラの警告 (レベル 1) C4632](../../error-messages/compiler-warnings/compiler-warning-level-1-c4632.md)|XML ドキュメント コメント: ファイルのアクセスが拒否されました: 理由|
|[コンパイラの警告 (レベル 3) C4633](../../error-messages/compiler-warnings/compiler-warning-level-3-c4633.md)|XML ドキュメント コメント ターゲット: エラー: 理由|
|[コンパイラの警告 (レベル 4) C4634](compiler-warning-level-4-c4634.md)|XML ドキュメント コメント ターゲット: 適用できません: 理由|
|[コンパイラの警告 (レベル 3) C4635](compiler-warning-level-3-c4635.md)|XML ドキュメント コメント対象: XML の形式が正しくありません: 理由|
|[コンパイラの警告 (レベル 3) C4636](compiler-warning-level-3-c4636.md)|構築に適用される XML ドキュメント コメント: タグには、空でない 'attribute' 属性が必要です。|
|[コンパイラの警告 (レベル 3 および 4) C4637](compiler-warning-level-3-c4637.md)|XML ドキュメント コメント ターゲット:\<含める > タグは破棄されます。 理由|
|[コンパイラの警告 (レベル 3) C4638](compiler-warning-level-3-c4638.md)|XML ドキュメント コメント対象: 不明なシンボル 'symbol' への参照。|
|[コンパイラの警告 (レベル 4) C4639](../../error-messages/compiler-warnings/compiler-warning-level-4-c4639.md)|MSXML エラーの場合は、XML ドキュメント コメントは処理されません。 理由|
|[コンパイラの警告 (レベル 3) C4640](../../error-messages/compiler-warnings/compiler-warning-level-3-c4640.md)|'instance': ローカル スタティック オブジェクトの構築がスレッド セーフではありません。|
|[コンパイラの警告 (レベル 3) C4641](../../error-messages/compiler-warnings/compiler-warning-level-3-c4641.md)|XML ドキュメント コメントには、あいまいなの相互参照があります。|
|[コンパイラの警告 (レベル 3) C4645](compiler-warning-level-3-c4645.md)|__declspec(noreturn) で宣言された関数に return ステートメントがあります。|
|[コンパイラの警告 (レベル 3) C4646](compiler-warning-level-3-c4646.md)|__declspec(noreturn) で宣言された関数に、non-void 戻り値の型があります。|
|コンパイラの警告 (レベル 3) C4647|動作変更: _ _is_pod (*型*) 別の値が、以前のバージョン|
|コンパイラの警告 (レベル 3) C4648|標準属性 'carries_dependency' は無視されます。|
|コンパイラの警告 (レベル 3) C4649|このコンテキストで属性は無視されます。|
|[コンパイラの警告 (レベル 1) C4650](../../error-messages/compiler-warnings/compiler-warning-level-1-c4650.md)|プリコンパイル済みヘッダー以外ではなくデバッグ情報ヘッダーからのグローバル シンボルのみが提供されます。|
|[コンパイラの警告 (レベル 1) C4651](../../error-messages/compiler-warnings/compiler-warning-level-1-c4651.md)|'定義' プリコンパイル済みヘッダーに定義されていますが、現在のコンパイルではありません。|
|[コンパイラの警告 (レベル 1) C4652](../../error-messages/compiler-warnings/compiler-warning-level-1-c4652.md)|コンパイラ オプション 'option' プリコンパイル済みヘッダーです。現在のコマンド ライン オプションには、プリコンパイル済みヘッダーで定義されている上書きされます。|
|[コンパイラの警告 (レベル 2) C4653](../../error-messages/compiler-warnings/compiler-warning-level-2-c4653.md)|コンパイラ オプション 'option' プリコンパイル済みヘッダーです。現在のコマンド ライン オプションは無視されます。|
|コンパイラの警告 (レベル 4) C4654|プリコンパイル済みヘッダーの前に配置されたコードは、行が無視されます。 コードをプリコンパイル済みヘッダーに追加します。|
|[コンパイラの警告 (レベル 1) C4655](compiler-warning-level-1-c4655.md)|'symbol': 変数の型が最新のビルドから新規か異なる方法では、他の場所で定義されています。|
|[コンパイラの警告 (レベル 1) C4656](../../error-messages/compiler-warnings/compiler-warning-level-1-c4656.md)|'symbol': データ型は、新しいがまたは最新のビルド以降に変更されたか、異なる方法では、他の場所で定義されています。|
|[コンパイラの警告 (レベル 1) C4657](compiler-warning-level-1-c4657.md)|式には、最新のビルドから新規データ型が含まれています|
|コンパイラの警告 (レベル 1) C4658|'function': 関数プロトタイプが最新のビルドから新規または異なる方法では、他の場所で宣言されています|
|[コンパイラの警告 (レベル 1) C4659](../../error-messages/compiler-warnings/compiler-warning-level-1-c4659.md)|#pragma 'プラグマ': #pragma comment (linker,...) を使用して、予約されたセグメント 'segment' の使用に未定義の動作を|
|[コンパイラの警告 (レベル 1) C4661](../../error-messages/compiler-warnings/compiler-warning-level-1-c4661.md)|'identifier': 明示的なテンプレート インスタンス化の要求に適した定義がありません。|
|[コンパイラの警告 (レベル 1) C4662](compiler-warning-level-1-c4662.md)|明示的なインスタンス化。テンプレート クラス 'identifier1' に 'identifier2' を特定する定義がありません|
|[コンパイラの警告 (レベル 1) C4667](../../error-messages/compiler-warnings/compiler-warning-level-1-c4667.md)|'function': 強制インスタンス化に一致するように定義された関数テンプレートはありません|
|[コンパイラの警告 (レベル 4) C4668](../../error-messages/compiler-warnings/compiler-warning-level-4-c4668.md)|'symbol' が 'directive' の '0' に置き換えて、プリプロセッサ マクロとして定義されていません|
|[コンパイラの警告 (レベル 1) C4669](../../error-messages/compiler-warnings/compiler-warning-level-1-c4669.md)|'cast': 安全でない変換: 'class' はマネージ型のオブジェクト|
|[コンパイラの警告 (レベル 4) C4670](compiler-warning-level-4-c4670.md)|'identifier': この基本クラスはアクセスできません|
|コンパイラの警告 (レベル 4) C4671|'identifier': コピー コンス トラクターにアクセスできません|
|[コンパイラの警告 (レベル 4) C4672](compiler-warning-level-4-c4672.md)|'identifier1': あいまいです。 1 つ目を 'identifier2' とします。|
|[コンパイラの警告 (レベル 4) C4673](../../error-messages/compiler-warnings/compiler-warning-level-4-c4673.md)|'identifier' に、次の種類をスローすることは考慮されません catch サイト|
|[コンパイラの警告 (レベル 1) C4674](compiler-warning-level-1-c4674.md)|'method' は宣言された 'static' であり、パラメーターを 1 つだけ持たなければなりません。|
|コンパイラの警告 (レベル 4) C4676|' % $s ': デストラクターにアクセスできません|
|[コンパイラの警告 (レベル 1) C4677](../../error-messages/compiler-warnings/compiler-warning-level-1-c4677.md)|'function': 公開されたメンバーのシグネチャにはアセンブリ プライベート型 'private_type' が含まれています|
|[コンパイラの警告 (レベル 1) C4678](compiler-warning-level-1-c4678.md)|基底クラス 'base_type' のアクセス可能性が 'derived_type' よりも小さい|
|[コンパイラの警告 (レベル 1) C4679](../../error-messages/compiler-warnings/compiler-warning-level-1-c4679.md)|'member': could not import member|
|[コンパイラの警告 (レベル 4) C4680](../../error-messages/compiler-warnings/compiler-warning-level-4-c4680.md)|'class': コクラスは既定のインターフェイスを指定していません|
|[コンパイラの警告 (レベル 4) C4681](compiler-warning-level-4-c4681.md)|'class': コクラスは、イベント ソースである既定のインターフェイスを指定していません|
|[コンパイラの警告 (レベル 4) C4682](compiler-warning-level-4-c4682.md)|'parameter': 方向性のあるパラメーター属性がいません指定すると、[in]|
|[コンパイラの警告 (レベル 1) C4683](../../error-messages/compiler-warnings/compiler-warning-level-1-c4683.md)|'function': イベント ソースが 'out' のパラメーターです。複数のイベント ハンドラーをフックするときに注意|
|[コンパイラの警告 (レベル 1) C4684](../../error-messages/compiler-warnings/compiler-warning-level-1-c4684.md)|' attribute':警告!! 属性が原因で、無効なコードの生成: 慎重に使用|
|[コンパイラの警告 (レベル 1) C4685](compiler-warning-level-1-c4685.md)|テンプレート パラメーターの解析中に '> >' が必要ですが、'>>' が見つかりました。|
|[コンパイラの警告 (レベル 3) C4686](../../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)|'user-defined type': 動作と UDT の戻り値の呼び出し規則に変更がある可能性があります。|
|[コンパイラの警告 (エラー) C4687](../../error-messages/compiler-warnings/compiler-warning-c4687.md)|'class': シールドされた抽象クラスはインターフェイス 'interface' を実装できません|
|[コンパイラの警告 (レベル 1) C4688](../../error-messages/compiler-warnings/compiler-warning-level-1-c4688.md)|'constraint': 制約リストはアセンブリ プライベート型 'type' を含んでいます|
|コンパイラの警告 (レベル 1) C4689|'%c': unsupported character in #pragma detect_mismatch; #pragma ignored|
|[コンパイラの警告 (レベル 4) C4690](../../error-messages/compiler-warnings/compiler-warning-level-4-c4690.md)|\[ emitidl (pop)]: ポップがプッシュ|
|[コンパイラの警告 (レベル 1) C4691](../../error-messages/compiler-warnings/compiler-warning-level-1-c4691.md)|'type': 参照されていないアセンブリ 'file' を代わりに使用される現在の翻訳単位で定義された型で参照される型が必要です|
|[コンパイラの警告 (レベル 1) C4692](../../error-messages/compiler-warnings/compiler-warning-level-1-c4692.md)|'関数': 公開されたメンバーのシグネチャはアセンブリ プライベート ネイティブ型 'native_type' を含んでいます|
|[コンパイラの警告 (レベル 1、エラー) C4693](../../error-messages/compiler-warnings/compiler-warning-c4693.md)|'class': シールドされた抽象クラスが任意のインスタンス メンバー 'インスタンス メンバー' ことはできません|
|[コンパイラの警告 (レベル 1、エラー) C4694](../../error-messages/compiler-warnings/compiler-warning-c4694.md)|'class': a sealed abstract class cannot have a base-class 'base_class'|
|コンパイラの警告 (レベル 1) C4695|#pragma execution_character_set: '文字セット' はサポートされている引数ではありません現在は 'utf-8' がサポートされています|
|コンパイラの警告 (レベル 1) C4696|/ZBvalue1 オプションは範囲です。'value2' と仮定した場合|
|[コンパイラの警告 (レベル 1 およびレベル 4) C4700](../../error-messages/compiler-warnings/compiler-warning-level-1-and-level-4-c4700.md)|初期化されていないローカル変数 'name' の使用|
|[コンパイラの警告 (レベル 4) C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)|初期化されていない可能性があるローカル変数 'name' の使用|
|[コンパイラの警告 (レベル 4) C4702](../../error-messages/compiler-warnings/compiler-warning-level-4-c4702.md)|到達できないコード|
|[コンパイラの警告 (レベル 4) C4703](../../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md)|初期化されていない可能性があるローカル ポインター変数 '%s' が使用されます。|
|[コンパイラの警告 (レベル 4) C4706](../../error-messages/compiler-warnings/compiler-warning-level-4-c4706.md)|条件付きの式内の割り当て|
|[コンパイラの警告 (レベル 4) C4709](../../error-messages/compiler-warnings/compiler-warning-level-4-c4709.md)|配列インデックス式の中でコンマ演算子|
|[コンパイラの警告 (レベル 4) C4710](../../error-messages/compiler-warnings/compiler-warning-level-4-c4710.md)|'function': インライン関数ではありません。|
|[コンパイラの警告 (レベル 1) C4711](../../error-messages/compiler-warnings/compiler-warning-level-1-c4711.md)|関数 'function' が自動インライン展開の選択|
|[コンパイラの警告 (レベル 4) C4714](../../error-messages/compiler-warnings/compiler-warning-level-4-c4714.md)|関数 'function' がマークされている _ _forceinline として記述しないインライン|
|[コンパイラの警告 (レベル 1) C4715](../../error-messages/compiler-warnings/compiler-warning-level-1-c4715.md)|'function': 値を返さないコントロール パスのすべて|
|[コンパイラの警告 (レベル 1、エラー) C4716](../../error-messages/compiler-warnings/compiler-warning-level-1-c4716.md)|'function': 値を返す必要があります|
|[コンパイラの警告 (レベル 1) C4717](../../error-messages/compiler-warnings/compiler-warning-level-1-c4717.md)|'function': すべてのコントロール パスで再帰的で、関数には、ランタイム スタック オーバーフローが発生します|
|[コンパイラの警告 (レベル 4) C4718](compiler-warning-level-4-c4718.md)|'function call': 再帰呼び出しに削除する副作用がありません|
|コンパイラの警告 (レベル 1) C4719|Qfast が指定された使用 'f' を 1 つの有効桁数を示すサフィックスとして時に検出された、二重の定数|
|コンパイラの警告 (レベル 2) C4720|インライン アセンブラー レポート: 'message'|
|コンパイラの警告 (レベル 1) C4721|'function': 組み込み関数として使用できません。|
|[コンパイラの警告 (レベル 1) C4722](compiler-warning-level-1-c4722.md)|'function': デストラクターに値がメモリ リークの可能性|
|[コンパイラの警告 (レベル 3) C4723](../../error-messages/compiler-warnings/compiler-warning-level-3-c4723.md)|0 による除算の潜在的です|
|[コンパイラの警告 (レベル 3) C4724](compiler-warning-level-3-c4724.md)|剰余の 2 番目のオペランドは、コンパイル時に 0 と評価され、不定の結果を返します。|
|コンパイラの警告 (レベル 3) C4725|Pentium のモデルによっては、命令が不正確になります。|
|[コンパイラの警告 (レベル 1) C4727](../../error-messages/compiler-warnings/compiler-warning-level-1-c4727.md)|PCH は、obj_file_1 や obj_file_2 で同じタイムスタンプを持つ pch_file の名前。  最初の PCH を使用します。|
|コンパイラの警告 (レベル 1) C4728|/Yl-オプションは PCH 参照が必要なため、無視されます。|
|コンパイラの警告 (レベル 4) C4729|フロー グラフ ベースの警告の関数が大きすぎます。|
|[コンパイラの警告 (レベル 1) C4730](../../error-messages/compiler-warnings/compiler-warning-level-1-c4730.md)コンパイラの警告 (レベル 1) C4730|'main': _m64 と浮動小数点式は、不適切なコード、可能性があります|
|[コンパイラの警告 (レベル 1) C4731](../../error-messages/compiler-warnings/compiler-warning-level-1-c4731.md)|'pointer': フレーム ポインター レジスタが 'の ' 登録インライン アセンブラー コードによって変更されました。|
|コンパイラの警告 (レベル 1) C4732|このアーキテクチャでは、組み込みの '% $s' はサポートされていません|
|[コンパイラの警告 (レベル 1) C4733](../../error-messages/compiler-warnings/compiler-warning-level-1-c4733.md)|インライン asm は 'FS:0 'に割り当てる: ハンドラーは安全なハンドラーとして登録されていません|
|[コンパイラの警告 (レベル 3) C4738](../../error-messages/compiler-warnings/compiler-warning-level-3-c4738.md)|メモリに 32 ビットの浮動結果を格納します。パフォーマンスが低下する可能性があります|
|[コンパイラの警告 (レベル 1) C4739](compiler-warning-level-1-c4739.md)|変数 'var' への参照はそのストレージ領域を超えています|
|[コンパイラの警告 (レベル 4) C4740](../../error-messages/compiler-warnings/compiler-warning-level-4-c4740.md)|インライン asm コードの内外でのフローは、グローバルな最適化を抑制します。|
|[コンパイラの警告 (レベル 1) C4742](../../error-messages/compiler-warnings/compiler-warning-level-1-c4742.md)|'var' が 'file1' および 'file2' 内で異なるアラインメント: 番号と番号|
|[コンパイラの警告 (レベル 1) C4743](../../error-messages/compiler-warnings/compiler-warning-level-1-c4743.md)|'type' が 'file1' および 'file2' で別のサイズ: 数とバイト数です。|
|[コンパイラの警告 (レベル 1) C4744](../../error-messages/compiler-warnings/compiler-warning-level-1-c4744.md)|'var' が 'file1' および 'file2' に別の種類: 'type1' および 'type2'|
|[コンパイラの警告 C4746](../../error-messages/compiler-warnings/compiler-warning-c4746.md)|揮発性アクセス '*式*' は/volatile:\<iso&#124;ms > 設定; _iso_volatile_load/store 組み込み関数を使用を検討してください|
|[コンパイラの警告 (レベル 1) C4747](../../error-messages/compiler-warnings/compiler-warning-level-1-c4747.md)|呼び出し元が管理されている ' entrypoint':DLL エントリ ポイントおよび DLL エントリ ポイントから到達した呼び出しを含むローダー ロック下で、マネージ コードを実行しない可能性があります。|
|コンパイラの警告 (レベル 4) C4749|条件付きでサポートされています: 非標準レイアウト型に適用される offsetof '*型*'|
|[コンパイラの警告 (レベル 1) C4750](compiler-warning-level-1-c4750.md)|'identifier': ループにインライン展開されている _alloca() を含む関数です|
|コンパイラの警告 (レベル 4) C4751|intel (r) ストリーミング SIMD 拡張命令はインライン ASM 内にあるに/arch:AVX は適用されません。|
|コンパイラの警告 (レベル 4) C4752|intel (r) Advanced Vector Extensions; が見つかりません/arch:AVX の使用を検討します。|
|[コンパイラの警告 (レベル 4) C4754](compiler-warning-level-4-c4754.md)|%S (%d) の比較での算術演算の変換規則では、その 1 つの分岐を実行することはできませんを意味します。 '%S' '%s' (または %d バイトの類似する型) にキャストされます。|
|コンパイラの警告 C4755|%S (%d) の比較での算術演算の変換規則という意味では、インライン関数でその 1 つの分岐は実行できません。 '%S' '%s' (または %d バイトの類似する型) にキャストされます。|
|[コンパイラの警告 (レベル 2) C4756](../../error-messages/compiler-warnings/compiler-warning-level-2-c4756.md)|定数演算でオーバーフローしました。|
|コンパイラの警告 (レベル 4) C4757|添字が大きな unsigned の値を負の定数を意図しましたか。|
|[コンパイラの警告 (レベル 4) C4764](compiler-warning-level-4-c4764.md)|キャッチ オブジェクトを 16 バイトより大きい値を割り当てることはできません。|
|コンパイラの警告 (レベル 4) C4767|セクション名 '%s' が 8 文字より長いと、リンカーによって切り詰められます|
|コンパイラの警告 (レベル 3) C4768|リンケージ指定の前に _ _declspec 属性は無視されます。|
|コンパイラの警告 C4770|部分的に検証された列挙型 '*名前*' インデックスとして使用|
|コンパイラの警告 C4771|単純なポインターでは; を使用して境界を作成する必要があります。MPX 組み込み関数は無視されます。|
|[コンパイラの警告 (レベル 1、エラー) C4772](../../error-messages/compiler-warnings/compiler-warning-level-1-c4772.md)|#import; 不足しているタイプ ライブラリから型を参照します。' missing_type' プレース ホルダーとして使用|
|コンパイラの警告 (レベル 4) C4774|'*文字列*': 書式指定文字列の引数で想定される*数*リテラル文字列はありません|
|コンパイラの警告 (レベル 3) C4775|書式指定文字列で使用される標準の拡張機能 '*文字列*'function' の*関数*'|
|コンパイラの警告 (レベル 1) C4776|' %*文字*'は関数の書式指定文字列で許可されていません'*関数*'|
|コンパイラの警告 (レベル 4) C4777|'*関数*': 書式文字列'*文字列*'型の引数が必要です'*type1*'、可変個引数が、*数*型が '*type2*'|
|コンパイラの警告 (レベル 3) C4778|'*関数*': 書式指定文字列の終端されていない'*文字列*'|
|[コンパイラの警告 (レベル 1) C4788](../../error-messages/compiler-warnings/compiler-warning-level-1-c4788.md)|'identifier': 識別子は 'number' 文字に切り詰められました|
|[コンパイラの警告 (レベル 1) C4789](../../error-messages/compiler-warnings/compiler-warning-level-1-c4789.md)|バッファー 'identifier' (サイズが N バイト) でオーバーランが発生します。M バイトがオフセット L から書き込まれます|
|コンパイラの警告 (レベル 2) C4792|関数 '%s' は sysimport を使用して宣言し、ネイティブ コードから参照されています。リンクに必要なライブラリをインポートします。|
|[コンパイラの警告 (レベル 1 および 3) C4793](../../error-messages/compiler-warnings/compiler-warning-level-1-and-3-c4793.md)|'function': ネイティブ: \n\t'reason としてコンパイルされた関数 '|
|[コンパイラの警告 (レベル 1) C4794](compiler-warning-level-1-c4794.md)|スレッド ローカル ストレージ変数 '%s' '%s' から '%s' に変更のセグメント|
|[コンパイラの警告 (レベル 1) C4799](../../error-messages/compiler-warnings/compiler-warning-level-1-c4799.md)|関数 'function' に EMMS 命令がありません。|

## <a name="see-also"></a>関連項目

[C/C++コンパイラとビルド ツールのエラーと警告](../compiler-errors-1/c-cpp-build-errors.md) \
[コンパイラの警告 C4000 - C5999](compiler-warnings-c4000-c5999.md)
