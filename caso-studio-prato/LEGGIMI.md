# Caso studio "Prato Macroterma" — versione sito web

Pagina web autonoma, pronta da caricare su www.giglioverde.com.
Ottimizzata per velocità e per la resa su smartphone (verticale e
orizzontale), tablet e desktop.

## Non è più una pagina isolata

Ho recuperato la struttura reale di www.giglioverde.com (menu, contatti,
social) e li ho integrati:

- **Header fisso in alto**, con il menu vero del sito (Servizi, Perché
  noi, Prodotti, Blog, Preventivo gratuito) che rimanda alla home. Su
  smartphone diventa un menu a scomparsa con l'icona hamburger — **zero
  JavaScript**, funziona con un meccanismo nativo del browser.
- **Breadcrumb** sotto l'header (Home / Blog / Conversione a prato
  macroterma), così chi arriva su questa pagina da un link esterno
  capisce subito dove si trova nel sito.
- **Footer con i contatti veri**: telefono, email, WhatsApp, Instagram
  e Facebook, tutti cliccabili.
- **CTA finale doppia**: WhatsApp diretto (328 7217116) oppure il
  modulo preventivi della home.

**Un'imprecisione possibile da correggere**: non ho potuto leggere i
colori e i font esatti del sito reale — i miei strumenti riescono a
leggerne il testo ma non il foglio di stile. Ho quindi usato la stessa
palette verde/crema/oro già vista nel PDF. Se il sito vero usa colori
diversi, aprili affiancati e dimmelo: sistemo i colori in due minuti,
sono tutti raccolti in un unico punto del CSS.

## Cosa c'è nella cartella

```
caso-studio-prato-macroterma.html   ← la pagina
assets/css/caso-studio.css          ← foglio di stile (separato per il caching)
assets/img/                         ← tutte le foto, in WebP + JPEG di riserva
```

## Come metterla online (GitHub → Netlify)

1. Copia l'intera cartella `sito-web/` dentro il repository
   `github.com/tommynoom/giglioverde`, ad esempio in una sottocartella
   `caso-studio/`.
2. Fai commit e push: Netlify pubblica in automatico come sempre.
3. La pagina sarà raggiungibile su
   `www.giglioverde.com/caso-studio/caso-studio-prato-macroterma.html`
   (o il percorso che scegli).
4. Aggiungi un link a questa pagina dal menu o dal blog, dove preferisci.

Non serve altro: nessuna build, nessuna dipendenza da installare, nessun
database. È HTML e CSS puri più le immagini.

## Perché è veloce

- **Ogni foto pesa in media 80–150 KB** invece dei 400–600 KB originali
  (compressione WebP con riserva JPEG per i browser più vecchi).
- **Lazy loading su tutte le foto tranne la prima**: la pagina carica
  subito solo quello che si vede, il resto arriva mentre si scorre.
  Al primo caricamento la pagina pesa meno di 400 KB.
- **Zero JavaScript.** Anche le domande frequenti si aprono e chiudono
  con un meccanismo nativo del browser (`<details>`), senza script da
  scaricare né eseguire.
- **Font caricati una sola volta** con `preconnect` e `font-display:
  swap`, così il testo compare subito anche se il font impiega un
  istante in più.

## Perché è responsiva

Il foglio di stile è scritto "mobile-first": tutto è pensato prima per
lo schermo piccolo, poi allargato con delle soglie (768px, 900px,
1200px) via via che lo schermo cresce. È stata verificata concretamente
in un browser reale su:

- smartphone verticale e orizzontale
- tablet verticale
- desktop

Le due tabelle più larghe (confronto microterme/macroterme e calendario
di concimazione) scorrono in orizzontale con il dito su schermo piccolo,
invece di rompere il layout o rimpicciolire il testo fino a renderlo
illeggibile.

## Una nota sui font

La pagina carica Lora, Poppins e IBM Plex Mono da Google Fonts (lo
stesso servizio usato da moltissimi siti). Se in futuro preferisci non
dipendere da un servizio esterno — anche per una questione di privacy,
dato che Google Fonts esterno ha creato qualche problema di conformità
GDPR ad alcuni siti italiani — si possono scaricare i tre font una
volta sola e ospitarli nella cartella `assets/fonts/` del sito. È un
lavoro di mezz'ora, non urgente: la pagina funziona bene comunque, e se
il font non si carica per qualunque motivo il testo resta leggibile con
il font di sistema del dispositivo (l'ho verificato: è già così che
appare nell'ambiente in cui ho preparato la pagina, dove Google Fonts
è bloccato).

## Se vuoi modificare qualcosa

- **Testi**: sono nell'HTML, in italiano semplice, cercabili per
  sezione (ogni sezione ha un commento tipo `<!-- ===== 05 A CHI E'
  RIVOLTO ===== -->`).
- **Colori**: tutti raccolti in cima al file CSS, sotto `:root`. Cambia
  lì e si aggiorna ovunque.
- **Foto**: se vuoi sostituirne una, mantieni lo stesso nome file per
  non dover toccare l'HTML, oppure cambia il riferimento nell'HTML.
  Le dimensioni consigliate: 1400px di larghezza per l'immagine di
  apertura, 760px per le foto della galleria — più che sufficiente per
  la resa su schermo, anche retina.

## Cosa NON è incluso

Questa pagina non è collegata al resto del sito (menu, header, footer
del sito principale) — è pensata per essere aperta come pagina a sé,
linkata da altre pagine. Se vuoi che erediti l'intestazione e il piè di
pagina del sito esistente, serve integrarla nel template del sito
invece che usarla come file singolo: fammi sapere se vuoi che prepari
anche quella versione.
