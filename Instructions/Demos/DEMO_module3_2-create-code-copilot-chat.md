---
demo:
  title: 'デモ:GitHub Copilot インライン チャットを使用してコードを作成する'
  module: 'Module 3: Develop code features using GitHub Copilot tools'
---

# デモ:GitHub Copilot インライン チャットを使用してコードを作成する

## 手順

デモのアクティビティは、次のリソースを含む環境向けに設計されています。

- Visual Studio Code。
- Visual Studio Code 用の C# 開発キット拡張機能。
- Visual Studio Code 用の GitHub Copilot および GitHub Copilot Chat 拡張機能。 GitHub Copilot のアクティブなサブスクリプションを持つ GitHub アカウントが必要です。
- C# を使用して作成されたサンプル コード プロジェクト。

**注**:デモには講師自身の GitHub アカウントと GitHub Copilot サブスクリプションを使用することを検討するようにお勧めします。 そうすると開発環境を制御およびカスタマイズできるようになります。 また、クラスルームの必要に合わせてデモを簡単に調整できます。

**重要**:講師の PC ではなく、ホストされたラボ環境でデモを実行することを選択した場合は、ホストされた環境でサンプル アプリを解凍できます。 デモを実行する前に、ホストされた環境で GitHub Copilot 拡張機能を構成する必要があります。 ホストされた環境はローカル環境よりも遅い場合があるため、それに応じてデモのペースを調整することが必要になる場合があります。

### デモを紹介する

Visual Studio Code 用の GitHub Copilot Chat 拡張機能には、次の 3 つのチャット インターフェイスが含まれています。

- **チャット ビュー**には、いつでも役立つ AI アシスタントが用意されています。
- **クイック チャット** ウィンドウを使用すると、簡単な質問をして、作業内容に戻ることができます。
- **インライン チャット** インターフェイスは、コーディング中にコンテキスト操作のためにエディターで直接開きます。

[チャット] ビューと [クイック チャット] ウィンドウを使用すると、AI との対話型のマルチターン会話が可能になります。 どちらのインターフェイスも、質問をしたり、コーディングの問題に関するヘルプを表示したり、コードを生成したりするための方法を提供します。 会話中、GitHub Copilot の応答には、自然言語テキスト、コード ブロック、その他の要素が含まれます。 応答でコード ブロックが提供されている場合は、コード ブロックをコピーするか、コード エディターに直接挿入することができます。

インライン チャット インターフェイスは、コーディング中にコンテキスト ヘルプとコード提案を提供するように設計されています。

このデモでは、GitHub Copilot のインライン チャット機能を使用して、新しいコード機能を生成します。 このデモは、前のデモでのプロジェクト シナリオの続きです。 準備したサンプル アプリ (`APL2007M3SalesReport-InlineChat`) を使用してデモを開始します。 デモでは、`SalesData` データ構造と `GenerateSalesData` メソッドを更新します。 また、`QuarterlySalesReport` メソッドを更新して、追加の計算と表示オプションを含めます。

#### コーディング タスクとプロジェクトの目標を確認する

このデモでは、GitHub Copilot を使用して次のタスクを高速化することに重点を置いています。

1. `SalesData` データ構造と `GenerateSalesData` メソッドを更新して、"実際の" データに似たデータ サンプルを生成します。

    - dateSold: 変更は必要ありません。
    - departmentName:文字列値は、8 つの部門のリストからランダムに選択する必要があります。 部門名ごとに、productID に含めることができる 4 文字の省略形を作成します。
    - productID: データ型を `int` から `string` に変更します。 productID 値は、ID のコンポーネントが次のように定義されているパターン "`DDDD-###-SS-CC-MMM`" を使用してフォーマットする必要があります。

        - 部署を表す 4 文字のコード。
        - 製品を表す 3 桁の数値。
        - 製品サイズを表す 2 文字のコード。
        - 製品の色を表す 2 文字のコード。
        - 製造サイトを表す 3 文字のコード (10 の製造場所の一覧からランダムに選択)。 コードは、2 文字の ISO 国番号の後に数字 (US1、CA2、MX3 など) を付ける必要があります。

    - quantitySold: 変更は必要ありません。
    - unitPrice:価格帯の下限を 25 に、上限を 300 に引き上げます。
    - baseCost:品目の製造コストのフィールドを追加します。 baseCost 値は、unitPrice (5 ~ 20%) からランダムに生成された割引を使用して生成する必要があります。
    - volumeDiscount:ボリューム割引率のフィールドを追加します。 volumeDiscount に割り当てられる値は、quantitySold の 10% (19 ユニットの 10% = 1% volumeDiscount) の整数コンポーネントである必要があります。
    - 生成されるレコードの数を 10,000 に増やします。

