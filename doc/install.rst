************
Installation
************


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
