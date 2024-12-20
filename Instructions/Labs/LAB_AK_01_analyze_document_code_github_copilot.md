---
lab:
  title: 'ラボ: GitHub Copilot を使用してアプリ開発を加速する'
  type: Answer Key
  module: Modules 2-5
---

# ラボ: GitHub Copilot を使用してアプリ開発を加速する
# 学生ラボ回答キー

## パート 1: GitHub Copilot ツールを使用してコードを分析および文書化する

### 開始する前に

#### プロジェクトの概要

あなたは、地域の IT 部門で働くソフトウェア開発者だとします。 携わっているアプリケーションのほとんどは、ローカル コミュニティをサポートするものです。 最近、コミュニティ図書館のサーバーが事故で破損しました。それを置き換える承認を得るのに数週間を要します。 あなたの部署は、司書が基本的な機能を実行できるようにするための一時的なソリューションを開発する必要があります。

あなたのチームは、司書に聞き取りを行いました。 彼らは、書籍の貸し出しや返却などの基本的なサービスを図書館の利用者に提供することを可能にする、最小限のソリューションを必要としています。 あなたのチームは利用可能なリソースを調査し、計画を策定します。 最初は、あなたともう 1 人の同僚だけがプロジェクトに割り当てられます。 一時的なソリューションが利用可能になるまで、自治体によって図書館は閉館されました。 図書館の再開を可能にする v1 ソリューションの開発に 3 日かけられます。

同僚がソフトウェアの作業を始める間、あなたは、図書館の記録を使用して、図書館の利用者のアカウント、書籍、書籍の貸し出しを表す JSON ファイルを作成します。 2 日目の終わりまでに、コードのサポートを開始する準備が整いました。 このソリューションは、図書館のラップトップ コンピューターのいずれかで実行できるコンソール アプリケーションです。 司書は、美しいインターフェイスを作る時間がないことは理解していますが、アプリが安全で信頼性が高い必要があることを強調しています。 アプリのバージョン 1.0 のデモンストレーションを行う期限まで、あと 1 日あります。

GitHub Copilot を使用して、作業を可能な限り効率的に行います。 すべてがうまくいけば、将来的に、このアプリは図書寄贈活動やその他のオフサイト機能をサポートするために使用されます。

#### ラボ シナリオ (パート 1)

GitHub Copilot は、説明やドキュメントを生成することで、コードベースを理解して文書化するのに役立ちます。

このラボのパート 1 では、GitHub Copilot を使用して図書館アプリケーションを分析および文書化します。 また、ライブラリ アプリケーション用の GitHub リポジトリを作成し、GitHub Copilot を使用してリポジトリの README ファイルを生成します。

パート 1 には、次の演習が含まれています。

- Visual Studio Code 用の GitHub Copilot 拡張機能を構成する。
- GitHub Copilot を使用して、ライブラリ アプリケーションのコードベースを説明する。
- Visual Studio Code を使用して、ライブラリ アプリケーション用の GitHub リポジトリを作成する。
- GitHub Copilot 拡張機能を使用して、リポジトリの README.md ファイルを作成する。

### 演習 1: GitHub Copilot 拡張機能を Visual Studio Code 用に構成する

GitHub アカウントを使用して、Visual Studio Code に GitHub Copilot サブスクリプションの確認を許可します。

次の手順に従って、GitHub Copilot 拡張機能をインストールします。

1. ブラウザー ウィンドウを開きます。

1. GitHub Enterprise ポータルを開くには、次の URL に移動します。

    ```plaintext
    https://github.com/enterprises/Microsoft-APL/sso
    ```

1. 次の資格情報を使用して、お使いの GitHub アカウントにサインインします。

    メールアドレス/ユーザー名: `@lab.CloudPortalCredential(1).Username`

    パスワード: `@lab.CloudPortalCredential(1).Password`

1. Visual Studio Code を開きます。

1. 左側のメニューで、**[拡張機能]** を選択します。

1. [Marketplace で拡張機能を検索する] テキスト ボックスに「**GitHub Copilot**」と入力し、Enter キーを押します。

1. フィルター処理された拡張機能一覧で、GitHub によって作成された **GitHub Copilot** 拡張機能を選択します。

1. GitHub Copilot 拡張機能ページで、**[インストール]** を選択します。

1. "Sign in to use GitHub Copilot" という通知が表示されたら、**[Sign in to GitHub]** を選択します。

    GitHub を使用してサインインすることを GitHub Copilot が求めているという内容のメッセージ ダイアログが表示された場合は、**[Allow]** を選択します。

    ブラウザー ウィンドウで GitHub アカウントに既にサインインしているので、ブラウザー ウィンドウに新しい [Verify Session] タブが開きます。

1. [Verify Session] ページで、**[Continue]** を選択します。

1. [Authorize Application] ページで、**[Authorize Visual Studio Code]** を選択します。

1. Visual Studio Code に戻るには、**[開く]** を選択します。

1. Visual Studio Code を閉じて、次に再度開きます。

    Visual Studio Code を再起動すると、GitHub Copilot が Visual Studio Code ユーザー インターフェイスに統合されていることを確認できます。

1. Visual Studio Code ウィンドウの場合、上部のコマンド センターの右側に **[チャットを開く]** ボタンが表示されます。

#### 概要 – 演習 1

この演習では、Visual Studio Code で GitHub Copilot 拡張機能をインストールしました。 また、GitHub アカウントへアクセスするために、Visual Studio Code を認証しました。 これで、GitHub Copilot を使用してライブラリ アプリケーションのコードベースを分析および文書化する準備ができました。

### 演習 2: ライブラリ アプリケーションのコードベースを分析する

コード リポジトリと README ファイルを作成する前に、少し時間を取って、コードベースを調べる必要があります。 プロジェクトを文書化する前に、アプリのアーキテクチャと主な機能を理解しておくことが重要です。 また、アプリケーションを実行して、期待どおりに動作するようにする必要もあります。

#### タスク 1: 開発環境にライブラリ アプリケーションを読み込む

あなたの同僚は、図書館アプリケーションの初期バージョンを開発し、.zip ファイルとして使用できるようにしました。 このラボを準備するには、次のアクションを実行する必要があります。

- ソリューションを含む zip ファイルをダウンロードします。
- コード ファイルを抽出します。
- Visual Studio Code でライブラリ アプリケーションを開き、正常にビルドされていることを確認します。

次の手順を使用してライブラリー アプリケーションを準備します。

1. Web ブラウザーが開かれていることを確認し、新しいブラウザー タブを開きます。

1. コード プロジェクトを含む zip ファイルをダウンロードするには、次の URL に移動します。

    ```plaintext
    https://raw.githubusercontent.com/MicrosoftLearning/APL-2007-Accelerate-app-development-by-using-GitHub-Copilot/master/LearnModuleExercises/Downloads/GuidedProjectApp.zip
    ```

    ソリューション コードを含む zip ファイル (GuidedProjectApp.zip) が自動的にダウンロードされます。

1. ダウンロードが完了したら、ブラウザー タブを閉じます。

    GitHub アカウントのブラウザー ページを開いたままにしておきます。 このファイルは、このラボで後ほど使用します。

1. Windows エクスプローラーを開き、[ダウンロード] フォルダーに移動します。

1. ダウンロードしたプロジェクト ファイルを解凍します。

    開発環境でコード プロジェクトを解凍します。 次に例を示します。

    1. ローカル コンピューターで、ダウンロード フォルダーに移動します。

    1. **GuidedProjectApp.zip** を右クリックし、**[すべて抽出]** を選択します。

    1. **[完了時に展開されたファイルを表示する]** を選んでから、**[展開]** を選びます。

    1. 展開したフォルダーの場所をメモしておきます。

1. 抽出した AccelerateDevGitHubCopilot フォルダーを、Windows デスクトップ フォルダーなど、アクセスしやすい場所にコピーします。

1. Visual Studio Code で **AccelerateDevGitHubCopilot** フォルダーを開きます。

    次に例を示します。

    1. PC で Visual Studio Code を開きます。

    1. Visual Studio Code の **[ファイル]** メニューで、 **[フォルダーを開く]** を選択します。

    1. Windows デスクトップ フォルダーに移動し、**AccelerateDevGitHubCopilot** フォルダーを見つけます。

    1. **AccelerateDevGitHubCopilot** を選択し、**[フォルダーの選択]** を選択します。

    1. **[はい、作成者を信頼します]** を選択します。

    > [!NOTE]
    > Visual Studio Code がプロジェクト ファイルと必要な .NET 更新プログラムを読み込むには、10 ~ 20 秒かかる場合があります。

1. Visual Studio Code のエクスプローラー ビューで、ソリューション エクスプローラーを選択し、次のプロジェクト構造を確認します。

    - AccelerateDevGitHubCopilot\
        - src\
            - Library.ApplicationCore\
            - Library.Console\
            - Library.Infrastructure\
        - tests\
            - UnitTests\

1. ソリューションが正常にビルドされていることを確認します。

    たとえば、ソリューション エクスプローラー ビューで **AccelerateDevGitHubCopilot** を右クリックし、**[ビルド]** を選択します。

    報告されたいくつかの**警告**が表示されますが、エラーは表示されないはずです。 この演習の後半でアプリケーションを実行します。

    > [!NOTE]
    > 講師から指示がない限り、ワークロードの更新プログラムをインストールしないでください。

#### タスク 2: GitHub Copilot を使用してライブラリ アプリケーションのコードベースを説明する

GitHub Copilot は、ソリューションと機能レベルで説明を生成することで、未知のコードベースを理解するのに役立ちます。

以下の手順に従って、演習のこのセクションを完了します。

1. Visual Studio Code に AccelerateDevGitHubCopilot ソリューションが開かれていることを確認します。

1. チャット ビューを開きます。

    チャット ビューは、次の 方法で開くことができます。

    - **[チャットを開く]** ボタンを選択します。(このボタンは、Visual Studio Code ウィンドウの上部にあり、コマンド センターのちょうど右側に位置します。)
    - **Ctrl + Alt + I** キーボード ショートカットを使用します。
    - GitHub Copilot 状態メニューを開き、**[GitHub Copilot Chat]** を選択します。

1. GitHub Copilot の **@workspace** 参加者を使用するプロンプトを入力し、プロジェクトの説明を生成します。

    たとえば、チャット ビューに次のプロンプトを入力します。

    ```plaintext
    @workspace Describe this project
    ```

    "GitHub Copilot Chat wants to sign in using GitHub" という Visual Studio Code ダイアログ ボックスが表示された場合は、**[許可]** を選択してから、GitHub アカウントを使用して承認プロセスを完了します。

1. 少し時間を取って、GitHub Copilot によって生成された応答を確認してください。

    次の説明のような応答が表示されます。

    ```markdown
    This project is a library management system implemented in C#. It consists of three main components:
    
    1. **Library.ApplicationCore**: This is the core application library containing the main business logic, entities, enums, and interfaces. It includes:
        - Entities such as Book, Patron, Loan, etc.
        - Enums like MembershipRenewalStatus, LoanReturnStatus, and LoanExtensionStatus.
        - Services like LoanService and PatronService.
        - Interfaces like ILoanRepository, IPatronRepository, ILoanService, and IPatronService.
    2. **Library.Console**: This is a console application that interacts with the user. It includes:
        - The main entry point in Program.cs.
        - Configuration settings in appSettings.json.
        - Console interaction logic in ConsoleApp.cs.
    3. **Library.Infrastructure**: This library handles data persistence. It includes:
        - JSON-based repositories like JsonPatronRepository and JsonLoanRepository.
        - Data loading and saving logic in JsonData.

    Additionally, there are unit tests located in the UnitTests directory, which test the functionality of the core services using the NSubstitute mocking framework and xUnit.
    
    The project uses .NET 8.0 and is configured to build and test using GitHub Actions as defined in the build-test.yml file. The solution file is AccelerateDevGitHubCopilot.sln, which includes all the projects and their configurations.
    ```

1. Visual Studio Code ソリューション エクスプローラー ビューでプロジェクト フォルダーを展開します。

1. **ConsoleApp.cs** ファイルを見つけて開きます。

    ConsoleApp.cs ファイルは src/Library.Console プロジェクトにあります。

1. ConsoleApp classの説明を生成するプロンプトをチャット ビューに入力します。

    たとえば、チャット ビューに次のプロンプトを入力します。

    ```plaintext
    @workspace #editor Describe the ConsoleApp class
    ```

1. 数分かけて応答を確認します。

    次の説明のような応答が表示されます。

    ```markdown
    The ConsoleApp class in ConsoleApp.cs is responsible for managing the console-based user interface of the library management system. It handles user interactions, processes user inputs, and coordinates actions with the underlying services and repositories.

    ### Fields
    - _currentState: Tracks the current state of the console application.
    - matchingPatrons: A list of patrons that match a search query.
    - selectedPatronDetails: Holds details of the currently selected patron.
    - selectedLoanDetails: Holds details of the currently selected loan.
    - _patronRepository: An instance of IPatronRepository for accessing patron data.
    - _loanRepository: An instance of ILoanRepository for accessing loan data.
    - _loanService: An instance of ILoanService for performing loan-related operations.
    - _patronService: An instance of IPatronService for performing patron-related operations.

    ### Constructor
    - ConsoleApp(ILoanService loanService, IPatronService patronService, IPatronRepository patronRepository, ILoanRepository loanRepository): Initializes the ConsoleApp with the provided services and repositories.

    ### Methods
    - Run(): The main entry point for running the console application.
    - PatronSearch(): Handles the logic for searching patrons.
    - ReadPatronName(): Reads the patron's name from the console input.
    - PrintPatronsList(List<Patron> matchingPatrons): Prints a list of matching patrons to the console.
    - PatronSearchResults(): Handles the logic for displaying and selecting from the search results.
    - ReadInputOptions(CommonActions options, out int optionNumber): Reads input options from the console.
    - WriteInputOptions(CommonActions options): Writes the available input options to the console.
    - PatronDetails(): Displays details of the selected patron.
    - LoanDetails(): Displays details of the selected loan and handles actions like extending or returning the loan.

    The class uses a state machine approach to manage different states of the console application, such as searching for patrons, displaying search results, showing patron details, and handling loan details.
    ```

1. **Program.cs** ファイルを開きます。

1. Program.cs ファイルの説明を生成するプロンプトをチャット ビューに入力します。

    たとえば、チャット ビューに次のプロンプトを入力します。

    ```plaintext
    @workspace #editor Describe the Program.cs file
    ```

1. 数分かけて応答を確認します。

    次の説明のような応答が表示されます。

    ```markdown
    The Program.cs file is the entry point for the console application. It sets up the dependency injection container, configures services, and starts the ConsoleApp.
    
    1. **Dependency Injection Setup**:
        - Creates a ServiceCollection to register services.
        - Builds a configuration object from the appSettings.json file.
        - Registers various services and repositories with different lifetimes (singleton, scoped).
    
    2. **Service Registration**:
        - Registers the repositories: JsonPatronRepository and JsonLoanRepository.
        - Registers the services: LoanService and PatronService.
        - Registers the JsonData class as a singleton.
        - Registers the ConsoleApp class as a singleton.
    
    3. **Service Provider**:
        - Builds the service provider from the registered services.
        - Retrieves the ConsoleApp service and runs it asynchronously.

    This setup ensures that all dependencies are properly injected and configured before the application starts running.
    ```

1. Library.Infrastructure プロジェクトを展開し、次にデータ フォルダーを展開します。

1. **JsonData.cs**、**JsonLoanRepository.cs**、および**JsonPatronRepository.cs**ファイルをチャット コンテキストに追加します。

    ドラッグ アンド ドロップ操作を使用して、ソリューション エクスプローラーからチャット ビューにファイルを追加できます。 チャット ビューの **[コンテキスト添付]** ボタン (ペーパー クリップ) を使用して、チャット コンテキストにファイルを追加することもできます。

1. データ アクセス クラスの説明を生成するプロンプトをチャット ビューに入力します。

    たとえば、チャット ビューに次のプロンプトを入力します。

    ```plaintext
    @workspace /explain Explain how the data access classes work
    ```

