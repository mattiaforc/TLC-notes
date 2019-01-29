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
**Simmetria hermitiana**:
$$c_{-n}=A_{-n}e^{-j\theta_{-n}}=c_n^*=A_ne^{-j\theta_n}\tag{1}$$
**Forma in soli coseni dello sviluppo in serie di Fourier**:
$$x(t)=c_0+2\sum_{n=1}^{+\infty}Re\{|c_n|e^{jarg{c_n}}e^{jn\omega_0t}\}=A_0+2\sum_{n=1}^{+\infty}A_ncos[n\omega_0t+\theta_n]\tag{2}$$
**Terza forma in seni e coseni** (ma senza fasi): definendo i coefficienti monolateri $a_n$, $b_n$, anch'essi reali:
$$a_n=\begin{cases} 2c_0\text{ se }n=0 \\ Re\{{2c_n}\}  \text{ se } n>0  
\end{cases}$$
$$b_n=-Im\{2c_n\} \text{ se } n > 0$$ 
si ha che:
$$x(t)=\frac{a_0}{2}+\sum_{n=1}^{+\infty}a_ncos[n\omega_0t]+\sum_{n=1}^{+\infty}b_nsin[n\omega_0t]\tag{3}$$
Per ricavare direttamente i coefficienti direttamente senza passare dalla conoscenza dei $c_n$:
$$a_n=\frac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}x(t)cos[n\omega_0t]dt \text{ se } n\ge 0$$
$$b_n =  \frac{2}{T}\int_{-\frac{T}{2}}^{\frac{T}{2}}x(t)sin[n\omega_0t]dt \text{ se } n>0\tag{4}$$

# Trasformata ed integrale di Fourier (funzioni aperiodiche tempo continue)
| | Trasformata (analisi, tempi $\Rightarrow$frequenze)| Antitrasformata (sintesi, tempi $\Leftarrow$frequenze)|
|- |-|-|
|Dominio pulsazioni |$X(\omega)=\int_{-\infty}^{+\infty}x(t)e^{-j\omega t}dt$| $x(t)=\frac{1}{2\pi}\int_{-\infty}^{+\infty}X(\omega)e^{j\omega t}d\omega$|
|Dominio frequenze |$X_f(f)=\int_{-\infty}^{+\infty}x(t)e^{-j2\pi ft}dt$| $x(t)=\int_{-\infty}^{+\infty}X_f(f)e^{j2\pi ft}df$|


# Rappresentazioni monolatere (segnali reali); integrale di Fourier
**Integrale di Fourier**: definito $V(\omega)=|\frac{X(\omega)}{\pi}|$, l'integrale di Fourier è:
$$x(t)=\int_0^{+\infty}V(\omega)cos[\omega t+ \varphi(\omega)]d\omega \tag{5}$$
**Proprietà della trasformata di Fourier**:
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
$$x(t)*\delta(t)=\int_{-\infty}^{+\infty}x(\tau)\delta(\tau-t)d\tau=x(t) \\ \Rightarrow x(t)*\delta(t)=<x, \delta_t>=<x(\tau), \delta(\tau-t))>=x(t)$$
-   **Cambio di argomento**:
$$|\alpha|\delta(\alpha t)=\delta(t) \text{ se } \alpha \ne 0 \Rightarrow \delta(\alpha t)=\frac{\delta(t)}{|\alpha|} \text{ se } \alpha \ne 0 \Rightarrow \delta(-x)=\delta(x)$$
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
$$h(t)=\lim_{\Delta\Rightarrow0}y_\Delta(t)$$
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
-   **Risposta ad un fasore**: Fasore in ingresso $\Rightarrow$ fasore in uscita, medesima frequenza angolare e diverso numero complesso rappresentativo. Se il segnale in ingresso è $x(t)=e^{j\omega_1t}$, la rete risponde con: 
$$y(t)=c_ye^{j\omega_1t}, \qquad c_y=c_xH(\omega_1) \tag{17}$$
-   **Risposta ad una sinusoide**: Sinusoide in ingresso, $h(t)\in\R \Rightarrow$ sinusoide in uscita, medesima  frequenza angolare e diversa ampiezza e fase, cioè diverso numero complesso rappresentativo. Se $x(t)=A_xcos(\omega_1t-\varphi_x)$, la rete risponde con (dove $A_y = A_xT(\omega_1)$, e $\varphi_y=\varphi_x+\beta(\omega_1)$):
$$y(t)=A_xT(\omega_1)cos\big[\omega_1t-\varphi_x-\beta(\omega_1)\big]=A_ycos(\omega_1t-\varphi_y)\tag{18}$$

