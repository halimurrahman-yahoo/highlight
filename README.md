# Q/A Lesson 3/4


# Exercise:
1. Download the netcdf data from https://www.rish.kyoto-u.ac.jp/radar-group/mu/data/ for 13 January, 2020 (24 hours of MU radar data at a time resolution of 10 min from 2 to 20 km). The spectral width is defined as 2σ1/2 (ms −1). Calculate 2σBB+SB from expressions of slide 39.
2. Calculate σ2turb,radar from the vertical beam.
3. Identify a notable event and discuss it.


# Answer

<img width="430" height="360" alt="Screenshot_2026-09-24_05-49-58" src="https://github.com/user-attachments/assets/6bec5e18-b2dc-4d3f-a4a1-67e173146894" />

Middle Upper (MU) Radar,located at the Shigaraki MU Observatory (34.85°N, 136.10°E) in Japan

Data MU Radar terdiri dari lima beam: vertical, north, east, south, west; empat beam miring berada pada zenith angle 10°. Produk standar mempunyai resolusi waktu 10 menit, resolusi vertikal 150 m, dan mencakup kira-kira 2.025–19.875 km. Nilai `999` adalah missing data. ([RISH][1]) Pada gambar Anda indexing-nya dimulai dari nol, sehingga `Beam 0 = official Beam 1 = vertical`.


<img width="1206" height="1280" alt="image" src="https://github.com/user-attachments/assets/1cfb5b9b-cc17-4a24-a74b-f9a2c816ebc4" />



## 1. Menghitung $\(2\sigma_{BB+SB}\)$

<img width="388" height="303" alt="Screenshot_2026-09-24_07-35-50" src="https://github.com/user-attachments/assets/61269372-337f-4c64-a244-db12e3a0706a" />


<img width="430" height="360" alt="himawari12Jan2026-23UTC" src="https://github.com/user-attachments/assets/503f7ecb-9bc0-435c-8043-5399daf7cb52" />

<img width="430" height="360" alt="chart" src="https://github.com/user-attachments/assets/9c92aad3-61cf-4abd-9076-c719a7338f5b" />

https://www.eorc.jaxa.jp/ptree/
<img width="1361" height="735" alt="windMu" src="https://github.com/user-attachments/assets/d4850d8a-381d-4466-a794-f18fceb9678e" />


<img width="1361" height="735" alt="windMu" src="https://github.com/user-attachments/assets/c84d6ab8-7aa4-4250-bf0e-b9464c010303" />


Prinsip dasarnya adalah memisahkan variance spektrum Doppler menjadi turbulence dan broadening non-turbulent:

$$
\sigma_{\rm obs}^{2}=
\sigma_{\rm turb,radar}^{2}
+
\sigma_{BB+SB}^{2}.
$$

Beam broadening (BB) berasal dari finite radar beam dalam horizontal wind, sedangkan shear broadening (SB) berasal dari variasi wind di dalam radar sampling volume. Yang penting, untuk **vertical beam, shear broadening menjadi nol**, sehingga vertical beam memerlukan koreksi paling sedikit. Penjelasam Prof. Huber.  Pendekatan ini yang sama digunakan dalam studi MU Radar untuk memperoleh turbulent Doppler variance dari vertical beam. ([Springer][2])

Untuk bentuk Dehghan–Hocking yang umum, correction variance dapat ditulis sebagai

$$
\begin{aligned}
\sigma_{BB+SB}^{2} =&
\frac{\theta^2}{k}U^2\cos^2\chi\\
&-a_0\frac{\theta}{k}\sin\chi
\left(
U\frac{\partial U}{\partial z}\zeta
\right)\\
&+
b_0\frac{2\sin^2\chi}{8k}
\left(
\frac{\partial U}{\partial z}\zeta
\right)^2\\
&+
c_0\sin^2\chi\cos^2\chi\,|U\xi|\\
&+
d_0\sin^2\chi\cos^2\chi\,\xi^2 ,
\end{aligned}
$$

dengan

$$
k=4\ln2,
$$

$$
\zeta=2R\theta\sin\chi,
$$

dan

$$
\xi=
\frac{\partial U}{\partial z}
\frac{\Delta R}{\sqrt{12}},
$$

