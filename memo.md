# 環境構成

Jenkins(Master) 192.168.33.10


# バージョン

|Name|Version|
|:-|:-|
|Vagrant|1.8.5|
|CentOS|7.2|
|OpenJDK|1.8.0|
|Jenkins| 2.19.1|

# インストール手順

## Vagrant
~~~
mkdir /path/to/workdir/
vagrant init bento/centos-7.2
~~~

## Jenkins

対象はVagrantで起動したJenkins(Master)

### epel
~~~
sudo yum -y install epel-release
~~~

### Java
~~~
sudo yum -y install java-1.8.0-openjdk
~~~

### Jenkins

~~~
sudo wget -O /etc/yum.repos.d/jenkins.repo http://pkg.jenkins-ci.org/redhat-stable/jenkins.repo
sudo rpm --import https://jenkins-ci.org/redhat/jenkins-ci.org.key
sudo yum -y install jenkins
~~~

~~~
sudo systemctl enable jenkins
sudo systemctl start jenkins
~~~

### Docker



#Jenkinsのログイン手順

WEBブラウザで、http://192.168.33.10:8080 にアクセスする。
以下のコマンドで取得した初期パスワードを画面に入力する。

~~~
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
~~~
