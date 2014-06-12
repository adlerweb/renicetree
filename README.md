# renicetree

a simple shell script to recursivly alter the niceness of a process and its childs

## Prerequirements

renicetree depends on "usual" GNU-utils, namely renice, bash and the /proc filesystem.

## Disclaimer

This script was created using trail&error without real knowledge of bash - use at your own risk...

## Motivation

make menuconfig, make, crap - when starting a make i sometimes forget to nice it to keep my system responding. Of course i can change the niceness later on using renice but this affects only the specified process and childs created afterwards. Especially if you are using a jobmanager (-j#) many processes will stay at the old nice level.

This script will recursivly search for all child processes and issue a renice for them individually

## Usage

./renicetree Niceness PID [1]

Niceness - Level between -20 and 19
           Note: Only root may set negative values
PID      - Process ID of the parent
1        - (optional) only process direct childs
           no recursion

Example: ./renicetree -5 1234 1

## Authors
Florian Knodt <adlerweb@adlerweb.info>
