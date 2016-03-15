FROM ruby:2.2.0
RUN apt-get update -qq && apt-get install -y build-essential libpq-dev vim git nodejs mtr
RUN mkdir /root/.ssh
RUN chmod 700 /root/.ssh/
COPY bitbucket_priv_key /root/.ssh/id_rsa
RUN chmod 600 /root/.ssh/id_rsa
RUN touch /root/.ssh/known_hosts
RUN ssh-keyscan bitbucket.org >> /root/.ssh/known_hosts
WORKDIR /home/
run git clone -b panel-v2-mysql-docker git@bitbucket.org:4eixos/panel-v2.git
WORKDIR /home/panel-v2
run git pull
RUN bundle install
RUN rm -f /root/.ssh/id_rsa
ADD . /home/panel-v2



