---
demo:
  title: 'デモ:GitHub Copilot Chat を使用してコードのセキュリティを改善する'
  module: 'Module 5: Implement code improvements using GitHub Copilot tools'
---

# デモ:GitHub Copilot Chat を使用してコードのセキュリティを改善する

## 手順

デモのアクティビティは、次のリソースを含む環境向けに設計されています。

- Visual Studio Code。
- Visual Studio Code 用の C# 開発キット拡張機能。
- Visual Studio Code 用の GitHub Copilot および GitHub Copilot Chat 拡張機能。 GitHub Copilot のアクティブなサブスクリプションを持つ GitHub アカウントが必要です。
- C# を使用して作成されたサンプル コード プロジェクト。

**注**:デモには講師自身の GitHub アカウントと GitHub Copilot サブスクリプションを使用することを検討するようにお勧めします。 そうすると開発環境を制御およびカスタマイズできるようになります。 また、クラスルームの必要に合わせてデモを簡単に調整できます。

**重要**:講師の PC ではなく、ホストされたラボ環境でデモを実行することを選択した場合は、ホストされた環境でサンプル アプリを解凍できます。 デモを実行する前に、ホストされた環境で GitHub Copilot 拡張機能を構成する必要があります。 ホストされた環境はローカル環境よりも遅い場合があるため、それに応じてデモのペースを調整することが必要になる場合があります。

### デモを紹介する

コード セキュリティとは、不正アクセス、データ侵害、その他のセキュリティ上の脅威からソフトウェアを保護するために実行する対策を指します。 コード セキュリティは、セキュリティ上の脅威からアプリケーションとシステムを保護する、ソフトウェア開発の重要な側面です。 コード セキュリティを強化すると、アプリケーションとシステムをセキュリティ上の脅威から保護するのに役立ちます。

> [!IMPORTANT]
> このデモが安全なコードを開発するためのベスト プラクティスを示すものではないことを学生に説明します。 そうではなく、GitHub Copilot Chat を使用して、サンプル アプリケーションのコード セキュリティを向上するための提案を示すことに焦点を当てています。 提案は、安全なコードを開発するためのベスト プラクティスや包括的なソリューションを表すものではありません。 開発者は、自身の判断と専門知識を使用して、GitHub Copilot Chat から提供される提案を評価し、実装する必要があります。 GitHub Copilot から提示された提案を実装したとしても、徹底的なコードの確認やテストが必要であることに変わりはありません。

#### コードセキュリティ

コード セキュリティの確保は、開発者だけでなく、すべてのユーザーの責任です。 ただし、重要な役割を果たすのは、安全なコーディング プラクティスに確実に従ってコードを記述する開発者です。 安全なコーディング プラクティスは、ソフトウェアの脆弱性が攻撃者によって悪用されないようにするのに役立ちます。 開発者は、安全なコーディング プラクティスに従うことで、ソフトウェアをセキュリティ上の脅威から保護し、安全性と信頼性を確保します。

以下のセクションでは、学生が知っておくべきコード セキュリティ プロセスの概要について説明します。

##### 包括的なアプローチを使用してコード セキュリティを評価する

コード セキュリティを評価するときは、ソフトウェア開発ライフサイクルのさまざまな側面を網羅した包括的なアプローチを検討することが重要です。 次にいくつかの主な考慮事項を示します。

- 安全なコーディング プラクティス:安全なコーディングの標準とガイドラインに従って脆弱性を防ぐ。
- コード分析ツール:静的および動的なコード分析ツールを使用して、セキュリティ上の欠陥を検出する。
- 依存関係の管理:サードパーティのライブラリと依存関係が最新状態になっており、既知の脆弱性がないことを確認する。
- 認証と承認:堅牢な認証と承認のメカニズムを実装して、不正アクセスから保護する。
- データ保護:保存されている機密データと転送中の機密データを両方とも暗号化して、データ侵害を防ぐ。
- エラー処理:機密情報を公開しない安全なエラー処理手順を作成する。
- セキュリティ テスト:侵入テストや脆弱性評価など、徹底的なセキュリティ テストを実施する。
- コンプライアンス:コードが、関連するセキュリティの標準や規制に準拠していることを確認する。
- 教育とトレーニング:開発者に継続的なセキュリティ教育とトレーニングを提供し、最新の脅威とベスト プラクティスに関する情報を提供する。
- インシデント応答:明確に定義されたインシデント応答計画を準備する。 セキュリティ侵害が発生した場合は、インシデント応答計画にアクセスできる必要があります。

これらの要素を考慮し、セキュリティのベスト プラクティスを開発プロセスに統合することが、安全なコンテンツとアプリケーションの作成に寄与します。

##### コード セキュリティ レビューの実施

コードが安全であることを確認する際、開発者はコードの次の側面を確認する必要があります。

