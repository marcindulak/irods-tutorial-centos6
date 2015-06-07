-----------
Description
-----------

Configure iRODS iCAT server and iRODS client, on CentOS 6.


------------
Sample Usage
------------

Assuming you have VirtualBox and Vagrant installed
https://www.virtualbox.org/ https://www.vagrantup.com/downloads.html::

        $ git clone https://github.com/marcindulak/irods-tutorial-centos6.git
        $ cd irods-tutorial-centos6/vagrant
        $ vagrant up

This installs the iRODS iCAT server **icat1** and an iRODS client **client1**.
The **vagrant** rodsuser is configured on **icat1** with **vagrant** password.

Create the irods environment file::

        $ vagrant ssh client1 -c "sudo su - vagrant -c 'mkdir -p ~/.irods'"
        $ vagrant ssh client1 -c "sudo su - vagrant -c 'cp /vagrant/vagrant/.irods/irods_environment.json ~/.irods'"

and test the basic functionality of iRODS with, e.g.::

        $ vagrant ssh client1 -c "sudo su - vagrant -c 'ienv'"
        $ vagrant ssh client1 -c "sudo su - vagrant -c 'echo vagrant | iinit'"
        $ vagrant ssh client1 -c "sudo su - vagrant -c 'ils'"
        $ vagrant ssh client1 -c "sudo su - vagrant -c 'echo 1 > testfile'"
        $ vagrant ssh client1 -c "sudo su - vagrant -c 'iput testfile'"
        $ vagrant ssh client1 -c "sudo su - vagrant -c 'ils'"
        $ vagrant ssh client1 -c "sudo su - vagrant -c 'irm testfile'"
        $ vagrant ssh client1 -c "sudo su - vagrant -c 'ils'"

See https://wiki.irods.org/index.php/Tutorial for more complex examples.

When done, destroy the test machines with::

        $ vagrant destroy -f

------------
Dependencies
------------

None


-------
License
-------

BSD 2-clause


----
Todo
----

Just some examples:

1. configure iCAT high-availability
2. add a resource server
3. iCAT backup an restore
4. configure idrop-web
5. configure storage1 as a resource
6. configure a microservice which performs automatic backups on storage1
