# Audio Primer

The standard audio cables are called phone connectors.

## Plug diameter

I grew up calling these 1/8-inch and 1/4-inch. These dimensions
refer to the diameter of the *sleeve* conductor. The metric names
are the actual diameters:

- 1/4-inch has a 6.35mm diameter sleeve
    - 1/4-inch is exactly 6.35mm
- 1/8-inch has a 3.5mm diameter sleeve
    - but 1/8-inch is 3.175mm: the sleeve diameter is 0.325mm
      more than 1/8-inch
    - 1/8-inch is simply the closest reasonable imperial name
    - the exact imperial diameter is 0.137795-inches

## Number of conductors

The plug part of the phone connector comes with different numbers
of conductors:

### TS (2-pole)
- Tip / Sleeve
- Two conductors
    - Tip : signal
    - Sleeve: 0V reference
- e.g., eurorack patch cables
- exclusively used for mono audio

### TRS (3-pole)
- Tip / Ring / Sleeve
- Three conductors
    - Tip : signal (depends on application)
    - Ring : signal (depends on application)
    - Sleeve: 0V reference
- has many uses:
    - stereo audio
    - balanced mono audio
    - MIDI

### TRS for stereo audio

- Tip is left
- Ring is right

I use the mnemonic RRR: Ring, Right, Red. In addition to the
color coding, the Hosa YMM-261 labels the breakouts "Tip" and
"Ring".

### TRS for balanced mono audio

- Tip is positive
- Ring is negative

### TRS for MIDI
- MIDI used to be a DIN 41524 plug:
    - 5 pins spread over a half-circle
- DIN 41524 numbers the pins 1, 4, 2, 5, 3, going
  CCW:
    - pin 1 at 180°
        - pin 4 between pins 1 and 2
    - pin 2 at 90°
        - pin 5 between pins 2 and 3
    - pin 3 at 0°
- MIDI DIN:
    - pins 1 and 3 are not connected
    - pin 4 is VCC, usually +5V
    - pin 2 is the cable shield
    - pin 5 is the current sink (the data)
        - i.e., the MIDI device floats pin 5 or pulls
          it low, sinking current from the device it
          connects to, and that current comes from
          pin 4
- MIDI TRS has two types: A and B

#### TRS MIDI A
- Type A MIDI TRS (Korg, Make Noise):
    - Tip: pin 5 (data)
    - Ring: pin 4 (VCC)
    - Sleeve: pin 2 (shield)

#### TRS MIDI B
- Type B MIDI TRS (Arturia) flips Tip and Ring:
    - Tip: pin 4 (VCC)
    - Ring: pin 5 (data)
    - Sleeve: pin 2 (shield)

### TRRS
- Tip / Ring-1 / Ring-2 / Sleeve
- two flavors:
    - CTIA: MIC is Sleeve, GND is Ring-2
    - OMTP: MIC is Ring-2, GND is Sleeve