serta

$$
a_0=0.945,\qquad
b_0=1.500,\qquad
c_0=0.030,\qquad
d_0=0.825.
$$

Bentuk ini digunakan untuk menghitung kombinasi beam dan shear broadening dari horizontal wind, vertical shear, beam angle, range dan range resolution. ([ESSD][3])

Yang diminta sebagai spectral-width correction adalah

$$
\boxed{
2\sigma_{BB+SB}=
2\sqrt{\sigma_{BB+SB}^{2}}
}
$$

bukan sekadar menjumlahkan \$(2\sigma_{BB}+2\sigma_{SB}\)$, karena yang bersifat aditif pada formulasi ini adalah **variance**.

### Khusus vertical beam

Untuk vertical beam,

$$
\chi=0^\circ.
$$

Karena

$$
\sin\chi=0,\qquad \cos\chi=1,
$$

semua shear terms hilang. Maka

$$
\boxed{
\sigma_{BB}^{2}=
\frac{\theta^2}{4\ln2}U_h^2
}
$$

dengan

$$
U_h=\sqrt{u^2+v^2}.
$$

Jadi:

$$
\boxed{
2\sigma_{BB}=
2\sqrt{
\frac{\theta^2}{4\ln2}
(u^2+v^2)
}
}
$$

MU Radar memiliki beam full width sekitar \$(3.6^\circ\)$, sehingga one-way half-power **half-width** yang dipakai di persamaan adalah

$$
\theta = 1.8^\circ
       = 0.031416~{\rm rad}.
$$

Sumber terbaru tentang MU Radar juga mengklarifikasi bahwa 3.6° merupakan one-way half-power full width. ([Springer][4])

Sebagai sanity check, misalnya pada suatu level:

$$
U_h=30~{\rm m\,s^{-1}},
$$

maka

$$
\sigma_{BB}^{2}=
\frac{(0.031416)^2(30)^2}
{4\ln2}
\approx0.320~{\rm m^2\,s^{-2}},
$$

sehingga

$$
2\sigma_{BB}\approx1.13~{\rm m\,s^{-1}}.
$$

Ini menunjukkan bahwa pada angin kuat sekalipun BB dapat signifikan, tetapi jauh lebih kecil daripada peak turbulent variance ditunjukkan pada gambar hitungan.

Untuk beam miring, ada satu hal penting: \$(\partial U/\partial z\)$ pada persamaan bukan sembarang magnitude total wind shear, tetapi **shear dari komponen horizontal wind pada vertical plane beam tersebut**. Jadi secara praktis north/south terutama terkait \$(dv/dz\)$, sedangkan east/west terkait \$(du/dz\)$; tanda shear juga penting karena salah satu cross-term dapat positif atau negatif. Prof. Hubert menekankan hal ini. 

---

## 2. Menghitung \$(\sigma_{\rm turb,radar}^2\)$ dari vertical beam

Pertanyaan menyatakan spectral width didefinisikan sebagai

$$
W = 2\sqrt{\sigma_{\rm obs}^{2}},
$$

sehingga

$$
\boxed{
\sigma_{\rm obs}^{2}=
\left(\frac{W}{2}\right)^2
}
$$

dan untuk vertical beam:

$$
\boxed{
\sigma_{\rm turb,radar}^{2}=
\left(\frac{W_{\rm vertical}}{2}\right)^2-
\frac{\theta^2}{4\ln2}(u^2+v^2)
}
$$

atau secara singkat:

$$
\boxed{
\sigma_{\rm turb,radar}^{2}=
\sigma_{\rm obs}^{2}-\sigma_{BB}^{2}
}
$$

karena

$$
\sigma_{SB}^{2}=0
$$

untuk vertical beam.

Untuk Python/Colab, inti perhitungannya cukup:

```python
import numpy as np

# MU radar beam half-width
theta = np.deg2rad(1.8)

# horizontal wind
Uh2 = u**2 + v**2

# observed spectral variance
sigma2_obs = (wdt_vertical / 2.0)**2

# beam-broadening variance
sigma2_BB = (
    theta**2 * Uh2 /
    (4.0 * np.log(2.0))
)

# turbulence-induced variance
sigma2_turb = sigma2_obs - sigma2_BB
```

