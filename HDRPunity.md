HDRP
============
2018-11-20 정리
---------------

- unity 2018 이후 사용자가 직접 rendering pipeline을 수정할 수 있도록 나옴
- HDRP 예제를 에셋스토어에서 다운받아서 뜯어보기 - Unity HDRI Pack
- unity hub에서 HDRP 설정을 따로 해줄 수 있다. (Beta)


**HDRP의 세 가지 원칙**<br>

    1. 물리 기반 렌더링
    2. 통합되고 일관된 조명
    3. 렌더링 패스의 독립적인 기능


**환경세팅**<br>
UnityHub를 통해 설정하는법<br>
 1.  New button을 클릭합니다.
 2.  Tamplet drop-down칸에서 High Definition을 선택해줍니다.
 3.  프로젝트를 생성합니다.

**https://blogs.unity3d.com/kr/2018/09/24/the-high-definition-render-pipeline-getting-started-guide-for-artists/**

![](https://blogs.unity3d.com/wp-content/uploads/2018/09/Unity_Hub_GIF.gif)<br>

18.3 버전 이후 settings창에 따로 존재<br>
Rendering -> HDRP settings<br>
lightbox -> HDRP<br>


**Scene setting**<br>
Hierarchy -> inspector -> profile<br>
Scene settings profile에서 필요한 설정을 해준다.<br>

**visual Environment**<br>
sky, fog등 설정 HDR 소스를 선택해서 적용<br>
 1. Sky Type : sky를 렌더링할 때 사용됩니다. 유저가 커스텀한 sky를 자동적으로 업데이트해줍니다.
 2. Fog Type : fog를 렌더링할 때 사용됩니다.

**Light**<br>
Light 값들의 종류 <br>
 1. PLU : 실제 측정 가능한 값을 기반으로 한 단위<br>
 2. LUD(lx) : 빛의 조명도를 나타내는 단위<br>
 3. Lumen(lm) : 가시광선의 총량을 나타내는 광선속의 단위<br>
 4. Candela(cd) : 광도의 단위<br>
 5. Luminance(lv) : 어떤 광원의 단위 면적단의 광도<br>

Light 옵션의 종류<br>
 1. Default
 2. Deffuse
 3. Spectacle
그림자에 대한 설정도 가능<br>

Spot light shape : cone, pyramid, box. max smoothness를 통해 빛이 닿았을 때의 크기를 조정가능<br>
Line lighting : 선적으로 light를 표현가능, 그림자는 아직 구현되어있지 않음<br>

**HDRP meterial**<br>
HDRP에서 제공하는 property : surface options, double sided등<br>
기본적으로 HDRP에서 사용하고 추가로 필요하면 unity standard shader를 이용해서 구현<br>

Meterial type은 총 6가지를 제공 -> 어떤 메터리얼을 표현하고 싶느냐에 따라 설정<br>

 1. 표면하산란(SSS) : 피부와 같은 반투명 매질의 경우 산란된 빛이 다시 반사되어 나타남<br>
profile을 설정해서 투과되는 빛이 어떻게 표현되느냐를 정해줄 수 있다.<br>
 2. 비등방성, 이방성(Anisotropy) : 방향에 따라서 물리적 성질이 다른것, 반사되는 방향 수정<br>
 3. IrideScene : 무지개 빛 -> 실시간으로 물이 증발하면서 가시광선이 난반사를 일으켜 무지개 빛이 나타남 ex) 기름<br>
 4. Specualr color : 헤드라이트와 같은 재질에 빛이 향하고 있을때 재질의 색 결정?<br>
 5. Decal : object에 decal을 사용하는가<br>
 6. Displacement mode : Vertex, pixel 두가지를 제공. Height map을 기반으로 진폭, minmax 항목으로 버텍스의 위치를 조정<br>
 7. Lit tessellation : 실제 triangle을 늘려서 Rendering하는 기술, 실제로 높이를 가지는 triangle에 생성된다<br>
 8. Vertex Animation : Enable wind - 바람에 흩날리는 효과를 위한 항목.<br>
 9. Clear coat : 재질의 겉 표면에 코팅한 느낌을 표현한다.<br>
 10. Detail import : Detail Texture 적용을 위하여 사용되는 항목 ex) 얼룩등 표시<br>
 11. Emission : 발광하는 물체 표명을 표현시에 사용한다. static mesh를 켜주면 Light처럼 사용이 가능하다.<br>
 12. Transperency : 굴절효과를 표현한다.<br>
 13. SS(Scene Space) : proxy, hiz, lor값을 조정해 상이 맺히는 모습을 바꿔줌.
 14. Render pipeline window : debug mode가 다양하게 존재한다.
