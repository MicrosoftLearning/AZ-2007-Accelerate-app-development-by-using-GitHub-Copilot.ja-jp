---
demo:
  title: 'デモ:GitHub Copilot Chat を使用してコードの信頼性とパフォーマンスを改善する'
  module: 'Module 5: Implement code improvements using GitHub Copilot tools'
---

# デモ:GitHub Copilot Chat を使用してコードの信頼性とパフォーマンスを改善する

## 手順

デモのアクティビティは、次のリソースを含む環境向けに設計されています。

- Visual Studio Code。
- Visual Studio Code 用の C# 開発キット拡張機能。
- Visual Studio Code 用の GitHub Copilot および GitHub Copilot Chat 拡張機能。 GitHub Copilot のアクティブなサブスクリプションを持つ GitHub アカウントが必要です。
- C# を使用して作成されたサンプル コード プロジェクト。

**注**:デモには講師自身の GitHub アカウントと GitHub Copilot サブスクリプションを使用することを検討するようにお勧めします。 そうすると開発環境を制御およびカスタマイズできるようになります。 また、クラスルームの必要に合わせてデモを簡単に調整できます。

**重要**:講師の PC ではなく、ホストされたラボ環境でデモを実行することを選択した場合は、ホストされた環境でサンプル アプリを解凍できます。 デモを実行する前に、ホストされた環境で GitHub Copilot 拡張機能を構成する必要があります。 ホストされた環境はローカル環境よりも遅い場合があるため、それに応じてデモのペースを調整することが必要になる場合があります。

### デモを紹介する

コードの信頼性とパフォーマンスは、ソフトウェアの品質と密接に関係しています。 これらは、次のような点で相互に依存しています。

- ある分野を改善すると、他の分野にも良い影響があります。
- 一方に不備があると、もう一方にも問題が生じます。

> [!IMPORTANT]
> このデモが、信頼性の高い、または高パフォーマンスのコードを開発するためのベスト プラクティスを示すものではないことを学生に説明します。 そうではなく、GitHub Copilot Chat を使用して、サンプル アプリケーションのコードの信頼性とパフォーマンスを向上するための提案を示すことに焦点を当てています。 提案は、コードの信頼性とパフォーマンスに関するベスト プラクティスや包括的なソリューションを表すものではありません。 開発者は、自身の判断と専門知識を使用して、GitHub Copilot Chat から提供される提案を評価し、実装する必要があります。 GitHub Copilot から提示された提案を実装したとしても、徹底的なコードの確認やテストが必要であることに変わりはありません。

#### コードの信頼性とパフォーマンス

開発者は、コードの信頼性とパフォーマンスのバランスをとるよう努力する必要があります。 うまくバランスをとることで、次のような互いに有益な結果が生まれます。

- 機能要件を満たすアプリケーション。
- シームレスで効率的なユーザー エクスペリエンスを提供するアプリケーション。

以下のセクションでは、学生が知っておくべきコードの信頼性とパフォーマンスの概要およびその他の要因について説明します。

##### コードの信頼性を調べる

コードの信頼性とは、ソフトウェアが特定の条件下で一定期間適切に機能する可能性を指します。 コードの信頼性を向上させることで、ソフトウェアは期待どおりのパフォーマンスを発揮し、ユーザーの要件を満たすことができます。

開発者は、コードの信頼性の向上に取り組むときに、次の要素を考慮することができます。

- 潜在的な問題:コードの潜在的な問題を特定することで、バグやエラーの発生を防ぐのに役立ちます。 潜在的な問題を特定するには、よくある落とし穴がないかコードを確認し、積極的に対処する必要があります。
- テスト:製品をリリースする前にバグを特定して修正するには、十分なテストが不可欠です。 適切なテストには、単体テスト、統合テスト、システム テスト、承認テストを含める必要があります。
- 例外処理:例外処理メカニズムが適切であれば、予期しない状況が発生した場合にシステムに障害が発生するのを防止できます。

> [!NOTE]
> コードの信頼性に取り組む前に、コード品質が高いことを確認します。 コードのリファクタリングは、標準やガイドラインとともに、高品質のコードを確保するのに役立ちます。

コードの信頼性に影響を与える要因は他にもあります。 これらの要因の中には、開発者の責任ではないものもあれば、コードの信頼性の前後に考慮が必要なものもあります。 その他の要因には次のものがあります。

- 開発プラクティス:コード レビュー、ペア プログラミング、コーディング標準への準拠など、ソフトウェア開発のベスト プラクティスに従うことで、より信頼性の高いコードを作成できます。
- 信頼性の目標とメトリック:信頼性の明確な目標を設定し、それを測定するメトリックを持つことが、より信頼性の高いソフトウェアを作成するための開発プロセスにつながります。
- ドキュメント:包括的なドキュメントは、システムの保守やトラブルシューティングに不可欠であるシステムとそのコンポーネントを理解するのに役立ちます。
- 依存関係:コードが依存する外部ライブラリや外部サービスは、コードの信頼性に影響を与える可能性があります。 サードパーティのサービスに障害が発生すると、依存するシステムにも障害が発生する可能性があります。
- パフォーマンス：パフォーマンスの問題は信頼性にも影響します。 システムがさまざまな負荷の下で優れたパフォーマンスを発揮できるようにすることが重要です。
- 監視とトラブルシューティング:継続的な監視と信頼性の高いトラブルシューティング ガイドは、問題を迅速に特定して対処することで、サービスの信頼性を維持するのに役立ちます。
- 設計とアーキテクチャ:強固なアーキテクチャを持つ十分に設計されたシステムは、エラーを適切に処理し、一部のコンポーネントに障害が発生しても機能を維持できます。
- 外部要因:リリース後の信頼性の問題は、ハードウェアやオペレーティング システムの更新などの外部要因によって発生する可能性があり、互換性の問題やシステム障害が発生する可能性があります。

