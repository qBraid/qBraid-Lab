:orphan:

.. _lab_intel:

Intel® Quantum SDK
====================

Intel Quantum SDK is a C++ based API that allows users to write software
targeted for Intel quantum hardware. It is available as a pre-installed
environment on qBraid Lab, and is free to access for all users:

.. image:: ../_static/cpp/UPDATE_ME_PLEASE.png
    :align: center
    :width: 90%
    :alt: Intel® Quantum SDK
    :target: javascript:void(0);

|

The Intel Quantum SDK is a C++ software engineering advance that provides
quantum computing integration with established professional software projects
operating at scale. The Intel Quantum SDK is natively designed to interoperate
with the Python software environment. The most straightforward approach to using the
Intel Quantum SDK is to provide a quantum kernel as C++ source in your Python
environment and expose that kernel for operation as a shared object.

Your first C++ Quantum Kernel
-----------------------------

We will create and manipulate a quantum kernal running on the
Intel Quantum Simulator directly in your notebook. This first kernel will demonstrate
a simple quantum Bell state as a common and familiar quantum computing system.

.. code-block:: python

    import intelqsdk.cbindings as iqsdk

    iqc = "/opt/.qbraid/environments/intel_dk7c2g/intel-quantum-compiler"

    num_qubits = 2

    # Create the Python parameterized 2 qubit C++ Bell state source
    Bell_source = f"""
    #include <clang/Quantum/quintrinsics.h>

    // Establish the classical and quantum kernel variables
    cbit c[{num_qubits}];
    qbit q[{num_qubits}];

    // Our Bell state Quantum Kernel
    quantum_kernel void bell()
    {
        H(q[0]);
        CNOT(q[0], q[1]);
        MeasZ(q[0], c[0]);
        MeasZ(q[1], c[1]);
    }
    """

    # Create the Intel Quantum SDK source file bell.cpp
    with open("bell.cpp", "w", encoding="utf-8") as output_file:
        for line in Bell_source:
            print(line, file=output_file)

    # Generate the Intel Quantum SDK shared object file bell.so
    iqsdk.compileProgram(iqc, "bell.cpp", "-s")

    # Expose and label the Intel Quantum SDK shared object as "my_bell"
    iqsdk.loadSdk("bell.so", "my_bell")

    # Setup the Intel Quantum Simulator to execute the quantum kernel
    iqs_config = iqsdk.IqsConfig()
    iqs_config.num_qubits = num_qubits
    iqs_config.simulation_type = "noiseless"
    iqs_device = iqsdk.FullStateSimulator(iqs_config)
    iqs_device.ready()

    # Invoke the quantum_kernel "bell" defined in the C++ source above
    iqsdk.callCppFunction("bell", "my_bell")

    # Establish references to the quntum kernel qubits
    qbit_ref = iqsdk.RefVec()
    for i in range(num_qubits):
        qbit_ref.append( iqsdk.QbitRef("q", i, "my_bell").get_ref() )

    # Print the probabilities of the quantum system
    probabilities = iqs_device.getProbabilities(qbit_ref)
    iqsdk.FullStateSimulator.displayProbabilities(probabilities, qbit_ref)

    # Printing probability register of size 4
    # |00>    : 0                             |10>    : 0
    # |01>    : 0                             |11>    : 1


OpenQASM Support
------------------

Intel(R) Quantum SDK provides a source-to-source converter which takes OpenQASM
code and converts it into C++ for use with the Intel(R) Quantum SDK. This
converter requires Python >= 3.10. Currently, it only processes OpenQASM 2.0
compliant code as described by the Open Quantum Assembly Language paper:
`arXiv:1707.03429 <https://arxiv.org/abs/1707.03429>`_.

To translate the OpenQASM file to C++ file, you can run the compiler script
with -B flag to generate the corresponding ``quantum_kernel`` functions in C++
format.

.. code-block:: bash

    $ intel-quantum-compiler -B example.qasm

.. raw:: html

    <h3 style="color:#D30982;">qBraid Instructions</h3>

On qBraid, the compiler is located in the Intel environment directory.

.. code-block:: bash

    /opt/.qbraid/environments/intel_dk7c2g/intel-quantum-compiler

This environment path can also be found from the qBraid CLI via

.. code-block:: bash

    $ qbraid envs list
    # installed environments:
    #
    default                  jobs  /opt/.qbraid/environments/qbraid_000000
    intel                          /opt/.qbraid/environments/intel_dk7c2g
    ...