- 正確さ:セキュリティの脆弱性につながる可能性のある論理的なエラーや欠陥がコードにないことを確認します。
- セキュリティ:コードがセキュリティのベスト プラクティスに準拠し、脆弱性が含まれていないことを確認します。
- 診断:適切なログ記録と診断の機能を組み込んで、セキュリティ インシデントを検出し、対応します。
- 設計エラーまたは制限事項:コードの設計を確認して、悪用される可能性のある欠陥や制限がないことを確認します。
- スケーラビリティとパフォーマンス:コードのパフォーマンスとスケーラビリティを考慮します。 パフォーマンスとスケーラビリティが低いと、負荷の高いシナリオでセキュリティに影響が及ぶ可能性があります。
- ローカライズ:コードがさまざまなロケールを安全に処理していることを確認します。これは、データの書式設定と表現に影響を与える可能性があります。
- アクセシビリティ (UX):セキュリティ対策がアクセシビリティとユーザー エクスペリエンスに悪影響を与えないことを確認します。
- テスト:テスト戦略を確認し、セキュリティ テストがコードのあらゆる側面を隅々まで網羅していることを確認します。
- インストルメンテーション:コードが、セキュリティ監視と脅威検出に対応するようにインストルメント化されていることを確認します。
- 一貫性とコード スタイルの規則:安全なコーディングのガイドラインと標準に準拠した、一貫したコーディング スタイルを維持します。

開発者がコードのこれらの側面を確認すると、コードのセキュリティを大幅に強化できます。 コードのレビューは、開発者が開発するソフトウェアの全体的なセキュリティ体制を支えるのに役立ちます。

##### コードの脆弱性の分析

アプリケーションの特定の部分はセキュリティ攻撃に対して脆弱であり、これらの領域のセキュリティ保護に重点を置くことが重要です。 脆弱性が高い領域の一部を次に示します。

- 統合ポイント:依存関係のある製品チームとの統合ポイントについて、セキュリティ設計のレビューを実施する必要があります。 レビューは、ビジネスへの影響が大きい (HBI) データを処理する製品や、エンタープライズのアプリケーションとサービスに不可欠です。
- 内部システム:内部インシデントは、特に中小企業におけるセキュリティ侵害の一般的な原因です。
- メール システム:メール サーバー、特にサポート対象外のメール サーバーやパッチが適用されていないメール サーバーは常に脆弱です。
- データベースとストレージ:機密データが保存前に暗号化されることを想定しているデータベースは、データが想定どおりに暗号化されていないと脆弱になる可能性があります。
- ランタイム環境: Runtime Application Self-Protection (RASP) などのテクノロジは、アプリケーションに対する攻撃をリアルタイムで検出でき、ランタイム環境をセキュリティ保護するべき重要な領域にします。
- Web アプリケーション:Web アプリケーションは、多くの場合、SQL インジェクション、クロスサイト スクリプティング (XSS)、バッファー オーバーフローなどの方法を使用して攻撃者によって標的にされます。
- エンドポイント:デバイスとアプリケーションは、サイバー攻撃の危険にさらされます。 ランサムウェアの軽減、アプリケーション制御、Web 保護、ネットワーク ファイアウォールなどの機能を使用して、攻撃対象領域を減らすことが不可欠です。

開発者とセキュリティ チームは、これらの領域に優先順位を付け、潜在的な攻撃から保護するための強力なセキュリティ対策を実装する必要があります。 定期的なセキュリティのレビューと更新、ベスト プラクティスへの準拠は、これらの脆弱性の軽減に役立ちます。

##### 一般的なセキュリティ上の欠陥の調査

開発者は、さまざまなセキュリティ上の欠陥をコード内で見つける場合があり、これらを適切に対処しないと脆弱性につながる可能性があります。 一般的なセキュリティ上の欠陥には、次のようなものがあります。

- インジェクションの欠陥:SQL、NoSQL、OS、LDAP インジェクションなど、信頼されていないデータがコマンドまたはクエリの一部としてインタープリターに送信されます。
- 認証の不備:認証とセッション管理が正しく実装されていないと、認証が正しく行われない可能性があります。 適切な実装により、パスワード、キー、セッション トークンが攻撃者によって侵害されないようにすることができます。
- 機密データの露出:機密データの保護が不十分な場合、ネットワーク経由で転送中のデータや、保存されているデータが露出する可能性があります。
- アクセス制御の不備:認証されたユーザーに付与されるアクセスを制御する制限が適切に適用されていません。
- クロスサイト スクリプティング (XSS):アプリケーションが、適切な検証やエスケープを行わずに、信頼されていないデータを Web ページに組み込むたびに、XSS の欠陥が発生します。
- 安全でない逆シリアル化:これにより、リモート コード実行、リプレイ攻撃、インジェクション攻撃、特権エスカレーション攻撃が発生する可能性があります。
- 不十分なログ記録と監視:ログ記録と監視が不十分で、さらに、インシデント応答との統合が欠落しているか効果的でない場合、継続的な攻撃を許すことになります。
- 安全でない直接オブジェクト参照 (IDOR):アプリケーションが、ユーザー指定の入力に基づいて、オブジェクトへの直接アクセスを提供する場合に発生する、アクセス制御問題の一種です。
- 機能レベルのアクセス制御の欠落:アプリケーションが機能レベルのアクセス制御を適切に保護しないために、攻撃者が適切な認証なしで機能へのアクセス要求を偽造できてしまう場合があります。

他にも多くのセキュリティ上の欠陥がコードで見つかることがあります。 開発者は、ツールとベスト プラクティスを使って、これらの問題を事前に特定して修正することが重要です。

### GitHub Copilot Chat のプロンプトを開発する

GitHub Copilot Chat について記述するプロンプトでは、明確に定義したコンテキストと意図を指定する必要があります。 プロンプトを開発するときは、次の推奨事項を考慮してください。

