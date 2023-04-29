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
Referência: https://www.khronos.org/opengl/wiki/Main_Page

### Pipeline
Referência: https://www.khronos.org/opengl/wiki/Rendering_Pipeline_Overview

A pipeline é um processo com diversas etapas, em muitas, opcionais, que é inicializada uma vez que se tem um programa e objetos que são arrays de vértices préviamente definidos, em uma etapa denominada Vertex Specification, na presença de tais, os vértices são processados e uma etapa chamada Vertex Processing, onde os vértices predefinidos pra renderização podem ser aplicados de um shader para vértices, com operações básicas e arbitrárias per-vertice, após isso é prevista a tesselação, aonde primitivas são aplicadas, conforme necessário, operações de mudanças na topologia, posteriormente é aplicado shaders de geometria, assim em cada e para cada primitiva pode-se aplicar operações para retorno de uma coleção de primitivas, é portanto passado para o pós-processamento dos vertices, começando com uma etapa denominada Transform Feedback, onde a coleção e/ou saída do shader de geometria é engendrado em um buffer de objetos para uso posterior, O que segue na etapa Primitive assembly, montando, baseado nos vértices processados das etapas anteriores, primitivas.

Isso segue na etapa de Clipping, aonde, definido um volume e/ou perspectiva de visão há uma transformação ou recorte de primitivas em outras ou ademais, para permitir que sejam descartadas posteriormente, o que por sua vez compreende a etapa de Face Culling, onde as primitivas (triângulares), são descartadas para renderização, impedindo que se renderize artefatos que não são visíveis.

Ao que segue a Rasterização, onde as primitivas não descartadas, da saída nas etapas anteriores, formam fragmentos, ao que correspondem nos pixels finalmente renderizados no frame, diretamente isso desencadeia o processamento de fragmentos, como uma nova etapa, onde serão aplicados os shaders de fragmento (frag shader), possívelmente aplicando ou manipulando valores de depth, stencil e/ou cor.

Ao fim é pressuposto a etapa de Per-Sample Operations, onde o output do frag shader, é aplicado a um agregado de testes, como Pixel ownership test (overlap de janelas), scissor test (recorte de visão/perspectiva), stencil test (comparação de valores do buffer de stencil), depth test (mesmo do stencil, porem com o buffer de depth), finalizando na operação de color blending, operações lógicas e mascára para remoção de pixels, para engendrar o frame renderizado.

Abaixo podemos visualizar a ilustração do que foi explicado acima.

