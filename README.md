# UnrealPetzalLens
<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a id="readme-top"></a>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->


Assignment 3, VIZA 626 Generative Art &amp; Design (Spring 2025)

<!-- PROJECT LOGO -->
<br />
<div align="center">
  </a>

  <h3 align="center">Unreal Petzal Lens</h3>

  <p align="center">
    This project recreates the distinct swirly bokeh effect of the vintage Helios 44-2 lens using a custom post-process material in Unreal Engine. By simulating the optical aberrations and radial blur characteristic of Petzval-style lenses, the shader introduces a dreamy, cinematic depth to out-of-focus areas—especially around the edges of the frame. The effect dynamically responds to camera focus and aperture settings, allowing for real-time artistic control in virtual production and stylized rendering environments.
    <br />
    <a  /> 
    <br />
    <br />
    <a href="https://carhua.myportfolio.com">Carolyn Hua</a>
    &middot;
    <a href="https://sites.google.com/view/viza626/home">VIZA 626</a>
  </p>
</div>

[![finished_shader][images-fig1]](https://example.com)

Figure 1. Ghostly shader showcasing the Fresnel effect. The images display variations in parameter adjustments, including changes to the Fresnel exponent, intensity, and emissive blending, which affect the glow and translucency of the shader.

<!-- Abstract -->
## Abstract
The Fresnel effect describes the relationship between a surface's reflectivity and the viewing angle, making it a critical component in realistic shading. This paper explores the significance of Fresnel in rendering and its role in conveying translucency and energy in visual effects. I detail the implementation of the Fresnel term in a custom ghostly shader, using it to enhance edge lighting and create an ethereal appearance. By manipulating Fresnel intensity and blending it with emissive properties, the shader dynamically responds to viewing angles, reinforcing an illusion of spectral presence. 

[![fresnel_eq][images-fig2]](https://example.com)

Figure 2. Fresnel algorithm used in the ghostly shader. This implementation calculates the rim-lighting effect based on the view angle, enhancing the glow and translucency. Adjusting the exponent and intensity parameters controls the falloff, influencing the final appearance of the spectral effect.

<!-- Introduction and Related Works -->
## Introduction and Related Works

[![fresnel_lake][images-fig3]](https://example.com)
Figure 3. Fresnel on a lake. As the viewing angle becomes steeper, the water appears more reflective, whereas at shallower angles, it looks less reflective and more transparent.

In real-world optics, the Fresnel effect is influenced by polarization, which affects how light reflects based on the orientation of the light wave. However, in computer graphics, particularly for real-time rendering, this effect is often simplified to optimize performance. By omitting polarization, we focus on the relationship between viewing angle and surface reflectivity, a common CG approach that balances realism with efficiency. As John Hable discusses in his blog on filmic rendering [1], Fresnel is present in all materials, influencing how they interact with light, even if they don’t appear reflective at first glance.
This paper explores how the Fresnel effect can be leveraged in shading techniques, such as in a custom ghostly shader, to create an ethereal appearance. By manipulating the intensity and blending it with emissive properties, the shader dynamically responds to viewing angles, enhancing the illusion of spectral presence.

[![incident_angle][images-fig4]](https://example.com)
Figure 4. Incident Angle. The equation and math behind the fresnel effect. 

In Unreal Engine,the Fresnel effect can be leveraged to enhance visual storytelling, particularly in materials that require a sense of translucency or otherworldly presence. By carefully manipulating Fresnel-based shading, artists can create much more complex shading and lighting on assets, allowing for a more realistic rendering of surfaces by accurately simulating how light interacts with different materials. This effect enhances the perception of depth and realism, making objects appear more naturally integrated into their environments.


## Methodology

[![shader_graph][images-fig5]](https://example.com)
Figure 5. This is my complete shader graph used to build my ghostly shader in Unreal. 

In Unreal Engine, the Fresnel Material Expression calculates a falloff effect using the dot product between the surface normal and the camera direction [3]. This value determines how much of the Fresnel effect is applied; 0 when the normal faces the camera directly (no effect) and 1 when perpendicular (full effect). To develop my ghostly shader, I expanded on this Fresnel effect by adjusting its intensity and integrating emissive properties. By modifying the Fresnel exponent, I controlled the sharpness of the glow at different viewing angles. Higher exponents concentrated the glow along the edges, while lower exponents produced a softer, more diffused effect, reinforcing the ethereal aesthetic.

[![inner_fresnel][images-fig6]](https://example.com)
Figure 6. Inner fresnel node graph. 


[![outer_fresnel][images-fig7]](https://example.com)
Figure 7. Outer fresnel node graph. 

To further enhance the spectral presence, I blended the Fresnel term with an emissive color, adjusting bias and scale parameters to control brightness and falloff. This allowed me to fine-tune the shader’s glow intensity and ensure a seamless transition between light and shadow. Additionally, I employed lerp (linear interpolation) functions to dynamically balance the Fresnel effect with other shading components, preventing abrupt transitions and maintaining realism in motion.

Finally, I applied and tested the shader on various assets, including character models and environmental elements to check the look and feel. By comparing different Fresnel exponent values, I observed how the shader influenced the perception of depth and translucency. The final implementation successfully enhanced the spectral quality of materials while maintaining real-time performance, demonstrating how Fresnel-based shading can be effectively used to create immersive supernatural effects in Unreal Engine.

[![test_manny][images-fig8]](https://example.com)

Figure 8. My shader on the mannequin 
## Result and Future Work

[![ghostly_ref][images-fig9]](https://example.com)

Figure 9. My ghostly reference that I worked off of and used as an aesthetic basis. 

The implemented Fresnel-based shader successfully enhanced the perception of translucency and spectral presence in Unreal Engine. By adjusting the Fresnel exponent, intensity, and emissive blending, the shader created a dynamic interaction with viewing angles, reinforcing the illusion of an ethereal form. Testing across different assets demonstrated its versatility, effectively improving the realism of ghostly and translucent materials while maintaining real-time performance.

For future work, Fresnel shading can be explored as a tool for stylization beyond realism. Many non-photorealistic rendering techniques, such as toon shading and painterly effects, use Fresnel to create bold rim highlights that emphasize form and silhouette. By modifying the Fresnel term with custom color gradients, artists can achieve unique aesthetic effects suited for animation, interactive media, or experimental visual styles. Additionally, integrating procedural noise or texture-driven Fresnel variations could enhance artistic expression by allowing more dynamic and unconventional shading responses. Expanding the shader’s flexibility in this way would open new possibilities for creative stylization in real-time rendering.

[![cel_shading][images-fig10]](https://example.com)

Figure 10. Cel Shading 

## Conclusion
[![fresnel_comp][images-fig11]](https://example.com)

Figure 11. Fresnel for realistic shading

The Fresnel effect plays a crucial role in realistic and stylized shading, influencing how materials interact with light based on viewing angles. This paper demonstrated its application in Unreal Engine through a custom ghostly shader, enhancing translucency and spectral presence. By adjusting Fresnel intensity and blending it with emissive properties, the shader created a dynamic, immersive effect. Beyond realism, Fresnel can also be leveraged for artistic stylization, offering new creative possibilities in rendering. Future exploration of procedural techniques and adaptive Fresnel scaling could further expand its use in both photorealistic and stylized visual effects.



<!-- Bibliography -->
## Bibliography 
[1] Hable, John. "Everything Has Fresnel." Filmic Worlds, 5 Dec. 2010, http://filmicworlds.com/blog/everything-has-fresnel/.

[2] Halladay, Kyle. "Fresnel Shaders: From the Ground Up." Kyle Halladay, 18 Feb. 2014, https://kylehalladay.com/blog/tutorial/2014/02/18/Fresnel-Shaders-From-The-Ground-Up.html.

[3] Epic Games, Inc., “Using Fresnel in your Unreal Engine materials,” Epic Games Developer Documentation, Mar. 24, 2025. [Online]. Available: https://dev.epicgames.com/documentation/en-us/unreal-engine/using-fresnel-in-your-unreal-engine-materials.

[4] Racoon Artworks, Fresnel Effect – Why is water reflective?, 2021. Available: https://www.racoon-artworks.de/cgbasics/fresnel.php.

<!-- CONTACT -->
## Contact

Carolyn Hua - chua@tamu.edu

Personal Website: [https://carhua.myportfolio.com](https://carhua.myportfolio.com/)
[2][3]




<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

This work is submitted as part of Assignment 1 for the VIZA 626 course at Texas A&M University, under the instruction of Professor You-Jin Kim, during the Spring 2025 semester.

VIZA 626 Class Website: [https://sites.google.com/view/viza626/](https://sites.google.com/view/viza626/home)

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/othneildrew/Best-README-Template/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/othneildrew/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=for-the-badge
[stars-url]: https://github.com/othneildrew/Best-README-Template/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=for-the-badge
[issues-url]: https://github.com/othneildrew/Best-README-Template/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/othneildrew/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
[product-screenshot]: images/screenshot.png
[images-fig1]: Assignment02_pics/ghostly_shader_finished.png
[images-fig2]: Assignment02_pics/fresnel_eq.png
[images-fig3]: Assignment02_pics/lake_ex.jpg
[images-fig4]: Assignment02_pics/incidentAngle.png
[images-fig5]: Assignment02_pics/shader_graph_full.png
[images-fig6]: Assignment02_pics/Fresnel_inner.png
[images-fig7]: Assignment02_pics/Fresnel_outer.png
[images-fig8]: Assignment02_pics/test_manny.png
[images-fig9]: Assignment02_pics/ghostly_ref.png
[images-fig10]: Assignment02_pics/Toon-shader.jpg
[images-fig11]: Assignment02_pics/fresnel_comp.jpg
[Next.js]: https://img.shields.io/badge/next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white
[Next-url]: https://nextjs.org/
[React.js]: https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB
[React-url]: https://reactjs.org/
[Vue.js]: https://img.shields.io/badge/Vue.js-35495E?style=for-the-badge&logo=vuedotjs&logoColor=4FC08D
[Vue-url]: https://vuejs.org/
[Angular.io]: https://img.shields.io/badge/Angular-DD0031?style=for-the-badge&logo=angular&logoColor=white
[Angular-url]: https://angular.io/
[Svelte.dev]: https://img.shields.io/badge/Svelte-4A4A55?style=for-the-badge&logo=svelte&logoColor=FF3E00
[Svelte-url]: https://svelte.dev/
[Laravel.com]: https://img.shields.io/badge/Laravel-FF2D20?style=for-the-badge&logo=laravel&logoColor=white
[Laravel-url]: https://laravel.com
[Bootstrap.com]: https://img.shields.io/badge/Bootstrap-563D7C?style=for-the-badge&logo=bootstrap&logoColor=white
[Bootstrap-url]: https://getbootstrap.com
[JQuery.com]: https://img.shields.io/badge/jQuery-0769AD?style=for-the-badge&logo=jquery&logoColor=white
[JQuery-url]: https://jquery.com 
