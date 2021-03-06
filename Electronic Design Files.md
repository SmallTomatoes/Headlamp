The electronic design of the headlamp is intentionally simple, but is governed by a few principles in order to create a product that is resilient in a remote location. 
If the design goals can be achieved through a different deisgn, the headlamp design/construction could be more 
or less simple.  Design goals: 
1. The product can be repaired or replaced by someone within one-day of traveling. 
2. The product design minimizes the need for industrial manufacturing. 
3. The product design maximizes the use of recyled, reused, or biodegradable materials. 
4. The design minimizes cost of the product. Ideally, all parts (excluding charging device) cost less than $7 USD per headlamp.

The design information below describes the first, licensed, open-source design for the headlamp. 

=========
Circuit Explanation
=========
This circuit uses a ferrite bead to facilitate a switching power supply and voltage gain. The implementation of this
device is known as a blocking oscillator. Two laminate wires are wound around the ferrite bead parallel to eachother,
producing a unique toroid. Unlike a standard transformer, the leading wires of the toroid are connected to form a
node that is connected to the power supply. The unique ends are connected to the base and collector of the 
transistor, independently. When the 1.2V battery is connected, the current flowing through the primary quickly turns on the transistor; thus allowing current to flow through the secondary winding. This current through the secondary
winding induces a voltage in the primary winding, which increases the current to the base of the transistor further.
The increased current to the base of the transistor allows for a greater current to flow through the collector. At
half of the period, the magnetic field of the ferrite bead passes through the saturation point of the hysteresis
curve. The resulting magnetic field breakdown induces a current in both windings. This sudden change in the magnetic
field induces the necessary voltage to drive the LED. The voltage from the secondary winding to the collector is
affected by the number of turns of wire around the bead. It can be varied to produce a voltage greater than 2.85V,
which is the “turn-on” voltage of the 1-watt LED. The frequency of this operation is about 75kHz at a battery voltage
of 1.2V, so the LED output appears continuous. Increasing the number of turns around the ferrite bead increases the
voltage gain. This was experimentally observed, and theoretically calculated. The operation of the circuit allows the
nominal 3.0V LED to be driven from a 1.2V battery. 

*Shortcut: In other words, this is a slightly-optimied joule-theif circuit!*

Modeling of the voltage and current of the circuit can be found here: 
[Schematics-Modeling](https://github.com/SmallTomatoes/Headlamp/tree/master/Schematics-Modeling)

=========
Circuit Construction
=========
If you want to build this circuit yourself from scratch, you can order a kit here:
Or, you could look at the following list of parts and make your own kit. I give suggestions below based off of the parts I specifically used in the second list. 

**Parts list**
- 1 Watt Neutral White LED 
- Ferrite Bead 
- NPN transistor 
- 1 kohm 1/4 watt tolerance
- 1,200mAh AA NiMH (nickle-metal hydride) recharable battery
- laminated copper wire, about 32 AWG
- 22 AWG insulated stranded copper wire, about 7"
- 22 AWG insulated solid copper wire, about 4"

**Specific Parts Suggestion**
- LED: [Luxeon Rebel Endor Star](http://www.ledsupply.com/leds/luxeon-rebel-endor-star-1-up-neutral-white-high-power-led) (LED with metal core PCB) or simply the [Luxeon Rebel Emitter](http://www.ledsupply.com/leds/luxeon-rebel-emitter-neutral-white-4000k)
- Ferrite Bead: If you want to fit the transistor insdie the ferrite bead, the inner diameter of the bead needs to be about 1mm larger than the width of the transistor, and about 9mm long. There are three examples of ferrite beads that fit this specification in the [Spec Sheets](https://github.com/SmallTomatoes/Headlamp/tree/master/Spec%20Sheets) folder. For the transistor recommended (below), the specs for the ferrite bead are as follows:
  * Inner diameter: 4.75mm
  * Outer diameter: 9.50mm
  * Length: 10.4mm
- NPN Transistor: Transistor should have a low collector-emitter saturation voltage and perform well with a low supply voltage. I have had good results with the Fairchild KSD5041. Common hobby transistors did not allow for a bright LED output. The ZTX1048A transistor [ZTX Spec Sheet](https://github.com/SmallTomatoes/Headlamp/blob/master/Spec%20Sheets/ZTX1048A-92228.pdf) produced a high-pitch noise with all other components remaining the same. 


