# Affected Version
Bento4 Version 1.6.0-641

# Vulnerability Description
Floating point exception (divide-by-zero) issues was discovered in Bento4 

# Bento4 download address
https://github.com/axiomatic-systems/Bento4

# Floating Point Exception (divide-by-zero) issue in functon AP4_TfraAtom4() of Ap4TfraAtom.cpp
*mp4dump* uses *\_tfra* to identify TFRA atoms in MP4 files and reads the number of entries (*entry\_count*) contained in TFRA atoms from a specific four bytes. *entry\_count* is used as a divisor when verifying that the average size of the entries meets the requirements. Nevertheless, *entry\_count* is calculated by the *ReadUI32()* function in *Ap4ByteStream.cpp* and is not judged to be zero. As a result, an FPE vulnerability is triggered when 4 bytes of *entry\_count* are recorded as zero.

<img src="https://github.com/JWH-96/Bugs-disclosure/blob/main/Fig.png" width="600px">

# Verification Process
1. Build Bneto4
2. Execute ./mp4dump path_to/id_000000.mp4 <br>
   https://github.com/JWH-96/Bugs-disclosure/blob/main/id_000000.mp4
4. Screenshot of the execution interface
<img src="https://github.com/JWH-96/Bugs-disclosure/blob/main/Fig2.png" width="600px">
