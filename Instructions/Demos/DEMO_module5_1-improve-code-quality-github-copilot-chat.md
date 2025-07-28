---
demo:
  title: 'デモ:GitHub Copilot Chat を使用してコードの品質を向上させる'
  module: 'Module 5: Implement code improvements using GitHub Copilot tools'
---

# デモ:GitHub Copilot Chat を使用してコードの品質を向上させる

## 手順

デモのアクティビティは、次のリソースを含む環境向けに設計されています。

- Visual Studio Code。
- Visual Studio Code 用の C# 開発キット拡張機能。
- Visual Studio Code 用の GitHub Copilot および GitHub Copilot Chat 拡張機能。 GitHub Copilot のアクティブなサブスクリプションを持つ GitHub アカウントが必要です。
- C# を使用して作成されたサンプル コード プロジェクト。

**注**:デモには講師自身の GitHub アカウントと GitHub Copilot サブスクリプションを使用することを検討するようにお勧めします。 そうすると開発環境を制御およびカスタマイズできるようになります。 また、クラスルームの必要に合わせてデモを簡単に調整できます。

**重要**:講師の PC ではなく、ホストされたラボ環境でデモを実行することを選択した場合は、ホストされた環境でサンプル アプリを解凍できます。 デモを実行する前に、ホストされた環境で GitHub Copilot 拡張機能を構成する必要があります。 ホストされた環境はローカル環境よりも遅い場合があるため、それに応じてデモのペースを調整することが必要になる場合があります。

### デモを紹介する

"コード品質" という用語は、読みやすさ、保守容易性、モジュール性など、コードベースの全体的な品質を指します。 コード品質は、コードがどのように "適切に構造化" されており、コードをどれだけ簡単に理解、保守、拡張できるかを測る尺度です。

> [!IMPORTANT]
> このデモが高品質のコードを開発するためのベスト プラクティスを示すものではないことを学生に説明します。 そうではなく、GitHub Copilot Chat を使用して、サンプル アプリケーションのコード品質を向上するための提案を示すことに焦点を当てています。 提案は、高品質のコードを開発するためのベスト プラクティスや包括的なソリューションを表すものではありません。 開発者は、自身の判断と専門知識を使用して、GitHub Copilot Chat から提供される提案を評価し、実装する必要があります。 GitHub Copilot から提示された提案を実装したとしても、徹底的なコードの確認やテストが必要であることに変わりはありません。

以下のセクションでは、学生が知っておくべきコード リファクタリングとコード品質の概要について説明します。

#### コード リファクタリングと高品質のコード

コード リファクタリングは、外部の動作を変更せずに既存のコードを再構築するプロセスです。 コード リファクタリングの目的は、コードベースの内部構造を改善し、理解、保守、拡張を容易にすることです。 コード リファクタリングは、読みやすさを高め、複雑さを軽減し、モジュール性を向上し、再利用性を高めることで、高品質のコードを生成するのに役立ちます。 これらの各要素は、管理しやすく保守しやすいコードベースを作成するのに役立ちます。

開発者は、コード品質の向上に取り組むときに、次の要素を考慮する必要があります。

- 読みやすさ:コードの読みやすさを向上または強化すると、開発者が理解しやすくなります。
- 複雑さ:コードの複雑さを軽減すると、コードの理解、管理、保守が容易になります。
- モジュール性と再利用性:コードを再利用可能な小さいモジュールまたはコンポーネントに分割すると、コードの管理と保守が容易になります。

上記の要素は、開発者がコード品質について検討するときに特定する 3 つの一般的な領域を表しています。 コード品質に関連付けることができるその他の要素は次のとおりです。

- テスト容易性:コードをテストして正常に動作することを確認することが簡単に行えること。 多くの場合、これは、優れた設計とモジュール性によって得られます。
- 拡張性:新しい機能を追加するためのコードの拡張や強化を簡単に行えること。 多くの場合、これは、優れた設計とモジュール性によって得られます。

コードの確認中に開発者が考慮する要素は、コード品質だけではありません。 コード品質に加えて、開発者がよく評価するその他の要因を次にいくつか示します。

