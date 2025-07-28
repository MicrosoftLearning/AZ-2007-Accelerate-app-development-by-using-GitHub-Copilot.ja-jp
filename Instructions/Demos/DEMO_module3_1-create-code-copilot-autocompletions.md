---
demo:
  title: 'デモ:コード行補完を使用してコードを作成する'
  module: 'Module 3: Develop code features using GitHub Copilot tools'
---

# デモ:コード行補完を使用してコードを作成する

## 手順

デモのアクティビティは、次のリソースを含む環境向けに設計されています。

- Visual Studio Code。
- Visual Studio Code 用の C# 開発キット拡張機能。
- Visual Studio Code 用の GitHub Copilot および GitHub Copilot Chat 拡張機能。 GitHub Copilot のアクティブなサブスクリプションを持つ GitHub アカウントが必要です。
- C# を使用して作成されたサンプル コード プロジェクト。

**注**:デモには講師自身の GitHub アカウントと GitHub Copilot サブスクリプションを使用することを検討するようにお勧めします。 そうすると開発環境を制御およびカスタマイズできるようになります。 また、クラスルームの必要に合わせてデモを簡単に調整できます。

**重要**:講師の PC ではなく、ホストされたラボ環境でデモを実行することを選択した場合は、ホストされた環境でサンプル アプリを解凍できます。 デモを実行する前に、ホストされた環境で GitHub Copilot 拡張機能を構成する必要があります。 ホストされた環境はローカル環境よりも遅い場合があるため、それに応じてデモのペースを調整することが必要になる場合があります。

### デモを紹介する

GitHub Copilot は、多数のプログラミング言語やさまざまなフレームワークに対してコード補完候補を表示できますが、特に Python、JavaScript、TypeScript、Ruby、Go、C#、C++ に適しています。 コード行の入力候補は、記述しているコードのコンテキストに基づいて生成されます。 GitHub Copilot によって提供される候補を受け入れる、拒否する、または部分的に受け入れることが可能です。

GitHub Copilot には、コード行の入力候補を生成する 2 つの方法が用意されています。

- **コメントから**:生成したいコードを説明するコメントを記述することで、コード行の入力候補を生成できます。 GitHub Copilot は、記述されたコメントに基づいてコード補完候補を表示します。

- **コードから**:コード行を開始するか、入力済みのコード行の後で Enter キーを押すことで、コード行の入力候補を生成できます。 GitHub Copilot は、記述されたコードに基づいてコード補完候補を表示します。

このデモでは、GitHub Copilot を使用して、Visual Studio Code 環境でコード行の入力候補を生成します。

### Visual Studio Code 環境でコンソール アプリを作成する

このデモでは、GitHub Copilot ツールを使用してコンソール アプリを作成します。

以下の手順に従って、デモのこのセクションを完了します。

1. Visual Studio Code の新しいインスタンスを開き、チャット ビューを開きます。

    Visual Studio Code コマンド センターから **[チャットを開く]** を選択するか、**[Ctrl+Alt+I]** キーボード ショートカットを使用することで、[チャット] ビューを開くことができます。

1. チャット ビューで、次のプロンプトを入力します。

    ```plaintext
    @workspace /new console application named APL2007M3. Use C# LangVersion 12 and NET8.0. Only .cs and .csproj files. Enable ImplicitUsings and Nullable
    ```

1. チャット ビューで、**[ワークスペースの作成]** を選択します。

    GitHub Copilot は、プロンプトを使用して、新しいコンソール アプリケーションのワークスペースを作成します。 アプリケーションは、`C#` と `.NET8.0` を使用します。 コード プロジェクトの名前は `APL2007M3` で、`.cs` ファイルと `.csproj` ファイルが含まれています。 `APL2007M3.csproj` ファイルは C# `LangVersion 12` を指定し、`ImplicitUsings` と `Nullable` を有効にします。

1. [フォルダーの選択] ダイアログで、[デスクトップ] フォルダーに移動し、**[デスクトップ]** を選択してから、**[親フォルダーとして選択]** を選択します。

    新しいワークスペースの親フォルダーを選択するように求められます。 このデモでは、デスクトップ フォルダーを選択することをお勧めします。 デスクトップ フォルダーは簡単に見つけることができます。 このトレーニングを完了したら、クリーンアップすることを忘れないでください。

