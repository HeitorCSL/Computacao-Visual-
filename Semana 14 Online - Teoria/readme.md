# Semana 14 Online - Teoria 

Os resultados obtidos nas operações tex1 * tex2 e mul(tex1, tex2) podem ser diferentes devido à forma como essas operações são definidas 
nas linguagens de shader, como HLSL.

Quando você usa o operador * entre duas texturas (tex1 * tex2), o resultado depende da implementação específica do operador de 
multiplicação para texturas na linguagem de shader que você está usando. Normalmente, o operador * aplicado a texturas é usado para 
realizar uma operação conhecida como "modulação". Nesse caso, os valores dos pixels das duas texturas são multiplicados componente por 
componente, resultando em uma nova textura onde cada componente é o produto dos componentes correspondentes das texturas originais.

Por outro lado, a função mul(tex1, tex2) é uma função específica de multiplicação fornecida pela linguagem de shader HLSL. Essa função é 
projetada para realizar a multiplicação entre os valores das texturas tex1 e tex2 da mesma maneira que o operador * aplicado a valores 
numéricos. Ou seja, a função mul opera multiplicando os valores de cada componente das texturas, independentemente do tipo de dado 
(textura, número ou outro tipo) que está sendo multiplicado.

Portanto, a diferença entre tex1 * tex2 e mul(tex1, tex2) está relacionada à forma como a multiplicação é tratada nas implementações 
específicas dessas operações em uma linguagem de shader. Se a linguagem de shader que você está usando define o operador * para realizar 
uma modulação entre texturas, o resultado será diferente da função mul, que realiza uma multiplicação direta dos valores das texturas.

--------------------------------------

### Referências

http://www.univasf.edu.br/~jorge.cavalcanti/comput_graf14_Texturas2.pdf

https://www.lcg.ufrj.br/cg/downloads/PDFs/17_LCG_Texturas.pdf

https://www.dca.fee.unicamp.br/courses/IA725/1s2009/slides/textura.pdf

https://learn.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl

https://en.wikipedia.org/wiki/High-Level_Shader_Language

https://www.codinblack.com/texture-mapping-in-cg-hlsl/

https://learn.microsoft.com/pt-br/windows/win32/direct3dhlsl/dx-graphics-hlsl-per-component-math

https://microsoft.github.io/DirectX-Specs/d3d/HLSL_SM_6_7_Advanced_Texture_Ops.html

https://learn.microsoft.com/pt-br/windows/win32/direct3dhlsl/dx-graphics-hlsl
