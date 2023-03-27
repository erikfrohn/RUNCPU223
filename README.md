# RUNCPU223 README

Made by
Erik Frohn
s1034685

The CPU is able to start and passes all tests. Example .hex files were able to be loaded and testing the CPU using hello-world.hex and game-of-life.hex proved succesful. 

## Design choices
Subcomponents of the CPU need no further explanation, except for the Instruction Decoder. The CPU kept initializing with the PC at +4, as I made it add 4 whenever we are in the Fetch phase. To prevent the PC starting at +4, I created a small circuit that becomes active only after the first fetch phase. The Instruction Register stores the instruction coming from the Databus_{in} at Fetch, and instantly gives the condition to the Tester, the rest of the output is set to 0, until the Execute phase, I've chosen to use a masking AND for this. During fetch phase (from the second fetch phase), I add +4 to the PC using the machine code 0x60040FF0. I've defaulted the Opcode to ADD, as it is needed for LOADHI, READ and WRITE. When decoding a LOADHI, the destination register is also sent to RegB, to make the overall data paths more clear, otherwise I'd have to branch RegD to RegB in the CPU whenever we perform a LOADHI
