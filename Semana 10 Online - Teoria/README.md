# Atividade Semana 10

### Pesquisa sobre a utilização dos operadores de gradiente Roberts, Prewitt e Sobel para detectar bordas em uma imagem, usando a linguagem Python.

Para a aplicação dos operadores, foi empregada a função de Convolução, para a extração das informações das bordas e sepração do que é borda e do que não é borda. A partir disso, a filtro será aplicado na imagem de entrada de forma horizontal e vertical, com base em cada operador, e então é feito o calculo de magnitude na imagem processada.
Como saídas temos a imagem original, sua versão após o processamento com o filtro da horizontal, sua versão após o processamento com o filtro da vertical e a imagem após a aplicação da funçaõ de magnitude.

--------------------------------------------
No arquivo notebook acima, há a exemplificação da aplicação dos operadores, com os respectivos códigos.

A imagem utilizada foi a Kodim23.png utilizada em atividades anteriores.



### Referências

https://viceri.com.br/insights/entendendo-de-vez-a-convolucao-base-para-processamento-de-imagens/

https://web.tecgraf.puc-rio.br/~raquelg/compgrafica/trabalho1.html#:~:text=SOBEL%3A%20%C3%89%20um%20filtro%20passa,n%C3%A3o%20linear%20no%20dom%C3%ADnio%20espacial.

https://pt.wikipedia.org/wiki/Filtragem_no_dom%C3%ADnio_espacial#:~:text=Filtro%20n%C3%A3o%20linear,-O%20filtro%20n%C3%A3o&text=O%20filtro%20Roberts%20possui%20a,claro%20do%20que%20as%20bordas.

https://pt.wikipedia.org/wiki/Operador_Prewitt#:~:text=O%20operador%20de%20Prewitt%20%C3%A9%20baseado%20na%20realiza%C3%A7%C3%A3o%20de%20uma,como%20Sobel%20e%20Kayyali%20operadores.

https://www.feis.unesp.br/Home/departamentos/engenhariaeletrica/pos-graduacao/273-dissertacao_patricia.pdf

https://web.fe.up.pt/~ee94010/apsi/estudo2/estudo2.htm

https://www.facom.ufu.br/~backes/gsi058/Aula06-FiltragemEspacial.pdf

https://medium.com/@thiagoluiz.nunes/relat%C3%B3rio-sobre-o-processamento-digital-de-imagens-utilizando-python-c7936143d940

https://www.viniboscoa.dev/blog/manipulacao-de-imagens-com-python-e-opencv-parte-1

https://docs.ufpr.br/~centeno/m_pdi/pdf/jaulapdi03.pdf

https://www.geeksforgeeks.org/introduction-to-convolutions-using-python/

https://medium.com/analytics-vidhya/2d-convolution-using-python-numpy-43442ff5f381

https://iq.opengenus.org/2d-convolution-in-python/

https://pythonguides.com/python-scipy-convolve-2d/

https://pyimagesearch.com/2016/07/25/convolutions-with-opencv-and-python/
