# TLC - Definizioni
**Modulo e argomento di un numero complesso**:
| | Modulo| Argomento |
|-|-|-|
|Forma trigonometrica $z=r(cos(\theta)+isin(\theta))$| $r$ | $\theta$ |
|Forma esponenziale $z=re^{i\theta}$| $r$ | $\theta$ |
Per la forma algebrica $z = a+ib$, abbiamo che il **modulo** vale:
$$r=|z|:=\sqrt{a^2+b^2}$$
mentre l'argomento:
$$\theta = Arg(z)=\begin{cases} \frac{\pi}{2}\text{ se } a=0,b>0\\ -\frac{\pi}{2}\text{ se } a=0,b<0\\ \text{non definito se } a=0,b=0\\ arctan(\frac{b}{a})\text{ se } a>0,b \text{ qualsiasi}\\ arctan(\frac{b}{a})+\pi\text{ se } a<0,b\ge0\\ arctan(\frac{b}{a})-\pi\text{ se } a<0,b<0\\
\end{cases}$$

**Seno e coseno in termini di somma e differenza di esponenziali**: 
$$cos(\theta)=\frac{e^{j\theta}+e^{-j\theta}}{2}, sin(\theta) = \frac{e^{j\theta}+e^{-j\theta}}{j2}$$
**Funzione sinusoidale**: 
$$x(t)=Acos(\omega t+\theta)$$
esprimibile anche come come somma di due funzioni esponenziali complesse:
$$Acos(\omega t + \theta) = \frac{A}{2}e^{j(\omega t+\theta)}+\frac{A}{2}e^{-j(\omega t+\theta)}$$
**Fasore**:
$$Ae^{j(\omega t+\theta)}$$
# Sviluppo in serie di Fourier (funzioni periodiche tempo continue)
**Forma esponenziale (segnali complessi)**: Data la funzione complessa $x(t)=x(t+T)$ con $x \in C\R$, può essere rappresentata come somma di infiniti fasori, aventi pulsazioni multiple della pulsazione fondamentale $\omega_0 = \frac{2\pi}{T}$ (in rad/s) (frequenza fondamentale in Hz = $f_0=\frac{1}{T}$) secondo la **formula di sintesi** seguente detta **serie di Fourier (in forma esponenziale)**:
$$x(t)=\sum_{n=-\infty}^{+\infty}c_ne^{jn\omega_0t}$$
I coefficienti $c_n$ indicano il numero complesso rappresentativo del fasore $c_n = A_ne^{j\theta n}$, e sono dati dalla **formula di analisi**:
$$c_n=\frac{1}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}x(t)e^{-jn\omega_0t}dt$$
I coefficienti $c_n$ sono in generale complessi anche quando il segnale $x(t)$ è reale. Sono invece *reali* se il segnale è *reale* e *pari*, puramente immaginarei se *reale* e *dispari*.
# Rappresentazioni monolatere (segnali reali)
[**Simmetria hermitiana**](#1-simmetria-hermitiana):
$$c_{-n}=A_{-n}e^{-j\theta_{-n}}=c_n^*=A_ne^{-j\theta_n} \tag{1}$$
[**Forma in soli coseni dello sviluppo in serie di Fourier**](#2-forma-in-soli-coseni-dello-sviluppo-in-serie-di-fourier):
$$x(t)=c_0+2\sum_{n=1}^{+\infty}Re\{|c_n|e^{jarg{c_n}}e^{jn\omega_0t}\}=A_0+2\sum_{n=1}^{+\infty}A_ncos[n\omega_0t+\theta_n]\tag{2}$$
[**Terza forma in seni e coseni**](#3-terza-forma-seni-e-coseni-senza-fasi) (ma senza fasi): definendo i coefficienti monolateri $a_n$, $b_n$, anch'essi reali:
$$a_n=\begin{cases} 2c_0\text{ se }n=0 \\ Re\{{2c_n}\}  \text{ se } n>0  
\end{cases}$$
$$b_n=-Im\{2c_n\} \text{ se } n > 0$$ 
si ha che:
$$x(t)=\frac{a_0}{2}+\sum_{n=1}^{+\infty}a_ncos[n\omega_0t]+\sum_{n=1}^{+\infty}b_nsin[n\omega_0t]\tag{3}$$
Per ricavare direttamente i coefficienti direttamente senza passare dalla conoscenza dei $c_n$:
$$a_n=\frac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}x(t)cos[n\omega_0t]dt \text{ se } n\ge 0$$
$$b_n =  \frac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}x(t)sin[n\omega_0t]dt \text{ se } n>0\tag{4}$$

# Trasformata ed integrale di Fourier (funzioni aperiodiche tempo continue)
| | Trasformata (analisi, tempi $\rightarrow$frequenze)| Antitrasformata (sintesi, tempi $\leftarrow$frequenze)|
|- |-|-|
|Dominio pulsazioni |$X(\omega)=\int_{-\infty}^{+\infty}x(t)e^{-j\omega t}dt$| $x(t)=\frac{1}{2\pi}\int_{-\infty}^{+\infty}X(\omega)e^{j\omega t}d\omega$|
|Dominio frequenze |$X_f(f)=\int_{-\infty}^{+\infty}x(t)e^{-j2\pi ft}dt$| $x(t)=\int_{-\infty}^{+\infty}X_f(f)e^{j2\pi ft}df$|


# Rappresentazioni monolatere (segnali reali); integrale di Fourier
[**Integrale di Fourier**](#5-integrale-di-fourier): definito $V(\omega)=|\frac{X(\omega)}{\pi}|$, l'integrale di Fourier è:
$$x(t)=\int_0^{+\infty}V(\omega)cos[\omega t+ \varphi(\omega)]d\omega \tag{5}$$
[**Proprietà della trasformata di Fourier**](#6-proprieta-trasformata-fourier):
Sia $x(t)$ un segnale complesso con trasformata $F[x(t)]=X(\omega)$:
-   **Coniugazione**: 
$$F[x^*(t)]=X^*(-\omega)$$
-   **Traslazione temporale**:
$$F[x(t-t_0)]=X(\omega)e^{-j\omega t_0}$$
-   **Derivata**: 
$$F[x'(t)]=j\omega X(\omega)$$
-   **Integrale**:
$$F\bigg[\int_{-\infty}^tx(u)du\bigg]=\frac{X(\omega)}{jw} \text{ se } X(0)=\int_{-\infty}^{+\infty}x(t)dt=0$$
-   **Convoluzione**:
$$F[x(t)*y(t)]=X(\omega)Y(\omega)\tag{6}$$

# Funzione generalizzata delta di Dirac
**Definizione**: 
$$<x, \delta> = x(0) = \int_{-\infty}^{+\infty}x(t)\delta(t)dt$$
e analogamente:
$$<x, \delta_{t_0}>=x(t_0)$$
La delta di Dirac è nulla per tutti i valori del parametro reale ad eccezione dello zero, ed il suo integrale sul parametro tra $-\infty$ e $+\infty$ è uguale a 1:
$$\int_{-\infty}^{+\infty}\delta(t)dt=1$$
**Proprietà della funzione generalizzata delta di Dirac**:
-   **Parità**:
$$\int_{-\infty}^{+\infty}x(t)\delta(t-t_0)dt=\int_{-\infty}^{+\infty}x(t)\delta(t_0-t)dt$$
-   **Convoluzione**:
$$x(t)*\delta(t)=\int_{-\infty}^{+\infty}x(\tau)\delta(\tau-t)d\tau=x(t) \\ \rightarrow x(t)*\delta(t)=<x, \delta_t>=<x(\tau), \delta(\tau-t))>=x(t)$$
-   **Cambio di argomento**:
$$|\alpha|\delta(\alpha t)=\delta(t) \text{ se } \alpha \ne 0 \rightarrow \delta(\alpha t)=\frac{\delta(t)}{|\alpha|} \text{ se } \alpha \ne 0 \rightarrow \delta(-x)=\delta(x)$$
-   **Trasformata di Fourier**:
$$\int_{-\infty}^{+\infty}\delta(t)e^{-j\omega t}dt=1$$
-   **Gradino unitario**:
$$U(t)=\int_{-\infty}^t\delta(\tau)d\tau\tag{7}$$

# Trasformata di Fourier di funzioni periodiche
-   **Trasformata di un segnale sviluppabile in serie di Fourier**:
$$x(t)=\sum_{n=-\infty}^{+\infty}c_ne^{jn\omega_0t},\qquad X(\omega)=\sum_{n=-\infty}^{+\infty}c_n2\pi\delta(\omega-n\omega_0), \qquad X_f(f)=\sum_{n=-\infty}^{+\infty}c_n\delta(f-nf_0)$$
-   **Trasformata del coseno**:
$$cos(\omega_0 t)= \frac{e^{j\omega_0t}+e^{-j\omega_0t}}{2}, \qquad X(\omega)=\frac{1}{2}\delta(\omega-\omega_0)2\pi+\frac{1}{2}\delta(\omega+\omega_0)2\pi, \qquad X_f(f)=\frac{1}{2}\delta(f-f_0)+\frac{1}{2}(f+f_0)$$
-   **Trasformata del seno**:
$$sin(\omega_0 t)= \frac{e^{j\omega_0t}-e^{-j\omega_0t}}{j2}, \qquad X(\omega)=\frac{1}{j2}\delta(\omega-\omega_0)2\pi-\frac{1}{j2}\delta(\omega+\omega_0)2\pi, \qquad X_f(f)=\frac{1}{j2}\delta(f-f_0)-\frac{1}{j2}(f+f_0)$$
-   **Trasformata di Fourier delle funzioni gradino**: a partire dalla trasformata del gradino $1(t)$: $\quad F[1(t)]=\frac{1}{j\omega}$, dalle definizioni di $U(t)$ e $sgn(t)$ segue $\quad F[U(t)]=\frac{1}{j\omega}+\frac{2\pi\delta(\omega)}{2}, \quad$ e $F[sgn(t)]=\frac{2}{j\omega}$
-   **Trasformata di Fourier di un integrale**:
$$y(t)=\int_{-\infty}^tx(\tau)d\tau=\int_{-\infty}^{\infty}x(\tau)U(t-\tau)d\tau=x(t)*U(t) \tag{8}$$

# Serie temporali
**Serie temporali**: Una serie temporale è una funzione tempo discreta che rappresenta o segnali che in origine hanno già questa forma o segnali ottenuti da una funzione tempo continua mediante lettura dei valori  da essa assunti in istanti che si succedono con intervallo $T$. Quest'operazione è detta campionamento. 
Consideriamo ora la serie temporale:
$$\{x_n\}=\{...,x_{-2}, x_{-1}, x_0, x_1, x_2, ...\}$$ 
**Trasformata**:
$$X_s(\omega)=\sum_{n=-\infty}^{+\infty}x_ne^{-jn\omega T}$$
**Antitrasformata:**
$$x_n=\frac{T}{2\pi}\int_{-\pi/T}^{\pi/T}X_s(\omega)e^{jn\omega T}d\omega \qquad n = ..., -2, -1, 0, 1, ...\tag{9}$$
**Relazione tra $X_s(\omega)$ della serie e la trasformata $X(\omega)$ della funzione campionata**:
$$X_s(\omega)=\frac{1}{T}\sum_{k=-\infty}^{+\infty}X(\omega+k\omega_0)\tag{10}$$

**Antitrasformata di un impulso nelle frequenze**: di ampiezza $X_o$ e periodo $\omega_m$, definito come: 
$$X(\omega)=\begin{cases} X_o \quad \text{ se } |\omega|<\omega_m \qquad \text{ con } X_o > 0 \text { entrambe}
\\ 0 \qquad \text{ altrove }   
\end{cases}$$
la sua antitrasformata secondo Fuorier è espressa da:
$$x(t)=x_osinc(\frac{\omega_mt}{\pi})$$

**Sviluppo in serie di Shannon**: Condizione sufficiente del teorema di Shannon, $\omega_o > 2\omega_m$, scelta la frequenza di Nyquist, ovvero $\omega_o/2$, abbiamo:
$$X(\omega)=\begin{cases} TX_s(\omega) \qquad \text{se }|\omega|<\omega_o/2 \\ 0 \qquad \text{altrove}
\end{cases}$$
Quindi lo sviluppo in serie di Shannon è:
$$x(t)=\frac{T}{2\pi}\sum_{n=-\infty}^{+\infty} x_n\int_{-\pi/T}^{\pi/T}e^{j\omega t} e^{-j\omega nT}d\omega=\sum_{n=-\infty}^{+\infty}x_nsinc\bigg(\frac{t-nT}{T}\bigg) \tag{11}$$

**Proprietà della trasformata di una serie temporale**:
-   **Serie ritardata**: se $F[\{x_n\}] = X_s(\omega),$ allora: 
$$F[\{x_{n-m}\}]=X_s(\omega)e^{-j\omega mT}$$
-   **Convoluzione fra serie temporali**: date due serie temporali $\{x_n\}$ e $\{y_n\}$ la loro convoluzione definisce una nuova serie temporale $\{z_n\}$ espressa da:
$$z_n=\sum_{i=-\infty}^{+\infty}x_iy_{n-i}$$
-   **Convoluzione fra una serie temporale ed una funzione tempo-continua**: date la serie temporale $\{x_n\}$ e la funzione tempo-continua $g(t)$, la loro convoluzione definisce una funzione tempo continua espressa da: 
$$y(t)=\{x_n\}*g(t)=\sum_{n=-\infty}^{+\infty}x_ng(t-nT) \tag{12}$$

# Trasformate 
**Trasformata di un impulso rettangolare** di ampiezza A e durata $\tau$:
$$X(\omega)=\tau Asinc\bigg(\frac{\omega\tau}{2\pi}\bigg)$$
**Segnale PAM, definizione**: Considerata una successione di impulsi rettangolari ottenuta campionando una funzione tempo continua $x(t)$ con intervallo $T$ e mantentendo i valori campionati per un intervallo $\tau < T$. La successione in esame, aventi intervallo di ripetizione e durata costanti, ma ampiezze variabili, costituisce un segnale PAM (*Pulse Amplitude Modulation*). Può essere visto come convoluzione fra la serie temporale $\{x_n\}$ e l'impulso rettangolare $g(t)$, di ampiezza unitaria e durata $\tau$. Si ha: 
$$y(t)=\sum_{n=-\infty}^{+\infty}x_ng(t-nT)=\{x_n\}*g(t)$$

**Trasformata di un segnale PAM** ottenuto da una serie di campioni:
$$Y(\omega)=X_s(\omega)G(\omega)=\frac{1}{T}\sum_{k=-\infty}^{+\infty}X(\omega+k\omega_o)G(\omega)$$
dove la trasformata $G(\omega)$ è definita come:
$$G(\omega)=\tau sinc\bigg(\frac{\omega\tau}{2\pi}\bigg)e^{-j\omega\frac{\tau}{2}} \tag{13}$$

# Trasformata di Fourier Discreta (DFT)
La trasformata discreta di Fourier non si applica più a una serie infinita di termini, ma ad una n-pla cioè ad un vettore.
L'elemento q-esimo dell'n-pla di arrivo è definito come:
$$X_q=\sum_{n=0}^{N-1}x_ne^{-j\frac{2\pi}{N}nq}\qquad q=0,1,...,N-1\tag{14}$$

**Antitrasformata IDFT**: 
La formula che ci restituisce un termine dell'n-pla di partenza a partire da quella di arrivo è la seguente:
$$x_n=\frac{1}{N}\sum_{q=0}^{N-1}X_qe^{j\frac{2\pi}{N}nq}\qquad n=0,1,...,N-1 \tag{15}$$

### TODO: Legame fra trasformata di Fourier discret e continua

# Sistemi lineari
Un sistema ingresso-uscita in cui $x(t)$ indica un segnale d'ingresso tempo-continuo e $y(t)=Q\big[x(t)\big]$ la corrispondente risposta, essa pure tempo-continua. 
Il sistema si dice lineare se:
$$Q\big[c_1x_1(t)+c_2x_2(t)\big]=c_1Q\big[x_1(t)\big]+c_2Q\big[x_2(t)\big]$$

**Sistemi tempo-inviarianti**: se la risposta al segnale ritardato è la risposta ritardata, qualunque sia il ritardo $t_o$:
$$y(t-t_o)=Q\big[x(t-t_o)\big]$$

**Risposta impulsiva di un sistema lineare**: La risposta impulsiva $h(t)$ è definita come la risposta della rete all'impulso di Dirac $\delta(t)$ (ci limitiamo al caso reale). Si consideri in ingresso la funzione ausiliaria $D(t, \Delta)$. La risposta $y_\Delta(t)$ alla funzione ausiliaria è la risposta impulsiva:
$$h(t)=\lim_{\Delta\rightarrow0}y_\Delta(t)$$
Con $x(t)$ segnale generico in ingresso nel dominio dei tempi, la relazione con l'uscita è:
$$y(t)=x(t)*h(t) \tag{16}$$

# Funzione di trasferimento di una rete lineare (FDT)
**Definizione**: Nel dominio delle frequenze, è la trasformata di Fourier della risposta impulsiva:
$$H(\omega)F\big[h(t)\big]$$
E di conseguenza:
$$Y(\omega)=X(\omega)H(\omega)$$

**Ampiezza e Fase**:
$$\begin{cases} T(\omega)=|H(\omega)| \qquad \text{Ampiezza}\\ \beta(\omega)=arg\{H(\omega)\ \qquad \text{Fase}
\end{cases}$$

**Proprietà della FDT** (rete lineare tempo-invariante):
-   **Risposta ad un fasore**: Fasore in ingresso $\rightarrow$ fasore in uscita, medesima frequenza angolare e diverso numero complesso rappresentativo. Se il segnale in ingresso è $x(t)=e^{j\omega_1t}$, la rete risponde con: 
$$y(t)=c_ye^{j\omega_1t}, \qquad c_y=c_xH(\omega_1) \tag{17}$$
-   **Risposta ad una sinusoide**: Sinusoide in ingresso, $h(t)\in\R \rightarrow$ sinusoide in uscita, medesima  frequenza angolare e diversa ampiezza e fase, cioè diverso numero complesso rappresentativo. Se $x(t)=A_xcos(\omega_1t-\varphi_x)$, la rete risponde con (dove $A_y = A_xT(\omega_1)$, e $\varphi_y=\varphi_x+\beta(\omega_1)$):
$$y(t)=A_xT(\omega_1)cos\big[\omega_1t-\varphi_x-\beta(\omega_1)\big]=A_ycos(\omega_1t-\varphi_y)\tag{18}$$
-   **Risposta ad un segnale trasformabile in serie di Fourier**: 
$$X(\omega) \qquad \qquad \qquad \qquad Y(\omega)=X(\omega)Y(\omega) \\ x(t)=\sum_{n=-\infty}^{+\infty}c_ne^{jn\omega_ot} \qquad y(t)=\sum_{n=-\infty}^{+\infty}c_nH(n\omega_o)e^{jn\omega_ot} \\ x(t)= A_o+2\sum_{n=1}^{+\infty}A_ncos\big[n\omega_ot-\theta_n\big] \qquad y(t)=A_oH(0)+2\sum_{n=1}^{+\infty}A_nT(n\omega_o)cos\big[n\omega_ot-\theta_n-\beta(n\omega_o)\big] \\ x(t)= \int_{0}^{+\infty}V(\omega)cos\big[\omega t-\varphi(\omega)\big]d\omega \qquad y(t) = \int_0^{+\infty}V(\omega)T(\omega)cos\big[\omega t - \varphi(\omega) - \beta(\omega)\big]d\omega$$

**FDT sistemi in cascata**: è uguale al prodotto delle funzioni di trasferimento dei vari blocchi:
$$H(\omega)=H(\omega_1)H(\omega_2)...H(\omega_n)\tag{19}$$

# Conversione analogico/digitale tecnica PCM

Il campionamento detto **PCM (Pulse Code Modulation)** prevede tre passaggi:
1.  **Campionamento**: Il campionatore campiona il segnale $x(t)$ ad una frequenza di campionamento $f_o$ prefissata, ottenendo la serie temporale $\{x_n\}, x_n=x(nT)$. Per il teorema di Shannon la frequenza di campionamento dovra essere necessariamente $f_o>2f_m$. La condizione è sufficiente per evitare l'aliasing.
2.  **Quantizzazione**: La serie temporale $\{x_n\}$ è un segnale tempo-discreto, ma non discreto nei valori. Assumento $x(t)$ bilanciato, con valori compresi nell'intervallo $[-M,M]$, i campioni risultano anch'essi compresi in detto intervalo, potendo assumere qualsiasi valore all'interno di esso. Per poter procedere occorre ridurre il numero dei valori da infinito a finito. L'operazione viene detta quantizzazione. L'intervallo su cui opera il quantizzatore, $[-Mq, Mq]$ viene suddiviso in un numero finito di intervalli di quantizzazione, e tutti i valori interni a ciascuno di questi vengono identificati con uno di essi, che indichiamo con $q_n$. La differenza fra campione e valore quantizzato corrispondente si dice "errore" di quantizzazione: $e_n=x_n-q_n$. La lagge di quantizzazione è: $q_n=f(x_n)$. L'aumento del numero di livelli di campionamento diminuisce l'errore di quantizzazione, ma aumenta i bit necessari a rappresentare il segnale.
3.  **Codifica**: Associa ad ognuno degli $L$ livelli che possono essere assunti dai valori quantizzati una parola formata da un certo numero di bit, in modo da avere una corrispondenza biunivoca fra valori ed "etichette" binarie. Si assume che tutte le etichette sono formate dallo stesso numero di bit, che dovra quindi essere : $l\ge \log_2 L$. DI norma conviene prendere $L$ potenza di due. Premesso questo quindi, il codificatore associa ad ogni elemento della serie $\{q_n\}$ una parola di $l$ bit ottenendo una serie di parole binarie $\big\{b_n^1b_n^2...b_n^l\big\}$. Gli elementi di tale serie, anzichè a blocchi di $l$ possono essere pensati come singoli bit, cioè come elementi di una serie binaria con intervallo fra bit, detto tempo di bit, ridotto di un fattore $l$, $T_b=\frac{T}{l}$.

# Conversione digitale/analogica tecnica PCM

LA conversione D/A prevede solo due passi:
1.  **Decodifica**: Si ricostruiscono i valori quantizzati $\{q_n\}$, a partire dalle parole di codice $\{b_n^1b_n^2...b_n^l\}$. Essendo la quantizzazione una operazione non reversibile, la serie $\{q_n\}$ deve necessariamente essere trattata come se fosse la serie $\{x_n\}$ dei valori campionati. L'errore di quantizzazione farà però si che il segnale ricostruito differisca da quello originale, e prende il nome di rumore di quantizzazione: $e(t)=x_r(t)-x(t)$.
2. **Ricostruzione del segnale**:
   1.  **Generazione del segnale PAM**: Si riscostruisce il segnale a partire dal segnale PAM ottenuto come prodotto di convoluzione della serie dei valori quantizzati, equivalente ai campioni, a meno dell'errore dovuto alla quantizzazione, con un impulso rettangolare $g(t)$, di ampiezza unitaria, con origine a $t=0$. Si ottiene quindi il segnale PAM : $y(t)=\{x_n\}*g(t)=\sum_{n=-\infty}^{+\infty}x_ng(t-nT)$
   2.  **Filtratura passa-basso**: Possiamo ricostruire il segnale $x(t)$ a partire da quello PAM, richiamando i risultati ottentui per la trasformata di un segnale PAM: $Y(\omega)=X_s(\omega)G(\omega)=\frac{1}{T}\sum_{k=-\infty}^{+\infty}X(\omega+k\omega_o)G(\omega)$. Si ha in uscita al filtro: $Y(\omega)=X(\omega)\frac{G(\omega)}{T}$.
   3.  **Eventuale equalizzazione**: Per ottener il segnale originario occorre porre in cascata al filtro passa-basso una rete equalizzatrice la cui funzione di trasferimento è data da: $H_e(\omega)\begin{cases} \frac{T}{G(\omega)} \qquad \text{se}\quad |\omega|\le \omega_m \\ \text{qualsiasi} \qquad \text{se} \quad |\omega|>\omega_m
   \end{cases}$

# Teoria della modulazione
**Modulazione**: Modulazione di una oscillazione sinusoidale, a frequenza sufficientemente elevata, detta *portante*. Il segnale $x(t)$ si dice segnale *modulante* in quanto modula le caratteristiche della portante (ampiezza e/o argomento). Il segnale ottenuto $s(t)$ è detto oscillazione *modulata*.

**Espressione della portante non modulata (stato iniziale)**: 
$$s_o(t)=V_ocos\big[\omega_ot-\varphi_o]$$

**Espressione generale di un'oscillazione sinusoidale modulata**: 
$$s(t)=V(t)cos[\varphi(t)]\qquad V(t)\ge 0$$

In relazione all'oscillazione modulata si hanno le seguenti definizioni:
-   $V(t) \rightarrow$ ampiezza istantanea;
-   $\varphi(t)\rightarrow$ fase istantanea;
-   $\omega(t)=\varphi(t) \rightarrow$ pulsazione istantanea; 

In relazione all'oscillazione portante si hanno le seguenti definizioni:
-   $V(t) = V_o\qquad\rightarrow$ ampiezza (costante);
-   $\varphi(t)=\omega_ot-\varphi_o\qquad\rightarrow$ argomento del coseno (lineare in $t$) ;
-   $\omega(t)=\omega_o \qquad\rightarrow$ pulsazione (costante);

**Definizione deviazioni**: in quanto definite come differenze introdotte dalla modulazione. Si chiamano istantanee, perchè dipendono da t.
-   $V(t)-V_o\qquad\rightarrow$ deviazione istantanea di ampiezza;
-   $m(t)=\frac{V(t)-V_o}{V_o}\rightarrow V(t)=V_o\big[1+m(t)\big]\qquad\rightarrow$ deviazione (istantanea) relativa di ampiezza poichè $V(t)\ge0,$ segue $m(t)\ge-1$;
-   $\alpha(t)=\varphi(t)-(\omega_ot-\varphi_o)=\int_{-\infty}^{t}\Delta\omega(\tau)d\tau \qquad\rightarrow$ deviazione istantanea di fase;
-   $\Delta\omega(t)=\omega(t)-\omega_o=\alpha(t)\qquad\rightarrow$ deviazione istantanea di pulsazione;

**Espressione generale di un'oscillazione sinusoidale modulata:** ottenuta introducendo nell'espressione di un'oscillazione modulata la deviazione relativa di ampiezza e la deviazione istantanea di fase:
$$s(t)=V_o\big[1+m(t)\big]cos\big[\omega_ot+\alpha(t)-\varphi_o\big]$$

# Principali modulazioni analogiche
-   **Modulazione di ampiezza (AM)**: la deviazione relativa di ampiezza è proporzionale al segnale modulante; la deviazione di fase è nulla. Viene modificata solo l'ampiezza dell'oscillazione portante. Inoltre in AM $kx(t)\ge-1$ a causa dell'analogo vincolo su $m(t)$, da cui deriva la condizione a destra nella seconda formula:
$$AM=\begin{cases} m(t) = kx(t) \\ \alpha(t) = 0 \end{cases} \\ s(t)=V_o\big[1+kx(t)\big]cos\big[\omega_ot-\varphi_o\big] \qquad \text{con }V_o\big[1+kx(t)\big]\ge0$$
-   **Modulazione di fase (PM)**: la deviazione di fase è proporzionale al segnale modulante; la deviazione relativa di ampiezza è nulla. Dato il legame fra deviazione di fase e deviazione di frequenza in PM si ha $\Delta\omega(t)=\alpha(t)=kx(t)$:
$$PM=\begin{cases} m(t) = 0 \\ \alpha(t)=kx(t) \end{cases} \\ s(t) = V_ocos\big[\omega_ot+kx(t)-\varphi_o\big]$$
-   **Modulazione di frequenza (FM)**: la deviazione di pulsazione è proporzionale al segnale modulante; la deviazione relativa di ampiezza è nulla. Dato il legame fra deviazione e deviazione di frequenza in FM si ha $\alpha(t)=\int_{-\infty}^{t}kx(\tau)d\tau$:
$$FM=\begin{cases} m(t) = 0 \\ \Delta\omega(t)=kx(t) \end{cases} \\ s(t) = V_o\bigg[\omega_ot+k\int_{-\infty}^{t}x(\tau)d\tau-\varphi_o\bigg]$$

**Indice di modulazione AM**: 
$$m_a=max(|m(t)|) \qquad m_a\in[0,1]$$
L'indice vale 0 per assenza totale di modulazione, ed 1 se si ha il massimo della modulazione. $V_{max}$ e $V_{min}$ sono la massima e minima ampiezza che l'oscillazione portante modulata raggiunge:
$$\begin{cases} V_{max} = 2V_o \qquad \text{se } m_a = 1 \\ V_{min}=V_o \qquad \text{se } m_a=0  \end{cases}$$

**Sovramodulazione (modulazione ibrida)**: Se si porta  il modulatore AM in sovramodulazione, ovvero ad avere $k*max(|x(t)|) > 1$, il segnale va in sovramodulazione e la modulazione diventa ibrida (la sovramodulazione di un segnale AM, cambiando la variazione di fase, non è piu un segnale AM). In questo caso si ha:
$$\text{sovramodulazione AM}=\begin{cases} V(t)=V_o(|1+kx(t)|) \qquad \text{poichè } V_o\big[1+kx(t)\big]\ge0 \\
\alpha(t) =  
    \begin{cases}
        0 \qquad \text{se } \quad 1+kx(t) > 0 \\
        \pi \qquad \text{se } \quad 1+kx(t)<0
    \end{cases}
\end{cases}$$

**Teorema fondamentale della modulazione, trasformata del prodotto del segnale con una sinusoide**:
Dato un segnale $x(t)$ dotato di trasformata $X(\omega)$, calcolare la trasformata $S(\omega)$ della funzione: $s(t) = x(t)cos(\omega_ot)$:
$$S(\omega)=\frac{1}{2}X(\omega-\omega_o)+\frac{1}{2}X(\omega+\omega_o) \tag{20}$$

# Inviluppo complesso rappresentativo di oscillazioni modulate
**Definizione**: (estensione del metodo simbolico di Steinmetz). Nell'estensione un'oscillazione sinusoidale, anche se modulata, è ancora vista come parte reale di un fasore, però al posto del numero complesso rappresentativo si ha una funzione complessa del tempo, detta **inviluppo complesso rappresentativo**. Dati:
$$s(t)=V(t)cos\big[\varphi(t)\big] \xrightarrow{conoscendo} \quad \alpha(t)=\varphi(t)-(\omega_ot-\varphi_o) \rightarrow \quad s(t)=V(t)cos\big[\omega_ot+\alpha(t)-\varphi_o \big]$$
Si può scrivere l'inviluppo complesso $i(t)$ come:
$$s(t) = Re\Big\{i(t)e^{j\omega_ot}\Big\} \qquad \text{con} \quad i(t)=V(t)e^{j\big[\alpha(t)-\varphi_o\big]}$$
**Proprietà**: Consideriamo ora due oscillazioni modulate diverse, ma aventi la stessa pulsazione della portante:
$$s_1(t)=Re\Big\{i_1(t)e^{j\omega_ot}\Big\} \qquad \text{con} \quad i_1(t)=V_1(t)e^{j\big[\alpha_1(t)-\varphi_{o1}\big]} \\ s_2(t)=Re\Big\{i_2(t)e^{j\omega_ot}\Big\} \qquad \text{con}\quad i_2(t)=V_2(t)e^{j\big[\alpha_2(t)-\varphi_{o2}\big]}$$
Per la somma risulta:
$$s(t)=s_1(t)+s_2(t)=Re\Big\{i_1(t)e^{j\omega_ot}\Big\}+Re\Big\{i_2(t)e^{j\omega_ot}\Big\}=Re\Big\{\big[i_1(t)+i_2(t)\big]e^{j\omega_ot}\Big\}=Re\Big\{i(t)e^{j\omega_ot}\Big\}$$
dove l'inviluppo complesso della somma è dato dalla somma dei due inviluppi:
$$i(t)=i_1(t)+i_2(t) \tag{21}$$
Si ha:
$$\begin{cases} V(t)=\big|i(t)\big| \\ \alpha(t)=arg\big\{i(t)\big\} \end{cases}$$

# Caratterstiche spettrali di una oscillazione AM
L'inviluppo complesso di una modulazione AM è dato da:
$$i(t)=V_o\big[1+kx(t)\big] \qquad \text{con} \quad V_o\big[1+kx(t)\big]\ge0$$

**Oscillazioni DSB (Double-Side Band)**: La trasformata di $s(t)$ può essere calcolata direttamente tramite la somma di tre termini: portante, banda laterale superiore, banda laterale inferiore:
$$s(t)=V_ocos(\omega_ot)+\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o+\omega)t-\varphi(\omega)\big]d\omega + \frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o-\omega)t+\varphi(\omega)\big]d\omega$$

