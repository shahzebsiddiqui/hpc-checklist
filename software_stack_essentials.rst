Software Stack Management
==========================

When starting out with Software Stack consider using one or more build frameworks and a module tool when designing your stack.

Build Frameworks
-----------------
- [ ] EasyBuild - http://easybuild.rtfd.io/
- [ ] Spack - https://spack.readthedocs.io/
- [ ] OpenHPC - https://openhpc.community/
- [ ] Anaconda - https://www.anaconda.com/

Module Tools
--------------

- [ ] Lmod - https://lmod.readthedocs.io/
- [ ] environment-modules - https://modules.readthedocs.io/en/latest/

Pre Reqs
--------

- [ ] Select a shared file system to host your software stack. 
- [ ] Select a service account to build your stack or use a shared unix group 
- [ ] Determine if cluster is homogeneous or heterogeneous. Run ``lscpu | grep -i Model`` and view Model Number. Consider running this cluster wide. For intel architecture see https://software.intel.com/en-us/articles/intel-architecture-and-processor-identification-with-cpuid-model-and-family-numbers
- [ ] Ensure all compute nodes and head nodes have same OS release. If you have ``clush`` you can run ``clush -b -a lsb_release -r``
- [ ] Ensure all nodes have same kernel release ``clush -b -a uname -r``

Getting Started
-----------------

When building software stack, consider releasing software stack once per year or twice per year. Whatever works for your site. **DO NOT PUT ALL SOFTWARE IN ONE MONOLITHIC STACK (i.e 10^5 or 10^6) modules** 

Root of software stack can be set as follows:
  
- Easybuild: /nfs/easybuild/YYYY/$ARCH/$OS/$OSVER
- Spack: /nfs/spack/YYYY/$ARCH/$OS/$OSVER

This format classifies the software stack version which can be dated by year (**YYYY**) and **$ARCH**, **$OS**, **$OSVER** will
specify the architecture, operating system and version used when building stack. 

Consider hiding the software stack by a module, lets say Easybuild and Spack stacks for 2018, 2019, 2020 can be ``eb/2018``, ``eb/2019``, ``eb/2020``, ``spack/2018``, ``spack/2019``, ``spack/2020``.

The content of these modules will just set ``MODULEPATH`` to the root of the software stack (assume its ``/nfs/easybuild/2020/Skylake/centos/7.6``), then content of module file ``eb/2020.lua`` can be::

  prepend_path("MODULEPATH","/nfs/easybuild/2020/Skylake/centos/7.6")
  
Consider storing these wrapper modules (``eb/YYYY``, and ``spack/YYYY``) in a separate directory in shared file system. For example store them in ``/nfs/modulefiles`` 
