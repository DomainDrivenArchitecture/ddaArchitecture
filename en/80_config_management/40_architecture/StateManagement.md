#State Management

Different states will sprawl across the modules if not governed. So in DDA, state is allowed only in one place - in /home/pallet/state on target machines. 

The dda-base-crate will do the handling - it reads and writes a state file per module where a module can manage its state.  