コードの信頼性を高めることで、バグ、エラー、予期しない動作が発生する可能性を削減できます。

##### コードのパフォーマンスを調べる

コード パフォーマンスとは、特に速度、メモリ使用量、全体のリソース消費量において、プログラムやアプリケーションがどれだけ効率的に実行されるかを指します。 コードのパフォーマンスを確保または改善するために、開発者は次のようなアクションを取ることができます。

開発者は、コードのパフォーマンスの向上に取り組むときに、次の要素を考慮する必要があります。

- アルゴリズムの最適化:目の前のタスクに対して最も効率的なアルゴリズムとデータ構造を選択します。 小さな改善でも、パフォーマンスが大きく向上する可能性があります。
- 不要なコストの回避:コストのかかる操作の結果を可能な限りキャッシュし、冗長な計算を回避します。
- マルチスレッドと非同期プログラミングの使用:タスクを並列化し、I/O 操作を非同期で実行することで、最新の CPU アーキテクチャを活用できます。
- I/O　操作の最小化:ディスクとネットワークの I/O は時間がかかる場合があるため、メイン実行スレッドがブロックされないように、これらの操作を最小限にするか、非同期で実行することが重要です。

> [!NOTE]
> コードのパフォーマンスに取り組む前に、コード品質が高いことを確認します。 コードのリファクタリングは、標準やガイドラインとともに、高品質のコードを確保するのに役立ちます。

コードのパフォーマンスに影響を与える要因は他にもあります。 これらの要因の中には、開発者の責任ではないものもあれば、コードのパフォーマンスに取り組む前後に考慮が必要なものもあります。 その他の要因には次のものがあります。

- プロファイルとベンチマーク:プロファイリング ツールを使用してパフォーマンスのボトルネックを特定します。 変更の前後でベンチマークを行うことで、最適化の影響を定量化できます。
- メモリの効率的な管理:メモリ プロファイリング ツールを使用してリークを検出し、メモリが適切に割り当てられ、割り当て解除されていることを確認します。
- データベースの対話の最適化:効率的なクエリ、適切なインデックス作成、データベース キャッシュを使用して、データベースとの対話によるパフォーマンスのオーバーヘッドを最小限に抑えます。
- コード レビュー:パフォーマンスに問題がないか、定期的にコードを確認します。 ピア レビューは、元の開発者が見逃した可能性のある非効率性を発見するのに役立ちます。
- 最新の状態への維持:言語、ライブラリ、フレームワークの最新バージョンを使用することで、パフォーマンスが向上する場合がよくあります。
- 教育とコラボレーション:パフォーマンス最適化のベスト プラクティスに関する情報を最新の状態に維持し、他の開発者と協力してその経験から学びます。

開発者がこれらの分野に集中することで、コードのパフォーマンスを大幅に向上させ、より高速で応答性の高いアプリケーションを実現できます。 パフォーマンスの最適化は継続的なプロセスであり、アプリケーションのパフォーマンスを継続的に監視し、改善することが重要です。

GitHub Copilot Chat は、アルゴリズムの最適化、不要な計算の削減、マルチスレッドおよび非同期プログラミングの使用、I/O 操作の最小化などの提案を提供することで、コードのパフォーマンスの向上に役立ちます。

### GitHub Copilot Chat のプロンプトを開発する

GitHub Copilot Chat について記述するプロンプトでは、明確に定義したコンテキストと意図を指定する必要があります。 プロンプトを開発するときは、次の推奨事項を考慮してください。

- 更新するコードよりも高いレベルで範囲を設定する、外側のコンテキストを定義します。 たとえば、メソッドを改善する場合は、そのメソッドを含むクラスまたはファイルを外側のコンテキストとして指定します。 メソッドを内側のコンテキストとして識別します。
- チャット参加者とチャット変数を使用して、コンテキストを指定します。 `#file:` と `#selection` のチャット変数を使用して、焦点を当てる特定のコードを識別できます。 必要に応じて、ワークスペース全体 (`@workspace`) を含めることもできます。 ファイルまたはプロンプトの自然言語部分の選択対象を参照してください。
- 意図は明確かつ簡潔で、具体的である必要があります。 プロンプトでは、達成したい改善点の種類を指定する必要があります。

デモのこの部分では、**APL2007M5BankAccount-Reliability** プロジェクトを確認し、GitHub Copilot Chat のプロンプトを 3 つ作成します。 プロンプトは、コードの信頼性とパフォーマンスの向上に焦点を当てています。

次の手順に従って、デモのこの部分を完了します。

1. Visual Studio Code で **APL2007M5BankAccount-Reliability** サンプル アプリを開きます。

1. [ソリューション エクスプローラー] ビューを開きます。

