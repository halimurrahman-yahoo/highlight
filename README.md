# Catatan highlight

Ya. Dengan tiga parameter tambahan ini—**spectral width, echo intensity, serta zonal–meridional–vertical wind**—interpretasi event menjadi jauh lebih kuat daripada hanya melihat \(\sigma^2_{\mathrm{turb,radar}}\).

## 1. Gambaran umum 13 Januari 2020

Ketiga gambar menunjukkan struktur atmosfer yang cukup konsisten. Spectral width relatif besar terdapat pada lapisan sekitar **8–13 km** hampir sepanjang hari, dengan beberapa penguatan sampai sekitar **14–16 km** pada pagi hari. Echo intensity paling kuat berada di troposfer bawah, kira-kira di bawah 8–10 km, sedangkan pada 14–16 km sinyalnya lebih lemah tetapi masih cukup koheren untuk dianalisis. Wind field memperlihatkan **arus zonal yang sangat kuat**, dengan maksimum di sekitar 9–12 km dan kecepatan tetap besar sampai sekitar 15 km.

Event yang paling menarik tetap event yang sebelumnya kita identifikasi dari corrected turbulent variance:

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

Pada South beam, penguatan serupa muncul sekitar 10 menit kemudian pada \(\sim14.4\) km. Jadi event tersebut bukan hanya satu pixel anomalous pada vertical beam.

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

Namun nilai tersebut **belum boleh langsung disebut turbulent variance**, karena spectral width juga dipengaruhi beam broadening dan shear broadening:

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

Materi kuliah memang menjelaskan bahwa vertical beam paling menguntungkan karena SB hilang, sedangkan finite beamwidth masih menghasilkan BB akibat horizontal wind. 

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

Meridional wind juga memperlihatkan perubahan vertikal yang cukup besar. Di sekitar event upper-troposphere/lower-stratosphere tersebut, \(v\) tampak positif dan cukup kuat, secara kasar sekitar orde

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

Vertical wind berbeda dari \(u\) dan \(v\): mean profile-nya dekat nol, tetapi time–height field menunjukkan banyak **alternating positive and negative patches**.

Di sekitar 12–16 km pada pagi hari terdapat beberapa localized vertical motions. Jadi event yang sedang kita lihat tidak terjadi dalam lingkungan dengan \(w=0\) secara sempurna.

Polanya lebih menarik daripada hanya adanya updraft besar, karena terlihat perubahan tanda:

$$
+w \rightarrow -w \rightarrow +w
$$

secara waktu/ketinggian.

Pola demikian dapat konsisten dengan **gravity-wave-associated vertical motion**, meskipun dari gambar ini saja kita belum boleh mengatakan bahwa gravity-wave breaking sudah terbukti.

Interpretasi yang lebih aman adalah:

> enhanced turbulence occurs within a region of strong horizontal shear accompanied by vertically oscillating motions, suggesting that shear instability and/or gravity-wave activity may contribute to the event.

Ini lebih kuat secara ilmiah daripada langsung menyebut Kelvin–Helmholtz instability.

## 6. Echo intensity memberikan QC yang sangat penting

Echo-intensity plot menunjukkan hal menarik. Pada sekitar 14–16 km sinyal masih terdeteksi jelas, walaupun jauh lebih lemah daripada echo di troposfer bawah.

Secara kasar, event upper-level mempunyai echo intensity sekitar belasan sampai dua-puluhan dB, sedangkan pada beberapa lapisan bawah dapat mencapai \(30-40\) dB atau lebih.

Artinya peak spectral width pada 15 km **tidak muncul di daerah tanpa echo**. Jadi parameter Gaussian spectral width masih mempunyai atmospheric signal yang mendasarinya.

Tetapi ada caveat penting.

Pada beberapa lapisan upper troposphere, vertical-beam echo tampak lebih kuat daripada oblique-beam echoes. Ini dapat menunjukkan **aspect sensitivity** dari VHF radar.

Dalam kasus itu vertical echo bisa berasal sebagian dari horizontally stratified refractive-index structures, bukan hanya isotropic turbulent Bragg scattering. Materi kuliah Anda menekankan bahwa vertical enhancement relatif terhadap oblique beams merupakan indikator aspect sensitivity; jika aspect ratio besar, penggunaan spectral width sebagai turbulence estimate menjadi kurang aman. 

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

Ini merupakan tambahan QC yang sangat berguna untuk assignment Anda.

## 7. Sintesis event sekitar 08:15 JST

Kalau semua parameter digabungkan, gambarnya menjadi seperti berikut.

| Parameter                               | Kondisi sekitar event 08:15 JST, 14–16 km                  | Interpretasi                                               |
| --------------------------------------- | ---------------------------------------------------------- | ---------------------------------------------------------- |
| Corrected (\sigma^2_{\rm turb,radar}\) | peak vertical (\sim7.73~{\rm m^2\,s^{-2}}\) pada 15.45 km | strong radial velocity fluctuations                        |
| Spectral width                          | enhanced/broad                                             | consistent with enhanced velocity variance                 |
| Echo intensity                          | measurable, moderate upper-level echo                      | spectral estimate supported by detectable atmospheric echo |
| Zonal wind                              | strong positive/eastward flow                              | event near strong upper-level flow                         |
| \(du/dz\)                               | substantial on upper flank of jet                          | possible shear production of turbulence                    |
| Meridional wind                         | significant, vertically varying                            | adds to total horizontal shear                             |
| \(dv/dz\)                               | non-negligible                                             | additional dynamical shear                                 |
| Vertical wind                           | alternating positive/negative perturbations                | compatible with organized vertical/wave motion             |
| Cross-beam response                     | event appears in more than one beam                        | argues against an isolated numerical outlier               |

