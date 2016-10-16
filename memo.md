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

~~~
sudo yum install git
sudo yum groupinstall "Development Tools"
sudo yum -y install bzip2-devel readline-devel openssl-devel
~~~

~~~
sudo yum install sloccount
~~~

#### Plugins

* pyenv
* Shining Panda
* Violations
* Cobertura

### Docker

~~~
sudo yum update

sudo tee /etc/yum.repos.d/docker.repo <<-'EOF'
[dockerrepo]
name=Docker Repository
baseurl=https://yum.dockerproject.org/repo/main/centos/7/
enabled=1
gpgcheck=1
gpgkey=https://yum.dockerproject.org/gpg
EOF

sudo yum install docker-engine
sudo systemctl enable docker.service
sudo systemctl start docker
sudo docker run --rm hello-world

usermod -a -G docker jenkins
sudo yum -y install sqlite sqlite-devel
~~~




#Jenkinsのログイン手順

WEBブラウザで、http://192.168.33.10:8080 にアクセスする。
以下のコマンドで取得した初期パスワードを画面に入力する。

~~~
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
~~~