1. 数分かけて応答を確認します。

    次の説明のような応答が表示されます。

    ```markdown
    The data access classes in this project are designed to handle the loading, saving, and manipulation of data stored in JSON files. These classes include JsonData, JsonPatronRepository, and JsonLoanRepository. Here's an explanation of how each class works:
    
    ### JsonData Class
    The JsonData class is responsible for loading and saving data from and to JSON files. It also provides methods to populate related entities.
    
    #### Key Responsibilities:
    1. **Loading Data**: The LoadData method loads data from JSON files into in-memory collections (Authors, Books, BookItems, Patrons, Loans).
    2. **Saving Data**: The SaveJson method saves data to JSON files. Specific methods like SaveLoans and SavePatrons handle saving loans and patrons, respectively.
    3. **Ensuring Data is Loaded**: The EnsureDataLoaded method ensures that data is loaded into memory before any operations are performed.
    4. **Populating Related Entities**: Methods like GetPopulatedPatron, GetPopulatedLoan, GetPopulatedBookItem, and GetPopulatedBook populate related entities to provide a complete view of the data.
    
    #### Example Methods:
    - **LoadData**: Loads all data from JSON files.
    - **SaveLoans**: Saves loan data to the JSON file.
    - **GetPopulatedPatron**: Populates a patron with related loans.
    - **SearchBookByTitle**: Searches for a book by its title.
    
    ### JsonPatronRepository Class
    The JsonPatronRepository class implements the IPatronRepository interface and provides methods to interact with patron data.

    #### Key Responsibilities:
    1. **Searching Patrons**: The SearchPatrons method searches for patrons by name. 
    2. **Getting a Patron**: The GetPatron method retrieves a patron by ID and populates related data.
    3. **Updating a Patron**: The UpdatePatron method updates patron information and saves it to the JSON file.
    
    #### Example Methods:
    - **SearchPatrons**: Searches for patrons whose names contain the search input.
    - **GetPatron**: Retrieves a patron by ID and populates related loans.
    - **UpdatePatron**: Updates patron information and saves it to the JSON file.
    
    ### JsonLoanRepository Class
    The JsonLoanRepository class implements the ILoanRepository interface and provides methods to interact with loan data.
    
    #### Key Responsibilities:
    1. **Getting a Loan**: The GetLoan method retrieves a loan by ID and populates related data.
    2. **Updating a Loan**: The UpdateLoan method updates loan information and saves it to the JSON file.
    
    #### Example Methods:
    - **GetLoan**: Retrieves a loan by ID and populates related book items and patrons.
    - **UpdateLoan**: Updates loan information and saves it to the JSON file.
    
    ### How They Work Together
    1. **Loading Data**: When the application starts, the JsonData class loads data from JSON files into memory.
    2. **Searching and Retrieving Data**: The JsonPatronRepository and JsonLoanRepository classes use the JsonData class to search and retrieve data. They ensure data is loaded before performing operations.
    3. **Updating Data**: When data is updated, the repository classes call methods on the JsonData class to save the updated data back to the JSON files.
    4. **Populating Related Entities**: The JsonData class provides methods to populate related entities, ensuring that when a patron or loan is retrieved, it includes related data like loans or book items.
    
    ### Example Workflow
    1. **Search for a Patron**:
        - The SearchPatrons method in JsonPatronRepository calls EnsureDataLoaded to ensure data is loaded.
        - It then searches the Patrons collection for matching names and returns the results.

    2. **Get a Loan**:
       - The GetLoan method in JsonLoanRepository calls EnsureDataLoaded to ensure data is loaded.
       - It retrieves the loan by ID and uses GetPopulatedLoan to include related book items and patrons.

    3. **Update a Patron**:
       - The UpdatePatron method in JsonPatronRepository calls EnsureDataLoaded to ensure data is loaded.
       - It updates the patron information and calls SavePatrons to save the updated data to the JSON file.

    By using these data access classes, the application can efficiently manage data stored in JSON files, ensuring that data is loaded, manipulated, and saved correctly.
    ```

1. 数分間をかけて、ライブラリ レコードのシミュレートに使用される JSON データ ファイルを調べます。

    JSON データ ファイルは、src/Library.Console/Jsonフォルダーにあります。

    データ ファイルは、ID プロパティを使用してエンティティをリンクします。 たとえば、ローン オブジェクトには、同じ ID を持つ パトロン オブジェクトにリンクする PatronId プロパティがあります。 JSON ファイルには、著者、書籍、書籍アイテム、パトロン、ローンのデータが含まれています。

    > [!NOTE]
    > このガイド付きプロジェクトの目的上、著者名、書籍タイトル、パトロン名は匿名になっています。

#### タスク 3: アプリケーションをビルドして実行する

アプリケーションを実行すると、ユーザー インターフェイス、アプリケーションの主な機能、アプリ コンポーネントの相互作用を理解するのに役立ちます。

以下の手順に従って、演習のこのセクションを完了します。

1. **ソリューション エクスプローラー** ビューが開かれていることを確認します。

    ソリューション エクスプローラー ビューは、エクスプローラー ビューと同じではありません。 ソリューション エクスプローラー ビューは、プロジェクト ファイルとソリューション ファイルを "ディレクトリ" ノードとして使用して、ソリューションの構造を表示します。

1. アプリケーションを実行するには、**Library.Console** を右クリックし、**[デバッグ]** を選択してから **[新しいインスタンスを開始]** を選択します。

    **[デバッグ]** と **[新しいインスタンスを開始]** オプションが表示されない場合は、エクスプローラー ビューではなくソリューション エクスプローラー ビューを使用していることを確認します。

    次の手順では、簡単なユース ケースについて説明します。

1. パトロン名の入力を求められたら、「**One**」と入力して Enter キーを押します。

    > [!NOTE]
    > アプリケーションは、大文字と小文字を区別する検索プロセスを使用します。 "O" が大文字の "One" を入力する必要があります。

    検索クエリに一致する利用者の一覧が表示されます。

1. "Input Options" プロンプトで「**2**」と入力し、Enter キーを押します。

    「**2**」と入力すると、リストにある 2 番目のパトロンが選択されます。

    パトロンの名前とメンバーシップの状態が表示され、その後に書籍ローンの詳細が表示されます。

1. "Input Options" プロンプトで「**1**」と入力し、Enter キーを押します。

    「**1**」と入力すると、リストにある最初の書籍が選択されます。

    期限や返却状況など、書籍の詳細が一覧表示されます。

1. "Input Options" プロンプトで「**r**」と入力し、Enter キーを押します。

    「**r**」と入力すると、書籍が返されます。

1. "Book was successfully returned." (ブックが正常に返されました。) というメッセージを確認します。 確認します。

    "Book was successfully returned." (ブックが正常に返されました。) というメッセージ の後に書籍の詳細が続く必要があります。 返されたブックは **Returned: True** でマークされます。

1. 新しい検索を開始するには、「**s**」と入力して Enter キーを押します。

1. パトロン名の入力を求められたら、「**One**」と入力して Enter キーを押します。

1. "Input Options" プロンプトで「**2**」と入力し、Enter キーを押します。

1. 最初の書籍貸出が **Returned: True** とマークされていることを確認します。

1. "Input Options" プロンプトで「**q**」と入力し、Enter キーを押します。

1. デバッグ セッションを停止します。

#### 概要 – 演習 2

この演習は、ライブラリ アプリケーションのコードベースと、アプリケーションがユーザーとどのように対話するかを理解するのに役立ちました。 GitHub Copilot を使用して、プロジェクト構造、選択したファイル、およびデータ アクセス クラスの説明を生成しました。 また、アプリケーションを実行して、コンソール インターフェイスの動作とアプリケーション コンポーネントの対話方法を確認しました。

### 演習 3: GitHub リポジトリと空の Readme ファイルを作成する

コード用の GitHub リポジトリを作成すると、他のユーザーと作業を共有したり、プロジェクトで共同作業を行うことができます。

#### タスク 1: GitHub リポジトリを作成する

以下の手順に従って、演習のこのセクションを完了します。

1. ブラウザー ウィンドウで GitHub アカウントを開いた状態にします。

    必要に応じて、ブラウザー ウィンドウを開き、次の情報を使用してログインします。

    URL: `https://github.com/enterprises/Microsoft-APL/sso`

    メールアドレス/ユーザー名: `@lab.CloudPortalCredential(1).Username`

    パスワード: `@lab.CloudPortalCredential(1).Password`

1. GitHub アカウント メニューを開き、**[ご使用のリポジトリ]** を選択します。

    リポジトリがまだ存在しないことを示すメッセージが表示されるはずです。

1. GitHub アカウントの資格情報を使用する Git 構成コマンドを作成するには、**メモ帳**を開き、次の Git コマンドを構築します。

    ```bash
    git config --global user.email "lab assigned email"
    git config --global user.name "user name"
    ```

    「**lab assigned email**」を、ラボ環境で定義されているメールアドレス `@lab.CloudPortalCredential(1).Username` に置き換えます。

    「**user name**」を自分の名前に置き換えます。

1. [Visual Studio Code] ウィンドウに切り替えます。

1. Visual Studio Code の統合ターミナルを開きます。

    [ターミナル] メニューで、**[新しいターミナル]** を選択します。

1. GitHub アカウントに関連付けられている資格情報を使用して Git を構成するには、メモ帳で作成した 2 つのコマンドを入力します。

1. Visual Studio Code で、ソース管理ビューを開きます。

1. **[GitHub に公開]** を選択します。

    GitHub アカウントを使用してサインインするように求めるダイアログ ボックスが開いた場合は、次の手順を実行します。

    1. **許可**を選択してださい。
    1. このラボ環境で使用するアカウントを選択します。
    1. 必要に応じて、**[GitHub に公開]** を再度選択します。

1. リポジトリの既定の名前 (AccelerateDevGitHubCopilot) をそのまま使用し、**[GitHub プライベート リポジトリに公開]** を選択します。

    公開プロセス中に、Visual Studio Code にステータス メッセージが表示されている点に注目します。

    GitHub アカウントをもう一度承認するように求められる場合があります。 その場合は、画面の指示に従って、ブラウザーでアカウントを承認します。 これにより、"最初のコミット" コミット メッセージを使用してリポジトリが公開される可能性があります。

1. コードがリポジトリに公開されておらず、ソース管理ビューに戻った場合は、コミット メッセージを入力し、**[Publish Branch]** を選択します。

    公開プロセスが完了すると、指定した GitHub リポジトリにコードが正常に公開されたことを示すメッセージが表示されます。

#### タスク 2: GitHub で空の README ファイルを作成する

以下の手順に従って、演習のこのセクションを完了します。

1. GitHub アカウントを表示しているブラウザー ウィンドウに切り替えます。

1. GitHub アカウントで新しい AccelerateDevGitHubCopilot リポジトリを開きます。

    AccelerateDevGitHubCopilot リポジトリが表示されない場合は、ページを更新します。 それでもリポジトリが表示されない場合は、次の手順を試してください。

    1. Visual Studio Code に切り替えます。
    1. 通知を開きます (通知は、新しいリポジトリが公開されたときに生成されています)。
    1. **[GitHub 上で開く]** を選択してリポジトリを開きます。

1. AccelerateDevGitHubCopilot リポジトリの [コード] タブで、**[README の追加]** を選択します。

1. README.md エディターで、「**Coming soon**」と入力し、**[変更をコミットする]** を選択します。

1. [変更のコミット] ダイヤログで、**[変更のコミット]** を選択します。

#### タスク 3: ローカル リポジトリに変更をプルします。

以下の手順に従って、演習のこのセクションを完了します。

1. Visual Studio Code に切り替え、ソース管理ビューが開かれていることを確認します。

1. **[その他の操作]** メニューを開き、**[プルする]** を選択します。

    [その他の操作] メニューは、ソース管理ビューの右上隅にある省略記号を使用して開けます。

1. エクスプローラー ビューを開き (ソリューション エクスプローラーを折りたたんで Visual Studio Code の既定のファイル/フォルダー エクスプローラーを使用)、**AccelerateDevGitHubCopilot** フォルダーを展開します。

1. README.md ファイルを開きます。

    "Coming soon" というメッセージが表示されます。

    > [!NOTE]
    > Visual Studio Code で README ファイルの内容を直接作成して、GitHub リポジトリに更新プログラムをプッシュできました。

この演習では、GitHub Copilot チャットを使用してリポジトリの README ファイルを更新します。

#### 概要 – 演習 3

この演習は、ライブラリ アプリケーション用の GitHub リポジトリと空の README ファイルを作成するのに役立ちました。 また、ローカル リポジトリに対する変更をプルして、最新の更新プログラムがあることを確認しました。

### 演習 4: README ファイルのプロジェクト ドキュメントを作成する

README ファイルは、GitHub リポジトリの重要な部分です。 README は、プロジェクト、プロジェクトの共同作成者、および利害関係者のニーズに基づいて情報を提供します。

このガイド付きプロジェクトの演習では、README ファイルに次のセクションが含まれている必要があります。

- **プロジェクトのタイトル**:プロジェクトの簡潔で明確なタイトル。
- **[説明]**: プロジェクトの内容と実行内容の詳細な説明。
- **プロジェクト構造**:主要なフォルダーやファイルなど、プロジェクト構造の内訳。
- **主要なクラスとインターフェイス**:プロジェクト内の主要なクラスとインターフェイスの一覧。
- **使用状況**:プロジェクトを使用する手順 (多くの場合、コード例を含む)。
- **ライセンス**:プロジェクトの基となるライセンス。

#### タスク 1: GitHub Copilot を使用し、プロジェクト ドキュメントを生成する。

演習のこのセクションでは、GitHub Copilot を使用してプロジェクト ドキュメントを作成し、README.md ファイルに追加します。

以下の手順に従って、演習のこのセクションを完了します。

1. チャット ビューを開きます。

    特定のコードまたはファイルに関心がある場合は、ドラッグ アンド ドロップ操作でチャット ビュー コンテキストにファイルを追加できます。 この場合は、ソリューション全体に関心があるため、個々のファイルを追加するのではなく、`@workspace` 参加者を使用します。

1. README ファイルのプロジェクト ドキュメントを生成するには、次のプロンプトを入力します。

    ```plaintext
    @workspace Generate the contents of a README.md file for the code repository. Use "Library App" as the project title. The README file should include the following sections: Description, Project Structure, Key Classes and Interfaces, Usage, License. Format all sections as raw markdown. Use a bullet list with indents to represent the project structure. Do not include ".gitignore" or the ".github", "bin", and "obj" folders.
    ```

    > [!NOTE]
    > 複数のプロンプトを使用すると、README ファイルのセクションごとに 1 つずつ、より詳細な結果が生成されます。 この演習では、プロセスを簡略化するために 1 つのプロンプトを使用します。

1. 応答を確認して、各セクションがマークダウンとして書式設定されていることを確認します。

    > [!NOTE]
    > より詳細な情報を提供する場合、または正しく書式設定されていない場合は、Readme セクションを個別に更新できます。 GitHub Copilot の応答を README ファイルにコピーし、マークダウン ファイルで直接修正することもできます。

1. エディターでマークダウン ファイルを開いた状態で、GitHub Copilot のステータス メニューを開き、**[Enable completions for markdown]** を選択します。

1. 推奨されるドキュメント セクションを README.md ファイルにコピーします。

    GitHub Copilot では、Markdown ドキュメントの提案を生成できます。 この機能は、マークダウン ファイルの作成と書式設定に役立ちます。

    たとえば、Readme.md ファイルの内容を選択し、インライン チャットを開いて、GitHub Copilot に "Markdown ドキュメントの書式設定を修正する" よう依頼できます。

1. 必要に応じて書式設定を調整し、更新された Readme.md ファイルを保存します。

    プロジェクト タイトル、説明、プロジェクト構造、主要なクラスとインターフェイス、使用方法、ライセンス情報を含む Readme ファイルがあるです。

    ```markdown
    # Library App
    
    ## Description
    Library App is a console-based application for managing library operations such as patron management, book loans, and membership renewals. It uses a JSON-based data storage system and provides various services to handle library functionalities.
    
    ## Project Structure
    - AccelerateDevGitHubCopilot.sln
    - README.md
    - src
      - Library.ApplicationCore/
        - Entities/
          - `Author.cs`
          - `Book.cs`
          - `BookItem.cs`
          - `Loan.cs`
          - `Patron.cs`
        - Enums/
          - `LoanExtensionStatus.cs`
          - `LoanReturnStatus.cs`
          - `MembershipRenewalStatus.cs`
        - Interfaces/
          - `IPatronRepository.cs`
          - `IPatronService.cs`
          - `ILoanRepository.cs`
          - `ILoanService.cs`
        - `Library.ApplicationCore.csproj`
        - Services/
          - `PatronService.cs`
          - `LoanService.cs`
      - Library.Console/
        - `appSettings.json`
        - `CommonActions.cs`
        - `ConsoleApp.cs`
        - `ConsoleState.cs`
        - `Library.Console.csproj`
        - `Program.cs`
      - Library.Infrastructure/
        - Data/
          - `JsonData.cs`
          - `JsonLoanRepository.cs`
          - `JsonPatronRepository.cs`
        - `Library.Infrastructure.csproj`
    - tests
      - UnitTests/
        - ApplicationCore/
          - LoanService/
            - `ReturnLoan.cs`
            - `ExtendLoan.cs`
          - PatronService/
            - `RenewMembership.cs`
        - `UnitTests.csproj`
    
    ## Key Classes and Interfaces
    - **Entities**
      - **Author**: Represents an author with properties like Id and Name.
      - **Book**: Represents a book with properties like Id, Title, AuthorId, Genre, ImageName, and ISBN.
      - **BookItem**: Represents a specific copy of a book with properties like Id, BookId, AcquisitionDate, and Condition.
      - **Loan**: Represents a loan with properties like Id, BookItemId, PatronId, LoanDate, DueDate, and ReturnDate.
      - **Patron**: Represents a library patron with properties like Id, Name, MembershipStart, MembershipEnd, and Loans.
    
    - **Enums**
      - **LoanExtensionStatus**: Enum for loan extension statuses.
      - **LoanReturnStatus**: Enum for loan return statuses.
      - **MembershipRenewalStatus**: Enum for membership renewal statuses.
    
    - **Interfaces**
      - **IPatronRepository**: Interface for patron repository with methods like GetPatron, SearchPatrons, and UpdatePatron.
      - **IPatronService**: Interface for patron service with method RenewMembership.
      - **ILoanRepository**: Interface for loan repository with methods like GetLoan and UpdateLoan.
      - **ILoanService**: Interface for loan service with methods like ReturnLoan and ExtendLoan.
    
    - **Services**
      - **PatronService**: Implements IPatronService to handle patron-related operations.
      - **LoanService**: Implements ILoanService to handle loan-related operations.
    
    - **Console**
      - **ConsoleApp**: Main console application class that handles user interactions and application flow.
      - **ConsoleState**: Enum for different states of the console application.
      - **CommonActions**: Enum for common actions in the console application.
    
    - **Infrastructure**
      - **JsonData**: Handles loading and saving data to JSON files.
      - **JsonLoanRepository**: Implements ILoanRepository to manage loan data.
      - **JsonPatronRepository**: Implements IPatronRepository to manage patron data.
    
    ## Usage
    1. Clone the repository.
    2. Open the solution file AccelerateDevGitHubCopilot.sln in Visual Studio.
    3. Build the solution to restore dependencies.
    4. Run the Library.Console project to start the console application.
    5. Follow the on-screen instructions to search for patrons, view patron details, extend loans, return books, and renew memberships.
    
    ## License
    This project is licensed under the MIT License.
    ```