- 更新するコードよりも高いレベルで範囲を設定する、外側のコンテキストを定義します。 たとえば、メソッドを改善する場合は、そのメソッドを含むクラスまたはファイルを外側のコンテキストとして指定します。 メソッドを内側のコンテキストとして識別します。
- チャット参加者とチャット変数を使用して、コンテキストを指定します。 `#file:` と `#selection` のチャット変数を使用して、焦点を当てる特定のコードを識別できます。 必要に応じて、ワークスペース全体 (`@workspace`) を含めることもできます。 ファイルまたはプロンプトの自然言語部分の選択対象を参照してください。
- 意図は明確かつ簡潔で、具体的である必要があります。 プロンプトでは、達成したい改善点の種類を指定する必要があります。

デモのこの部分では、**APL2007M5BankAccount-Security** プロジェクトを確認し、GitHub Copilot Chat のプロンプトを 3 つ作成します。 プロンプトでは、コード セキュリティの向上に重点を置きます。

次の手順に従って、デモのこの部分を完了します。

1. **APL2007M5BankAccount-Security** プロジェクトを開き、**Program.cs** と **BankAccount.cs** コード ファイルを確認します。

    **Program.cs** ファイルには、銀行口座の作成、トランザクション、転送をシミュレートする単純な銀行アプリケーションのコードが含まれています。

    **BankAccount.cs** ファイルには、預金、出金、残高照会などの基本的な機能を備えた銀行口座を表す、`BankAccount` クラスのコードが含まれています。

1. 少し時間を取って、コードのセキュリティを向上させるために使用できるプロンプトを説明します。

    このプロジェクトでは、次のプロンプトを使用して、コード セキュリティを向上するための提案を生成できます。

    プロンプト: `@workspace /explain How can I implement authentication in the [selected code]?` (チャット コンテキストに BankAccount.cs をアタッチ)

    プロンプト: `@workspace /explain How can I protect sensitive data in the [selected code]?` (チャット コンテキストに BankAccount.cs を添付する)

    プロンプト: `@workspace /explain How can I implement logging of suspicious account activities of the [selected code]?` (チャット コンテキストに BankAccount.cs を添付する)

    プロンプト: `@workspace /explain How can I improve the security of exception handling in the [selected code]?` (チャット コンテキストに BankAccount.cs を添付する)

    プロンプト: `@workspace /explain How can I improve the security of the [selected code]?` (チャット コンテキストに BankAccount.cs を添付する)

    プロンプト: `@workspace /explain How can I improve the security of the [selected code]?` (チャット コンテキストに Program.cs を添付する)

1. デモの残りの部分で使用する 3 つのプロンプトを選択します。

    BankAccount.cs ファイルのセキュリティの問題に対処する 2 つのプロンプトと、Program.cs ファイルの問題に対処する 1 つのプロンプトを選択してください。 このデモでは、BankAccount クラスが "product" を表します。 Program.cs ファイルは、BankAccount クラスを使用して、口座のアクティビティとトランザクションをシミュレートします。

### GitHub Copilot Chat を使用して BankAccount クラスのコード セキュリティを強化する

安全なコードの開発は、どのソフトウェア プロジェクトにも不可欠です。 必要なセキュリティ レベルは、アプリケーションの性質と処理するデータによって異なります。

このデモでは、GitHub Copilot Chat を使用して、**APL2007M5BankAccount-Security** プロジェクトの BankAccount クラスのセキュリティを向上させる提案を生成します。

コード セキュリティを向上するには、GitHub Copilot Chat を使用できます。 プロンプトは、GitHub Copilot に対して、認証、データ保護、ログ記録、その他多数のトピックを改善するための提案を生成するように指示できます。 また、コード セキュリティを向上するための一般的な提案を求める、広範なプロンプトを作成することもできます。 特定のプロンプトと一般的なプロンプトを組み合わせることで、改善が必要な領域を特定し、必要な変更を実装できます。

> [!TIP]
> 推奨される更新プログラムの実装とテストには時間がかかり、このデモでは時間が決め手になる可能性があります。 特定の改善領域に焦点を当てたプロンプトを選択すると、時間を管理するのに役立ちます。 プロンプトが広範囲すぎると、多数の提案が生成されたり、短時間では評価や実装が困難な複雑な提案が生成される場合があります。 開始後に、提案された更新の範囲が広すぎる、または複雑すぎると感じたら、より具体的なプロンプトに更新できます。

1. プロジェクトがビルドされ、エラーなしで実行されることを確認します。

    警告はアプリケーションが実行されている限り許容されますが、エラーは、GitHub Copilot Chat の使用を開始する前に解決する必要があります。

1. Visual Studio Code で BankAccount.cs ファイルを開き、ファイル内のすべてのコードを選択します。

1. チャット ビューを開きます。

1. チャット ビューで、**[コンテキスト添付]** ボタンを使用して関連するファイルをチャット コンテキストに追加し、プロンプトを入力します。

