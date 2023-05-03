# Semana 13 Online - Teoria 

Toon shading - funciona por renderizar os objetos com cores constantes com os limites delineados, em vez dos grandientes definidos pelas outras técnicas de shading, já que o objetivo é diminuir a variação no shading. Definindo melhor, a técnica de toon shading envolve 3 componentes:
 - Componente difusa, que precisa ser representada por apenas dois valores por cor do material, uma para regiões com brilho e outra para regiões sem brilho; 
 - Componente specular, aonde os destaques pela luz devem ser representadas por uma única cor, quando a intensidade da luz for suficiente;
 - Outline/borda fortemente destacada como uma cor escura.

Para a componente difusa, o conceito é baseado em substituir valores arbitrários de cores (de uma componente difusa das técnicas realisticas de rendering), para 2 cores complementares, uma para regiões com pouca luz e uma para regiões com luz suficiente, ou até outra dinâmica de valores, não sendo limitado à luz. Então, poderia ser feito a limiarização dos valores do gradiente de cor da componente difusa "realistica", em outros valores arbitráriamente definidos, em um processo que pode ser explicado na troca da função/curva de valores continuos de cor, para uma função step, que limiariza e mapeia todos os valores anteriores em apenas 2 valores discretos.

Para a componente especular, de maneira muito correlatada a componente anterior, é suposto de aplicar um limiar ou função step da componente especular dos outros modelos de shader. Entretanto, novamente de maneira similar a componente difusa, é suposto a terem dois valores apenas, deve-se aplicar destaque ou não se deve aplicar destaque, em detrimento do gradiente outrora feito para os modelos realisticos.

Por fim, para a componente de outline, entendida como uma silhueta do objeto, deve-se primeiramente achar os pontos inclusos na silhueta do objeto. Para tal, pode-se utilizar do vetor normal da superfície N, e do vetor view, dado por V, assim, no dot product de N e V, sabe-se quanto da superfície do objeto é vísivel no momento, dado que um valor negativo de N . V está invisível, e do contrário, é visível, assim valores que estejam próximos a zero e por tal, próximos de valores negativos, devem ser marcados com a cor da silhueta por estarem no limiar da parte visível e não-visível do objeto.