- 信頼性:コードが、指定された条件下で目的の機能を実行できること。
- パフォーマンス：コードがどの程度効率的に実行できるか。
- セキュリティ:コードが、不正なアクセスや改ざんからデータやリソースを保護できること。
- スケーラビリティ: コードが、今後増加するワークロードや規模の拡張に対応できること。
- 使いやすさ:開発者またはエンド ユーザーがコードを簡単に使用できること。
- 移植性:コードが、さまざまなプラットフォームまたは環境で実行できること。

> [!NOTE]
> このモジュールの次の 2 つのユニットでは、GitHub Copilot Chat を使用して、コードの信頼性、パフォーマンス、セキュリティを向上する方法について説明します。

多くの場合、コード品質の向上は、新機能や機能拡張を追加する前に行われるものと考えられています。 コードの信頼性、パフォーマンス、またはセキュリティに取り組む前に、コード品質の向上を検討する必要があります。

このデモでは、GitHub Copilot Chat を使用して、サンプル アプリケーションのコード品質の向上に役立つ提案を生成します。

### GitHub Copilot Chat のプロンプトを開発する

適切なプロンプトを作成することの重要性を繰り返します。

GitHub Copilot Chat について記述するプロンプトでは、明確に定義した*コンテキスト*と*意図*を指定する必要があります。 プロンプトの*意図*の部分は、達成したい目標を示します。 たとえば、GitHub Copilot に "コードのモジュール性を向上するようにリファクタリングする" ことを依頼できます。 プロンプトの*コンテキスト*部分は、考慮する必要のあるリソースを GitHub Copilot に知らせます。 たとえば、ワークスペース全体を考慮しつつ、特定のファイルまたはコード セクションに注目するよう GitHub Copilot に伝えル場合があります。 プロンプトを開発するときは、次の推奨事項を考慮してください。

- 更新するコードよりも高いレベルで範囲を設定する、外側のコンテキストを定義します。 たとえば、メソッドをリファクタリングする場合は、そのメソッドを含むクラスまたはファイルを外側のコンテキストとして指定します。 メソッドを内側のコンテキストとして識別します。
- チャット参加者とチャット変数を使用して、コンテキストを指定します。 `#file:` と `#selection` のチャット変数を使用して、焦点を当てる特定のコードを識別できます。 必要に応じて、ワークスペース全体 (`@workspace`) を含めることもできます。 たとえば、特定のファイル内のメソッドをリファクタリングするとします。 `#file:` チャット変数を使用して、どのファイルを対象とするかを GitHub Copilot に指示できます。 エディターでメソッドを選択し、`#selection` チャット変数を使用して、リファクタリングするコードを GitHub Copilot に指示できます。 また、`@workspace` チャット変数を使用して、ワークスペース全体を考慮するように GitHub Copilot に指示することもできます。 プロンプトの自然言語部分の選択対象またはファイルを参照して、指定されたコンテキストを強化します。 たとえば、"選択したコードの読みやすさを向上するにはどうすればよいか" と言うことができます。
- 意図は、明確で具体的であること、そして、改善したいコード品質の側面を示している必要があります。 たとえば、"選択したコードのモジュール性を向上するにはどうすればよいか" と GitHub Copilot Chat に尋ねることができます。

デモのこの部分では、**APL2007M5BankAccount** プロジェクトを確認し、GitHub Copilot Chat のプロンプトを 3 つ作成します。 プロンプトでは、コードの読みやすさ、保守容易性、モジュール性の向上に焦点を当てます。

次の手順に従って、デモのこの部分を完了します。

1. Visual Studio Code で **APL2007M5BankAccount** サンプル アプリを開きます。

1. **Program.cs** ファイルを開き、コードを確認します。

    このプログラムは、銀行システムをシミュレートするコンソール アプリケーションです。 主な機能は次のとおりです。

    - Main メソッド:Main メソッドは、アプリケーションのエントリ ポイントです。 これは、銀行口座を作成し、その口座を使用してトランザクションをシミュレートします。

    - 定数:このプログラムは、Program クラスの先頭にいくつかの定数を定義します。 定数には、作成する口座の数、シミュレートするトランザクションの数、トランザクションの制限などがあります。

