# SPDX-License-Identifier: Apache-2.0

add_subdirectory(utils)
add_subdirectory_if_kconfig(coap)
add_subdirectory_if_kconfig(lwm2m)
add_subdirectory_if_kconfig(socks)
add_subdirectory_if_kconfig(sntp)
add_subdirectory_ifdef(CONFIG_MQTT_LIB          mqtt)
add_subdirectory_ifdef(CONFIG_NET_CONFIG_SETTINGS config)
add_subdirectory_ifdef(CONFIG_NET_SOCKETS       sockets)
add_subdirectory_ifdef(CONFIG_TLS_CREDENTIALS   tls_credentials)

if (CONFIG_DNS_RESOLVER
    OR CONFIG_MDNS_RESPONDER
    OR CONFIG_LLMNR_RESPONDER)
  add_subdirectory(dns)
endif()

if(CONFIG_HTTP_PARSER_URL
    OR CONFIG_HTTP_PARSER)
  add_subdirectory(http)
endif()

add_subdirectory_ifdef(CONFIG_OPENTHREAD_PLAT openthread)
