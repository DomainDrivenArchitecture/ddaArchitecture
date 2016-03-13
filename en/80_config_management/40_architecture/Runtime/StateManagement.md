#State Management

Different states will sprawl across the modules if not governed. So in DDA, state is allowed only in one place - in the dda-base-crate. 

Therefore dda-base-crate reads and writes a state file per module where a module can manage its state.  