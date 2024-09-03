# ベースイメージとしてPHP Apacheイメージを使用
FROM php:8.2-apache

# 必要な拡張モジュールをインストール
RUN apt-get update && apt-get install -y \
    libpq-dev \
    && docker-php-ext-install pdo pdo_pgsql

# Node.jsとnpmをインストール
RUN curl -sL https://deb.nodesource.com/setup_16.x | bash - && \
    apt-get install -y nodejs

# 作業ディレクトリを設定
WORKDIR /var/www/html

# Composerのインストール
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# プロジェクトファイルをコピー
COPY . /var/www/html

# 権限を設定
RUN chown -R www-data:www-data /var/www/html

# Laravel用ポートを設定
EXPOSE 80

# Apacheの設定
RUN echo "\n\
    <VirtualHost *:80>\n\
    DocumentRoot /var/www/html/public\n\
    <Directory /var/www/html/public>\n\
    AllowOverride All\n\
    Require all granted\n\
    </Directory>\n\
    </VirtualHost>" > /etc/apache2/sites-available/000-default.conf

