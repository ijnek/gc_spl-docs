Tutorial
########

First, you should run the gc_spl node that handles communication with the SPL GameController.
From the tabs below, select which `GameController`_ branch/tag you are using:

.. tabs::

   .. group-tab:: 2022

      .. code-block:: sh

         ros2 run gc_spl_2022 gc_spl

   .. group-tab:: master

      .. code-block:: sh

         ros2 run gc_spl_master gc_spl

List the topics:

.. code-block:: sh

   ros2 topic list -t

You should see the following amongst the listed topics:

.. tabs::

   .. group-tab:: 2022

      .. code-block:: sh

         /gc/data [rcgcd_spl_14/msg/RCGCD]
         /gc/return_data [rcgcrd_spl_4/msg/RCGCRD]

   .. group-tab:: master

         /gc/data [rcgcd_spl_14/msg/RCGCD]
         /gc/return_data [rcgcrd_spl_4/msg/RCGCRD]

Echoing data from GameController
================================

To access GameController data from within your own node, simply subscribe to the ``/gc/data`` topic.

The gc_spl node receives UDP packets from the GameController, converts them to ROS msgs and publishes them as ROS topics.
``/gc/data`` is the topic that it publishes to.

Bring up a GameController instance, following instructions in the `GameController`_ README:

.. image:: images/GameController.png
   :align: center

Use the following command to echo the ``/gc/data`` topic:

.. code-block:: sh

   ros2 topic echo /gc/data

You should see the data from the GameController being echoed similar to the following:

.. code-block:: sh

   ---
   packet_number: 11
   players_per_team: 6
   competition_phase: 0
   competition_type: 0
   game_phase: 0
   state: 0
   set_play: 0
   first_half: 1
   kicking_team: 18
   secs_remaining: 600
   secondary_time: 0
   teams:
   - team_number: 18
   team_colour: 2
   score: 0
   penalty_shot: 0
   single_shots: 0
   message_budget: 1200
   players:
   - penalty: 0
      secs_till_unpenalised: 0
   - penalty: 0
      secs_till_unpenalised: 0
   - penalty: 0
      secs_till_unpenalised: 0
   - penalty: 0
      secs_till_unpenalised: 0
   - penalty: 0
      secs_till_unpenalised: 0
   - penalty: 14
      secs_till_unpenalised: 0
   - penalty: 14
      secs_till_unpenalised: 0
   - team_number: 0
   team_colour: 1
   score: 0
   penalty_shot: 0
   single_shots: 0
   message_budget: 1200
   players:
   - penalty: 0
      secs_till_unpenalised: 0
   - penalty: 0
      secs_till_unpenalised: 0
   - penalty: 0
      secs_till_unpenalised: 0
   - penalty: 0
      secs_till_unpenalised: 0
   - penalty: 0
      secs_till_unpenalised: 0
   - penalty: 14
      secs_till_unpenalised: 0
   - penalty: 14
      secs_till_unpenalised: 0
   ---

Sending data to GameController
==============================

To send data from within your own node, simply publish to the ``/gc/return_data`` topic.

The gc_spl node listens on the ``/gc/return_data`` topic, converts them to UDP packets and sends them to the GameController.

Bring up a GameController instance with one team set to team 18 (rUNSWift), following instructions in the `GameController`_ README:

.. image:: images/GameController.png
   :align: center

Use the following command to publish a msg to the topic:

.. code-block:: bash

   ros2 topic pub --once /gc/return_data rcgcrd_spl_4/msg/RCGCRD "{player_num: 2, team_num: 18}"

You can see that the GameController is reporting a green light for team 18's player 2, indicating a message has been received recently.

.. image:: images/GameController-with-active-player.png
   :align: center

.. _GameController: https://github.com/RoboCup-SPL/GameController


