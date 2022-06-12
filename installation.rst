Installation
############

.. warning::

   This package targets **ROS2 Foxy onwards**. It won't compile on all ROS1 and older ROS2 distros.

Source Installation
*******************

.. note::

   Instructions here assume that you have and are in a ROS2 workspace's root directory.

Cloning repositories
====================

In your ROS2 workspace, clone the repository:

.. tabs::

   .. tab:: Foxy / Galactic

      .. code-block:: console

         git clone https://github.com/ros-sports/gc_spl.git src/gc_spl --branch=galactic

   .. tab:: Humble / Rolling

      .. code-block:: console

         git clone https://github.com/ros-sports/gc_spl.git src/gc_spl

Building
========

In your ROS2 workspace, install the dependencies:

.. code-block:: console

   rosdep install --from-paths src

Build the package:

.. code-block:: console

   colcon build
