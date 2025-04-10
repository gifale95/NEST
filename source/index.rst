Welcome to NEST Documentation
============================

.. .. image:: static/nest_logo.png
   :width: 300
   :alt: NEST Logo

**Neural Encoding Simulation Toolkit (NEST)** is a Python package that provides trained encoding models of the brain that you can use to generate accurate in silico neural responses to stimuli of your choice.

In silico neural responses from encoding models increasingly resemble in vivo responses recorded from real brains, enabling the novel research paradigm of in silico neuroscience. These simulated responses are quick and cheap to generate, allowing researchers to explore and test scientific hypotheses across vastly larger solution spaces than possible with traditional methods.

Novel findings from large-scale in silico experimentation can be validated through targeted small-scale in vivo data collection, optimizing research resources. This approach scales beyond what is possible with in vivo data alone and democratizes research across groups with diverse data collection infrastructure and resources.

----

Contents
-------

.. toctree::
   :maxdepth: 1
   :caption: Getting Started

   installation
   Quickstart

.. toctree::
   :maxdepth: 1
   :caption: Tutorials
   
   tutorials/Adding_New_Models_to_Nest

.. toctree::
   :maxdepth: 2
   :caption: Models
   
   models/overview
   models/fmri_nsd_fwrf.rst
   models/eeg_things_eeg_2_vit_b_32.rst

.. toctree::
   :maxdepth: 1
   :caption: About
   
   about/terms_and_conditions
   about/citation

----

Quick Start
----------

Install NEST using pip:

.. code-block:: bash

   pip install -U git+https://github.com/gifale95/NEST.git

Generate in silico fMRI responses:

.. code-block:: python

   from nest import NEST
   
   # Initialize NEST
   nest = NEST("/path/to/nest_dir")
   
   # Get an encoding model
   model = nest.get_encoding_model("fmri_nsd_fwrf", subject=1, roi="V1")
   
   # Generate responses to stimuli
   import numpy as np
   stimuli = np.random.randint(0, 255, (10, 3, 224, 224), dtype=np.uint8)
   responses = nest.encode(model, stimuli)
   
   print(f"Generated responses shape: {responses.shape}")