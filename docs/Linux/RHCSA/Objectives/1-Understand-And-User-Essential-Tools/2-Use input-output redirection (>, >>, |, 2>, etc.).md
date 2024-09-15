-   > (same as 1>) - Redirects STDOUT. If redirection is to a file, the current contents of
`# ls -al /tmp > /root/output.log`
-   >> (same as 1>>) - Redirects STDOUT. If output is written to a file, the output is
`# ls -al /usr >> /root/output.log`
-   2> - Redirects STDERR
`somerandomcommand 2>error.txt`
-   2>&1 - Redirects STDERR to the same destination as STDOUT. Notice that this has to be used in combination with normal output redirection,
` ls whuhiu > errout 2>&1`.
-   < (same as 0<) - Redirects STDIN.