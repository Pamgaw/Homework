# Homework
Tasks from the end of a presentation

import random
import time
from colorama import init
from termcolor import colored
init()
punkty_gracz = 0
punkty_komp = 0
runda = 0
print(colored("-- INSTRUKCJA GRY -- \n","cyan"))
print(" * Papier owija kamień, \n * kamień tępi nożyce, \n * nożyce tną papier.")
print("W grze posługujemy się skrótami: p-papier, k-kamień, n-nożyce")
print("Gra kończy się, kiedy ty lub komputer zdobędziecie 3 punkty.")
print("Powodzenia! \n")
while True:
    runda += 1
    print(colored("-- RUNDA","blue"),colored(runda,"blue"),colored("--","blue"))
    print("\npodaj znak")
    znak = str(input())
    while znak != "p" and znak != "k" and znak != "n":
        print("Podałeś nieznany znak. Wpisz p/k/n ")
        znak = str(input())
    if znak == "p":
        print("\nTy: papier.")
    elif znak == "k":
        print("\nTy: kamień.")
    else:
        print("\nTy: nożyce.")
    choice = "pkn"
    komp = random.choice(choice)
    if komp == "p":
        print("Komputer: papier. \n")
        if znak == "p":
            print("Remis \n")
        elif znak == "k":
            print("Papier owija kamień.")
            print("Punkt dla komputera. \n")
            punkty_komp += 1
        else:
            print("Nożyce tną papier.")
            print("Punkt dla ciebie. \n")
            punkty_gracz += 1
    elif komp == "k":
        print("Komputer: kamień \n")
        if znak == "p":
            print("Papier owija kamień.")
            print("Punkt dla ciebie. \n")
            punkty_gracz += 1
        elif znak == "k":
            print("Remis \n")
        else:
            print("Kamień tępi nożyce.")
            print("Punkt dla komputera. \n")
            punkty_komp += 1
    else:
        print("Komputer: nożyce \n")
        if znak == "p":
            print("Nożyce tną papier.")
            print("Punkt dla komputera. \n")
            punkty_komp += 1
        elif znak == "k":
            print("Kamień tępi nożyce.")
            print("Punkt dla ciebie. \n")
            punkty_gracz += 1
        else:
            print("Remis \n")
    if punkty_gracz == 3:
        print(colored("WYGRAŁEŚ!","red"))
        print("Czy chcesz zagrać jeszcze raz? (t-tak/n-nie)")
        restart = str(input())
        while restart != "t" and restart != "n":
            print("Nieznane polecenie.")
            restart = str(input())
        if restart == "t":
            punkty_komp = 0
            punkty_gracz = 0
            runda = 0
            print(colored("-----NOWA GRA----- \n","magenta"))
            continue
        else:
            print("Do zobaczenia!")
            break
    elif punkty_komp == 3:
        print(colored("KOMPUTER WYGRAŁ!","red"))
        print("Czy chcesz zagrać jeszcze raz? (t-tak/n-nie)")
        restart = str(input())
        while restart != "t" and restart != "n":
            print("Nieznane polecenie.")
            restart = str(input())
        if restart == "t":
            punkty_komp = 0
            punkty_gracz = 0
            runda = 0
            print(colored("-----NOWA GRA----- \n","magenta"))
            continue
        else:
            print("\nDo zobaczenia!")
            break
    else:
        continue
