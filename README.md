# 486 Sandwich Socket Blaster

The 486 Sandwich Socket Blaster is a new design of the 486SocketBlaster that is much easier to solder and put together.
It is a simple voltage adapter / interposer for 486 processors. It allows you to use a 3-volt 486 CPU on an older 5-volt-only motherboard.
For example you can use a DX4 or an Am5x86 on an old 486 motherboard that would normally only work with 5-volt CPUs.
This basically converts any 3-volt CPU to an "Overdrive".

<img src='img/486SandwichSocketBlaster_pcb_front.jpg' alt='486SandwichSocketBlaster' height=240 width=auto>

<img src='img/486SandwichSocketBlaster_pcb_back.jpg' alt='486SandwichSocketBlaster' height=240 width=auto>

# How does it work ?

It is really simple: All CPU pins are passed through to the motherboard socket, except for the Vcc.
Those are connected to the output of a mini buck converter that can be soldered to the 486SocketBlaster board.

# Soldering/Assembly Instructions

The adapter includes two parts: the top and bottom part, both of which use the exact same PCB.
The two parts connect to each other with standard 2.54mm-pitch pin-headers, the top part with male headers and the bottom part with female headers.
The top part accepts the CPU with either a female 168-pin BGA socket, or an equivalent collection of female headers.
The bottom part has the pins that insert into the motherboard socket.
The pins are made from widely available pin-headers.

## Solder Jumpers
These need to be set differently for the top and bottom parts.

# Voltage regulator

The Sandwich Socket Blaster can be powered by a cheap of-the-shelf buck converter, or by an external one.
Unlike the original Socket Blaster, this only accepts the small voltage buck converter (18mm x 12mm), usually found using keywords like "mini buck converter".
These are commonly rated at up to 3A of current.
Given that 3-volt 486 CPUs are usually very efficient (the DX4-100 is rated at max 3.55/5.22W typical/max) such a regulator should be adequate in most cases.
For best stability try to source a good quality part.

If you are planning to overclock or to use a more power hungry CPU, please use an external regulation circuit plugged in to the `EXTPWR` header, or use a *very* good quality mini buck converter.

# WARNING!!!

Please make sure you know what you are doing!
Improper assembly/settings/use can damage both your precious motherboard and your precious CPU!

# Features

- External Power Header. This can be used either for monitoring the CPU voltage, or for providing power externally, either with an external power supply or an external voltage regulator.
- CLKMUL Header for selecting/overriding the CPU multiplier. This controls CPU pin `R17`. 1-2 connects it to the motherboard socket pin and 2-3 connects it to ground. This reduces the multiplier of a DX4 to 2x (66MHz) and sets the multiplier of an Am5x86 to 4x (133MHz).
- WB/WT Header for selecting/overriding Write-Back/Write-Through cache. This controls processor CPU pin `B13` (which is the `CLKMUL` pin in earlier 486 CPUs). 1-2 connects it to the motherboard socket pin, and 2-3 connects it to Vcc, which enables Write-Back.
- STPCLK pin for use with the Throttle Blaster. This connects directly to CPU pin `G15`, which in DX4 and 5x86 CPUs is the STPCLK pin. This allows you to throttle down the CPU and achieve the whole range of speeds from the original IBM PC all the way to the max speed the CPU can provide.

# Bill of materials

Item                            | ##  | Description
--------------------------------|-----|--------------------------------------------------------
mini buck converter             | 1   | We only the small 18mm x 12mm ones. These usually have chips like MP1584, MP2307 and others
40pin SIP pin header (male)     | 5   | Single-row round pin 2.54mm pitch (male). Socket pin diameter: 0.50mm, PCB pin diameter: 0.60mm. (see photo below)
40pin SIP socket header (female)| 5   | Single-row round pin sockets, 2.54mm pitch. PCB pin diameter: 0.55mm. (see photo below) 
SMD Ceramic Capacitors          | 4   | 10uF SMD 1206, 6.3V or higher
3-pin header 2.54mm pitch       | 2   | (optional) Headers used for selecting the CPU Multiplier (CLKMUL) and Write-Back/Write-Through cache (WB/WT)
1-pin header 2.54mm pitch       | 1   | (optional) For connecting the Throttle Blaster to STPCLK.
Jumper 2.54mm pitch             | 2   | (optional) Jumpers for the CLKMUL and WB/WT headers

Gerber files can be found in the releases: https://github.com/scrapcomputing/486SandwichSocketBlaster/releases

Please note that the headers are a very tight fit. So please make sure that you get headers of the correct pin diameter.