1. **BankAccount** プロジェクトを展開し、**BankAccount.cs** および **Program.cs** コード ファイルを確認します。

    **BankAccount.cs** ファイルには `BankAccount` クラス用のコードが含まれます。このクラスは、AccountNumber、Balance、AccountHolderName、AccountType、DateOpened などのプロパティを持つ銀行口座を表します。 それには次のメソッドが含まれています。

    - Credit(double amount):このメソッドは、指定された金額に応じて口座の残高を増やします。
    - Debit(double amount):このメソッドは、指定された金額に応じて口座の残高を減らします。 口座残高が金額より小さい場合、"出金額に対して残高が不足しています" というメッセージとともに例外がスローされます。
    - GetBalance():このメソッドは、勘定の現在の残高を返します。
    - Transfer(BankAccount toAccount, double amount):このメソッドは、現在の口座から指定された金額を toAccount に送金します。 口座残高が金額より小さい場合、"送金額に対して残高が不足しています" というメッセージとともに例外がスローされます。 AccountHolderName が異なり、金額が 500 を超える場合、"異なる口座送金者に対する送金額が上限を超過しています" というメッセージとともに例外がスローされます。
    - PrintStatement():このメソッドは、コンソールに AccountNumber と Balance を表示します。
    - CalculateInterest(double interestRate):このメソッドは、指定された interestRate を使用して現在の Balance の利息を計算します。

    **Program.cs** ファイルには、銀行システムをシミュレートするコンソール アプリケーションが含まれます。 これには次のメソッドが含まれています。

    - Main メソッド:アプリケーションのエントリ ポイントです。 銀行口座の一覧を作成し、トランザクションをシミュレートし、これらの口座で転送します。
    - CreateBankAccounts メソッド:このメソッドは、指定した数の銀行口座を、ランダムな初期残高、口座所有者名、口座の種類、口座開設日を使用して作成します。 これは、try-catch ブロックを使用して、口座の作成時に発生する可能性のある例外を処理します。
    - SimulateTransactions メソッド:このメソッドは、指定された一覧の各口座に対し、指定した数のトランザクションをシミュレートします。 各トランザクションはランダムなドルの金額で、金額がプラスかマイナスかによって、credit (入金) か debit (出金) のどちらかになります。
    - SimulateTransfers メソッド:このメソッドは、SimulateTransactions と同じです。 口座間の送金をシミュレートするのが目的のように見えますが、現状では SimulateTransactions の機能と重複しているだけです。
    - GenerateRandomDollarAmount メソッド:このメソッドは、指定した範囲内でランダムなドルの金額を生成します。 範囲と計算方法は、口座残高とトランザクションのどちらに対する金額であるかによって異なります。
    - GenerateRandomAccountHolder メソッド:このメソッドは、定義済みの一覧から、ランダムな口座所有者の名前を選択します。
    - GenerateRandomAccountType メソッド:このメソッドは、定義済みの一覧から、ランダムな口座の種類を選択します。
    - GenerateRandomDateOpened メソッド:このメソッドは、口座開設日に対して指定した範囲内でのランダムな日付を生成します。

1. 少し時間を取って、コードの信頼性とパフォーマンスの向上に役立つプロンプトについて説明します。

    BankAccount クラスと Program クラスの両方に対するプロンプトを作成します。 プロンプトを開発する場合は、次の信頼性とパフォーマンスの要素を考慮してください。

    - 潜在的な問題:コードの潜在的な問題を特定することで、バグやエラーの発生を防ぐのに役立ちます。 これには、よくある落とし穴がないかコードを確認し、積極的に対処することが含まれます。
    - テスト:製品をリリースする前にバグを特定して修正するには、十分なテストが不可欠です。 これには、単体テスト、統合テスト、システム テスト、承認テストが含まれます。
    - 例外処理:例外処理メカニズムが適切であれば、予期しない状況が発生した場合にシステムに障害が発生するのを防止できます。

    - アルゴリズムの最適化:目の前のタスクに対して最も効率的なアルゴリズムとデータ構造を選択します。 小さな改善でも、パフォーマンスが大きく向上する可能性があります。
    - 不要なコストの回避:コストのかかる操作の結果を可能な限りキャッシュし、冗長な計算を回避します。
    - マルチスレッドと非同期プログラミングの使用:タスクを並列化し、I/O 操作を非同期で実行することで、最新の CPU アーキテクチャを活用できます。
    - I/O　操作の最小化:ディスクとネットワークの I/O は時間がかかる場合があるため、メイン実行スレッドがブロックされないように、これらの操作を最小限にするか、非同期で実行することが重要です。

    このプロジェクトでは、次のプロンプトを使用して、コードの信頼性を向上するための提案を生成できます。

    プロンプト: `@workspace /explain How can I improve exception handling the [selected code]?` (チャット コンテキストに BankAccount.cs を添付する)

    プロンプト: `@workspace /explain How can I reduce unexpected issues for the [selected code]?` (チャット コンテキストに BankAccount.cs を添付する)

    プロンプト: `@workspace /explain How can I improve unit test support for the [selected code]?` (チャット コンテキストに BankAccount.cs を添付する)

    プロンプト: `@workspace /explain How can I avoid future bugs or issues in the [selected code]?` (チャット コンテキストに Program.cs を添付する)

    プロンプト: `@workspace /explain How can I improve exception handling for the [selected code]?` (チャット コンテキストに Program.cs を添付する)

    プロンプト: `@workspace /explain How can I improve the efficiency of algorithms or data structures for the [selected code]?` (チャット コンテキストに Program.cs を添付する)

    プロンプト: `@workspace /explain How can I improve performance with asynchronous tasks or methods in the [selected code]?` (チャット コンテキストに Program.cs を添付する)

    プロンプト: `@workspace /explain How can I improve unit test support for the [selected code]?` (チャット コンテキストに BankAccountTests.cs と BankAccount.cs を添付する)

1. このデモ中に、BankAccount クラスを改善するために使用できるプロンプトを 2 つ選択します。

    BankAccount クラスでは、信頼性に焦点を当てたプロンプトを選択してみてください。