1. `QuarterlySalesReport` メソッドを次のように更新します。

    1. 販売結果を表示するときに、結果を論理的な順序で一覧表示します。 たとえば、四半期ごとの売上合計を一覧表示する場合、四半期は第 1 四半期から第 4 四半期までの順序で一覧表示されます。
    1. 地域設定を使用して通貨値を表示します。
    1. 四半期利益および利益率の計算を含める
    1. 部門別の四半期売上、利益、利益率の計算を含めます。

#### GitHub Copilot Chat のプロンプトを開発するためのアプローチを説明する

GitHub Copilot のインライン チャット機能では、送信したプロンプトを使用して、解決しようとしているタスクまたは問題を理解します。 プロンプトは、具体的で簡潔である必要があります。 適切なプロンプトにより、より良い応答が生成されます。

GitHub Copilot のプロンプトを作成するときは、次のベスト プラクティスを検討してください。

- 具体的に、シンプルに保つ:解決しようとしているタスクまたは問題を説明する明確で簡潔なプロンプトを提供します。 AI を混乱させる可能性のある複雑な言語や専門用語を使用しないでください。
- 自然言語を使用する:会話のトーンでプロンプトを記述します。 同僚やチーム メンバーと話すときに使用する自然言語を使用します。
- 複雑なタスクを分割する:タスクが複雑な場合は、小さな手順に分割します。 GitHub Copilot が正しいコードを生成するのに役立つ各手順のプロンプトを提供します。
- コンテキストを指定する:GitHub Copilot が解決しようとしているタスクまたは問題を理解するのに役立つ関連情報を含めます。 プロンプトに関連するデータ、変数、またはコード ブロックに関する詳細を含めます。
- チャット参加者、スラッシュ コマンド、チャット変数を使用する:GitHub Copilot のインライン チャット機能は、チャット参加者、スラッシュ コマンド、チャット変数をサポートしています。 これらの機能を使用して GitHub Copilot と対話し、プロンプトに追加のコンテキストを提供します。

### インライン チャットを使用してデータ構造を生成する

通常、プロジェクトは、固定または既知の機能またはパラメーターで始まります。 多くの場合、データ ソースを選択するか、サンプル データを作成することをおすすめします。

デモのこのセクションでは、シミュレートされた売上データを作成するのに役立つデータ構造を使用します。 このデータは、`QuarterlySalesReport` メソッドを更新するときに、 GitHub Copilot に便利なコンテキストを提供します。

> [!NOTE]
> 実際のビジネス プロジェクトでは、シミュレートされたデータを生成するのではなく、履歴データを使用する可能性があります。 このトレーニングでは、シミュレートされたデータを生成することで、GitHub Copilot ツールを使用して練習する機会を得ることができます。 データのシミュレートは、ビジネス プロジェクトのベスト プラクティスとしては推奨されません。

プロジェクトの目標は、次のデータ構造に取り組む必要があることを示しています。

- 8 つの部署名のリストが必要です。 各部門名は、4 文字の文字列を使用して省略する必要があります。 衣料品やスポーツ用品などの架空の会社の業界を選び、GitHub Copilot に部門名と 4 文字コードの辞書を生成してもらいます。
- 10 の製造サイトの一覧が必要です。 各サイトは 3 文字のコードで表す必要があります。 コードは、2 文字の ISO 国番号の後に数字 (US1、CA2、MX3 など) を付けることができます。 3 から 4 の国番号を使用して、GitHub Copilot に 10 の製造サイトの辞書を生成させます。
- `SalesData` データ構造を更新する必要があります。 部門コード、製造サイト コードの新しいフィールドを含める必要があります。 また、productID のデータ型を `int` から `string` に変更する必要があります。

データ構造を作成して更新するには、次の手順を実行します。

1. Visual Studio Code で **APL2007M3SalesReport-InlineChat** プロジェクト フォルダーを開きます。

1. アプリケーションが実行され、次の出力のようなレポートが生成されることを確認します。

    ```plaintext
    Quarterly Sales Report
    ----------------------
    Q3: $690095.7142725277
    Q4: $600536.3320750712
    Q2: $678194.7943550209
    Q1: $595963.0477790226
    ```

    データはランダムに生成されるため、数値は実行ごとに異なります。

1. Program.cs ファイルを開きます。

1. `SalesData` データ構造の下の空白行にカーソルを置きます。

1. インライン チャット インターフェイスを開くには、キーボードの **Ctrl + I** キーを押します。

