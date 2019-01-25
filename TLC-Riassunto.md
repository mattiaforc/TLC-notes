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