#### タスク 2: Readme ファイルの更新をコミットしてプッシュする

以下の手順に従って、演習のこのセクションを完了します。

1. Visual Studio Code の [ソース管理] ビューを開きます。

1. GitHub Copilot によってコミット メッセージが生成されるようにするには、メッセージ ボックスの右側にあるアイコンを選択します。

    次のようなコミット メッセージが表示されます。

    ```plaintext
    Update README.md with project description, structure, key classes, usage instructions, and license information
    ```

1. ファイルの更新をステージングしてコミットします。

1. GitHub リポジトリに更新を同期 (またはプッシュ) します。

    プロンプトが表示されたら、GitHub 資格情報を使用して同期/プッシュ操作を承認します。

#### タスク 3: 作業を確認する

作業内容を確認するには、次の手順を実行します。

1. AccelerateDevGitHubCopilot プロジェクトの GitHub リポジトリを開きます。

1. **[コード]** タブを使用して、更新された README.md ファイルを確認します。

    更新された Readme ファイルを確認するには、ブラウザの更新が必要な場合があります。

1. README ファイルで説明されているプロジェクト構造が、リポジトリのフォルダー構造と一致していることを確認します。

    Readme ファイルのプレビュー中は、GitHub インターフェイスの左側にあるファイル ツリーを使用して、リポジトリ構造を展開および確認できます。

1. コミット履歴を確認し、GitHub Copilot によって生成されたコミット メッセージを見つけます。

#### まとめ - 演習 4

この演習は、GitHub Copilot を使用して Readme ファイルのプロジェクト ドキュメントを作成するのに役立ちました。 GitHub Copilot を使用して、プロジェクトの説明、プロジェクト構造、主要なクラスとインターフェイス、使用方法、ライセンス情報を生成しました。 また、Readme ファイルの更新をコミットして GitHub リポジトリにプッシュしました。

## パート 2: GitHub Copilot ツールを使用してコード機能を開発する

### 開始する前に

#### プロジェクトの概要

あなたと同僚は、図書館アプリケーションの目標について話し合うためにミーティングを行います。 あなたは、図書館司書と利用者のユーザー エクスペリエンスを向上させたいと考えています。 アプリケーションに追加できるいくつかの新機能について説明します。

あなたは、次の機能に取り組むことに同意します。

- 書籍の在庫:図書館司書が書籍の在庫の状態を判断できるようにします。 この機能では、書籍が貸出可能かどうか、または現在ほかの利用者に貸出中の場合は返却期限を示すメッセージを表示する必要があります。

- 書籍の貸出:図書館司書が書籍を利用者に貸し出せるようにします (書籍が利用可能な場合)。 この機能は、利用者が貸出中の本を受け取るオプションを表示し、Loans.json を新しい貸出内容で更新して、利用者の更新された貸出の詳細を表示する必要があります。

- 書籍の予約:図書館司書が利用者のために書籍を予約できるようにします (書籍が既に予約されている場合を除く)。 この機能は、新しい書籍予約プロセスを実装する必要があります。 この機能では、予約プロセスのサポートに必要な新しいクラスとインターフェイスと共に、新しい Reservations.json ファイルを作成する必要がある場合があります。

各メンバーが、新しい機能のうち 1 つに取り組んでから、再グループ化します。 あなたは、書籍の在庫の状態を判断する機能に取り組みます。 同僚は、書籍を利用者に貸し出す機能に取り組みます。 最後の、利用者のために書籍を予約する機能は、他の 2 つの機能が完了した後に開発されます。

#### ラボ シナリオ (パート 2)

GitHub Copilot は、図書館アプリケーションの新機能の開発に役立ちます。

このラボのパート 2 では、GitHub Copilot を使用して、新機能をより迅速かつ正確に実装するのに役立つコード候補を生成します。

パート 2 には、次の演習が含まれています。

- 新しい "書籍の在庫" 機能を開発する。
- 変更をリポジトリのメイン ブランチにマージする。

### 演習 5: 新しい "書籍の在庫" 機能を開発する

書籍の在庫の機能には、次のコード更新プログラムが含まれている必要があります。

- 司書が書籍を検索するオプションを選択できるようにする新しい CommonActions.SearchBooks アクションを実装します。
- ConsoleApp.cs に新しい SearchBooks メソッドを作成します。 SearchBooks メソッドは、ユーザーが指定した書籍のタイトルを読み取る必要があります。 書籍が貸出可能かどうかを確認し、"book.title は貸出可能です" または "book.title は別の利用者に貸し出されています" のいずれかのメッセージを表示します。 返却期限は loan.DueDat です。

この演習では、次のタスクを完了します。

- コード リポジトリに "書籍の在庫" ブランチを作成します。
- GitHub Copilot の提案を使用すると、司書が選択できる新しい一般的な SearchBooks アクションの実装に役立ちます。
- GitHub Copilot の提案を使用すると、ユーザーが指定した書籍タイトルを読み取り、書籍が貸出可能かどうかを確認し、書籍の在庫状況を示すメッセージを表示する SearchBooks メソッドの開発に役立ちます。

#### タスク 1: リポジトリに新しいブランチを作成する

新しい "書籍の在庫" 機能の開発を開始する前に、リポジトリに新しいブランチを作成する必要があります。 これにより、リポジトリのメイン ブランチに影響を与えずに、新しい機能に取り組むことができます。 新しい機能の準備ができたら、メイン ブランチにマージできます。

以下の手順に従って、演習のこのセクションを完了します。

1. Visual Studio Code に AccelerateDevGitHubCopilot ソリューションが開かれていることを確認します。

1. [ソース管理] ビューを選択し、ローカル リポジトリがリモート リポジトリ (プルまたは同期) と同期していることを確認します。

1. ウィンドウの左下隅にある **[メイン]** を選択します。

1. 新しいブランチを作成するには、「**書籍の在庫**」と入力したあと、**[+ 新しいブランチの作成]** を選択します。

1. 新しいブランチをリモート リポジトリにプッシュするには、**[ブランチの発行]** を選択します。

#### タスク 2: 新しい一般的な "SearchBooks" アクションを実装する

演習のこのセクションでは、GitHub Copilot を使用して、SearchBooks という名前のメニュー オプションの実装に役立てます。 司書は SearchBooks アクションを選択して、書籍の在庫状況を確認します。

このタスク中に完了するファイル更新は次のとおりです。

- CommonActions.cs の CommonActions 列挙型の更新: CommonActions 列挙型に新しい SearchBooks アクションを追加します。
- ConsoleApp.cs の WriteInputOptions メソッドの更新: 新しい CommonActions.SearchBooks オプションを表示するためのサポートを追加します。
- ConsoleApp.cs の ReadInputOptions メソッドの更新: 新しい CommonActions.SearchBooks オプションを読み取る (選択する) ためのサポートを追加します。
- ConsoleApp.cs の PatronDetails メソッドの更新: 新しい CommonActions.SearchBooks オプションが選択されたときにそのオプションを処理するためのサポートを追加します。

以下の手順に従って、演習のこのセクションを完了します。

1. [ソリューション エクスプローラー] ビューを開きます。

1. CommonActions.cs ファイルを開いて、**CommonActions** 列挙型を選択します。

    CommonActions に新しい SearchBooks アクションを追加する必要があります。

1. インライン チャットを開き、次のプロンプトを入力します。

    ```plaintext
    Update selection to include a new `SearchBooks` action.
    ```

    GitHub Copilot により、新しい SearchBooks アクションを CommonActions 列挙型に追加するコード更新が提案されるはずです。

1. 推奨された更新を確認し、**[承諾]** を選択します。

    ```csharp

    public enum CommonActions
    {
        Repeat = 0,
        Select = 1,
        Quit = 2,
        SearchPatrons = 4,
        RenewPatronMembership = 8,
        ReturnLoanedBook = 16,
        ExtendLoanedBook = 32,
        SearchBooks = 64
    }

    ```

1. ConsoleApp.cs ファイルを開きます。

1. **WriteInputOptions** メソッドを見つけて選択します。

    新しい CommonActions.SearchBooks オプションのサポートを追加する必要があります。 書籍が貸出可能かどうかを確認するオプションを表示します。

1. インライン チャットを開き、次のプロンプトを入力します。

    ```plaintext
    Update selection to include an option for the `CommonActions.SearchBooks` action. Use the letter "b" and the message "to check for book availability".
    ```

    GitHub Copilot により、SearchBooks アクションの新しい "if" ブロックを追加するコード更新が提案されます。

1. 推奨された更新を確認し、**[承諾]** を選択します。

    提案される更新は、次のコード スニペットのような内容になります。

    ```csharp

    static void WriteInputOptions(CommonActions options)
    {
        Console.WriteLine("Input Options:");
        if (options.HasFlag(CommonActions.ReturnLoanedBook))
        {
            Console.WriteLine(" - \"r\" to mark as returned");
        }
        if (options.HasFlag(CommonActions.ExtendLoanedBook))
        {
            Console.WriteLine(" - \"e\" to extend the book loan");
        }
        if (options.HasFlag(CommonActions.RenewPatronMembership))
        {
            Console.WriteLine(" - \"m\" to extend patron's membership");
        }
        if (options.HasFlag(CommonActions.SearchPatrons))
        {
            Console.WriteLine(" - \"s\" for new search");
        }
        if (options.HasFlag(CommonActions.SearchBooks))
        {
            Console.WriteLine(" - \"b\" to check for book availability");
        }
        if (options.HasFlag(CommonActions.Quit))
        {
            Console.WriteLine(" - \"q\" to quit");
        }
        if (options.HasFlag(CommonActions.Select))
        {
            Console.WriteLine("Or type a number to select a list item.");
        }
    }

    ```

1. 少し上にスクロールして、**ReadInputOptions** メソッドを見つけます。

1. **ReadInputOptions** メソッドを選択します。

    新しい CommonActions.SearchBooks オプションのサポートを追加する必要があります。 SearchBooks アクションを選択するユーザーを処理するケースを入れます。

1. インライン チャットを開き、次のプロンプトを入力します。

    ```plaintext
    Update selection to include an option for the `CommonActions.SearchBooks` action.
    ```

    GitHub Copilot により、SearchBooks アクションを選択するユーザーを処理する新しい "ケース" を追加するコード更新が提案されます。

1. 推奨された更新を確認し、**[承諾]** を選択します。

    提案される更新は、次のコード スニペットのような内容になります。

    ```csharp

    static CommonActions ReadInputOptions(CommonActions options, out int optionNumber)
    {
        CommonActions action;
        optionNumber = 0;
        do
        {
            Console.WriteLine();
            WriteInputOptions(options);
            string? userInput = Console.ReadLine();
            action = userInput switch
            {
                "q" when options.HasFlag(CommonActions.Quit) => CommonActions.Quit,
                "s" when options.HasFlag(CommonActions.SearchPatrons) => CommonActions.SearchPatrons,
                "m" when options.HasFlag(CommonActions.RenewPatronMembership) => CommonActions.RenewPatronMembership,
                "e" when options.HasFlag(CommonActions.ExtendLoanedBook) => CommonActions.ExtendLoanedBook,
                "r" when options.HasFlag(CommonActions.ReturnLoanedBook) => CommonActions.ReturnLoanedBook,
                "b" when options.HasFlag(CommonActions.SearchBooks) => CommonActions.SearchBooks,
                _ when int.TryParse(userInput, out optionNumber) => CommonActions.Select,
                _ => CommonActions.Repeat
            };
            if (action == CommonActions.Repeat)
            {
                Console.WriteLine("Invalid input. Please try again.");
            }
        } while (action == CommonActions.Repeat);
        return action;
    }

    ```

1. 下にスクロールし、**PatronDetails** メソッドを見つけて選択します。

    2 つのことを実行する必要があります。

    - ReadInputOptions を呼び出す前に、CommonActions.SearchBooks をオプションに追加する必要があります。
    - また、SearchBooks アクションを処理する else if も追加する必要があります。 else if ブロックは、SearchBooks という名前の新しいメソッドを呼び出す必要があります。

    これらの両方に一緒に対処できます。

1. インライン チャットを開き、次のプロンプトを入力します。

    ```plaintext
    Update selection to add `CommonActions.SearchBooks` to `options` before calling `ReadInputOptions`. Add an `else if` block to handle the `SearchBooks` action. The `else if` block should call a new method named `SearchBooks`.
    ```

    GitHub Copilot により、ReadInputOptions を呼び出す前に、CommonActions.SearchBooks をオプションに追加するコード更新が提案されるはずです。

1. 推奨された更新を確認し、**[承諾]** を選択します。

    ```csharp

    async Task<ConsoleState> PatronDetails()
    {
        Console.WriteLine($"Name: {selectedPatronDetails.Name}");
        Console.WriteLine($"Membership Expiration: {selectedPatronDetails.MembershipEnd}");
        Console.WriteLine();
        Console.WriteLine("Book Loans:");
        int loanNumber = 1;
        foreach (Loan loan in selectedPatronDetails.Loans)
        {
            Console.WriteLine($"{loanNumber}) {loan.BookItem!.Book!.Title} - Due: {loan.DueDate} - Returned: {(loan.ReturnDate != null).ToString()}");
            loanNumber++;
        }
        CommonActions options = CommonActions.SearchPatrons | CommonActions.Quit | CommonActions.Select | CommonActions.RenewPatronMembership | CommonActions.SearchBooks;
        CommonActions action = ReadInputOptions(options, out int selectedLoanNumber);
        if (action == CommonActions.Select)
        {
            if (selectedLoanNumber >= 1 && selectedLoanNumber <= selectedPatronDetails.Loans.Count())
            {
                var selectedLoan = selectedPatronDetails.Loans.ElementAt(selectedLoanNumber - 1);
                selectedLoanDetails = selectedPatronDetails.Loans.Where(l => l.Id == selectedLoan.Id).Single();
                return ConsoleState.LoanDetails;
            }
            else
            {
                Console.WriteLine("Invalid book loan number. Please try again.");
                return ConsoleState.PatronDetails;
            }
        }
        else if (action == CommonActions.Quit)
        {
            return ConsoleState.Quit;
        }
        else if (action == CommonActions.SearchPatrons)
        {
            return ConsoleState.PatronSearch;
        }
        else if (action == CommonActions.RenewPatronMembership)
        {
            var status = await _patronService.RenewMembership(selectedPatronDetails.Id);
            Console.WriteLine(EnumHelper.GetDescription(status));
            // reloading after renewing membership
            selectedPatronDetails = (await _patronRepository.GetPatron(selectedPatronDetails.Id))!;
            return ConsoleState.PatronDetails;
        }
        else if (action == CommonActions.SearchBooks)
        {
            return await SearchBooks();
        }
        throw new InvalidOperationException("An input option is not handled.");
    }

    ```

    > [!NOTE]
    > インライン チャットの提案により、SearchBooks メソッドのスタブ コードが作成される場合もあります。

#### タスク 3: SearchBooks メソッドを開発する

完了すると、SearchBooks メソッドにより、ユーザーが指定した書籍タイトルが読み取られ、書籍が貸し出し可能かどうかが確認され、その書籍の貸し出し状況を示すメッセージが表示されるはずです。 このメソッドでは、Books.json ファイルと Loans.json ファイルを使用して、一致する書籍タイトルを検索し、その書籍の貸し出し状況を判断する必要があります。

以下の手順に従って、演習のこのセクションを完了します。

