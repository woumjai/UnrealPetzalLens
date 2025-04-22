# Assignment 03 - Final
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
This project recreates the distinct swirly bokeh effect of the vintage Helios 44-2 lens using a custom post-process material in Unreal Engine. By simulating the optical aberrations and radial blur characteristic of Petzval-style lenses, the shader aims to introduces a dreamy, cinematic depth to out-of-focus areas—especially around the edges of the frame. The effect dynamically responds to camera focus and aperture settings, allowing for real-time artistic control in virtual production and stylized rendering environments.
    <br />
    <a  /> 
    <br />
    <br />
    <a href="https://carhua.myportfolio.com">Carolyn Hua</a>
    &middot;
    <a href="https://sites.google.com/view/viza626/home">VIZA 626</a>
  </p>
</div>

[![WIP_blur][images-fig1]](https://example.com)

Figure 1. Post Process Material showcasing my WIP swirly bokeh effect in Unreal. 

<!-- Abstract -->
## Abstract
Inspired by the optical quirks of vintage lenses, this project explores how real-time shaders can evoke emotional texture through simulated imperfection. The custom Petzval lens shader recreates the swirly bokeh and radial distortion of the Helios 44-2, not as a purely technical exercise, but as a tool for atmospheric storytelling. Built in Unreal Engine’s post-process pipeline, the shader blends circular blur, camera depth cues, and controlled UV distortion to mimic the quirks of analog glass. This work investigates how emulating characteristics of physical lens in a digital space can enhance visual mood, bridging the gap between photorealism and expressive rendering.

<!-- Introduction and Related Works -->
## Introduction and Related Works

[![fresnel_eq][images-fig2]](https://example.com)

Figure 2. Real-world photograph demonstrating conventional bokeh.

The Petzval-style bokeh, most famously produced by the Helios 44-2 lens, is known for its swirling background blur and dreamlike distortion around the edges of the frame—an optical flaw turned artistic signature. In photography and optics, bokeh refers to the visual quality of out-of-focus areas, particularly the way light is shaped and softened by a lens’s optical design. As Vorenkamp explains, this quality depends on elements like spherical aberration, aperture blade geometry, and the lens's internal construction, which collectively determine how background highlights are rendered [2]. Rockwell adds that bokeh is a direct result of how a lens reproduces out-of-focus point sources of light, and that even subtle differences in lens design can dramatically affect the smoothness and emotional tone of the background [1].

[![fresnel_lake][images-fig3]](https://example.com)
Figure 3. The swirly bokeh effect in real life. The background follows a concentric swirl blur while leaving the focal point or subject sharp and unaffected by distortion. 

This project draws from these principles to investigate how analog lens behavior can be emulated for artistic effect in real-time rendering. Built within Unreal Engine’s post-process pipeline, the shader incorporates depth-based masking, radial UV distortion, and circular blur sampling to replicate the characteristic swirl of Petzval-style optics. While cinematic depth of field in Unreal achieves photographic realism, it often lacks the expressive asymmetries and nuanced aberrations that give vintage lenses their signature look. This shader embraces those imperfections, using them not as flaws to be corrected, but as visual tools to evoke atmosphere and memory within virtual production workflows. 


## Methodology

[![incident_angle][images-fig4]](https://example.com)
Figure 4. DOF demonstrated in unreal natively. Image sourced from.[3]

[![shader_graph][images-fig5]](https://example.com)
Figure 5. The demo scene with only native unreal DOF.

The shader was implemented as a custom post-process material in Unreal Engine to recreate the swirling bokeh and radial blur associated with Petzval-style lenses. This work builds upon Unreal Engine’s existing cinematic depth of field pipeline, which models real-world optics using physically-based blur calculations, including Circle of Confusion (CoC) and diaphragm-based rendering [3]. However, the default implementation lacks support for swirl distortion and non-uniform bokeh behavior, which this project addresses through custom UV manipulations and depth masking.

[![inner_fresnel][images-fig6]](https://example.com)
Figure 6. The swirl bokeh effect recreated in shader toy to nail down the math and implementation look first.  

To emulate the Helios 44-2 aesthetic, the shader calculates the radial distance from each pixel to the screen center, using this to rotate UVs around the image. Multiple samples are taken along these rotated offsets and averaged to create a blur that increases with distance from the focal plane. A depth-based mask—constructed by comparing the camera’s focus distance with the scene’s depth—isolates the effect to out-of-focus regions. Parameters like swirl intensity, aperture size, and sample count are exposed for real-time tuning.

[![outer_fresnel][images-fig7]](https://example.com)
Figure 7. Outer fresnel node graph. 

As part of the development process, educational resources such as Unreal Engine’s official documentation [3] and YouTube tutorials [4] were used iteratively to test and refine implementation strategies. These materials helped clarify how Unreal internally handles cinematic depth of field, informing how custom logic could be layered on top of the engine’s rendering architecture. The final shader combines these techniques to deliver a stylized, camera-aware blur effect that mimics the analog flaws of Petzval-style lenses. 

[![test_manny][images-fig8]](https://example.com)
Figure 8. Another iterative shader graph process in the hopes of recreating the math and swirl effect. 

## Result and Future Work

[![ghostly_ref][images-fig9]](https://example.com)
Figure 9. The swirl effect in the current WIP state.  

While the current implementation successfully applies a swirl and blur effect based on depth and radial distance, the result does not yet fully capture the smooth, concentric bokeh and nuanced lens falloff characteristic of the Helios 44-2. The blur edges are still too intense, and the swirl lacks the subtle gradient seen in real Petzval-style optics. Additionally, I still need to implement the depth mask to better isolate the in-focus subject from the background. 

Future work will focus on improving the quality of the radial blur by experimenting with smoother sampling strategies, incorporating more realistic falloff curves, and possibly implementing chromatic aberration or vignetting for added authenticity. There is also potential to optimize performance by reducing shader cost while maintaining visual fidelity. Ultimately, the goal is to achieve a real-time, expressive bokeh effect that is both technically sound and emotionally evocative—bringing the imperfections of analog glass into digital cinematic spaces.

## Conclusion

[![cel_shading][images-fig10]](https://example.com)
Figure 10. Cel Shading 

This project represents an ongoing exploration into the expressive potential of real-time lens simulation. By attempting to recreate the signature swirl and optical imperfections of a Petzval-style lens in Unreal Engine, the shader aims to bridge the gap between technical rendering and emotional storytelling. Although the results are still in development, the process has revealed both the challenges and creative opportunities in translating analog lens behaviors into digital form. As the shader continues to evolve, it holds promise not only as a visual effect but as a storytelling tool—one that reintroduces warmth, texture, and imperfection into the precision of virtual production.

<!-- Bibliography -->
## Bibliography 
[1] K. Rockwell, "Bokeh," KenRockwell.com, 2008. [Online]. Available: https://www.kenrockwell.com/tech/bokeh.html

[2] T. Vorenkamp, "Understanding Bokeh," B&H eXplora, Jul. 28, 2021. [Online]. Available: https://www.bhphotovideo.com/explora/photography/tips-and-solutions/understanding-bokeh

[3] Epic Games, "Cinematic Depth of Field in Unreal Engine," Unreal Engine Documentation, 2025. [Online]. Available: https://dev.epicgames.com/documentation/en-us/unreal-engine/cinematic-depth-of-field-in-unreal-engine

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
[images-fig1]: Assignment03_pics/Iteration002.png
[images-fig2]: Assignment03_pics/fresnel_eq.png
[images-fig3]: Assignment03_pics/lake_ex.jpg
[images-fig4]: Assignment03_pics/incidentAngle.png
[images-fig5]: Assignment03_pics/shader_graph_full.png
[images-fig6]: Assignment03_pics/Fresnel_inner.png
[images-fig7]: Assignment03_pics/Fresnel_outer.png
[images-fig8]: Assignment03_pics/test_manny.png
[images-fig9]: Assignment03_pics/ghostly_ref.png
[images-fig10]: Assignment03_pics/Toon-shader.jpg
[images-fig11]: Assignment03_pics/fresnel_comp.jpg
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
