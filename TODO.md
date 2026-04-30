# Fixes TODO
- update PSC files including util.py and exec_anaconda.py
  - https://github.com/splunk/Splunk-python-for-scientific-computing/blob/main/package/bin/exec_anaconda.py
  - https://github.com/splunk/Splunk-python-for-scientific-computing/blob/main/package/bin/util.py
- add regex lib to bin/
  - Last Python 3.9 supported version: https://pypi.org/project/regex/2026.1.15/

# Anaconda Python Runtime
Python for Scientific Computing (for Linux 64-bit) 
- For version 4.3.1 of the Splunk app
- https://splunkbase.splunk.com/app/2882
- Bundles CPython 3.13.11

## Analysis from Claude:
Based on the binary analysis, this Python binary would be supported on:

Key Requirements:
- Architecture: x86-64 (64-bit Intel/AMD processors)
- Minimum kernel: Linux 2.6.32 or newer
- Minimum glibc: 2.17 (the highest version referenced)

Compatible Linux Distributions:

This binary should work on most modern x86_64 Linux distributions from around 2013 onwards, including:

- RHEL/CentOS/Rocky/Alma: 7.0+ (glibc 2.17)
- Ubuntu: 13.04+ (glibc 2.17+)
- Debian: 8 (Jessie) and newer
- Fedora: 18+
- SUSE/openSUSE: SLES 12+, openSUSE 12.3+
- Amazon Linux: 2 and newer
- Oracle Linux: 7+

Will NOT work on:
- 32-bit x86 systems
- ARM, PowerPC, or other non-x86_64 architectures
- Older distributions with glibc < 2.17 (e.g., RHEL/CentOS 6, Ubuntu 12.04)

The binary is dynamically linked, so the target system must have compatible shared libraries installed, but this is standard for most modern Linux distributions.

## Supported Wheels
Compatible Wheel Tags

  Based on the extension module naming (cpython-313-x86_64-linux-gnu.so), compatible wheels would have these tags:

  Primary compatibility (most specific to least):

  1. cp313-cp313-manylinux_2_17_x86_64 - CPython 3.13, manylinux2014 (glibc 2.17+)
  2. cp313-cp313-manylinux2014_x86_64 - Alternative name for manylinux_2_17
  3. cp313-cp313-manylinux_2_12_x86_64 - manylinux2010 (glibc 2.12+)
  4. cp313-cp313-manylinux_2_5_x86_64 - manylinux1 (glibc 2.5+)
  5. cp313-cp313-linux_x86_64 - Generic Linux x86_64
  6. cp313-abi3-manylinux_2_17_x86_64 - Stable ABI wheels (if available for 3.13+)
  7. py313-none-any - Pure Python, 3.13 specific
  8. py3-none-any - Pure Python, any Python 3
  9. py2.py3-none-any - Universal pure Python

  Key Points:

  - cp313 = CPython 3.13
  - manylinux_2_17 is the best fit given the glibc 2.17 requirement
  - Pure Python wheels (py3-none-any) will always work
  - Wheels built for older Python 3.x versions won't work with 3.13
  - Stable ABI wheels (abi3) built for 3.13 or earlier would be compatible

  The most common wheels you'll find are cp313-cp313-manylinux_2_17_x86_64 for packages with C extensions and py3-none-any for pure Python packages.