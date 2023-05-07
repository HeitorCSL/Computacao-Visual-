# Semana 13 Online - Teoria 

### Toon shading

Funciona por renderizar os objetos com cores constantes com os limites delineados, em vez dos grandientes definidos pelas outras técnicas de shading, já que o objetivo é diminuir a variação no shading. Definindo melhor, a técnica de toon shading envolve 3 componentes:
 - Componente difusa, que precisa ser representada por apenas dois valores por cor do material, uma para regiões com brilho e outra para regiões sem brilho; 
 - Componente specular, aonde os destaques pela luz devem ser representadas por uma única cor, quando a intensidade da luz for suficiente;
 - Outline/borda fortemente destacada como uma cor escura.

Para a componente difusa, o conceito é baseado em substituir valores arbitrários de cores (de uma componente difusa das técnicas realisticas de rendering), para 2 cores complementares, uma para regiões com pouca luz e uma para regiões com luz suficiente, ou até outra dinâmica de valores, não sendo limitado à luz. Então, poderia ser feito a limiarização dos valores do gradiente de cor da componente difusa "realistica", em outros valores arbitráriamente definidos, em um processo que pode ser explicado na troca da função/curva de valores continuos de cor, para uma função step, que limiariza e mapeia todos os valores anteriores em apenas 2 valores discretos.

Para a componente especular, de maneira muito correlatada a componente anterior, é suposto de aplicar um limiar ou função step da componente especular dos outros modelos de shader. Entretanto, novamente de maneira similar a componente difusa, é suposto a terem dois valores apenas, deve-se aplicar destaque ou não se deve aplicar destaque, em detrimento do gradiente outrora feito para os modelos realisticos.

Por fim, para a componente de outline, entendida como uma silhueta do objeto, deve-se primeiramente achar os pontos inclusos na silhueta do objeto. Para tal, pode-se utilizar do vetor normal da superfície N, e do vetor view, dado por V, assim, no dot product de N e V, sabe-se quanto da superfície do objeto é vísivel no momento, dado que um valor negativo de N . V está invisível, e do contrário, é visível, assim valores que estejam próximos a zero e por tal, próximos de valores negativos, devem ser marcados com a cor da silhueta por estarem no limiar da parte visível e não-visível do objeto.

### Cel shading

O nome Cel vem do material outrora utilizado para desenho de animações, Celuloide (já que a técnica computa imagens de maneira similar a um desenho feito a mão), e similarmente ao Toon shading, os gradientes utilizados nos shadings convencionais são substituidos por blocos de cores e sombramento, alterando a maneira com que a luz decaí pelos objetos.

De mais a mais, entende-se que as diferenças entre Toon shading e Gouraud ou Phong, está na maneira como o decaimento da luz sob um objeto é tratado, aonde Gouraud calcula a intensidade da luz ou sombreamento por interpolar as cores, eliminando descontinuidades bruscas de intensidade (enquanto não elimina qualquer mudança), e trabalhando com a superfície, no vertex shader, Phong trabalha interpolando o vetor normal, pela superfície (normal da superfície), pegando os valores do vetor normal de um determinado ponto, e calculando a intensidade pela interpolação deste e seus consequentes, assim trabalhando no fragment shader. 

Dessa maneira, os dois funcionam de forma similar, interpolando e definindo neste cálculo um gradiente na intensidade e sombreamento. O Toon shading porém, trabalha definindo limiares e blocos restritos de cores/intensidades, assim não é necessário um cálculo complexo para definição dos valores e implantação da técnica, apenas necessitanto, como antes discutido, de valores máximo mínimo (função step) para componentes difusa e especular (além da deliniação da borda/silhueta).

- Comparação Gouraud/Phong shading:

![comparacao_flat_gouraud_phong](https://user-images.githubusercontent.com/79479170/236689473-69b81daf-ee9d-4e85-aee9-8d3db8902978.png)
