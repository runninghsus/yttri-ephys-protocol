# yttri-ephys-protocol
Yttri Lab ephys analysis protocol


### Prerequisite
For OpenEphys, you must have the following files transferred to network drive

<span style="color:orange;font-weight:350;font-size:18px">
     continuous.dat
</span>


### Move your file to PSC to utilize GPU

First, transfer the `continuous.dat` file from network drive `Z:\ ` to `data.bridges.psc.edu`

##### Step 1.1: Network drive log in
Open windows powershell and log into network drive `Z:\ `.

![](./tmp/win_powershell.png)

##### Step 1.2: Transfer binary file to PSC bridges2
Once logged in, you will be in `Z:\ ` directory. To transfer the file over to PSC:

```commandline
scp -r -caes128-gcm@openssh.com -o Compression=no AE2_Training/072423/ yttri@data.bridges.psc.edu:/ocean/projects/bio210065p/yttri/AE2_Training/
```

This should be transfering at
<span style="color:orange;font-weight:350;font-size:18px">
     >500MB/s
</span>


### Log into PSC bridges2 and run matlab
Confirm that you have mobaxterm installed (only available in windows).

##### Step 2.1: Log into bridges2
If you had previously logged into bridges2 before, you can simply select that session.
![](./tmp/mobaxterm.png)

Otherwise, select `Session -> New session`. Select the left most SSH button, and enter credentials.
![](./tmp/mobaxterm_newsess.png)

##### Step 2.2: Interact with a partition of the GPU.
First, go into the project directory that houses the computational resources.
```commandline
cd /ocean/projects/bio210065p/yttri
```

Then, ask for a partition within the GPU-shared resource.
```commandline
interact -p GPU-shared --gres=gpu:v100-32:1 -t 08:00:00
```
The `-t 08:00:00` is asking for shared node for up to <span style="color:orange;font-weight:350;font-size:18px">
     8 hours
</span>

##### Step 2.3: Load matlab
Once you have access to the GPU node. You can load up matlab.
```commandline
module load matlab
matlab
```

MATLAB 2022b will pop up and allow you to run kilosort like you would on a normal computer.


### Manual sorting with Phy
Once kilosort3 is finished, we can transfer the processed files back to `Z:\ ` to manual sort the neurons.

##### Step 3.1: Network drive log in