1. 少し時間をかけて SearchBooks メソッドのプロセス要件を検討しましょう。

    メソッドは何を行う必要がありますか? 何を返す必要がありますか? パラメーターは必要ですか?

    SearchBooks メソッドは、次のプロセスを実行する必要があります。

    1. ユーザーに書籍のタイトルの入力を求めるメッセージを表示する。
    1. ユーザーが指定した書籍のタイトルを読み取る。
    1. 書籍が貸出可能かどうかを確認する
    1. 次のいずれかのオプションを示すメッセージを表示する。

        - "book.title は貸し出し可能"
        - "book.title は別の利用者に貸し出されています。 返却期限は loan.DueDat です。

    メッセージ オプションをビルドするには、コードで次の JSON ファイルにアクセスする必要があります。

    - 一致する Title と BookId を検索するには、Books.json が必要です。
    - 一致する BookItemId の ReturnDate と DueDate を検索するには、Loans.json が必要です。 BookItemId は、Books.json 内の BookId と同じです。

1. ConsoleApp.cs ファイルに次の **SearchBooks** メソッドが作成されていることを確認してください。

    ```csharp

    async Task<ConsoleState> SearchBooks()
    {
        return ConsoleState.PatronDetails;
    }

    ```

    > [!NOTE]
    > GitHub Copilot によって作成されたコード コメントは必ず削除してください。 不要で不正確なコメントは、GitHub Copilot の提案に悪影響を及ぼすおそれがあります。

1. **SearchBooks** メソッドを選択します。

1. インライン チャットを開き、次のプロンプトを入力します。

    ```plaintext
    Update selection to obtain a book title. Prompt the user to "Enter a book title to search for". Read the user input and ensure the book title isn't null.
    ```

    GitHub Copilot により、ユーザーが指定した書籍のタイトルをキャプチャするコード更新プログラムが提案されます。

1. 推奨された更新を確認し、**[承諾]** を選択します。

    ```csharp

    async Task<ConsoleState> SearchBooks()
    {
        string? bookTitle = null;
        while (String.IsNullOrWhiteSpace(bookTitle))
        {
            Console.Write("Enter a book title to search for: ");
            bookTitle = Console.ReadLine();
        }
        // Perform book search logic here
        return ConsoleState.PatronDetails;
    }

    ```

    > [!NOTE]
    > GitHub Copilot では、書籍タイトルのユーザー入力を処理する別のメソッドを作成できます。 その提案を受け入れ、引き続き SearchBooks メソッドでプライマリ ロジックを開発できます。

1. GitHub Copilot によって生成されたすべてのプレースホルダー コメントを削除して、**SearchBooks** メソッドを選択します。

1. チャット ビューを開きます。

1. チャット コンテキストに次のファイルを追加します: ConsoleApp.cs、JsonData.cs、JsonLoanRepository.cs、Books.json、Loans.json、BookItems.json。

1. 次のプロンプトを入力します。

    ```plaintext
    @workspace  Explain how to update the `SearchBooks` method and ConsoleApps class to determine whether a book title is available for loan. Inside the SearchBooks method, use a LINQ query and the user supplied book title to return a matching book. If a book is found, use a LINQ query and Loans.json to check if the book is available for loan. If the book has been returned, display a message stating "`book.title` is available for loan". If the book is on loan, display a message stating "`book.title` is on loan to another patron. The return due date is `loan.DueDate`".
    ```

1. 少し時間をかけて、提案された更新を確認しましょう。

    GitHub Copilot は、次のような候補に類似した更新プログラムを提案する必要があります。

    SearchBooks メソッドと ConsoleApp クラスを更新して、AE 書籍タイトルが貸出に使用できるかどうかを判断するには、次の手順に従います。

    a. JsonData クラスでタイトル別に書籍を検索するメソッドを追加します。
    b. ConsoleApp クラスの SearchBooks メソッドを更新して、この新しいメソッドを使用します。
    c. 書籍の貸出状態を確認し、適切なメッセージを表示します。

    更新されたコードを次に示します。

    手順 1: JsonData クラスでタイトル別に書籍を検索するメソッドを追加する

    ```csharp

    public Book? SearchBookByTitle(string title)
    {
        return Books?.FirstOrDefault(b => b.Title.Equals(title, StringComparison.OrdinalIgnoreCase));
    }

    ```

    手順 2: ConsoleApp クラスの SearchBooks メソッドを更新する

    ```csharp

    async Task<ConsoleState> SearchBooks()
    {
        string bookTitle = ReadBookTitle();
        // ensure data is loaded
        await _jsonData.LoadData();
        // find the book by title
        Book? book = _jsonData.SearchBookByTitle(bookTitle);
        if (book == null)
        {
            Console.WriteLine($"No book found with title: {bookTitle}");
            return ConsoleState.PatronDetails;
        }
        // find the loan status of the book
        Loan? loan = _jsonData.Loans?.FirstOrDefault(l => l.BookItemId == book.Id && l.ReturnDate == null);
        if (loan == null)
        {
            Console.WriteLine($"{book.Title} is available for loan.");
        }
        else
        {
            Console.WriteLine($"{book.Title} is on loan to another patron. The return due date is {loan.DueDate}.");
        }
        return ConsoleState.PatronDetails;
    }

    ```

    手順 3: JsonData を含むように ConsoleApp クラス コンストラクターを更新する

    ```csharp

    public class ConsoleApp
    {
        // Existing fields...
        JsonData _jsonData;
        public ConsoleApp(ILoanService loanService, IPatronService patronService, IPatronRepository patronRepository, ILoanRepository loanRepository, JsonData jsonData)
        {
            _patronRepository = patronRepository;
            _loanRepository = loanRepository;
            _loanService = loanService;
            _patronService = patronService;
            _jsonData = jsonData;
        }
        // Other methods...

    }

    ```

    手順 4: JsonData を ConsoleApp に渡すProgram.csを更新する

    ```csharp

    using Microsoft.Extensions.DependencyInjection;
    using Library.Infrastructure.Data;
    using Library.ApplicationCore;
    using Microsoft.Extensions.Configuration;
    var services = new ServiceCollection();
    var configuration = new ConfigurationBuilder()
    .SetBasePath(Directory.GetCurrentDirectory())
    .AddJsonFile("appSettings.json")
    .Build();
    services.AddSingleton<IConfiguration>(configuration);
    services.AddScoped<IPatronRepository, JsonPatronRepository>();
    services.AddScoped<ILoanRepository, JsonLoanRepository>();
    services.AddScoped<ILoanService, LoanService>();
    services.AddScoped<IPatronService, PatronService>();
    services.AddSingleton<JsonData>();
    services.AddSingleton<ConsoleApp>();
    var servicesProvider = services.BuildServiceProvider();
    var consoleApp = servicesProvider.GetRequiredService<ConsoleApp>();
    consoleApp.Run().Wait();

    ```

    これらの変更により、ConsoleApp クラスの SearchBooks メソッドは、Books.json ファイル内のタイトルで書籍を検索し、Loans.json ファイルでその貸出状態を確認します。 書籍が貸出可能な場合は、書籍が貸出可能であることを示すメッセージが表示されます。 書籍が貸出中の場合は、書籍が貸出中であることを示すメッセージが表示され、返却期限が表示されます。

    > [!NOTE]
    > GitHub Copilot は、JsonData クラスのメソッドを使用するのではなく、SearchBooks メソッドで LINQ クエリを使用してブック オブジェクトを返すように提案する場合があります。 ただし、(SEARCHBooks メソッドに LINQ クエリを使用するのではなく) 書籍のタイトルを返し、貸出状態を確認するためのメソッドを `JsonData` クラスに作成することも推奨されます。 以下の手順は、これらのアプローチの組み合わせを使用する GitHub Copilot の提案に基づいています。

1. 提案された SearchBookByTitle メソッドを **JsonData** クラスの末尾に追加します。

    ```csharp

    public Book? SearchBookByTitle(string title)
    {
        return Books?.FirstOrDefault(b => b.Title.Equals(title, StringComparison.OrdinalIgnoreCase));
    }

    ```

1. _jsonData フィールド宣言をクラス コンストラクターの前の ConsoleAp クラスに追加します。

    ```csharp

    JsonData _jsonData;

    ```

1. JsonData パラメーターを ConsoleApp クラス コンストラクターに追加し、それを使用してコンストラクター内の _jsonData フィールドを初期化します。

    更新されたクラス コンストラクターは、次のコード スニペットのようになります。

    ```csharp

    public ConsoleApp(ILoanService loanService, IPatronService patronService, IPatronRepository patronRepository, ILoanRepository loanRepository, JsonData jsonData)
    {
        _patronRepository = patronRepository;
        _loanRepository = loanRepository;
        _loanService = loanService;
        _patronService = patronService;
        _jsonData = jsonData;
    }

    ```

1. JsonData が ConsoleApp クラスで認識されていないことに注意してください。

    ConsoleApp.cs ファイルの先頭に "using Library.Infrastructure.Data;" を追加する必要があります。

1. ConsoleApp.csファイルの先頭に、次の "using" ステートメントが追加されていることを確認します。

    ```csharp

    using Library.Infrastructure.Data;

    ```

1. コード候補を使用して、**SearchBooks** メソッドを更新します。

    提案されたコードは、SearchBookByTitle メソッド（または LINQ クエリ）を使用してタイトルで書籍を検索する必要があります。 書籍が見つかった場合は、LINQ クエリを使用して、書籍が貸出中かどうかを判断します。 このコードには、検索結果に基づいて書籍の在庫状態を表示するロジックも含まれています。 応答メッセージの表示に使用されるロジックを実装する方法がいくつかあります。 例は以下のコード スニペットに示されています。

    次のコード スニペットは、SearchBooks メソッドの 1 つの実装を示しています。

    ```csharp

    async Task<ConsoleState> SearchBooks()
    {
        string bookTitle = ReadBookTitle();
        Book? book = _jsonData.SearchBookByTitle(bookTitle);
        if (book == null)
        {
            Console.WriteLine($"No book found with title: {bookTitle}");
            return ConsoleState.PatronDetails;
        }
        Loan? loan = _jsonData.Loans?.FirstOrDefault(l => l.BookItemId == book.Id && l.ReturnDate == null);
        if (loan == null)
        {
            Console.WriteLine($"{book.Title} is available for loan.");
        }
        else
        {
            Console.WriteLine($"{book.Title} is on loan to another patron. The return due date is {loan.DueDate}.");
        }
        return ConsoleState.PatronDetails;
    }

    ```

1. 既存の **Program.cs** ファイルと推奨される更新プログラムを比較します。

    ```csharp

    using Microsoft.Extensions.DependencyInjection;
    using Library.Infrastructure.Data;
    using Library.ApplicationCore;
    using Microsoft.Extensions.Configuration;
    var services = new ServiceCollection();
    var configuration = new ConfigurationBuilder()
        .SetBasePath(Directory.GetCurrentDirectory())
        .AddJsonFile("appSettings.json")
        .Build();
    services.AddSingleton<IConfiguration>(configuration);
    services.AddScoped<IPatronRepository, JsonPatronRepository>();
    services.AddScoped<ILoanRepository, JsonLoanRepository>();
    services.AddScoped<ILoanService, LoanService>();
    services.AddScoped<IPatronService, PatronService>();
    services.AddSingleton<JsonData>();
    services.AddSingleton<ConsoleApp>();
    var servicesProvider = services.BuildServiceProvider();
    var consoleApp = servicesProvider.GetRequiredService<ConsoleApp>();
    consoleApp.Run().Wait();

    ```

    もし Program.cs ファイルに、ASP.NET Core の依存関係挿入システムに対して JsonData クラスの単一のインスタンスを作成し、JsonData が要求された際にその同じインスタンスを使用するよう指示するコードが既に含まれている場合、更新は不要です。

1. **SearchBooks** メソッドを選択します。

1. チャット ビューを開き、次のプロンプトを入力します。

    ```plaintext
    Explain the LINQ queries and the evaluation of the book's availability status.
    ```

1. 少し時間をかけて、GitHub Copilot から提供された説明を確認しましょう。

    書籍が貸出中かどうかを確認するクエリには、次の説明に似た内容が表示されるはずです。

    ```markdown
    **Search for the Loan Status of the Book**
    ```

    ```csharp

    Loan? loan = _jsonData.Loans?.FirstOrDefault(l => l.BookItemId == book.Id && l.ReturnDate == null);

    ```

    ```markdown
    - _jsonData.Loans: Accesses the list of loans from the JsonData class.

    - ?.: The null-conditional operator ensures that if _jsonData.Loans is null, the entire expression will return null without throwing a NullReferenceException.

    - FirstOrDefault: A LINQ method that returns the first element in the collection that matches the specified condition, or null if no such element is found.

    - Lambda Expression: l => l.BookItemId == book.Id && l.ReturnDate == null

        - l.BookItemId == book.Id: Checks if the BookItemId of the loan matches the Id of the book being searched.

        - l.ReturnDate == null: Checks if the loan's ReturnDate is null, indicating that the book is currently on loan and has not been returned.

    - Result: If a matching loan is found, it is assigned to the loan variable. If no matching loan is found, loan is null.

    **Evaluation of the Book's Availability Status**

    After executing the LINQ queries, the method evaluates the availability status of the book:

      - If loan is null, the book has been returned. The method prints that the book is available for loan.
      - If loan is not null, the book is currently on loan (no return date). The method prints that the book is on loan and provides the date when the book should be returned.

    ```

1. **Check if the Book is on Loan** (書籍が貸出中かどうかを確認する) クエリによって実装されたロジックを検証します。

    Null 条件演算子: ”?."  は "null 条件演算子" と呼ばれる演算子です。 これは、_jsonData.Loans が null の場合、NullReferenceException をスローすることなく、式全体が null と評価されることを保証します。

    ラムダ式: ラムダ式 "l => l.BookItemId == book.Id && l.ReturnDate == null" は、FirstOrDefault メソッドの条件を定義します。 各貸出オブジェクト "l" をチェックして、そのオブジェクトの BookItemId が書籍オブジェクトの Id と一致するかどうか、および貸出オブジェクトの ReturnDate が null 値かどうかを確認します。

    このコードは、BookItemId が指定された書籍の Id と一致し ReturnDate が null 値である、_jsonData.Loans コレクション内の最初の貸出オブジェクトを検索しようとしています。 そのような貸出オブジェクトが見つからない場合や、"_jsonData.Loans" が null 値の場合は、貸出オブジェクトが null 値に設定されます。

    > [!NOTE]
    > ほとんどの現代の図書館には、同じ書籍が複数冊所蔵されています。 このコードは、各書籍が 1 冊だけであることを前提としています。 図書館に同じ書籍が複数ある場合は、同じ書籍の複数の貸出を処理するためにコードを更新する必要があります。 このトレーニングの目的上、各書籍は 1 冊だけであり、提供されるロジックで十分であると想定しています。

1. 更新されたファイルを保存します。

1. エラーが発生しないようにソリューションをビルドします。

    **警告**メッセージが表示されますが、エラーは発生しないはずです。

    ソリューション エクスプローラー ビューでソリューションをビルドするには、**AccelerateDevGitHubCopilot** を右クリックし、**[ビルド]** を選択します。

#### まとめ - 演習 5

GitHub Copilot を使用して、図書館アプリケーションの新機能の実装に役立てました。 リポジトリに新しいブランチを作成したあと、GitHub Copilot を使用して、新機能をより迅速かつ正確に実装するのに役立つコード候補を生成しました。 CommonActions に新しい SearchBooks アクションを追加し、ConsoleApp.cs の WriteInputOptions メソッドと ReadInputOptions メソッドを更新し、書籍の在庫状況を判断する新しい SearchBooks メソッドを作成しました。

### 演習 6: 変更をリポジトリのメイン ブランチにマージする

司書が書籍の在庫状況を判断できるようになる新しい機能を作成しました。 次に、機能が期待どおりに動作することを確認し、変更をリポジトリのメイン ブランチにマージする必要があります。

この演習では、次のタスクを完了します。

- 新しい機能が期待どおりに動作することを確認する
- 変更をリモート リポジトリと同期する
- 変更をリポジトリのメイン ブランチにマージする pull request を作成します。

#### タスク 1: 新しい機能が期待どおりに動作することを確認する

自動テストがないため、手動テストを使用して、新しい機能が期待どおりに動作することを確認できます。 検証できるデータ ソースを使用することが重要です。 この場合は、Books.json ファイルと Loans.json ファイルを使用して、新しい機能が書籍の在庫状況を正しく報告することを確認します。

以下の手順に従って、演習のこのセクションを完了します。

1. [ソリューション エクスプローラー] ビューを開きます。

1. アプリケーションを実行するには、**Library.Console** を右クリックし、**[デバッグ]** を選択してから **[新しいインスタンスを開始]** を選択します。

1. 利用者名の入力を求められたら、「**One**」と入力して Enter キーを押します。

    検索クエリに一致する利用者の一覧が表示されます。

