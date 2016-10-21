# Components

#HSLIDE 
## qu'est ce que cest 

#VSLIDE
 - vue uniquement
 
#VSLIDE
 - vdom + jsx + cssmodules 
 code jsx (inline)
 code style associe 
 
#VSLIDE
 - -> react/virtual-dom/ -> html


#HSLIDE 
## installation
  - slide: clone  npm i  npm start
  --> sandbox

#HSLIDE 
## comment creer un template pour une app

#VSLIDE
  - split vue/metier 
    - definit les etats
    - definit les fixtures

#VSLIDE
  - creation du template
    - decoupe en components 
    - choix de la responsabilite parent/enfant  [grid VS card]
    - creation des dom + css
    - decoupe de apif/ixtures par composants
    - branchement des parents/enfants jusqu'au template

#HSLIDE 
## branchement sur les apps

#VSLIDE
build
   - babel --> /lib /es
   - webpack ---> dist css/js
   - bundler --> webpack 

#VSLIDE
- adapters --> mooc/www

#VSLIDE  
- mooc
   code directive
   
#VSLIDE  
- www
   code helper
   
#VSLIDE  
- webpack pour les apps
  code jsx

#VSLIDE  
- le branchement
  - npm link
  - publish npm + bump sur le projet
  
  