Untuk plotting biasanya:

```python
sigma2_turb_plot = np.where(
    sigma2_turb >= 0,
    sigma2_turb,
    np.nan
)
```

tetapi untuk analisis statistik jangan langsung membuang semua nilai negatif tanpa mempertimbangkan error measurement; materi kuliah juga mengingatkan bahwa nilai negatif dapat muncul karena uncertainty correction. 

di halaman web RISH menyebut `wdt1...wdt5` sebagai **half-power full width**, sedangkan di soal secara eksplisit mendefinisikannya sebagai \$(2\sqrt{\sigma^2}\)$. ([RISH][1]) Untuk assignment ini mengikuti definisi yang diberikan soal, yaitu memakai \$(W/2\)$. Tidak mengubah  menjadi Gaussian FWHM dengan \$(2\sqrt{2\ln2}\)$. slide 39 konversi?

### Hasil

<img width="1206" height="1280" alt="image" src="https://github.com/user-attachments/assets/ea954b79-cd06-4e21-93d9-25425e7b917e" />


Pada vertical beam, gambar menunjukkan:

$$
\boxed{
\sigma_{\rm turb,radar,max}^{2}
\approx7.730~{\rm m^2\,s^{-2}}
}
$$

pada

$$
\boxed{
z=15.45~{\rm km}
}
$$

dan

$$
\boxed{
t=2020\text{-}01\text{-}12\;23{:}15~UTC
}
$$

yang setara dengan sekitar

$$
08{:}15~{\rm JST}
$$

tanggal 13 Januari.

RMS turbulent radial velocity yang berkaitan dengan variance tersebut adalah

$$
\sigma_{\rm turb}=
\sqrt{7.730}
\approx2.78~{\rm m\,s^{-1}}.
$$

Dengan convention spectral width soal, turbulent contribution terhadap full width adalah

$$
2\sigma_{\rm turb}
\approx5.56~{\rm m\,s^{-1}}.
$$

Jadi angka **7.73 m² s⁻²** pada gambar bukan spectral width; itu sudah merupakan **turbulence-induced Doppler variance**.

Peak yang terlihat pada gambar adalah:

| Beam pada plot | Direction | Peak \(\sigma_{\rm turb}^2\) | UTC          |       Height |
| -------------- | --------- | ---------------------------: | ------------ | -----------: |
| 0              | Vertical  |             **7.730 m² s⁻²** | 12 Jan 23:15 | **15.45 km** |
| 1              | North     |                 8.550 m² s⁻² | 13 Jan 01:05 |     11.70 km |
| 2              | East      |                 7.137 m² s⁻² | 13 Jan 05:35 |      2.55 km |
| 3              | South     |             **8.552 m² s⁻²** | 12 Jan 23:25 | **14.40 km** |
| 4              | West      |                 8.011 m² s⁻² | 13 Jan 09:45 |     13.95 km |

---

# 3. Notable event: sekitar 23 UTC pada 12 Januari / 08 JST 13 Januari

Event terkait dengan nilai terbesar dari kelima beam, juga struktur yang mempunyai coherence dalam waktu–ketinggian dan muncul pada lebih dari satu beam.

Pada gambar terlihat enhanced turbulent variance yang cukup jelas pada sekitar

$$
13-15.5~{\rm km}
$$

mulai kira-kira

$$
20{:}00~UTC
$$

hingga sekitar

$$
01{:}00-02{:}00~UTC.
$$

Di dalam lapisan ini vertical beam mencapai maksimum

$$
7.73~{\rm m^2\,s^{-2}}
$$

pada 15.45 km, 23:15 UTC. Hanya 10 menit kemudian South beam mempunyai peak yang bahkan sedikit lebih besar,

$$
8.552~{\rm m^2\,s^{-2}}
$$

pada 14.40 km, 23:25 UTC.

Ini jauh lebih meyakinkan sebagai **notable turbulence event** daripada, misalnya, peak East beam pada 2.55 km, karena event sekitar 14–15 km merupakan bagian dari struktur yang lebih luas dan terlihat pada beberapa beam.

