作成手順

1.dockerのインストール
    Amazon Linux 2 の場合　下記のコマンドを入力：
    sudo yum install -y docker
    sudo systemctl start docker
    sudo systemctl enable docker

    インストールできたかどうか確認する
    sudo usermod -a -G docker ec2-user

2.作業用ディレクトリを作ってその中に移動（例：dockertest）
    mkdir dockertest
    cd dockertest

3.dockertest内で
    docker compose build
    docker compose up

4.DB(MySQL)にテーブルを作成
    今回作成したDockerコンテナ(コンテナ名はmysql)内のMySQLサーバーにmysqlコマンドで接続する場合は、
    docker compose exec mysql mysql example_db
    と入力

    テーブルの作成
    CREATE TABLE `bbs_entries` (
        `id` INT UNSIGNED NOT NULL AUTO_INCREMENT PRIMARY KEY,
        `body` TEXT NOT NULL,
        `image_filename` TEXT DEFAULT NULL,
        `created_at` DATETIME DEFAULT CURRENT_TIMESTAMP
        );

