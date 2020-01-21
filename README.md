# SafeKey Testing tools
most of these features are going to be included in further releases of SafeKey Desktop.

# SafeKey Tool installation

```
pip3 uninstall solo-python -y  
pip3 uninstall safekey-python -y
pip3 install ./safekey_python-1.0.0-py3-none-any.whl --user
```

activation.pem (is a key generated and owned by saetech)


# CS-Activation

Activation feature allows to enable or disable Custom Storage (CS) commands on the given custom FIDO2 device. It is based on the Elliptic Curve Cryptography (ECC), with set of operations based on public and private keys.

By default CS commands are disabled, and device returns error code on attempt of their execution.

Activation could be performed locally, with a potential extension to remote work (without firmware change). No one besides the person in the possession of the key can perform the procedure. The received activation signature is restricted to the given device, and valid for only a single request, due to the use of MCU’s serial number, and a randomly device-generated transaction token. Data received from the device allow to identify it, and track the activation status on the server.


## to get device activation status
safekey activation status `activation.pem`

## to activate device, to support Custom Storage features 
safekey activation activate `activation.pem`

## to deactivate device, so it would be limited to SAfeKey FIDO2 features only 
safekey activation deactivate `activation.pem`

## Custom Storage tests

This repository contains tests for the Custom Storage features, which are part of the SafeKey firmware.

## Test list

- `test_activation.py` - unit tests for the Activation feature; 
- `test_comm.py` - general suite for the low-level communication, read and write of the data on the device; 
- `test_cs_unlock.py` - tests for the Unlock Passphrase feature;
- `test_pin_management.py` - test suite for the PIN handling, and the connection between FIDO2 and Custom Storage PIN counter;
- `test_fido2.py` - brief FIDO2 tests;

## Setup

To run the tests, a `pytest` package has to be installed beforehand, as well as all requirements for the `safekey-tool`. Please run the tests in the same environment, as the tool is installed. For user-scope installation:

```shell script
pip3 install pytest -y
``` 

## Running

```shell script
pytest -xv test_comm.py 
```

# Other
To blink the connected device, execute:
```shell script
safekey key wink
```

For touch button status:
```shell script
safekey key status
```

Copyright 2019 SoloKeys Developers
Copyright 2020 SAfeTech BVBA
Licensed under the Apache License, Version 2.0, <LICENSE-APACHE or
http://apache.org/licenses/LICENSE-2.0> or the MIT license <LICENSE-MIT or
http://opensource.org/licenses/MIT>, at your option. This file may not be
copied, modified, or distributed except according to those terms.

