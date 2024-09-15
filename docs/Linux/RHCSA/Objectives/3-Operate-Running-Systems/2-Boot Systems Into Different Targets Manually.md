### Booting Into a Specific Target 

How would you boot into a specific target?
- On theGrub 2 boot prompt, use `systemctl.unit=xxx.target` to boot into a specific target. 
	- ![[Pasted image 20220821143355.png|700]]



- How would you change between targets on a running system?
	- systemctl isolate xxx.target