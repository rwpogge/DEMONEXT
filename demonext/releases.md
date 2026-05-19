# DEMONEXT module release notes

**Last Release: 2026 May 19**

## Version 1.0.2 - 2026 May 19
Patch, fixed bug in `Camera.cooldown()` method that ignored changing the set point with the 
optional argument.


## Version 1.0.1 - 2026 May 17
Field install and test at SRO.
 * Fixed issues with dependencies in `pyprohect.toml`, advanced version ID
 * Bug online 229 of `telescope.py` - incorrect nesting of `else` statement fixed
Ran in an ipython shell far from the source, worked fine. Verified with
copy of the notebooks away from development version, worked fine.


## Version 1.0.0 - 2026 May 16

Migrated working code from https://github.com/kyleecpi/DEMONEXT after deployment of the telescope and instrumentation at Sierra Remote Observatories in March 2026.

New development will continue in this repository.  This separates the core observatory telescope and instrument control code from the overall director and
scheduler code development led by Kylee Carden at JHU.
