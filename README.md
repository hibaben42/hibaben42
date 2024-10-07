
def afficher_bienvenue():
    print("######################################")
    print("IFT-1004 Airlines")
    print("######################################")
    print("La meilleure compagnie aérienne au monde!")

def calculer_prix_billet(age, nom):
    prix_base = 150.0
  
    if age <= 3:
        prix = 0.0
        print(f"Prix du billet réservé pour {nom} : {prix:.2f}$")
    elif age >= 65:
        rabais = random.randint(15, 55)
        prix = prix_base * (1 - rabais / 100)
        print(f"Rabais appliqué pour {nom} : {rabais}%")
        print(f"Prix du billet réservé pour {nom} : {prix:.2f}$")
    else:
        prix = prix_base
        print(f"Prix du billet réservé pour {nom} : {prix:.2f}$")
    
    return prix

def reserver_billets():
    total_reservation = 0
    nb_passagers = int(input("Combien de billets souhaitez-vous réserver ? "))

    for i in range(1, nb_passagers + 1):
        print(f"============\nPassager {i}/{nb_passagers}\n============")
        nom = input(f"Nom du passager {i} : ")
        age = int(input(f"Âge du passager {i} : "))
        total_reservation += calculer_prix_billet(age, nom)

    if nb_passagers > 0:
        print(f"Montant total à encaisser pour cette réservation : {total_reservation:.2f}$")
    
    return total_reservation

def afficher_menu():
    print("1. Enregistrer un autre client")
    print("2. Quitter")
    choix = input("Entrez votre choix : ")
    while choix not in ['1', '2']:
        print("Choix invalide. Veuillez entrer 1 ou 2.")
        choix = input("Entrez votre choix : ")
    return choix

def main():
    afficher_bienvenue()
    
    total_cumule = 0
    while True:
        total_cumule += reserver_billets()
        
        choix = afficher_menu()
        if choix == '2':
            print(f"Montant total cumulé pour tous les clients enregistrés : {total_cumule:.2f}$")
            print("Bye bye!")
            break

if __name__ == "__main__":
    main()

