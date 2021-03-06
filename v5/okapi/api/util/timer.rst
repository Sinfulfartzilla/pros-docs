=====
Timer
=====

.. contents:: :local:

okapi::Timer
============

A timing related utility class.

Constructor(s)
--------------

.. tabs ::
   .. tab :: Prototype
      .. highlight:: cpp
      ::

        Timer()

----

Methods
-------

getDt
~~~~~~

Returns the time passed in ms since the previous call of this function.

.. tabs ::
   .. tab :: Prototype
      .. highlight:: cpp
      ::

        virtual std::uint32_t getDt()

**Returns:** The time passed in ms since the previous call of this function.

----

getStartingTime
~~~~~~~~~~~~~~~

Returns the time the timer was first constructed.

.. tabs ::
   .. tab :: Prototype
      .. highlight:: cpp
      ::

        virtual std::uint32_t getStartingTime() const

**Returns:** The time the timer was first constructed.

----

getDtFromStart
~~~~~~~~~~~~~~

Returns the time since the timer was first constructed.

.. tabs ::
   .. tab :: Prototype
      .. highlight:: cpp
      ::

        virtual std::uint32_t getDtFromStart() const

**Returns:** The time since the timer was first constructed.

----

placeMark
~~~~~~~~~

Place a time marker. Placing another marker will overwrite the previous one.

.. tabs ::
   .. tab :: Prototype
      .. highlight:: cpp
      ::

        virtual void placeMark()

----

placeHardMark
~~~~~~~~~~~~~

Place a hard time marker. Placing another hard marker will not overwrite the previous one; instead, call ``clearHardMark()`` and then place another.

.. tabs ::
   .. tab :: Prototype
      .. highlight:: cpp
      ::

        virtual void placeHardMark()

----

clearHardMark
~~~~~~~~~~~~~

Clears the hard marker.

.. tabs ::
   .. tab :: Prototype
      .. highlight:: cpp
      ::

        virtual std::uint32_t clearHardMark()

**Returns:** The old hard marker.

----

getDtFromMark
~~~~~~~~~~~~~

Returns the time since the time marker.

.. tabs ::
   .. tab :: Prototype
      .. highlight:: cpp
      ::

        virtual std::uint32_t getDtFromMark() const

**Returns:** The time since the time marker.

----

getDtFromHardMark
~~~~~~~~~~~~~~~~~

Returns the time since the hard time marker.

.. tabs ::
   .. tab :: Prototype
      .. highlight:: cpp
      ::

        virtual std::uint32_t getDtFromHardMark() const

**Returns:** The time since the hard time marker.

----

repeat
~~~~~~

Returns ``true`` when the input time period has passed, then resets. Meant to be used in loops to run an action every so many ms without blocking.

.. tabs ::
   .. tab :: Prototype
      .. highlight:: cpp
      ::

        virtual bool repeat(const std::uint32_t ms)

   .. tab :: Example
      .. highlight:: cpp
      ::

        void opcontrol() {
          okapi::Timer timer;
          while (true) {
            if (timer.repeat(100)) {
              // Do something every 100 ms
            }
            pros::delay(10);
          }
        }

============ ===============================================================
 Parameters
============ ===============================================================
 ms           The time period in ms.
============ ===============================================================

**Returns:** ``true`` when the input time period has passed, ``false`` after reading ``true`` until the period has passed again