- CTIA is the more common type and it makes more sense
- CTIA is sometimes called AHJ (American Headset Jack)
- OMTP shows up on older devices
- See this [reference](https://help.longtailproducts.com/hc/en-us/articles/207970396-Smartphone-Headset-Standards-Apple-iPhone-AHJ-CTIA-OMTP) for details about which products have which type of TRRS

## Balanced and Unbalanced Audio Signals

Balanced audio cables use two signal conductors to carry one
signal.

*Balanced* is the **special case**. Most audio cables are *unbalanced*.

Thinking about the number of conductors for the different plug
types (TS, TRS), there are two logical conclusions:

*All stereo audio (TRS) cables are unbalanced because they carry two
signals and have two signal conductors plus one 0V reference.*

*All mono audio (TS) cables are unbalanced because they carry one signal
and have one signal conductor plus one 0V reference.*


So for an audio cable to carry "balanced" audio, it needs:

- Three conductors
- Two conductors carry one differential signal
- One conductor is a shield to prevent electrostatic coupling

Unbalanced means the signal is the voltage difference between a
signal conductor (e.g, the TIP or RING in TRS) and the cables 0V
reference conductor (e.g., the SLEEVE in TRS). The downstream
amplifier *uses* the 0V reference. If the audio cable is stereo,
the single input has two such amplifiers: one for the LEFT and
one for the RIGHT.

Balanced means the signal is the difference between two
conductors (e.g., the TIP and RING in TRS, or two of the
conductors in an XLR).

This provides noise immunity assuming noise couples equally onto
the two conductors. Noise common to both signal conductors is
called common-mode signal, and it is rejected by the downstream
amplifier using a design a called a "difference" amplifier.
Difference amplifiers achieve very high common-mode rejection and
only amplify the difference between the two inputs.

To add to the noise immunity, balanced audio cables also have a
shield conductor. So that's three conductors in total.

Therefore:

- there is no TS balanced audio cable because it does not have
  enough conductors
- and all TRS balanced audio cable is mono because the signal is sent
  differentially on the TIP and RING
- a balanced stereo audio cable, for which I am not aware of any
  standard, requires five conductors: two conductors for
  differential LEFT, two conductors for differential RIGHT, and
  one shield conductor

### Shield vs 0V reference

A balanced audio cable has a "shield". An unbalanced audio cable
has a "0V reference". In a balanced system using a TRS cable, the
SLEEVE is the "shield". For unbalanced, the SLEEVE is the 0V
reference for both the left and right audio channels.

People lazily refer to both "shield" and "0V reference" as
ground.

#### Shield

The shield of a balanced audio cable is connected to a DC
reference for shielding, i.e, blocking noise from coupling onto
the signal conductors. The downstream amplifier does not use the
shield conductor as an input.

People lazily refer to the shield as ground. This ground is
usually the potential of the metal chassis. The metal chassis is
usually connected to an earth ground, but there is nothing magic
about earth ground. The only reason to connect to earth ground is
for safety in high-voltage equipment -- in case a high-voltage
conductor comes loose and makes contact with the chassis, tieing
the chassis to earth ground creates a ground fault that trips the
circuit breaker feeding the machine.

In audio, the reason to connect to the chassis is purely for
noise immunity. It doesn't matter what voltage the chassis
happens to be at relative to earth ground. Connecting the shield
conductor to the chassis creates a Faraday cage to prevent noise
from coupling into the signal path via electrostatics (i.e., a
change in charge on the chassis will not induce a change in
charge on the signal wires via a capacitive coupling because the
shield conductor and the chassis are at the same potential, so it
is physically impossible for an electric field to form between
these two conductors).

One last complication: since the balanced cable is going between
two devices, it's possible that both have a metal chassis. The
shield should only connect to one of these, otherwise, it's
possible that the two metal cases are at a different potential,
in which case the shield is carrying current. It doesn't matter
which one is used, and there is no convention, so people need to
check (with a continuity meter) to see what convention is used on
each device and figure out what convention they need to follow in
this setup. A lot of work, particularly when you have to start
modifying the cables by "lifting" the shield off one end to
prevent making a connection.

#### 0V reference

People lazily refer to 0V signal references as ground. In this
case, it has nothing to do earth ground or with the metal
chassis. The 0V signal (SLEEVE) is the reference potential for
the signal (TIP or RING).

### Mixing balanced and unbalanced systems

First, take the common case of mixing unbalanced stereo and mono.
A stereo OUT to a MONO in shorts the right channel of stereo to
the 0V reference. The right channel is missing, and it *might*
harm the stereo OUT because the stereo OUT is not happy trying to
drive a 0V reference.

Now take the same case, but make the mono input **balanced**.
This is my case for combining my laptop stereo audio out with the
Behringer mixer's balanced mono inputs.

Connecting a STEREO (and therefore unbalanced) OUT to a
**balanced** MONO IN will sound awful because the difference
amplifier is outputting the difference between the left and right
channels. And, again, it *might* be harmful, but this time the
potential for harm is to the balanced IN amplifier. The the
common-mode signal will have a larger DC component than it would
normally (normal being a balanced output connected to the
difference amp).

There is no harm connecting an **unbalanced** MONO OUT into a
**balanced** MONO IN (which is why the Behringer labels its
inputs "BAL or UNBAL"), but there is also no noise reduction
benefit running unbalanced OUT into balanced IN. The amplifier in
the balanced input takes the difference between two signals. An
unbalanced MONO cable has its signal on TIP and its 0V reference
on SLEEVE.

But the reverse is not true. Connecting a balanced MONO OUT into
an unbalanced MONO IN is not a good idea for the same reason
connecting a STEREO OUT to an unbalanced MONO IN is not a good
idea. In this case, the "negative" signal from the balanced OUT
is connected to 0V by the amplifier.