1. このデモ中に、Program クラスを改善するために使用できるプロンプトを 2 つ選択します。

    Program クラスでは、信頼性に焦点を当てたプロンプトとパフォーマンスに焦点を当てたプロンプトを 1 つずつ選択してみてください。

### GitHub Copilot Chat を使用して BankAccount クラスのコードの信頼性を強化する

運用コードの信頼性を確保することは、どのソフトウェア プロジェクトに対しても不可欠です。 APL2007M5BankAccount-Reliability サンプル アプリケーションでは、Program クラスを使用して銀行シナリオをシミュレートしていますが、運用環境にデプロイされるのは BankAccount クラスです。 BankAccount クラスの信頼性を向上させることで、期待どおりのパフォーマンスを発揮し、ユーザーの要件を満たすことができます。

コードの信頼性を向上するには、GitHub Copilot Chat を使用できます。 GitHub Copilot にプロンプトを指示することで、例外処理の改善、予期しない問題の削減、単体テストのサポートの改善などの提案を生成できます。 また、コードの信頼性を向上するための一般的な提案を求める、広範なプロンプトを作成することもできます。 特定のプロンプトと一般的なプロンプトを組み合わせることで、改善が必要な領域を特定し、必要な変更を実装できます。

> [!NOTE]
> 推奨される更新プログラムの実装とテストには時間がかかり、このデモでは時間が決め手になる可能性があります。 特定の改善領域に焦点を当てたプロンプトを選択すると、時間を管理するのに役立ちます。 プロンプトが広範囲すぎると、多数の提案が生成されたり、短時間では評価や実装が困難な複雑な提案が生成される場合があります。 開始後に、提案された更新の範囲が広すぎる、または複雑すぎると感じたら、より具体的なプロンプトに更新できます。

次の手順に従って、デモのこの部分を完了します。

1. プロジェクトがビルドされ、エラーなしで実行されることを確認します。

    アプリケーションが実行されている限り警告は許容されますが、アプリケーションのクラッシュを引き起こす未処理のエラーは、GitHub Copilot Chat の使用を開始する前に解決する必要があります。

1. Visual Studio Code で BankAccount.cs ファイルを開き、ファイル内のすべてのコードを選択します。

1. チャット ビューを開きます。

1. チャット ビューで、関連するファイルをチャット コンテキストに追加し、プロンプトを入力します。

1. GitHub Copilot Chat から提供される提案を確認します。

    たとえば、次のアクションを完了したとします。

    - BankAccount.cs ファイルを開き、すべてのコードを選択します。
    - 次のプロンプトを選択します: `@workspace /explain How can I improve exception handling in the BankAccount.cs file?`
    - チャット ビューを開き、BankAccount.cs ファイルと Program.cs ファイルをチャット コンテキストに添付します。
    - チャット ビューにプロンプトを入力します。

    GitHub Copilot Chat から、次の応答のような更新内容が提案されます。

    "BankAccount.cs ファイルの例外処理を改善するには、次の提案を検討します。"**

    *1.**具体的な例外を使用する**:基となる `Exception` クラスをスローする代わりに、より特殊な例外を使用します。こうすることで、呼び出し元コードで特定の種類のエラーを解釈し、処理しやすくなります。たとえば、資金不足の状態で出金や送金を行おうとしたときに InvalidOperationException をスローすることができます。*

    *2.**例外メッセージに詳細情報を含める**:失敗した操作の詳細を例外メッセージで提供できます。たとえば、`Debit` メソッドでは、出金しようとした金額と現在の残高を例外メッセージに含めることができます。*

    *3.**カスタム例外を考慮する**:アプリケーションに固有のエラー条件がある場合は、必要に応じてカスタム例外クラスを作成します。カスタム例外を作成することで、エラー状態に関する詳細情報をカプセル化し、コードの目的を明確化できます。*

    *次のような提案を使用した `Debit` メソッドの改善方法を示します:*

    ```csharp

    public void Debit(double amount)
    {
        if (Balance >= amount)
        {
            Balance -= amount;
        }
        else
        {
            throw new InvalidOperationException($"Insufficient balance for debit. Attempted to debit {amount}, but current balance is {Balance}.");
        }
    }

    ```

    *また、カスタム例外クラスの例を次に示します:*

    ```csharp

    public class InsufficientFundsException : Exception
    {
        public double AttemptedAmount { get; }
        public double CurrentBalance { get; }
        public InsufficientFundsException(double attemptedAmount, double currentBalance)
            : base($"Insufficient balance for debit. Attempted to debit {attemptedAmount}, but current balance is {currentBalance}.")
        {
            AttemptedAmount = attemptedAmount;
            CurrentBalance = currentBalance;
        }
    }

    ```

    *Debit メソッドでこのカスタム例外をスローできます:*

    ```csharp

    public void Debit(double amount)
    {
        if (Balance >= amount)
        {
            Balance -= amount;
        }
        else
        {
            throw new InsufficientFundsException(amount, Balance);
        }
    }

    ```

    *こうすることで、呼び出しコードは InsufficientFundsException をキャッチし、AttemptedAmount プロパティと CurrentBalance プロパティにアクセスして、エラー状態をより効果的に処理できます。*

1. `BankAccount` クラスのコードの信頼性を向上するのに役立つ、提案された更新を実装します。

