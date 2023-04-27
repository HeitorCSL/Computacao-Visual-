# Semana 11 Online - Teoria

### Grupo

Gustavo de Araujo Ramos Rodrigues  - 32088531

Heitor Ce Sun Lin  - 31930451

Lucca Dias Bartholomei  - 31910017

----------------------------------------------------
Pesquisa sobre APIs gráficas, suas pipelines e shaders suportados.

Para cada API, será apresentada sua explicação, aplicação e exemplificação por meio de um exemplo em código.

-----------------------------------------------------

## OpenGL

### Pipeline
A pipeline é um processo com diversas etapas, em muitas, opcionais, que é inicializada uma vez que se tem um programa e objetos que são arrays de vértices préviamente definidos, em uma etapa denominada Vertex Specification, na presença de tais, os vértices são processados e uma etapa chamada Vertex Processing, onde os vértices predefinidos pra renderização podem ser aplicados de um shader para vértices, com operações básicas e arbitrárias per-vertice, após isso é prevista a tesselação, aonde primitivas são aplicadas, conforme necessário, operações de mudanças na topologia, posteriormente é aplicado shaders de geometria, assim em cada e para cada primitiva pode-se aplicar operações para retorno de uma coleção de primitivas, é portanto passado para o pós-processamento dos vertices, começando com uma etapa denominada Transform Feedback, onde a coleção e/ou saída do shader de geometria é engendrado em um buffer de objetos para uso posterior, O que segue na etapa Primitive assembly, montando, baseado nos vértices processados das etapas anteriores, primitivas.

Isso segue na etapa de Clipping, aonde, definido um volume e/ou perspectiva de visão há uma transformação ou recorte de primitivas em outras ou ademais, para permitir que sejam descartadas posteriormente, o que por sua vez compreende a etapa de Face Culling, onde as primitivas (triângulares), são descartadas para renderização, impedindo que se renderize artefatos que não são visíveis.

Ao que segue a Rasterização, onde as primitivas não descartadas, da saída nas etapas anteriores, formam fragmentos, ao que correspondem nos pixels finalmente renderizados no frame, diretamente isso desencadeia o processamento de fragmentos, como uma nova etapa, onde serão aplicados os shaders de fragmento (frag shader), possívelmente aplicando ou manipulando valores de depth, stencil e/ou cor.

Ao fim é pressuposto a etapa de Per-Sample Operations, onde o output do frag shader, é aplicado a um agregado de testes, como Pixel ownership test (overlap de janelas), scissor test (recorte de visão/perspectiva), stencil test (comparação de valores do buffer de stencil), depth test (mesmo do stencil, porem com o buffer de depth), finalizando na operação de color blending, operações lógicas e mascára para remoção de pixels, para engendrar o frame renderizado.

### Shaders
Em relação as linguagens de shader suportadas pela API, tem-se a GLSL ou OpenGL Shading Language, uma linguagem estruturada similarmente ao C, propícia ao uso em OpenGL por ser criada e estruturada pelos mesmo criadores, a linguagem recebeu adversas atualizações, com a última versão sendo a 4.60, por fim, similarmente ao que foi dito sobre a pipeline, existe uma wiki e página de documentação com referências para a GLSL, tais que podem ser encontradas abaixo, como segue.
