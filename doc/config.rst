*************
Configuration
*************


NEB Plugin
==========


nag2mqttd
=========

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
