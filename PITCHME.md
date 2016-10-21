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
## La bibliotheque

#VSLIDE
### structure
    - design: `atom -> molecule -> organism -> template`
    - behaviour


#HSLIDE 
## creer un template : analyse

#VSLIDE
- discussion vue/metier 

#VSLIDE
- definir les etats --> les fixtures

#VSLIDE
- decoupe en components 

#HSLIDE
## creer un template : implementation

#VSLIDE
### analyse macro
    - choix de la responsabilite parent/enfant  [grid VS card]
    - decoupe de api/fixtures par composants

#VSLIDE
### realisation macro
    - creation des dom + css
    - branchement des parents/enfants jusqu'au template

#HSLIDE
## creer un template : outils

#VSLIDE
### validation -> api-check
 code conditions

#VSLIDE 
### factory + jsx
 code createComponent
 
 
#VSLIDE
### css-modules
        class composition
        inline
        ajout de classe sur un enfant
        media queries

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
  
  