1. ここで少しの時間を取って、コードの読みやすさ、保守容易性、モジュール性を向上するために使用できるプロンプトを記述してみましょう。

    BankAccount プロジェクトの場合は、BankAccount.cs ファイルや Program.cs ファイルをチャット コンテキストにアタッチする必要があります。 プロンプトは次の例のようになります。

    プロンプト: `@workspace /explain How can I improve the readability of the [selected code]?`

    プロンプト: `@workspace /explain #selection How can I improve the maintainability of the [selected code]?`

    プロンプト: `@workspace /explainHow can I improve the modularity of the [selected code]?`

    プロンプト: `#selection How can I refactor the [selected code] to improve modularity?`

    プロンプト: `@workspace /explain What are some options for simplifying the [selected code]?`

1. デモの残りの部分で使用する 3 つのプロンプトを作成します。

### GitHub Copilot Chat を使用してコードをリファクタリングする

GitHub Copilot Chat を使用すると、コードをリファクタリングして改善するコード更新を提案できます。 アプリケーションをどのようにリファクタリングするかを決定する前に、コードと目標を理解することが重要です。

GitHub Copilot Chat が提供する提案は、慎重に確認する必要があります。 どの提案が目標の達成に役立つかを、実装する前に検討してください。 このデモでは、どの提案を実装するかを決定する際に時間も考慮する必要があります。

次の手順に従って、デモのこの部分を完了します。

1. ここで少しの時間を取って、Program.cs ファイルに含まれるメソッドを確認してください。

    - CreateBankAccounts メソッド:このメソッドは、指定した数の銀行口座を、ランダムな初期残高、口座所有者名、口座の種類、口座開設日を使用して作成します。 これは、try-catch ブロックを使用して、口座の作成時に発生する可能性のある例外を処理します。

    - SimulateTransactions メソッド:このメソッドは、銀行口座の一覧に対し、指定した数のトランザクションをシミュレートします。 トランザクションごとにランダムなトランザクション金額を生成し、金額が正か負かに応じて、この金額を貸方または借方に記入します。 try-catch ブロックを使用して、トランザクション中に発生する可能性のある例外を処理します。

    - SimulateTransfers メソッド:このメソッドは、SimulateTransactions メソッドと同じです。 口座間の転送をシミュレートすることを目的としているように見えますが、現時点では、個々の口座のトランザクションをシミュレートするだけです。

    - GenerateRandomDollarAmount メソッド:このメソッドは、指定した範囲内でランダムなドルの金額を生成します。 これは、別の数式を使用して、口座残高とトランザクションのどちらに対する金額であるかに応じて金額を生成します。

    - GenerateRandomAccountHolder メソッド:このメソッドは、定義済みの名前の一覧から、ランダムな口座所有者の名前を選択します。

    - GenerateRandomAccountType メソッド:このメソッドは、定義済みの種類の一覧から、ランダムな口座の種類を選択します。

    - GenerateRandomDateOpened メソッド:このメソッドは、現在の日付より前の、指定した年内のランダムな日付を生成します。

1. プロジェクトがビルドされ、エラーなしで実行されることを確認します。

1. 準備したプロンプトから最初のプロンプトを選択します。

1. 改善するコードを選択し、チャット ビューを開きます。

1. チャット ビューで、**[コンテキストのアタッチ]** ボタンを使用して関連するファイルをチャット コンテキストに追加し、プロンプトを入力します。

    ドラッグ アンド ドロップ操作を使用して、ソリューション エクスプローラー ビューからチャット コンテキストにファイルをアタッチする方法を示すこともできます。