**Oscillazioni SSB (Single-Side Band)**: Poichè ciascuno dei due segnali corrispondenti alla banda laterale superiore od inferiore contiente la stessa informazione, è possibile eliminare una delle due bande laterali. Viene generato a partire da una oscillazione AM, che viene filtrata con un filtro passa-banda che provveda ad eliminare la banda indesiderata. Le espressioni della SSB sono:
$$s(t)=V_ocos(\omega_ot)+\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o+\omega)t-\varphi(\omega)\big]d\omega \\ s(t)=Re\big\{i(t)e^{j\omega_ot}\big\} \qquad \text{con} \quad i(t)=V_o+\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)e^{j\big[\omega t-\varphi(\omega)\big]}d\omega$$

**Oscillazioni DSB-SC (DSB Suppressed Carrier)**: In essa vengono mantenute entrambe le bande laterali, ma viene eliminata la portante, per risparmiare potenza, senza perdere il contenuto informativo relativo al segnale modulante. DI fatto si ottiene una modulazione a prodotto:
$$s(t)=\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o+\omega)t-\varphi(\omega)\big]d\omega+\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o-\omega)t+\varphi(\omega)\big]d\omega \\ s(t)=Re\big\{i(t)e^{j\omega_ot}\big\} \qquad \text{con} \quad i(t)=\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)e^{j\big[\omega t-\varphi(\omega)\big]}d\omega + \frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)e^{-j\big[\omega t-\varphi(\omega)\big]}d\omega$$

