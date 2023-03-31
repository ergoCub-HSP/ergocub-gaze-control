# ergocub-gaze-control
Controller for ergoCub gaze

# Prerequisites
This repository utilizes:
- [Eigen](https://eigen.tuxfamily.org/index.php?title=Main_Page),
- [Robotology Superbuild](https://github.com/robotology/robotology-superbuild),
- [iCub Models](https://github.com/robotology/icub-models), and
- [Gazebo](https://gazebosim.org/home) for simulation.

Follow the links to install each of these.

# Installation

1. Clone the repository to your workspace:
```
git clone https://github.com/ergoCub-HSP/ergocub-gaze-control.git
```

2. Navigate to the directory:
```
cd ergocub-gaze-control/
```

3. Create a new `build` directory and navigate to it:
```
mkdir build && cd build
```

4. Then build the repository:
```
cmake ../ && make
```

# Running a demo in Gazebo

1. Open a new terminal in Ubuntu with `ctrl + alt + t` and start the YARP server:
```
yarpserver
```

  If this fails to launch, try using:
```
yarpserver --write
```

2. Open *another* terminal and run:
```
gazebo ~/your_workspace_directory/icub-bimanual/gazebo/words/ergocub-grasp-demo.sdf
```

  A model of the ergoCub should launch in Gazebo.

3. In a *third* terminal, navigate to `~/ergocub-gaze-control/build` and run:
```
./bin/gaze_control ~/directory/to/ergoCub/urdf
```

If successful, then a yarp port `/GazeController` should be open for communication.

4. In a *fourth* terminal, run:
```
yarp rpc /GazeController
```

You can now type commands for the robot to execute.

## List of Commands
In the terminal where you can `yarp rpc /GazeController`, you can type the following:
- **look_at**: point the camera to a 3D point in the robot frame