1. 次のプロンプトを入力します。

    ```output
    I need a public struct ProdDepartments that contains a static string array for 8 clothing industry departments. Create separate string array containing 4-character abbreviations for each department name. The abbreviation must be unique. The department names should represent real department names for the clothing industry.
    ```

    フィールド名の特定のリストがある場合は、プロンプトでフィールド名を指定できます。 たとえば、実際の会社データを使用して部署名を指定できます。

1. GitHub Copilot によって提供される提案を確認します。

    プロンプトが明確で具体的である限り、GitHub Copilot は便利な提案を提供します。 提案が予期した内容でない場合は、拒否してもう一度試すことができます。 この場合、部署の名前は重要ではないため、おそらく提案を受け入れることもできます。

    データ構造は次のコードのようになります。

    ```csharp

    public struct ProdDepartments
    {
        public static string[] DepartmentNames =  ["Men's Clothing", "Women's Clothing", "Children's Clothing", "Accessories", "Footwear", "Outerwear", "Sportswear", "Undergarments"];
        public static string[] DepartmentAbbreviations =  ["MENS", "WOMN", "CHLD", "ACCS", "FOOT", "OUTR", "SPRT", "UNDR" ];
    }

    ```

1. 提案を受け入れるには、タブ キーを押すか、**[承諾]** を選択します。

    インライン チャット機能を使用して、新しいコードを文書化することもできます。 コードを選択し、**Ctrl + I** キーを押してインライン チャットを開き、「`/doc`」と入力して、推奨されるインライン ドキュメントを確認してから、更新を受け入れます。

1. `ProdDepartments` データ構造の下の空白行にカーソルを置きます。

1. インライン チャット インターフェイスを開くには、キーボードの **Ctrl + I** キーを押します。

1. 次のプロンプトを入力します。

    ```output
    I need a public struct ManufacturingSites that contains a static string array for 10 manSites. Manufacturing sites should be represented by a 3-character code that includes a 2-letter ISO country code followed by a digit. Use 3 ISO country codes.
    ```

    フィールド名の特定のリストがある場合は、プロンプトでフィールド名を指定できます。 たとえば、実際の会社データを使用してフィールド名を指定できます。

1. GitHub Copilot によって提供される提案を確認します。

    データ構造は次のコードのようになります。

    ```csharp

    public struct ManufacturingSites
    {
        public static string[] manSites = [ "US1", "US2", "US3", "UK1", "UK2", "UK3", "JP1", "JP2", "JP3", "MX1" ];
    }

    ```

1. 提案を受け入れるには、タブ キーを押すか、**[承諾]** を選択します。

1. `SalesData` データ構造を選択し、**Ctrl + I** キーを押してインライン チャット インターフェイスを開きます。

    `baseCost` と `volumeDiscount` のフィールドを `SalesData` データ構造 (`double` と `int`) に追加する必要があります。 また、`productID` のデータ型を `int` から `string` に変更する必要があります。

1. 次のプロンプトを入力します。

    ```output
    add double field baseCost and int field volumeDiscount to SalesData. Change productID from int to string.
    ```

    実際には、これらの変更を手動で行う方が簡単な場合があります。 ただし、GitHub Copilot を使用すると、より良い結果を得るためにプロンプトを構造化する方法を学習するのに役立ちます。

1. GitHub Copilot によって提供される提案を確認し、**[承諾する]** を選択します。

    更新された SalesData データ構造は、次のコードのようになります。

    ```csharp

    public struct SalesData
    {
        public DateOnly dateSold;
        public string departmentName;
        public string productID;
        public int quantitySold;
        public double unitPrice;
        public double baseCost;
        public int volumeDiscount;
    }

    ```

新しいデータ構造と更新されたデータ構造を使用して、`GenerateSalesData` メソッドの更新に取り組むことができます。

### インライン チャットを使用して GenerateSalesData メソッドを更新する

プロジェクトの目標は、"実際の" データに似たデータ サンプルを生成するために、 `GenerateSalesData` メソッドを更新する必要があることを示しています。 部門コードと製造サイト コードの新しいフィールドを含むように、 `SalesData` データ構造が既に更新されています。 また、`productID` のデータ型を `int` から `string` に変更しました。 次に、`GenerateSalesData` メソッドを更新して、更新されたフィールドのデータを生成する必要があります。

次の更新プログラムを実装する必要があります。

