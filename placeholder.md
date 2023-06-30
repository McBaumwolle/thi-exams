# Human Pose Estimation 
<!--- to be continued --->

# Generative Adversarial Networks
Ziel ist es, künstliche Daten zu generieren, die von echten Daten nicht zu unterscheiden sind. <br>

## Aufbau 
Zur Visualisierung von GANs, siehe [ganlab](https://poloclub.github.io/ganlab/), [Playground](https://reiinakano.com/gan-playground/) und [Image2Image](https://affinelayer.com/pixsrv/). <br>

**Generator** <br>
Generiert Daten, die weiter zum Discriminator gegeben werden. <br>

**Discriminator** <br>
Versucht zu erkennen, ob die Daten vom Generator oder vom echten Datensatz stammen. <br>

<img src="resources/cv/18_gan.png" width="500">

Das Training kann sehr lange (bis zu mehreren Wochen) dauern, es gibt keine gute Methode zur Evaluation - menschliches Einschreiten ist notwendig. 

## Probleme
Falls der Generator zu gut wird, kann der Discriminator nicht mehr lernen, auch wenn noch Verbesserungspotential vorhanden ist.

**Mode Collapse** <br>
Der Generator generiert immer die selben Daten, die der Discriminator nicht mehr unterscheiden kann und somit nicht mehr lernen kann. 


## Typen

**deep convolutional GANs** <br>
...

**minibatch GANs** <br>
...

**conditional GANs** <br>
...
