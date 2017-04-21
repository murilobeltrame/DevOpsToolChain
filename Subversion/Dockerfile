FROM debian:latest

RUN apt-get update -y
RUN apt-get install -y wget
RUN apt-get install -y subversion apache2 libapache2-svn
RUN svnadmin create /home/svn
RUN addgroup subversion
RUN usermod -a -G subversion www-data
RUN chown -R www-data:subversion /home/svn
RUN chmod -R g+rws /home/svn
RUN /usr/sbin/a2enmod auth_digest
RUN rm /etc/apache2/mods-available/dav_svn.conf
ADD dav_svn.conf /etc/apache2/mods-available/dav_svn.conf
RUN mkdir -p /etc/subversion


EXPOSE 80