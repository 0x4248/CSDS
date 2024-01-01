# Computer System Diagnostics Standard

Onboard Diagnostics Standard (CSDS) is a standard for receiving diagnostic data from a computer system.

It is designed to be used to quickly send diagnostic data from a computer system to diagnostic software or diagnostic hardware.

## Key parts

When a computer sends diagnostic data, it can send it trough a serial port, or save it to a file. The data is send in a hex format and has special characters to indicate different parts of the data.

### Magic number

The magic number is the first 4 bytes of the data. It is used to identify the data as CSDS data. The magic number is `43534453` in hex, or `CSDS` in ASCII.

### Version

The next 2 bytes are the version of the CSDS standard. A example version is `0100` in hex, this equates to version `1.0`.

### Metadata

The meta data section starts with `4d455441` in hex, or `META` in ASCII. Then the metadata starts with a key then value pair. Each key is 4 bytes long and each value is in plain text. Each value is terminated with a `00` in hex.

#### Metadata key mappings

|     Key    |                 Value                  |
| ---------- | -------------------------------------- |
| `00000001` | `Computer Name`                        |
| `00000002` | `Computer Manufacturer`                |
| `00000003` | `Computer Model`                       |
| `00000004` | `Computer Serial Number`               |
| `00000005` | `Computer System Version`              |
| `00000006` | `Architecture`                         |
| `00000008` | `Diagnostic date`                      |
| `00000009` | `Diagnostic time`                      | 
| `0000000A` | `CPU`                                  |
| `0000000B` | `CPU Cores`                            |
| `0000000C` | `CPU Threads`                          |
| `0000000D` | `CPU Clock Speed`                      |
| `0000000E` | `CPU Architecture`                     |
| `0000000F` | `CPU Cache`                            |
| `00000010` | `CPU Vendor`                           |
| `00000011` | `CPU Custom Data` (Ends at `0000001F`) |
| `00000020` | `GPU`                                  |
| `00000021` | `GPU Vendor`                           |
| `00000022` | `GPU Memory`                           |
| `00000023` | `GPU Clock Speed`                      |
| `00000024` | `GPU Custom Data` (Ends at `0000002F`) |
| `00000030` | `RAM`                                  |
| `00000031` | `RAM Vendor`                           |
| `00000032` | `RAM Speed`                            |
| `00000033` | `RAM Size`                             |
| `00000034` | `RAM Custom Data` (Ends at `0000003F`) |
| `00000040` | `Motherboard`                          |
| `00000041` | `Motherboard Vendor`                   |
| `00000042` | `Motherboard Model`                    |
| `00000043` | `Motherboard Serial Number`            |
| `00000044` | `Motherboard Custom Data` (Ends at `0000004F`) |
| `00000050` | `Custom Hardware data` (Ends at `000000FF`) |
| `00000100` | `OS`                                   |
| `00000101` | `OS Name`                              |
| `00000102` | `OS Version`                           |
| `00000103` | `OS Build`                             |
| `00000104` | `OS Architecture`                      |
| `00000105` | `OS Parameters`                        |
| `00000106` | `OS Uptime`                            |
| `00000107` | `OS Custom Data` (Ends at `0000010F`)  |
| `00000110` | `BIOS`                                 |
| `00000111` | `BIOS Vendor`                          |
| `00000112` | `BIOS Version`                         |
| `00000113` | `BIOS Date`                            |
| `00000114` | `BIOS Custom Data` (Ends at `0000011F`) |
| `00000120` | `Custom Software data` (Ends at `000002FF`) |
| `00000300` | `Network`                              |
| `00000301` | `Network Name`                         |
| `00000302` | `Network IP`                           |
| `00000303` | `Network MAC`                          |
| `00000304` | `Host Name`                            |
| `00000305` | `Adapter Name`                         |
| `00000306` | `Adapter Type`                         |
| `00000307` | `Adapter Speed`                        |
| `00000308` | `Adapter Status`                       |
| `00000309` | `Adapter Custom Data` (Ends at `0000030F`) |
| `00000310` | `Custom Network data` (Ends at `000003FF`) |
| `00000400` | `Custom Hardware data` (Ends at `000004FF`) |
| `00000500` | `Custom Software data` (Ends at `000005FF`) |
| `00000600` | `Custom Data` (Ends at `0000FFFF`)     |

### Custom Metadata Mapping

After the metadata section, there is a section that is used for mapping the custom metadata keys to values. The section starts with `4d415050` in hex, or `MAPP` in ASCII. Then the mapping starts with a key then value key name pair. 

This allows the software to read the custom metadata keys and values.

### Data

After that there is a section that is used for the zipped diagnostic data. This can include anything from text files or entire disk dumps. The section starts with `44415441` in hex, or `DATA` in ASCII. 

### End
There is no end to the file the file ends when the data ends.

## Licence

This project has no licence and is free to use in any way for diagnostic purposes.