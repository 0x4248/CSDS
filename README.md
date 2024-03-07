# Computer System Diagnostics Standard

Computer System Diagnostics Standard (CSDS) is a standard for receiving diagnostic data from a computer system that is easy to read and write.

It is designed to be used to quickly send diagnostic data from a computer system to diagnostic software or diagnostic hardware. It is also designed to be complexly readable by any computer or human.

## File Structure

The diagnostics should be sent in zip format containing the following files:

- `diagmap.csv` - A csv file containing the diagnostic map (location,description)
- `meta.dat` - A config like file containing the meta data of the diagnostic data
- Other files - The actual diagnostic data

## `diagmap.csv`

This file shows what each file in the zip contains. It is a csv file with the following format:

```
location,description
example.txt,This is an example file
```

## `meta.dat`

This file contains the meta data of the diagnostic data. It is like a config like file with the following format:

```
## BASIC INFO

NAME = Computer
DATE = 1/1/1970
TIME = 12:00 AM GMT

## OS

OS = Linux
VERSION = 6.0
OTHER_VERSION = beta
```

Each `##` section is a section. Each `KEY = VALUE` is a key value pair. If there are just `#` then it is a comment.

## Other files

These are the actual diagnostic data. They can be any file type.

## License

This format is completely open source and free to use. You can use it for any purpose.
