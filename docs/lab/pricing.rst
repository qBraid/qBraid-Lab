.. _lab_pricing:

Pricing
---------

There are two pricing components for on-demand use of a quantum computer, or quantum processing unit (QPU),
on Amazon Braket: a per-shot fee and a per-task fee.

A shot is a single execution of a quantum algorithm on a QPU. For example, a shot is a single pass through
each stage of a complete quantum circuit on a gate-based QPU from IonQ, Rigetti, or OQC. or the time evolution
of a Hamiltonian on a QPU from QuEra. A task is a sequence of repeated shots based on the same circuit design
or Hamiltonian. You define how many shots you want included in a task when you submit the task to Amazon Braket.

Per-task pricing is the same across all QPUs. The per-shot pricing depends on the type of QPU used.
For gate-based QPUs, the per-shot price is not affected by the number or type of gates used in a quantum circuit.
Note that the use of error mitigation on IonQ's Aria QPU requires a minimum of 2,500 shots per task.

Quantum Computers (on-demand)
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

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
     - Aspen-M
     - 30 credits
     - 0.035 credits