1. 変更によってエラーが発生しないようにするには、続行する前にソリューションをビルドして実行します。

    > [!TIP]
    > 上記の例では、[チャット] ビューは、提案された更新の一例 (特定の例外のを使用する、例外メッセージに詳細な情報を含める、カスタム例外を作成する) を実装するコード スニペットを提供しました。 提案を実装したら、コード行入力候補を使用して、更新を複製した新しいコードを生成してみてください。 この例の場合、コード行入力候補を使用して、詳細なカスタム例外クラスを作成できます。 次に、コード行入力候補を使用して、新しいカスタム例外で他のメソッドを更新できます。 元のプロンプトを再実行して他の提案を確認することもできます。

1. BankAccount.cs ファイル内のすべてのコードを選択します。

1. チャット ビューを開きます。

1. **[コンテキスト添付]** ボタンを使用して関連するファイルをチャット コンテキストに追加し、2 番目の "信頼性" プロンプトを入力します。

1. GitHub Copilot Chat から提供される提案を確認します。

    たとえば、[チャット] ビューに `@workspace /explain How can I reduce unexpected issues for the selected code?` と入力すると、GitHub Copilot Chat からは、次の応答のような更新が提案されます。

    "BankAccount クラスでの予期しない問題を減らすために、次の改善を実装できます。"**

    *1.口座の種類に Enum を使用する:口座の種類に文字列を使用し、それが "Savings" か "Current" かを確認するのではなく、列挙型を使用することを検討します。これにより、文字列の比較で発生する可能性のある問題 (大文字小文字の区別など) を防ぎ、口座の種類を定義済みの値に制限できます。*

    ```csharp

    public enum AccountType
    {
        Savings,
        Current
    }

    ```

    *2.金額に 10 進数を使用する:一般に、丸めエラーを回避するために、金額には double 型ではなく decimal 型を使用することをお勧めします。*

    *3.その他の検証を追加する:メソッドに検証を追加することもできます。たとえば、Transfer メソッドでは、送金を実行する前に toAccount が NULL でないことを確認できます。*

    *4.マジック ナンバーに定数を使用する:使用する Transfer メソッドにはマジック ナンバー 500 があります。それをクラスの先頭で、意味のある名前を持つ定数として定義することが適しています。*

    ```csharp
    private const double MaxTransferAmountForDifferentOwners = 500;
    ```

    *5.送金上限に対するカスタム例外:異なる口座所有者に対して送金額が上限を超えた場合に一般的な例外をスローする代わりに、ExceededTransferLimitException のようなカスタム例外を作成することを検討してください。*

    *6.ログ記録:アプリケーションにログ記録を追加することを検討してください。これは、アプリケーションのフローを理解し、問題を診断するのに役立ちます。*

    *7.単体テスト:メソッドの単体テストを記述して、さまざまなシナリオでメソッドが期待どおりに動作することを確認します。これは、開発プロセスの早い段階で問題をキャッチするのに役立ちます。*

1. GitHub Copilot Chat で提供される提案の範囲と幅を考慮してください。

    プロンプトによっては、広い範囲に影響する多数の提案が生成される場合があります。 このような場合は、より具体的な意図やコンテキストを提供する新しいプロンプトを定義するために単一の提案項目を使用できるかどうかを確認してください。

1. 提案の一覧を使用して、より詳細な意図やコンテキストを含むプロンプトを作成します。

    GitHub Copilot Chat で提供された提案は、それぞれ個別に調査して実装できます。 一覧の先頭から始めて、下へ行くほど、一度に 1 つの改善に焦点を当てることができます。

1. [チャット] ビューに詳細なプロンプトを入力し、GitHub Copilot Chat で提供される提案を確認します。

    2 番目の prompt プロンプトの例を使用したとします。 GitHub Copilot Chat の応答には、次の提案項目が含まれています。

    *その他の検証を追加する:メソッドに検証を追加することもできます。たとえば、Transfer メソッドでは、送金を実行する前に toAccount が NULL でないことを確認できます。*

    この提案を使用して、Transfer メソッドに検証を追加することに焦点を当てた新しいプロンプトを作成できます。 Transfer メソッドを選択し、[チャット] ビューで次のプロンプトを入力できます。

    `@workspace /explain #file:BankAccount.cs How can I improve method validations for the selected code?`

    この場合は、GitHub Copilot Chat から、次の応答のような更新内容が提案されます。

    *指定したコードは適切に構造化されており、例外処理に関するお勧めの方法に従っています。ただし、改善できる部分がいくつかあります。*

    *1.検証ロジックを統合する:すべての検証ロジックを処理するために、別の検証クラスやメソッドを作成できます。これにより、BankAccount クラスがより明確になり、主な役割に重点が置かれるようになります。*

    *2.カスタム検証属性を使用する:検証の一部には、カスタム検証属性を使用できます。これにより、検証が必要なプロパティに注釈を付け、検証ロジックをビジネス ロジックから分離できます。*

    *3.Fluent Validation を使用する:Fluent Validation は、検証規則を構築するために fluent インターフェイスとラムダ式を使用する .NET ライブラリです。これにより、検証コードをより直感的で読みやすくすることができます。*

    *4.マジック ナンバーを避ける:Transfer メソッドでは、ハードコードされた値として 500 が設定されています。一般的に、"マジック ナンバー" は回避し、代わりにクラスの先頭で意味のある名前を持つ定数として定義するのがお勧めの方法です。*

    これらの提案のいくつかを実装する方法の例を次に示します。

    ```csharp

    public class BankAccount
    {
        private const double MaxTransferAmountForDifferentOwners = 500;
        // ...
        public void Transfer(BankAccount toAccount, double amount)
        {
            ValidateTransferAmount(amount);
            ValidateTransferLimitForDifferentOwners(toAccount, amount);
    
            if (Balance >= amount)
            {
                Debit(amount);
                toAccount.Credit(amount);
            }
            else
            {
                throw new InsufficientFundsException(amount, Balance);
            }
        }
        private void ValidateTransferAmount(double amount)
        {
            if (amount < 0)
            {
                throw new InvalidTransferAmountException(amount);
            }
        }
        private void ValidateTransferLimitForDifferentOwners(BankAccount toAccount, double amount)
        {
            if (AccountHolderName != toAccount.AccountHolderName && amount > MaxTransferAmountForDifferentOwners)
            {
                throw new Exception("Transfer amount exceeds maximum limit for different account owners.");
            }
        }
    }

    ```

    GitHub Copilot Chat で提供される提案を参考にしながら、必要と思われる改善をすべて実施するまで作業を続行できます。

