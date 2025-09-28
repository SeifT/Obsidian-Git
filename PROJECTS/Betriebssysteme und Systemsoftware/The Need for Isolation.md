Some operations are critical and could break the system if done improperly:
- Modify the state of a device
	- e.g., modify the state of the microphone LED to make it look muted when it is not
	- e.g., make a USB drive read-only/writable
- Access restricted memory areas
	- e.g., modify a variwable from another program
	- e.g., read private data – passwords – from other programs


==The operating system needs to isolate these operations to make the system safe and secure!==
