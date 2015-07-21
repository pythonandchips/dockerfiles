FROM debian:sid

RUN apt-get update

ENV RUBY_MAJOR 2.2
ENV RUBY_VERSION 2.2.2

RUN apt-get update && apt-get install -y build-essential curl procps libffi-dev automake bison  \
    autoconf pkg-config libreadline6 libreadline6-dev openssl libssl-dev git-core zlib1g zlib1g-dev \
    libpq-dev libyaml-dev libxml2-dev libxslt1-dev bison ruby && rm -rf /var/lib/apt/lists/*

ENV GEM_HOME /usr/local/bundle
ENV PATH $GEM_HOME/bin:$PATH
ENV BUNDLE_APP_CONFIG $GEM_HOME

RUN mkdir -p /usr/src/ruby \
    && curl -o /usr/src/ruby/ruby-${RUBY_VERSION}.tar.gz http://cache.ruby-lang.org/pub/ruby/${RUBY_MAJOR}/ruby-${RUBY_VERSION}.tar.gz \
    && tar -zxvf /usr/src/ruby/ruby-${RUBY_VERSION}.tar.gz -C /usr/src/ruby \
    && cd /usr/src/ruby/ruby-${RUBY_VERSION} \
    && ./configure --disable-install-doc \
    && make \
    && make install \
    && apt-get purge -y --auto-remove bison ruby \
    && rm -r /usr/src/ruby

RUN echo 'gem: --no-rdoc --no-ri' >> "$HOME/.gemrc" \
    && gem install bundler \
    && bundle config --global path "$GEM_HOME" \
    && bundle config --global bin "$GEM_HOME/bin"