Saya akan menulis interpretasinya kira-kira seperti ini:

> A notable enhancement of turbulence-induced Doppler variance was observed in the upper troposphere/lower-stratosphere region during the morning of 13 January 2020 JST. The vertical beam showed a maximum corrected variance of approximately \(7.73~{\rm m^2\,s^{-2}}\) at 15.45 km at 23:15 UTC on 12 January (08:15 JST on 13 January). A comparable enhancement was detected by the southward beam about 10 min later at 14.40 km, suggesting that the feature was not merely an isolated spectral-width outlier but was associated with a vertically and horizontally structured region of enhanced velocity fluctuations.

Lalu lanjutkan:

> The vertical-beam result is particularly useful because shear broadening vanishes for a vertically pointing beam, leaving beam broadening as the principal non-turbulent correction. Consequently, the enhanced corrected Doppler variance provides stronger evidence of atmospheric velocity fluctuations than an enhancement observed only in an oblique beam.

Dan untuk mekanismenya saya akan berhati-hati:

> The altitude and layered structure are consistent with turbulence occurring in the upper-troposphere/lower-stratosphere environment. Possible mechanisms include turbulence generated by strong vertical wind shear or gravity-wave breaking. However, the Doppler spectral width alone cannot uniquely distinguish these mechanisms. Confirmation would require examination of the horizontal wind, vertical wind shear, static stability or Brunt–Väisälä frequency, and preferably the gradient Richardson number.

Ini lebih ilmiah daripada langsung menyebutnya Kelvin–Helmholtz instability.

Ada juga ciri menarik bahwa enhanced layer tampak **berubah ketinggian dengan waktu**, bukan berupa satu pixel sporadis. Itu mendukung interpretasi sebagai atmospheric layer yang berevolusi. Perbedaan antara vertical, north, south, east, dan west tidak harus dianggap masalah: pada ketinggian 15 km, beam 10° sudah memandang volume atmosfer beberapa kilometer secara horizontal dari vertical column, sehingga kelima beam memang tidak mengukur volume yang identik. Konfigurasi geometrinya memang demikian. ([AGU Journals][5])

White area yang besar sekitar 03–04 UTC juga jangan ditafsirkan sebagai “zero turbulence”. Karena dataset menggunakan missing value `999`, bagian putih lebih tepat disebut **missing/invalid radar retrievals**. ([RISH][1])

### Kesimpulan yang bisa dipakai untuk menjawab ketiga soal

Secara ringkas, gambar mendukung bahwa observed spectral width pertama-tama diubah menjadi variance melalui

$$
\sigma_{\rm obs}^{2}=(W/2)^2,
$$

kemudian beam- dan shear-broadening dihitung dan dikurangkan. Untuk vertical beam, \(SB=0\), sehingga

$$
\boxed{\sigma_{\rm turb,radar}^{2}=
\left(\frac{W_{\rm vertical}}{2}\right)^2-
\frac{\theta^2}{4\ln2}(u^2+v^2)
}
$$

dengan \$(\theta=1.8^\circ\)$. Hasil plot menunjukkan bahwa event sekitar **23:15 UTC, 15.45 km**, dengan

$$
\boxed{\sigma_{\rm turb,radar}^{2}=7.73~{\rm m^2\,s^{-2}}},
$$

$$
\boxed{\sigma_{\rm turb}\approx2.78~{\rm m\,s^{-1}}},
$$

dan

$$
\boxed{2\sigma_{\rm turb}\approx5.56~{\rm m\,s^{-1}}}.
$$

Cek  **script yang menghasilkan gambar **, bgmn menghitung \$(BB+SB\)$ untuk North/East/South/West. Cross-term Eq. 28 sensitif terhadap **arah dan tanda \$(du/dz\)$ atau \$(dv/dz\)$**. !!!! 


## Parameter —**spectral width, echo intensity, serta zonal–meridional–vertical wind**— sbg interpretasi event unutuk memperkuat \$(\sigma^2_{\mathrm{turb,radar}}\)$.

<img width="617" height="929" alt="20200113 wdt" src="https://github.com/user-attachments/assets/1beb6f00-cadc-496d-b206-d51ace223688" />

