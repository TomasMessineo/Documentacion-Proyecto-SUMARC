
### Lunes 10/8
# DistLearn: Entrenamiento de orden cero descentralizado por capas mediante descenso de coordenadas por bloques, basado en teoría de juegos.

Filtrado de partículas y teoría de juegos -> fundamento para el algoritmo.
Cada capa es una función o un jugador. Asociado al mismo está el espacio donde viven sus coeficientes. 
Si tengo 2 partículas o dos configuraciones para una capa y miro la diferencia encontrada de verosimilitud, la diferencia que veo en la red completa es la misma que veo en las capas. Una mejora que produce una capa, es una mejora que se va a reflejar completamente en toda la red. Esto me permite ir por turnos mejorando cada capa. 
Se adotpa una distribución Cauchy como función de verosimilitud. DistLearn no estima el gradiente, pero se puede planear.

La ventaja de DistLearn es que es un algoritmo que no explota por la dimensionalidad. En este caso se tienen particulas que reducen la dispersión. Soluciona los grandes problemas que tienen lso grandes algoritmos evolutivos en general. 

- Equilibrio de nash.
- ADAM (en python)
- Distribución Cauchy

---
# 