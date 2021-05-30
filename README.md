# HDR_OpenGL
* Progetto di Computer Graphichs & 3D
* Realizzazione di una stanza con OpenGL e di un oggetto molto luminoso posto al centro
* Confronto di tecniche HDR con tone mapping per gestione della luminosità e del colore

## Problema
* I valori di luminosità e colore di default sono limitati ad essere nell'intervallo 0.0 e 1.0 nel framebuffer.
* Se la somma di multiple sorgenti luminose eccede il valore 1.0 il risultato che si ha normalmente è che si blocca il valore a 1.0
* Come risultato si hanno vaste aree molto bianche che rendono la scena irreale 

## Soluzione
* Si permette ai valori di eccedere temporaneamente il valore 1.0 e si trasformano successivamente tramite tone mapping nell'intervallo corretto senza perdere dettagli
### Reinhard Tone Mapping
````c
result = hdrColor / (hdrColor + vec3(1.0));

````

### Exposure Tone Mapping
````c
result = vec3(1.0) - exp(-hdrColor * exposure);
````

### Gamma Correction
````c
result = pow(result, vec3(1.0 / gamma));
FragColor = vec4(result, 1.0);
````

## Utilizzo
1. Scaricare la seguente repository e unzip di 'HDR_OpenGL-main'
2. Scaricare glm da [Google Drive](https://drive.google.com/drive/folders/1WHGnKOe_OktN5xeseHJauRhnvlLcQpEf?usp=sharing), unzip e trascinare la cartella 'glm' nella repository precedentemente scaricata in "../OpenGL_HDR-main/includes"
3. Scaricare [Visual Studio Community](https://visualstudio.microsoft.com/it/vs/) ed installare l'IDE
4. Aprire infine in Visual Studio Community la cartella 'HDR_OpenGL-main' tramite l'opzione "Aprire una cartella locale"
5. Selezionare eseguibile e lanciare (Selezione e poi Ctrl+F5)

## Comandi implementati
Possibilità di muoversi all'interno della scena 3D e di modificare Tone Mapping:
* **A** spostamento a sinistra
* **S** indietro
* **D** destra
* **W** avanti
* **Q** decremento del valore di esposizione
* **E** aumento del valore di esposizione
* **M** cambio metodo da Reinhard a Exposure ciclico
* **SPACE** disattivazione/attivazione HDR con rispettivo metodo di tone mapping
* **Mouse** muove la scena
* **Scroll** zoom in/out 
* **Esc** termina l'esecuzione

## HDR Off
<p align="center">
  <img src="https://github.com/edoardore/HDR_OpenGL/blob/main/screenshot/off.png" width="650" title="HDR Off">
</p>

## Reinhard Tone Mapping
<p align="center">
  <img src="https://github.com/edoardore/HDR_OpenGL/blob/main/screenshot/reinhard.png" width="650" title="Reinhard">
</p>


## Exposure = 0.033
<p align="center">
  <img src="https://github.com/edoardore/HDR_OpenGL/blob/main/screenshot/exp033.png" width="650" title="Exposure 0.033">
</p>

## HDR Off
<p align="center">
  <img src="https://github.com/edoardore/HDR_OpenGL/blob/main/screenshot/off%20(2).png" width="650" title="HDR Off">
</p>

## Reinhard Tone Mapping
<p align="center">
  <img src="https://github.com/edoardore/HDR_OpenGL/blob/main/screenshot/reinhard%20(2).png" width="650" title="Reinhard">
</p>


## Exposure = 0.033
<p align="center">
  <img src="https://github.com/edoardore/HDR_OpenGL/blob/main/screenshot/exp033%20(2).png" width="650" title="Exposure 0.033">
</p>

## Exposure = 0.008
<p align="center">
  <img src="https://github.com/edoardore/HDR_OpenGL/blob/main/screenshot/exp008.png" width="650" title="Exposure 0.008">
</p>
