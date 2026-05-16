# Telescope and Instrument Configuration Files

Repository of the runtime configuration files for telescope mount and instrument functions

Control computer is an Industrial Computers RCO-300-CFL-A fanless computer, 32Gb RAM, 1Tb SATA drive

User: DEMONEXT - see security document for passwords

User home directory: <code>C:\Users\DEMONEXT</code>

## PlaneWave SiTech Interface (STI)

**Current STI version: 1.4.3**

<dl>
  <dt><code>SiTech.cfg</code></dt>
    <dd>Active STI runtime configuration file, resides in <code>Documents\Sidereal Technology\STI\SiTech.cfg</code>/</dd>
  <dt><code>SiTech_site_CCYYmmdd.cfg</code></dt>
    <dd>Backup of <code>SiTech.cfg</code> for a particular site (e.g., site={Lab,Winer,SRO}) created on local date CCYY-mm-dd</dd>
</dl>

## DEMONEXT runtime configuration files

We use YAML for the DEMONEXT runtime configuration files.

YAML (YAML Ain't Markup Language) is a simple, structured, ascii-based data serialization language used across many 
languages and operating systems that is often used for human-readable and editable runtime configuration files because
of its simple syntax.

 * Official YAML website: https://yaml.org/
 * PyYAML, the standard python YAML loader/emitter (comes with Anaconda): http://pyyaml.org 
 * A nice YAML tutorial: https://www.cloudbees.com/blog/yaml-tutorial-everything-you-need-get-started
 * Another YAML tutorial: https://python.land/data-processing/python-yaml

### YAML demo code

Demo code showing how to read in a YAML file and print the contents in a structure way.  Will work with the example
config files in this folder.

<dl>
  <dt><code>YAML Sandbox.ipynb</code></dt>
  <dd>Jupyter notebook sandbox used to learn how to handle YAML files.</dd>
  <dt><code>loadConfig.py</code></dt>
  <dd>Class to load and handle a YAML config file</dd>
  <dt><code>configDemo.py</code></dt>
  <dd>Demo program using a <code>loadConfig</code> class instance to read a file like <code>demonext.txt</code> and print the contents</dd>
</dl>

### DEMONEXT system runtime configuration file examples

Prototype DEMONEXT runtime configuration file

<dl>
  <dt><code>demonext.txt</code></dt>
  <dd>ASCII text file in YAML format with the default runtime configuration for DEMONEXT.  This is where we define instrument and observatory site
      information for FITS headers, data and log paths, subsystem settings, etc. Currently a work-in-progress.</dd>
</dl>

### Raritan PDU runtime configuration file

<dl>
  <dt><code>raritanPDU.txt</code></dt>
    <dd>ASCII text file in YAML format with the default runtime parameters for the DEMONEXT Raritan PXO 4-port PDU used by the `raritanPDU.py` class</dd>
    <dd>See also the similar section in <code>demonext.txt</code>.  We will eventually embed the name/path in the main DEMONEXT runtime configuration
      file so we can use this file for standalone programs, and changes there will automatically become visible to the DEMONEXT systems that operate the PDU for subsystem power management.</dd>
</dl>

## Observation Files

We use YAML for the DEMONEXT observation files.  These are how a single observation "visit" to a target for a program are passed into the data acquisition
system by the scheduler.  They consist of 4 blocks:
 * `project` - project information (Project ID, PI name, institution, and email) to establish data ownership for program execution tracking and time accounting
 * `target` - target name and J2000 RA and Dec celestial coordinates
 * `sequence` - observation sequence, including the guider mode, number of observations, number of repeats (if any, default is repeat=0, or do once), and then an observation parameter list with the filter, exposure time, and number of images.  These are the images to be taken in sequence by the data-taking system.
 * `constraints` - set of observation constraints applied. These include airmass, moon angle and moon phase limits, sky limits, and start/end date/time.

The observation files are loaded into the data-taking system using a demonext `ObsFile` class instance (code in `obsfile.py`).  This loads the YAML file, and defines the 
class properties to give access to the key for execution.

### Example observation (.obs) file

See these demo .obs files
<dl>
  <dt><code>myObs.obs</code></dt>
  <dd>maximal observation file used for `ObsFile` class definition and testing</dd>
  <dt><code>obsTest.obs</code></dt>
  <dd>YAML obs file created using the YAML file emit methods to show what a machine-generated version using YAML `dump()` looks like (see `YAML Sandbox.ipynb` for how this file was generated.  The by-hand syntax used by `myObs.obs` is cleaner and 
      will be the method we propose we use, including the provision for adding comments to improve readability and provenance tracking</dd>
</dl>
These .obs files may be tested using the `ObsFile Sandbox.ipynb` Jupyter notebook, but you will need to copy into your working directory a copy of the `obsfile.py` code from the demonext
module if it is not in your python path
