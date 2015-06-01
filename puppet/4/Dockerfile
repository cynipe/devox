FROM centos:centos6

RUN rpm -ivh http://yum.puppetlabs.com/puppetlabs-release-pc1-el-6.noarch.rpm \
  && yum -y install puppet-agent \
  && yum clean all

ADD puppet.sh /etc/profile.d/
