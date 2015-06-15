============
Stack Status
============

Stacks and resources have a state and a status as described in the lists
that follow:

State:

-  INIT – (Resources only) The resource has not been provisioned.

-  CREATE – The stack/resource is new.

-  UPDATE – The stack/resource is changed.

-  DELETE – The stack/resource is deleted.

-  ROLLBACK – A previously failed change is being reverted.

-  ADOPT – The stack/resource is adopted.

-  CHECK – The stack/resource health is checked.

-  SUSPEND – (Stacks only) The stack is suspended.

-  RESUME – (Stacks only) The stack is resumed.

Status:

-  IN-PROGRESS – The operation is in progress.

-  COMPLETE – The operation is compete.

-  FAILED – The operation failed.

So, if you create a new stack and something goes wrong, your stack would
be CREATE FAILED. One or more resources of that stack may be in the
following states:

-  INIT COMPLETE

-  CREATE FAILED

-  CREATE COMPLETE