Yang paling penting adalah **spatial relationship**:

$$
\boxed{
\text{turbulence maximum}
\approx
\text{upper flank of strong horizontal wind layer}
}
$$

dan bukan tepat di pusat wind maximum.

Ini justru dinamika yang masuk akal. Turbulence yang disebabkan shear sering muncul pada flank dari jet, di mana

$$
\left|\frac{\partial \vec V_h}{\partial z}\right|
$$

lebih besar daripada di jet core sendiri.

## 8. Mekanisme yang paling masuk akal

Berdasarkan data yang ada, urutan interpretasi fisik yang paling kuat adalah

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

Jadi saya akan menginterpretasikan event sebagai:

> **an upper-tropospheric/lower-stratospheric enhanced-turbulence event associated with strong vertical wind shear, possibly modulated by gravity-wave activity.**

Saya belum akan menyebutnya definitif sebagai Kelvin–Helmholtz instability, karena untuk itu idealnya kita perlu menghitung

$$
Ri=
\frac{N^2}{S^2}.
$$

Jika nanti diperoleh

$$
Ri<0.25,
$$

barulah argumen dynamic instability/Kelvin–Helmholtz menjadi jauh lebih kuat.

## 9. Ada kemungkinan gravity-wave–shear interaction

Vertical wind plot sebenarnya membuka interpretasi tambahan yang menarik.

Jika \(w\) menunjukkan alternating upward/downward perturbations sementara \(u\) dan \(v\) juga mengalami perubahan vertikal, kondisi tersebut dapat mengindikasikan gravity wave yang memodulasi background wind shear.

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
S_{\rm total}
=
S_{\rm background}
+
S_{\rm wave}.
$$

Jika shear menjadi cukup besar, wave dapat ikut memicu localized turbulent breakdown.

Ini cocok dengan sifat event yang **terlokalisasi dalam waktu dan altitude**, bukan turbulence kuat yang merata selama 24 jam.

## 10. Satu hal yang perlu dibedakan dari event bawah

Spectral width dan echo intensity juga sangat besar di sekitar beberapa kilometer bawah.

Saya tidak menyarankan menggunakan peak di **2–5 km** sebagai event utama assignment ini tanpa QC tambahan. Di troposfer bawah, high echo power, cloud/precipitation effects, convective motions, hydrometeors, dan strong vertical motions lebih mungkin mengkontaminasi interpretation of Doppler width.

Event sekitar **14–16 km** lebih menarik untuk pembahasan atmospheric clear-air turbulence karena:

* berada dekat strong wind/shear environment,
* terlihat pada beberapa beam,
* mempunyai measurable but not extremely precipitation-like echo intensity,
* vertical wind memperlihatkan wave-like variability,
* dan corrected turbulent variance menunjukkan enhancement yang jelas.

## Versi discussion yang bisa langsung dipakai dalam laporan

> **A notable turbulence event was identified near 14–16 km during approximately 07–09 JST on 13 January 2020. The vertical beam showed a maximum corrected turbulent Doppler variance of approximately \(7.73~\mathrm{m^2\,s^{-2}}\) at 15.45 km around 08:15 JST (23:15 UTC on 12 January). The raw Doppler spectral-width field also showed enhanced values in the same altitude region, and a comparable enhancement was observed by the southward beam, indicating that the feature was not an isolated spectral outlier. Echo intensity remained detectable at these altitudes, supporting the reliability of the spectral-width retrieval, although the stronger vertical-beam echo relative to some oblique beams suggests that aspect sensitivity should be examined.**
>
> **The wind measurements provide a plausible dynamical explanation for the event. A strong eastward zonal flow occupied the upper troposphere, with the turbulence enhancement occurring near the upper flank of the high-speed wind layer where the zonal wind decreased substantially with height. The meridional wind also exhibited appreciable vertical variation, implying that both \(du/dz\) and \(dv/dz\) contributed to the total horizontal wind shear. This configuration is favorable for shear-generated turbulence. In addition, the vertical-wind field exhibited alternating upward and downward perturbations near the event altitude, which may indicate gravity-wave activity. Therefore, the event can reasonably be interpreted as an enhanced-turbulence layer associated primarily with strong vertical wind shear, possibly modulated by gravity waves. Verification of Kelvin–Helmholtz instability would require additional information on static stability and calculation of the gradient Richardson number.**

Satu analisis tambahan yang menurut saya **sangat bernilai sebelum laporan difinalkan** adalah membuat tiga panel baru untuk event 06–10 JST: **\(S=\sqrt{(du/dz)^2+(dv/dz)^2}\), vertical/oblique echo aspect ratio, dan \(\sigma_{\rm turb,radar}^2\)**. Kalau ketiganya peak pada altitude dan waktu yang sama, argumen event turbulence Anda akan jauh lebih kuat.
