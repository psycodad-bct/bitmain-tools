# Antminer L3+[+] autotuner for DAC voltage: l3plus_autotune.py

This python 2 script builds upon [jstefanops great work](https://bitcointalk.org/index.php?topic=3546316) and makes the process of voltage-tuning your L3+ miners easy and straightforward.

The right voltage level for your hash boards depends on many external and internal factors like board quality, frequency, ambient temperature etc.
Apparently it can become necessary to re-tune your miners once you changed frequency or i.e. ambient temperatures shifted by some degrees (i.e. winter/summer).

Since finding the best 8-bit value for each hash board everytime some factor changes is a time consuming affair, this script helps you automate the process massively.


While this script bases off the work of jstefanop, it does not use his *set_voltage* binary and you do not need anything installed on your Antminer L3+ to use it.


## Install
Just clone this repo, change into the scripts directory and you should be ready to go.
The script requires the paramiko Python module, on a Debian based distro just do:

`sudo apt-get install python-paramiko`

## Usage

```
Usage:
./l3plus_autotune.py -i <ip>|--minerip=<ip> [OPTIONS]

Options:
 -p <adminpass>                 admin password if not set to 'admin'
 --password=<adminpass>
 -s <chain1[,chain2]>           skip one or more chains
 --skip <chain1[,chain2]>

Examples:
Tune miner on 10.10.10.33, use '1234' as admin password and skip tuning chain 2 and 3:
./l3plus_autotune.py -i 10.10.10.33 -p 1234 --skip 2,3
Default usage :
./l3plus_autotune.py -i 10.10.10.33
```

The script will take anywhere from 30min to several hours to complete, it may also decide that it is unable to tune your miner completely. 

Once it has finished it will output a report and also write that report to a file.

## Disclaimer
This software/script has alpha-quality or less and comes as-is with no warranties at all. 
I have tested it heavily and to the best of my knowledge it should do no harm, but it has the potential to damage your miner and even if not it will probably void your Bitmain warranty.

Use completely at your own risk!
