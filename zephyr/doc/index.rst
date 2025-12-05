Dhara Zephyr Module
===================

This module integrates the Dhara flash translation layer (FTL) into the Zephyr
RTOS as a disk driver. It allows the use of Dhara to manage NAND flash memory
devices, providing wear leveling and bad block management. It sits between a
filesystem and a flash driver and makes a logical-to-physical memory mapping.

The FTL driver exposes a disk access API to the filesystem, allowing standard
file operations to be performed. It uses the standard flash API for reading,
writing, and erasing data, and the extended operations for bad block
management.

Following devicetree snippet shows an example integraton:

.. code-block:: devicetree

    ftl {
        compatible = "zephyr,ftl-dhara";
        partition = <&nand_partition>;
        disk-name = "NAND";
        buffer-size = <DT_SIZE_K(2)>;
        gc-ratio = <15>;
    };

The implementation details of Dhara are documented in the
`official repository documentation`_. That is also where the license details
can be found.

Maintainer
**********
This module is maintained by Endress+Hauser GmbH+Co. KG.

Limitations
***********

- ECC is not yet supported as the example NAND flash provided on-die ECC.
- An additional health monitoring API is not yet implemented.

.. _`official repository documentation`:
   https://github.com/dlbeer/dhara/blob/master/README
