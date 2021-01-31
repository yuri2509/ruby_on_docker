FROM ruby:2.5.1

# 必要なパッケージのインストール
RUN apt-get update -qq && \
  apt-get install -y build-essential libpq-dev


# yarnのインストール(vueを利用している場合に必要)
RUN apt-get update && apt-get install -y curl apt-transport-https wget && \
  curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - && \
  echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list && \
  apt-get update && apt-get install -y yarn

# Nodeのインストール(vueを利用している場合に必要)
RUN curl -sL https://deb.nodesource.com/setup_13.x | bash - && \
  apt-get install -y nodejs

RUN mkdir /app
RUN cd /app
RUN gem install bundler
COPY ./sample_rails_application/ /app
WORKDIR /app

EXPOSE 3000

# 実行したいコマンド
CMD ["ruby", "-v"]