1. 新しいプロジェクトを開くか確認するメッセージが表示されたら、**[開く]** を選択します。

1. エクスプローラー ビューで、**Program.cs** を選択します。

1. Program.cs ファイルの内容を次のコードに置き換えます。

    ```csharp

    namespace ReportGenerator
    {
        class QuarterlyIncomeReport
        {
            static void Main(string[] args)
            {
                // create a new instance of the class
                QuarterlyIncomeReport report = new QuarterlyIncomeReport();
                // call the GenerateSalesData method
                // call the QuarterlySalesReport method
            }
            public void QuarterlySalesReport()
            {
                Console.WriteLine("Quarterly Sales Report");
            }
        }    
    }

    ```

セットアップ要件が完了し、デモを続行する準備ができました。

### GitHub Copilot を使用してコメントからコード行の入力補完を生成する

GitHub Copilot は、コメントとアプリの既存のコンテキストに基づいてコード補完候補を生成します。 コメントを使用して、コード スニペット、メソッド、データ構造、およびその他のコード要素を記述できます。

以下の手順に従って、デモのこのセクションを完了します。

1. **Program.cs** ファイルで、`Main` メソッドの下に 2 つの空のコード行を作成します。

1. テスト データの生成に使用できるデータ構造を作成するには、次のコード コメントを作成し、Enter キーを押します。

    ```C#
    // public struct SalesData. Include the following fields: date sold, department name, product ID, quantity sold, unit price
    ```

    GitHub Copilot は、コード コメントとアプリ内で見つかった既存のコードに基づいて、1 つ以上のコード補完候補を生成します。

1. 少し時間を取って、GitHub Copilot によって提供されるコード補完候補を確認してください。

    > [!NOTE]
    > GitHub Copilot がデータ構造ではなくメソッドの提案を生成する場合は、「**public str**」と入力し、コードの入力候補の提案が更新されるまで待ちます。 GitHub Copilot は、追加の情報を使用して自身の提案を改善します。

    データ構造のフィールドを宣言するために使用されるデータ型に注目してください。 GitHub Copilot は、既存のコードとコード コメントに基づいてデータ型と変数名を選択します。 GitHub Copilot は、アプリケーションが変数をどのように使用するかを判断し、それに応じてデータ型を定義しようとします。

    GitHub Copilot で複数の提案が生成された場合は、**[承諾する]** ボタンの左側にある左または右矢印 (`>` または `<`) を選択すると、提案を順番に表示できます。 これにより、ニーズに最も適した提案を確認して選択できます。

    目的のコードと完全に一致しないコードの入力候補の提案を受け入れても問題ありません。 ただし、提案を "修正" するために必要な変更を明確にする必要があります。 この場合、データ型の一部が目的の型ではありませんが、オートコンプリートの提案を受け入れた後にそれらを調整することができます。

    提案されたオプションが必要なオプションと似ていない場合、次の 2 つの方法を試すことができます。 他の提案の一覧を含む新しいエディター タブを開くには、**Ctrl** + **Enter** キーを押します。 このホットキーの組み合わせにより、最大 10 個の他の提案を含む新しいタブが開きます。 各提案の後に、その提案を受け入れるために使用できるボタンが表示されます。 提案を受け入れると、タブは自動的に閉じます。 もう 1 つの方法は、**Esc** キーを押して、提案を無視し、もう一度試すことです。 コードのコメントを調整して、GitHub Copilot が機能するためのより多くのコンテキストを提供できます。

    > [!NOTE]
    > GitHub Copilot では、段階的に候補が提案されることがあります。 このような場合、Tab キーを押した後に Enter キーを押すと、次の段階の提案を表示できます。

1. 提案されたデータ構造を受け入れるには、Tab キーを押すか、**[承諾する]** を選択します。