1. GitHub Copilot Chat から提供される提案を確認します。

    たとえば、次のアクションを完了したとします。

    - Program.cs ファイルで作業することにします。
    - 次のプロンプトを選択します: `@workspace /explain #selection How can I improve the readability of the GenerateRandomBalance, GenerateRandomAccountHolder, GenerateRandomAccountType, and GenerateRandomDateOpened methods?`
    - Program.cs ファイルを開き、`GenerateRandomBalance`、`GenerateRandomAccountHolder`、`GenerateRandomAccountType`、`GenerateRandomDateOpened` のメソッドを選択します。
    - チャット ビューを開き、Program.cs ファイルをチャット コンテキストにアタッチします。
    - チャット ビューにプロンプトを入力します。

    これらのアクションを完了すると、GitHub Copilot Chat から、次の応答のような更新内容が提案されます。

    *これらのメソッドの読みやすさを向上させるために、次の手順に従うことができます。*

    *1.繰り返しコードを別のメソッドに抽出する:Random オブジェクトが、さまざまなメソッドで複数回作成されています。クラス レベルで静的な Random オブジェクトを作成して、すべてのメソッドで使用することもできます。これにより、読みやすさが向上するだけでなく、ランダム性も向上します。*

    `private static readonly Random random = new Random();`

    *2.わかりやすい変数名を使用する:GenerateRandomDateOpened メソッドの変数名 `range` は少しあいまいです。daysRange のようなわかりやすい名前を使用します。*

    *3.コメントを追加する:コードは、ほとんどの場合、見るだけでその内容がわかるようになっていますが、そのメソッドが何を実行するかを説明するコメントを追加しておくと、他の開発者がコードを使用する際に役立ちます。*

    *4.マジック ナンバーに定数を使用する:GenerateRandomDateOpened メソッドでは、数値 `10` を使用して、開始日から何年前までを指定できるかを表します。これを定数に抽出して、`MaxYearsBack` などのわかりやすい名前を付けることができます。*

    *5.var キーワードを使用する:C# では、代入の右側で型が明らかになったときに var キーワードを使用できます。これにより、コードがよりすっきりし、読みやすくなります。*

   *これらの改善を行った後、コードがどのように表示されるかを次に示します。*

    ```csharp

    private static readonly Random random = new Random();
    private const int MaxYearsBack = 10;
    static double GenerateRandomBalance(double min, double max)
    {
        double balance = random.NextDouble() * (max - min) + min;
        return Math.Round(balance, 2);
    }
    static string GenerateRandomAccountHolder()
    {
        string[] accountHolderNames = {  /* names here */  };
        var accountHolderName = accountHolderNames[random.Next(0, accountHolderNames.Length)];
        return accountHolderName;
    }
    static string GenerateRandomAccountType()
    {
        string[] accountTypes = {  /* types here */  };
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

    ```

    > [!IMPORTANT]
    > `GenerateRandomAccountHolder` メソッドと `GenerateRandomAccountType` メソッドのプレースホルダー値 (`/* types here */` など) に注目してください。 GitHub Copilot Chat では、コードの詳細がプレースホルダーに置き換えられる場合があります。 これらは、よく見れば簡単に見つかります。 更新を実装するときは、プレースホルダーの値をアプリの値に置き換える必要があります。 プレースホルダーが表示されたら、提案された更新を実装する前に、既存のコードのコピーを作成する必要があります。 提案されたコード ブロックがアプリ内のコードと一致する場合は、ブロック コメントを使用して既存のコードをコメントアウトし、チャット ビューの **[カーソル位置に挿入]** ボタンを使用すると、名前の競合なく、提案された更新を実装できます。 提案された更新が期待どおりに動作することを確認したら、ブロック コメントを削除できます。

1. コードの読みやすさ、保守容易性、モジュール性を向上するのに役立つ、提案された更新を実装します。

    ブロック コメントを使用して既存のコードをコメントアウトした場合は、チャット ビューの **[カーソル位置に挿入]** を使用して、提案された更新を挿入できます。 [コピー] オプションを使用して、選択した場所に更新内容を貼り付けることもできます。

    どの更新の提案を実装するかを選択する前に、職場で実施されているコード作成の標準とポリシーを考慮してください。

1. 更新の実装時にエラーが発生しないようにするには、続行する前にソリューションをビルドして実行します。

1. 2 番目のプロンプトを入力し、GitHub Copilot Chat から提案された更新を確認します。

