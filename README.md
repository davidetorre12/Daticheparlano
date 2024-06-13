SUPSI 20223-24  
Corso d’interaction design, CV428.01  
Docenti: A. Gysin, G. Profeta  

Elaborato 2: Me Myself and AI 

# Titolo progetto
Autore: Davide Torre  
[Dati che Parlano AI che Interpretano](https://davidetorre12.github.io/daticheparlano/)


## Introduzione e tema
Dati che Parlano AI che Interpretano è un progetto che esplora come un singolo dato possa acquisire presenza e significato all’interno di uno spazio, rappresentando frammenti di vita estrapolati da fotografie. L’atto di esaminare le proprie fotografie, un gesto apparentemente semplice, può esporre inaspettatamente la propria identità privata a terzi. Questo progetto si concentra sull’analisi di come descrizioni, statistiche, date temporali, informazioni e altri dati possano delineare abitudini, caratteristiche, comportamenti o informazioni.

L’aspetto più affascinante è l’utilizzo dell’intelligenza artificiale per estrapolare i dati dalle fotografie. Il progetto mira a definire una mia identità attraverso i dati estrapolati da script come Face Detect, YOLO e Exif. Per approfondire quanto questi dati possano raccontare su di me, ho utilizzato ChatGPT per interpretare i dati, riconoscere pattern e comportamenti, e definire abitudini. Questo processo non solo rivela dettagli personali, ma mette anche in luce le potenzialità e i limiti dell’intelligenza artificiale nella comprensione e interpretazione dei dati personali.




## Riferimenti progettuali
Il progetto è stato sviluppato utilizzando script come Face Detect, YOLO e Exif. Durante il corso di interaction design, i docenti hanno fornito supporto e guida su come applicare queste tecnologie per l’analisi dei dati fotografici.


https://user-images.githubusercontent.com/6561331/236182302-68a6bd12-7b83-4d19-b83e-c9b7db795881.mp4


## Design dell’interfraccia e modalià di interazione
L’interfaccia del progetto è strutturata, chiara, semplice e intuitiva, facilitando la navigazione e la comprensione dei dati. La navigazione avviene tramite uno scroll verticale, rendendo l’esperienza utente fluida e naturale. Inoltre, l’interfaccia è completamente responsive, adattandosi a diverse dimensioni di schermo.


## Tecnologia usata

Il progetto utilizza diverse tecnologie per l’analisi e l’interpretazione dei dati fotografici:

	>   Fa Dceetect: Uno script per il rilevamento dei volti nelle immagini.
	>   YOLO (You Only Look Once): Uno script per il riconoscimento di oggetti che utilizza il Machine Learning.
	>   Exif: Un formato per la registrazione delle informazioni sugli scatti fotografici.
	>   ChatGPT: Un modello di intelligenza artificiale sviluppato da OpenAI per l’interpretazione e l’analisi dei dati.


const fs = require('fs')

const exif = JSON.parse(fs.readFileSync('data_exif.json'))
const face = JSON.parse(fs.readFileSync('data_face.json'))
const yolo = JSON.parse(fs.readFileSync('data_yolo.json'))

console.log("Exif: " + exif.length)
console.log("Face: " + face.length)
console.log("Yolo: " + yolo.length)

const num = exif.length

const combi = []

for (let i=0; i<num; i++) {
    combi.push( {
        FileName : exif[i].FileName,
        FileExtension : exif[i].FileExtension,
        EXIF : exif[i].EXIF,
        Faces : face[i].Faces, 
        Objects : yolo[i].Objects
    } )
}

const JSON_PATH = "combi.json"

console.log()
console.log("Scrivo dati nel file: " + JSON_PATH + "...")
fs.writeFileSync(JSON_PATH, JSON.stringify(combi, null, 4), 'utf8')
console.log("Fatto!")
console.log(":)")

Creazione di un array combinato

## Target e contesto d’uso
Questo progetto è pensato per chiunque è interessato a esplorare come l’intelligenza artificiale può interagire con i dati personali. È utile per chi studia nuovi metodi di analisi e interpretazione dei dati, per chi crea opere digitali e vuole integrare nuove tecnologie, e per chi è curioso di vedere come l’IA può dare significato ai dati della vita quotidiana.
