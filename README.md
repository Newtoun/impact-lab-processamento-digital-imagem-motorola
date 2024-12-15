# Análise de Luminosidade - Motorola - Impactlab

## Nilton da Silva Nascimento

### Problemática

<p>A clareamento de imagens escuras é uma técnica comum no processamento de imagens que visa melhorar a visibilidade e revelar detalhes ocultos em áreas subexpostas. No entanto, essa prática não está isenta de desafios e pode acarretar diversos problemas que impactam a qualidade final da imagem. Um dos principais problemas é o aumento do ruído presente na imagem, uma vez que clarear as áreas escuras também amplifica os artefatos de ruído, resultando em uma degradação da qualidade visual. Problema que pode ser percebido nos exemplos abaixo.</p>

---

### Experimento

<p>A princípio, eu gostaria de testar a permutação de 7 funções de tratamento de imagem. Porém, considerando 7! = 5040, o tempo médio de 5 minutos no processamento de cada imagem e o total do dataset com cerca de 800 imagens, a execução iria demorar aproximadamente 14 mil dias.</p>

<p>Dado o problema acima, decidi testar a sequência de funções que faz mais sentido para o tratamento e correções de certos casos:</p>

<ul>
  <li>adaptive_histogram_equalization</li>
  <li>logarithmic_transformation</li>
  <li>gamma_correction</li>
  <li>bilateral_filter</li>
  <li>multi_scale_retinex</li>
  <li>color_correction</li>
  <li>sharpen_with_mask</li>
</ul>

---

### Resultados

<p>Os parâmetros dos valores utilizados na melhor métrica foram:</p>

```python
image = adaptive_histogram_equalization(image)
image = logarithmic_transformation(image, 0.8)
image = gamma_correction(image, 10)
image = bilateral_filter(image, 2, 300, 100) # diminuindo diameter
image = multi_scale_retinex(image, [6, 60, 125])
image = color_correction(image, 32)
```
<p>
  === Resultados das Métricas ciclo 1 ===
PSNR Médio: 10.598844353483399
SSIM Médio: 0.44045560096943054

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.06376636364926
NIQE Médio: 0.9152449948326965

=== Resultados das Métricas ciclo 2 ===
PSNR Médio: 14.452315803319802
SSIM Médio: 0.5109691532805469

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.050424466825373
NIQE Médio: 0.9202788266013754

=== Resultados das Métricas ciclo 3 ===
PSNR Médio: 6.5394710880865405
SSIM Médio: 0.22108979199591433

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.05871422388886
NIQE Médio: 0.9449762683901403

=== Resultados das Métricas ciclo 4 ===
PSNR Médio: 14.632920839672384
SSIM Médio: 0.4094723069411472

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.079613120863502
NIQE Médio: 0.8490003738407489

=== Resultados das Métricas ciclo 5 ===
PSNR Médio: 12.809945572804372
SSIM Médio: 0.28991000951859436

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.070292198297974
NIQE Médio: 0.9012029032056713

=== Resultados das Métricas ciclo 6 ===
PSNR Médio: 11.610941968556029
SSIM Médio: 0.24325874444061946

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.08016715334157
NIQE Médio: 0.8697258934023787

=== Resultados das Métricas ciclo 7 ===
PSNR Médio: 11.200994267236817
SSIM Médio: 0.15686299578648505

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.114192707405575
NIQE Médio: 0.6575061301657616

=== Resultados das Métricas ciclo 8 ===
PSNR Médio: 11.586002150816505
SSIM Médio: 0.16195871840826684

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.11198121066211
NIQE Médio: 0.6722418704953833

=== Resultados das Métricas ciclo 9 ===
PSNR Médio: 11.586002150816505
SSIM Médio: 0.16195871840826684

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.11198121066211
NIQE Médio: 0.6722418704953833

=== Resultados das Métricas ciclo 10 ===
PSNR Médio: 13.732880402969828
SSIM Médio: 0.3322285527842765

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.08165996749916
NIQE Médio: 0.783332944076605

=== Resultados das Métricas ciclo 11 ===
PSNR Médio: 10.554944006928178
SSIM Médio: 0.13437595703108415

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.118238852105026
NIQE Médio: 0.6111976586958551

=== Resultados das Métricas ciclo 12 ===
PSNR Médio: 13.32461023046901
SSIM Médio: 0.2881200487932748

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.094334026962137
NIQE Médio: 0.7514729342003093

=== Resultados das Métricas ciclo 13 ===
PSNR Médio: 12.70737333053099
SSIM Médio: 0.3357632253687305

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.093895455840066
NIQE Médio: 0.751300733632048

=== Resultados das Métricas ciclo 14 ===
PSNR Médio: 7.727258179960996
SSIM Médio: 0.2646532383240985

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.10730345930281
NIQE Médio: 0.7490900061456823

=== Resultados das Métricas ciclo 15 ===
PSNR Médio: 7.188235506826052
SSIM Médio: 0.23788308635341676

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.100277466688777
NIQE Médio: 0.7906628544851552

=== Resultados das Métricas ciclo 16 ===
PSNR Médio: 13.342585253372317
SSIM Médio: 0.2765358102249684

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.091493610232245
NIQE Médio: 0.7763156880209495

=== Resultados das Métricas ciclo 17 ===
PSNR Médio: 13.45305871476898
SSIM Médio: 0.2955776611607229

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.07883968957447
NIQE Médio: 0.7987862342060619

=== Resultados das Métricas ciclo 18 ===
PSNR Médio: 11.029113508357963
SSIM Médio: 0.4054926918163132

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.043867448456936
NIQE Médio: 0.8487919477506257

=== Resultados das Métricas ciclo 19 ===
PSNR Médio: 13.418533817166825
SSIM Médio: 0.29394272734113064

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.078688227767174
NIQE Médio: 0.7971724820962895

=== Resultados das Métricas ciclo 20 ===
PSNR Médio: 14.915984889293496
SSIM Médio: 0.4622058072041255

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.0265317352379
NIQE Médio: 0.9061422626749286

=== Resultados das Métricas ciclo 21 ===
PSNR Médio: 11.847593739318889
SSIM Médio: 0.4788379630577406

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.020676869850554
NIQE Médio: 0.8991824300148759

=== Resultados das Métricas ciclo 22 ===
PSNR Médio: 12.046542042399146
SSIM Médio: 0.5246675130626413

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.010207904226124
NIQE Médio: 0.9061409838403133

=== Resultados das Métricas ciclo 23 ===
PSNR Médio: 14.89829490754133
SSIM Médio: 0.4584207950770065

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.027274760194047
NIQE Médio: 0.9039213175752674

=== Resultados das Métricas ciclo 24 ===
PSNR Médio: 14.8970984643092
SSIM Médio: 0.4583423536717545

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.027279449505762
NIQE Médio: 0.9039112893575478

=== Resultados das Métricas ciclo 25 ===
PSNR Médio: 14.916848654521441
SSIM Médio: 0.43887301056052486

BRISQUE e NIQE (menores valores são melhores):
BRISQUE Médio: 19.037722610643304
NIQE Médio: 0.8810591336391026


</p>
