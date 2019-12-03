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