1. GitHub Copilot Chat から提供される提案を確認します。

    たとえば、次のアクションを完了したとします。

    - BankAccount.cs ファイルを開き、すべてのコードを選択します。
    - 次のプロンプトを選択します: `@workspace /explain How can I implement authentication in the BankAccount.cs file?`
    - チャット ビューを開き、BankAccount.cs ファイルと Program.cs ファイルをチャット コンテキストに添付します。
    - チャット ビューにプロンプトを入力します。

    GitHub Copilot Chat から、次の応答のような更新内容が提案されます。

    *通常、このコンテキストで認証を実装する場合は、特定の操作を許可する前に、口座所有者の ID を検証するメソッドを BankAccount クラスに追加します。これは、パスワード、PIN、またはその他の形式の認証を使用して行うことができます。*

    *BankAccount クラスにパスワードベースの認証を追加する方法の簡単な例を次に示します。*

    ```csharp

    public class BankAccount
    {
        // Existing code...
        private string password;
        public BankAccount(string accountNumber, double initialBalance, string accountHolderName, string accountType, DateTime dateOpened, string password)
        {
            // Existing code...
    
            this.password = password;
        }
        public bool Authenticate(string password)
        {
            return this.password == password;
        }
        public void Credit(double amount, string password)
        {
            if (!Authenticate(password))
            {
                throw new Exception("Authentication failed.");
            }
            // Existing code...
        }
        // Similar changes would be made to the Debit, Transfer, and other methods...
    }

    ```

    *この例では、パスワードが BankAccount コンストラクターにパラメーターとして追加され、プライベート フィールドに格納されます。指定されたパスワードが格納されているパスワードと一致するかどうかを確認する Authenticate メソッドが追加されます。Credit メソッド (および認証を必要とするその他のメソッド) は、操作を実行する前にパスワードを引数として受け取り、Authenticate を呼び出すように変更されます。*

    *これはきわめて基本的な認証形式であり、実際のアプリケーションでは安全性が十分ではありません。実際のアプリケーションでは、パスワードを格納する前にハッシュしてソルト化する必要があり、安全な方法でユーザーからアプリケーションにパスワードを送信する必要があります。また、2 要素認証やその他のより安全な方法の使用を検討することもできます。*

1. `BankAccount` クラスのコード セキュリティを向上するのに役立つ、提案された更新を実装します。

    Program.cs ファイルは、BankAccount クラスに追加されたパスワードと認証を使用するように更新する必要があります。 GitHub Copilot Chat を使用して、Program.cs ファイルを更新するための提案を生成できます。

    1. Program.cs ファイルの内容を選択し、Program.cs ファイルと BankAccount.cs ファイルをチャット コンテキストにアタッチし、チャット ビューに次のプロンプトを入力します。

        ```plaintext
        @workspace /Explain How can I update the Program.cs file to use the password and authentication added to BankAccount.cs?
        ```

    1. GitHub Copilot Chat によって提供される提案を確認し、推奨される更新を実装します。

    1. 変更によってエラーが発生しないようにするには、続行する前にソリューションをビルドして実行します。

        GitHub Copilot を使用して、ビルド プロセス中に特定された問題を解決するための支援とします。

    > [!IMPORTANT]
    > きわめて基本的なこの認証形式は、実際のアプリケーションでは安全性が不十分なことを学生に理解させてください。 実際のアプリケーションでは、パスワードを格納する前にハッシュしてソルト化する必要があり、安全な方法でユーザーからアプリケーションにパスワードを送信する必要があります。 また、2 要素認証やその他のより安全な方法の使用を検討することもできます。

1. 続行する前に、アプリケーションがビルドされて実行されていることを確認します。

1. BankAccount.cs ファイル内のすべてのコードを選択し、チャット ビューに 2 番目のプロンプトを入力します。

