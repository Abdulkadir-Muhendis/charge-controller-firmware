# MPPT Charger Software

Software based on ARM mbed framework for the LibreSolar MPPT solar charge controllers

**Remark:** See also development branch for more recent updates.

## Supported devices

The software is configurable to support different charge controller PCBs with either STM32F072 (including CAN support) or low-power STM32L072/3 MCUs.

- [Libre Solar MPPT 20A (v0.10)](https://github.com/LibreSolar/MPPT-Charger_20A)
- [Libre Solar MPPT 12A (v0.5)](https://github.com/LibreSolar/MPPT-Charger_20A/tree/legacy-12A-version)
- [Libre Solar / CloudSolar MPPT 10A (v0.2 and v0.4)](https://github.com/LibreSolar/MPPT-Charger_10A)

## Toolchain and flashing instructions

See the Libre Solar website for a detailed instruction how to [develop software](http://libre.solar/docs/toolchain/) and [flash new firmware](http://libre.solar/docs/flashing/).

**Remark:** The 10A charge controller with STM32L0 often needs several attempts until the software is flashed with OpenOCD (integrated in PlatformIO). The ST-Link tools seem to be better for this MCU. For Windows there is a GUI tool. Under Linux use following command:

    st-flash write .pioenvs/cloudsolar_0_4/firmware.bin 0x08000000


## Initial software setup (IMPORTANT!)

1. Select the correct board in `platformio.ini` by removing the comment before the board name under [platformio]
2. Copy `config.h_template` to `config.h` and adjust basic settings (`config.h` is ignored by git, so your changes are kept after software updates using `git pull`)
3. (optional) To perform more advanced battery settings, copy `config.cpp_template` to `config.cpp` and change according to your needs. (also `config.cpp` is excluded from git versioning)

## Additional firmware documentation (docs folder)

- [MPPT charger firmware details](docs/firmware.md)
- [Charger state machine](docs/charger.md)