<img width="618" height="929" alt="20200113 pwr" src="https://github.com/user-attachments/assets/edc84574-583a-4253-bbdd-053092c19157" />

<img width="621" height="873" alt="20200113 wnd" src="https://github.com/user-attachments/assets/1c4c851e-c8e1-49d5-858c-88384e819ae3" />


## 1. Gambaran umum 13 Januari 2020

Ketiga gambar menunjukkan struktur atmosfer yang cukup konsisten. Spectral width relatif besar terdapat pada lapisan sekitar **8–13 km** hampir sepanjang hari, dengan beberapa penguatan sampai sekitar **14–16 km** pada pagi hari. Echo intensity paling kuat berada di troposfer bawah, kira-kira di bawah 8–10 km, sedangkan pada 14–16 km sinyalnya lebih lemah tetapi masih cukup koheren untuk dianalisis. Wind field memperlihatkan **arus zonal yang sangat kuat**, dengan maksimum di sekitar 9–12 km dan kecepatan tetap besar sampai sekitar 15 km.

Event yang paling menarik tetap event yang sebelumnya  mengidentifikasi dari corrected turbulent variance:

$$
\boxed{t \approx 08{:}15\ {\rm JST},\qquad z\approx15.45~{\rm km}}
$$

atau

$$
\boxed{23{:}15~{\rm UTC}\ {\rm pada\ 12\ Januari}}
$$

dengan vertical-beam corrected variance sekitar

$$
\boxed{\sigma_{\rm turb,radar}^{2}\approx7.73~{\rm m^2\,s^{-2}}}.
$$

Pada South beam, penguatan serupa muncul sekitar 10 menit kemudian pada \$(\sim14.4\)$ km. Jadi event tersebut bukan hanya satu pixel anomalous pada vertical beam.

## 2. Spectral width: indikasi awal peningkatan velocity variance

Gambar spectral width menunjukkan suatu lapisan dengan width besar pada sekitar **13–16 km pada pagi hari**, termasuk sekitar 08 JST. Pada beberapa beam warnanya mencapai kuning–merah, sehingga width jauh lebih besar dibandingkan lapisan di atasnya.

Secara fisik spectral width menggambarkan sebaran radial velocities di dalam radar sampling volume. Jika definisi soal adalah

$$
W=2\sqrt{\sigma_{\rm obs}^{2}},
$$

maka

$$
\sigma_{\rm obs}^{2}=
\left(\frac{W}{2}\right)^2.
$$

Namun nilai tersebut **tidak langsung disebut turbulent variance**, karena spectral width juga dipengaruhi beam broadening dan shear broadening:

$$
\sigma_{\rm obs}^{2}=
\sigma_{\rm turb,radar}^{2}
+
\sigma_{BB+SB}^{2}.
$$

Untuk vertical beam, shear broadening akibat horizontal wind shear hilang secara geometris, sehingga koreksi paling sederhana:

$$
\boxed{
\sigma_{\rm turb,radar}^{2}=
\left(\frac{W_V}{2}\right)^2-
\sigma_{BB}^{2}
}
$$

Prof. Hubert menjelaskan bahwa vertical beam paling menguntungkan karena SB hilang, sedangkan finite beamwidth masih menghasilkan BB akibat horizontal wind. 

Hal ini penting karena gambar wind menunjukkan horizontal wind yang sangat kuat. Dengan demikian, sebagian width yang besar—terutama pada oblique beams—dapat berasal dari **BB+SB**, bukan semuanya turbulence.

## 3. Hubungan dengan zonal wind

Zonal wind merupakan parameter yang paling mencolok dalam event ini. Pada sekitar **9–12 km** terdapat zonal jet dengan kecepatan mencapai bagian atas skala gambar, kira-kira

$$
u \gtrsim 40-50~{\rm m\,s^{-1}}.
$$

Pada 14–16 km, \(u\) masih cukup besar, tetapi berkurang dengan ketinggian. Dengan kata lain, event turbulence sekitar 15 km berada kira-kira pada **upper flank dari strong zonal-wind maximum**.

Ini sangat penting karena menghasilkan