1. GitHub Copilot Chat から提供される提案を確認します。

    たとえば、次のアクションを完了したとします。

    - BankAccount.cs ファイルを開き、すべてのコードを選択します。
    - 次のプロンプトを選択します: `@workspace /explain How can I protect account numbers and account holder names in the selected code?`
    - チャット ビューを開き、BankAccount.cs ファイルと Program.cs ファイルをチャット コンテキストに添付します。
    - チャット ビューにプロンプトを入力します。

    GitHub Copilot Chat から、次の応答のような更新内容が提案されます。

    *口座番号や口座名義人名など、BankAccount クラスの機密データを保護するには、次の手順を実行します。*

    *1.カプセル化を使用する:*

    *- 機密性の高いプロパティをプライベートにし、メソッドを使用して制御されたアクセスを提供します。*

    *2.機密データを暗号化する:*

    *- 暗号化を使用して機密データを安全に格納します。*

    *3.プレーンテキストでの格納を避ける:*

    *- 機密データがプレーンテキストで格納されたり送信されたりしないようにします。*

    *更新された実装*:

    *アカウント番号とアカウント所有者名に暗号化を使用する BankAccount.cs の更新バージョンを次に示します。*

    ```csharp

    using System;
    using System.Security.Cryptography;
    using System.Text;
    namespace BankAccountApp
    {
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
        public class InvalidAccountTypeException : Exception
        {
            public string AccountType { get; }
            public InvalidAccountTypeException(string accountType)
                : base($"Invalid account type: {accountType}.")
            {
                AccountType = accountType;
            }
        }
        public class InvalidAccountNumberException : Exception
        {
            public string AccountNumber { get; }
            public InvalidAccountNumberException(string accountNumber)
                : base($"Invalid account number: {accountNumber}.")
            {
                AccountNumber = accountNumber;
            }
        }
        public class InvalidAccountHolderNameException : Exception
        {
            public string AccountHolderName { get; }
            public InvalidAccountHolderNameException(string accountHolderName)
                : base($"Invalid account holder name: {accountHolderName}.")
            {
                AccountHolderName = accountHolderName;
            }
        }
        public class InvalidDateOpenedException : Exception
        {
            public DateTime DateOpened { get; }
            public InvalidDateOpenedException(DateTime dateOpened)
                : base($"Invalid date opened: {dateOpened}.")
            {
                DateOpened = dateOpened;
            }
        }
        public class InvalidInitialBalanceException : Exception
        {
            public double InitialBalance { get; }
            public InvalidInitialBalanceException(double initialBalance)
                : base($"Invalid initial balance: {initialBalance}.")
            {
                InitialBalance = initialBalance;
            }
        }
        public class InvalidInterestRateException : Exception
        {
            public double InterestRate { get; }
            public InvalidInterestRateException(double interestRate)
                : base($"Invalid interest rate: {interestRate}.")
            {
                InterestRate = interestRate;
            }
        }
        public class InvalidTransferAmountException : Exception
        {
            public double TransferAmount { get; }
            public InvalidTransferAmountException(double transferAmount)
                : base($"Invalid transfer amount: {transferAmount}.")
            {
                TransferAmount = transferAmount;
            }
        }
        public class InvalidCreditAmountException : Exception
        {
            public double CreditAmount { get; }
            public InvalidCreditAmountException(double creditAmount)
                : base($"Invalid credit amount: {creditAmount}.")
            {
                CreditAmount = creditAmount;
            }
        }
        public class InvalidDebitAmountException : Exception
        {
            public double DebitAmount { get; }
            public InvalidDebitAmountException(double debitAmount)
                : base($"Invalid debit amount: {debitAmount}.")
            {
                DebitAmount = debitAmount;
            }
        }
        public class AuthenticationException : Exception
        {
            public AuthenticationException(string message) : base(message) { }
        }
        public class BankAccount
        {
            public enum AccountTypes
            {
                Savings,
                Checking,
                MoneyMarket,
                CertificateOfDeposit,
                Retirement
            }
            private string EncryptedAccountNumber { get; }
            private string EncryptedAccountHolderName { get; }
            public double Balance { get; private set; }
            public AccountTypes AccountType { get; }
            public DateTime DateOpened { get; }
            private const double MaxTransferAmountForDifferentOwners = 500;
            private string Username { get; }
            private string Password { get; }
            public BankAccount(string accountNumber, double initialBalance, string accountHolderName, string accountType, DateTime dateOpened, string username, string password)
            {
                if (accountNumber.Length != 10)
                {
                    throw new InvalidAccountNumberException(accountNumber);
                }
                if (initialBalance < 0)
                {
                    throw new InvalidInitialBalanceException(initialBalance);
                }
                if (accountHolderName.Length < 2)
                {
                    throw new InvalidAccountHolderNameException(accountHolderName);
                }
                if (dateOpened > DateTime.Now)
                {
                    throw new InvalidDateOpenedException(dateOpened);
                }
                EncryptedAccountNumber = Encrypt(accountNumber);
                EncryptedAccountHolderName = Encrypt(accountHolderName);
                Balance = initialBalance;
                AccountType = (AccountTypes)Enum.Parse(typeof(AccountTypes), accountType);
                DateOpened = dateOpened;
                Username = username;
                Password = password;
            }
            public void Credit(double amount)
            {
                if (amount < 0)
                {
                    throw new InvalidCreditAmountException(amount);
                }
                Balance += amount;
            }
            public void Debit(double amount)
            {
                if (amount < 0)
                {
                    throw new InvalidDebitAmountException(amount);
                }
                if (Balance >= amount)
                {
                    Balance -= amount;
                }
                else
                {
                    throw new InsufficientFundsException(amount, Balance);
                }
            }
            public double GetBalance()
            {
                return Balance;
            }
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
                if (Decrypt(EncryptedAccountHolderName) != Decrypt(toAccount.EncryptedAccountHolderName) && amount > MaxTransferAmountForDifferentOwners)
                {
                    throw new Exception("Transfer amount exceeds maximum limit for different account owners.");
                }
            }
            public void PrintStatement()
            {
                Console.WriteLine($"Account Number: {Decrypt(EncryptedAccountNumber)}, Balance: {Balance}");
            }
            public double CalculateInterest(double interestRate)
            {
                if (interestRate < 0)
                {
                    throw new InvalidInterestRateException(interestRate);
                }
                return Balance * interestRate;
            }
            public void Authenticate(string username, string password)
            {
                if (Username != username || Password != password)
                {
                    throw new AuthenticationException("Invalid username or password.");
                }
            }
            private string Encrypt(string plainText)
            {
                using (Aes aes = Aes.Create())
                {
                    aes.Key = Encoding.UTF8.GetBytes("A very strong key"); // Use a secure key
                    aes.IV = Encoding.UTF8.GetBytes("A strong IV123456"); // Use a secure IV
                    ICryptoTransform encryptor = aes.CreateEncryptor(aes.Key, aes.IV);
                    using (var ms = new System.IO.MemoryStream())
                    {
                        using (var cs = new CryptoStream(ms, encryptor, CryptoStreamMode.Write))
                        {
                            using (var sw = new System.IO.StreamWriter(cs))
                            {
                                sw.Write(plainText);
                            }
                        }
                        return Convert.ToBase64String(ms.ToArray());
                    }
                }
            }
            private string Decrypt(string cipherText)
            {
                using (Aes aes = Aes.Create())
                {
                    aes.Key = Encoding.UTF8.GetBytes("A very strong key"); // Use a secure key
                    aes.IV = Encoding.UTF8.GetBytes("A strong IV123456"); // Use a secure IV
                    ICryptoTransform decryptor = aes.CreateDecryptor(aes.Key, aes.IV);
                    using (var ms = new System.IO.MemoryStream(Convert.FromBase64String(cipherText)))
                    {
                        using (var cs = new CryptoStream(ms, decryptor, CryptoStreamMode.Read))
                        {
                            using (var sr = new System.IO.StreamReader(cs))
                            {
                                return sr.ReadToEnd();
                            }
                        }
                    }
                }
            }
        }
    }

    ```

    *使用法:*

    *- 必要な暗号化ライブラリが使用可能であることを確認します。上の例では、簡明さを目的としてハードコーディングされたキーと IV を使用した AES 暗号化を使用しています。実際のアプリケーションでは、キーと IV を安全に管理する必要があります (一例としてはキー管理サービスを使用するなど)。*

    > [!IMPORTANT]
    > 実際のアプリケーションでは、キーと IV を安全に管理する必要があります (一例としてはキー管理サービスを使用するなど)。 このトレーニングで提供される例では、改善の余地のある点を特定していますが、セキュリティで保護された暗号化のベスト プラクティスを表すものではありません。 GitHub Copilot Chat を使用して、アプリケーションの暗号化とデータ保護を改善するためのさらなる提案を求めることができます。

