FYP-Template
============

Unofficial template for making a Final Year Project (FYP) at Brunel University. This is still a `work-in-progress` (WIP) and may require a little bit of configuring in order to get it to fully function.

Requirements
------------

You'll need a TeX system installed 

I used these on my `Windows 7` installation:
* TexMaker (Basically this is your TeX IDE where you'll write up your report)
* MiKTeX (You'll need a TeX engine to be able to compile your `.tex` documents)
	* BibTex (Part of MiKTeX)
	* PdfLaTeX (Part of MiKTeX)
* JabRef (A very good program to handle the `biblio.bib` file so you can easily manage your references)
* Python (Some scripts and packages will require Python to be installed)
* Pygments (A Python script that is required by the `minted` package so that you can import source code that will be automatically coloured in)
* TexCount (A Perl script that is required to perform the word count)

For `Linux` distributions, you may find a different TeX IDE to suit your tastes better; however for `Windows` TexMaker was the only IDE that I was able to set-up relatively quickly, the others I tried required a lot to configure.


General Tips
------------

Focus on writing up the content of your report first. Don't worry too much about how it looks, it's much easier to deal with layout when you have more content.

I kept `Images` and `Figures` in a seperate folder and then when I wanted to insert them I would do:

	\begin{figure}[h!]
		\centering
		\includegraphics[scale=0.6]{system_architecture}
		\caption{System Architecture}
		\label{fig:system_architecture}
	\end{figure}

The `system_architecture` would look for `system_architecture.png` first and it would find the image inside the `Figures` folder. However if you have images with the same name in both folders, it may cause some problems.


Compiling
---------

TeX requires the code to be compiled multiple times to fix all cross referencing issues and other things, this is partly due to the way the TeX engine was structured and built.

My compile script, of which I simply used in the `Quick Build` option in TeXMaker:

> pdflatex -shell-escape -synctex=1 -interaction=nonstopmode %.tex|bibtex %|pdflatex -shell-escape -synctex=1 -interaction=nonstopmode %.tex|pdflatex -shell-escape -synctex=1 -interaction=nonstopmode %.tex|"C:/Program Files (x86)/Adobe/Reader 10.0/Reader/AcroRd32.exe" %.pdf

An automatic perl script exists to ensure the correct number of compilations to resolve cross references etc. through the use of [latexmk](http://www.phys.psu.edu/~collins/software/latexmk-jcc/). I haven't personally used it, but you might find it useful.


Questions & Comments
--------------------

Please feel free to comment with any questions you may have; or fork this and make your own changes.

