.. _appx-nag2mqtt:

************************
Appendix: nag2mqtt Setup
************************

About
=====

nag2mqtt consists of a *Nagios Event Broker* (NEB) module and a small perl daemon. The NEB module
publishes all check results in the local filesystem (using tmpfs is highly recommended).
These file are than publish by the perl daemon to a MQTT broker.

By publishing the check results via MQTT it is possible to visualize the Nagios check states and performance data
in SNMD using the `snmd-widgets-nagios <http://snmd.readthedocs.io/projects/snmd-widgets-nagios/en/latest/>`_ widgets.


Prerequisites
=============

You need a running `Nagios Core <https://www.nagios.org/projects/nagios-core/>`_ setup or an extension like
`Check_MK <https://mathias-kettner.de/check_mk.html>`_.


Perl
----

nag2sms has several dependencies on Perl modules available in `CPAN <https://www.cpan.org/>`_. Although most modules are
already packaged, Debian lacks a package for the ``AnyEvent::MQTT`` module. You can build it by using *dh-make-perl*:

- install packages *libanyevent-perl* and *dh-make-perl* to build the missing Debian packages from CPAN modules
.. code-block:: console

    # apt-get install libanyevent-perl dh-make-perl

- build Net::MQTT required for AnyEvent::MQTT
.. code-block:: console

    $ cpan2deb Net::MQTT --version 1.163170

- install Net::MQTT
.. code-block:: console

    # dpkg -i libnet-mqtt-perl_1.163170_all.deb
 
- build AnyEvent::MQTT
.. code-block:: console

    $ cpan2deb AnyEvent::MQTT --depends libnet-mqtt-perl

- install AnyEvent::MQTT
.. code-block:: console

    # dpkg -i libanyevent-mqtt-perl_1.172121-1_all.deb


Installation
============

To install nag2mqtt on *Debian GNU/Linux* it is recommended to use the `prebuild package <https://github.com/DE-IBH/nag2mqtt/releases>`_:

.. code-block:: console

    # dpkg -i nag2mqtt_0.4_amd64.deb
    # apt-get install -f


For non-Debian systems you need to build nag2mqtt from the sources.



Configuration
=============

You need to configure the ``nag2mqtt.conf`` to fit your needs (Perl syntax):

.. code-block:: perl
    :caption: /etc/nag2mqtt/nag2mqtt.conf

    # Directory used by NEB plugin (neb2mqtt.so)
    #$conf{base_dir} = q(/run/nag2mqtt/publish);

    # MQTT topic used by nag2mqttd
    #$conf{base_topic} = q(nagios);

    # MQTT broker host
    #$mqtt_conf{host} = q(localhost);

    # MQTT last will topic
    #$mqtt_conf{will_topic} = q(nagios/hosts/).hostname;

    # MQTT client ID
    #$mqtt_conf{client_id} = q(nag2mqtt);

    # MQTT user name
    #$mqtt_conf{user_name} = 'foo';

    # MQTT password
    #$mqtt_conf{password} = 'secret';


    # DO NOT REMOVE
    1;