1. 2 番目のプロンプトで推奨される更新を実装する必要はありません。

    この例では、推奨される更新はアプリケーションのセキュリティを強化するのに役立ちますが、それには Program.cs コードに対する相当な構成と更新が必要となります。これは、このデモの対象範囲ではありません。

### GitHub Copilot Chat を使用して Program クラスのコード セキュリティを強化する

1. Visual Studio Code で Program.cs ファイルを開き、ファイル内のすべてのコードを選択します。

1. チャット ビューを開き、Program クラス用に準備した最初のプロンプトを入力します。

1. GitHub Copilot Chat から提供される提案を確認します。

    たとえば、次のアクションを完了したとします。

    - Program.cs ファイルを開き、すべてのコードを選択します。
    - 次のプロンプトを選択します: `@workspace /explain How can I improve the security of the Program.cs file?`
    - チャット ビューを開き、BankAccount.cs ファイルと Program.cs ファイルをチャット コンテキストに添付します。
    - チャット ビューにプロンプトを入力します。

    GitHub Copilot Chat から、次の応答のような更新内容が提案されます。

    *Program.cs ファイルのセキュリティを強化するには、次の領域に重点を置く必要があります。*

    *1.パスワードの取り扱いをセキュリティで保護する:*

    *- 安全なパスワード ハッシュを使用し、プレーンテキストでパスワードを格納しないようにします。*
    *- パスワードをハッシュするために BCrypt.Net などのライブラリを使用します。*

    *2.機密データを暗号化する:*

    *- アカウント番号やアカウント所有者名などの機密データを暗号化します。*

    *3.パスワードのハードコーディングは避ける:*

    *- ハードコーディングされたパスワードは使用しないでください。代わりに、強力なランダム パスワードを生成するか、独自のパスワードを作成するようユーザーに求めます。*

    *4.安全な乱数生成を使用する:*

    *- 機密データの生成に暗号論的乱数生成器を使用します。*

    *更新された実装*:

    *次の機能強化が組み込まれた Program.cs の更新バージョンを次に示します。*

    ```csharp

    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Security.Cryptography;
    using System.Text;
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
            static async Task Main()
            {
                List<BankAccount> accounts = CreateBankAccounts(NumberOfAccounts);
                await SimulateTransactionsAsync(accounts, NumberOfTransactions, minTransactionAmount, maxTransactionAmount);
                await SimulateTransfersAsync(accounts, NumberOfTransactions, minTransactionAmount, maxTransactionAmount);
            }
            static List<BankAccount> CreateBankAccounts(int numberOfAccounts)
            {
                List<BankAccount> accounts = new();
                int createdAccounts = 0;
                while (createdAccounts < numberOfAccounts)
                {
                    try
                    {
                        double initialBalance = GenerateRandomDollarAmount(true, minAccountStart, maxAccountStart);
                        string accountHolderName = GenerateRandomAccountHolder();
                        string accountType = GenerateRandomAccountType();
                        DateTime dateOpened = GenerateRandomDateOpened();
                        string accountNumber = "102000" + random.Next(1000, 9999).ToString();
                        string username = "user" + createdAccounts;
                        string password = GenerateSecurePassword();
                        BankAccount account = new(accountNumber, initialBalance, accountHolderName, accountType, dateOpened, username, password);
                        accounts.Add(account);
                        createdAccounts++;
                    }
                    catch (ArgumentException ex)
                    {
                        Console.WriteLine($"Account creation failed due to invalid argument: {ex.Message}");
                        // Log the exception
                    }
                    catch (Exception ex)
                    {
                        Console.WriteLine($"Account creation failed: {ex.Message}");
                        // Log the exception
                    }
                    finally
                    {
                        // Any cleanup code would go here.
                    }
                }
                return accounts;
            }
            static async Task SimulateTransactionsAsync(List<BankAccount> accounts, int numberOfTransactions, double minTransactionAmount, double maxTransactionAmount)
            {
                var tasks = accounts.Select(async account =>
                {
                    for (int i = 0; i < numberOfTransactions; i++)
                    {
                        double transactionAmount = GenerateRandomDollarAmount(false, minTransactionAmount, maxTransactionAmount);
                        try
                        {
                            account.Authenticate(account.Username, account.Password); // Authenticate before transaction
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
                    }
                    Console.WriteLine($"Account: {account.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                });
                await Task.WhenAll(tasks);
            }
            static async Task SimulateTransfersAsync(List<BankAccount> accounts, int numberOfTransactions, double minTransactionAmount, double maxTransactionAmount)
            {
                var tasks = accounts.Select(async account =>
                {
                    for (int i = 0; i < numberOfTransactions; i++)
                    {
                        double transactionAmount = GenerateRandomDollarAmount(false, minTransactionAmount, maxTransactionAmount);
                        try
                        {
                            account.Authenticate(account.Username, account.Password); // Authenticate before transfer
                            BankAccount toAccount = accounts[random.Next(accounts.Count)];
                            toAccount.Authenticate(toAccount.Username, toAccount.Password); // Authenticate target account
                            account.Transfer(toAccount, transactionAmount);
                            Console.WriteLine($"Transfer: {transactionAmount}, From: {account.AccountNumber}, To: {toAccount.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                        }
                        catch (Exception ex)
                        {
                            Console.WriteLine($"Transfer failed: {ex.Message}");
                        }
                    }
                    Console.WriteLine($"Account: {account.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                });
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
                DateTime startDate = new(DateTime.Today.Year - MaxYearsBack, 1, 1);
                int daysRange = (DateTime.Today - startDate).Days;
                DateTime randomDate = startDate.AddDays(random.Next(daysRange));
                if (randomDate.Year == DateTime.Today.Year && randomDate >= DateTime.Today)
                {
                    randomDate = randomDate.AddDays(-1);
                }
                return randomDate;
            }
            static string GenerateSecurePassword()
            {
                const int passwordLength = 12;
                const string validChars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890!@#$%^&*()";
                StringBuilder password = new StringBuilder();
                using (RNGCryptoServiceProvider rng = new RNGCryptoServiceProvider())
                {
                    byte[] uintBuffer = new byte[sizeof(uint)];
                    while (passwordLength > password.Length)
                    {
                        rng.GetBytes(uintBuffer);
                        uint num = BitConverter.ToUInt32(uintBuffer, 0);
                        password.Append(validChars[(int)(num % (uint)validChars.Length)]);
                    }
                }
                return password.ToString();
            }
        }
    }

    ```

