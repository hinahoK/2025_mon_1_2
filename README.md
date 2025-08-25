作成手順

1.dockerのインストール
    Amazon Linux 2 の場合　下記のコマンドを入力：
        sudo mkdir -p /usr/local/lib/docker/cli-plugins/
        sudo curl -SL https://github.com/docker/compose/releases/download/v2.36.0/docker-compose-linux-x86_64 -o /usr/local/lib/docker/cli-plugins/docker-compose
        sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose
    インストールできたかどうか確認する
    docker compose version

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

