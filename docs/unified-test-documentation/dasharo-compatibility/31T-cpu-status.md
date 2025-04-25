# Dasharo Compatibility: CPU Status

## Test cases common documentation

**Test setup**

1. Proceed with the
    [Generic test setup: firmware](../generic-test-setup.md#firmware).
1. Proceed with the
    [Generic test setup: OS installer](../generic-test-setup.md#os-installer).
1. Proceed with the
    [Generic test setup: OS installation](../generic-test-setup.md#os-installation).
1. Proceed with the
    [Generic test setup: OS boot from disk](../generic-test-setup.md#os-boot-from-disk).

## CPU001.0XX CPU works (Linux generic)

**Test description**

Check whether the mounted on the DUT CPU works.

**Test configuration data**

1. `FIRMWARE` = Dasharo
1. `OPERATING_SYSTEM` = _Linux-based_

**Test setup**

1. Proceed with the
    [Test cases common documentation](#test-cases-common-documentation) section.

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot and note the result.

**Expected result**

The `OPERATING_SYSTEM` screen should be displayed.

## CPU001.001 CPU works (Ubuntu)

Follows the generic CPU001.0XX Linux-based test case

## CPU001.002 CPU works (Windows)

**Test description**

Check whether the mounted on the DUT CPU works.

**Test configuration data**

1. `FIRMWARE` = Dasharo
1. `OPERATING_SYSTEM` = Windows

**Test setup**

1. Proceed with the
    [Test cases common documentation](#test-cases-common-documentation) section.

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot and note the result.

**Expected result**

The `OPERATING_SYSTEM` screen should be displayed.

## CPU001.010 CPU works (XCP-NG)

Follows the generic CPU001.0XX Linux-based test case

## CPU001.011 CPU works (ESXI)

Follows the generic CPU001.0XX Linux-based test case

## CPU002.0XX CPU cache enabled (Linux generic)

**Test description**

Check whether all declared for the DUT cache levels are enabled.

**Test configuration data**

1. `FIRMWARE` = Dasharo
1. `OPERATING_SYSTEM` = _Linux-based_

**Test setup**

1. Proceed with the
    [Test cases common documentation](#test-cases-common-documentation) section.

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot.
1. Execute below command in terminal:

    ```bash
    getconf -a | grep CACHE
    ```

1. Note the result.

**Expected result**

The output of the command should contain information about all cache levels,
their size and association. Example output:

```bash
LEVEL1_ICACHE_SIZE                 32768
LEVEL1_ICACHE_ASSOC                32
LEVEL1_ICACHE_LINESIZE             128
LEVEL1_DCACHE_SIZE                 32768
LEVEL1_DCACHE_ASSOC                32
LEVEL1_DCACHE_LINESIZE             128
LEVEL2_CACHE_SIZE                  524288
LEVEL2_CACHE_ASSOC                 2048
LEVEL2_CACHE_LINESIZE              32
LEVEL3_CACHE_SIZE                  10485760
LEVEL3_CACHE_ASSOC                 40960
LEVEL3_CACHE_LINESIZE              32
LEVEL4_CACHE_SIZE                  0
LEVEL4_CACHE_ASSOC                 0
LEVEL4_CACHE_LINESIZE              0
```

## CPU002.001 CPU cache enabled (Ubuntu)

Follows the generic CPU002.0XX Linux-based test case

## CPU002.002 CPU cache enabled (Windows)

**Test description**

Check whether all declared for the DUT cache levels are enabled.

**Test configuration data**

1. `FIRMWARE` = Dasharo
1. `OPERATING_SYSTEM` = Windows

**Test setup**

1. Proceed with the
    [Test cases common documentation](#test-cases-common-documentation) section.

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot.
1. Run PowerShell as an administrator and execute command:

    ```powershell
    Get-Wmiobject -class win32_cachememory | fl Purpose, CacheType, InstalledSize
    ```

1. Note the result.

**Expected result**

The output of the command should contain information about all cache levels,
their size and association. Example output:

```powershell
Purpose       : CACHE1
CacheType     : 4
InstalledSize : 192

Purpose       : CACHE1
CacheType     : 3
InstalledSize : 128

Purpose       : CACHE2
CacheType     : 5
InstalledSize : 5120

Purpose       : CACHE3
CacheType     : 5
InstalledSize : 8192
```

## CPU002.010 CPU cache enabled (XCP-NG)

Follows the generic CPU002.0XX Linux-based test case

## CPU002.011 CPU cache enabled (ESXI)

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot.
1. Execute below command in terminal:

```bash
esxcli hardware cpu list | grep Cache
```

1. Note the result.

**Expected result**

The output of the command should contain information about all cache levels,
their size and association. Example output:

```bash
L2 Cache Size: 2097152
L2 Cache Associativity: 16
L2 Cache Line Size: 64
L2 Cache CPU Count: 4
L3 Cache Size: 6291456
L3 Cache Associativity: 12
L3 Cache Line Size: 64
L3 Cache CPU Count: 4
```

## CPU003.0XX Multiple CPU support (Linux generic)

**Test description**

Check whether the DUT has multiple CPU support.

**Test configuration data**

1. `FIRMWARE` = Dasharo
1. `OPERATING_SYSTEM` = _Linux-based_

**Test setup**

1. Proceed with the
    [Test cases common documentation](#test-cases-common-documentation) section.

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot.
1. Execute below command in terminal:

    ```bash
    lscpu
    ```

1. Note the result.

**Expected result**

The output of the command should contain basic information about the CPU,
including the number of the `CPU (s)`. If `CPU(s)` are more than 1, the DUT
has multiple CPU support. Example results:

```bash
Architecture:                    ppc64le
Byte Order:                      Little Endian
CPU(s):                          32
On-line CPU(s) list:             0-31
Thread(s) per core:              4
Core(s) per socket:              4
Socket(s):                       2
NUMA node(s):                    2
```

## CPU003.001 Multiple CPU support (Ubuntu)

Follows the generic CPU003.0XX Linux-based test case

## CPU003.002 Multiple CPU support (Windows)

**Test description**

Check whether the DUT has multiple CPU support.

**Test configuration data**

1. `FIRMWARE` = Dasharo
1. `OPERATING_SYSTEM` = Windows

**Test setup**

1. Proceed with the
    [Test cases common documentation](#test-cases-common-documentation) section.

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot.
1. Run PowerShell as an administrator and execute command:

    ```powershell
    WMIC CPU Get NumberOfCores
    ```

1. Note the result.

**Expected result**

The output of the command should contain information about the CPUs.
Example results:

```powershell
NumberOfCores
4
```

## CPU003.010 Multiple CPU support (XCP-NG)

Follows the generic CPU003.0XX Linux-based test case

## CPU003.011 Multiple CPU support (ESXI)

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot.
1. Execute below command in terminal:

```bash
esxcli hardware cpu global get
```

1. Note the result.

**Expected result**

The output of the command should contain basic information about the CPU,
including the number of the `CPU Cores`. If it is greater than 1, the DUT
has multiple CPU support. Example results:

```bash
CPU Packages: 1
CPU Cores: 4
CPU Threads: 4
Hyperthreading Active: false
Hyperthreading Supported: false
Hyperthreading Enabled: true
HV Support: 3
```

## CPU004.0XX Multiple-core support (Linux generic)

**Test description**

Check whether the DUT has multi-core support.

**Test configuration data**

1. `FIRMWARE` = Dasharo
1. `OPERATING_SYSTEM` = _Linux-based_

**Test setup**

1. Proceed with the
    [Test cases common documentation](#test-cases-common-documentation) section.

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot.
1. Execute below command in terminal:

    ```bash
    lscpu
    ```

1. Note the result.

**Expected result**

The output of the command should contain basic information about the CPU,
including the number of the `Core(s) per socket`. If `Core(s) per socket`
are more than 1, the DUT has multi-core support. Example results:

```bash
Architecture:                    ppc64le
Byte Order:                      Little Endian
CPU(s):                          32
On-line CPU(s) list:             0-31
Thread(s) per core:              4
Core(s) per socket:              4
Socket(s):                       2
NUMA node(s):                    2
```

## CPU004.001 Multiple-core support (Ubuntu)

Follows the generic CPU004.0XX Linux-based test case

## CPU004.002 Multiple-core support (Windows)

**Test description**

Check whether the DUT has multi-core support.

**Test configuration data**

1. `FIRMWARE` = Dasharo
1. `OPERATING_SYSTEM` = Windows

**Test setup**

1. Proceed with the
    [Test cases common documentation](#test-cases-common-documentation) section.

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot.
1. Run PowerShell as an administrator and check total CPU cores by executing
command:

    ```powershell
    WMIC CPU Get NumberOfCores
    ```

1. Note the result.
1. Check total CPU socket number by executing command:

    ```powershell
    (Get-CimInstance -ClassName Win32_ComputerSystem).NumberOfProcessors
    ```

1. Note the result.

**Expected result**

1. If number of cores is higher than number of sockets then DUT has multi-core
support. Example outputs:

- 1st command:

```powershell
NumberOfCores
4
```

- 2nd command:

```powershell
1
```

## CPU004.010 Multiple-core support (XCP-NG)

Follows the generic CPU004.0XX Linux-based test case

## CPU004.011 Multiple-core support (ESXI)

**Test steps**

1. Power on the DUT.
1. Wait for the `OPERATING_SYSTEM` to boot.
1. Execute below command in terminal:

```bash
esxcli hardware cpu list | grep Id
```

1. Note the result.

**Expected result**

The output of the command will show a list of CPU cores on the system
along with the `Package Id:` This designates the socket to which the
core belongs.If the number of cores with the same `Package Id:`
is more than 1, the DUT has multi-core support. Example results:

```bash
Id: 0
Package Id: 0
Id: 1
Package Id: 0
Id: 2
Package Id: 0
Id: 3
Package Id: 0
```
