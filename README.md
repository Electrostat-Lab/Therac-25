# <img src=https://github.com/Electrostat-Lab/Therac-25/blob/master/assets/radiation-nuclear-svgrepo-com.svg height=60 width=60/> Therac-25
**Preface**: This is a detailed scientific guide that analyze the operation of the Therac series devices, a radiation therapy series designed, developed, and assembled by the affiliates of Compagnie générale de radiologie (CGR) of France and the Atomic Energy of Canda Limited (AECL) Corps. The document is based on Leveson's report files that investigate the sequential failures in much more detail, however the focus here is mainly to use the mathematical and programming models to analyze the issues explained in Levenson's documents.

## Outline:
* History of the _Therac Series Radiation Therapy_ devices.
* **Device Engineering:** Single-pass and Double-pass operating modes.
* **Physics:** Electron operating mode.
* **Physics:** X-ray operating mode.
* **Device Engineering:** Double-pass Switching Automata.
* **Device Engineering:** A component diagram for the original desing of Therac-25, and its Therac-6 and Therac-20 counterparts.
* **Hardware Engineering:** Fuse protection mechanisms and their automata models.
* **Software Engineering:** Basic principles of concurrency.
* **Software Engineering:** Concurrent Automatas (Conditional locked states using feedback transitions).
* **Software Engineering:** Concurrency issues with the previous versions of Therac-25.
* **Software Engineering:** Concurrency issues with Therac-25.
* **Mathematical Modelling:** A deterministic machine modelling the normal automata and the catastrophic automata.
* **Complex Systems Modelling:** An accident causation model (i.e., Swiss Cheese Model) explaining the alignment of active system failures with latent failures, and other humanitarian factors.
* **Software Engineering:** A summary of the AECL patches to the device, and their eventual result.
* **Complex Sytems:** The aftermath.
* **Hardware-Software Co-design:** A simulation to the normal automata and the catastrophic automata that has led to this imminent failure.
* **Hardware-Software Co-design:** Suggested pathces to this simulation.
* **Hardware-Software Co-design:** Nowadays' preventions of these catastrophes.

## References:
* [Leveson, N. G., & Turner, C. S. (1993). An investigation of the Therac-25 accidents, ACM DL](https://dl.acm.org/doi/10.1109/MC.1993.274940)
* [Therac-25 Update](http://sunnyday.mit.edu/papers/therac.pdf)
* [Therac-25 Wikipedia page.](https://en.wikipedia.org/wiki/Therac-25)
* [Introduction to Theory of Computation]()
* [Guide to Discrete Mathematics]()
* [Switching and Finite Automata Theory, Cambridge Press]()
* [Practical Electronics for Inventors, McGrawHill]()
* [Electronic Devices and Circuit Theory, Robert L. Boylestad - Louis Nashelsky, Pearson]()
* [Advances in Radiation Therapy - Cancer and Treatment Research, Steven T. Rosen, Springer]()
