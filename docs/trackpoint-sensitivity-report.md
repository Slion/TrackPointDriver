Those are USBHID SET_REPORT Request when changing TrackPoint Stick sensitivity.

Only thing that's changing is:
- IRPID which is bytes 2 to 9 which is a pointer to something so that's to be expected I guess.
- Byte marked by ^^ is most certainly the sensitivity value being sent to our TrackPoint keyboard.

Min sensitivity:
```          
             ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ
0000   1c 00 40 91 9c 49 06 8d ff ff 00 00 00 00 1b 00
0010   00 01 00 07 00 00 02 0d 00 00 00 00 21 09 04 03
0020   01 00 05 00 04 6a 03 66 38
                            ^^ 
```

Max sensitivity:
```          
             ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ
0000   1c 00 a0 f7 b0 3e 06 8d ff ff 00 00 00 00 1b 00
0010   00 01 00 07 00 00 02 0d 00 00 00 00 21 09 04 03
0020   01 00 05 00 04 6a 03 fc 38
                            ^^ 
```

Back to normal:
```          
             ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ ˇˇ
0000   1c 00 10 20 5f 41 06 8d ff ff 00 00 00 00 1b 00
0010   00 01 00 07 00 00 02 0d 00 00 00 00 21 09 04 03
0020   01 00 05 00 04 6a 03 b3 38
                            ^^ 
```                            