1. "Input Options" プロンプトで「**2**」と入力し、Enter キーを押します。

    「**2**」と入力すると、リストにある 2 番目のパトロンが選択されます。

    利用者の名前とメンバーシップの状態が表示され、その後に書籍貸出の詳細が表示されます。

1. "Input Options" プロンプトで「**b**」と入力し、Enter キーを押します。

    「**b**」と入力すると、書籍の在庫状態を検索するオプションが選択されます。

    書籍のタイトルを入力するプロンプトが表示されます。

1. 「**Book One**」と入力し Enter キーを押します。

    ダウンロードした元のデータでは、**Book One** は現在 **Patron Forty-Nine**に貸出中であるため、在庫がありません。

1. 書籍が別の利用者に貸し出されていることを示すメッセージがアプリケーションに表示されることを確認します。

    上にスクロールしないとメッセージが見えない場合があります。

1. **Book Nine** が **Patron One** により返却されたことを確認します。

    前の演習では、図書館アプリケーションのテスト中に、**Patron One** に **Book Nine** を返却してもらいました。 アプリケーションで **Book Nine** が **Patron One** によって返却されていないと示されている場合は、入力オプションを使用して **Book Nine** を選択して返却してから続行してください。

    > [!NOTE]
    > Library.Console.csproj ファイルを使用すると、アプリケーションのビルド時に JSON データ ファイルが出力ディレクトリに確実にコピーされます。 ただし、クリーンまたはリビルド操作を実行すると、本質的にデータがリセットされます。 ビルド操作を繰り返し実行しても、出力ディレクトリ ("/bin/Debug/net8.0/") 内のデータはリセットされません。

1. "Input Options" プロンプトで「**b**」と入力し、Enter キーを押します。

1. 「**Book Nine**」と入力し Enter キーを押します。

1. 書籍が貸出可能であることを示すメッセージがアプリケーションに表示されることを確認します。

1. "Input Options" プロンプトで「**q**」と入力し、Enter キーを押します。

1. デバッグ セッションを停止します。

1. **Loans.json** ファイルを開きます。

    Loans.json ファイルは、各書籍の貸出状況を追跡するために使用されます。 Loans.json ファイルを使用して、Book One と Book Nine の在庫状況が正しいことを確認できます。

    更新された Loans.json ファイルは、"Library.Console\bin\Debug\net8.0\Json" フォルダーまたは "Library.Console\Json" フォルダーにあるはずです。

    - Visual Studio Code デバッガーを使用してアプリを実行している場合は、更新された Loans.json ファイルは "Library.Console\bin\Debug\net8.0\Json" フォルダーにあるはずです。

    - "AccelerateDevGitHubCopilot\src\Library.Console" フォルダーから "dotnet run" コマンドを使用してアプリを実行している場合、更新された Loans.json ファイルは "Library.Console\Json" フォルダーにあるはずです。

1. 貸出 ID 37 と貸出 ID 46 が両方とも Book One ("BookItemId": 1) のものであることを確認します。

    - 貸出 ID 37 には ReturnDate 値 (2024-01-17) があるはずです
    - 貸出 ID 46 には ReturnDate 値がないはずです。 ReturnDate 値は null 値のはずです。

    ReturnDate 値は、書籍が現在貸出中かどうかを判断するために使用されます。 ReturnDate 値が null 値の場合、書籍は貸出中と見なされます。

1. 貸出 ID 22 が Book Nine ("BookItemId": 9) のものであり、ReturnDate 値が当日の日付に設定されていることを確認します。

    デバッガーで実行していて、Loans.json ファイルに変更を加えた後でソリューションをクリーンした場合、それらの変更内容は失われます。 ソリューションをクリーンしたら、次回アプリケーションを実行するときに、Loans.json ファイルが元のデータにリセットされます。 Loans.json ファイルを手動で更新して、Book One と Book Nine の在庫状況をテストできます。

#### タスク 2: 変更をリモート リポジトリと同期する

Visual Studio Code のソース管理ビューを使用して、変更内容をローカル リポジトリにコミットできます。 変更内容をコミットしたら、リモート リポジトリと同期できます。

以下の手順に従って、演習のこのセクションを完了します。

1. [ソース管理] ビューを選択します。

1. **Changes**の下に CommonActions.cs、ConsoleApp.cs、および JsonData.cs ファイルが一覧表示されていることを確認します。

    GitHub Copilot が LINQ クエリを使用して SearchBooks メソッド内で書籍の在庫状況を直接判断する場合は、**Changes** の下に JsonData.cs が表示されない可能性があります。

1. GitHub Copilot を使用して、**[コミット]** のメッセージを生成します。

1. 変更をステージングしてコミットするには、**[コミット]** を選択してから、**[はい]** を選択します。

1. 変更をリモート リポジトリに同期 (またはプッシュ) します。

    要求された場合は、GitHub アカウントを使用して同期を認証および承認します。

#### タスク 3: 変更をリポジトリのメイン ブランチにマージする pull request を作成する

pull request を使用すると、リポジトリのメイン ブランチに対する変更を提案できます。 pull request を作成したら、変更内容をレビューし、チェックに合格したことを確認してから、変更をメイン ブランチにマージできます。 GitHub Copilot を使用すると、レビュー担当者が変更内容を理解するのに役立つ、pull request の概要を生成しやすくなります。

以下の手順に従って、演習のこのセクションを完了します。

1. Web ブラウザーで GitHub リポジトリを開きます。

1. **[pull request]** タブを開きます。

1. **[New pull request](新しい pull request)** を選択します。

1. **[変更の比較]** で、**main** ブランチに **base** が構成されていることを確認します。

1. **[比較]** が **book-availability** ブランチ用に構成されていることを確認します。

    ブランチを構成すると、**main** と **book-availability** の間の変更の比較が表示されます。 CommonActions.cs、ConsoleApp.cs、および JsonDaa.cs ファイルに加えた変更が表示されるはずです。

1. **[pull request の作成]** を選択します。

1. pull request のタイトルを入力します。

    GitHub Copilot Enterprise のサブスクリプションに加入している企業に所属している場合は、GitHub Copilot を使用して pull request の概要を生成できます。 詳細な概要は、変更内容をレビュー担当者が理解するのに役立ちます。

1. GitHub Copilot を使用して、pull request の概要を生成します。

    概要を生成するには、Copilot アクション ボタンを選択し、**[概要]** を選択します。

    [プレビュー] タブを使用して、GitHub Copilot で生成された pull request 概要を確認できます。

1. タイトルと説明にコードの更新が反映されていることを確認し、**[pull request の作成]** を選択します。

1. チェックが完了するのを待ってから、すべてのチェックに合格し、ベース ブランチとの競合がないことを確認します。

    チェックが完了するまでに 1 分かかる場合があります。 変更をメイン ブランチにマージする前に、特定された問題に対処する必要があります。

1. 変更をメイン ブランチにマージするには、**[pull request をマージする]** を選択し、**[マージの確認]** を選択します。

    変更をマージした後、book-availability ブランチを削除できることに注意してください。

1. Visual Studio Code を開きます。

1. リポジトリの **main** ブランチに切り替えます。

1. リモート リポジトリから変更を**プル**します。

    プロンプトが表示されたら、GitHub アカウントを使用してプルを認証および承認します。

1. **book-availability** ブランチに加えた変更が、**main** ブランチに含まれていることを確認します。

    CommonActions.cs と ConsoleApp.cs ファイルに加えた変更は、main ブランチに存在する必要があります。

#### 概要 – 演習 6

この演習では、コードをテストした後、変更をリポジトリの main ブランチにマージしました。 ローカル リポジトリに変更をコミットし、それらをリモート リポジトリと同期させた後、変更をリポジトリの main ブランチにマージする pull request を作成しました。 GitHub Copilot を使用して pull request の概要を生成し、レビュー担当者が変更内容を理解できるようにしました。

## パート 3: GitHub Copilot ツールを使用して単体テストを開発する

### 開始する前に

#### プロジェクトの概要

同僚が UnitTests という名前のテスト プロジェクトを作成しました。 既存の単体テストでは、Library.ApplicationCore プロジェクトのサービス クラスが部分的にカバーされています。 Library.ApplicationCore プロジェクトには、ライブラリ管理システムのビジネス ロジックが含まれています。 UnitTests プロジェクトでは、xUnit フレームワークを使用して単体テストを記述して実行します。 また、このプロジェクトでは NSubstitute ライブラリを使用して、テスト用のモック オブジェクトを作成します。

UnitTests プロジェクトを拡張して、Library.Infrastructure プロジェクトのデータ アクセス クラスをカバーする必要があります。

#### ラボ シナリオ (パート 3)

GitHub Copilot は、コードの単体テストを記述するのに役立ちます。 GitHub Copilot を使用して単体テストを生成するには、いくつかの方法があります。

- **テスト ケースの生成**:GitHub Copilot を使用して、コードのテスト ケースを生成できます。 Copilot は、記述したコードに基づいてテスト ケースを提案できます。 その後、これらのテスト ケースを使用して、コードの単体テストを作成できます。
- **テスト メソッドの生成**:Copilot では、コードのテスト メソッドを生成することもできます。 これらのテスト メソッドを使用して、コードの単体テストを作成できます。
- **テスト アサーションの生成**:Copilot は、単体テストで使用できるアサーションを提案できます。 これらのアサーションは、コードの動作を確認するのに役立ちます。
- **テスト モックの生成**:Copilot では、単体テストで使用できるモック オブジェクトを生成できます。 これらのモック オブジェクトは、テストするコードを依存関係から分離するのに役立ちます。
- **テスト データの生成**:Copilot では、単体テストで使用できるテスト データを生成できます。 このテスト データは、さまざまな入力でコードをテストするのに役立ちます。
- **テスト セットアップ コードの生成**:Copilot では、単体テストのセットアップ コードを生成できます。 このコードは、テストを実行する前にテスト環境を設定するのに役立ちます。
- **テスト ティアダウン コードの生成**:Copilot では、単体テストのティアダウン コードを生成できます。 このコードは、テストの実行後にテスト環境をクリーンアップするのに役立ちます。

このラボのパート 3 では、Library.Infrastructure プロジェクトの単体テストを開発します。

パートには、次の演習が含まれます。

- GitHub Copilot を使用して UnitTests プロジェクトを評価および拡張します。

### 演習 7: GitHub Copilot を使用して UnitTests プロジェクトを評価および拡張する

この演習では、GitHub Copilot を使用して次のタスクを完了します。

1. GitHub Copilot を使用して、既存の UnitTests プロジェクトを評価します。

1. UnitTests プロジェクトを拡張してデータ アクセス クラスのテストを開始します。

#### タスク 1: GitHub Copilot を使用して既存の UnitTests プロジェクトを評価する

現在、UnitTests プロジェクトは次のフォルダー構造を実装しています。

- UnitTests\
  - ApplicationCore\
    - LoanService\
      - ExtendLoan.cs
      - ReturnLoan.cs
    - PatronService\
      - RenewMembership.cs
  - LoanFactory.cs
  - PatronFactory.cs

この構造は、ApplicationCore プロジェクトの Services 部分をミラー化し、サポートします。

- ApplicationCore\
  - Services\
    - LoanService.cs: ExtendLoan メソッドと ReturnLoan メソッドが含まれます。
    - PatronService.cs: RenewMembership メソッドが含まれます。

既存の単体テストを評価すると、Library.Infrastructure プロジェクトのデータ アクセス クラスの単体テストを開発するのに役立ちます。

以下の手順に従って、演習のこのセクションを完了します。

1. エディターで開いているすべてのファイルを閉じます。

1. チャット ビューを開きます。

1. チャット コンテキストに次のファイルを追加します: **LoanFactory.cs**、**PatronFactory.cs**、**ExtendLoan.cs**、**ReturnLoan.cs**、**RenewMembership.cs**、**LoanService.cs**、**PatronService.cs**。

    ファイルは、"tests/UnitTests"、"tests/UnitTests/ApplicationCore/LoanService"、"tests/UnitTests/ApplicationCore/PatronService"、および "src/Library.ApplicationCore/Services" フォルダーにあります。

1. 次のプロンプトを入力します。

    ```plaintext
    @workspace Explain the approach to unit testing that's been implemented in this workspace.
    ```

    このプロンプトは、ワークスペースのコンテキストでの単体テストのアプローチについて説明するように GitHub Copilot に求めます。 応答のコンテキストを提供するために、プロンプトにはいくつかのファイルが含まれています。

1. 少し時間を取って、GitHub Copilot からの応答を確認してください。

    次の説明に似た情報が提示されます。

    - モックの依存関係:テストでは、NSubstitute を使用してインターフェイスのモック実装を作成します。
    - テストの編成:テストは、テストされるメソッドに基づいて個別のファイルに編成されます。 たとえば、ExtendLoan メソッドと ReturnLoan メソッドは、LoanService フォルダーの下で個別のファイルでテストされます。
    - アサーション:アサーションは、各テストの予想される結果を検証するために使用されます。
    - テスト シナリオ:テストでは、入力に基づいて異なる状態を返すなど、メソッドごとにさまざまなシナリオがカバーされています。
    - 分離性: 各テストは、副作用を防ぐために他のテストから分離されます。
    - ファクトリ メソッド:ファクトリ メソッドは、テスト データを一貫して作成するために使用されます。

1. 次のプロンプトを入力します。

    ```plaintext
    @workspace What are the benefits of this approach to unit testing?
    ```

1. 少し時間を取って、GitHub Copilot からの応答を確認してください。

    次に挙げるような利点の一覧を示す説明が表示されます。

    - 依存関係の分離:モックを使用すると、作業単位が依存関係から分離されます。
    - 再現性と一貫性:ファクトリ メソッドは、テスト データを作成するための一貫した方法を提供します。
    - 読みやすさと保守容易性:記述的なテスト メソッドとテスト ステップの明確な配置により、テストの読みやすさが向上します。
    - 包括的なカバレッジ:さまざまなシナリオをテストすることで、コードが堅牢になり、さまざまなエッジ ケースを確実に処理できます。
    - 懸念事項の分離:テスト ロジック自体からテスト データの作成を分離すると、テストがクリーンに保たれ、テスト対象の動作に集中できます。
    - 即時のフィードバック:単体テストを実行すると、コードの正確性に関するフィードバックがすぐに得られます。

1. チャット コンテキストに次のファイルを追加します: **ExtendLoan.cs**、**ReturnLoan.cs**、**RenewMembership.cs**、**LoanFactory.cs**、**PatronFactory.cs**、**LoanService.cs**、**PatronService.cs**。

1. 次のプロンプトを入力します。

    ```plaintext
    @workspace How can I extend the `UnitTests` project to begin testing methods in the `Library.Infrastructure` project? Provide a process overview.
    ```

    このプロンプトは、UnitTests プロジェクトを拡張して、Library.Infrastructure プロジェクトでメソッドのテストを開始するためのプロセスの概要を提供するよう GitHub Copilot に求めます。 応答のコンテキストを提供するために、プロンプトにはいくつかのファイルが含まれています。

1. 少し時間を取って、GitHub Copilot からの応答を確認してください。

    次の説明に似た情報が提示されます。

    ```markdown
    1. Add Project Reference:

      - Open the UnitTests.csproj file located at tests/UnitTests/UnitTests.csproj.
      - Add a reference to the Library.Infrastructure project.

    2. Identify methods to test:

      - Identify the methods in the Library.Infrastructure project that need to be tested. For example, if you want to test the LoanService class, identify the methods in the LoanService class that need to be tested.

    3. Create Test Classes:

      - Create new test classes in the tests/UnitTests directory to test the methods in the Library.Infrastructure project. For example, if you want to test LoanService, create a file named LoanServiceTests.cs.

    4. Write Unit Tests:

      - In the newly created test classes, write unit tests for the methods in the Library.Infrastructure project. Use the xUnit framework for writing tests and NSubstitute for mocking dependencies.

    5. Run Tests:

      - Use Visual Studio Code's integrated terminal or the Test Explorer to run the tests.
      - Ensure that the tests are discovered and executed correctly.
    ```

#### タスク 2: UnitTests プロジェクトを拡張してデータ アクセス クラスのテストを開始する

演習のこのセクションでは、GitHub Copilot を使用して、Library.Infrastructure プロジェクトの単体テストを作成します。

Library.Infrastructure プロジェクトには、ファイル システムを操作して、データを読み込んで保存するデータ アクセス クラスが含まれています。 プロジェクトには、次のクラスが含まれています。

- JsonData:JSON データを読み込んで保存するクラス。
- JsonLoanRepository:ILoanRepository インターフェイスを実装し、JsonData クラスを使用して貸し出しデータを読み込んで保存するクラス。
- JsonPatronRepository:IPatronRepository インターフェイスを実装し、JsonData クラスを使用して利用者データを読み込んで保存するクラス。

まず、JsonLoanRepository クラスの単体テストを記述します。

以下の手順に従って、演習のこのセクションを完了します。

1. プロジェクト ファイル **UnitTests.csproj** をチャット コンテキストに追加します。

