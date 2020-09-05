# dkms-hid-nintendo

A Nintendo HID kernel module.


## Installation

Install it from source with:

```
git clone https://github.com/nicman23/dkms-hid-nintendo
cd dkms-hid-nintendo

sudo dkms add .
sudo dkms build nintendo -v 3.0
sudo dkms install nintendo -v 3.0
```


## Related projects

- [joycond](https://github.com/DanielOgorchock/joycond): A userspace daemon to
  combine joy-cons from the hid-nintendo kernel driver
- [joycond-cemuhook](https://github.com/joaorb64/joycond-cemuhook): Support for
  cemuhook's UDP protocol for joycond devices