**Oscillazioni SSB-SC (SSB Supressed Carrier)**: A partire da una DSB-SC si elimina anche una delle due bande laterali mediante un filtro. Solitamente la portante non è soppressa del tutto ma solo attenuata, si parla di SSB a portante parzialmente soppressa. 
Le espressioni sono:
$$s(t)=\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o+\omega)t-\varphi(\omega)\big]d\omega \\ s(t)=Re\big\{i(t)e^{j\omega_ot}\big\} \qquad \text{con} \quad i(t)=\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)e^{j\big[\omega t-\varphi(\omega)\big]}d\omega$$

| | $s(t)$ | $s(t)=Re\big\{i(t)e^{j\omega_ot}\big\} \qquad \text{con} \quad i(t)$ 
|-|-|-
**DSB** | $V_ocos(\omega_ot)+\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o+\omega)t-\varphi(\omega)\big]d\omega + \frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o-\omega)t+\varphi(\omega)\big]d\omega$ | -
|**SSB** | $V_ocos(\omega_ot)+\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o+\omega)t-\varphi(\omega)\big]d\omega$ | $V_o+\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)e^{j\big[\omega t-\varphi(\omega)\big]}d\omega$ 
| **DSB-SC** | $\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o+\omega)t-\varphi(\omega)\big]d\omega+\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o-\omega)t+\varphi(\omega)\big]d\omega$| $\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)e^{j\big[\omega t-\varphi(\omega)\big]}d\omega + \frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)e^{-j\big[\omega t-\varphi(\omega)\big]}d\omega$
| **SSB-SC** | $\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)cos\big[(\omega_o+\omega)t-\varphi(\omega)\big]d\omega$| $\frac{V_ok}{2}\int_{\omega_i}^{\omega_m}V(\omega)e^{j\big[\omega t-\varphi(\omega)\big]}d\omega$

