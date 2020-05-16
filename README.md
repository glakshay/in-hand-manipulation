

## ROS Workspace
The 'ros_ws' folder contains all the ROS packages and projects.  For a description of what each folder and directory does, please refer to their individual 'README.md' files.

In brief, everything in the 'src' folder outside of the 'projects' folder are general packages that can be used by anyone in workspace, and are a general list of packages that can be used by others.

Anything in the 'projects' folder is project-specific, and are usually not meant to be used by others.  If you are looking to start up a new project/package, please create it here.  If possible, please organize all your project's packages into a single folder containing them.  This helps prevent clutter and keeps things organized.

Avoid using generic names for items in the 'projects' folder, like a node called 'robot\_simulator'.  If a package is really general, move it outside the projects folder and modify it to be flexible and modular.  Otherwise, be more specific with names to avoid collisions when running 'catkin\_make'.

### Setup
To setup the ros workspace locally:
1. Go to the workspace location you want
2. Run 'git clone'
3. 'cd' into the repository
4. Run 'rosdep install --from-paths --ignore-src ros_ws -y' to install all dependencies
5. 'cd' into the 'ros_ws' folder
6. Run 'catkin_make'
Note that the above instructions are no substitute for actually install ros and setting up rosdep, please first follow the instructions at 'http://wiki.ros.org/melodic/Installation/Ubuntu' (or whatever your ros distribution and linux distro combination happen to be).

### package.xml
Due to the use of the 'rosdep' command, it is recommended to explicitly list all build/exec dependencies in your package's 'package.xml' file.  This ensures the above command will download and setup all necessary files when a new user is setting up the workspace.

### *_moveit_config Files
These files generated by moveit can differ from project to project, even if the same robot is used

For this reason, we recommend the names of the config files to be changed from the default to avoid interference

The process to do so is as follows:
* No config file generated:
    1. Run moveit setup assistant:
    `rosrun moveit_setup_assistant moveit_setup_assistant`
    2. Click 'Create New Moveit Configuration Package'
    3. Fill out all necessary information on the robot
    4. When done, at the last page (Configuration Files), set the folder to be the custom config name:
    `mer_lab/src/projects/project_name_moveit_config`
    Replace project_name with the name of the project this moveit_config file is for
* Config file has already been generated:
    1. Run moveit setup assistant:
    `rosrun moveit_setup_assistant moveit_setup_assistant`
    2. Click Edit Existing Moveit Configuration Package
    3. Go to the last page (Configuration Files), and set the folder to be the new custom config name:
    `mer_lab/src/projects/project_name_moveit_config`
    Replace project_name with the name of the project this moveit_config file is for
    4. Try launching moveit from the required package that needs it and connecting to it
    5. If successfull, delete old moveit_config package


