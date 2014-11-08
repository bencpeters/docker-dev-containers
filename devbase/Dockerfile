FROM ubuntu:14.04
MAINTAINER Ben Peters

RUN apt-get update -y
RUN apt-get install -y git build-essential gdb strace cmake vim curl python python-dev

RUN useradd benpeters -u 1000 -s /bin/bash -m -p $(echo "password" | openssl passwd -1 -stdin)

RUN mkdir /var/shared/
RUN chown -R benpeters:benpeters /var/shared
VOLUME ["/var/shared"]

RUN chown -R benpeters:benpeters /home/benpeters
RUN adduser benpeters sudo
RUN mkdir /var/run/screen; chmod 777 /var/run/screen
WORKDIR  /home/benpeters
ENV HOME /home/benpeters
USER benpeters

RUN mkdir Downloads;
RUN cd Downloads; git clone https://github.com/bencpeters/Environment-Configuration.git
RUN cp Downloads/Environment-Configuration/.bash_profile ./
RUN cp Downloads/Environment-Configuration/.bashrc ./
RUN cp Downloads/Environment-Configuration/.gemrc ./
RUN cp Downloads/Environment-Configuration/.inputrc ./
RUN cp Downloads/Environment-Configuration/.vimrc ./
RUN cp Downloads/Environment-Configuration/.screenrc ./
RUN cp Downloads/Environment-Configuration/.gitconfig ./
RUN cp Downloads/Environment-Configuration/.git-completion.bash ./
RUN cp -rf Downloads/Environment-Configuration/.vim ./
RUN vim +BundleInstall +qall
RUN cd .vim/bundle/YouCompleteMe; ./install.sh --clang-completer; cp third_party/ycmd/examples/.ycm_extra_conf.py /home/benpeters

#RUN cd Downloads; \curl -sSL https://get.rvm.io | bash -s stable

RUN mkdir -p /var/shared/Dev; ln -s /var/shared/Dev

EXPOSE 8080
EXPOSE 3000
