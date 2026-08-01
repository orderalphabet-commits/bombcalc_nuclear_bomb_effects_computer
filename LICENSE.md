# Software Licenses

This product (software, documents, and data files) is licensed under a
Creative Commons
[Attribution-ShareAlike 4.0 International
License](https://creativecommons.org/licenses/by-sa/4.0/)
([legal text](https://creativecommons.org/licenses/by-sa/4.0/legalcode)).
You are free to copy and redistribute this material in any
medium or format, and to remix, transform, and build upon the
material for any purpose, including commercially.  You must give
credit, provide a link to the license, and indicate if changes
were made.  If you remix, transform, or build upon this
material, you must distribute your contributions under the same
license as the original.

This product is provided with no warranty, either expressed or implied,
including but not limited to any implied warranties of merchantability
or fitness for a particular purpose, regarding these materials and is
made available available solely on an “as-is” basis.

In no event shall John Walker be liable to anyone for special,
collateral, incidental, or consequential damages in connection with or
arising out of distribution or use of these materials.  The sole and
exclusive liability of John Walker, regardless of the form of action,
shall not exceed the compensation received by the author for the
product.

John Walker reserves the right to revise and improve this products as
he sees fit.  This publication describes the state of this product at
the time of its publication, and may not reflect the product at all
times in the future.
# Bombcalc — Nuclear Bomb Effects Computer

![Nuclear bomb effects computer](webtree/figures/enwcalc.jpg)

This repository is the development directory and archive for
Fourmilab's Web resource, “[*Strangelove Slide Rule*:
Nuclear Bomb Effects Computer](https://www.fourmilab.ch/bombcalc/)”,
which provides an interactive computer emulation of the circular
slide rule weapons effect computer optionally available with the
1962 edition of the U.S. government publication
[*The Effects of Nuclear Weapons*](https://www.fourmilab.ch/etexts/www/effects/).
In addition to the interactive calculator, downloadable file and
instructions are included to allow printing and constructing a
physical replica of the original plastic slide rule in the
interest of authenticity or for use in a post-apocalyptic world where
Internet access may be spotty.

## Structure of the repository

This repository is organised into the following directories.

* **webtree**: Replica of the Web tree from the Fourmilab site
containing all of the HTML documents, images, and downloads.  These
pages contain relative references to style sheets, icons, and other
resources on the Fourmilab Web site and will not work without
modification in other environments.

* **cgi**: Programs and supporting data files for the Common Gateway
Interface (CGI) services used to generate the updated slide rule
image for requests made either from the Web pages or from earlier
queries.  These programs will have to be modified to run in the CGI
environment of the server on which they are installed.

* **netpbm_tools**: Source code for three additions to the
[Netpbm](http://netpbm.sourceforge.net/) image manipulation toolkit,
which are used by the programs in the **cgi** directory to generate
the graphical results from queries.  You must integrate these programs
in a current version of Netpbm (which may require some work: the
versions that appear here were developed and tested with Netpbm
version 10.25 dating from 2005), then install them where the CGI
programs can run them.

* **tools**: An Excel worksheet, `pixparam.xls`, used to develop the
mapping between pixel position and numerical parameters for processing
queries.

* **diy**: Images used to make a printable replica of the original
bumb effects calculator.

## Web resources

* [*Strangelove Slide Rule*:
Nuclear Bomb Effects Computer](https://www.fourmilab.ch/bombcalc/)
    - [Bomb Effects Computer Instructions](https://www.fourmilab.ch/bombcalc/instructions.html)
    - [Production Notes](https://www.fourmilab.ch/bombcalc/production.html)
    - [Build Your Own Bomb Effects Computer Slide Rule](https://www.fourmilab.ch/bombcalc/brico.html)
* [*The Effects of Nuclear Weapons*](https://www.fourmilab.ch/etexts/www/effects/)

