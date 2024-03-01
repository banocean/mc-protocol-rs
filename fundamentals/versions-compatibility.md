# Versions compatibility

### Struct-based Representation
- Each packet will be represented by a specific struct, containing all its relevant data fields.
- If a packet structure remains consistent across versions, use the earliest defined struct for serialization and deserialization.
- Packets duplicated across versions will use a `type` definition to reference the original definition.
- Serialization and deserialization outputs can differ between versions as long as the underlying data remains compatible.
### Version-Specific Changes:
- Packets with compatible same fields across versions will utilize traits with implementing versions providing the necessary data.
- Packets with values that have data format changes but same functionality will utilize traits returning enums representing the various data types across versions.
### Unified Representation:
- Data evolving over versions, like blocks, will have implementations holding all possible data variations, allowing seamless serialization and deserialization regardless of the originating version (it shouldn't allow serialization for versions not supporting it, but could provide additional method that wraps over it and provides something replacing it).
- Users have the option to convert packets with substantial unified data into structures containing these fields, employing unified structures (from previous point) and enums for representing format changes while preserving functionality.

TODO: defining packets for multiple versions at once
