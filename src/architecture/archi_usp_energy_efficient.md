# Energy Efficiency

A high degree of energy-efficiency gains is embedded in the federated IT cloud technology itself. We were able to incorporate many efficiency-gaining measures:
- The biggest saving lies in the fact that the Zero-OS operating system has been created from scratch (only Linux kernel remains), thereby removing many layers of complexity compared to other operating systems, resulting mainly in a multifactor optimization. Examples of the way layers are removed compared to classic operating systems:
   
  - All is running under the same Operating System in containers, no need for OS activity linked to a Virtual Machine (which makes up big part of cloud energy consumption).
  - In general, a lot of abstraction layers and context switching degrades substantially the efficiency and performance of a system. As a consequence, cost of operation increases and energy efficiency decreases drastically. By rebuilding the operating system from scratch, many abstraction layers could be removed.
  - All data is encrypted at the location of its creation before it leaves the container, so once it exits the node, data can’t be exploited by hackers. By doing this, the need for additional security layers disappears
- The ability to have very small cloud nodes makes the density of infrastructure far lower, resulting in a lower need of cooling infrastructure.
- Unused disks are powered down in an automated way.
- Bringing cloud capacity to the edge reduces substantially the load on the network, simply by
reducing the distances that data need to traverse. A cellular phone base station near a local community, a school, or even a smart TV box, available in about every household, can host a TF node. This way a very decentralized grid is created. By doing so, all data storage, compute capacity and containerized applications are available within a stone’s throw of the end consumer instead of sending data around the globe before it arrives at its destination. See also the big trend towards MEC (Mobile Edge Clouds).
- We plan to develop a system to manage the remote shutdown of unused nodes, saving more energy (consumption will be limited to 10W even though hardware nodes remain available).