1. チャット ビューで次のプロンプトを入力します。

    ```plaintext
    @workspace Explain how to add a reference to the Library.Infrastructure project inside `UnitTests.csproj`.
    ```

    このプロンプトは、GitHub Copilot に、UnitTests.csproj ファイル内に Library.Infrastructure プロジェクトへの参照を追加する方法を説明するように求めます。

1. GitHub Copilot の応答を使用して、UnitTests.csproj ファイルを更新します。

    更新された UnitTests.csproj ファイルは、次の XML コードのようになります。

    ```xml

    <Project Sdk="Microsoft.NET.Sdk">
      <PropertyGroup>
        <TargetFramework>net8.0</TargetFramework>
        <ImplicitUsings>enable</ImplicitUsings>
        <Nullable>enable</Nullable>
        <IsPackable>false</IsPackable>
        <IsTestProject>true</IsTestProject>
      </PropertyGroup>
      <ItemGroup>
        <PackageReference Include="coverlet.collector" Version="6.0.0" />
        <PackageReference Include="Microsoft.NET.Test.Sdk" Version="17.8.0" />
        <PackageReference Include="NSubstitute" Version="5.1.0" />
        <PackageReference Include="xunit" Version="2.5.3" />
        <PackageReference Include="xunit.runner.visualstudio" Version="2.5.3" />
      </ItemGroup>
      <ItemGroup>
        <Using Include="Xunit" />
      </ItemGroup>
      <ItemGroup>
        <ProjectReference Include="..\..\src\Library.ApplicationCore\Library.ApplicationCore.csproj" />
        <ProjectReference Include="..\..\src\Library.Infrastructure\Library.Infrastructure.csproj" />
      </ItemGroup>
    </Project>

    ```

1. **JsonLoanRepository.cs** ファイルを開きます。

    JsonLoanRepository.csは src/Library.Infrastructure/Data/ フォルダーにあります。

1. 少し時間を取って **JsonLoanRepository.cs** ファイルを確認してください。

    ```csharp

    using Library.ApplicationCore;
    using Library.ApplicationCore.Entities;
    namespace Library.Infrastructure.Data;
    public class JsonLoanRepository : ILoanRepository
    {
        private readonly JsonData _jsonData;
        public JsonLoanRepository(JsonData jsonData)
        {
            _jsonData = jsonData;
        }
        public async Task<Loan?> GetLoan(int id)
        {
            await _jsonData.EnsureDataLoaded();
    
            foreach (Loan loan in _jsonData.Loans!)
            {
                if (loan.Id == id)
                {
                    Loan populated = _jsonData.GetPopulatedLoan(loan);
                    return populated;
                }
            }
            return null;
        }
        public async Task UpdateLoan(Loan loan)
        {
            Loan? existingLoan = null;
            foreach (Loan l in _jsonData.Loans!)
            {
                if (l.Id == loan.Id)
                {
                    existingLoan = l;
                    break;
                }
            }
            if (existingLoan != null)
            {
                existingLoan.BookItemId = loan.BookItemId;
                existingLoan.PatronId = loan.PatronId;
                existingLoan.LoanDate = loan.LoanDate;
                existingLoan.DueDate = loan.DueDate;
                existingLoan.ReturnDate = loan.ReturnDate;
                await _jsonData.SaveLoans(_jsonData.Loans!);
                await _jsonData.LoadData();
            }
        }
    }

    ```

1. **JsonLoanRepository** クラスに関する次の詳細に注意してください。

    - JsonLoanRepository クラスには、GetLoan と UpdateLoan という 2 つのメソッドが含まれています。
    - JsonLoanRepository クラスは、JsonData オブジェクトを使用して貸し出しデータの読み込みおよび保存を行います。

    まず、GetLoan メソッドの単体テストを記述します。

1. **UnitTests** プロジェクトの下に次のフォルダー構造を作成します。

    - Infrastructure\
        - JsonLoanRepository\

    このフォルダー構造は、Library.ApplicationCore 単体テストに使用されるアプローチを反映しています。

1. JsonLoanRepository フォルダーに、**GetLoan** という名前のクラス ファイルを作成します。

1. 少し時間を取って、GetLoan 単体テストのフィールド コンストラクターとクラス コンストラクターの要件を検討しましょう。

    JsonLoanRepository.GetLoan メソッドは、呼び出されたときに貸し出し ID パラメーターを受け取ります。 このメソッドでは、"_jsonData.EnsureDataLoaded" を使用して最新の JSON データを取得し、"_jsonData.Loans" を使用して一致する貸し出しを検索します。 このメソッドで一致する貸し出し ID が見つかると、事前設定された貸し出しオブジェクト (populated) が返されます。 メソッドで一致する貸し出し ID を見つけることができない場合は、null 値が返されます。

    GetLoan 単体テストの場合:

    - モック貸し出しリポジトリ オブジェクト ("_mockLoanRepository") を使用すると、一致する ID が見つかったケースをテストできます。 検索する ID を使用してモックを読み込みます。 ReturnLoanTest クラスは、ILoanRepository インターフェイスをモックし、モック貸し出しリポジトリ オブジェクトをインスタンス化する方法を示します。

    - 非モック貸し出しリポジトリ オブジェクト ("_jsonLoanRepository") を使用すると、一致する ID が見つからないケースをテストできます。 ファイルに含まれていないことがわかっている貸し出し ID を指定するだけです (100 を超えるものが機能するはずです)。

    - 非モック JsonLoanRepository オブジェクトを作成するには、JsonData オブジェクトが必要です。 UnitTests プロジェクトは ConsoleApp プロジェクトによって作成された JsonData オブジェクトにアクセスできないため、IConfiguration インターフェイスを使用してオブジェクトを作成する必要があります。

1. チャット コンテキストに、**JsonLoanRepository.cs**、**ReturnLoan.cs**、**LoanService.cs**、**LoanFactory.cs**、および **JsonData.cs** ファイルを追加します。

1. 次のプロンプトを入力します。

    ```plaintext
    @workspace Create fields and a class constructor for the `GetLoan.cs` file. The class will be used to create unit tests for the GetLoan method in the `JsonLoanRepository.cs` file. Create the following private readonly fields: `_mockLoanRepository`, `_jsonLoanRepository`, `_configuration`, and `_jsonData`. Instantiate the fields in the `GetLoanTest` constructor. Use `ConfigurationBuilder` to create a `_configuration` object that can be used to instantiate the JsonData object.
    ```

    このプロンプトは、GitHub Copilot にフィールドとクラス コンストラクターを提案するように求めます。

1. 少し時間を取って、GitHub Copilot からの応答を確認してください。

    次のコード スニペットのようなコード候補が表示されます。

    ```csharp

    using NSubstitute;
    using Library.ApplicationCore;
    using Library.ApplicationCore.Entities;
    using Library.ApplicationCore.Interfaces;
    using Library.Infrastructure.Data;
    using Microsoft.Extensions.Configuration;
    namespace UnitTests.Infrastructure.JsonLoanRepository;
    public class GetLoanTest
    {
        private readonly ILoanRepository _mockLoanRepository;
        private readonly JsonLoanRepository _jsonLoanRepository;
        private readonly IConfiguration _configuration;
        private readonly JsonData _jsonData;
        public GetLoanTest()
        {
            _mockLoanRepository = Substitute.For<ILoanRepository>();
            _configuration = new ConfigurationBuilder()
                .AddJsonFile("appsettings.json")
                .Build();
            _jsonData = new JsonData(_configuration);
            _jsonLoanRepository = new JsonLoanRepository(_jsonData);
        }
        // Add test methods here
    }

    ```

1. GitHub Copilot から提供されるコード候補を使用して、**GetLoan.cs** を更新します。

1. 次の問題に注意してください。

    - コード内で、名前空間と JsonLoanRepository の使用との間に競合があります。 ReturnLoan.cs ファイルと RenewMembership.cs ファイルで使用されるパターンに従って、GetLoans.cs の名前空間を更新する必要があります。

    - コードで ILoanRepository が認識されない場合は、Library.ApplicationCore の using ディレクティブをファイルの先頭に追加することが必要になる場合があります。

    - _configuration オブジェクトが正しくインスタンス化されていない場合は、ConfigurationBuilder を含むコード行の更新が必要になる場合があります。 コードを簡略化して "_configuration = new ConfigurationBuilder().Build();" を使用できます。

    - GitHub Copilot によって "using Library.ApplicationCore.Interfaces" が提案されている場合は、その部分をファイルの先頭から削除できます。

1. 次のコード スニペットに一致するように **GetLoan.cs** ファイルを更新します。

    ```csharp

    using NSubstitute;
    using Library.ApplicationCore;
    using Library.ApplicationCore.Entities;
    using Library.Infrastructure.Data;
    using Microsoft.Extensions.Configuration;
    namespace UnitTests.Infrastructure.JsonLoanRepositoryTests;
    public class GetLoanTest
    {
        private readonly ILoanRepository _mockLoanRepository;
        private readonly JsonLoanRepository _jsonLoanRepository;
        private readonly IConfiguration _configuration;
        private readonly JsonData _jsonData;
        public GetLoanTest()
        {
            _mockLoanRepository = Substitute.For<ILoanRepository>();
            _configuration = new ConfigurationBuilder().Build();
            _jsonData = new JsonData(_configuration);
            _jsonLoanRepository = new JsonLoanRepository(_jsonData);
        }
    }

    ```

    コードの更新では、前のステップで特定された問題に対処します。 プロジェクトをビルドすると、エディターで特定された問題が解決されます。

1. チャット コンテキストに、**JsonLoanRepository.cs**、**ReturnLoan.cs**、**LoanService.cs**、**LoanFactory.cs**、**JsonData.cs**、**Loans.json** の各ファイルを追加します。

1. GetLoan.cs ファイルの内容を選択してから、チャット ビューに次のプロンプトを入力します。

    ```plaintext
    @workspace Update the selection to include a unit test for the `JsonLoanRepository.GetLoan` method. The unit test should test the case where a loan ID is found in the data. Use `_mockLoanRepository` to arrange the expected return loan. Use `_jsonLoanRepository` to return an actual loan. Asserts should verify that the return loan ID matches the expected loan ID. Use a loan ID that exists in the `Loans.json` file.
    ```

    このプロンプトは、GitHub Copilot に対して、JsonLoanRepository.GetLoan メソッドの単体テストを提案するように求めます。 単体テストでは、データに貸し出し ID が見つかったケースをテストする必要があります。 このテストでは、"_mockLoanRepository" を使用して、想定される返却貸出、実際の貸出を返却するための "_jsonLoanRepository"、返却貸出 ID と想定される貸出 ID の一致を確認するためのアサートを用意する必要があります。 貸出 ID は、Loans.json ファイルに存在するはずです。

1. 少し時間を取って、GitHub Copilot からの応答を確認してください。

    次のコード スニペットのようなコード候補が表示されます。

    ```csharp

    using NSubstitute;
    using Library.ApplicationCore;
    using Library.ApplicationCore.Entities;
    using Library.Infrastructure.Data;
    using Microsoft.Extensions.Configuration;
    using Xunit;
    namespace UnitTests.Infrastructure.JsonLoanRepositoryTests;
    public class GetLoanTest
    {
        private readonly ILoanRepository _mockLoanRepository;
        private readonly JsonLoanRepository _jsonLoanRepository;
        private readonly IConfiguration _configuration;
        private readonly JsonData _jsonData;
        public GetLoanTest()
        {
            _mockLoanRepository = Substitute.For<ILoanRepository>();
            _configuration = new ConfigurationBuilder().Build();
            _jsonData = new JsonData(_configuration);
            _jsonLoanRepository = new JsonLoanRepository(_jsonData);
        }
        [Fact(DisplayName = "JsonLoanRepository.GetLoan: Returns loan when loan ID is found")]
        public async Task GetLoan_ReturnsLoanWhenLoanIdIsFound()
        {
            // Arrange
            var loanId = 1; // Use a loan ID that exists in the Loans.json file
            var expectedLoan = new Loan { Id = loanId, BookItemId = 101, PatronId = 202, LoanDate = DateTime.Now, DueDate = DateTime.Now.AddDays(14) };
            _mockLoanRepository.GetLoan(loanId).Returns(expectedLoan);
            await _jsonData.EnsureDataLoaded(); // Ensure data is loaded
            // Act
            var actualLoan = await _jsonLoanRepository.GetLoan(loanId);
            // Assert
            Assert.NotNull(actualLoan);
            Assert.Equal(expectedLoan.Id, actualLoan?.Id);
        }
    }

    ```

1. GitHub Copilot から提供されるコード候補を使用して、**GetLoan.cs** を更新します。

    JsonLoanRepository.GetLoan メソッドは、JSON データが確実に読み込まれるように "_jsonData.EnsureDataLoaded" を呼び出します。 "_jsonData.EnsureDataLoaded" を呼び出すコード行がテスト メソッドに含まれている場合は削除できます。

    コードで Loan クラスが認識されない場合は、GetLoan.cs ファイルの先頭に "using Library.ApplicationCore.Entities" ステートメントを必ず含めます。 Loan クラスは Library.ApplicationCore.Entities 名前空間にあります。

1. エラーが発生しないように AccelerateDevGitHubCopilot ソリューションを構築してください。

1. GitHub Copilot のオートコンプリート機能を使用して、貸し出し ID が見つからない場合のテストを作成します。

    GetLoan_ReturnsLoanWhenLoanIdIsFound メソッドの後に空白行を作成します。

    オートコンプリートの提案を受け入れて、新しいテスト メソッドを作成します。

1. 少し時間を取って、GitHub Copilot からの応答を確認してください。

    GitHub Copilot のオートコンプリート機能は、必要がない場合でも予想される貸し出しをモックする可能性があります。 想定される貸出をモックするコードは削除できますが、Loans.json ファイルに存在しない貸出 ID が必要です。

    次のコード スニペットのいずれかに似たコード候補が表示されます。

    ```csharp

    [Fact(DisplayName = "JsonLoanRepository.GetLoan: Returns null when loan ID is not found")]
    public async Task GetLoan_ReturnsNullWhenLoanIdIsNotFound()
    {
        // Arrange
        var loanId = 999; // Use a loan ID that does not exist in the Loans.json file
        var expectedLoan = new Loan { Id = loanId, BookItemId = 101, PatronId = 202, LoanDate = DateTime.Now, DueDate = DateTime.Now.AddDays(14) };
        _mockLoanRepository.GetLoan(loanId).Returns(expectedLoan);
        // Act
        var actualLoan = await _jsonLoanRepository.GetLoan(loanId);
        // Assert
        Assert.Null(actualLoan);
    }

    ```

1. データ セットにない loanId 値を割り当てるオートコンプリート候補を採用します。

    データ セットにない loanId 番号を割り当てる候補がない場合は、**Ctrl + Enter** キーボード ショートカットを使用して追加の候補を一覧表示できます。

1. 単体テストでは JSON データ ファイルへのアクセスが必要であることに注意してください。

    JsonLoanRepository.GetLoan メソッドは、JsonData オブジェクトを使用して貸出データの読み込みおよび保存を行います。

    JSON データ ファイルは、"Library.Console\Json" フォルダーにあります。 これらのファイルをテスト プロジェクトに含めるには、UnitTests.csproj ファイルを更新する必要があります。

1. 次の XML スニペットを **UnitTests.csproj** ファイルに追加します。

    ```xml

    <ItemGroup>
        <None Include="..\..\src\Library.Console\Json\**\*">
            <Link>Json\%(RecursiveDir)%(FileName)%(Extension)</Link>
            <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>
        </None>
    </ItemGroup>

    ```

    これにより、テストの実行時に JSON データ ファイルが出力ディレクトリにコピーされます。

#### タスク 3: 作業を確認する

JsonLoanRepository クラスの単体テストを実行するには、いくつかの方法があります。 Visual Studio Code のテスト エクスプローラー、統合ターミナル、または "dotnet test" コマンドを使用できます。

以下の手順に従って、演習のこのセクションを完了します。

1. GetLoans.cs ファイルがエディターで開かれていることを確認します。

1. ソリューションをビルドし、エラーがないことを確認します。

    **AccelerateDevGitHubCopilot** を右クリックし、**[ビルド]** を選択します。

1. テスト メソッドの左側にある "緑色の再生ボタン" に注目してください。

1. Visual Studio Code のテスト エクスプローラー ビューを開きます。

    テスト エクスプローラー ビューを開くには、左側のアクティビティ バーにあるビーカー型のアイコンを選択します。 テスト エクスプローラーには、ユーザー インターフェイスで [テスト] というラベルが付けられています。

    テスト エクスプローラーは、ワークスペース内のすべてのテスト ケースを表示するツリー ビューです。 テスト ケースを実行/デバッグし、テスト エクスプローラーを使用してテスト結果を表示できます。

1. **UnitTests** とその下のノードを展開して、**GetLoanTest** を見つけます。

1. 次を実行します: **JsonLoanRepository.GetLoan:Returns loan when loan ID is found** テスト ケース。

    > [!NOTE]
    > GitHub Copilot では、テスト メソッドの名前が異なる場合があります。 データに存在する貸出 ID を使用するテスト メソッドを実行します。