- departmentName:割り当てられた値を更新します。 `ProdDepartments` データ構造からランダムに選択された部門名を割り当てます。
- productID:割り当てられた値を更新します。 ID のコンポーネントが次のように定義されているパターン "`DDDD-###-SS-CC-MMM`" を使用して productID をフォーマットします。

    - 部署を表す 4 文字のコード。 割り当てられた部門名に対応する `ProdDepartments` データ構造の省略形を使用します。
    - 製品を表す 3 桁の数値。 最初の数字は、ランダムに選択された部門のインデックス番号である必要があります。 次の 2 桁は 1 ~ 99 の乱数にする必要がありますが、先頭には 0 を含めます。 たとえば、1 は 01 としてフォーマットする必要があります。
    - 製品サイズを表す 2 文字のコード。 5 つのサイズのリストから製品サイズをランダムに選択します。XS、S、M、L、XL。
    - 製品の色を表す 2 文字のコード。 2 文字の色の省略形 8 種類からランダムに製品の色を選択します。BK、BL、GR、RD、YL、OR、WT、GY。
    - 製造サイトを表す 3 文字のコード。 `ManufacturingSites` データ構造から製造サイトをランダムに選択します。

- unitPrice:価格帯の下限を 25 に、上限を 300 に引き上げます。 サイズと色が単価に影響しないものとします。
- baseCost:製造コストを表す値を baseCost に割り当てます。 値は、unitPrice (5 ~ 20%) からランダムに生成された割引を使用して生成することができます。 現実的ではありませんが、このデモでは許容されます。
- volumeDiscount:小売購入者に与えられる割引率を表す値を volumeDiscount に割り当てます。 volumeDiscount に割り当てられる値は、quantitySold の 10% (19 ユニットの 10% = 1% volumeDiscount) の整数コンポーネントである必要があります。

`GenerateSalesData` メソッドを更新するには、次の手順を実行します。

1. Program.cs ファイルで `GenerateSalesData` メソッドを見つけます。

1. `departmentName` 値の割り当てに使用するコード行を選択します。

1. インライン チャット インターフェイスを開くには、キーボードの **Ctrl + I** キーを押します。

1. 次のプロンプトを入力します。

    ```output
    Update the departmentName assignment to randomly select a department name. Use the ProdDepartments data structure. 
    ```

1. GitHub Copilot によって提供される提案を確認し、**[承諾する]** を選択します。

1. `departmentName` 割り当ての後に 3 つの空白のコード行を作成します。

1. `productID` に割り当てられた値を構築する方法を検討するには、少し時間がかかります。

    productID 値は "`DDDD-###-SS-CC-MMM`" としてフォーマットする必要があります。ここで、ID のコンポーネントは次のように定義されます。

    - `DDDD` は、部署を表す 4 文字のコードです。 割り当てられた部門名に対応する `ProdDepartments` データ構造の省略形を使用します。
    - `###` は、製品を表す 3 つの数字です。 最初の桁は、部門のインデックス番号です。 次に、1 から 99 の乱数で、先頭に 0 を付けた値を指定します (例: "07" など)。
    - `SS` は、製品サイズを表す 2 文字のコードです。 5 つのサイズのリストから製品サイズをランダムに選択します。XS、S、M、L、XL。
    - `CC` は、製品の色を表す 2 文字のコードです。 2 文字の色の省略形 8 種類からランダムに製品の色を選択します。BK、BL、GR、RD、YL、OR、WT、GY。
    - `MMM` は、製造サイトを表す 3 文字のコードです。 `ManufacturingSites` データ構造から製造サイトをランダムに選択します。

    この書式指定は複雑すぎるため、1 つのプロンプトとして記述する必要があります。 これは、より小さなステップに分割する必要があります。

    選択した departmentName のインデックス番号を使用して departmentAbbreviation を選択し、製品番号の最初の桁を計算できることに注意してください。

1. 次の変数宣言をコピーし、作成した 2 番目の空白のコード行の場所に貼り付けます。

    ```csharp

    int indexOfDept = 0;
    string deptAbb = "";
    string firstDigit = "";
    string nextTwoDigits = "";
    string sizeCode = "";
    string colorCode = "";
    string manufacturingSite = "";

    ```

    変数宣言の前後に空白のコード行が必要です。

    インライン チャットでプロンプトからコード更新候補を生成するために変数宣言は必要ありませんが、これらは、GitHub Copilot が更新を適用すべき特定のコード行を認識するのに役立ちます。

1. `int indexOfDept = 0;` コード行を選択し、インライン チャットを開き、次のプロンプトを入力します。

    ```output
    Assign the array index for departmentName to indexOfDept.
    ```

