#Modules and building blocks

![architectural overview](../resources/archtectural-overview.png)

There are many crates in the pallet world. In order to get a better overview, we will group these crates into the following groups:

* **core**: There are the pallet-core-crates at the one hand and dda-core-crates on the other hand. dda-core-crates enhances the pure pallet core. Examples of core crates are: Pallet itself, the pallet crate foundation, the dda-configuration-crate or the dda-base-crate containing versioning and state management.
* **operational services**: The operational services are service abstractions like user handling, or ssh handling. Also crosscutting aspects like backup, monitoring, security or provider abstraction are residing in operational services group.
* **base products**: base-product-crates are abstractions for often used and combined products like apache web server, databases or applications servers.
* **app-stack**: app-stack-crates represents the different application stacks, combining all the base products and operational services in order to provide business applications to users.

