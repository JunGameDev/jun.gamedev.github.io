---
title: 'DirectX 11의 렌더링 파이프라인'
date: 2021-05-18 01:58:00
category: 'DirectX'
draft: false
---

> ⚠️ 아래의 내용은 공부하면서 계속 추가될 예정이다.


[![DirectX Rendering Pipeline](https://www.3dgep.com/wp-content/uploads/2014/03/DirectX-11-Rendering-Pipeline.png)]

# 1. Input-Assembler Stage
- 정점 정보를 전달하는 단계.
- 정점들이 어떻게 연결되어 있는지 전달한다.

# 2. Vertex Shader Stage
- 1 단계에서 넘겨준 정점들을 대상으로 하는 연산 처리를 실행.

# 3. Hull Shader, Tessellator, Domain Shader Stage
- 이 세개를 합쳐서 그냥 Tessellator 단계라고도 부른다.
- DX11에서 추가된 개념.
- 이 단계에서 LOD 같은 개념들이 활용될 수 있음.
- 4번쨰 단계와 함께 정점을 추가하는 개념. 단 이 단계는 좀 더 거시적.

# 4. Geometry Shader Stage
- 좀 더 작은 단위로 정점을 추가하는 단계

# 5. Rasterizer Stage
- 정점들 사이에 있는 픽셀들에 대한 보간 작업이 이루어지는 단계.

# 6. Pixel Shader Stage
- 최종적으로 색상을 입히는 단계.
- 색상 변경이 이 단계에서 이루어짐.

# 7. Output-Merger Stage
- 모든 데이터들을 결합해서 최종 색상을 결정함.

# 📚 <b> 레퍼런스 </b>
Introduction to DirectX 11 : https://www.3dgep.com/introduction-to-directx-11/#DXGI

