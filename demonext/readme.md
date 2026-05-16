# DEMONEXT observatory control system

**Updated: 2026 May 16 [rwp/osu]**

## Modules and Scripts

The `demonext` module implements classes we need for robotic operation of the 
DEMONEXT observatory.

#### Current status:

Submodules implemented to date:
 * `camera.py` - Science and guide camera operation (`Camera` class) with MaxIm DL and ASCOM
 * `config.py` - YAML runtime configuration file handling (`Config` class)
 * `focuser.py` - PlaneWave Hedrick focuser operation (`Focuser` class) with PWI3.
 * `guider.py` - DEMONEXT science guiding (`Guider` class)
 * `obsfile.py` - Observation file handling ('ObsFile` class)
 * `pdu.py` - Raritan power-distribution unit query and control (`RaritanPDU` class)
 * `site.py` - Observatory site info for the Sierra Remote Observatory (`Site` class)
 * `telescope.py` - telescope mount operation (`Telescope` class) with PlaneWave STI interface and ASCOM

