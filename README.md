 README - Laboratorio di ADVANCEd Computer Architecture 

Benvenuti al laboratorio di Architettura Avanzata dei Computer. Questo laboratorio coprirà vari esercizi di programmazione parallela, con particolare attenzione a CUDA e OpenMP. L'ambiente di sviluppo verrà eseguito in un container Docker per garantire consistenza e portabilità del codice.

 Requisiti

Software
- **Docker**: per eseguire il laboratorio in un ambiente isolato.
- **NVIDIA Docker**: per abilitare l'accelerazione GPU all'interno dei container.
- **CUDA Toolkit**: necessario per compilare ed eseguire i programmi CUDA.
- **GCC**: per compilare i programmi OpenMP.
- **Makefile**: utilizzato per semplificare il processo di compilazione.

 Hardware
- GPU compatibile con CUDA: per gli esercizi CUDA.
 Configurazione dell'Ambiente

 Installazione Docker

Assicurati di avere Docker installato sulla tua macchina. Segui le istruzioni ufficiali di Docker per la tua piattaforma:
- [Installazione Docker](https://docs.docker.com/get-docker/)
 Abilitazione dell'accelerazione GPU con NVIDIA Docker

Se il tuo sistema ha una GPU NVIDIA, installa il plugin per Docker che consente di eseguire container con accesso alla GPU:
- [Installazione NVIDIA Docker](https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/install-guide.html)

Creazione dell'immagine Docker

Nel repository è presente un file `Dockerfile` che creerà un'immagine con tutto il necessario per lo sviluppo con CUDA e OpenMP.

Per creare l'immagine, eseguire il seguente comando:

```bash
docker build -t laboratorio-architettura-avanzata .
```

 Avvio del container

Una volta creata l'immagine, puoi avviare un container interattivo con il seguente comando:

```bash
docker run --rm -it --gpus all -v $(pwd):/workspace laboratorio-architettura-avanzata
```

Il flag `--gpus all` assicura che Docker possa accedere alla tua GPU. Il volume `-v $(pwd):/workspace` monta la cartella corrente all'interno del container per permettere di accedere ai file del laboratorio.

 Esercizi

 Esercizio 1: Programmazione CUDA di base
In questo esercizio, verrà implementato un semplice programma CUDA per eseguire il calcolo parallelo su una GPU.

1. Naviga nella cartella `cuda/01_base`.
2. Compila il programma CUDA:
   ```bash
   nvcc main.cu -o main_cuda
   ```
3. Esegui il programma compilato:
   ```bash
   ./main_cuda
   ```

 Esercizio 2: OpenMP
In questo esercizio, utilizzerai OpenMP per parallelizzare un programma su una CPU multi-core.

1. Naviga nella cartella `omp/01_base`.
2. Compila il programma OpenMP:
   ```bash
   gcc -fopenmp main.c -o main_omp
   ```
3. Esegui il programma:
   ```bash
   ./main_omp
   ```

 Esercizio 3: CUDA + OpenMP
Combineremo l'uso di CUDA e OpenMP per sfruttare sia la CPU che la GPU in uno stesso programma.

1. Naviga nella cartella `cuda_omp/01_combined`.
2. Compila il programma:
   ```bash
   nvcc -Xcompiler -fopenmp main_combined.cu -o main_combined
   ```
3. Esegui il programma:
   ```bash
   ./main_combined
   ```
 Troubleshooting

 Problemi con l'accesso alla GPU
Se il container non riesce ad accedere alla GPU, verifica che il plugin NVIDIA Docker sia correttamente installato e che i driver NVIDIA siano aggiornati.

 Errori di compilazione
Assicurati di avere il CUDA Toolkit installato correttamente nel container. Controlla che i file sorgente siano correttamente montati all'interno del container.

Autori

- Monruethai Sueksakan
- Università degli studi di verona
- monruethai.sueksakan_03@studenti.univr.it

