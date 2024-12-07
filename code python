import streamlit as st
import pandas as pd
from streamlit_authenticator import Authenticate
from streamlit_option_menu import option_menu
data = pd.read_csv("./fichier_pandas.csv", sep=',')

# Nos données utilisateurs doivent respecter ce format

lesDonneesDesComptes = {'usernames': {'utilisateur': {'name': 'utilisateur',
   'password': 'utilisateurMDP',
   'email': 'utilisateur@gmail.com',
   'failed_login_attemps': 0, # Sera géré automatiquement
   'logged_in': False, # Sera géré automatiquement
   'role': 'utilisateur'},
  'root': {'name': 'root',
   'password': 'rootMDP',
   'email': 'admin@gmail.com',
   'failed_login_attemps': 0, # Sera géré automatiquement
   'logged_in': False, # Sera géré automatiquement
   'role': 'administrateur'}}}

authenticator = Authenticate(
    lesDonneesDesComptes, # Les données des comptes
    "cookie name", # Le nom du cookie, un str quelconque
    "cookie key", # La clé du cookie, un str quelconque
    30, # Le nombre de jours avant que le cookie expire 
)
authenticator.login()

if st.session_state["authentication_status"] is False:
    st.error("L'username ou le password est/sont incorrect")
elif st.session_state["authentication_status"] is None:
    st.warning('Les champs username et mot de passe doivent être remplie')

# Création du menu qui va afficher les choix qui se trouvent dans la variable options
with st.sidebar:
        authenticator.logout("Déconnexion")
        f"Bienvenu:{st.session_state["name"]}"
        selection = option_menu(
                    menu_title=None,
                    options = ["Accueil", "Les photos de mon chat"]
                )

# On indique au programme quoi faire en fonction du choix
if selection == "Accueil":
    st.write("Bienvenue sur la page d'accueil !")
    st.image('https://www.cdiscount.com/pdt2/0/0/3/1/700x700/auc1697092063003/rw/5d-chat-mignon-diamond-painting-diy-chaton-peintu.jpg')
elif selection == "Les photos de mon chat":
    st.write("Bienvenue sur mon album photo")
    col1,col2,col3=st.columns(3)
    with col1:
     st.image('https://png.pngtree.com/background/20230516/original/pngtree-adorable-cute-cats-wallpaper-picture-image_2615778.jpg')
    with col2:
     st.image('https://diamond-faction.com/cdn/shop/products/broderie-diamant-petit-chat-mignon-abstrait-277576.jpg?v=1700762733')
    with col3:
     st.image('https://img.pikbest.com/origin/09/99/83/834pIkbEsTwZF.png!w700wp')

# ... et ainsi de suite pour les autres pages
