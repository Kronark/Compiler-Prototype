<!--
Notes:
- all positions are single precision floating point
- all widths and heights are single precision floating point
- N denoted variable byte integers, where fully set bytes (i.e. 11111111) signal an additional byte to be read, byte ordering is little endian
 -->

# Header

- `kronarknode` magic number [11]
- version number [1]

# Roots

- root positions:
    - input root position x [4]
    - input root position y [4]
    - output root position x [4]
    - output root position y [4]
- output root connection count [N]
- output root connections:
    - connection node [N]
    - connection socket [N]

# Nodes

- table size [N]
- table items:
    - node name length [N]
    - node name [string]

# Types

- table size [N]
- table items:
    - type name length [N]
    - type name [string]

# Instances

- instance count [N]
- instances:
    - instance key [N]
    - instance type [N]
    - instance position:
        - instance position x [4]
        - instance position y [4]
    - instance width [4]
    - instance name length [1]
    - instance name [string]
    - instance socket count [N]
    - instance sockets:
        - socket flags [1]:
            - PADDING [2 bit]
            - type and direction [3 bits]:
                - 000 = outgoing named
                - 001 = incoming named
                - 010 = incoming number
                - 011 = incoming select
                - 100 = incoming switch
                - 101 = incoming text
            - repetitive [1 bit]
            - connected [1 bit]
            - switch value [1 bit]
        - socket type index [N]
        - socket port slot [N]
        - if incoming:
            - if connected:
                - connection node [1]
                - connection socket [1]
            - if not connected and not switch:
                - value length [N]
                - value [string]

# Groups

- group count [N]
- groups:
    - group dimensions:
        - group width [4]
        - group height [4]
    - group position:
        - group position x [4]
        - group position y [4]
    - group colour [3]
    - group name length [N]
    - group name [string]
    - group item count [N]
    - group items:
        - item key [N]

# Comments

- comment count [N]
- comments:
    - comment dimensions:
        - comment width [4]
        - comment height [4]
    - comment position:
        - comment position x [4]
        - comment position y [4]
    - comment colour [3]
    - comment length [N]
    - comment [string]