1. テスト エクスプローラー ビューとエディターのテスト結果に注目してください。

    テストに合格したことを示す緑色のチェックマークが表示されます。

1. エディターを使用して、次を実行します: **JsonLoanRepository.GetLoan:Returns null when loan ID is not found** テスト ケース。

1. テスト エクスプローラー ビューとエディターのテスト結果に注目してください。

    エディターからテストを実行するには、テスト メソッドの左側にある緑色の再生ボタンを選択します。

1. **JsonLoanRepository.GetLoan:Returns null when loan ID is not found** テストに合格していることを確認します。

    両方のテストの左側に緑色のチェックマークが表示されているはずです。

#### まとめ - 演習 7

この演習では、GitHub Copilot を使用して既存の UnitTests プロジェクトを評価し、プロジェクトを拡張して Library.Infrastructure プロジェクトのデータ アクセス クラスのテストを開始しました。 UnitTests.csproj ファイルに Library.Infrastructure プロジェクトへの参照を追加し、JsonLoanRepository クラスの単体テストを作成しました。 GitHub Copilot を使用することで、JsonLoanRepository クラスの GetLoan メソッドの単体テストを記述できるようになりました。 Visual Studio Code のテスト エクスプローラーを使用して単体テストを実行し、テストがパスすることを確認しました。

## パート 4: GitHub Copilot ツールを使用してコード セクションをリファクターおよび改善する

### 開始する前に

#### プロジェクトの概要

あなたと仕事仲間は、プロジェクトの初期開発フェーズを完了し、今はコードベースをリファクターおよび改善する方法を調査しています。

コード リファクタリングは、外部の動作を変更せずに既存のコードを再構築するプロセスです。 リファクタリングは、多くの場合コードの特定の側面を改善するために使用されます。 GitHub Copilot は、コードの品質、信頼性、パフォーマンス、セキュリティを向上させる変更を提案することで、コードのリファクターを支援します。

#### ラボ シナリオ (パート 4)

このラボのパート 4 では、GitHub Copilot を使用して、次のコード セクションをリファクターします。

- リフレクションではなくディクショナリを使用するように EnumHelper クラスをリファクターします。 ディクショナリを使用すると、リフレクションのオーバーヘッドが軽減され、パフォーマンスが向上します。 また、リフレクションを排除すると、コードの可読性、保守性、セキュリティも向上します。

- foreach ループではなく LINQ (統合言語クエリ) を使用するようにデータ アクセス メソッドをリファクターします。 LINQ を使用すると、コレクション、データベース、XML ドキュメントのクエリを実行する、より簡潔で読みやすい方法が提供されます。 LINQ を使用すると、コードの可読性、保守性、パフォーマンスを向上させることができます。

パートには次の演習が含まれています。

- GitHub Copilot を使用して EnumHelper クラスをリファクターします。
- GitHub Copilot を使用して、LINQ によるデータ アクセス クラスを改善します。

### 演習 8: GitHub Copilot を使用して EnumHelper クラスをリファクターする

リフレクションは、実行時にオブジェクトを検査および操作できる強力な機能です。 ただし、リフレクションには時間がかかる可能性があり、リフレクションに関連する潜在的なセキュリティ リスクを考慮する必要があります。

既存の EnumHelper クラスは、リフレクションを使用して列挙値の description 属性を取得します。 リフレクションではなくディクショナリを使用するように EnumHelper クラスをリファクターできます。 ディクショナリを使用すると、パフォーマンスが向上し、リフレクションの使用に関連するセキュリティ上の懸念が解消されます。

この演習では、GitHub Copilot を使用して、EnumHelper クラスのリファクターを支援します。

以下の手順に従ってこの演習を完了します。

1. ソリューション エクスプローラー ビューを使用して、EnumHelper.cs ファイルを開きます。

    EnumHelper.cs は src/Library.ApplicationCore/Enums フォルダーにあります。

    ```csharp

    using System.ComponentModel;
    using System.Reflection;
    namespace Library.ApplicationCore.Enums;
    public static class EnumHelper
    {
        public static string GetDescription(Enum value)
        {
            if (value == null)
                return string.Empty;
            FieldInfo fieldInfo = value.GetType().GetField(value.ToString())!;
            DescriptionAttribute[] attributes =
                (DescriptionAttribute[])fieldInfo.GetCustomAttributes(typeof(DescriptionAttribute), false);
            if (attributes != null && attributes.Length > 0)
            {
                return attributes[0].Description;
            }
            else
            {
                return value.ToString();
            }
        }
    }

    ```

1. チャット ビューを開き、**EnumHelper.cs**、**LoanExtensionStatus.cs**、**LoanReturnStatus.cs**、および **MembershipRenewalStatus.cs** ファイルをチャット コンテキストに追加します。

1. 次のプロンプトを入力します。

    ```plaintext
    @workspace I want to refactor the `EnumHelper` class using dictionaries rather than reflection to get enum description attributes. I want a separate dictionary for each enum. The enum values are in the `LoanExtensionStatus.cs`, `LoanReturnStatus.cs`, and `MembershipRenewalStatus.cs` files. Explain how to update the EnumHelper class to use dictionaries and provide the updated code.
    ```

    このプロンプトは、GitHub Copilot に対し、リフレクションではなくディクショナリを使用するように EnumHelper クラスを更新する方法の説明を求めます。 また、列挙値ごとにディクショナリを使用するように更新されたコードも要求します。

1. 少し時間をとって、GitHub Copilot から提供された説明を確認します。

    説明は次のようなものになります。

    ```markdown
    To refactor the EnumHelper class to use dictionaries for each enum, you need to create a dictionary for each enum type that maps the enum values to their descriptions. This will eliminate the need for reflection at runtime.

    Here's how you can update the EnumHelper class:

    1. Create dictionaries for each enum type.
    2. Populate these dictionaries with the enum values and their corresponding descriptions.
    3. Update the GetDescription method to use these dictionaries.

    Below is the updated code for the EnumHelper class:

    ```

    ```csharp

    using System.ComponentModel;
    using System.Collections.Generic;
    namespace Library.ApplicationCore.Enums
    {
        public static class EnumHelper
        {
            private static readonly Dictionary<MembershipRenewalStatus, string> MembershipRenewalStatusDescriptions = new()
            {
                { MembershipRenewalStatus.Success, "Membership renewal was successful." },
                { MembershipRenewalStatus.PatronNotFound, "Patron not found." },
                { MembershipRenewalStatus.TooEarlyToRenew, "It is too early to renew the membership." },
                { MembershipRenewalStatus.LoanNotReturned, "Cannot renew membership due to an outstanding loan." },
                { MembershipRenewalStatus.Error, "Cannot renew membership due to an error." }
            };
            private static readonly Dictionary<LoanReturnStatus, string> LoanReturnStatusDescriptions = new()
            {
                { LoanReturnStatus.Success, "Book was successfully returned." },
                { LoanReturnStatus.LoanNotFound, "Loan not found." },
                { LoanReturnStatus.AlreadyReturned, "Cannot return book as the book is already returned." },
                { LoanReturnStatus.Error, "Cannot return book due to an error." }
            };
            private static readonly Dictionary<LoanExtensionStatus, string> LoanExtensionStatusDescriptions = new()
            {
                { LoanExtensionStatus.Success, "Book loan extension was successful." },
                { LoanExtensionStatus.LoanNotFound, "Loan not found." },
                { LoanExtensionStatus.LoanExpired, "Cannot extend book loan as it already has expired. Return the book instead." },
                { LoanExtensionStatus.MembershipExpired, "Cannot extend book loan due to expired patron's membership." },
                { LoanExtensionStatus.LoanReturned, "Cannot extend book loan as the book is already returned." },
                { LoanExtensionStatus.Error, "Cannot extend book loan due to an error." }
            };
            public static string GetDescription(Enum value)
            {
                if (value == null)
                    return string.Empty;
                return value switch
                {
                    MembershipRenewalStatus status => MembershipRenewalStatusDescriptions[status],
                    LoanReturnStatus status => LoanReturnStatusDescriptions[status],
                    LoanExtensionStatus status => LoanExtensionStatusDescriptions[status],
                    _ => value.ToString()
                };
            }
        }
    }

    ```

    ```markdown

    This refactored EnumHelper class uses dictionaries to store the descriptions for each enum type. The GetDescription method now uses pattern matching to determine the type of the enum and retrieves the description from the appropriate dictionary. This approach avoids the use of reflection and improves performance.

    ```

    > [!NOTE]
    > GitHub Copilot がディクショナリに正しい説明を事前設定しない場合は、GitHub Copilot 拡張機能が再起動を要求していないことを確認します。 している場合は、拡張機能を再起動し、プロンプトをもう一度試してください。

1. GitHub Copilot が提案する EnumHelper クラスを使用して、EnumHelper.cs ファイルを更新します。

1. 更新された EnumHelper クラスが、LoanExtensionStatus.cs、LoanReturnStatus.cs、および MembershipRenewalStatus.cs ファイルの列挙値を使用していることを確認します。

    各列挙ファイルを開き、ディクショナリ内の列挙値が正しいことを確認します。 不整合がある場合は、GitHub Copilot で各列挙型のディクショナリを個別に更新します。 たとえば、LoanExtensionStatus 列挙型に対して次のプロンプトを使用できます。

    ```plaintext
    @workspace Use the description values in LoanExtensionStatus.cs to update the LoanExtensionStatus dictionary in the EnumHelper class. Provide the updated code for the LoanExtensionStatus dictionary in the EnumHelper class.
    ```

    必要に応じて、LoanReturnStatus 列挙型と MembershipRenewalStatus 列挙型に対して同じアプローチを使用します。

1. 少し時間を取って **GetDescription** メソッドを確認してください。

    ```csharp

    public static string GetDescription(Enum value)
    {
        if (value == null)
            return string.Empty;
        return value switch
        {
            MembershipRenewalStatus status => MembershipRenewalStatusDescriptions[status],
            LoanReturnStatus status => LoanReturnStatusDescriptions[status],
            LoanExtensionStatus status => LoanExtensionStatusDescriptions[status],
            _ => value.ToString()
        };
    }

    ```

    このコードは、パターン マッチングを使用して列挙型の型を判断し、適切なディクショナリから説明を取得します。 switch ステートメントは列挙値の型をチェックし、ディクショナリから対応する説明を返します。 列挙値がディクショナリ内に見つからない場合、このメソッドは列挙値を文字列として返します。

    GitHub Copilot にこのコードをリファクターしてラムダ式を削除するように依頼すると、読みやすくなります。

    ```csharp

    public static string GetDescription(Enum value)
    {
        if (value == null)
            return string.Empty;
        switch (value)
        {
            case MembershipRenewalStatus status:
                return MembershipRenewalStatusDescriptions[status];
            case LoanReturnStatus status:
                return LoanReturnStatusDescriptions[status];
            case LoanExtensionStatus status:
                return LoanExtensionStatusDescriptions[status];
            default:
                return value.ToString();
        }
    }

    ```

1. 変更内容を EnumHelper.cs ファイルに保存します。

1. ソリューションを構築してエラーがないことを確認します。

    警告が表示されます。 今のところは無視しても構いません。

#### まとめ - 演習 8

この演習では、GitHub Copilot を使用して、リフレクションではなくディクショナリを使用するように EnumHelper クラスをリファクターしました。 ディクショナリを使用すると、リフレクションのオーバーヘッドが軽減され、パフォーマンスが向上します。 また、リフレクションを排除すると、コードの可読性、保守性、セキュリティも向上します。

### 演習 9: GitHub Copilot を使用して LINQ によるデータ アクセス クラスを改善する

LINQ (言語統合クエリ) は、コレクション、データベース、XML ドキュメントに対し統一した方法でクエリを実行できるようにする C# の強力な機能です。 LINQ は、従来の foreach ループと比較して、データのクエリを実行するためのより簡潔で読みやすい方法を提供します。

この演習には、次のタスクが含まれています。

- LINQ を使用するように JsonData.cs のメソッドをリファクターします。
- LINQ を使用するように JsonLoanRepository.cs のメソッドをリファクターします。
- LINQ を使用するように JsonPatronRepository.cs のメソッドをリファクターします。

#### タスク 1: LINQ を使用するように JsonData.cs のメソッドをリファクターする

JsonData クラスには、次のデータ アクセス メソッドが含まれています。GetPopulatedPatron、GetPopulatedLoan、GetPopulatedBookItem、GetPopulatedBook。 これらのメソッドは、foreach ループを使用してコレクションを反復処理し、オブジェクトを設定します。 これらのメソッドをリファクターして LINQ を使用すると、コードの可読性と保守性が向上します。

以下の手順に従って、演習のこのセクションを完了します。

1. JsonData.cs ファイルを開きます。

1. **GetPopulatedPatron** メソッドを選択します。

    GetPopulatedPatron メソッドは、完全に事前設定された Patron オブジェクトを作成するように設計されています。 これは、Patron の基本プロパティをコピーし、その Loans コレクションを詳細な Loans オブジェクトを使用して事前設定します。

    ```csharp

    public Patron GetPopulatedPatron(Patron p)
    {
        Patron populated = new Patron
        {
            Id = p.Id,
            Name = p.Name,
            ImageName = p.ImageName,
            MembershipStart = p.MembershipStart,
            MembershipEnd = p.MembershipEnd,
            Loans = new List<Loan>()
        };
        foreach (Loan loan in Loans!)
        {
            if (loan.PatronId == p.Id)
            {
                populated.Loans.Add(GetPopulatedLoan(loan));
            }
        }
        return populated;
    }

    ```

1. インライン チャットを開き、LINQ を使用してメソッドをリファクターするプロンプトを入力します。

    ```plaintext
    #selection refactor selection to `return new Patron` using LINQ
    ```

1. 少し時間を取って、おすすめの更新を確認します。

    おすすめの更新は、次のコードのようになります。

    ```csharp

    public Patron GetPopulatedPatron(Patron p)
    {
        return new Patron
        {
            Id = p.Id,
            Name = p.Name,
            ImageName = p.ImageName,
            MembershipStart = p.MembershipStart,
            MembershipEnd = p.MembershipEnd,
            Loans = Loans!
                .Where(loan => loan.PatronId == p.Id)
                .Select(GetPopulatedLoan)
                .ToList()
        };
    }

    ```

    最初に、LINQ クエリを使用して"foreach (Loan loan in Loans!)" ループを置き換えます。 LINQ コードを配置すると、オブジェクト初期化子を使用して、オブジェクト プロパティを新しい Patron オブジェクトに割り当てることができます。 こうすることで、Patron オブジェクトの個別の事前設定インスタンスの必要性が軽減されます。 全体的に、更新されたコードは短くなり、読みやすくなっています。

    このコードは、入力された利用者 "p" を使用して、いくつかの基本プロパティを新しい Patron オブジェクトに割り当てます。 次に、入力された利用者に関連付けられた貸し出しを使用して Loans コレクションを事前設定し、GetPopulatedLoan メソッドを使用して各貸し出しを変換します。

    Loans コレクションを事前設定する LINQ コード行は次のように分解できます。

    - `Loans!`: "Loans!" 式は Loans コレクションにアクセスします。 "!" 演算子は null 免除演算子であり、Loans が null ではないと開発者が確信していることを示します。 GetPopulatedPatron メソッドを呼び出す前に、Loans を適切に初期化する必要があります。
    - `.Where(loan => loan.PatronId == p.Id)`: このコードは、入力された利用者 "p" に属するもののみを含むように、貸し出しをフィルター処理します。
    - `.Select(GetPopulatedLoan)`: このコードは、GetPopulatedLoan メソッドを使用して、フィルター処理された各貸し出しを変換します。
    - `.ToList()`: 結果を Loan オブジェクトのリストに変換します。

1. おすすめの更新を受け入れるには、**[同意する]** を選択します。

    GetPopulatedPatron メソッドをリファクターする方法を見てきましたが、LINQ を使用するように GetPopulatedLoan、GetPopulatedBookItem、および GetPopulatedBook メソッドをリファクターすることもできます。

1. 同じ方法で、**GetPopulatedLoan**、**GetPopulatedBookItem**、および **GetPopulatedBook** メソッドをリファクターします。

    たとえば、次のプロンプトを使用して 3 つのメソッドをリファクターします。

    **GetPopulatedLoan** メソッドの場合:

    ```plaintext
    #selection refactor selection to `return new Loan` using LINQ. Use `GetPopulatedBookItem` for the `BookItem` property. Use `Single` for BookItem and Patron properties.
    ```

    **GetPopulatedBookItem** メソッドの場合:

    ```plaintext
    #selection refactor selection to `return new BookItem` using LINQ. Use `GetPopulatedBook` and `Single` for the `BookItem` property.
    ```

    **GetPopulatedBook** メソッドの場合:

    ```plaintext
    #selection refactor selection to `return new Book` using LINQ. Use `Where` and `Select` for `Author` property. Use `First` author.
    ```

