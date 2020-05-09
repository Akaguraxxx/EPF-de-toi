# EPF-de-toi
EPF de toi
# -*- coding: utf-8 -*-
"""
Created on Tue Apr 14 16:31:05 2020

@author: Florane_000
"""

#tkinter est tres specifique donc je te mets
#plein de commentaires pour que tu comprennes bien 
#ce que j'ai fait



from tkinter import *
import random



def Choisir_Personnage():
    global sexe_choisi
    sexe_choisi=var_choix.get()
    
    frame_depart.destroy()
    
    w=IntVar()
    choix_crush=0
#    #les frames de la fenetre sont des blocs ou tu peux grouper du texte,des images,etc
#    #les frames sont independantes les unes des autres 
#    ###FRAME DES PERSONNAGES
    
    Frame1 = Frame(fenetre1, borderwidth=2, relief=GROOVE)
#    #pour la position, padx et pady sont tres importants
#    #car il permettent de placer ton element
    Frame1.pack()
#    while w != 1:
#        a=Tirage()
#    #les canvas contiennent et animent les images
#    ###PHOTO PERSONNAGE (DANS LA FRAME)
#    
    canvas1 = Canvas(Frame1, width=100, height=100, background="#FFFFFF")
##  
    if choix_crush==0:
        if sexe_choisi=="Homme":
            var1=random.randint(0,1)
        elif sexe_choisi=="Femme":
            var1=random.randint(0,1)
        elif sexe_choisi=="Homme et Femme":
            var1=random.randint(0,1)
    #solution secours:
    #var1=random.randint(0,1)
##            
##    
        perso_propose=tab2tab[var1]
        Photo_visible=canvas1.create_image(50,290,image=perso_propose[0])
        canvas1.pack()
##
##    frame_perso=Frame(fenetre)
        Label(Frame1, text=perso_propose[4]).pack(padx=10, pady=10)
        Label(Frame1, text="Voulez-vous commencer à discuter avec "+perso_propose[5]+" ?").pack(padx=10, pady=10)
        bouton_oui = Radiobutton(Frame1, text="oui",variable=w,value=1)
        bouton_non = Radiobutton(Frame1, text="non",variable=w,value=0)
        bouton_valider2=Button(Frame1, text="Valider", font=("Tahoma", 12), bg="#BE2121", fg ="white" , width=20)

        bouton_oui.pack()
        bouton_non.pack()
        bouton_valider2.pack()
        choix_crush=w.get()
    if choix_crush==1:
        Frame1.destroy()
    
    
###DEPART
def Depart() : 
    global frame_depart
    #☻frame_depart = Frame(fenetre1, bg="#D83AA1")
    frame_depart = Frame(fenetre1, bd=50, bg="pink", cursor = "heart")
    frame_depart.pack()
    global var_choix
    var_choix = StringVar()
    choix_femme = Radiobutton(frame_depart, text=F, bg="pink",variable=var_choix, value="Femme")
    choix_homme = Radiobutton(frame_depart, text=M, bg="pink",variable=var_choix, value="Homme")
    choix_les2 = Radiobutton(frame_depart, text=X, bg="pink", variable=var_choix, value="Homme et Femme")

    choix_femme.pack()
    choix_homme.pack()
    choix_les2.pack()
    
    
        
    bouton_valider = Button(frame_depart, text="Valider", font=("Tahoma", 12), bg="#BE2121", fg ="white" , width=20,command=Choisir_Personnage)
    bouton_valider.pack()  


def secondaire():
        toplevel = Toplevel()
        label = Label(toplevel, text='Coucou')
        label.pack()



#----------------------------- Programme principal ---------------------------

# création de la fenetre principale où se deroule le jeu
fenetre1 = Tk()
fenetre1.title("♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥   Jeu EPF de toi  ♥ ♥ ♥ ♥ ♥ ♥ ♥ ♥")

# Définir la taille de la fenêtre
global largeur_ecran
largeur_ecran=fenetre1.winfo_screenwidth()
global hauteur_ecran

hauteur_ecran=fenetre1.winfo_screenheight()
pourcentage=0.8
fenetre1.geometry("%dx%d+0+0" %(largeur_ecran*pourcentage,hauteur_ecran*pourcentage))

fenetre1.configure(bg="pink")

# Ajouter un boutton Quitter en bas de la fenêtre
Bouton_quitter=Button(fenetre1, text="Fermer le fenêtre",fg='navy', command=fenetre1.destroy)
Bouton_quitter.pack()
# On place le boutton Quitter
Bouton_quitter.place(x=largeur_ecran*pourcentage-140, y=hauteur_ecran*pourcentage-30)


# Changer l'icône de la fenêtre (NE FONCTIONNE PAS !!!)
#icon=PhotoImage(file="coeur.png").zoom(35).subsample(32)
#fenetre1.iconbitmap('coeur.ico')

# création d'une fenêtre secondaire
#toplevel = Toplevel()
#fenetre2 = Label(toplevel, text='Coucou')
#fenetre2.pack()



#bouton = Button(fenetre1, text='Choisis ton crush ♥ ?', command=secondaire)
#bouton.pack()



#fenetre.deiconify()

###ELEMENTS ETAPE 1


#les label sont les equivalents de print pour tkinter
#label = Label(fenetre, text="Choisis ton crush <3")
# .pack() sert à afficher l'element dans la fenetre sinon on ne voit pas
#label.pack()

                 
                    
#DONNEES
                 
                 
###PHOTO POUR CHAQUE PERSO                
Photo1=PhotoImage(file="Sasuke.png").zoom(35).subsample(32)

Photo2=PhotoImage(file="Sakura.png") .zoom(35).subsample(32)

#tableaux des caracteristiques visibles des persos
M="Homme"
F="Femme"
X="Peu importe"

Sasuke=[Photo1,M,18,"ninja","Paraît distant mais a un grand coeur","Sasuke"]
Sakura=[Photo2,F,18,"ninja","Très gentille et empathique","Sakura"]


tab2tab=[Sasuke,Sakura]




Commencer=Depart()

fenetre1.mainloop()           

               
               
               
               
