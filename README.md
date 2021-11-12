# MSI Silent Option
Silent Option is a tiny applet made by MSI for MSI laptops as a fan control solution (original download found [here](https://forum-en.msi.com/index.php?threads/updated-2016-05-06-silent-option-fan-control-application-for-msi-laptops.255972/))

However the installer for Silent Option is bloaty (InstallShield) and the installer installs a lot of unnecessary service DLLS (such as the MSI SCM service dll, which is not required for newer MSI laptops and has been replaced by WMI definition instrumentation)

This repository will provide a portable archive file ([under Releases](https://github.com/hanzbadua/MSISilentOption/releases)) with Silent Option so you don't have to go through the bloat installation

NOTE: YOU NEED TO MAKE A REGISTRY KEY ENTRY WITH THE NAME `MofImagePath` AND THE VALUE POINTING TO THE LOCATION OF `FanControlDefs.dll` FOUND IN THE ARCHIVE. THIS ENTRY GOES IN `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WmiAcpi` WITH THE TYPE `REG_EXPAND_SZ`

For example: If I extracted the Silent Option archive and put the Silent Option folder in my `C:\Program Files (x86)` folder, the path of `FanControlDefs.dll` would be `C:\Program Files (x86)\SilentOption\FanControlDefs.dll`. Therefore, I would set the `MofImagePath` registry key to `%programfiles(x86)%\SilentOption\FanControlDefs.dll` (`%programfiles(x86)%` is an environment variable pointing to your `C:\Program Files (x86)` directory)

If you don't create this registry key, the `FanControlDefs.dll` containing custom MSI MOF WMI definitions won't be loaded by the `WmiAcpi` service, and Silent Option will NOT work functionally at all

ANOTHER NOTE: I've only tested Silent Option with custom MOF definitions on my MSI GF65-9SEXR laptop. It may not work for other MSI laptop models, and I'm not helping whatsoever with any issues

OTHER OTHER NOTE: YOU MUST RESTART YOUR COMPUTER CREATING THE MOF DEFINITION PATH REGISTRY KEY. THE WMIACPI SERVICE ONLY INSTANTIATES CUSTOM MOF DEFINITIONS ON BOOT
