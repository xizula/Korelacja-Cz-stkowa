import math    

class Obj:
    def __init__(self):  
        self.w1 = None
        self.w2 = None
        self.w3 = None
        self.w12 = None
        self.w13 = None
        self.w23 = None

    def wprowadz(self):  # metoda uzupelnająca zmienne w1, w2, w3
        self.w1 = float(input("Podaj wartość w1: "))  
        self.w2 = float(input("Podaj wartość w2: "))  
        self.w3 = float(input("Podaj wartość w3: "))


    def wylicz(self):   # wylicznie w12, w13, w23
        self.w12 = self.w1 * self.w2
        self.w13 = self.w1 * self.w3
        self.w23 = self.w2 * self.w3

    def __str__(self):  # deklaratcja metody __str__ w celu czytania obiektu
        return str(self.w1) + "\t\t\t\t" + str(self.w2) + "\t\t\t\t" + str(self.w3)


# Dodawanie zmiennych
wybor = 0
lista = []
while True:
    while wybor < 1 or wybor > 2:
        try:        
            wybor = int(input("Wybierz akcję:\n1. Dodaj zmienne\n2. Zakończ\nWprowadź 1 lub 2: "))
            if wybor < 1 or wybor > 2:      # dla nieprawidłowego wyboru (nie 1 i nie 2) wyświetli się komunikat
                print("Nieprawidlowe dane, spróbuj ponownie")
        except ValueError:      # jeżeli podana wartość nie będzie liczbą, a np. str, wyświetli się komunikat
            print("Zmienna musi być liczbą (1 lub 2), spróbuj ponownie")
            wybor = 0
    if wybor == 1:  
        wybor = 0  
        while True:
            try:
                w = Obj()   
                w.wprowadz()    
                w.wylicz()
                lista.append(w)     
                break
            except:
                print("Wprowadzone złe wartości, spróbuj ponownie")
                continue
    elif wybor == 2:
        if len(lista) < 3:
            print("Wprowadzono za mało danych, dodaj kolejne:") 
            wybor = 1
            continue   
        else:
            break


# Wyświetlanie wprowadzonych zmiennych
print("Wprowadzone elementy")
print("w1\t\t\t\tw2\t\t\t\tw3")
for elem in lista:
    print(elem)


# Obliczenia

n = len(lista)  # ilość elementow listy
suma_w1 = 0     # dodawanie zmiennych okreslajacych sumy wszytskich elementów kolejno: w1, w2 i w3
suma_w2 = 0     # początkowo wszystkie zmienne przyjmuja wartosć 0 bo zdaen element nie został dodany
suma_w3 = 0
suma_w12 = 0
suma_w13 = 0
suma_w23 = 0

# Pętla licząca sumy
for elem in lista:  # pętla przechodzi przez każdy element listy (każdy obiekt)
    suma_w1 += elem.w1  # i dodaje do siebie wszystkie kolejne wartości w1
    suma_w2 += elem.w2  # następnie w2 itd.
    suma_w3 += elem.w3
    suma_w12 += elem.w12
    suma_w13 += elem.w13
    suma_w23 += elem.w23

# Oblicznie średnich
sr_w1 = suma_w1/n
sr_w2 = suma_w2/n
sr_w3 = suma_w3/n
sr_w12 = suma_w12/n
sr_w13 = suma_w13/n
sr_w23 = suma_w23/n

# Oblicznie wartości oczekiwanej
ocz_12 = sr_w1 * sr_w2
ocz_13 = sr_w1 * sr_w3
ocz_23 = sr_w2 * sr_w3

# Obliczanie odchylenia standardowego
suma_kw1 = 0    # sumy kwadratów - licznik odchylenia st
suma_kw2 = 0
suma_kw3 = 0
for elem in lista:
    x = (elem.w1 - sr_w1)**2
    suma_kw1 += x
    x = (elem.w2 - sr_w2)**2
    suma_kw2 += x
    x = (elem.w3 - sr_w3)**2
    suma_kw3 +=x

sdv_1 = math.sqrt(suma_kw1/n)
sdv_2 = math.sqrt(suma_kw2/n)
sdv_3 = math.sqrt(suma_kw3/n)

# Mnożenie odchyleń
sdv_12 = sdv_1 * sdv_2
sdv_13 = sdv_1 * sdv_3
sdv_23 = sdv_2 * sdv_3

# Kowariancja
k_12 = sr_w12 - ocz_12
k_13 = sr_w13 - ocz_13
k_23 = sr_w23 - ocz_23

# obliczanie r
r_12 = k_12/sdv_12
r_13 = k_13/sdv_13
r_23 = k_23/sdv_23

# Obliczanie r^2
r_12_2 = r_12**2
r_13_2 = r_13**2
r_23_2 = r_23**2

# Obliczanie R
R_12_3 = ((r_12-(r_13 * r_23))/(math.sqrt((1-r_13_2)*(1-r_23_2))))
R_13_2 = ((r_13-(r_12 * r_23))/(math.sqrt((1-r_12_2)*(1-r_23_2))))
R_23_1 = ((r_23-(r_12 * r_13))/(math.sqrt((1-r_12_2)*(1-r_13_2))))

# Wyświetlenie wyniku w zaokrągleniu do 3 miejsc po przecinku
print("Korelacja cząstkowa (12) w wyłączeniem (3): ", round(R_12_3, 3))
print("Korelacja cząstkowa (13) w wyłączeniem (2): ", round(R_13_2, 3))
print("Korelacja cząstkowa (23) w wyłączeniem (1): ", round(R_23_1, 3))