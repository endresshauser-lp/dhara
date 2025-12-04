if(CONFIG_DISK_DRIVER_FTL)
  zephyr_include_directories(${ZEPHYR_DHARA_MODULE_DIR}/zephyr/include/)

  file(GLOB dhara_sources ${ZEPHYR_DHARA_MODULE_DIR}/dhara/*.c)

  zephyr_library()
  zephyr_library_sources(
    ${ZEPHYR_DHARA_MODULE_DIR}/zephyr/drivers/disk/ftl_dhara.c
    ${dhara_sources}
  )
endif()
