# BoxNav

![](demo.gif)

A simple playground for making an agent navigate around some directed corridors represented as overlapping boxes.

## Getting Started in Unreal Engine

### Dependencies
Create or open an unreal engine project. Ensure you have the OSC (Open Sound Control)plugin file downloaded into your current project. Ensure you also have the [ue5osc](https://github.com/arcslaboratory/ue5osc) library downloaded. 

### Beginning the Simulation in UE5
Clone this repository. Move into the cloned boxnav directory. Press play on your Unreal Engine project.

Then to kick off the simulation you must first ensure the following steps are followed:

1. It is essential that you create a conda environment.

```
conda create --name <env_name>
```

2. Next, activate this newly created environment and run the following commands in the terminal.

```
conda install python matplotlib celluloid
```

```
python -m pip install python-osc
```

3. After downloading the ue5osc library, navigate into this repository and you will need to install this library with:

```
python -m pip install --editable .
```

4. Now every time you want to run the Boxnav script you must ensure you open the environment with:

```
conda activate <env_name>
```

5. After activating the environment, the script is now ready to run with the command:

- To run the script just by itself, you do not need to open unreal engine and you can type:

~~~bash
python boxsim.py <navigator> 
~~~

- In order to operate with unreal engine the following line will instead be required:

~~~bash
python boxsim.py <navigator> --ue
~~~


### Note about Command Line Arguments

The above command specifies the required arguments needed to run the box simulation in Unreal Engine. But there are other optional specifications. Here are all the arguments you can specify:

- \<navigator>: must choose between "wandering" and "perfect" and decides the navigator that will be used when running the simulation.
- --anim_ext=\<extension>: (optional) extension for output format to help visualize run.
- --max_actions=\<int>: (optional) Maximum number of allowed actions when running the simulation
- --save_images=\<file path>: (optional) enables image capturing to specified path (may be relative or absolute path)
- --ue: (optional) Note: Required if you want to connect to Unreal Engine
- --py_port=\<port>: (optional) Python OSC server port.
- --ue_port=\<port>: (optional) Unreal Engine OSC server port.
- --image_ext=\<extension>: (optional) Sets file extensions for images to be saved as.
- --resolution=\<string ResXxResY>: (optional) sets resolution of screen

You can look at how these arguments are used in the boxsim.py file.

### Notes about Unreal Engine

- In our packaged 'game' you can add the following lines into the Game.ini file found in either:
    - MacOS: (Hidden folder) \<Packaged_Game_Name>\Epic\ARCSAssets\Saved\Config\Mac
    - Windows: \<Packaged_Game_Name>\ARCSAssets\Saved\Config\Windows
```
[/ARCSRobots/SimpleRobotCamera/BP_Pawn_SimpleRobotCamera.BP_Pawn_SimpleRobotCamera_C]
UEPort=<port>
PyPort=<port>
RobotVisible=<Bool>
```

### Other Notes

Right-handed coordinate system.

- Up-Down is y relative to Oldenborg
- Left-right is x relative to Oldenborg
