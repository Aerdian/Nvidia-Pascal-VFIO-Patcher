# NVIDIA Pascal VFIO Patcher

This tool should be compatible with all NVIDIA Pascal series GPUs (1xxx), but this tool is provided with no warranty or liability. You are solely responsible for your own hardware and system. I accept no liability for you choosing to use this tool and any problems that arise as a result. You can report an issue on GitHub if you're having problems and I will try to get back to it, but I have no guarantees I will be able to assist. You choose to use this patcher at your own risk. If you are not using an NVIDA Pascal card, do not use this tool; it may cause serious problems. The patcher tool does perform a few checks to help avoid serious problems or malfunctions, but there are absolutely no guarantees of any kind to the validity of the patched ROM.

nvidia_pascal_vfio_patcher.py is a script that creates a patched copy of an NVIDIA vBIOS that allows PCI passthrough when using libvirt. This copy of the vBIOS can then be passed to libvirt, allowing the NVIDIA GPU to be used in a guest VM, which is done by adding the following lines to the VM domain XML file:

```
   <hostdev>
     ...
     <rom file='/path/to/your/patched/gpu/bios.bin'/>
     ...
   </hostdev>
```
# Extract vBIOS

This tool is designed to allow you to pass a Pascal (1xxx) series NVIDIA GPU through your host to a guest VM. A clean copy of the vBIOS must be used in order to accomplish this, so in order to use this tool, you must have a full clean vBIOS downloaded. You can either extract it from the graphics card using [nvflash](https://www.techpowerup.com/download/nvidia-nvflash/) or [GPU-Z](https://www.techpowerup.com/gpuz/) through Windows (preferred), or download one for your specific GPU model from [TechPowerUp](https://www.techpowerup.com/vgabios/).

# Install and Patch

The tool is compatible with Python 2 and 3. To create a patched version of the BIOS, run the script using the following parameters:

```
python nvidia_vbios_vfio_patcher.py -i <ORIGINAL_ROM> -o <PATCHED_ROM>
```

This writes a patched version of <ORIGINAL_ROM> to <PATCHED_ROM>.
