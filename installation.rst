Installation
############

To install the packages, do one of the following:

* a `Binary Installation`_
* a `Source Installation`_

Binary Installation
*******************

Binary installation is available for all active distros.

Source your ROS installation, then run:

.. code-block:: console

  sudo apt update
  sudo apt install ros-${ROS_DISTRO}-game-controller-spl

If this method does not work for your platform, perform the `Source Installation`_ instead.

Source Installation
*******************

Cloning repositories
====================

Source your ROS2 installation, then in your ROS2 workspace, run:

.. code-block:: sh

   git clone https://github.com/ros-sports/game_controller_spl.git src/game_controller_spl --branch ${ROS_DISTRO}

Building
========

In your ROS2 workspace, install the dependencies:

.. code-block:: console

   rosdep install --from-paths src -i

Build the package:

.. code-block:: console

   colcon build
