# pyrobocopy

This script was initially developed by Anand Pillai on ActiveState.
(http://code.activestate.com/recipes/231501-python-robocopier-advanced-directory-synchronizati/)

I am just putting this on git so that I have the baseline in a static place.

# Issue 1: When using shutil.copy(), the files which are copied into targetdir will have the current date/time in their attributes, not the sourcedir file date/time. To fix this, simply change instances of shutil.copy() to shutil.copy2() - which does copy file attributes by calling shutil.copystat(). - Matt Wilson

# Issue 2: When symlinks are encountered, it copies the target file instead of recreating the link. This modification to __copy will help:

replacing: shutil.copy(sourcefile, dir2)

with: if os.path.islink(sourcefile): os.symlink(os.readlink(sourcefile), os.path.join(dir2, filename)) else: shutil.copy(sourcefile, dir2)

and similarly for the 'target to source' block

 - Michael Kantor