1. 提案された更新プログラムを実装し、続行する前にソリューションをビルドして実行します。

    続行する前に、変更によって生じたエラーを修正します。

### GitHub Copilot Chat を使用して Program クラスのコードの信頼性とパフォーマンスを改善する

1. Visual Studio Code で Program.cs ファイルを開き、ファイル内のすべてのコードを選択します。

1. Visual Studio Code で Program.cs ファイルを開き、ファイル内のすべてのコードを選択します。

1. チャット ビューを開きます。

1. チャット ビューで、**[コンテキスト添付]** ボタンを使用して関連するファイルをチャット コンテキストに追加し、プロンプトを入力します。

1. GitHub Copilot Chat から提供される提案を確認します。

    たとえば、[チャット] ビューに `@workspace /explain How can I improve performance with asynchronous tasks or methods in the Program.cs file?` と入力すると、GitHub Copilot Chat からは、次の応答のような更新が提案されます。

    Program.cs ファイル内の非同期タスクまたはメソッドのパフォーマンスを高めるには、async および await キーワードを使用した非同期プログラミングを使用できます。*これにより、プログラムはメイン スレッドをブロックせずに I/O バウンド操作を実行できるようになり、応答性と効率性が向上します。*

    "非同期メソッドを含む Program.cs ファイルの改善されたバージョンを次に示します。"**

    ```csharp

    using System;
    using System.Collections.Generic;
    using System.Threading.Tasks;
    namespace BankAccountApp
    {
        class Program
        {
            private static readonly Random random = new Random();
            private const int MaxYearsBack = 10;
            private const int NumberOfAccounts = 20;
            private const int NumberOfTransactions = 100;
            private const double minTransactionAmount = -500.0;
            private const double maxTransactionAmount = 500.0;
            private const double minAccountStart = 200.0;
            private const double maxAccountStart = 1000.0;
            static async Task Main(string[] args)
            {
                List<BankAccount> accounts = await CreateBankAccountsAsync(NumberOfAccounts);
                await SimulateTransactionsAsync(accounts, NumberOfTransactions, minTransactionAmount, maxTransactionAmount);
                await SimulateTransfersAsync(accounts, NumberOfTransactions, minTransactionAmount, maxTransactionAmount);
            }
            static async Task<List<BankAccount>> CreateBankAccountsAsync(int numberOfAccounts)
            {
                List<BankAccount> accounts = new List<BankAccount>();
                int createdAccounts = 0;
                while (createdAccounts < numberOfAccounts)
                {
                    try
                    {
                        double initialBalance = GenerateRandomDollarAmount(true, minAccountStart, maxAccountStart);
                        string accountHolderName = GenerateRandomAccountHolder();
                        string accountType = GenerateRandomAccountType();
                        DateTime dateOpened = GenerateRandomDateOpened();
                        BankAccount account = new BankAccount($"Account {createdAccounts + 1}", initialBalance, accountHolderName, accountType, dateOpened);
                        accounts.Add(account);
                        createdAccounts++;
                    }
                    catch (Exception ex)
                    {
                        Console.WriteLine($"Account creation failed: {ex.Message}");
                    }
                    await Task.Yield(); // Yield control to allow other tasks to run
                }
                return accounts;
            }
            static async Task SimulateTransactionsAsync(List<BankAccount> accounts, int numberOfTransactions, double minTransactionAmount, double maxTransactionAmount)
            {
                List<Task> tasks = new List<Task>();
                foreach (BankAccount account in accounts)
                {
                    tasks.Add(Task.Run(async () =>
                    {
                        for (int i = 0; i < numberOfTransactions; i++)
                        {
                            double transactionAmount = GenerateRandomDollarAmount(false, minTransactionAmount, maxTransactionAmount);
                            try
                            {
                                if (transactionAmount >= 0)
                                {
                                    account.Credit(transactionAmount);
                                    Console.WriteLine($"Credit: {transactionAmount}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                                }
                                else
                                {
                                    account.Debit(-transactionAmount);
                                    Console.WriteLine($"Debit: {transactionAmount}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                                }
                            }
                            catch (Exception ex)
                            {
                                Console.WriteLine($"Transaction failed: {ex.Message}");
                            }
                            await Task.Yield(); // Yield control to allow other tasks to run
                        }
                        Console.WriteLine($"Account: {account.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                    }));
                }
                await Task.WhenAll(tasks);
            }
            static async Task SimulateTransfersAsync(List<BankAccount> accounts, int numberOfTransactions, double minTransactionAmount, double maxTransactionAmount)
            {
                List<Task> tasks = new List<Task>();
                foreach (BankAccount account in accounts)
                {
                    tasks.Add(Task.Run(async () =>
                    {
                        for (int i = 0; i < numberOfTransactions; i++)
                        {
                            double transactionAmount = GenerateRandomDollarAmount(false, minTransactionAmount, maxTransactionAmount);
                            try
                            {
                                if (transactionAmount >= 0)
                                {
                                    account.Credit(transactionAmount);
                                    Console.WriteLine($"Credit: {transactionAmount}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                                }
                                else
                                {
                                    account.Debit(-transactionAmount);
                                    Console.WriteLine($"Debit: {transactionAmount}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                                }
                            }
                            catch (Exception ex)
                            {
                                Console.WriteLine($"Transaction failed: {ex.Message}");
                            }
                            await Task.Yield(); // Yield control to allow other tasks to run
                        }
                        Console.WriteLine($"Account: {account.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                    }));
                }
                await Task.WhenAll(tasks);
            }
            static double GenerateRandomDollarAmount(bool isAccount, double min, double max)
            {
                if (isAccount)
                {
                    double accountStartingValue = random.NextDouble() * (max - min) + min;
                    return Math.Round(accountStartingValue, 2);
                }
                else
                {
                    double transactionAmount = random.NextDouble() * random.Next((int)min, (int)max) + random.NextDouble();
                    return Math.Round(transactionAmount, 2);
                }
            }
            static string GenerateRandomAccountHolder()
            {
                string[] accountHolderNames = { "John Smith", "Maria Garcia", "Mohammed Khan", "Sophie Dubois", "Liam Johnson", "Emma Martinez", "Noah Lee", "Olivia Kim", "William Chen", "Ava Wang", "James Brown", "Isabella Nguyen", "Benjamin Wilson", "Mia Li", "Lucas Anderson", "Charlotte Liu", "Alexander Taylor", "Amelia Patel", "Daniel Garcia", "Sophia Kim" };
                var accountHolderName = accountHolderNames[random.Next(0, accountHolderNames.Length)];
                return accountHolderName;
            }
            static string GenerateRandomAccountType()
            {
                string[] accountTypes = { "Savings", "Checking", "Money Market", "Certificate of Deposit", "Retirement" };
                return accountTypes[random.Next(0, accountTypes.Length)];
            }
            static DateTime GenerateRandomDateOpened()
            {
                DateTime startDate = new DateTime(DateTime.Today.Year - MaxYearsBack, 1, 1);
                int daysRange = (DateTime.Today - startDate).Days;
                DateTime randomDate = startDate.AddDays(random.Next(daysRange));
                if (randomDate.Year == DateTime.Today.Year && randomDate >= DateTime.Today)
                {
                    randomDate = randomDate.AddDays(-1);
                }
                return randomDate;
            }
        }
    }

    ```