# Modulazioni a prodotto
**Modulatore**: La modulazione a prodotto può essere ottenuta direttamente, senza passare dall'AM, facendo il prodotto del segnle modulante $x(t)$ per una sinusoide tramite un circuito detto modulatore a prodotto o "mixer", ottenendo:
$$s(t)=x(t)cos(\omega_ot)$$
L'inviluppo complesso coincide con il segnale modulante: 
$$i(t)=x(t)$$
$$\text{modulazione a prodotto}\quad = \begin{cases} 
    V(t) = |x(t)| \qquad \text{poichè} \quad V(t)\ge0 \\
    \alpha(t)= \begin{cases} 0 \qquad \text {se} \quad x(t)>0 \\ \pi \qquad \text {se} \quad x(t)<0
    \end{cases}
\end{cases} \tag{22}$$
Efficienza:
$$n_f=\frac{\omega_m}{2\omega_m} = \frac{1}{2}$$
Trasformata:
$$S(\omega)=\frac{1}{2}X(\omega-\omega_o)+\frac{1}{2}X(\omega+\omega_o)$$

**Demodulatore**: 
La demodulazione si ottiene rimoltiplicando l'oscillazione modulata per la portante:
$$u(t)=2s(t)cos(\omega_ot)=2x(t)cos^2(\omega_ot)$$

