---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======
* Ph.D. in Computational Mathematics, The Chinese University of Hong Kong, Shenzhen, 2023 – 2027 (expected)
* B.Sc. in Mathematics and Applied Mathematics, Nanjing Normal University, 2019 – 2023

Research Interests
======
* Scientific computing, numerical simulation
* Finite element methods, high-order discretizations
* Preconditioning, fast iterative solvers
* Stokes equations, fluid-structure interaction

Research Contributions
======
* Designed high-order discretization schemes for fluid-structure interaction problems
* Developed a fast solver for fluid-rigid body interaction problems
* Analyzed the inf-sup condition and convergence of iterative solvers for the Stokes equation in tight domains
* Proposed robust preconditioners for the Stokes equation in tight domains

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

Skills
======
* Programming: Python, MATLAB, LaTeX
* Scientific computing: FEniCS / FEniCSx, Gmsh, pctools, pfibs
* Methods: finite element discretizations, high-order and ALE schemes, operator preconditioning, iterative and block solvers

Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

<!-- Internship 暂时隐藏（学术主页里先不展示）；想恢复就删掉本段首尾的注释符号
Internship
======
* Jul – Aug 2024: Research Intern, Shenzhen Raymind Biotechnology Co., Ltd.
  * Assisted in numerical simulation and model development
  * Implemented and validated the isoparametric finite element method
  * Developed high-order temporal discretization schemes for fluid-structure interaction problems
-->

Awards and Achievements
======
* 2024: Outstanding Student Chair, National Outstanding Graduate Students Workshop, CUHK-Shenzhen
* 2020 – 2021: First Prize, 12th & 13th National College Mathematics Competition (Jiangsu Province)