1. `Program` クラスのコードのパフォーマンス (または信頼性) を向上するのに役立つ、提案された更新を実装します。

1. 変更によってエラーが発生しないようにするには、続行する前にソリューションをビルドして実行します。

1. Program.cs ファイル内のすべてのコードを選択し、チャット ビューに "reliability" プロンプトを入力します。

1. GitHub Copilot Chat から提供される提案を確認します。

    > [!NOTE]
    > この 4 番目のプロンプトから GitHub Copilot が生成した更新の提案を実装する必要はありませんが、提案を確認する必要があります。

    たとえば、チャット ビューに `@workspace /explain How can I improve exception handling for the selected code?` と入力すると、GitHub Copilot Chat からは、次の応答のような更新が提案されます。

    "Program.cs ファイルでの例外処理を改善するには、次の提案を実装することができます。"**

    *1.特定の例外の種類を使用する: 一般的な例外をキャッチする代わりに、可能な限り特定の例外をキャッチします。"*

    *2.より多くのコンテキストを例外に追加する: デバッグを容易にするために、より多くのコンテキストを例外メッセージに指定します。"*

    *3.例外をログする: 例外をコンソールに出力するだけでなく、追跡可能性を向上するために例外をログすることを検討します。"*

    "例外処理を改善した Program.cs ファイルの改善されたバージョンを次に示します。"**

    ```csharp

    using System;
    using System.Collections.Generic;
    using System.Threading.Tasks;
    namespace BankAccountApp
    {
        class Program
        {
            private static readonly Random random = new Random();
            private const int MaxYearsBack = 10;
            private const int NumberOfAccounts = 20;
            private const int NumberOfTransactions = 100;
            private const double minTransactionAmount = -500.0;
            private const double maxTransactionAmount = 500.0;
            private const double minAccountStart = 200.0;
            private const double maxAccountStart = 1000.0;
            static async Task Main(string[] args)
            {
                List<BankAccount> accounts = await CreateBankAccountsAsync(NumberOfAccounts);
                await SimulateTransactionsAsync(accounts, NumberOfTransactions, minTransactionAmount, maxTransactionAmount);
                await SimulateTransfersAsync(accounts, NumberOfTransactions, minTransactionAmount, maxTransactionAmount);
            }
            static async Task<List<BankAccount>> CreateBankAccountsAsync(int numberOfAccounts)
            {
                List<BankAccount> accounts = new List<BankAccount>();
                int createdAccounts = 0;
                while (createdAccounts < numberOfAccounts)
                {
                    try
                    {
                        double initialBalance = GenerateRandomDollarAmount(true, minAccountStart, maxAccountStart);
                        string accountHolderName = GenerateRandomAccountHolder();
                        string accountType = GenerateRandomAccountType();
                        DateTime dateOpened = GenerateRandomDateOpened();
                        BankAccount account = new BankAccount($"Account {createdAccounts + 1}", initialBalance, accountHolderName, accountType, dateOpened);
                        accounts.Add(account);
                        createdAccounts++;
                    }
                    catch (ArgumentException ex)
                    {
                        Console.WriteLine($"Account creation failed due to invalid argument: {ex.Message}");
                    }
                    catch (Exception ex)
                    {
                        Console.WriteLine($"Account creation failed: {ex.Message}");
                    }
                    await Task.Yield(); // Yield control to allow other tasks to run
                }
                return accounts;
            }
            static async Task SimulateTransactionsAsync(List<BankAccount> accounts, int numberOfTransactions, double minTransactionAmount, double maxTransactionAmount)
            {
                List<Task> tasks = new List<Task>();
                foreach (BankAccount account in accounts)
                {
                    tasks.Add(Task.Run(async () =>
                    {
                        for (int i = 0; i < numberOfTransactions; i++)
                        {
                            double transactionAmount = GenerateRandomDollarAmount(false, minTransactionAmount, maxTransactionAmount);
                            try
                            {
                                if (transactionAmount >= 0)
                                {
                                    account.Credit(transactionAmount);
                                    Console.WriteLine($"Credit: {transactionAmount}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                                }
                                else
                                {
                                    account.Debit(-transactionAmount);
                                    Console.WriteLine($"Debit: {transactionAmount}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                                }
                            }
                            catch (ArgumentException ex)
                            {
                                Console.WriteLine($"Transaction failed due to invalid argument: {ex.Message}");
                            }
                            catch (InsufficientBalanceException ex)
                            {
                                Console.WriteLine($"Transaction failed due to insufficient balance: {ex.Message}");
                            }
                            catch (Exception ex)
                            {
                                Console.WriteLine($"Transaction failed: {ex.Message}");
                            }
                            await Task.Yield(); // Yield control to allow other tasks to run
                        }
                        Console.WriteLine($"Account: {account.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                    }));
                }
                await Task.WhenAll(tasks);
            }
            static async Task SimulateTransfersAsync(List<BankAccount> accounts, int numberOfTransactions, double minTransactionAmount, double maxTransactionAmount)
            {
                List<Task> tasks = new List<Task>();
                foreach (BankAccount account in accounts)
                {
                    tasks.Add(Task.Run(async () =>
                    {
                        for (int i = 0; i < numberOfTransactions; i++)
                        {
                            double transactionAmount = GenerateRandomDollarAmount(false, minTransactionAmount, maxTransactionAmount);
                            try
                            {
                                if (transactionAmount >= 0)
                                {
                                    account.Credit(transactionAmount);
                                    Console.WriteLine($"Credit: {transactionAmount}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                                }
                                else
                                {
                                    account.Debit(-transactionAmount);
                                    Console.WriteLine($"Debit: {transactionAmount}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                                }
                            }
                            catch (ArgumentException ex)
                            {
                                Console.WriteLine($"Transaction failed due to invalid argument: {ex.Message}");
                            }
                            catch (InsufficientBalanceException ex)
                            {
                                Console.WriteLine($"Transaction failed due to insufficient balance: {ex.Message}");
                            }
                            catch (Exception ex)
                            {
                                Console.WriteLine($"Transaction failed: {ex.Message}");
                            }
                            await Task.Yield(); // Yield control to allow other tasks to run
                        }
                        Console.WriteLine($"Account: {account.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                    }));
                }
                await Task.WhenAll(tasks);
            }
            static double GenerateRandomDollarAmount(bool isAccount, double min, double max)
            {
                if (isAccount)
                {
                    double accountStartingValue = random.NextDouble() * (max - min) + min;
                    return Math.Round(accountStartingValue, 2);
                }
                else
                {
                    double transactionAmount = random.NextDouble() * random.Next((int)min, (int)max) + random.NextDouble();
                    return Math.Round(transactionAmount, 2);
                }
            }
            static string GenerateRandomAccountHolder()
            {
                string[] accountHolderNames = { "John Smith", "Maria Garcia", "Mohammed Khan", "Sophie Dubois", "Liam Johnson", "Emma Martinez", "Noah Lee", "Olivia Kim", "William Chen", "Ava Wang", "James Brown", "Isabella Nguyen", "Benjamin Wilson", "Mia Li", "Lucas Anderson", "Charlotte Liu", "Alexander Taylor", "Amelia Patel", "Daniel Garcia", "Sophia Kim" };
                var accountHolderName = accountHolderNames[random.Next(0, accountHolderNames.Length)];
                return accountHolderName;
            }
            static string GenerateRandomAccountType()
            {
                string[] accountTypes = { "Savings", "Checking", "Money Market", "Certificate of Deposit", "Retirement" };
                return accountTypes[random.Next(0, accountTypes.Length)];
            }
            static DateTime GenerateRandomDateOpened()
            {
                DateTime startDate = new DateTime(DateTime.Today.Year - MaxYearsBack, 1, 1);
                int daysRange = (DateTime.Today - startDate).Days;
                DateTime randomDate = startDate.AddDays(random.Next(daysRange));
                if (randomDate.Year == DateTime.Today.Year && randomDate >= DateTime.Today)
                {
                    randomDate = randomDate.AddDays(-1);
                }
                return randomDate;
            }
        }
    }

    ```

## まとめ

このデモでは、GitHub Copilot Chat を使用して、サンプル アプリケーションのコードの信頼性とパフォーマンスの向上に役立つ提案を生成します。 GitHub Copilot に例外処理の改善、予期しない問題の削減、単体テストのサポートの改善などを提案するプロンプトを開発しました。 また、非同期タスクやメソッドを使用してパフォーマンスを向上させることに焦点を当てたプロンプトも作成しました。