$$
\frac{\partial u}{\partial z}\neq0.
$$

Secara visual, kecepatan zonal maksimum berada di bawah event, kemudian menurun menuju sekitar 15–18 km. Jadi terdapat vertical shear yang nyata.

Interpretasinya menjadi:

$$
\text{strong zonal flow}
\rightarrow
\text{vertical wind shear}
\rightarrow
\text{possible dynamical instability}
\rightarrow
\text{enhanced turbulence}.
$$

Untuk East dan West beams, \(u\) dan terutama

$$
\frac{\partial u}{\partial z}
$$

juga secara langsung masuk ke perhitungan shear broadening. Karena itu raw spectral width East/West tidak boleh dibandingkan langsung dengan vertical beam tanpa koreksi.

## 4. Meridional wind memberikan tambahan shear

Meridional wind juga memperlihatkan perubahan vertikal yang cukup besar. Di sekitar event upper-troposphere/lower-stratosphere tersebut, \$(v\)$ tampak positif dan cukup kuat, secara kasar sekitar orde

$$
10-20~{\rm m\,s^{-1}},
$$

dengan struktur vertikal yang berubah antara kira-kira 10–17 km.

Dengan demikian total horizontal shear sebenarnya adalah

$$
S=
\sqrt{
\left(\frac{\partial u}{\partial z}\right)^2+
\left(\frac{\partial v}{\partial z}\right)^2
}.
$$

Jadi bukan hanya zonal jet yang relevan; perubahan meridional wind juga dapat memperkuat shear total.

Untuk North/South beams, komponen yang sangat penting dalam BB+SB adalah

$$
v,\qquad \frac{\partial v}{\partial z},
$$

sementara untuk East/West beams terutama

$$
u,\qquad \frac{\partial u}{\partial z}.
$$

Inilah salah satu alasan mengapa peak variance dari South beam pada sekitar 14.4 km tidak harus sama dengan vertical beam pada 15.45 km.

## 5. Vertical wind: indikasi adanya organized vertical motion

Vertical wind berbeda dari \$(u\)$ dan \$(v\)$: mean profile-nya dekat nol, tetapi time–height field menunjukkan banyak **alternating positive and negative patches**.

Di sekitar 12–16 km pada pagi hari terdapat beberapa localized vertical motions. Jadi event yang sedang kita lihat tidak terjadi dalam lingkungan dengan \$(w=0\)$ secara sempurna.

Polanya lebih menarik daripada hanya adanya updraft besar, karena terlihat perubahan tanda:

$$
+w \rightarrow -w \rightarrow +w
$$

secara waktu/ketinggian.

Pola demikian apakah konsisten dengan **gravity-wave-associated vertical motion**?, gravity-wave breaking sudah terbukti.


> enhanced turbulence occurs within a region of strong horizontal shear accompanied by vertically oscillating motions, suggesting that shear instability and/or gravity-wave activity may contribute to the event.


## 6. Echo intensity memberikan info penting

Echo-intensity plot menunjukkan hal menarik. Pada sekitar 14–16 km sinyal masih terdeteksi jelas, walaupun jauh lebih lemah daripada echo di troposfer bawah.

Secara kasar, event upper-level mempunyai echo intensity sekitar belasan sampai dua-puluhan dB, sedangkan pada beberapa lapisan bawah dapat mencapai \$(30-40\)$ dB atau lebih.

Artinya peak spectral width pada 15 km **tidak muncul di daerah tanpa echo**. Jadi parameter Gaussian spectral width masih mempunyai atmospheric signal yang mendasarinya.


Pada beberapa lapisan upper troposphere, vertical-beam echo tampak lebih kuat daripada oblique-beam echoes. Ini dapat menunjukkan **aspect sensitivity** dari VHF radar.

Dalam kasus itu vertical echo bisa berasal sebagian dari horizontally stratified refractive-index structures, bukan hanya isotropic turbulent Bragg scattering. Prof. Hubert menjelaskan bahwa vertical enhancement relatif terhadap oblique beams merupakan indikator aspect sensitivity; jika aspect ratio besar, penggunaan spectral width sebagai turbulence estimate menjadi kurang aman. 

Karena itu sebaiknya selanjutnya dihitung