1. GitHub Copilot Chat から提供される提案を確認します。

    たとえば、次のアクションを完了したとします。

    - 最初のサンプル プロンプトで GitHub Copilot Chat が提案した更新を実装します。
    - Program.cs ファイルでの作業を続行することにします。
    - 次のプロンプトを選択します: `@workspace /explain How can I improve the maintainability of the Main, GenerateRandomBalance, GenerateRandomAccountHolder, GenerateRandomAccountType, and GenerateRandomDateOpened methods?`。
    - 次のメソッドを選択します: `Main`、`GenerateRandomBalance`、`GenerateRandomAccountHolder`、`GenerateRandomAccountType`、`GenerateRandomDateOpened`。
    - チャット ビューを開き、Program.cs ファイルをチャット コンテキストにアタッチします。
    - チャット ビューにプロンプトを入力します。

    これらのアクションを完了すると、GitHub Copilot Chat から、次の応答のような更新内容が提案されます。

    *これらのメソッドの保守容易性を向上させるために、次の手順に従うことができます。*

    *1.懸念事項の分離:Main メソッドでは、口座の作成、トランザクションのシミュレート、転送のシミュレートなど、多くのことを行います。これらは、読みやすさと保守容易性を向上させるために、別々のメソッドに分けることができます。*

    *2.エラー処理:このコードでは、エラー処理に一般的な例外を使用しています。アプリケーションに固有のカスタム例外を作成することをお勧めします。それにより、エラーの理解と処理が容易になります。*

    *3.マジック ナンバー:このコードにはマジック ナンバーが含まれています (口座の数を表す 20、トランザクションの数を表す 100 など)。これらは名前付き定数に置き換えるべきです。*

    *4.コードの重複:ランダムな値を生成するためのコードが、複数の場所で重複しています。これは、ユーティリティ クラスまたはメソッドにリファクタリングできます。*

    ```csharp

    class Program
    {
        private static readonly Random random = new Random();
        private const int MaxYearsBack = 10;
        private const int NumberOfAccounts = 20;
        private const int NumberOfTransactions = 100;
        static void Main(string[] args)
        {
            List<BankAccount> accounts = CreateBankAccounts(NumberOfAccounts);
            SimulateTransactions(accounts, NumberOfTransactions);
            SimulateTransfers(accounts);
        }
        static List<BankAccount> CreateBankAccounts(int numberOfAccounts)
        {
            List<BankAccount> accounts = new List<BankAccount>();
            int createdAccounts = 0;
            while (createdAccounts < numberOfAccounts)
            {
                try
                {
                    // same code as before...
                }
                catch (Exception ex)
                {
                    Console.WriteLine($"Account creation failed: {ex.Message}");
                }
            }
            return accounts;
        }
        static void SimulateTransactions(List<BankAccount> accounts, int numberOfTransactions)
        {
            // same code as before...
        }
        static void SimulateTransfers(List<BankAccount> accounts)
        {
            // same code as before...
        }
        // same helper methods as before...
    }

    ```

1. GitHub Copilot Chat から提供される提案を確認します。

1. コードの読みやすさ、保守容易性、モジュール性を向上するのに役立つ、提案された更新を実装します。

    ブロック コメントを使用して既存のコードをコメントアウトした場合は、チャット ビューの **[カーソル位置に挿入]** を使用して、提案された更新を挿入できます。 [コピー] オプションを使用して、選択した場所に更新内容を貼り付けることもできます。

1. 変更によってエラーが発生しないようにするには、続行する前にソリューションをビルドして実行します。

