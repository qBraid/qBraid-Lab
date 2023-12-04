:orphan:

.. _lab_intel:

Intel® Quantum SDK
====================

Intel Quantum SDK is a C++ based API that allows users to write software targeted for Intel quantum hardware. It is available as a pre-installed
environment on qBraid Lab, and is free to access for all users:

.. image:: ../_static/cpp/cpp_intel.png
    :align: center
    :width: 90%
    :alt: Intel Quantum SDK
    :target: javascript:void(0);

|

OpenQASM Support
------------------

Intel(R) Quantum SDK provides a source-to-source converter which takes OpenQASM code and converts it into C++ for use with the Intel(R) Quantum SDK. This converter requires Python >= 3.7. Currently, it only processes OpenQASM 2.0 compliant code as described by the Open Quantum Assembly Language paper: `arXiv:1707.03429 <https://arxiv.org/abs/1707.03429>`_.

To translate the OpenQASM file to C++ file, you can run the compiler script with -B flag to generate the corresponding ``quantum_kernel`` functions in C++ format.

.. code-block:: bash

    $ ./intel-quantum-compiler -B example.qasm

.. raw:: html

    <h3 style="color:#D30982;">qBraid Instructions</h3> 

On qBraid, the compiler is located in the Intel environment directory.

.. code-block:: bash

    /opt/.qbraid/environments/intel_dk7c2g/intel-quantum-compiler

This environment path can also be found from the qBraid CLI via

.. code-block:: bash

    $ qbraid envs list


Python Interface
------------------

The Python Interface provides users a way to run the Intel(R) Quantum SDK using Python 3, through the **iqsdk** library. There are two modes for interacting with Python:

1. Write quantum circuits in OpenQASM 2.0 -- write a quantum circuit to a file, and convert that to a ``.cpp`` file that has ``quantum_kernel`` functions, compile, and use the ``iqsdk`` library to run the ``quantum_kernel`` functions and call APIs, all from within Python.

2. Write ``quantum_kernel`` functions in C++, compile to a ``.so`` file, and call APIs from Python.

.. raw:: html

    <h3 style="color:#D30982;">qBraid Instructions</h3> 

The Python interface is installed in the Intel(R) Quantum SDK environment in qBraid. Before running this notebook, make sure that you have activated the Intel(R) Quantum SDK environment, and have selected the `Python [IQSDK]` kernel in the top-right of your menu bar. To run your Python scripts using the **iqsdk** library, you can use the qBraid CLI

.. code-block:: bash

    $ qbraid envs activate intel

or call your script with the full python3 path at

.. code-block:: bash

    $ /opt/.qbraid/environments/intel_dk7c2g/pyenv/bin/python3

Python via OpenQASM
^^^^^^^^^^^^^^^^^^^^

**Step 1:** Write quantum programs in OpenQASM2.0 or alternatively, transpile your python program into OpenQASM 2.0

You can use your choice of quantum programming package to write your program. As long as the program can be turned into a qasm file, the Bridge library will be able to translate it to a C++ source file for the SDK.

**Step 2:** Write your Python script

First, we will construct a circuit using Qiskit, and convert it to a qasm string:

.. code-block:: python

    import iqsdk
    from openqasm_bridge.v2 import translate
    from qiskit.circuit.random import random_circuit

    num_qubits = 2
    depth = 2

    circ = random_circuit(num_qubits, depth, measure=True)

    input_string = circ.qasm()

    print(input_string)


.. code-block::

    OPENQASM 2.0;
    include "qelib1.inc";
    qreg q[2];
    creg c[2];
    u2(5.203871548363386,2.3186480813640444) q[0];
    ry(2.194897794397605) q[1];
    u(0.8036803530101524,3.796981478934022,2.161748825203784) q[0];
    sdg q[1];
    measure q[0] -> c[0];
    measure q[1] -> c[1];


Alternatively, we could have read directly from a local ``.qasm`` file:

.. code-block:: python

    with open('example.qasm', 'r', encoding='utf8') as input_file:
        input_string: str = input_file.read()

Next, we will use Bridge to translate the OpenQASM file to C++, and compile the
translated C++ code using the qBraid Intel Quantum SDK environment compiler path:

.. code-block:: python

    kernel = "my_kernel"

    translated: list[str] = translate(input_string, kernel_name=kernel)

    with open('example.cpp', 'w', encoding='utf8') as output_file:
        for line in translated:
            output_file.write(line + "\n")

    compiler_path = "/opt/.qbraid/environments/intel_dk7c2g/intel-quantum-compiler"
    iqsdk.compileProgram(compiler_path, "example.cpp", "-s")

.. code-block::

    ===============================================================================
                        Intel(R) Quantum SDK (V1.0)
    ===============================================================================
    Processing source file:
    /home/jovyan/qbraid-tutorials/intel_tutorials/qbraid-python-example/example.cpp 
    -------------------------------------------------------------------------------
    Intermediate representation (IR) output file: 
    /home/jovyan/qbraid-tutorials/intel_tutorials/qbraid-python-example/example.ll
    -------------------------------------------------------------------------------
    Transforming IR...
    Validating and processing quantum kernels...
    Optimizing using option 0...
    Finalizing quantum IR...
    -------------------------------------------------------------------------------
    Generating quantum object file...
    Compiling and linking to shared object...
    Final shared object: 
    /home/jovyan/qbraid-tutorials/intel_tutorials/qbraid-python-example/example.so
    -------------------------------------------------------------------------------

From here, we can start calling APIs to set up the simulator and run the quantum program. For example:

.. code-block:: python

    iqs_config = iqsdk.IqsConfig()
    iqs_config.num_qubits = num_qubits
    iqs_config.simulation_type = "noiseless"
    iqs_device = iqsdk.FullStateSimulator(iqs_config)
    iqs_device.ready()
    iqsdk.callCppFunction(kernel)
    qbit_ref = iqsdk.RefVec()
    for i in range(num_qubits):
        qbit_ref.append(iqsdk.QbitRef("q", i).get_ref())
    probabilities = iqs_device.getProbabilities(qbit_ref)
    iqsdk.FullStateSimulator.displayProbabilities(probabilities, qbit_ref)

.. code-block::

    Printing probability register of size 4
    |00>    : 0                             |10>    : 1                             
    |01>    : 0                             |11>    : 0