1. GitHub Copilot によって提供される提案を確認します。

    選択した departmentName に対応する配列インデックス番号を indexOfDept に割り当てる提案が表示されます。

    予想される提案が表示されない場合は、**[破棄]** を選択して提案を拒否し、もう一度やり直すことができます。 次のプロンプトは、割り当ての追加のコンテキストを提供します。

    ```output
    Create an int named indexOfDept. Assign the array index number corresponding to the selected departmentName to indexOfDept.
    ```

    このプロンプトでは、`indexOfDept` という名前の整数変数の作成と、値の割り当て方法を指定します。 変数宣言を作成または選択せずにこのプロンプトを実行することもできますが、コードを選択せずにインライン チャットを開くと、GitHub Copilot がアンカー ポイントを失うことがあります。

    > [!NOTE]
    > **[変更の切り替え]** ボタン (**[受け入れる]** ボタンと **[破棄]** ボタンの右側にある **[その他のアクション]** ドロップダウン メニューからアクセスできます) を使用すると、推奨される更新プログラムによって削除されたコードを表示または非表示にすることができます。 これは、元のコードと推奨されるコードの更新を表示する場合に役立ちます。

1. GitHub Copilot から提供された提案を受け入れるには、**[承諾する]** を選択します。

1. `string deptAbb = "";` コード行を選択し、インライン チャットを開き、次のプロンプトを入力します。

    ```output
    Use indexOfDept to assign a department abbreviation to deptAbb.
    ```

1. GitHub Copilot によって提供される提案を確認します。

    選択した departmentName に対応する配列インデックス番号を indexOfDept に割り当てる提案が表示されます。

1. GitHub Copilot から提供された提案を受け入れるには、**[承諾する]** を選択します。

1. `string firstDigit = "";` コード行を選択し、インライン チャットを開き、次のプロンプトを入力します。

    ```output
    Assign indexOfDept + 1 to firstDigit.
    ```

1. GitHub Copilot によって提供される提案を確認し、**[承諾する]** を選択します。

1. `string string nextTwoDigits = ""; = "";` コード行を選択し、インライン チャットを開き、次のプロンプトを入力します。

    ```output
    Assign a random number 1-99 to nextTwoDigits. Include a leading 0 for numbers less than 10.
    ```

1. GitHub Copilot によって提供される提案を確認し、**[承諾する]** を選択します。

1. `string sizeCode = "";` コード行を選択し、インライン チャットを開き、次のプロンプトを入力します。

    ```output
    From the list {XS, S, M, L, XL}, randomly select a product size and assign it to sizeCode.
    ```

1. GitHub Copilot によって提供される提案を確認し、**[承諾する]** を選択します。

    この場合、ランダムに選択された製品サイズを `sizeCode` 変数に割り当てる提案が表示されます。 このプロンプトを満たすために 1 行または数行のコードを使用することが GitHub Copilot から提案されます。 どちらの方法でも、製品サイズの文字列配列を作成し、`random` を使用してサイズのいずれかを `sizeCode` に割り当てることが推奨されます。

1. `string colorCode = "";` コード行を選択し、インライン チャットを開き、次のプロンプトを入力します。

    ```output
    From the list {BK, BL, GR, RD, YL, OR, WT, GY}, randomly select a product color and assign it to colorCode.
    ```

1. GitHub Copilot によって提供される提案を確認し、**[承諾する]** を選択します。

1. `string manufacturingSite = "";` コード行を選択し、インライン チャットを開き、次のプロンプトを入力します。

    ```output
    Assign a randomly selected manufacturing site to manufacturingSite.
    ```

1. GitHub Copilot によって提供される提案を確認し、**[承諾する]** を選択します。

1. 少し時間を取ってコードを確認してください。

    productID の構築に使用する変数に値を割り当てる一連のコード行が必要です。 次の手順では、productID 値を構築します。

    ```csharp

    int indexOfDept = Array.IndexOf(ProdDepartments.departmentNames, salesData[i].departmentName);
    string deptAbb = ProdDepartments.departmentAbbreviations[indexOfDept];
    string firstDigit = (indexOfDept + 1).ToString();
    string nextTwoDigits = random.Next(1, 100).ToString("D2");
    string sizeCode = new string[] { "XS", "S", "M", "L", "XL" }[random.Next(0, 5)];
    string colorCode = new string[] { "BK", "BL", "GR", "RD", "YL", "OR", "WT", "GY" }[random.Next(0, 8)];
    string manufacturingSite = ManufacturingSites.manufacturingSites[random.Next(0, ManufacturingSites.manufacturingSites.Length)];

    ```

1. `salesData[i].productID = random.Next(1, 101);` コード行を選択し、インライン チャットを開き、次のプロンプトを入力します。

    ```output
    Add a "-" to deptAbb, nextTwoDigits, sizeCode, and colorCode. Combine deptAbb, firstDigit, nextTwoDigits, sizeCode, colorCode, and manufacturingSite to create the productID.
    ```