1. この Program.cs の更新は、安全な乱数の生成に焦点を当てていることに注意してください。

    別の提案は BankAccount クラスに適用されるものです。その実装はこのトレーニングの対象範囲ではありません。

1. 安全な例外処理を目的とする Program.cs の追加のプロンプトを作成します。

1. GitHub Copilot Chat から提供される提案を確認します。

    たとえば、[チャット] ビューに `@workspace /explain How can I implement secure exception handling in the Program.cs file?` と入力すると、GitHub Copilot Chat からは、次の応答のような更新が提案されます。

    *Program.cs ファイルに安全な例外処理を実装するには、次のベスト プラクティスに従う必要があります。*

    *1.具体的な例外をキャッチする:*

    *- 一般的な catch (Exception ex) ブロックを使用するのではなく、具体的な例外をキャッチします。これは、さまざまな種類のエラーを適切に解釈して処理するのに役立ちます。*

    *2.例外を安全にログに記録する:*

    *- 機密情報を公開することなく、例外を安全にログに記録します。ログ記録フレームワークを使用してログを管理します。*

    *3.わかりやすいメッセージを提供する:*

    *- 内部的な詳細を明らかにすることなく、わかりやすいエラー メッセージを提供します。*

    *4.finally ブロックをクリーンアップに使用する:*

    *- 例外がスローされたかどうかに関係なく、finally ブロックを使用して、必要なクリーンアップが確実に実行されるようにします。*

    *5.クリティカルでない例外のキャッチを避ける:*

    *- OutOfMemoryException や StackOverflowException など、伝達を許可するべき例外をキャッチしないようにします。*

    *安全な例外処理を備えた Program.cs の更新バージョンを次に示します。*

    ```csharp

    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Security.Cryptography;
    using System.Text;
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
            static async Task Main()
            {
                List<BankAccount> accounts = CreateBankAccounts(NumberOfAccounts);
                await SimulateTransactionsAsync(accounts, NumberOfTransactions, minTransactionAmount, maxTransactionAmount);
                await SimulateTransfersAsync(accounts, NumberOfTransactions, minTransactionAmount, maxTransactionAmount);
            }
            static List<BankAccount> CreateBankAccounts(int numberOfAccounts)
            {
                List<BankAccount> accounts = new();
                int createdAccounts = 0;
                while (createdAccounts < numberOfAccounts)
                {
                    try
                    {
                        double initialBalance = GenerateRandomDollarAmount(true, minAccountStart, maxAccountStart);
                        string accountHolderName = GenerateRandomAccountHolder();
                        string accountType = GenerateRandomAccountType();
                        DateTime dateOpened = GenerateRandomDateOpened();
                        string accountNumber = "102000" + random.Next(1000, 9999).ToString();
                        string username = "user" + createdAccounts;
                        string password = GenerateSecurePassword();
                        BankAccount account = new(accountNumber, initialBalance, accountHolderName, accountType, dateOpened, username, password);
                        accounts.Add(account);
                        createdAccounts++;
                    }
                    catch (ArgumentException ex)
                    {
                        Console.WriteLine($"Account creation failed due to invalid argument: {ex.Message}");
                        // Log the exception securely
                        LogException(ex);
                    }
                    catch (Exception ex)
                    {
                        Console.WriteLine($"Account creation failed: {ex.Message}");
                        // Log the exception securely
                        LogException(ex);
                    }
                    finally
                    {
                        // Any cleanup code would go here.
                    }
                }
                return accounts;
            }
            static async Task SimulateTransactionsAsync(List<BankAccount> accounts, int numberOfTransactions, double minTransactionAmount, double maxTransactionAmount)
            {
                var tasks = accounts.Select(async account =>
                {
                    for (int i = 0; i < numberOfTransactions; i++)
                    {
                        double transactionAmount = GenerateRandomDollarAmount(false, minTransactionAmount, maxTransactionAmount);
                        try
                        {
                            account.Authenticate(account.Username, account.Password); // Authenticate before transaction
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
                        catch (InvalidCreditAmountException ex)
                        {
                            Console.WriteLine($"Invalid credit amount: {ex.Message}");
                            LogException(ex);
                        }
                        catch (InvalidDebitAmountException ex)
                        {
                            Console.WriteLine($"Invalid debit amount: {ex.Message}");
                            LogException(ex);
                        }
                        catch (InsufficientFundsException ex)
                        {
                            Console.WriteLine($"Insufficient funds: {ex.Message}");
                            LogException(ex);
                        }
                        catch (AuthenticationException ex)
                        {
                            Console.WriteLine($"Authentication failed: {ex.Message}");
                            LogException(ex);
                        }
                        catch (Exception ex)
                        {
                            Console.WriteLine($"Transaction failed: {ex.Message}");
                            LogException(ex);
                        }
                    }
                    Console.WriteLine($"Account: {account.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                });
                await Task.WhenAll(tasks);
            }
            static async Task SimulateTransfersAsync(List<BankAccount> accounts, int numberOfTransactions, double minTransactionAmount, double maxTransactionAmount)
            {
                var tasks = accounts.Select(async account =>
                {
                    for (int i = 0; i < numberOfTransactions; i++)
                    {
                        double transactionAmount = GenerateRandomDollarAmount(false, minTransactionAmount, maxTransactionAmount);
                        try
                        {
                            account.Authenticate(account.Username, account.Password); // Authenticate before transfer
                            BankAccount toAccount = accounts[random.Next(accounts.Count)];
                            toAccount.Authenticate(toAccount.Username, toAccount.Password); // Authenticate target account
                            account.Transfer(toAccount, transactionAmount);
                            Console.WriteLine($"Transfer: {transactionAmount}, From: {account.AccountNumber}, To: {toAccount.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                        }
                        catch (InvalidTransferAmountException ex)
                        {
                            Console.WriteLine($"Invalid transfer amount: {ex.Message}");
                            LogException(ex);
                        }
                        catch (InsufficientFundsException ex)
                        {
                            Console.WriteLine($"Insufficient funds: {ex.Message}");
                            LogException(ex);
                        }
                        catch (AuthenticationException ex)
                        {
                            Console.WriteLine($"Authentication failed: {ex.Message}");
                            LogException(ex);
                        }
                        catch (Exception ex)
                        {
                            Console.WriteLine($"Transfer failed: {ex.Message}");
                            LogException(ex);
                        }
                    }
                    Console.WriteLine($"Account: {account.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                });
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
                DateTime startDate = new(DateTime.Today.Year - MaxYearsBack, 1, 1);
                int daysRange = (DateTime.Today - startDate).Days;
                DateTime randomDate = startDate.AddDays(random.Next(daysRange));
                if (randomDate.Year == DateTime.Today.Year && randomDate >= DateTime.Today)
                {
                    randomDate = randomDate.AddDays(-1);
                }
                return randomDate;
            }
            static string GenerateSecurePassword()
            {
                const int passwordLength = 12;
                const string validChars = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ1234567890!@#$%^&*()";
                StringBuilder password = new StringBuilder();
                using (RNGCryptoServiceProvider rng = new RNGCryptoServiceProvider())
                {
                    byte[] uintBuffer = new byte[sizeof(uint)];
                    while (passwordLength > password.Length)
                    {
                        rng.GetBytes(uintBuffer);
                        uint num = BitConverter.ToUInt32(uintBuffer, 0);
                        password.Append(validChars[(int)(num % (uint)validChars.Length)]);
                    }
                }
                return password.ToString();
            }
            static void LogException(Exception ex)
            {
                // Implement a secure logging mechanism here
                // For example, log to a file, database, or external logging service
                Console.WriteLine($"Logged exception: {ex.Message}");
            }
        }
    }

    ```

1. `Program.cs` ファイルのコード セキュリティを向上するのに役立つ、提案された更新を実装します。

1. 変更によってエラーが発生しないようにするには、ソリューションをビルドして実行します。

## まとめ

このデモでは、GitHub Copilot Chat を使用して、サンプル アプリケーションのコード セキュリティを向上させる提案を生成しました。 認証、データ保護、ログ記録、その他のセキュリティ関連のトピックを改善するための提案を提供するように GitHub Copilot に指示するプロンプトを開発しました。 **APL2007M5BankAccount-Security** プロジェクトで BankAccount クラスと Program クラスのセキュリティを向上するために、提案された更新を実装しました。
