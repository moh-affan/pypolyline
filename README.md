[![Build Status](https://travis-ci.org/urschrei/pypolyline.svg?branch=master)](https://travis-ci.org/urschrei/pypolyline) [![Build status](https://ci.appveyor.com/api/projects/status/0n7d5iwb3uqhsos6/branch/master?svg=true)](https://ci.appveyor.com/project/urschrei/pypolyline/branch/master)

# Fast Google Polyline Encoding and Decoding

## Installation
`pip install pypolyline`  
Please use a recent (>= 8.1.2) version of `pip`.

### Supported Python Versions
Python 2.7
Python 3.5

### Supported Platforms
- Linux (manylinux1-compatible)  
- OS X
- Windows 32-bit / 64-bit 

## Usage
```python
from pypolyline.util import encode_coordinates, decode_polyline

coords = [
            [52.64125, 23.70162],
            [52.64938, 23.70154],
            [52.64957, 23.68546],
            [52.64122, 23.68549],
            [52.64125, 23.70162]
            ]

# precision is 5 for Google Polyline, 6 for OSRM / Valhalla
polyline = encode_coordinates(coords, 5)
# polyline is 'ynh`IcftoCyq@Ne@ncBds@EEycB'
decoded_coords = decode_polyline(polyline, 5)
```

Attempts to decode an invalid Polyline will return `[[NaN, NaN]]`  
Attempts to encode invalid coordinates will return `Couldn't decode Polyline`

## How it Works
FFI using `ctypes` and a [Rust binary](https://github.com/urschrei/polyline-ffi)

## License
[MIT](license.txt)