![opengl](https://user-images.githubusercontent.com/79479170/235012362-c15bc048-5aaf-4d35-b9f9-ca35d4bd2f49.png)

### Shaders
Referência: https://registry.khronos.org/OpenGL-Refpages/gl4/index.php

Referência: https://www.khronos.org/opengl/wiki/OpenGL_Shading_Language
             
Em relação as linguagens de shader suportadas pela API, tem-se a GLSL ou OpenGL Shading Language, uma linguagem estruturada similarmente ao C, propícia ao uso em OpenGL por ser criada e estruturada pelos mesmo criadores, a linguagem recebeu adversas atualizações, com a última versão sendo a 4.60, por fim, similarmente ao que foi dito sobre a pipeline, existe uma wiki e página de documentação com referências para a GLSL, tais que podem ser encontradas abaixo, como segue.

### Aplicação
Agora focando em exemplos de aplicações que utilizam do OpenGL, pode-se atrelar o software Blender, que possui uma engine estruturada em cima (e com várias chamadas), para o OpenGL, além da game engine Unity, mesmo que nesta exista suporte para outras API gráficas, não sendo essencialmente estruturada ou limitada ao OpenGL

### Exemplo de código
Exemplos de códigos "Hello Word" para a API e a liguagem de shader:

- OpenGL

Referência: https://en.wikiversity.org/wiki/OpenGL/Hello_World

```
#include <GL/gl.h>
void initGL(void)
{
    glMatrixMode(GL_PROJECTION);
    glLoadIdentity();
    glOrtho(-RESOLUTION_WIDTH/2, RESOLUTION_WIDTH/2, -RESOLUTION_HEIGHT/2, RESOLUTION_HEIGHT/2, 1, -1);
    glMatrixMode(GL_MODELVIEW);
    glLoadIdentity();
}

void render(void)
{
    glClear(GL_COLOR_BUFFER_BIT);
    glRotatef(1, 0, 0, 1);
    glBegin(GL_TRIANGLES);
        glColor3f(1, 0, 0); glVertex2f( 0,  32); /* Bottom      */
        glColor3f(0, 1, 0); glVertex2f(-32, 0 ); /* Upper Left  */
        glColor3f(0, 0, 1); glVertex2f( 32, 0 ); /* Upper Right */
    glEnd();
}
```

- Shader

Referência: https://thebookofshaders.com/02/

```
#ifdef GL_ES
precision mediump float;
#endif

uniform float u_time;

void main() {
    gl_FragColor = vec4(1.000,0.057,0.124,1.000);
}
```
## Vulkan

Referência: https://vulkan-tutorial.com

### Pipeline
Referência: https://vulkan-tutorial.com/Drawing_a_triangle/Graphics_pipeline_basics/Introduction

Para inicio do processo da pipeline, providos os dados que se quer renderizar, como um agregado a ser processado e transformado em pixels em um tela, a etapa de Vertex Shader roda para cada vértice renderizado na imagem final, resultando nas localizações e parâmetros dos vertices destinados a GPU.

Disso a Tesselização abrange as primitivas dadas nos vértices para gerar outras primitivas, seja da subdivisão da estrutura em detalhes, ou decimação dessa.

Após, é passado o estágio para Geometry Shader, onde a suposição de operações nas primitivas, per vértice, permite manipulação da geometria e primitivas em diferentes geometrias e primitivas.

Posteriomente, a rasterização discretiza as primitivas em fragmentos, contemplando aos pixels que preenchem o buffer do frame, ainda depreendendo de descartar aquilo em que não sentido renderizar, por questões de perspectiva, overlap, etc...

Dado a confecção dos fragmentos, é permissiado a aplicação de shaders de fragmento (frag shader), aplicando operações em cores, luz, profundidade, stencil, mascáras, e mais, antes dos fragmentos serem aplicados em renderização do frame atual.

Tal aplicação compondo, inicialmente, de juntar fragmentos e pixels iguais ou que ocupam igualmente espaços no frame. Dado que o próximo estágio e final para a operação, envolve a composição do frame.

Abaixo podemos visualizar a ilustração do que foi explicado acima.

![img1](https://user-images.githubusercontent.com/64573867/235012678-4d60e11e-087b-4e5e-865e-31adfc3a397d.svg)

### Shaders
Em relação as linguagens de shader suportadas pela API, sabe-se que é necessário que o código de shader seja especificado e codificado em um formado de bytecode denominado SPIR-V.

Ainda sim, podem e geralmente vai se utilizar outras linguagens na programação de shaders para Vulkan, prévio ao SPIR-V, e por tal via, também é possível dizer, em relação as linguagens de shader suportadas pela API, que tem-se a GLSL ou OpenGL Shading Language (devidamente apresentada na seção da API gráfica OpenGL), além da HLSL ou High-Level Shading Language que é uma linguagem de alto nível oficialmente criada pela Microsoft como a linguagem de shading oficial do DirectX

### Aplicação
Frente ao que foi falado anteriormente, e visando citar exemplos de aplicações que utilizam da Vulkan, é passível que se cite aplicações como jogos, a exemplo do Dota 2, além disso pode ser citado a game engine Unreal Engine, tendo que esta possui suporte ao Vulkan, mas não se limita ao mesmo, similarmente a outras engines como a Unity e Source 2 (que também possuem suporte, mas não se limitam à).

### Exemplos de código

Exemplos de códigos "Hello Word" para a API e a liguagem de shader:

- Vulkan

Referência: https://vulkan-tutorial.com/Drawing_a_triangle/Drawing/Rendering_and_presentation

Para essa API gráfica, devido à complexidade e tamanho dos exemplos, segue link para um tutorial do Vulkan para a criação de um "Hello World".

Link:  https://vulkan-tutorial.com/Drawing_a_triangle/Drawing/Rendering_and_presentation

- Shader GLSL

Referência: https://thebookofshaders.com/02/

```
#ifdef GL_ES
precision mediump float;
#endif

uniform float u_time;

void main() {
    gl_FragColor = vec4(1.000,0.057,0.124,1.000);
}
```

- Shader HLSL

Referência:  https://komap.wordpress.com/2009/12/17/hello-world-program-on-hlsl/

```
const int L[18]={
    0xad27, 0xa925, 0xED25, 0xa925, 0xaDB7, 0x0000,
    0x85eE, 0x852b, 0xad2b, 0xf92e, 0x712b, 0x51e9, 0x0000,
    0xC3CF, 0xc36f, 0xc326, 0xc360, 0xf3cf
};
float4 PS(float2 tex : TEXCOORD0):COLOR0
{
    float4 output = float4(0,tex.x,tex.y,1);
    int x= (1-tex.x)*16;
    int y= (1-tex.y)*18;
    //no bitwise ioerations on shadermodel 3 yet :(
    int mask=L[y]*2;
    for (int i = 0; i<16&& i <x; i++)
        mask*=0.5;output.r = ( frac(0.5*mask) < 0.1);
    return output;
}
```