1. GitHub Copilot によって提供される提案を確認し、**[承諾する]** を選択します。

    前に割り当てた変数を使用して productID 値を構築する提案が表示されます。 提案には、productID を "`DDDD-###-SS-CC-MMM`" としてフォーマットするために必要なコードが含まれている必要があります。

1. 次のように、`unitPrice` の割り当てを手動で更新し、25 から 300 の範囲を使用します。

    ```csharp
    salesData[i].unitPrice = random.Next(25, 300) + random.NextDouble();
    ```

1. `unitPrice` 割り当ての後に空白行を作成します。

1. 表示されるコード行の入力候補を受け入れます。

    GitHub Copilot は、次のコード行のように表示される `baseCost` に値を割り当てる提案を提供する必要があります。

    ```csharp
    salesData[i].baseCost = random.Next(10, 100) + random.NextDouble();
    ```

1. `salesData[i].baseCost` に値を割り当てるために使用するコード行を選択し、インライン チャットを開き、次のプロンプトを入力します。

    ```output
    Discount the unitPrice by a random percentage between 5 and 20. Assign the result to baseCost.
    ```

1. GitHub Copilot によって提供される提案を確認し、**[承諾する]** を選択します。

1. `baseCost` 割り当ての後に空白行を作成し、表示されるコード行の入力候補を受け入れます。

    GitHub Copilot により、`volumeDiscount` に値を割り当てることが提案されます。

1. `salesData[i].volumeDiscount` に値を割り当てるために使用するコード行を選択し、インライン チャットを開き、次のプロンプトを入力します。

    ```output
    Assign 10 percent of quantitySold to volumeDiscount. Truncate any fractional values.
    ```

1. GitHub Copilot によって提供される提案を確認し、**[承諾する]** を選択します。

1. 更新された GenerateSalesData メソッドは、次のスニペットのようになります。

    ```csharp

    public SalesData[] GenerateSalesData()
    {
        SalesData[] salesData = new SalesData[1000];
        Random random = new Random();
        for (int i = 0; i < 1000; i++)
        {
            salesData[i].dateSold = new DateOnly(2023, random.Next(1, 13), random.Next(1, 29));
            salesData[i].departmentName = ProdDepartments.departmentNames[random.Next(0, ProdDepartments.departmentNames.Length)];
            int indexOfDept = Array.IndexOf(ProdDepartments.departmentNames, salesData[i].departmentName);
            string deptAbb = ProdDepartments.departmentAbbreviations[indexOfDept];
            string firstDigit = (indexOfDept + 1).ToString();
            string nextTwoDigits = random.Next(1, 100).ToString("D2");
            string sizeCode = new string[] { "XS", "S", "M", "L", "XL" }[random.Next(0, 5)];
            string colorCode = new string[] { "BK", "BL", "GR", "RD", "YL", "OR", "WT", "GY" }[random.Next(0, 8)];
            string manufacturingSite = ManufacturingSites.manufacturingSites[random.Next(0, ManufacturingSites.manufacturingSites.Length)];
            salesData[i].productID = $"{deptAbb}-{firstDigit}{nextTwoDigits}-{sizeCode}-{colorCode}-{manufacturingSite}";
            salesData[i].quantitySold = random.Next(1, 101);
            salesData[i].unitPrice = random.Next(25, 300) + random.NextDouble();
            salesData[i].baseCost = salesData[i].unitPrice * (1 - (random.Next(5, 21) / 100.0));
            salesData[i].volumeDiscount = (int)(salesData[i].quantitySold * 0.1);
        }
        return salesData;
    }

    ```

1. 変更を保存。

### インライン チャットを使用して QuarterlySalesReport メソッドを更新する

`QuarterlySalesReport` メソッドを更新する必要があります。 プロジェクトの目標に基づいて、次の更新プログラムを実装する必要があります。

- 販売結果を表示するときに、結果を論理的な順序で一覧表示します。 たとえば、四半期ごとの売上合計を一覧表示する場合、四半期は第 1 四半期から第 4 四半期までの順序で一覧表示されます。
- 地域設定を使用して通貨値を表示します。
- 四半期利益および利益率の計算を追加する
- 四半期ごとの売上、利益、利益率など、個々の部門に固有の計算を追加します。
- 四半期ごとの売上、利益、利益率など、特定の製造場所の計算を追加します。

この時点で、`QuarterlySalesReport` メソッドは次のコード スニペットのようになります。

```csharp

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
        Console.WriteLine("{0}: ${1}", quarter.Key, quarter.Value);
    }
}

```

`QuarterlySalesReport` メソッドを更新するには、次の手順を実行します。