# Modulazioni QAM (Quadrature Amplitude Modulation)
La modulazione QAM consiste di due modulazioni a prodotto con la seconda portante sfasata in anticipo di $\pi/2$.

**Modulatore**: Vi sono due segnali modulanti $x_1(t)$ e $x_2(t)$ aventi le stesse caratteristiche spettrali, e devono essere indipendenti. Si ha:
$$s(t)=x_1(t)cos(\omega_ot)-x_2(t)sin(\omega_ot) \tag{23}$$
L'inviluppo complesso è dato da:
$$i(t)=x_1(t)+jx_2(t)$$
Efficienza:
$$n_f=\frac{\omega_m}{2\omega_m} = \frac{1}{2}$$
**Demodulatore**: E' la somma di due demodulatori a prodotto. Il componente in fase (prima uscita $u_1$), e via in quadratura (seconda uscita $u_2$):
$$u_1(t)=2s(t)cos(\omega_ot)=2x_1(t)cos^2(\omega_ot)-2x_2(t)sin(\omega_ot)cos(\omega_ot) \\ = x_1(t)+x_1(t)cos(2\omega_ot)+x_2(t)sin(2\omega_ot)$$
$$u_2(t)= -2s(t)sin(\omega_ot)=2x_2(t)sin^2(\omega_ot)-2x_1(t)sin(\omega_ot)cos(\omega_ot) \\ = x_2(t)-x_2(t)cos(\omega_ot)-2x_1(t)sin(2\omega_ot)$$

# Segnali ad energia ed a potenza finita
**Potenza istantanea di un segnale**: Dato un segnale $x(t)$ in generale complesso, si definisce:
$$p(t)=x^*(t)x(t)=\big|x(t)\big|^2$$
**Potenza media di un segnale**: Dato un segnale $x(t)$, in generale complesso e definito il prodotto scalare tra funzione continue nel medesimo intervallo come $<f,g>=\int_{-\infty}^{+\infty}f(x)g(x)dx$, si definiscono potenza e potenza media:
$$P=<\big|x(t)\big|^2>=\int_{-\infty}^{+\infty}\big|x(t)\big|^2dt = \lim_{T\rightarrow\infty}\int_{-T/2}^{T/2}\big|x(t)\big|^2dt, \qquad P_m= \frac{1}{T} \lim_{T\rightarrow\infty}\int_{-T/2}^{T/2}\big|x(t)\big|^2dt$$
**Energia di un segnale**: dato un segnale $x(t)$ in generale complesso:
$$E=\int_{-\infty}^{+\infty}\big|x(t)\big|^2dt$$

**Segnale ad energia finita**: Se l'integrale che ne rappresenta l'energia converge. La potenza tende a zero, quindi non può essere anche a potenza finita.