$$
AR=
P_V-
\frac{P_N+P_E+P_S+P_W}{4}
$$

dalam dB.

Sebagai practical criterion dari materi tersebut,

$$
AR\lesssim3-5~{\rm dB}
$$

lebih mendukung isotropic-scattering interpretation, sedangkan nilai yang jauh lebih besar harus diberi caution. 

Perlukah!!!!

## 7. Sintesis event sekitar 08:15 JST

Kalau semua parameter digabungkan, gambarnya menjadi seperti berikut.

| Parameter                               | Kondisi sekitar event 08:15 JST, 14–16 km                  | Interpretasi                                               |
| --------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| Corrected ($\sigma^2_{\rm turb,radar}$) | peak vertical ($\sim7.73~{\rm m^2\,s^{-2}}\$) pada 15.45 km | strong radial velocity fluctuations                        |
| Spectral width                          | enhanced/broad                                             | consistent with enhanced velocity variance                 |
| Echo intensity                          | measurable, moderate upper-level echo                      | spectral estimate supported by detectable atmospheric echo |
| Zonal wind                              | strong positive/eastward flow                              | event near strong upper-level flow                         |
| \(du/dz\)                               | substantial on upper flank of jet                          | possible shear production of turbulence                    |
| Meridional wind                         | significant, vertically varying                            | adds to total horizontal shear                             |
| \(dv/dz\)                               | non-negligible                                             | additional dynamical shear                                 |
| Vertical wind                           | alternating positive/negative perturbations                | compatible with organized vertical/wave motion             |
| Cross-beam response                     | event appears in more than one beam                        | argues against an isolated numerical outlier               |

ada **spatial relationship**:

$$
\boxed{
\text{turbulence maximum}
\approx
\text{upper flank of strong horizontal wind layer}
}
$$

dan bukan tepat di pusat wind maximum.

Turbulence yang disebabkan shear sering muncul pada flank dari jet, di mana

$$
\left|\frac{\partial \vec V_h}{\partial z}\right|
$$

lebih besar daripada di jet core sendiri.

## 8. Perkiraan Mekanisme 

Berdasarkan data yang ada, urutan interpretasi fisik adalah

$$
\text{strong horizontal wind}
$$

$$
\Downarrow
$$

$$
\text{large vertical shear on the upper flank}
$$

$$
\Downarrow
$$

$$
\text{dynamically favorable environment for turbulence}
$$

dan bersamaan dengan itu terdapat vertical-wind fluctuations yang memungkinkan adanya kontribusi gravity waves.

Jadi 

> **an upper-tropospheric/lower-stratospheric enhanced-turbulence event associated with strong vertical wind shear, possibly modulated by gravity-wave activity.**

untuk Kelvin–Helmholtz instability, perlu menghitung

$$
Ri=
\frac{N^2}{S^2}.
$$

Jika nanti diperoleh

$$
Ri<0.25,
$$

argumen dynamic instability/Kelvin–Helmholtz menjadi jauh lebih kuat.

## 9. Apakah gravity-wave–shear interaction?

Vertical wind plot sebenarnya membuka interpretasi tambahan yang menarik.

Jika \$(w\)$ menunjukkan alternating upward/downward perturbations sementara \$(u\)$ dan \$(v\)$ juga mengalami perubahan vertikal, kondisi tersebut dapat mengindikasikan gravity wave yang memodulasi background wind shear.

Secara konseptual:

$$
\text{gravity wave}
\rightarrow
\begin{cases}
u',v'\\
w'
\end{cases}
$$

kemudian pada fase tertentu wave dapat memperkuat background shear:

$$
S_{\rm total}=
S_{\rm background}
+
S_{\rm wave}.
$$

Jika shear menjadi cukup besar, wave dapat ikut memicu localized turbulent breakdown.

Ini sifat event yang **terlokalisasi dalam waktu dan altitude**, bukan turbulence kuat yang merata selama 24 jam.

## 10. Satu hal yang perlu dibedakan dari event bawah

Spectral width dan echo intensity juga sangat besar di sekitar beberapa kilometer bawah.

