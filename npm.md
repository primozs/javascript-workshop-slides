# Npm
- `Npm` package manager pride skupaj z inštalacijo `node`-a 
- namenjen vsem vrstam knjižnic (server, client in desktop)



## Npmjs
Moduli se nahajajo na Npmjs-u.
- <https://www.npmjs.com/>
- Kako poiščemo paket
- Katere informacije najdemo na npmjs-u   



## Npm komande
### Novi projekt (package, module)
Definicija in nastavitve paketa se nahajajo v datoteki `package.json`
 
    $ mkdir noviprojekt && cd noviprojekt
    $ npm init


    
### Inštalacija paketov
Inštalacije so lahko lokalne v direktoriju `node_modules`:

```
$ npm install  
$ npm install experss   
$ npm install experss --save  
$ npm install webpack --save-dev
$ npm install react@0.13.3 --save
$ npm install react@0.13.3 --save
$ npm install express@git+https://git@github.com/nekdo/express.git
```

ali pa globalne

```
$ npm install nek-cli -g
```



### Odstranitev paketov

```
$ rm -r node_modules
$ npm remove experss --save  
$ npm remove webpack --save-dev
```



### Cache clean
`npm cache clean`



### Npm run 

    $ npm run start
    $ npm run custom



### Razvoj modula vzporedno s drugim modulom
```
// mod-a depends mod-b

$ cd mod-a
$ npm install ../..mod-b

// ob vsaki spremembi v mod-b moramo na novo narediti install
```

```
// mod-a depends mod-b

$ cd mod-a 
npm link ../../mod-b

// enako kot symlink
$ ln -s ../../mod-b ./node_modules/mod-b

// ob vsaki spremembi v mod-b nam ni potrebno na novi ištalirati mob-b
```
