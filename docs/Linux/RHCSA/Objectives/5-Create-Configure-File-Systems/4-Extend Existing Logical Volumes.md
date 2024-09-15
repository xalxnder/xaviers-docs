1. [[Logical Volumes#Create The Partition]]
2. Run `vgs` to verify
3. As we can see, we no space left on our volume group
	1. ![[Pasted image 20220909065605.png]]
4. Once you have your partition use vgextend on it. 
	1. ![[Pasted image 20220909065448.png]]
5. Run vgs to see your `VFREE`. This will be uses in the final command	
5. Finally, run lvextend:
	1. ![[Pasted image 20220909065711.png]]