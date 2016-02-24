FROM centos:7
MAINTAINER michael@faille.io <michael@faille.io>

RUN rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-CentOS-7 && \
    rpm --import https://getfedora.org/static/352C64E5.txt && \
    yum -y localinstall https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm && \
    yum -y install ansible wget which git make rpm-build python2-devel asciidoc && \
    git clone  -b v2.0.1.0-0.2.rc2 --single-branch --depth=1 https://github.com/ansible/ansible.git --recursive && \
    cd ./ansible; v make rpm; rpm -Uvh ./rpm-build/ansible-*.noarch.rpm; cd  ..; rm -Rf ansible

COPY requirements.yml requirements.yml
RUN ansible-galaxy install -r requirements.yml -vvvv --force
# git clone https://github.com/mikefaille/packer-ansible-bigdata.git && \

    # echo "{ install_date: 'Sun Feb  21 12:00:00 2016', version: 0.0.1 }"  | tee /etc/ansible/roles/packer-ansible-bigdata/meta/.galaxy_install_info && \

   # ansible-playbook packer-ansible-bigdata/site.yml -i "localhost," -c local -vvvv
