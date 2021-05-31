---
layout: post
toc: true
---
[toc]

You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. You can rebuild the site in many different ways, but the most common way is to run `jekyll serve`, which launches a web server and auto-regenerates your site when a file is updated.

To add new posts, simply add a file in the `_posts` directory that follows the convention `YYYY-MM-DD-name-of-post.ext` and includes the necessary front matter. Take a look at the source for this post to get an idea about how it works.

$$ x = y^2 $$

$$mean = \frac{\displaystyle\sum_{i=1}^{n} x_{i}}{n}$$

Jekyll also offers powerful support for code snippets:

{% highlight ruby %}
def print_hi(name)
  puts "Hi, #{name}"
end
print_hi('Tom')
#=> prints 'Hi, Tom' to STDOUT.
{% endhighlight %}

## Chapter 1 URP Shader Basic Term
### Section 1

``` c
// Shader 시작. 셰이더의 폴더와 이름을 여기서 결정합니다.
Shader "URPTraining/URPBasic"
{
  Properties
  {   
    // Properties Block 
  }  

  SubShader
  {  
    Tags
    {
      //Render type과 Render Queue를 여기서 결정합니다.
      "RenderPipeline"="UniversalPipeline"
      "RenderType"="Opaque"          
      "Queue"="Geometry"
     }
     Pass
     {  		
       Name "Universal Forward"
       Tags { "LightMode" = "UniversalForward" }

       HLSLPROGRAM

       #pragma prefer_hlslcc gles
       #pragma exclude_renderers d3d11_9x
       #pragma vertex vert
       #pragma fragment frag

       #include "Packages/com.unity.render-pipelines.universal/  	 ShaderLibrary/Lighting.hlsl"        	
  
       //vertex buffer에서 읽어올 정보를 선언합니다. 	
       struct VertexInput
       {
         float4 vertex : POSITION;
       };

       //보간기를 통해 버텍스 셰이더에서 픽셀 셰이더로 전달할 정보를 선언합니다.
       struct VertexOutput
       {
         float4 vertex : SV_POSITION;
       };

       //버텍스 셰이더
       VertexOutput vert(VertexInput v)
       {
         VertexOutput o;      
         o.vertex = TransformObjectToHClip(v.vertex.xyz);

         return o;
        }

        //픽셀 셰이더
        half4 frag(VertexOutput i) : SV_Target
        {  	
          return half4(0.5 , 0.5, 0.5, 1);  
        }
        ENDHLSL  
    }
  }
}
```

## Chapter 1 URP Shader Basic Term
### Section 1
### Section 1


## Chapter 1 URP Shader Basic Term
### Section 1
### Section 1

| Priority apples | Second priority | Third priority |
|-------|--------|---------|
| ambrosia | gala | red delicious |
| pink lady | jazz | macintosh |
| honeycrisp | granny smith | fuji |

| Type   | Name        |     Header      | 로컬 공간 (모델 공간)의 정점 위치       |
| ------ | ----------- | :-------------: | --------------------------------------- |
| float4 | vertex      |  **POSITION**   | 버텍스의 노멀                           |
| float3 | normal      |   **NORMAL**    | 버텍스의 노멀                           |
| float4 | texcoord[n] | **TEXCOORD[n]** | 버텍스의 UV 좌표.                       |
| float4 | tangent     |   **TANGENT**   | 메시에서 계산된 또는 import된 탄젠트 값   |
| float4 | color       |    **COLOR**    | 버텍스의 컬러값.                        |