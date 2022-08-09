Versions
########

The RoboCup competition is hosted annually, with the competition usually around July.
Additionally, there are regional RoboCup competitions such as the German Open, Asia Pacific, and Japan Open.
The structure of the UDP packets used to communicate with the GameController are versioned, and frequently change with rule changes in SPL.

GameController SPL (GCSPL)
**************************

``gc_spl_master`` is a package in the dev branch, that works with the master branch of `GameController`_ and is useful when developing against the most recent GameController.
**This package is not released** in any of the distros, and is not for use in upcoming competitions.

For each competition, a package named ``gc_spl_{COMPETITION}`` will be split off from ``gc_spl_master`` and be released for all active distros. (eg. ``gc_spl_2022`` for the main RoboCup 2022 Competition)
Packages for regional competitions such as the German Open or RoboCup Asia Pacific, will be named as ``gc_spl_go2022`` and ``gc_spl_ap2022``.

The competition-specific packages will not break API/ABI compatibility throughout their lifetime.

RoboCup GameControl Data (RCGCD)
********************************

The structure of RoboCup GameControl Data is defined in `GameController`_, and has an associated version number.
Every time there is a rule change, the version number is increased and a new package named ``rcgcd_spl_{VERSION_NUMBER}`` (eg. ``rcgcd_spl_14``) will be released for all active ROS2 distros.

RoboCup GameControl Return Data (RCGCRD)
****************************************

Similar to RCGCD, every time there is a new version, a new package named ``rcgcrd_spl_{VERSION_NUMBER}`` will be released (eg. ``rcgcrd_spl_4``).

Supported Distros
*****************

Packages will be released for all active ROS distributions at the time of competition.
The table below lists the current availability of packages under different ROS distros and competitions.

.. list-table:: Package availability
   :widths: 25 25 25 25 25
   :header-rows: 1
   :stub-columns: 1

   * -
     - Foxy
     - Galactic
     - Humble
     - Rolling
   * - gc_spl_2022
     - Yes
     - Yes
     - Yes
     - Yes
   * - gc_spl_master
     - No
     - No
     - No
     - No

.. _GameController: https://github.com/RoboCup-SPL/GameController
