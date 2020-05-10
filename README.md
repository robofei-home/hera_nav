# hera_nav

This package is an implementation of the [Ros Navigation Stack (RNS)](http://wiki.ros.org/navigation) for the [HERA robot (2020 version)](http://robofei.aquinno.com/athome/wp-content/uploads/2020/01/TDP2020ROBOFEI.pdf).

## Dependencies:
* [ROS](https://www.ros.org/) (Melodic Morenia)
  * [roslaunch](http://wiki.ros.org/roslaunch)
  * [rviz](http://wiki.ros.org/rviz)
* [hera_description](https://gitlab.com/fpimentel/hera/hera_description)

## File structure:
```
|-- hera_description
  |-- config
  |-- doc
  |-- launch
  |-- CMakeLists.txt
  |-- package.xml
  |-- README.md
```

### config:
This folder contains parameters configurations used to visualize and configure the robot navigation.
```
  |-- config
    |-- amcl
      |-- amcl.yaml
    |-- move_base
      |--move_base_params.yaml
      |--costmap_common_params.yaml
      |--costmap_global_params.yaml
      |--costmap_local_params.yaml
      |--local_planner_base_params.yaml
      |--local_planner_dwa_params.yaml
      |--local_planner_eband_params.yaml
      |--local_planner_teb_params.yaml
    |-- rviz
      |-- mapping.rviz
      |-- navigation.rviz
```

### doc
This folder contains files used in this markdown document.
```
  |-- doc
    .
    .
    .
```

### launch:
This folder contains files used to launch the robot using roslaunch in the ROS ecosystem.
they are divided in two categories:
* xml files - for intern use (they are not visible in the roslaunch system).
* launch files - for public use.
```
  |-- launch
    |--localization.xml
    |--navigation.xml
    |--bringup_mapping.launch
    |--bringup_navigation.launch
```
* **bringup_mapping**: Used to start the mapping process of a new environment. Parameters:
  * **robot_model**: (string, default: hera_full) - Robot used. Available in the [hera_description](https://gitlab.com/fpimentel/hera/hera_description) package.
* **bringup_navigation**: Used to start the navigation process. Parameters:
  * **robot_model**: (string, default: hera_full) - Robot used. Available in the [hera_description](https://gitlab.com/fpimentel/hera/hera_description) package.
  * **map_resource**: (string, default: ) - Path to map folder used to navigation. This folder must contain a _pgm_ and a _yaml_ files.
  * **use_fake_localization**: (boolean, default: false) - Used in simulated environment if you want an accurate localization.
    * **true** - Use [fake_localization](http://wiki.ros.org/fake_localization) package.
    * **false** - Use [amcl](http://wiki.ros.org/amcl) package.
  * **global_planner**: (string, default: navfn/NavfnROS) - Global planer used to plan the navigation.
  * **local_planner**: (string, default: eband_local_planner/EBandPlannerROS) - Local planner used to navigate. There are four available:
    * [base_local_planner/TrajectoryPlannerROS](http://wiki.ros.org/base_local_planner)
    * [dwa_local_planner/DWAPlannerROS](http://wiki.ros.org/dwa_local_planner)
    * [eband_local_planner/EBandPlannerROS](http://wiki.ros.org/eband_local_planner)
    * [teb_local_planner/TebLocalPlannerROS](http://wiki.ros.org/teb_local_planner)

<!-- add rqt_reconfigure -->


<!-- https://github.com/zkytony/ROSNavigationGuide/blob/master/main.pdf -->
