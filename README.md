unix-training
=============

How to generate the slides from the source:

    pandoc -t beamer --slide-level=2 -s unix_i.md -o unix_i.pdf
    pandoc -t s5 --slide-level=2 -s unix_i.md -o unix_i.html