1. 現在の四半期売上レポートの出力を確認するには、アプリケーションを実行します。

    四半期ごとの売上結果の一覧がコンソール ウィンドウに表示されます。 ランダムな値が使用されるため、数値データは実行ごとに異なります。

    四半期ごとの売上レポートの出力は次のようになります。

    ```output
    Quarterly Sales Report
    ----------------------
    Q3: $2060165.1045630067
    Q2: $2000706.5521363618
    Q4: $2168920.603583816
    Q1: $2174302.3663762277
    ```

    四半期が順に表示されず、通貨値が正しくフォーマットされていないことに注意してください。

    最初のタスクは、これらの問題を解決することです。

1. Program.cs ファイルで `QuarterlySalesReport` メソッドを見つけます。

1. メソッド全体を選択します。

1. インライン チャット インターフェイスを開き、次のプロンプトを入力します。

    ```output
    Update the QuarterlySalesReport method to display quarterly results in order. Format currency using regional settings. 
    ```

1. GitHub Copilot によって提供される提案を確認するには、少し時間がかかります。

    四半期ごとの利益と利益率を計算するために必要なコードを含む提案が表示されます。 提案には、四半期ごとの利益と利益率を計算するために必要なコードが含まれています。

1. GitHub Copilot から提供された提案を受け入れるには、**[承諾する]** を選択します。

1. 変更を保存。

1. アプリケーションを実行し、四半期ごとの売上の結果が順番に表示され、通貨値が正しくフォーマットされていることを確認します。

    数値は異なりますが、四半期ごとの売上レポートの出力は、次の出力のようにフォーマットされます。

    ```output
    Quarterly Sales Report
    ----------------------
    Q1: $2,174,302.37
    Q2: $2,000,706.55
    Q3: $2,060,165.10
    Q4: $2,168,920.60

    ```

    次の手順では、四半期ごとの利益と利益率の計算を追加します。

1. Program.cs ファイルで `QuarterlySalesReport` メソッドを見つけます。

1. メソッド全体を選択します。

1. インライン チャット インターフェイスを開き、次のプロンプトを入力します。

    ```output
    Update the QuarterlySalesReport method to include calculations for quarterly profit and profit percentage. Include the new calculations in the report output.
    ```

1. GitHub Copilot によって提供される提案を確認するには、少し時間がかかります。

    四半期ごとの利益と利益率を計算するために必要なコードを含む提案が表示されます。 提案には、四半期ごとの利益と利益率を計算するために必要なコードが含まれています。

1. GitHub Copilot から提供された提案を受け入れるには、**[承諾する]** を選択します。

1. 残りの提案に対しても **[承諾する]** を選択して続けてください。

1. 変更を保存。

1. アプリケーションを実行し、四半期ごとの売上結果に利益と利益率の計算が含まれるようになったことを確認します。

    数値は異なりますが、四半期ごとの売上レポートの出力は、次の出力のようにフォーマットされます。

    ```output
    Quarterly Sales Report
    ----------------------
    Q1: Sales: $1,881,091.17, Profit: $231,351.24, Profit Percentage: 12.00%
    Q2: Sales: $1,949,240.91, Profit: $244,649.35, Profit Percentage: 11.00%
    Q3: Sales: $2,298,017.35, Profit: $273,622.53, Profit Percentage: 5.00%
    Q4: Sales: $2,279,185.96, Profit: $272,548.80, Profit Percentage: 16.00%    

    ```

    次の手順では、部門別の四半期売上、利益、および利益率の計算を追加します。

1. メソッド全体を選択します。

1. インライン チャット インターフェイスを開き、次のプロンプトを入力します。

    ```output
    Update the QuarterlySalesReport method to include calculations for quarterly sales, profit, and profit percentage by department. Include the new calculations in the report output. 
    ```

1. GitHub Copilot によって提供される提案を確認するには、少し時間がかかります。

    四半期ごとの利益と利益率を計算するために必要なコードを含む提案が表示されます。 提案には、四半期ごとの利益と利益率を計算するために必要なコードが含まれています。

1. GitHub Copilot から提供された提案を受け入れるには、**[承諾する]** を選択します。

1. 残りの提案に対しても **[承諾する]** を選択して続けてください。

1. 変更を保存。