1. おすすめの更新を受け入れたら、少し時間を取って、コードの変更を確認します。

    更新されたコードは、次のコードのようになります。

    ```csharp

    public Loan GetPopulatedLoan(Loan l)
    {
        return new Loan
        {
            Id = l.Id,
            BookItemId = l.BookItemId,
            PatronId = l.PatronId,
            LoanDate = l.LoanDate,
            DueDate = l.DueDate,
            ReturnDate = l.ReturnDate,
            BookItem = GetPopulatedBookItem(BookItems!.Single(bi => bi.Id == l.BookItemId)),
            Patron = Patrons!.Single(p => p.Id == l.PatronId)
        };
    }
    public BookItem GetPopulatedBookItem(BookItem bi)
    {
        return new BookItem
        {
            Id = bi.Id,
            BookId = bi.BookId,
            AcquisitionDate = bi.AcquisitionDate,
            Condition = bi.Condition,
            Book = GetPopulatedBook(Books!.Single(b => b.Id == bi.BookId))
        };
    }
    public Book GetPopulatedBook(Book b)
    {
        return new Book
        {
            Id = b.Id,
            Title = b.Title,
            AuthorId = b.AuthorId,
            Genre = b.Genre,
            ISBN = b.ISBN,
            ImageName = b.ImageName,
            Author = Authors!.Where(a => a.Id == b.AuthorId).Select(a => new Author {
                Id = a.Id,
                Name = a.Name
            }).First()
        };
    }

    ```

1. LINQ クエリの説明を表示するには、**Explain** スマート アクションを使用します。

    **Explain** スマート アクションは、コードで使用されている LINQ クエリの詳細な説明を提供します。

    たとえば、GetPopulatedBook メソッドで **Explain** スマート アクションを使用すると、Book オブジェクトの Author プロパティを事前設定するのに使用される LINQ クエリの説明を表示できます。

    ```csharp

    Author = Authors!.Where(a => a.Id == b.AuthorId).Select(a => new Author {
        Id = a.Id,
        Name = a.Name
    }).First()

    ```

    **Explain** スマート アクションは、Book オブジェクトの Author プロパティを事前設定するのに使用される LINQ クエリの詳細な説明を提供します。

    たとえば、説明は次のようになります。

    ```plaintext
    The active selection is a C# code snippet that assigns a value to the Author property. This value is derived from a collection of Author objects named Authors. The code uses LINQ (Language Integrated Query) to filter and transform the data within this collection.
    
    First, the Authors! expression uses the null-forgiving operator (!) to indicate that Authors is not null, even if the compiler might think otherwise. This is a way to suppress nullable warnings. The Where method is then called on the Authors collection to filter the elements. The lambda expression a => a.Id == b.AuthorId is used to find all Author objects where the Id matches the AuthorId property of another object b.
    
    After filtering, the Select method is used to project each filtered Author object into a new Author object. This is done by creating a new instance of the Author class and copying the Id and Name properties from the original Author object.
    
    Finally, the First method is called to retrieve the first element from the resulting sequence. This means that the Author property will be assigned the first Author object that matches the filter criteria and has been projected into a new Author instance.
    
    This approach ensures that the Author property is set to a new Author object with the same Id and Name as the first matching Author in the Authors collection.
    ```

1. 変更内容を JsonData.cs ファイルに保存します。

1. ソリューションを構築してエラーがないことを確認します。

    警告が表示されます。 今のところは無視しても構いません。

#### タスク 2: LINQ を使用するように JsonLoanRepository.cs のメソッドをリファクターする

JsonLoanRepository クラスには、GetLoan および UpdateLoan データ アクセス メソッドが含まれています。 これら 2 つのメソッドをリファクターし、foreach ループを LINQ に置き換えて、コードの可読性と保守性を向上させます。

以下の手順に従って、演習のこのセクションを完了します。

1. **JsonLoanRepository.cs** ファイルを開きます。

1. **GetLoan** メソッドを選択します。

    GetLoan メソッドは、ID によって貸し出しを取得するように設計されています。

    ```csharp

    public async Task<Loan?> GetLoan(int id)
    {
        await _jsonData.EnsureDataLoaded();
        foreach (Loan loan in _jsonData.Loans!)
        {
            if (loan.Id == id)
            {
                Loan populated = _jsonData.GetPopulatedLoan(loan);
                return populated;
            }
        }
        return null;
    }

    ```

1. インライン チャットを開き、LINQ を使用してメソッドをリファクターするプロンプトを入力します。

    たとえば、次のプロンプトを入力します。

    ```plaintext
    #selection refactor selection using LINQ with `_jsonData.Loans!. Use `Where`, `Select` and `GetPopulatedLoan` to return `FirstOrDefault`.
    ```

1. 少し時間を取って、おすすめの更新を確認します。

    おすすめの更新は、次のコードのようになります。

    ```csharp

    public async Task<Loan?> GetLoan(int id)
    {
        await _jsonData.EnsureDataLoaded();
        Loan? loan = _jsonData.Loans!
            .Where(l => l.Id == id)
            .Select(l => _jsonData.GetPopulatedLoan(l))
            .FirstOrDefault();
        return loan;
    }

    ```

    更新されたコードでは、LINQ を使用してローンのコレクションをフィルター処理し、指定された ID を持つローンのみを含めます。 貸し出しは Null 許容 (`Loan? loan`) として宣言する必要があることに注意してください。 次に、GetPopulatedLoan メソッドを使用して貸し出しを変換し、最初の結果を返します。 一致する貸し出しが見つからない場合、FirstOrDefault は null 値を返します。 このメソッドは、指定された "id" の貸し出しが存在しない場合は null 値となる可能性がある、この貸し出しオブジェクトを返します。 このアプローチにより、返されたローンには必要なすべての関連データが完全に設定され、ローンのレコードの包括的なビューが提供されます。

    このコードはさらに簡略化できます。

    ```csharp

    public async Task<Loan?> GetLoan(int id)
    {
        await _jsonData.EnsureDataLoaded();
        return _jsonData.Loans!
            .Where(l => l.Id == id)
            .Select(l => _jsonData.GetPopulatedLoan(l))
            .FirstOrDefault();
    }

    ```

1. 更新された GetLoan メソッドを受け入れるには、**[Accept]** を選択します。

1. **UpdateLoan** メソッドを選択します。

    ```csharp

    public async Task UpdateLoan(Loan loan)
    {
        Loan? existingLoan = null;
        foreach (Loan l in _jsonData.Loans!)
        {
            if (l.Id == loan.Id)
            {
                existingLoan = l;
                break;
            }
        }
        if (existingLoan != null)
        {
            existingLoan.BookItemId = loan.BookItemId;
            existingLoan.PatronId = loan.PatronId;
            existingLoan.LoanDate = loan.LoanDate;
            existingLoan.DueDate = loan.DueDate;
            existingLoan.ReturnDate = loan.ReturnDate;
            await _jsonData.SaveLoans(_jsonData.Loans!);
            await _jsonData.LoadData();
        }
    }

    ```

1. インライン チャットを開き、LINQ を使用してメソッドをリファクターするプロンプトを入力します。

    たとえば、次のプロンプトを入力します。

    ```plaintext
    #selection refactor selection using LINQ find an existing loan `_jsonData.Loans!. Replace existing loan.
    ```

1. 少し時間を取って、おすすめの更新を確認します。

    おすすめの更新は、次のコードのようになります。

    ```csharp

    public async Task UpdateLoan(Loan loan)
    {
        Loan? existingLoan = _jsonData.Loans!.FirstOrDefault(l => l.Id == loan.Id);
        if (existingLoan != null)
        {
            existingLoan.BookItemId = loan.BookItemId;
            existingLoan.PatronId = loan.PatronId;
            existingLoan.LoanDate = loan.LoanDate;
            existingLoan.DueDate = loan.DueDate;
            existingLoan.ReturnDate = loan.ReturnDate;
            await _jsonData.SaveLoans(_jsonData.Loans!);
            await _jsonData.LoadData();
        }
    }

    ```

    更新されたコードでは、LINQ を使用してローンのコレクション内の既存のローンを検索します。 次に、既存のローンを新しいローン データで更新します。 次に、このメソッドは更新されたローンのコレクションを保存し、データを再読み込みします。 このアプローチにより、ローン データが正しく更新され、変更がデータ ストアに保持されることが保証されます。

    メソッドが実行される前にデータが確実に読み込まれるようにするコードを追加することもできます。

    ```csharp

    public async Task UpdateLoan(Loan loan)
    {
        await _jsonData.EnsureDataLoaded();
        Loan? existingLoan = _jsonData.Loans!.FirstOrDefault(l => l.Id == loan.Id);
        if (existingLoan != null)
        {
            existingLoan.BookItemId = loan.BookItemId;
            existingLoan.PatronId = loan.PatronId;
            existingLoan.LoanDate = loan.LoanDate;
            existingLoan.DueDate = loan.DueDate;
            existingLoan.ReturnDate = loan.ReturnDate;
            await _jsonData.SaveLoans(_jsonData.Loans!);
            await _jsonData.LoadData();
        }
    }

    ```

1. 更新された UpdateLoan メソッドを受け入れるには、**[Accept]** を選択します。

1. 変更内容を JsonLoanRepository.cs ファイルに保存します。

1. ソリューションを構築してエラーがないことを確認します。

    警告が表示されます。 今のところは無視しても構いません。

#### タスク 3: LINQ を使用するように JsonPatronRepository のメソッドをリファクターする

JsonPatronRepository クラスには、SearchPatrons、GetPatron、および UpdatePatron メソッドが含まれており、最適化の有力な候補です。 これらのメソッドをリファクターし、foreach ループを LINQ に置き換えて、コードの可読性と保守性を向上させます。

以下の手順に従って、演習のこのセクションを完了します。

1. **JsonPatronRepository.cs** ファイルを開きます。

1. **SearchPatrons** メソッドを選択します。

    SearchPatrons メソッドは、利用者を名前で検索するように設計されています。

    ```csharp

    public async Task<List<Patron>> SearchPatrons(string searchInput)
    {
        await _jsonData.EnsureDataLoaded();
        List<Patron> searchResults = new List<Patron>();
        foreach (Patron patron in _jsonData.Patrons)
        {
            if (patron.Name.Contains(searchInput))
            {
                searchResults.Add(patron);
            }
        }
        searchResults.Sort((p1, p2) => String.Compare(p1.Name, p2.Name));
        searchResults = _jsonData.GetPopulatedPatrons(searchResults);
        return searchResults;
    }

    ```

1. インライン チャットを開き、LINQ を使用してメソッドをリファクターするプロンプトを入力します。

    たとえば、次のプロンプトを入力します。

    ```plaintext
    #selection refactor selection using LINQ with `_jsonData.Patrons!. Replace the loop with `Where`, `OrderBy`, and `GetPopulatedPatrons`.
    ```

1. 少し時間を取って、おすすめの更新を確認します。

    おすすめの更新は、次のコードのようになります。

    ```csharp

    public async Task<List<Patron>> SearchPatrons(string searchInput)
    {
        await _jsonData.EnsureDataLoaded();
        List<Patron> searchResults = _jsonData.Patrons!
            .Where(patron => patron.Name.Contains(searchInput))
            .OrderBy(patron => patron.Name)
            .ToList();
        searchResults = _jsonData.GetPopulatedPatrons(searchResults);
        return searchResults;
    }

    ```

1. 更新された SearchPatrons メソッドを受け入れるには、**[Accept]** を選択します。

1. **GetPatron** メソッドを選択します。

    GetPatron メソッドは、指定した "id" に一致する利用者を返すように設計されています。

    ```csharp

    public async Task<Patron?> GetPatron(int id)
    {
        await _jsonData.EnsureDataLoaded();
        foreach (Patron patron in _jsonData.Patrons!)
        {
            if (patron.Id == id)
            {
                Patron populated = _jsonData.GetPopulatedPatron(patron);
                return populated;
            }
        }
        return null;
    }

    ```

1. インライン チャットを開き、LINQ を使用してメソッドをリファクターするプロンプトを入力します。

    たとえば、次のプロンプトを入力します。

    ```plaintext
    #selection refactor selection using LINQ with `_jsonData.Patrons!. Use `Where`, `Select` and `GetPopulatedPatron` to return `FirstOrDefault`
    ```

1. 少し時間を取って、おすすめの更新を確認します。

    おすすめの更新は、次のコードのようになります。

    ```csharp

    public async Task<Patron?> GetPatron(int id)
    {
        await _jsonData.EnsureDataLoaded();
        var patron = _jsonData.Patrons!
            .Where(p => p.Id == id)
            .Select(p => _jsonData.GetPopulatedPatron(p))
            .FirstOrDefault();
        return patron;
    }

    ```

    このコードはさらに簡略化できます。

    ```C#

    public async Task<Patron?> GetPatron(int id)
    {
        await _jsonData.EnsureDataLoaded();
        return _jsonData.Patrons!
            .Where(p => p.Id == id)
            .Select(p => _jsonData.GetPopulatedPatron(p))
            .FirstOrDefault();
    }

    ```

1. 更新された GetPatron メソッドを受け入れるには、**[Accept]** を選択します。

1. **UpdatePatron** メソッドを選択します。

    UpdatePatron メソッドは、指定した "id" の利用者を更新するように設計されています。

    ```csharp

    public async Task UpdatePatron(Patron patron)
    {
        await _jsonData.EnsureDataLoaded();
        var patrons = _jsonData.Patrons!;
        Patron existingPatron = null;
        foreach (var p in patrons)
        {
            if (p.Id == patron.Id)
            {
                existingPatron = p;
                break;
            }
        }
        if (existingPatron != null)
        {
            existingPatron.Name = patron.Name;
            existingPatron.ImageName = patron.ImageName;
            existingPatron.MembershipStart = patron.MembershipStart;
            existingPatron.MembershipEnd = patron.MembershipEnd;
            existingPatron.Loans = patron.Loans;
            await _jsonData.SavePatrons(patrons);
            await _jsonData.LoadData();
        }
    }

    ```

1. インライン チャットを開き、LINQ を使用してメソッドをリファクターするプロンプトを入力します。

    たとえば、次のプロンプトを入力します。

    ```plaintext
    #selection refactor selection using LINQ to find `patron` in `_jsonData.Patrons!. Replace existing patron with `patron`.
    ```

1. 少し時間を取って、おすすめの更新を確認します。

    おすすめの更新は、次のコードのようになります。

    ```csharp

    public async Task UpdatePatron(Patron patron)
    {
        await _jsonData.EnsureDataLoaded();
        var patrons = _jsonData.Patrons!;
        var existingPatron = patrons.FirstOrDefault(p => p.Id == patron.Id);
        if (existingPatron != null)
        {
            existingPatron.Name = patron.Name;
            existingPatron.ImageName = patron.ImageName;
            existingPatron.MembershipStart = patron.MembershipStart;
            existingPatron.MembershipEnd = patron.MembershipEnd;
            existingPatron.Loans = patron.Loans;
            await _jsonData.SavePatrons(patrons);
            await _jsonData.LoadData();
        }
    }

    ```

1. 更新された UpdatePatron メソッドを受け入れるには、**[Accept]** を選択します。

#### タスク 4:作業を確認する

作業内容を確認するには、以下の手順を実行します。

1. ソリューションをクリーンアップするには、**AccelerateAppDevGitHubCopilot** を右クリックし、**[Clean]** を選択します。

    このアクションにより、以前のビルドからビルド成果物が削除されます。 ソリューションをクリーンすると、JSON データ ファイルが (出力ディレクトリ内で) 元の値に効率的にリセットされます。

1. アプリケーションをビルドして、エラーがないことを確認します。

1. アプリケーションを実行します。

    **Library.Console** プロジェクトを右クリックし、**[デバッグ]** を選択して、**[新しいインスタンスの開始]** を選択することで、ソリューション エクスプローラー ビューからアプリケーションを実行できます。

1. パトロン名の入力を求められたら、「**One**」と入力して Enter キーを押します。

1. "Matching Patrons" プロンプトで「**2**」と入力し、Enter キーを押します。

1. "Book Loans" プロンプトで「**1**」と入力し、Enter キーを押します。

1. "Input Options" プロンプトで「**r**」と入力し、Enter キーを押します。

1. **"Book was successfully returned."** (書籍は問題なく返却されました) というメッセージが表示されることを 確認します。

1. 新しい検索を開始するには、「**s**」と入力して Enter キーを押します。

1. パトロン名の入力を求められたら、「**One**」と入力して Enter キーを押します。

1. "Matching Patrons" プロンプトで「**2**」と入力し、Enter キーを押します。

1. 最初の書籍貸出が **Returned: True** とマークされていることを確認します。

1. "Input Options" プロンプトで「**q**」と入力し、Enter キーを押します。

1. アプリケーションを停止します。

#### まとめ - 演習 9

この演習では、LINQ を使用するように JSONData、JsonLoanRepository、および JsonPatronRepository クラスのデータ アクセス メソッドをリファクターしました。 これらの変更により、コードの可読性、保守性、パフォーマンスが向上します。