Peak di **2–5 km** sebagai event utama assignment ini tanpa analisis tambahan. Di troposfer bawah, high echo power, cloud/precipitation effects, convective motions, hydrometeors, dan strong vertical motions lebih mungkin mengkontaminasi interpretation of Doppler width.

Event sekitar **14–16 km** lebih menarik untuk pembahasan atmospheric clear-air turbulence karena:

* berada dekat strong wind/shear environment,
* terlihat pada beberapa beam,
* mempunyai measurable but not extremely precipitation-like echo intensity,
* vertical wind memperlihatkan wave-like variability,
* dan corrected turbulent variance menunjukkan enhancement yang jelas.

## Keimpulan

> **A notable turbulence event was identified near 14–16 km during approximately 07–09 JST on 13 January 2020. The vertical beam showed a maximum corrected turbulent Doppler variance of approximately \$(7.73~\mathrm{m^2\,s^{-2}}\)$ at 15.45 km around 08:15 JST (23:15 UTC on 12 January). The raw Doppler spectral-width field also showed enhanced values in the same altitude region, and a comparable enhancement was observed by the southward beam, indicating that the feature was not an isolated spectral outlier. Echo intensity remained detectable at these altitudes, supporting the reliability of the spectral-width retrieval, although the stronger vertical-beam echo relative to some oblique beams suggests that aspect sensitivity should be examined.**
>
> **The wind measurements provide a plausible dynamical explanation for the event. A strong eastward zonal flow occupied the upper troposphere, with the turbulence enhancement occurring near the upper flank of the high-speed wind layer where the zonal wind decreased substantially with height. The meridional wind also exhibited appreciable vertical variation, implying that both \$(du/dz\)$ and \$(dv/dz\)$ contributed to the total horizontal wind shear. This configuration is favorable for shear-generated turbulence. In addition, the vertical-wind field exhibited alternating upward and downward perturbations near the event altitude, which may indicate gravity-wave activity. Therefore, the event can reasonably be interpreted as an enhanced-turbulence layer associated primarily with strong vertical wind shear, possibly modulated by gravity waves. Verification of Kelvin–Helmholtz instability would require additional information on static stability and calculation of the gradient Richardson number.**

Tambahan tiga panel baru untuk event 06–10 JST: **$\(S=\sqrt{(du/dz)^2+(dv/dz)^2}\)$, vertical/oblique echo aspect ratio, dan \$(\sigma_{\rm turb,radar}^2\)$**. Kalau ketiganya peak pada altitude dan waktu yang sama, argumen event turbulence akan jauh lebih kuat.



<img width="430" height="360" alt="himawari12Jan2026-23UTC" src="https://github.com/user-attachments/assets/503f7ecb-9bc0-435c-8043-5399daf7cb52" />

<img width="430" height="360" alt="chart" src="https://github.com/user-attachments/assets/9c92aad3-61cf-4abd-9076-c719a7338f5b" />

https://www.eorc.jaxa.jp/ptree/


[1]: https://www.rish.kyoto-u.ac.jp/radar-group/mu/data/?utm_source=chatgpt.com "MU Radar Data"
[2]: https://link.springer.com/article/10.1186/s40623-018-0979-1?utm_source=chatgpt.com "Turbulence kinetic energy dissipation rates estimated from concurrent UAV and MU radar measurements | Earth, Planets and Space | Springer Nature Link"
[3]: https://essd.copernicus.org/articles/17/4023/2025/?utm_source=chatgpt.com "ESSD - Low-level atmospheric turbulence dataset in China generated by combining radar wind profiler and radiosonde observations"
[4]: https://link.springer.com/article/10.1007/s44394-025-00002-3?utm_source=chatgpt.com "Statistics of vertical wind velocity measured by MU radar over a 38-year period (1987–2024) in the 2–20 km altitude range | Journal of the Meteorological Society of Japan | Springer Nature Link"
[5]: https://agupubs.onlinelibrary.wiley.com/doi/10.1029/2024JD041677?utm_source=chatgpt.com "A Climatological Study of the Frequency Spectra of Vertical Winds From MU Radar Data (1987–2022) - Luce - 2024 - Journal of Geophysical Research: Atmospheres - Wiley Online Library"