1. フィールドのデータ型を変更するには、次のようにコードを更新します。

    ```csharp

    public struct SalesData
    {
        public DateOnly dateSold;
        public string departmentName;
        public int productID;
        public int quantitySold;
        public double unitPrice;
    }

    ```

    コードの入力候補の提案をすばやく調整すると、必要なコードを確実にビルドできます。 コードベースの大部分をまだ開発する必要がある場合、開発プロセスの早い段階で修正を行うことが特に重要です。 以降のコード入力候補は、既に作成したコードに基づいて行われるため、コードが可能な限り正確であることを確認することが重要です。

1. `SalesData` データ構造の下に 2 つの空のコード行を作成します。

1. `SalesData` データ構造を使用してテスト データを生成するメソッドを作成するには、次のコード コメントを記述し、Enter キーを押します。

    ```C#
    /* the GenerateSalesData method returns 1000 SalesData records. It assigns random values to each field of the data structure */
    ```

1. 少し時間を取って、GitHub Copilot によって提供されるコード補完候補を確認してください。

    `GenerateSalesData` メソッドは、`SalesData` オブジェクトの配列を返すように設計されていることに注意してください。 このメソッドは、`SalesData` データ構造の各フィールドにランダムな値が割り当てられた 1,000 レコードのテスト データを生成します。

    GitHub Copilot および GitHub Copilot Chat によって提案された候補は、正しいように見える場合でも、常に確認する必要があります。

    > [!NOTE]
    > GitHub Copilot で、完成した `GenerateSalesData` メソッドではなく単一のコード行が提案された場合は、**Ctrl + Enter** キーを押して [GitHub Copilot Suggestions] タブを開きます。この新しいタブの提案を確認します。次の手順で、[Accept suggestion #] ボタンを使用して提案を受け入れます。 GitHub Copilot は、提案を段階的に提示する場合があります。 コードの入力候補を段階的に受け入れることはできますが、[GitHub Copilot の提案] タブを使用して、完全な提案を確認してから、受け入れるか、無視するかを決定することをお勧めします。

1. コード補完に関する提案をスクロールし、要件に最も合うものを選択します。

1. コードの入力候補を受け入れるには、Tab キーを押します。

    コードの入力候補の提案には、`DateSold` フィールドを生成するために使用されるコードに構文エラーが含まれていることに注意してください。 `DateOnly` は、正しい順序で一覧表示する必要がある 3 つの整数値 (**年**、**月**、**日**) を受け入れます。

1. `DateSold` フィールドの生成に使用するコードに 1 年を指定するには、次のようにコード行を更新します。

    ```C#
    salesData[i].DateSold = new DateOnly(2023, random.Next(1, 13), random.Next(1, 29));
    ```

1. 必要に応じて、次のコード スニペットに一致するように他のコード行を調整します。

    ```csharp

    public SalesData[] GenerateSalesData()
    {
        SalesData[] salesData = new SalesData[1000];
        Random random = new Random();
        for (int i = 0; i < salesData.Length; i++)
        {
            salesData[i].dateSold = new DateOnly(2023, random.Next(1, 13), random.Next(1, 29));
            salesData[i].departmentName = "Department " + random.Next(1, 11);
            salesData[i].productID = random.Next(1, 101);
            salesData[i].quantitySold = random.Next(1, 101);
            salesData[i].unitPrice = random.NextDouble() * 100;
        }
        return salesData;
    }

    ```

コード コメントからコードを生成する機能は、GitHub Copilot の強力な機能です。 2 つのコメントだけで、データ構造とテスト データを生成するメソッドを生成できました。

### GitHub Copilot を使用してコード行の入力候補を生成する

GitHub Copilot では、入力したコードに基づいてコード行の入力候補を生成できます。 コード行の入力候補は、次の 2 つの方法で生成できます。

- コード行の入力を開始し、GitHub Copilot によって未完成のコード行のオートコンプリートが提案されるまで待ちます。
- 完全なコード行を入力して **Enter** キーを押し、GitHub Copilot によって次のコード行のオートコンプリートが提案されるまで待ちます。

> [!NOTE]
> GitHub Copilot は、入力したコードと、アプリ内のコードによって定義されたコンテキストに基づいて、提案するコード補完を生成します。 高品質のコードであれば、アプリ内のコードが増えるほど、GitHub Copilot が利用できるコンテキストも増えます。 既存のコードの量が増え、品質が良くなるにつれて、GitHub Copilot が提案するコード行の入力候補の品質と信頼性も向上します。 GitHub Copilot は、特に一連の関連コンポーネントを生成する必要がある場合に、一般的なプログラミング タスクおよびパターンのコード行の入力候補を生成するのに非常に適しています。

デモのこの部分では、`QuarterlySalesReport` メソッドを操作します。

完了する必要があるタスクを次に示します。

- `SalesData` オブジェクトのコレクションを受け入れるパラメーターを使用してメソッド コンストラクターを更新します。
- GitHub Copilot を使用して、四半期レポートの売上データを処理するコード行の入力候補を生成します。
- アプリを実行し、四半期売上レポートを確認します。

以下の手順に従って、デモのこのセクションを完了します。

1. `QuarterlySalesReport` のメソッド コンストラクターを次のように更新します。

    ```C#
    public void QuarterlySalesReport(SalesData[] salesData)
    ```

1. 少し時間を取って、開発が必要なコードについて考えてみてください。

    コンセプトは単純です。 コードで売上データに基づいて四半期ごとの売上を計算し、レポートを作成する必要があります。 そのためには、コードで次のことを行う必要があります。

    - `salesData` コレクションを反復処理します。
    - 販売数量と単価に基づいて各販売額を計算します。
    - 販売日を使用して、売上がどの四半期に属するかを判断します。
    - 各四半期の売上を合計します。
    - 四半期ごとの売上レポートを作成します。

    1 つのオプションは、`foreach` ループのコードの入力を開始してから、GitHub Copilot が提案する内容を確認することです。

1. `QuarterlySalesReport` メソッドで、コード ブロックの先頭に新しいコード行を作成します。

    新しいコード行と、`Console.WriteLine()` を含むコード行との間に、少なくとも 1 つの空のコード行が必要です。

1. コード行の入力候補を生成するには、「`foreach (`」と入力し、GitHub Copilot によってコード行の入力候補オプションが提案されるまで待ちます。

1. GitHub Copilot によって提案されたコード補完を確認します。

    提案されたコードの入力候補は、目的のコードではありません。

    GitHub Copilot は、`salesData` を反復処理する `foreach` ループを提案していますが、ループ内に分析や計算はありません。 提案された各オプションには、望ましくない、または必要のない `Console.WriteLine` ステートメントが含まれています。

1. 少し時間を取って、GitHub Copilot が `Console.WriteLine` ステートメントを提案する理由を考えてみてください。

    GitHub Copilot は、コードのコンテキストに基づいてコード補完候補を生成することを思い出してください。 この場合、GitHub Copilot が考慮すべきコードはそれほどありません。 状況はさらに悪化します。

    GitHub Copilot がメソッド内に示すコードは、`Console.WriteLine` ステートメントです。 メソッド内で利用可能な他のコンテキストがなく、コードベース内に取得できる同様のメソッドもないため、GitHub Copilot は、`foreach` ループ内に `Console.WriteLine` ステートメントを*必要としている*可能性があると結論付けます。

    GitHub Copilot は、コードがクリーンで焦点が絞られている場合に最適に機能します。 コード内に余分なコード コメントやステートメントが含まれている場合は、GitHub Copilot のコード補完を使用する前にそれらを削除することをお勧めします。

1. GitHub Copilot をもう一度試す前にコードをクリーンアップするには、次の手順を実行します。

    - 提案された `foreach (` コード補完を取り消します。
    - 入力した部分的な `foreach (` ステートメントを削除します。
    - `QuarterlySalesReport` メソッドから `Console.WriteLine` ステートメントを削除します。

    これで、GitHub Copilot をもう一度試す準備が整いました。

1. `QuarterlySalesReport` メソッドが次のようなコードになっていることを確認してください。

    ```C#
    public void QuarterlySalesReport(SalesData[] salesData)
    {


    }
    ```

1. `QuarterlySalesReport` メソッド内の空白のコード行にカーソルを置き、Enter キーを押します。

    提案するコード補完を GitHub Copilot が 生成するまでに少し時間がかかる場合があります。

1. 少し時間を取って、提案されたコード補完を確認してください。

    > [!NOTE]
    > GitHub Copilot で表示されるのは使用するメソッド名とパラメーターだけですが、有用な候補を生成するにはおそらくそれだけで十分です。 四半期ごとの売上を計算するための候補が表示されます。 候補を拒否してもう一度試してみると、異なる結果が得られる可能性があります。

    `>` または `<` を選択することで、候補を順番に表示できます。

    提案されたコード補完が売上データを反復処理し、四半期ごとの売上計算を実行することに注目してください。

1. 提案されたコード補完を受け入れるには、Tab キーを押します。

    提案されたコード補完は、売上データに基づいて四半期の収入を計算して表示します。

    ```csharp

    // create a dictionary to store the quarterly sales data
    Dictionary<string, double> quarterlySales = new Dictionary<string, double>();
    // iterate through the sales data
    foreach (SalesData data in salesData)
    {
        // calculate the total sales for each quarter
        string quarter = GetQuarter(data.dateSold.Month);
        double totalSales = data.quantitySold * data.unitPrice;
        if (quarterlySales.ContainsKey(quarter))
        {
            quarterlySales[quarter] += totalSales;
        }
        else
        {
            quarterlySales.Add(quarter, totalSales);
        }
    }
    // display the quarterly sales report
    Console.WriteLine("Quarterly Sales Report");
    Console.WriteLine("----------------------");
    foreach (KeyValuePair<string, double> quarter in quarterlySales)
    {
        Console.WriteLine(entry.Key + ": $" + entry.Value);
    }

    ```

1. 販売月に基づいて四半期を判断するために `GetQuarter` メソッドが使用されていることに注目してください。

    このメソッドはコードに実装されていませんが、コードをビルドして実行するために必要です。

1. `QuarterlySalesReport` メソッドの下に 2 つの空のコード行を作成します。

1. GitHub Copilot が `GetQuarter` メソッドのコード補完を提案していることに注目してください。

    GitHub Copilot は、`QuarterlySalesReport` メソッドによって提供されるコンテキストを使用して、販売月に基づいて四半期を判断する `GetQuarter` メソッドのコード補完を簡単に生成できます。

1. 少し時間を取って、提案された `GetQuarter` メソッドのコード行の入力候補を確認してください。

1. 提案されたコード補完を受け入れるには、Tab キーを押します。

    ```csharp

    public string GetQuarter(int month)
    {
        if (month >= 1 && month <= 3)
        {
            return "Q1";
        }
        else if (month >= 4 && month <= 6)
        {
            return "Q2";
        }
        else if (month >= 7 && month <= 9)
        {
            return "Q3";
        }
        else
        {
            return "Q4";
        }
    }

    ```

1. コードを実行する前に `Main` メソッドを完成させる必要があることに注目してください。

    `Main` メソッドのコメントを使用してコードを更新できます。

1. `// call the GenerateSalesData method` コード コメントの末尾にカーソルを置き、Enter キーを押します。

    GitHub Copilot は、このコメントを使用してメソッドの呼び出し元ステートメントを提案します。

1. GitHub Copilot によって提案されたコード補完を確認し、受け入れます。

1. `// call the QuarterlySalesReport method` コード コメントに対して、このプロセスを繰り返します。

1. `Main` メソッドには、次のコードが含まれています。

    ```csharp

    static void Main(string[] args)
    {
        // create a new instance of the class
        QuarterlyIncomeReport report = new QuarterlyIncomeReport();
        // call the GenerateSalesData method
        SalesData[] salesData = report.GenerateSalesData();
        // call the QuarterlySalesReport method
        report.QuarterlySalesReport(salesData);
    }

    ```

1. 少し時間を取って、`QuarterlyIncomeReport` クラスのコードを確認してください。

    ```csharp

    namespace ReportGenerator
    {
        class QuarterlyIncomeReport
        {
            static void Main(string[] args)
            {
                // create a new instance of the class
                QuarterlyIncomeReport report = new QuarterlyIncomeReport();
                // call the GenerateSalesData method
                SalesData[] salesData = report.GenerateSalesData();
                // call the QuarterlySalesReport method
                report.QuarterlySalesReport(salesData);
            }
            /* public struct SalesData includes the following fields: date sold, department name, product ID, quantity sold, unit price */
            public struct SalesData
            {
                public DateOnly dateSold;
                public string departmentName;
                public int productID;
                public int quantitySold;
                public double unitPrice;
            }
            /* the GenerateSalesData method returns 1000 SalesData records. It assigns random values to each field of the data structure */
            public SalesData[] GenerateSalesData()
            {
                SalesData[] salesData = new SalesData[1000];
                Random random = new Random();
                for (int i = 0; i < 1000; i++)
                {
                    salesData[i].dateSold = new DateOnly(2023, random.Next(1, 13), random.Next(1, 29));
                    salesData[i].departmentName = "Department " + random.Next(1, 11);
                    salesData[i].productID = random.Next(1, 101);
                    salesData[i].quantitySold = random.Next(1, 101);
                    salesData[i].unitPrice = random.NextDouble() * 100;
                }
                return salesData;
            }
            public void QuarterlySalesReport(SalesData[] salesData)
            {
                // create a dictionary to store the quarterly sales data
                Dictionary<string, double> quarterlySales = new Dictionary<string, double>();
                // iterate through the sales data
                foreach (SalesData data in salesData)
                {
                    // calculate the total sales for each quarter
                    string quarter = GetQuarter(data.dateSold.Month);
                    double totalSales = data.quantitySold * data.unitPrice;
                    if (quarterlySales.ContainsKey(quarter))
                    {
                        quarterlySales[quarter] += totalSales;
                    }
                    else
                    {
                        quarterlySales.Add(quarter, totalSales);
                    }
                }
                // display the quarterly sales report
                Console.WriteLine("Quarterly Sales Report");
                Console.WriteLine("----------------------");
                foreach (KeyValuePair<string, double> quarter in quarterlySales)
                {
                    Console.WriteLine(entry.Key + ": $" + entry.Value);
                }
            }
            public string GetQuarter(int month)
            {
                if (month >= 1 && month <= 3)
                {
                    return "Q1";
                }
                else if (month >= 4 && month <= 6)
                {
                    return "Q2";
                }
                else if (month >= 7 && month <= 9)
                {
                    return "Q3";
                }
                else
                {
                    return "Q4";
                }
            }
        }
    }
    
    ```

    このコードは、ほぼ完全に、GitHub Copilot によって生成されたコード行の入力候補を使用して作成されました。 ただし、コードに関する提案の確認は重要であり、修正が必要でした。 GitHub Copilot で提案されるコード補完を常に確認し、コードが要件を満たしていることを確認する必要があります。

1. レポートの出力を確認するために、アプリを実行します。

    Visual Studio Code のターミナル ウィンドウを開き、次のコマンドを入力します。

    ```bash
    dotnet run
    ```

    出力には四半期収入レポートが表示され、部門名、四半期、およびテスト データで表された各部門および各四半期の収入が示されます。

1. ターミナル ウィンドウで出力を確認します。

    四半期ごとの結果はランダムな数値に基づいていますが、次のような出力形式のレポートが表示されます。

    ```output

    Quarterly Sales Report
    ----------------------
    Q3: $635637.5019563352
    Q4: $672247.315297204
    Q2: $667269.194630603
    Q1: $642769.2700531208

    ```

    `QuarterlyIncomeReport` クラスを完成させるには、まだ作業が必要です。 次のユニットでは、GitHub Copilot Chat を使用してアプリを拡張および更新します。

### まとめ

このデモでは、GitHub Copilot を使用して、Visual Studio Code 環境でコード行の入力候補を生成しました。 コード コメントを使用して、データ構造とテスト データを生成するメソッドを生成しました。 また、コード行の入力候補を使用して、四半期収入レポートの売上データを処理するコードを生成しました。
