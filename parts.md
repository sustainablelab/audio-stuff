# Parts

## Audio sources

Laptops and iPads usually have a 3.5mm audio output. This is
stereo. But this is a TRRS (four-conductor) output, not TRS
(three-conductor). The extra conductor is for microphone input,
so this audio "output" jack is also the microphone input.

For my purposes, it is safe to ignore the fourth conductor.
Connecting a male TRS, the sleeve (ground) will connect the
microphone input to 0V. This is absolutely fine: it's the
equivalent of no signal on the microphone.

The Behringer Xenyx 502 has no stereo inputs. A simple stereo
cable will not work. For example OF THE WRONG THING TO DO,
connecting a laptop headphone output to the Behringer with a
stereo cable:

```wrong
WRONG:
male 3.5mm plugs into laptop
male 6.35mm plugs into a mono input on the Behringer
```

To connect such a 3.5mm audio source with stereo output, use the
Hosa YMM-261 Stereo Breakout cable:

- male: 3.5mm TRS stereo (plugs into audio source)
- breakout:
    - 3.5mm TS Mono female 


## Mixer

I have the Behringer Xenyx 502. It's cheap and solid.

### Inputs

There are three channels and five inputs. Channel 1 is mono,
channels 2 and 3 are stereo. All five inputs are mono.


#### Channel 1

- XLR: balanced mono
- 6.35mm: balanced mono

#### Channel 2-3

- 6.35mm: balanced mono left
- 6.35mm: balanced mono right

Laptop audio out is 3.5mm stereo.

Do not connect this directly to the inputs on the Behringer with
a 3.5mm to 6.35mm (1/8" to 1/4") stereo cable.

## Hardware Synths

I have the Korg NTS-1.

The only sucky thing about this tiny synth is that there is no
way to save state. When power is lost, everything resets. Make a
nice patch? Good for you, no way to save it.

### Loading new sounds

There is NTS-1 digital Librarian, a Korg GUI for use when
USB-connected to the NTS-1, but this is for loading new
oscillators and effects onto the NTS-1.

Connect to computer over USB, directly to USB port, no hub.

Search for support on NTS-1 on Korg site under Synthesizers. The
link (for now) is this:

    https://www.korg.com/us/support/download/product/0/832/

There are PDFs:

- the manual that comes with the NTS-1
- MIDI implementation chart
- MIDI connectivity manual
- keyboard ribbon calibration

There is Windows software:

- NTS-1 digital Librarian
- System Updater
- Effect template
- 2D/3D data

There is a Windows driver:

- KORG USB-MIDI Driver

Also go to the Korg NTS-1 product page. Scroll down and find this
link:

    https://korginc.github.io/logue-sdk/unit-index/

### MIDI control

The Korg NTS-1 has a midi input but it is a TRS jack. Connect a
type A MIDI TRS. I bought a type A MIDI TRS cable from Pacific
Circuits, part number `0-COASTMidi`, but the MIDI end is female,
while the Arturia Keystep also has a female MIDI jack. So I also
need a regular male-to-male MIDI cable between the Arturia and
the type A MIDI TRS cable.

## MIDI keyboards

I have an Arturia Keystep and an Impact GX61.

The Arturia has a USB jack and a MIDI output, while the Impact
GX61 only has a USB jack.

Connect the Arturia Keystep to the Korg NTS-1 using the type A
MIDI cable and a second male-to-male MIDI cable.
