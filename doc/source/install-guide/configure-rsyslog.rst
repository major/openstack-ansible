`Home <index.html>`_ OpenStack-Ansible Installation Guide

Configuring rsyslog (optional)
------------------------------

Collecting logs is critical for troubleshooting and for security auditing
within the OpenStack infrastructure. The openstack-ansible project configures
a container with an rsyslog server to receive logs from all of the containers
as well as certain logs from the hosts.

By default, rsyslog is configured to listen for log traffic in three ways:

* UDP plaintext traffic to port 514
* TCP plaintext traffic to port 514
* TLS encrypted TCP traffic to port 10514

All rsyslog customizations are done within
``/etc/openstack_deploy/user_variables.yml``.

Securing rsyslog communication with SSL certificates
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The openstack-ansible project provides TLS encrypted log reception for rsyslog
by default.  To opt-out of this configuration, set
``rsyslog_server_tls_reception`` to ``false``:

.. code-block:: yaml

    rsyslog_server_tls_reception: false

Sensitive information often appears inside rsyslog data from certain OpenStack
services and deployers are **strongly urged** to transmit log traffic over
encrypted connections whenever possible.

The deployment of certificates for rsyslog can be easily customized.
Self-signed certificates are generated and used for the rsyslog server by
default, but user-provided certificates can be used as well.  Refer to
`Securing services with SSL certificates`_ for available configuration
options.

.. _Securing services with SSL certificates: configure-sslcertificates.html

--------------

.. include:: navigation.txt