**Segnale a potenza finita**: nel caso in cui l'integrale che ne rappresenta la potenza converga ad un valore diverso da zero.

**Valore efficace**: di una funzione periodica (per un segnale a potenza finita) il valore:
$$x_{eff}=\lim_{T\rightarrow\infty}\sqrt{\frac{1}{T}\int_{-T/2}^{T/2}\big|x(t)\big|^2dt}=\sqrt{P}$$
*Nota:* il valore efficace di una sinusoide $x(t)=Acos(\omega t - \varphi)$ è dato da $A/\sqrt{2}$.

## Segnali ad energia finita

**Funzione di crosscorrelazione**: Dati due segnali in generale complessi, $x(t)$ ed $y(t)$ ad energia finita, il coniugato del prodotto interno di uno di essi per la versione anticipata dell'altro:
$$R_{xy}(\tau)=<x,y_\tau>^*=\int_{-\infty}^{\infty}x^*(t)y(t+\tau)dt$$
**Funzione di autocorrelazione**:
Nel particolare caso in cui $x(t)=y(t)$ prende il nome di autocorrelazione che viene definita:
$$R_{x}(\tau)=<x,x_\tau>^*=\int_{-\infty}^{\infty}x^*(t)x(t+\tau)dt$$
*Nota:* calcolata nell'origine rappresenta l'energia di un segnale.

**Proprietà delle funzioni di cross ed autocorrelazione (energia finita)**:

-   **Proprietà 1**: Per la funzione di crosscorrelazione vale la seguente proprietà:
$$R_{xy}(\tau)=R_{yx}^*(-\tau)$$
-   **Proprietà 2**: Per la funzione di autocorrelazione si ha (simmetria hermitiana):
$$\big|R_x(\tau)\big|\le R_x(0)=E_x$$
-   **Proprietà 3**: Per la funzione di crosscorrelazione vale la seguente relazione (prodotto di convoluzione):
$$R_{xy}(\tau)=x^*(-\tau)*y(\tau)\tag{24}$$

**Densità spettrale di energia (bilatera e riferita alle pulsazioni)**: Dati due segnali complessi $x(t)$ e $y(t)$, se coincidono si ottiene:
$$E_{bil}(\omega)=\frac{F\big|R_x(\tau)\big|}{2\pi}=\frac{\big|X(\omega)\big|^2}{2\pi}$$

**Densità spettrale di energia monolatera** se $x(t)$ è reale:
$$E(\omega)=\begin{cases} 2E_{bil}(\omega) \qquad \text{se} \quad \omega > 0 \\ E_{bil}(\omega) \qquad \text {se} \quad \omega = 0
\end{cases}$$

**Densità riferite alle frequenze**:
$$E_{f,bil}(f)=2\pi E_{bil}(2\pi f)$$

**Trasformazione lineare tempo invariante di spettri di energia**:
Siano $x(t)$ e $y(t)$ segnali rispettivamente in ingresso ed uscita ad una rete lineare tempo invariante, avente risposta impulsiva $h(t)$ e funzione di trasferimento $H(\omega)$:
$$E_{y,bil}(\omega)=\big|H(\omega)\big|^2E_{x,bil}(\omega) \tag{28}$$

## Segnali a potenza finita
**Funzione di crosscorrelazione**:
$$R_{xy}(\tau)=<x,y_\tau>^*=\lim_{T\rightarrow\infty}\frac{1}{T}\int_{-T/2}^{T/2}x^*(t)y(t+\tau)dt$$

**Funzione di autocorrelazione**:
$$R_{x}(\tau)=<x,x_\tau>^*=\lim_{T\rightarrow\infty}\frac{1}{T}\int_{-T/2}^{T/2}x^*(t)x(t+\tau)dt$$
*Nota:* calcolata nell'origine rappresenta la potenza di un segnale.

**Proprietà delle funzioni di crosscorrelazione ed autocorrelazione (potenza finita)**:
-   **Proprietà 1**: Per la funzione di crosscorrelazione vale la seguente proprietà:
$$R_{xy}(\tau)=R_{yx}^*(-\tau)$$
-   **Proprietà 2**: Per la funzione di autocorrelazione si ha (simmetria hermitiana):
$$\big|R_x(\tau)\big|\le R_x(0)=P_x \tag{26}$$

**Densità spettrale di potenza (bilatera, riferita alle pulsazioni)**:
$$P_{bil}=\frac{F\big[R_x(\tau)\big]}{2\pi}$$

**Densità spettrale di potenza monolatera**:
$$P(\omega)=\begin{cases} 2P_{bil}(\omega) \qquad \text{se} \quad \omega > 0 \\ P_{bil}(\omega) \qquad \text{se} \quad \omega = 0
\end{cases}$$

**Densità riferite alle frequenze**:
$$P_{f,bil}(f)=2\pi P_{bil}(2\pi f)$$

**Trasformazione lineare tempo invariante di spettri di potenza**:
$$P_{y,bil}(\omega)=\big|H(\omega)\big|^2P_{x,bil}(\omega) \tag{29}$$

## Segnali periodici a potenza finita
**Funzione di crosscorrelazione**:
$$R_{xy}(\tau)=\frac{1}{T}\int_{-T/2}^{T/2}x^*(t)y(t+\tau)dt$$

**Funzione di autocorrelazione**: 
$$R_x(\tau)=\frac{1}{T}\int^{T/2}_{-T/2}x^*(t)x(t+\tau)dt$$

**Densità spettrale di potenza di segnali periodici**:
$$P_{bil}(\omega)=\frac{F\big[R_x(\tau)\big]}{2\pi}=\sum_{n=-\infty}^{+\infty}|c_n|^2\delta(\omega-n\omega_o)$$
In caso di segnali reali può essere scritta in forma monolatera ($A_0=c_0, A_n=2|c_n|$ con $n>0$):
$$P(\omega)=A_0^2\delta(\omega)+\sum_{n=1}^{+\infty}\frac{A_n^2}{2}\delta(\omega-n\omega_o) \tag{27}$$

**Tabella riassuntiva**:

| | **Segnali a energia finita** | **Segnali a potenza finita** | **Segnali periodici a potenza finita**
|-|-|-| -|
|**Crosscorrelazione** $R_{xy}(\tau)=<x,y_\tau>^*$| $\int_{-\infty}^{\infty}x^*(t)y(t+\tau)dt$ | $\lim_{T\rightarrow\infty}\frac{1}{T}\int_{-T/2}^{T/2}x^*(t)y(t+\tau)dt$ | $R_{xy}(\tau)=\frac{1}{T}\int_{-T/2}^{T/2}x^*(t)y(t+\tau)dt$|
| **Autocorrelazione** $R_{x}(\tau)=<x,x_\tau>^*$| $\int_{-\infty}^{\infty}x^*(t)x(t+\tau)dt$ | $\lim_{T\rightarrow\infty}\frac{1}{T}\int_{-T/2}^{T/2}x^*(t)x(t+\tau)dt$ | $R_x(\tau)=\frac{1}{T}\int^{T/2}_{-T/2}x^*(t)x(t+\tau)dt$
| **Proprietà 1 (crosscorrelazione)** | $R_{xy}(\tau)=R_{yx}^*(-\tau)$ | $R_{xy}(\tau)=R_{yx}^*(-\tau)$ | -
| **Proprietà 2 (autocorrelazione - simmetria hermitiana)** | $\|R_x(\tau)\|\le R_x(0)=E_x$ | $\|R_x(\tau)\|\le R_x(0)=P_x$ | -
**Proprietà 3 (crosscorrelazione - prodotto di convoluzione):** | $R_{xy}(\tau)=x^*(-\tau)*y(\tau)$ | - |-
**Densità spettrale bilatera** $\frac{F\big[R_x(\tau)\big]}{2\pi}$ | $E_{bil}(\omega)=\frac{\big\|X(\omega)\big\|^2}{2\pi}$ | $P_{bil}=\text{uguale}$ | $P_{bil}(\omega)=\sum_{n=-\infty}^{+\infty}\|c_n\|^2\delta(\omega-n\omega_o)$
| **Densità spettrale monolatera** $(\omega>0)$ | $E(\omega)=2E_{bil}(\omega)$ | $P(\omega)=2P_{bil}(\omega)$ | $P(\omega)=A_0^2\delta(\omega)+\sum_{n=1}^{+\infty}\frac{A_n^2}{2}\delta(\omega-n\omega_o)$ 
| **Densità spettrale monolatera** $(\omega = 0)$ | $E_{bil}(\omega)$ | $P_{bil}(\omega)$ | $\text{come sopra, non vi sono due casi in base alle } \omega$
**Densità riferite alle frequenze** | $E_{f,bil}(f)=2\pi E_{bil}(2\pi f)$ | $P_{f,bil}(f)=2\pi P_{bil}(2\pi f)$ | -
| **Trasformazioni lineari tempo invarianti di spettri** | $E_{y,bil}(\omega)=\|H(\omega)\|^2E_{x,bil}(\omega)$ | $P_{y,bil}(\omega)=\|H(\omega)\|^2P_{x,bil}(\omega)$ | -

