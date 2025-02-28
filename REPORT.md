bari@ubuntu24:~$ export GITHUB_USERNAME=YaQQrQ
bari@ubuntu24:~$ export GITHUB_EMAIL=bari.tsapaev@gmail.com
bari@ubuntu24:~$ export GITHUB_TOKEN=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
bari@ubuntu24:~$ alias edit=nano
bari@ubuntu24:~$ cd ${GITHUB_USERNAME}/workspace
bari@ubuntu24:~/YaQQrQ/workspace$ source scripts/activate
bari@ubuntu24:~/YaQQrQ/workspace$ mkdir ~/.config
mkdir: cannot create directory ‘/home/bari/.config’: File exists
bari@ubuntu24:~/YaQQrQ/workspace$ cat > ~/.config/hub <<EOF
> github.com:
> - user: ${GITHUB_USERNAME}
> oauth_token: ${GITHUB_TOKEN}
> protocol: https
> EOF
bari@ubuntu24:~/YaQQrQ/workspace$ git config --global hub.protocol https
bari@ubuntu24:~/YaQQrQ/workspace$ mkdir projects/lab02 && cd projects/lab02
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git init
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint:
hint: 	git config --global init.defaultBranch <name>
hint:
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint:
hint: 	git branch -m <name>
Initialized empty Git repository in /home/bari/YaQQrQ/workspace/projects/lab02/.git/
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git init
Reinitialized existing Git repository in /home/bari/YaQQrQ/workspace/projects/lab02/.git/
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git config --global user.name ${GITHUB_USERNAME}
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git config --global user.email ${GITHUB_EMAIL}
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git config -e --global
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git remote add origin https://github.com/${GITHUB_USERNAME}/lab02.git
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (4/4), 1.48 KiB | 758.00 KiB/s, done.
From https://github.com/YaQQrQ/lab02
 * branch            master     -> FETCH_HEAD
 * [new branch]      master     -> origin/master
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ touch README.md
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git status
On branch master
nothing to commit, working tree clean
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git add README.md
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git commit -m"added README.md"
On branch master
nothing to commit, working tree clean
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git push origin master
Username for 'https://github.com': YaQQrQ
Password for 'https://YaQQrQ@github.com': 
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/YaQQrQ/lab02.git/'
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git pull origin master
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (2/2), done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0 (from 0)
Unpacking objects: 100% (3/3), 981 bytes | 981.00 KiB/s, done.
From https://github.com/YaQQrQ/lab02
 * branch            master     -> FETCH_HEAD
   d57da5b..78b07c8  master     -> origin/master
Updating d57da5b..78b07c8
Fast-forward
 .gitignore | 4 ++++
 1 file changed, 4 insertions(+)
 create mode 100644 .gitignore
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git log
commit 78b07c86ea7dac2a2b92605f8ea99bd4231ef611 (HEAD -> master, origin/master)
Author: YaQQrQ <bari.tsapaev@gmail.com>
Date:   Fri Feb 28 18:22:24 2025 +0000

    Create .gitignore

commit d57da5b835063e183a4d1f1eddef909316959ea8
Author: YaQQrQ <bari.tsapaev@gmail.com>
Date:   Fri Feb 28 18:14:57 2025 +0000

    Initial commit
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ mkdir sources
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ mkdir include
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ mkdir examples
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ cat > sources/print.cpp <<EOF
> #include <print.hpp>

void print(const std::string& text, std::ostream& out)
{
  out << text;
}

void print(const std::string& text, std::ofstream& out)
{
  out << text;
}
> EOF
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ cat > include/print.hpp <<EOF
> #include <fstream>
#include <iostream>
#include <string>

void print(const std::string& text, std::ofstream& out);
void print(const std::string& text, std::ostream& out = std::cout);
EOF
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ cat > examples/example1.cpp <<EOF
> #include <print.hpp>

int main(int argc, char** argv)
{
  print("hello");
}
EOF
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ cat > examples/example2.cpp <<EOF
> #include <print.hpp>

#include <fstream>

int main(int argc, char** argv)
{
  std::ofstream file("log.txt");
  print(std::string("hello"), file);
}
EOF
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ ^C
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ edit README.md
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git add .
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git commit -m"added sources"
[master fd8e837] added sources
 5 files changed, 34 insertions(+), 1 deletion(-)
 create mode 100644 examples/example1.cpp
 create mode 100644 examples/example2.cpp
 create mode 100644 include/print.hpp
 create mode 100644 sources/print.cpp
bari@ubuntu24:~/YaQQrQ/workspace/projects/lab02$ git push origin master
Username for 'https://github.com': YaQQrQ
Password for 'https://YaQQrQ@github.com': 
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/YaQQrQ/lab02.git/'
bari@ubuntu24:~$ cd ~/workspace/
bash: cd: /home/bari/workspace/: No such file or directory
bari@ubuntu24:~$ ^C
bari@ubuntu24:~$ cd ~/YaQQrQ/workspace/
bari@ubuntu24:~/YaQQrQ/workspace$ export LAB_NUMBER=02
bari@ubuntu24:~/YaQQrQ/workspace$ git clone https://github.com/tp-labs/lab${LAB_NUMBER}.git tasks/lab${LAB_NUMBER}
Cloning into 'tasks/lab02'...
remote: Enumerating objects: 96, done.
remote: Counting objects: 100% (3/3), done.
remote: Compressing objects: 100% (3/3), done.
remote: Total 96 (delta 0), reused 1 (delta 0), pack-reused 93 (from 1)
Receiving objects: 100% (96/96), 1.29 MiB | 4.05 MiB/s, done.
Resolving deltas: 100% (28/28), done.
bari@ubuntu24:~/YaQQrQ/workspace$ mkdir reports/lab${LAB_NUMBER}
bari@ubuntu24:~/YaQQrQ/workspace$ cp tasks/lab${LAB_NUMBER}/README.md reports/lab${LAB_NUMBER}/REPORT.md
bari@ubuntu24:~/YaQQrQ/workspace$ cd reports/lab${LAB_NUMBER}
bari@ubuntu24:~/YaQQrQ/workspace/reports/lab02$ alias edit=nano
bari@ubuntu24:~/YaQQrQ/workspace/reports/lab02$ edit REPORT.md
bari@ubuntu24:~/YaQQrQ/workspace/reports/lab02$ gist REPORT.md
gist: (WARNING) fread failed (command) on CGM file REPORT.md
gist: (WARNING) BEGIN METAFILE element missing
gist: (WARNING) REPORT.md is not a binary CGM, cannot open