1. 3 番目のプロンプトを入力し、少し時間を取って提案を確認します。

    たとえば、次のアクションを完了したとします。

    - 1 番目と 2 番目のプロンプトで GitHub Copilot Chat が提案した更新を実装します。
    - Program.cs ファイルでの作業を続行することにします。
    - 次のプロンプトを選択します: `@workspace /explain How can I improve the modularity of the Program.cs file?`。
    - 次のコードを選択します。すべての Program.cs ファイルを選択します。
    - チャット ビューを開き、Program.cs ファイルをチャット コンテキストにアタッチします。
    - チャット ビューにプロンプトを入力します。

    これらのアクションを完了すると、GitHub Copilot Chat から、次の応答のような更新内容が提案されます。

    *Program.cs ファイルのモジュール性を向上させるために、次の手順に従うことができます。*

    *1.懸念事項を分離する:`Program` クラスで行う処理が多すぎます。口座の作成、トランザクションのシミュレート、ランダム データの生成を行っています。これらの役割はそれぞれ別のクラスに分けることができます。たとえば、銀行口座の作成を担当する `BankAccountFactory` クラス、トランザクションをシミュレートする `TransactionSimulator` クラス、ランダム データを生成する `RandomDataGenerator` クラスに分けることができます。*

    *2.インターフェイスを使用する:インターフェイスを使用して、クラスのコントラクトを定義できます。これにより、コードの柔軟性が高まり、テストが容易になります。たとえば、`Create` メソッドを使用して `IAccountFactory` インターフェイスを定義し、`BankAccountFactory` でこのインターフェイスを実装できます。*

    *3.マジック ナンバー:コードにはいくつかの "マジック ナンバー" があります (10、50000、-500、500 など)。コードの読みやすさと保守容易性を高めるために、これらの数値を名前付き定数に置き換えるべきです。*

    *4.重複:メソッド `SimulateTransactions` と `SimulateTransfers` のコードはほぼ同じです。この重複を排除するには、両方のメソッドが呼び出す共通のメソッドを作成します。*

   *CreateBankAccounts メソッドをリファクタリングする方法の例を次に示します。*

    **コード スニペット A:インターフェイスを使用する**

    ```csharp

    interface IAccountFactory
    {
        BankAccount Create(int index);
    }
    class BankAccountFactory : IAccountFactory
    {
        private readonly RandomDataGenerator _randomDataGenerator;
        public BankAccountFactory(RandomDataGenerator randomDataGenerator)
        {
            _randomDataGenerator = randomDataGenerator;
        }
        public BankAccount Create(int index)
        {
            double initialBalance = _randomDataGenerator.GenerateRandomBalance(10, 50000);
            string accountHolderName = _randomDataGenerator.GenerateRandomAccountHolder();
            string accountType = _randomDataGenerator.GenerateRandomAccountType();
            DateTime dateOpened = _randomDataGenerator.GenerateRandomDateOpened();
            return new BankAccount($"Account {index + 1}", initialBalance, accountHolderName, accountType, dateOpened);
        }
    }
    // In the `Program` class, you would then use the `IAccountFactory` to create accounts:
    interface IAccountFactory
    {
        BankAccount Create(int index);
    }
    class BankAccountFactory : IAccountFactory
    {
        private readonly RandomDataGenerator _randomDataGenerator;
        public BankAccountFactory(RandomDataGenerator randomDataGenerator)
        {
            _randomDataGenerator = randomDataGenerator;
        }
        public BankAccount Create(int index)
        {
            double initialBalance = _randomDataGenerator.GenerateRandomBalance(10, 50000);
            string accountHolderName = _randomDataGenerator.GenerateRandomAccountHolder();
            string accountType = _randomDataGenerator.GenerateRandomAccountType();
            DateTime dateOpened = _randomDataGenerator.GenerateRandomDateOpened();
            return new BankAccount($"Account {index + 1}", initialBalance, accountHolderName, accountType, dateOpened);
        }
    }

    ```

    **コード スニペット B:重複**

    ```csharp

    static void SimulateOperations(List<BankAccount> accounts, int numberOfOperations, Action<BankAccount, double> operation)
    {
        foreach (BankAccount account in accounts)
        {
            for (int i = 0; i < numberOfOperations; i++)
            {
                double transactionAmount = GenerateRandomBalance(-500, 500);
                try
                {
                    operation(account, transactionAmount);
                    Console.WriteLine($"Operation: {transactionAmount}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
                }
                catch (Exception ex)
                {
                    Console.WriteLine($"Operation failed: {ex.Message}");
                }
            }
            Console.WriteLine($"Account: {account.AccountNumber}, Balance: {account.Balance.ToString("C")}, Account Holder: {account.AccountHolderName}, Account Type: {account.AccountType}");
        }
    }
    // Then you can call this method like this:
    SimulateOperations(accounts, NumberOfTransactions, (account, amount) => {
        if (amount >= 0)
        {
            account.Credit(amount);
        }
        else
        {
            account.Debit(-amount);
        }
    });

    ```

    > [!NOTE]
    > 3 番目のプロンプトから GitHub Copilot が生成した更新の提案を実装する必要はありません。 この提案を確認すると、コード改善プロセスがどのように進むかの情報がわかります。

次の 2 つのデモでは、次のトピックについて説明します。

- GitHub Copilot Chat を使用してコードの信頼性とパフォーマンスを改善する
- GitHub Copilot Chat を使用してコードのセキュリティを改善する

## まとめ

このデモでは、GitHub Copilot Chat を使用して、サンプル アプリケーションのコード品質の向上に役立つ提案を生成しました。 コードの読みやすさ、保守容易性、モジュール性の向上に重点を置いたプロンプトを作成しました。 GitHub Copilot Chat から提供された提案を確認し、コード品質の向上に役立つ更新を実装しました。 また、コードをさらに改善できる追加の提案も検討しました。