# Teorema di Parseval generalizzato e condizioni di ortogonalità:
$$\int_{-\infty}^{\infty}x^*(t)y(t)dt=\frac{1}{2\pi}\int_{-\infty}^{\infty}X^*(\omega)Y(\omega)d\omega \tag{25}$$

# Spettri di segnali PAM deterministici
I segnali PAM esprimibili come convoluzione tra una serie temporale $\{a_n\}$ ed un impulso ad energia finita $g(t)$ (impulso rettangolare, di ampiezza unitaria, con origine a t=0):
$$s(t)=\{a_n\}*g(t)=\sum_{n=-\infty}^{+\infty}a_ng(t-nT) \tag{30}$$
-   **Serie temporale ad energia finita**, allora anche il segnale PAM è ad energia finita, e la sua trasformata è:
$$S(\omega)=A_s(\omega)G(\omega)=\frac{1}{T}\sum_{k=-\infty}^{+\infty}A(\omega+k\omega_o)G(\omega)$$
-   **Serie temporale a potenza finita**, allora il segnale PAM è anch'esso a potenza finita e non è possibile trasformarlo secondo Fourier. Calcolandone lo spettro di potenza come:
$$P_{s,bil}(\omega)=\frac{|G(\omega)|^2}{2\pi T}\sum_{k=-\infty}^{+\infty}c_ke^{-jk\omega T}$$
-   **Serie temporale $\{a_n\}$ reale**, la sua autocorrelazione $\{c_n\}$ è reale e pari, per cui la sua trasformata può essere scritta con solo riferimento agli indici positivi ottenendo: 
$$P_{s,bil}(\omega)=\frac{|G(\omega)|^2}{2\pi T}\Bigg[c_o+2\sum_{k=1}^{+\infty}c_kcos(k\omega T)\Bigg]$$
-   **Autocorrelazione nulla per $k$ diverso da zero**, si ottiene:
$$P_{s,bil}(\omega)=\frac{c_o|G(\omega)|^2}{2\pi T}$$

# Spettri di segnali PAM aleatori
Un segnale PAM è aleatorio (processo stocastico) se lo è la serie temporale $\{a_n\}$. 
**Autocorrelazione statistica (a priori)** come media statistica del prodotto delle coppie di valori posti a distanza $k$, ovvero come $E\big[a^*_na_{n+k}\big]$; se la serie è **stazionaria** la probabilità della coppia (congiunta del secondo ordine) $P(a^i, a^l, k)$ non dipende dalla posizione delle due variabili aleatorie all'interno della sequenza ma solo dalla distanza fra gli elementi, cioè da k:
$$c_{stat,k}=E\big[a^*_na_{n+k}\big]=\sum_{i=1}^{L}\sum_{l=1}^{L}(a^i)^*a^lP(a^i, a^l, k) \tag{31}$$
**Potenza statistica** (valore medio del secondo ordine): il valore per k = 0.

**Variabili aleatorie incorrelate** a distanza $k$ se:
$$c_{stat,k}=E\big[a^*_na_{n+k}\big]=\begin{cases}
E\big[|a_n|^2\big] \qquad \text{se} \quad k=0 \\
E\big[a_n^*\big]E\big[a_{n+k}\big]=E\big[a_n^*\big]E\big[a_{n}\big]\qquad \text{se} \quad k \ne 0
\end{cases}$$
Condizione sufficiente per l'incorrelazione è che le variabili aleatorie $a_n$ e $a_{n+k}$ siano indipendenti.

Se la serie è a valor medio nullo e gli elementi della serie aleatoria sono incorrelati si ottiene infine:
$$P_{s,bil})\omega)=\frac{E\big[|a_n|^2\big]\big|G(\omega)\big|^2}{2\pi T}$$

# Cenni sui segnali digitali aleatori in banda base

Il segnale numerico che viene trasmesso è il segnale PAM che si ottiene convolvendo questa serie temporale con l'impulso $g(t)$.

**Codifica binaria**: 
Questa codifica trasforma i bit a "0" in "-1", allo scopo di rendere a balor medio nullo la serie temporale degli $\{a_n\}$ che ovviamente risulta reale.

$$E[a_n]=0$$

$$c_{stat,k}=\begin{cases} E[a_n^2]=1\qquad \text{se}\quad k = 0 \\ E[a_n]E[a_n]=0\qquad \text{se} \quad k \ne 0
\end{cases}$$

**Codifica multilivello**:
E' un'estensione della codifica bipolare, nella quale viene emesso un simbolo ogni $l$ bit, per cui si ha 
$$T=lT_{b}, \qquad f_s=\frac{f_b}{l}$$

I simboli possono assumere i seguenti $L=2^l$ valori:
$$a_n = \pm 1, \pm 3,..., \pm (L-1)$$

Il valor medio è nullo mentre la funzione di autocorrelazione statistica è data da:
$$c_{stat,k}=\begin{cases} E[a_n^2]=\frac{L^2-1}{3} \qquad \text{se} \quad k=0 \\ E[a_n]E[a_n]=0 \qquad \text{se} \quad k \ne 0 
\end{cases} \tag{32}$$

# Spettri dei segnali PAM aleatori con codifica multilivello

Nel caso di codifica multilivello (comprendente il caso bipolare), la autocorrelazione è nulla tranne che nell'origine. Lo spettro del segnale PAM diventa quindi:
$$P_{s,bil}(\omega)=\frac{E\bigg[|a_n|^2\bigg]|G(\omega)|^2}{2\pi T}$$

Se come impulos $g(t)$ si prende l'impulso rettangolare di durata $T$, la sua trasformata è data da:
$$G(\omega)=T\frac{sin(\omega\frac{T}{2})}{\omega\frac{T}{2}}$$

Da cui: 
$$P_{s,bil}(\omega)=\frac{E\bigg[|a_n|^2\bigg]T}{2\pi T} \Bigg| \frac{sin(\omega\frac{T}{2})}{\omega\frac{T}{2}}\Bigg|^2 $$

E passando alle frequenze:

$$=\frac{E\bigg[|a_n|^2\bigg]}{f_s} \Bigg|sinc\bigg(\frac{f}{f_s}\bigg)\Bigg|^2$$

# Dimostrazioni
### 1) Simmetria hermitiana
Ricordando che il coniugato di un numero complesso, è il medesimo numero complesso con la parte immaginaria cambiata
di segno e che il coniugato di un numero/funzione reale, è il medesimo numero/funzione. 
$$c_n^*=\bigg[\frac{1}{T}\int_{-T/2}^{T/2}x(t)e^{-jn\omega_ot}dt\bigg]^*=\frac{1}{T}\int_{-T/2}^{T/2}x(t)e^{jn\omega_ot}dt=\frac{1}{T}\int_{-T/2}^{T/2}\bigg(\sum_{-k=-\infty}^{+\infty}c_{-k}e^{-jk\omega_ot}\bigg)e^{jn\omega_ot}dt \\ = \frac{1}{T}\bigg\{\sum_{-k=-\infty}^{+\infty}c_{-k}\int_{-T/2}^{T/2}e^{-jk\omega_ot}e^{jn\omega_ot}dt\bigg\}=\frac{1}{T}\bigg\{\sum_{-k=-\infty}^{+\infty}c_{-k}\int_{-T/2}^{T/2}e^{j(n-k)\omega_ot}dt\bigg\}$$
L'integrale al secondo membro, data l'ortogonalità dei fasori, è dato da:
$$\int_{-T/2}^{T/2}e^{j(n-k)\omega_ot}dt=\begin{cases} 
T \qquad \text{se} \quad k=n \\ 0 \qquad \text{se} \quad k \ne n
\end{cases}$$
di conseguenza, come volevasi dimostrare, si ha:
$$c_n^*=\bigg[\frac{1}{T}\int_{-T/2}^{T/2}x(t)e^{-jn\omega_ot}dt\bigg]^*=\frac{1}{T}\int_{-T/2}^{T/2}x(t)e^{jn\omega_ot}dt=c_{-n}$$

