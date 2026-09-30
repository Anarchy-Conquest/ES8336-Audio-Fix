# ES8336 Audio Fix for Linux Mint

A persistent solution for the Everest Semiconductor ES8336 audio codec issue on Linux Mint, resolving the conflict where the internal microphone and speakers cannot function simultaneously.

---

## Instructions

### 1. Configure SOF Driver Options
Create or edit `/etc/modprobe.d/intelsnd.conf`:

```bash
options snd-sof-pci-intel-tgl dmic_num=2

amixer -c 0 cset name='Headphone Switch' on
amixer -c 0 cset name='Speaker Switch' on
amixer -c 0 cset name='Internal Mic Switch' on

3. Make It Persistent (Startup Applications)
​To make the fix run automatically every time you log in:
​Open the app menu and launch Startup Applications.
​Click the + icon at the bottom and select Custom command.
​Fill in the fields:
​Name: ES8336 Audio Routing Fix
​Command: sh -c "amixer -c 0 cset name='Headphone Switch' on && amixer -c 0 cset name='Speaker Switch' on && amixer -c 0 cset name='Internal Mic Switch' on"
​Startup delay: 2
​Click Add.
​Created to restore full audio and microphone functionality on Linux Mint.