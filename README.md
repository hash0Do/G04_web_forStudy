# G04_web_forStudy

## G04 Webアプリチーム 学習用Repository
**フロントエンド、バックエンド共用の学習用リポジトリです。**  

  どのように使っても問題ないです。勉強用なので、どんどん作ってどんどん触ってみましょう。  
  GitHubのリポジトリにも様々な機能(Issues, Projects, etc.)があるので、そちらも是非勝手に触ってみてください。  
  このリポジトリが壊れても別に問題ないです。  
  もし不安であれば、ご自身のGitHubアカウントで作成して個人的にやってもOKです。これはあくまでもチームでアプリ開発をする際にテスト的に使えるリポジトリと思ってください。  


## よく使うGitHubコマンド
**<span style="color: red; ">※まずはGitをローカルにインストールください↓</span>**<br>
[Gitインストール方法](https://www.sejuku.net/blog/73444#index_id4)
<br>

以下はリモートリポジトリとローカルリポジトリの連携をして、test.txtをリモートリポジトリに配置する(push)までの流れでコマンドを列挙しています。ご参考ください。

<br>
リモートリポジトリとローカルリポジトリの関係性と主要なコマンドの挙動のイメージは以下の通り。
<img width=100% height=75% src="https://www.server-memo.net/wp-content/uploads/2018/12/github_work_overview.jpg">

1.  **git clone**  

    最初にローカルPCに、リモートリポジトリ(このリポジトリ)と連携する際に利用する。<br>
    そこで以下の`git clone`コマンドを実行する。
    ```git:git clone  
    $ git clone https://github.com/hash0Do/G04_web_forStudy.git
    Cloning into 'G04_web_forStudy'...
    remote: Enumerating objects: 54, done.
    remote: Counting objects: 100% (54/54), done.
    remote: Compressing objects: 100% (35/35), done.
    remote: Total 54 (delta 16), reused 3 (delta 0), pack-reused 0
    Receiving objects: 100% (54/54), 11.93 KiB | 2.39 MiB/s, done.
    Resolving deltas: 100% (16/16), done.
    ```
    すると実行されたディレクトリ内に「.git」ディレクトリというgitを操作する上で必要なファイル群が作成されます。
    ```git:
    $ ls -a
    ./  ../  .git/  G04_web_forStudy/
    ```
    
2.  **git add**  

    G04_web_forStudyフォルダに移動しtest.txtを作成する。git bashで`touch test.txt`を実行しても、エクスプローラでtext.txtを作っても問題ない。<br>
    作成された後`git add`を実行し、test.txtをステージングに移動させる。
    これによって、バージョン管理対象にすることができる。
    ```git:
    $ git add ./test.txt   
    ```
    
3.  **git status**  

     addした後、作業ディレクトリ(ローカルPCのcloneしたディレクトリ)にバージョン管理対象になっているものを確認できる。  
     ```git: git status
     $ git status
     On branch main
     Your branch is up to date with 'origin/main'.
     
     Changes to be committed:
     (use "git restore --staged <file>..." to unstage)
         new file:   test.txt
     ```
   

4.  **git commit**  

    addしたファイルをローカルリポジトリに登録する。これで、リモートリポジトリに配置(push)するための準備ができる。
    ```git: git commit
    $ git commit
    [main 2e1c545] First commit
    1 file changed, 0 insertions(+), 0 deletions(-)
    create mode 100644 test.txt
    ```
    その後`git status`で正常にaddされたものが消えているか確認。
    ```git: git status
    $ git status
    On branch main
    Your branch is ahead of 'origin/main' by 2 commits.
    (use "git push" to publish your local commits)

    nothing to commit, working tree clean
    ```

5.  **git log**  

    commitした情報を確認するコマンド。
    ```git: git log
    $ git log
    commit 2e1c545ce3eaaff0dc68c962860ca11929e5f0d7 (HEAD -> main)
    Author: TAISEIKAMIMIZU <tafutoji9121@gmail.com>
    Date:   Sat Oct 21 11:15:18 2023 +0900

      First commit    
    ```

6.  **git push**  

    いよいよローカルリポジトリからリモートリポジトリに配置します。`git push`コマンドで実施します。
    ```git: git push
    $ git push
    Enumerating objects: 16, done.
    Counting objects: 100% (16/16), done.
    Delta compression using up to 8 threads
    Compressing objects: 100% (10/10), done.
    Writing objects: 100% (13/13), 1.41 KiB | 159.00 KiB/s, done.
    Total 13 (delta 0), reused 0 (delta 0), pack-reused 0
    To https://github.com/hash0Do/G04_web_forStudy.git
       aa03694..b891dbe  main -> main
    ```

これ以降でエラーが出た場合は、各自で調べてみてください。分からなければSlackで！
※ちなみにVSCodeを使うなら、GUIでもっと分かりやすいので開発時はこっちを使いましょう。  
しかし内部的にどのような動きをしているか確認できるのがGit Bashのいいところではあります。
