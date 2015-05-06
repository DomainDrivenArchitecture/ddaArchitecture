#### Requirements as a key element (2.)
Requirements are the key elements in the system scope. Nearly all elements refer to single requirements. With this kind of reference each of the described changes will cause only a local refactoring. 
The system-vision is the only exception, as I suppose the system vision to be stable enough for being referenced.
The requirements are described at a maximum level of abstraction to succeed with this balancing act concerning the system overview.
Requirements have the following characteristics:
1. They can clearly be identified and referenced (characterized by the stereotype <<entity>>).
2. They are individually version-numbered (characterized by the stereotype <<versionable>>). As versionable objects, requirements are implicitly changeable, too. Date of change and author will be documented.
3. Title: Besides the ID, requirements also have a title. According to experience, the title often changes and is therefore not used for referencing. 
4. State: In this case the distinction between [premature, mature, deprecated] is sufficient.
5. Optionally, the goodwill can put on record on the requirement level. This is useful for a prioritisation of requirements that is independent from costs.

The following types of requirements can typically be distinguished:
