*****
About
*****

nag2mqtt consists of a *Nagios Event Broker* (NEB) module and a small perl daemon. The NEB module
publishes all check results in the local filesystem (using tmpfs is highly recommended).
These file are than publish by the perl daemon to a MQTT broker.

By publishing the check results via MQTT it is possible to visualize the Nagios check states and performance data
in `SNMD <http://snmd.readthedocs.io/projects/snmd/en/latest/>`_ using the `snmd-widgets-nagios <http://snmd.readthedocs.io/projects/snmd-widgets-nagios/en/latest/>`_ widgets.


.. include:: ../AUTHORS.rst


Copyright
=========

* 2016 - 2017 (C) Thomas Liske [https://fiasko-nw.net/~thomas/]


License
=======

This program is free software; you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation; either version 2 of the License, or
(at your option) any later version.
  
This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.
  
You should have received a copy of the GNU General Public License
along with this package; if not, write to the Free Software
Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301 USA