.. note::

    For convenience when working with the terminal, consider appending the Intel®
    Quantum SDK path to your shell's environment:

    ..

        ``export PATH=$PATH:/opt/.qbraid/environments/intel_dk7c2g``

Python Interface
------------------

The Python Interface provides users a way to run the Intel® Quantum SDK using
Python 3, through the **intelqsdk.cbindings** library. There are two modes for
interacting with Python:

1. Write quantum circuits in OpenQASM 2.0 -- write a quantum circuit to a file,
   and convert that to a ``.cpp`` file that has ``quantum_kernel`` functions,
   compile, and use the ``intelqsdk.cbindings`` library to run the
   ``quantum_kernel`` functions and call APIs, all from within Python.

2. Write ``quantum_kernel`` functions in C++, compile to a ``.so`` file, and
   call APIs from Python.

.. raw:: html

    <h3 style="color:#D30982;">qBraid Instructions</h3>

The Python interface is installed in the Intel® Quantum SDK environment
in qBraid. Before running this notebook, make sure that you have activated
the Intel® Quantum SDK environment, and have selected the ``Python
[IQSDK]`` kernel in the top-right of your menu bar. To run your Python
scripts using the **intelqsdk.cbindings** library, you can use the qBraid CLI

.. code-block:: bash

    $ qbraid envs activate intel

or call your script with the full python3 path at

.. code-block:: bash

    $ /opt/.qbraid/environments/intel_dk7c2g/virtualenv/bin/python3

Python via OpenQASM
^^^^^^^^^^^^^^^^^^^^

**Step 1:** Write quantum programs in OpenQASM2.0 or alternatively, transpile
your python program into OpenQASM 2.0

You can use your choice of quantum programming package to write your program.
As long as the program can be turned into a qasm file, the Bridge library will
be able to translate it to a C++ source file for the SDK.

**Step 2:** Write your Python script

First, we will construct a circuit using Qiskit, and convert it to an OpenQASM
string:

.. code-block:: python

    from qiskit import QuantumCircuit

    # Create bell circuit with measurement over both qubits
    circuit = QuantumCircuit(2, 2)
    circuit.h(0)
    circuit.cx(0, 1)
    circuit.measure([0, 1], [0, 1])

    input_qasm = circuit.qasm()

We could have also read directly from a local ``.qasm`` file:

.. code-block:: python

    with open("example.qasm", "r", encoding="utf-8") as input_file:
        input_qasm: str = input_file.read()


Either way, we now have an example OpenQASM string that looks as follows:

.. code-block:: python

    >>> print(input_qasm)
    OPENQASM 2.0;
    include "qelib1.inc";
    qreg q[2];
    creg c[2];
    h q[0];
    cx q[0],q[1];
    measure q[0] -> c[0];
    measure q[1] -> c[1];


Next, we will use Bridge to translate the OpenQASM file to C++,

.. code-block:: python

    from openqasm_bridge.v2 import translate

    kernel = circuit.name # assuming generated from qiskit

    translated: list[str] = translate(input_qasm, kernel_name=kernel)

    with open("example.cpp", "w", encoding="utf-8") as output_file:
        for line in translated:
            print(line, file=output_file)


and compile the translated C++ code using the qBraid Intel® Quantum SDK environment compiler path:

.. code-block:: python

    import intelqsdk.cbindings as iqsdk

    compiler_path = "/opt/.qbraid/environments/intel_dk7c2g/intel-quantum-compiler"

    iqsdk.compileProgram(compiler_path, "example.cpp", "-s")
    # Generates output IR file example.ll and quantum object file example.so

From here, we can start calling APIs to set up the simulator and run the quantum program. For example:

.. code-block:: python

    import intelqsdk.cbindings as iqsdk
    iqsdk.loadSdk("example.so", "my_bell")

    num_qubits = circuit.num_qubits # assuming generated from qiskit

    iqs_config = iqsdk.IqsConfig()
    iqs_config.num_qubits = num_qubits
    iqs_config.simulation_type = "noiseless"

    iqs_device = iqsdk.FullStateSimulator(iqs_config)
    iqs_device.ready()

    iqsdk.callCppFunction(kernel, "my_bell")

    qbit_ref = iqsdk.RefVec()

    for i in range(num_qubits):
        qbit_ref.append( iqsdk.QbitRef("q", i, "my_bell").get_ref() )

    probabilities = iqs_device.getProbabilities(qbit_ref)
    iqsdk.FullStateSimulator.displayProbabilities(probabilities, qbit_ref)
    # Printing probability register of size 4
    # |00>    : 0                             |10>    : 0
    # |01>    : 0                             |11>    : 1
