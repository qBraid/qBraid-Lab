.. _lab_pricing:

:orphan:

Pricing
---------

Each qBraid credit is worth $.01 USD, so a quantum job costing $3.80 would subtract 380 credits from your qBraid balance. Credits can be `purchased <https://account.qbraid.com/billing.>`_
from your account page, or `redeemed <account.html#add-access-key>`_ using an access key. You can check your current credit balance on your `account page <https://account.qbraid.com/billing.>`_,


Quantum Computers (on-demand)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

There are two pricing components for on-demand use of a quantum computer, or quantum processing unit (QPU),
on qBraid: a per-shot fee and a per-task fee.

A shot is a single execution of a quantum algorithm on a QPU. For example, a shot is a single pass through
each stage of a complete quantum circuit on a gate-based QPU from IonQ, Rigetti, or OQC. or the time evolution
of a Hamiltonian on a QPU from QuEra. A task is a sequence of repeated shots based on the same circuit design
or Hamiltonian. You define how many shots you want included in a task when you submit the task to Amazon Braket.

Per-task pricing is the same across all QPUs. The per-shot pricing depends on the type of QPU used.
For gate-based QPUs, the per-shot price is not affected by the number or type of gates used in a quantum circuit.
Note that the use of error mitigation on IonQ's Aria QPU requires a minimum of 2,500 shots per task.

.. list-table::
   :widths: 25 25 25 25
   :header-rows: 1

   * - Hardware Provider
     - QPU Family
     - Per-task price
     - Per-shot price
   * - IonQ
     - Harmony
     - 30 credits
     - 1 credit
   * - IonQ
     - Aria
     - 30 credits
     - 3 credits
   * - OQC
     - Lucy
     - 30 credits
     - 0.035 credits
   * - QuEra
     - Aquila
     - 30 credits
     - 1 credit
   * - Rigetti
     - Aspen-M-3
     - 30 credits
     - 0.035 credits
   * - IQM
     - Garnet
     - 30 credits
     - 0.145 credits


Quantum Circuit Simulators
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Verify your circuits using a simulator before you run it on a QPU, so you can fine-tune your circuit without
incurring charges for QPU usage. Although the results from running the circuit on a simulator may not be identical
to the results from running the circuit on a QPU, you can identify coding errors or configuration issues using a simulator.

.. list-table::
   :widths: 25 25 25
   :header-rows: 1

   * - Provider
     - Simulator
     - Per-minute price
   * - AWS
     - DM1
     - 7.5 credits
   * - AWS
     - SV1
     - 7.5 credits
   * - AWS
     - TN1
     - 7.5 credits


CPUs + GPUs
^^^^^^^^^^^^^

qBraid Lab classical compute pay-as-you go pricing. Instances marked with an asterisk (*) are available only via `subscription <https://www.qbraid.com/pricing>`_.

.. list-table::
   :widths: 25 25 25 25 25
   :header-rows: 1

   * - Instance
     - CPU
     - GPU
     - RAM
     - Per-minute price
   * - Free
     - 2 x86_64
     - 0
     - 4G
     - 0.00 credits
   * - Standard*
     - 4 x86_64
     - 0
     - 8G
     - 0.00 credits
   * - Pro*
     - 10 x86_64
     - 0
     - 59G
     - 0.00 credits
   * - GPU
     - 4 x86_64
     - 1 NVIDIA V100
     - 25G
     - 4.13 credits

.. seealso::

  - `qBraid Lab GPUs <gpu.html>`_
  - `Compute Manager <compute_manager.html>`_
  - `Quantum Jobs <quantum_jobs.html>`_
  - `Quantum Devices <quantum_devices.html>`_