**FDT sistemi in cascata**: è uguale al prodotto delle funzioni di trasferimento dei vari blocchi:
$$H(\omega)=H(\omega_1)H(\omega_2)...H(\omega_n)\tag{19}$$

# Teoria della modulazione
**Modulazione**: Modulazione di una oscillazione sinusoidale, a frequenza sufficientemente elevata, detta *portante*. Il segnale $x(t)$ si dice segnale *modulante* in quanto modula le caratteristiche della portante (ampiezza e/o argomento). Il segnale ottenuto $s(t)$ è detto oscillazione *modulata*.

**Espressione della portante non modulata (stato iniziale)**: 
$$s_o(t)=V_ocos\big[\omega_ot-\varphi_o]$$

**Espressione generale di un'oscillazione sinusoidale modulata**: 
$$s(t)=V(t)cos[\varphi(t)]\qquad V(t)\ge 0$$

In relazione all'oscillazione modulata si hanno le seguenti definizioni:
-   $V(t) \Rightarrow$ ampiezza istantanea;
-   $\varphi(t)\Rightarrow$ fase istantanea;
-   $\omega(t)=\varphi(t) \Rightarrow$ pulsazione istantanea; 

In relazione all'oscillazione portante si hanno le seguenti definizioni:
-   $V(t) = V_o\qquad\Rightarrow$ ampiezza (costante);
-   $\varphi(t)=\omega_ot-\varphi_o\qquad\Rightarrow$ argomento del coseno (lineare in $t$) ;
-   $\omega(t)=\omega_o \qquad\Rightarrow$ pulsazione (costante);

**Definizione deviazioni**: in quanto definite come differenze introdotte dalla modulazione. Si chiamano istantanee, perchè dipendono da t.
-   $V(t)-V_o\qquad\Rightarrow$ deviazione istantanea di ampiezza;
-   $m(t)=\frac{V(t)-V_o}{V_o}\Rightarrow V(t)=V_o\big[1+m(t)\big]\qquad\Rightarrow$ deviazione (istantanea) relativa di ampiezza poichè $V(t)\ge0,$ segue $m(t)\ge-1$;
-   $\alpha(t)=\varphi(t)-(\omega_ot-\varphi_o)=\int_{-\infty}^{t}\Delta\omega(\tau)d\tau \qquad\Rightarrow$ deviazione istantanea di fase;
-   $\Delta\omega(t)=\omega(t)-\omega_o=\alpha(t)\qquad\Rightarrow$ deviazione istantanea di pulsazione;

**Espressione generale di un'oscillazione sinusoidale modulata:** ottenuta introducendo nell'espressione di un'oscillazione modulata la deviazione relativa di ampiezza e la deviazione istantanea di fase:
$$s(t)=V_o\big[1+m(t)\big]cos\big[\omega_ot+\alpha(t)-\varphi_o\big]$$

# Principali modulazioni analogiche
-   **Modulazione di ampiezza (AM)**: la deviazione relativa di ampiezza è proporzionale al segnale modulante; la deviazione di fase è nulla. Viene modificata solo l'ampiezza dell'oscillazione portante. Inoltre in AM $kx(t)\ge-1$ a causa dell'analogo vincolo su $m(t)$, da cui deriva la condizione a destra nella seconda formula:
$$AM=\begin{cases} m(t) = kx(t) \\ \alpha(t) = 0 \end{cases} \\ s(t)=V_o\big[1+kx(t)\big]cos\big[\omega_ot-\varphi_o\big] \qquad \text{con }V_o\big[1+kx(t)\big]\ge0$$
-   **Modulazione di fase (PM)**: la deviazione di fase è proporzionale al segnale modulante; la deviazione relativa di ampiezza è nulla. Dato il legame fra deviazione di fase e deviazione di frequenza in PM si ha $\Delta\omega(t)=\alpha(t)=kx(t)$:
$$PM=\begin{cases} m(t) = 0 \\ \alpha(t)=kx(t) \end{cases} \\ s(t) = V_ocos\big[\omega_ot+kx(t)-\varphi_o\big]$$
-   **Modulazione di frequenza (FM)**: la deviazione di pulsazione è proporzionale al segnale modulante; la deviazione relativa di ampiezza è nulla. Dato il legame fra deviazione e deviazione di frequenza in FM si ha $\alpha(t)=\int_{-\infty}^{t}kx(\tau)d\tau$:
$$FM=\begin{cases} m(t) = 0 \\ \Delta\omega(t)=kx(t) \end{cases} \\ s(t) = V_o\bigg[\omega_ot+k\int_{-\infty}^{t}x(\tau)d\tau-\varphi_o\bigg]$$