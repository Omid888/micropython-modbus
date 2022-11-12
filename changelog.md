# Changelog
All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

<!--
## [x.y.z] - yyyy-mm-dd
### Added
### Changed
### Removed
### Fixed
-->

<!-- ## [Unreleased] -->

## Released
## [1.1.1] - 2022-11-09
### Fixed
- Default value of `setup_registers` function parameter `use_default_vals`
  changed to `False` to avoid confusion behaviour if not explicitly defined,
  see [issue 13][ref-issue-13]
- Missing function docstring added to `setup_registers` function
- `write_single_coil` allows `0`, `1`, `False`, `True`, `0x0` or `0xFF00`
  instead of `0x0` and `0xFF00` only as set value, see [issue 14][ref-issue-14]

## [1.1.0] - 2022-11-03
### Added
- `float_to_bin`, `bin_to_float`, `int_to_bin` functions added to
  [`umodbus/functions.py`](umodbus/functions.py)
- Deploy to [Test Python Package Index](https://test.pypi.org/) on every PR
  build with a [PEP440][ref-pep440] compliant `-rc<BUILDNUMBER>.dev<PR_NUMBER>`
  meta data extension
- [Test release workflow](.github/workflows/test-release.yaml) running only on
  PRs is archiving and uploading built artifacts to
  [Test Python Package Index](https://test.pypi.org/)

### Changed
- Author is explicitly mentioned in [`setup.py`](setup.py) instead of used by
  `__author__` variable which has been previously defined in
  [`version.py`](umodbus/version.py) but no longer available with autodeploy.

### Fixed
- All uncovered flake8 warnings of [`umodbus`](umodbus)

## [1.0.0] - 2022-02-26
### Added
- [`setup.py`](setup.py) and [`sdist_upip.py`](sdist_upip.py) taken from
  [pfalcon's picoweb repo][ref-pfalcon-picoweb-sdist-upip] and PEP8 improved
- [`MIT License`](LICENSE)
- [`version.py`](umodbus/version.py) storing current library version
- [`typing.py`](umodbus/typing.py) enabling type hints

### Changed
- Moved all uModbus files from `lib/uModbus` into [`umodbus`](umodbus)
- Update import statements of all files of [`umodbus`](umodbus)
- Update [`README`](README.md) usage description of MicroPython lib deploy to
  [PyPi][ref-pypi]
- Usage examples in [`README`](README.md) updated with new import path
- Update [`boot`](boot.py) and [`main`](main.py) files to use `be_helpers`
- Enable setting of `max_connections` to TCP socket in
  [`modbus ModbusTCP bind function`](umodbus/modbus.py) and [`tcp TCPServer bind function`](umodbus/tcp.py)

### Removed
- MicroPython helpers module no longer used
- MicroPython ESP WiFi Manager module no longer used
- Lib folder of dependency modules no longer used
- Commented print debug messages in several files of umodbus

## [0.1.0] - 2022-02-20
### Added
- This changelog file
- [`.gitignore`](.gitignore) file
- [`requirements.txt`](requirements.txt) file to setup tools for board
  interactions
- Creation header to all files of [`lib/uModbus`](lib/uModbus) in order to
  provide proper credits to [Pycom](https://www.pycom.io)
- `get_is_bound()` function added to [`lib/uModbus/tcp.py`](lib/uModbus/tcp.py)
  to check status of socket binding for the Modbus TCP Server (host)
- [Example register files](registers) to show basic usage with a MyEVSE board

### Changed
- Reworked [`boot.py`](boot.py) and [`main.py`](main.py) for simple usage
- [`README`](README.md) file with usage examples
- Replaced WiPy specific calls in [`lib/uModbus`](lib/uModbus) files with
  MicroPython 1.16 or higher calls
- Limit number of concurrent socket connections to the Modbus TCP Server (host)
  to 10
- Return on `_accept_request()` in case of an `OSError` as MicroPython raises
  this type of error in case a socket timeout occured. `TimeoutError` is not
  available on MicroPython compared to WiPy

### Fixed
- PEP8 style issues on all files of [`lib/uModbus`](lib/uModbus)

<!-- Links -->
[Unreleased]: https://github.com/brainelectronics/micropython-modbus/compare/1.1.1...develop

[1.1.1]: https://github.com/brainelectronics/micropython-modbus/tree/1.1.1
[1.1.0]: https://github.com/brainelectronics/micropython-modbus/tree/1.1.0
[1.0.0]: https://github.com/brainelectronics/micropython-modbus/tree/1.0.0
[0.1.0]: https://github.com/brainelectronics/micropython-modbus/tree/0.1.0

[ref-issue-13]: https://github.com/brainelectronics/micropython-modbus/issues/13
[ref-issue-14]: https://github.com/brainelectronics/micropython-modbus/issues/14
[ref-pep440]: https://peps.python.org/pep-0440/
[ref-pypi]: https://pypi.org/
[ref-pfalcon-picoweb-sdist-upip]: https://github.com/pfalcon/picoweb/blob/b74428ebdde97ed1795338c13a3bdf05d71366a0/sdist_upip.py
[ref-be-micropython-module]: https://github.com/brainelectronics/micropython-modules/tree/1.1.0