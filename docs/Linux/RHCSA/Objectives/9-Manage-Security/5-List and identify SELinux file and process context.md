To see current context, use `-Z`
- ![[Pasted image 20220911081608.png]]
	- For the exam, we're concerned with `_t`

`semanage fcontext` to set file context label
`semanage fcontext -a` - Sets a new context label
`semanage fcontext -m` - Modifies an existing context label 
`semanage fcontext -l -C` - This shows only settings that have changes in the current policy


>[!TIP] When using fcontext, this only writes to the SELinix Policy. But, we need it written to the filesystem. To do that, you must use `restorecon`.


