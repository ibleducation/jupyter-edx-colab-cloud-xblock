# Colab XBlock

## Overview
Provides a link with optional instructions to a Google Colab Notebook

## Installation
### XBlock
* login as the root user: `sudo -i`
* New Installation:
    * `/edx/bin/pip.edxapp install git+https://gitlab.com/iblstudios/jupyter-edx-colab-cloud-xblock`
* Re-Installation:
    * `/edx/bin/pip.edxapp install --upgrade --no-deps --force-reinstall git+https://gitlab.com/iblstudios/jupyter-edx-colab-cloud-xblock`
* Restart the `edxapp` via `/edx/bin/supervisorctl restart edxapp:`

### Edx Server Setup
In the following files:
* `/edx/app/edxapp/edx-platform/lms/envs/common.py` 

Add the following at the bottom of the `INSTALLED_APPS` section:
```python
    # Colab XBlock
    'colab_xblock',
```

* In the studio, go to the course you would like to implement this XBlock in
* Under `Settings` at the top, select `Advanced Settings`
* in the Advanced Module List, add: `"colab_xblock"`
    * ensure there is a comma after the second to last entry, and no comma exists after the last entry
* Select Save

The Google Colab Link can now be added to a unit by selecting `Colab XBlock` from the `Advanced` component menu

Restart `edxapp` via `/edx/bin/supervisorctl restart edxapp:`

## How it works
Provides a button that will open a new tab/window to the provided google colab notebook.

If the link is a github link, we reformat it to a google colab link, otherwise we leave it as is.

The user can enter optional instructions which will be displayed above the link.