## 2) Forma in soli coseni dello sviluppo in serie di fourier
Per un segnale reale lo spettro di ampiezza risulta simmetrico rispetto all'origine e quello di fase antisimmetrico nella rappresentazione bilatera, cioè:
$$|c_n|=|c_{-n}| \qquad arg\{c_n\}=-arg\{c_{-n}\}$$
Sfruttando la simmetria hermitiana è possibile manipolare la funzione di sintesi in modo da utilizzare solo le frequenze positive. Spezzando quindi la sommatoria in tre termini e ricordando che la somma di due numeri complessi coniugati è pari a due volte la loro parte reale si ha:
$$x(t)=\sum_{n=-\infty}^{-1}c_ne^{jn\omega_ot}+c_o+\sum_{n=1}^{+\infty}c_ne^{jn\omega_ot}=\sum_{n=1}^{+\infty}c_{-n}e^{-jn\omega_ot}+c_o+\sum_{n=1}^{+\infty}c_ne^{jn\omega_ot} \\ = +c_o+\sum_{n=1}^{+\infty}2Re\{c_ne^{jn\omega_ot}\}=c_o+\sum_{n=1}^{+\infty}Re\{2c_ne^{jn\omega_ot}\}$$
Definendo gli spettri di ampiezza e fase monolateri (in quanto associati alle sole pulsazioni o frequenze positive), come: 
$$\begin{cases} 
A_0=c_0 \qquad \\   
A_n = |c_n| \qquad \text{se} \quad n > 0
\end{cases} \qquad \theta_n=arg\{c_n\}\quad \text{se} \quad n>0, A_n \ne 0$$
Ed operando le seguenti due sostituzioni (il segno della fase è arbitrario): 
$$c_o=A_o \qquad c_n=A_ne^{j\theta_n} \quad \text{se} \quad n>=$$
Si ottiene infine la forma in soli coseni dello sviluppo in serie di Fourier:
$$x(t)=c_0+2\sum_{n=1}^{+\infty}Re\{|c_n|e^{jarg{c_n}}e^{jn\omega_0t}\}=A_0+2\sum_{n=1}^{+\infty}A_ncos[n\omega_0t+\theta_n]$$

## 3) Terza forma seni e coseni senza fasi 
$$x(t)=\frac{a_0}{2}+\sum_{n=1}^{+\infty}Re\big\{(a_n-jb_n)e^{jn\omega_ot}\big\}  = \frac{a_0}{2}+\sum_{n=1}^{+\infty}Re\big\{a_ne^{jn\omega_ot}\big\} + \sum_{n=1}^{+\infty}Re\big\{(-jb_n)e^{jn\omega_ot}\big\} \\ = \frac{a_0}{2}+\sum_{n=1}^{+\infty}a_ncos[n\omega_0t]+\sum_{n=1}^{+\infty}b_nsin[n\omega_0t]$$

## 5) Integrale di fourier
Analogamente a quanto fatto in precedenza, nel caso di
alla formula di sintesi. Quando $x(t)$ reale si possono dare delle espressioni alternative, monolatere, reale, vale la relazione (simmetria hermitiana):
$$X(-\omega)=X^*(\omega)$$
Sfruttando la simmetria hermitiana è possibile manipolare la funzione di sintesi in modo da utilizzare solo le frequenze positive. Spezzando quindi la sommatoria in tre termini e ricordando che la somma di due numeri complessi coniugati è pari a due volte la loro parte reale si ha:
$$x(t)=\frac{1}{2\pi}\Bigg\{\int_{-\infty}^0X(\omega)e^{j\omega t}d\omega+\int_{0}^{+\infty}X(\omega)e^{j\omega t}d\omega\Bigg\}=\frac{1}{2\pi}\Bigg\{\int_{0}^{+\infty}X(-\omega)e^{-j\omega t}d\omega+\int_{0}^{+\infty}X(\omega)e^{j\omega t}d\omega\Bigg\} \\ = \frac{1}{2\pi}\int_{0}^{+\infty}2Re \bigg\{X(\omega)e^{j\omega t}\bigg\} d\omega = \frac{1}{2\pi}\int_{0}^{+\infty}2Re \big\{|X(\omega)|e^{jarg\{X(\omega)\}}e^{j\omega t}d\omega\big\} = \int_0^{+\infty}\frac{|X(\omega)|}{\pi}cos\big[arg{X(\omega)}+\omega t\big]d\omega$$
Da cui definito lo spettro (densità spettrale) di ampiezza monolatero e quello monolatero di fase come:

$$V(\omega)=\frac{|X(\omega)|}{\pi} \qquad \text{se} \quad \omega \ge 0, \qquad \varphi(\omega)=arg\{X(\omega)\} \qquad \text{se} \quad \omega \ge 0, V(\omega)\ne 0$$

Otteniamo la seguente espressione, definita come integrale di Fourier:

$$x(t)=\int_0^{+\infty}V(\omega)cos[\omega t+ \varphi(\omega)]d\omega$$

## 6) Proprieta trasformata fourier
**Coniugazione**:
$$x(t)=\bigg[\frac{1}{2\pi}\int_{-\infty}^{+\infty}X(\omega)e^{j\omega t}d\omega\bigg]^*=\frac{1}{2\pi}\int_{-\infty}^{+\infty}X^*(\omega)e^{-j\omega t}d\omega \\ = \frac{1}{2\pi}\int_{-\infty}^{+\infty}X^*(-\omega)e^{j\omega t}d\omega=F^{-1}\big[X^*(-\omega)\big]$$
**Traslazione temporale**:
$$F[x(t-t_o)]=\int_{-\infty}^{+\infty}x(t-t_o)e^{-j\omega t}dt\\ =\int_{-\infty-t_o}^{+\infty-t_o}x(u)e^{-j\omega(u+t_o)}du \quad \text{con} \begin{cases}
    u=t-t_o, \quad \text{se} \quad t=+\infty \Rightarrow u=+\infty -t_o = +\infty
    \\ t = u-t_o, \quad \text{se} \quad t=-\infty \Rightarrow u=-\infty -t_o=-\infty
    \\ dt = du
\end{cases}
\\ =e^{-j\omega t_o}\int_{-\infty}^{+\infty}x(u)e^{-j\omega u}du = X(\omega)e^{-j\omega t_o} $$
**Derivata**:
$$x'(t)=\frac{d}{dt}\bigg\{\frac{1}{2\pi}\int_{-\infty}^{+\infty}X(\omega)e^{j\omega t}d\omega\bigg\}=\frac{1}{2\pi}\int_{-\infty}^{+\infty}X(\omega)\frac{d}{dt}e^{j\omega t}d\omega = F^{-1}\big[j\omega X(\omega)\big]$$
**Convoluzione**:
$$x(t)*y(t)=\int_{-\infty}^{+\infty}x(\tau)y(t-\tau)d\tau=\int_{-\infty}^{+\infty}x(\tau)\bigg(\frac{1}{2\pi}\int_{-\infty}^{+\infty}Y(\omega)e^{j\omega(t-\tau)}d\omega\bigg)d\tau \\ = \frac{1}{2\pi} \int_{-\infty}^{+\infty}Y(\omega)\bigg(\int_{-\infty}^{+\infty}x(\tau)e^{-j\omega\tau}d\tau\bigg)e^{j\omega t}d\omega = \frac{1}{2\pi} \int_{-\infty}^{+\infty}Y(\omega)X(\omega)e^{j\omega t}d\omega=F^{-1}[Y(\omega)X(\omega)]$$