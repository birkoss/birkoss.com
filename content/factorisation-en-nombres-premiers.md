Title: Factorisation en nombres premiers
Category: code
Tags: python
Date: 2015-07-29
Slug: factorisation-en-nombres-premiers

Cette petite fonction en python permet d'afficher la factorisation en nombres premiers d'un nombre :

    def print_factor(n):
            d = 2
            while n &gt; 1:
                    while n % d == 0:
                            n /= d
                            print "Factor: " + str(d)
                    d += 1

Voici le résultat avec le nombre 330: **print_factor(330)**

    birkoss@thinkpad:~/Code$ python factor.py 
    Factor: 2
    Factor: 3
    Factor: 5
    Factor: 11
