# Resume
My markdown resume, to convert it to a pdf with pandoc use this command:

````pandoc resume.md -V geometry:margin=1in -V pagestyle:empty -o resume.pdf````
-o is for output
-V is for variable key:value
without the geometry:margin key:value it ends up with a very large margin.
pagestyle:empty is to avoid line numbers. 

[Download the PDF resume here](https://github.com/freefrancisco/resume/blob/master/resume.pdf)