1. アプリケーションを実行し、四半期ごとの売上結果に利益と利益率の計算が含まれるようになったことを確認します。

    数値は異なりますが、四半期ごとの売上レポートの出力は、次の出力のようにフォーマットされます。

    ```output
    Quarterly Sales Report
    ----------------------
    Q1: Sales: $2,043,493.57, Profit: $262,571.72, Profit Percentage: 14.00%
    By Department:
    Department: Accessories, Sales: $188,977.90, Profit: $25,229.53, Profit Percentage: 14.00%
    Department: Children's Clothing, Sales: $186,552.49, Profit: $25,511.74, Profit Percentage: 13.00%
    Department: Footwear, Sales: $293,706.49, Profit: $39,224.99, Profit Percentage: 19.00%
    Department: Men's Clothing, Sales: $301,385.47, Profit: $36,756.06, Profit Percentage: 19.00%
    Department: Outerwear, Sales: $238,099.65, Profit: $24,371.92, Profit Percentage: 15.00%
    Department: Sportswear, Sales: $251,349.38, Profit: $34,142.40, Profit Percentage: 8.00%
    Department: Undergarments, Sales: $297,690.60, Profit: $35,305.13, Profit Percentage: 9.00%
    Department: Women's Clothing, Sales: $285,731.58, Profit: $42,029.95, Profit Percentage: 19.00%
    
    Q2: Sales: $1,925,948.90, Profit: $232,929.95, Profit Percentage: 17.00%
    By Department:
    Department: Accessories, Sales: $251,572.42, Profit: $33,250.17, Profit Percentage: 11.00%
    Department: Children's Clothing, Sales: $311,862.99, Profit: $36,537.33, Profit Percentage: 8.00%
    Department: Footwear, Sales: $203,148.87, Profit: $23,041.46, Profit Percentage: 11.00%
    Department: Men's Clothing, Sales: $229,781.14, Profit: $26,226.68, Profit Percentage: 9.00%
    Department: Outerwear, Sales: $211,610.47, Profit: $23,684.65, Profit Percentage: 9.00%
    Department: Sportswear, Sales: $204,083.63, Profit: $20,750.56, Profit Percentage: 8.00%
    Department: Undergarments, Sales: $264,733.26, Profit: $35,155.66, Profit Percentage: 15.00%
    Department: Women's Clothing, Sales: $249,156.13, Profit: $34,283.45, Profit Percentage: 17.00%
    
    Q3: Sales: $2,113,223.50, Profit: $256,591.16, Profit Percentage: 7.00%
    By Department:
    Department: Accessories, Sales: $288,161.91, Profit: $32,279.54, Profit Percentage: 10.00%
    Department: Children's Clothing, Sales: $198,313.55, Profit: $24,146.72, Profit Percentage: 7.00%
    Department: Footwear, Sales: $205,840.60, Profit: $27,630.49, Profit Percentage: 5.00%
    Department: Men's Clothing, Sales: $229,279.26, Profit: $26,618.62, Profit Percentage: 13.00%
    Department: Outerwear, Sales: $353,696.46, Profit: $44,634.82, Profit Percentage: 14.00%
    Department: Sportswear, Sales: $229,490.12, Profit: $27,697.91, Profit Percentage: 5.00%
    Department: Undergarments, Sales: $316,942.44, Profit: $40,518.71, Profit Percentage: 5.00%
    Department: Women's Clothing, Sales: $291,499.15, Profit: $33,064.35, Profit Percentage: 10.00%
    
    Q4: Sales: $1,896,279.88, Profit: $248,226.28, Profit Percentage: 15.00%
    By Department:
    Department: Accessories, Sales: $336,698.68, Profit: $44,714.55, Profit Percentage: 11.00%
    Department: Children's Clothing, Sales: $193,345.18, Profit: $23,261.33, Profit Percentage: 13.00%
    Department: Footwear, Sales: $215,183.23, Profit: $29,616.00, Profit Percentage: 15.00%
    Department: Men's Clothing, Sales: $171,663.38, Profit: $24,299.37, Profit Percentage: 5.00%
    Department: Outerwear, Sales: $229,791.52, Profit: $28,211.17, Profit Percentage: 15.00%
    Department: Sportswear, Sales: $230,031.90, Profit: $32,732.40, Profit Percentage: 8.00%
    Department: Undergarments, Sales: $300,824.19, Profit: $34,649.79, Profit Percentage: 6.00%
    Department: Women's Clothing, Sales: $218,741.80, Profit: $30,741.67, Profit Percentage: 20.00%

    ```

### まとめ

このデモでは、インライン チャット機能を使用して、`GenerateSalesData` メソッドと `QuarterlySalesReport` メソッドを更新しました。 `SalesData` データ構造に新しいフィールドを追加し、`GenerateSalesData` メソッドを更新して新しいフィールドのデータを生成しました。 また、四半期利益と利益率の計算を含むように `QuarterlySalesReport` メソッドを更新しました。 また、部門別の四半期売上、利益、利益率の計算も追加しました。
