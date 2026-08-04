
[![Arduino CI](https://github.com/RobTillaart/MLX90316/workflows/Arduino%20CI/badge.svg)](https://github.com/marketplace/actions/arduino_ci)
[![Arduino-lint](https://github.com/RobTillaart/MLX90316/actions/workflows/arduino-lint.yml/badge.svg)](https://github.com/RobTillaart/MLX90316/actions/workflows/arduino-lint.yml)
[![JSON check](https://github.com/RobTillaart/MLX90316/actions/workflows/jsoncheck.yml/badge.svg)](https://github.com/RobTillaart/MLX90316/actions/workflows/jsoncheck.yml)
[![GitHub issues](https://img.shields.io/github/issues/RobTillaart/MLX90316.svg)](https://github.com/RobTillaart/MLX90316/issues)

[![License: MIT](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/RobTillaart/MLX90316/blob/master/LICENSE)
[![GitHub release](https://img.shields.io/github/release/RobTillaart/MLX90316.svg?maxAge=3600)](https://github.com/RobTillaart/MLX90316/releases)
[![PlatformIO Registry](https://badges.registry.platformio.org/packages/robtillaart/library/MLX90316.svg)](https://registry.platformio.org/libraries/robtillaart/MLX90316)


# MLX90316

Arduino library for SPI based MLX90316 rotary encoder.


## Description

**Experimental**

**Warning:** This library is not tested with hardware yet.
So use with care, feedback welcome.

MLX90316 is a library for the **MLX90316** rotation encoder.
This devices decodes 360.0° in 16384 steps which implies an accuracy
of about 0.022°.


The MLX90316 is capable of much more, this might be implemented in a later
version of the library.

The angle is calculated every 200 μs, so 5000 times per second.

TODO CHECK details.

As the device can handle up to 800 rpm = 75 milliseconds per rotation.
To have a fair indication of rpm and direction one has to sample
4 times so roughly once every 20 ms.

Feedback as always, is welcome. Please open an issue.


_library is based upon ERCFS library, so some artefacts may exist_


### Hardware

TODO:


### Related

Angle math

- https://github.com/RobTillaart/Angle
- https://github.com/RobTillaart/AngleConvertor
- https://github.com/RobTillaart/AverageAngle
- https://github.com/RobTillaart/runningAngle

Decoders

- https://github.com/RobTillaart/AMT25
- https://github.com/RobTillaart/AS5600 magnetic rotation meter.
- https://github.com/RobTillaart/ERCFS rotation decoder (bit similar)
- https://github.com/RobTillaart/MLX90316 this library
- https://p3america.com/ercf-1-05spi-360-z/ home of ERCFS datasheet.

Related rotary decoder libraries

- https://github.com/RobTillaart/rotaryDecoder
- https://github.com/RobTillaart/rotaryDecoderSwitch
- https://github.com/RobTillaart/rotaryDecoder8
- https://github.com/RobTillaart/rotaryDecoderSwitch5


### Tested

TODO:

### Please report your experiences.

If you have a MLX90316 device, please let me know your experiences
with the sensor and this (or other) library.


## Interface

```cpp
#include "MLX90316.h"
```

### Constructor

- **MLX90316(uint8_t select, __SPI_CLASS__ \* mySPI = &SPI)** HARDWARE SPI
- **MLX90316(uint8_t select, uint8_t dataIn, uint8_t dataOut, uint8_t clock)** SOFTWARE SPI
- **bool begin()** initializes the communication.


### Read

- **uint16_t getRawValue()** returns a value from 0..16383
- **float getAngle()** returns an absolute angle from 0..360.0°, optional
with offset correction.
- **void setOffset(float offset = 0)** set an offset in degrees for the angle.
- **float getOffset()** returns the current offset in degrees.
- **uint32_t lastRead()** timestamp in microseconds since start.
Note this wraps every ~70 minutes however for RPM measurements one
need to read the device far more often.


### SPI

- **void setSPIspeed(uint32_t speed)** idem, clipped to max 2 MHz.
- **uint32_t getSPIspeed()** idem.
- **bool usesHWSPI()** idem.


### Debug

- **uint16_t getStatus()** return last status bytes.

TODO explain bits.


## Future

#### Must

- improve documentation
- get hardware to test

#### Should

- improve error handling

#### Could

- add examples
- add unit tests (if possible)

#### Wont


## Support

If you appreciate my libraries, you can support the development and maintenance.
Improve the quality of the libraries by providing issues and Pull Requests, or
donate through PayPal or GitHub sponsors.

Thank you,


