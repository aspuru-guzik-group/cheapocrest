# cheapocrest

for when you want conformers fast!

`cheapocrest` does automatic conformer generation directly from SMILES using
[OpenBabel](http://openbabel.org/wiki/Main_Page), refines them using
[xtb](https://github.com/grimme-lab/xtb) &
[crest](https://github.com/grimme-lab/crest) bypassing the computationally
expensive parts of (specifically, the metadynamics section). `cheapocrest` is
a much less powerful conformer generator than CREST, but it is significantly
faster. It is appropriate for fairly stiff organic molecules (where conformer
generation is easy) and optical excitation studies (where conformation effects
are small).

To generate conformers, use

```bash
  cheapocrest [--ff FORCEFIELD] [--nconfs N] -- INPUTSMILES
```

where `FORCEFIELD` is the openbabel forcefield used in the generation
(defaults to UFF), `N` is the requested maximum number of conformers generated
by openbabel (defaults to 10) and `INPUTSMILES` is either an input SMILES or a
file containing an input SMILES. Currently the refinement steps always use
GFN2.

Note that `cheapocrest` works with charged molecules, and the SMILES-detected
global  charge will be automatically stored into a ~.CHRG~ file for use
with `xtb`.

This repo also contains an utility script `split_conformers` takes an xyz file
containing multiple conformers as input and splits it into folders `conf-0`,
`conf-1`, etc.

## installation

To install, simply add the content of this directory to `$PATH`. You'll need
relatively recent versions of `xtb`, `OpenBabel` and `crest` as well as a Perl
5 compatible interpreter. There are no other dependencies.


## license

Permission is hereby granted, free of charge, to any person obtaining
a copy of this software and associated documentation files (the
"Software"), to deal in the Software without restriction, including
without limitation the rights to use, copy, modify, merge, publish,
distribute, sublicense, and/or sell copies of the Software, and to
permit persons to whom the Software is furnished to do so, subject to
the following conditions:

The above copyright notice and this permission notice shall be
included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY
CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT,
TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE
SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
