# Connected doorbell demo FreeRTOS ESPEYE Tensorflow
afr_demo_module(connected_doorbell)

# Set the default demo that is enabled in the downloaded package.
afr_set_demo_metadata(ID "CONNECTED_DOORBELL_DEMO")
afr_set_demo_metadata(DESCRIPTION "Examples that demonstrate a simple connected doorbell example based on FreeRTOS, Tensorflow Lite on ESPEYE and connected to AWS IoT")
afr_set_demo_metadata(DISPLAY_NAME "connected_doorbell Demos")

# Add the CMakeLists.txt file of module to metadata list.
afr_module_cmake_files(${AFR_CURRENT_MODULE} 
    ${CMAKE_CURRENT_LIST_DIR}/CMakeLists.txt
)

afr_module_sources(
    ${AFR_CURRENT_MODULE}
    INTERFACE
        "${CMAKE_CURRENT_LIST_DIR}/connected_doorbell_demo.c"
)

afr_module_dependencies(
    ${AFR_CURRENT_MODULE}
    INTERFACE
        AFR::core_mqtt
        AFR::backoff_algorithm
        AFR::transport_interface_secure_sockets
        AFR::secure_sockets
        AFR::pkcs11_helpers
        # Add dependency on the core_mqtt_demo_dependencies metadata module 
        # so that FreeRTOS console shows this demo ONLY when the core MQTT library
        # (or another library depending on coreMQTT) is selected on the console.
        AFR::core_mqtt_demo_dependencies
)
