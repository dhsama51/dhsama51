<div align="center">

<img src="https://capsule-render.vercel.app/api?type=waving&color=b4c5f9&height=180&text=%EC%9D%B4%EB%8F%99%ED%9B%88%20(Lee%20DongHoon)&animation=&fontColor=000000&fontSize=50" />

### Lee DongHoon
<em>Multimodal Security · LLM Security · Network & Protocol Security</em>

<br/>

<em>"Without haste, but without rest."</em>

</div>

---

## 🏛 Education & Organization

<table width="100%">
<thead>
<tr>
<th align="left" width="18%">Period</th>
<th align="left" width="30%">Education / Organization</th>
<th align="left" width="52%">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td nowrap="nowrap">21.03 ~</td>
<td><b>정보보안암호수학과</b></td>
<td>Undergraduate Student at Kookmin University</td>
</tr>
<tr>
<td nowrap="nowrap">22.05 ~</td>
<td><b>소프트웨어학부</b></td>
<td>Double Major at Kookmin University</td>
</tr>

<tr><td colspan="3"><br/></td></tr>

<tr>
<td nowrap="nowrap">26.08 ~</td>
<td><a href="https://github.com/dhsama51/ISS-Lab"><b>ISS Lab</b></a></td>
<td>Undergraduate Intern, Korea University — Network Security & AI Security</td>
</tr>
<tr>
<td nowrap="nowrap">26.01 ~ 26.04</td>
<td><a href="https://github.com/dhsama51/CSE"><b>CSE</b></a></td>
<td>Undergraduate Intern — Cryptographic implementation and CKKS performance analysis</td>
</tr>
<tr>
<td nowrap="nowrap">25.07 ~ 25.11</td>
<td><a href="https://github.com/dhsama51/MobiSec"><b>MobiSec</b></a></td>
<td>Undergraduate Intern / Researcher — TLS analysis and 5G security</td>
</tr>
<tr>
<td nowrap="nowrap">24.12 ~ 25.05</td>
<td><b>FaS</b></td>
<td>Digital forensics academic club in the Department of Information Security, Cryptology and Mathematics</td>
</tr>
</tbody>
</table>

---

## 🛡️ About Me

<div align="center">

I am an undergraduate student at **Kookmin University**, majoring in **Information Security, Cryptomathematics and Mathematics** and double majoring in **Software**.
I am interested in **how LLMs and vision-language models represent information, align different modalities, and reason** — and in using that understanding to build models that are **more efficient and more reliable** in real systems.

My research habit comes from **empirical, protocol-level security research** — reproducing published attacks and validating whether their assumptions hold in real implementations (TLS, 5G NAS). I now apply the same discipline to AI systems: in two independent projects on **multimodal retrieval** and **LLM-based RAG**, I reproduced recent papers from top venues, tested whether their assumptions hold beyond the reported setting, and traced unexpected results back to representation, modality alignment, and model-judgment behavior.

</div>

---

## 🔬 Research Interests

<table width="100%">
<thead>
<tr>
<th align="left" width="30%">Area</th>
<th align="left" width="70%">Keywords</th>
</tr>
</thead>
<tbody>
<tr>
<td><b>Multimodal Learning & VLMs</b></td>
<td>Representation Learning, Multimodal Alignment, Image–Text Retrieval, Vision-Language Models</td>
</tr>
<tr>
<td><b>Efficient & Reliable LLMs</b></td>
<td>Efficient Adaptation / Inference, Reasoning, Hallucination & Reliability, Retrieval-Augmented Generation</td>
</tr>
<tr>
<td><b>AI Security & Robustness</b></td>
<td>Adversarial Robustness of Multimodal Retrieval, Cross-Model Transferability, RAG Poisoning, Responsibility Attribution</td>
</tr>
<tr>
<td><b>Network & Protocol Security</b></td>
<td>TLS, DNS, 5G NAS, Implementation Analysis, Reproducible Attack Validation</td>
</tr>
</tbody>
</table>

---

## 🧭 Research Interest

My long-term interest is in **how LLMs, VLMs, and multimodal models represent information, align modalities, and reason** — and in using that understanding to propose models and methods that improve both performance and training/inference efficiency, while remaining reliable in real systems.

My current work approaches this question from the reliability side, through two independent reproduction-and-extension projects.

The first is on **adversarial hubness in multimodal retrieval** — why a single adversarial image can dominate nearest-neighbor search across unrelated queries (*hubness*), why that dominance largely collapses when the image is moved to another encoder, and why a detector's success depends on whether its queries come from the text or the image modality.

The second is on **responsibility attribution in LLM-based RAG (Retrieval-Augmented Generation) systems** — how an attribution algorithm narrows down which retrieved passage caused a misgeneration, how its termination condition can be forced to stop before a deeply hidden poison is reached, and how the choice of judgment LLM changes the algorithm's efficiency without changing its accuracy.

Across both directions I apply the same empirical approach — reproduce the original claims, stress-test them at their boundary conditions, and isolate root causes when results diverge — building on a foundation of protocol-level security research (TLS certificate validation, 5G NAS).

---

## 🌐 Featured Research

<table width="100%">
<thead>
<tr>
<th align="left" width="16%">Period</th>
<th align="left" width="84%">Project</th>
</tr>
</thead>
<tbody>
<tr>
<td nowrap="nowrap">26.09</td>
<td>
<a href="https://github.com/dhsama51/adversarial-hubness-reproduction"><b>Adversarial Hubness in Multi-Modal Retrieval — Reproduction & Extension</b></a><br/>
[Python, CLIP, OpenCLIP, ImageBind, FAISS] Reproduced the adversarial hub attack from Zhang et al. (IEEE S&P'26) on a CLIP-based image-text retrieval pipeline (MS-COCO, held-out ASR@1 ≈ 68% vs. ~85% reported, on a single 8 GB GPU) and reimplemented the detector from its follow-up paper (Habler et al., 2026), comparing it against the official implementation.
<ul>
<li>Formulated and tested an original hypothesis — that transfer attack success rate correlates with representational similarity (RSA/Alignment) across 8 image–text encoders — and found <b>no statistically significant relationship</b> in the current sample (n = 7 targets, RSA r = 0.43, p = 0.33); hubs reaching 99.8% ASR@1 in their own embedding space kept only 3–7% on other encoders</li>
<li>Diagnosed why the official detector is near chance under its <code>mixed</code> query-sampling mode (ROC-AUC 0.36–0.57) yet succeeds with real caption queries (0.94–0.98) on identical inputs — the query source, not the algorithm, explains the gap — and, by reading its source code, traced the failure to a likely (not yet isolated) image–text modality mismatch</li>
<li>Found that word hubs match or outperform cluster hubs on general queries, reversing the original paper's ranking, and tested candidate causes through targeted ablations: evaluation scale was rejected, while surrogate model and cluster-size restriction were rejected only in combination, leaving the cause unexplained</li>
<li>Practiced explicit self-review of scope: distinguished experiments that reproduce the paper's core claim (weight-sharing surrogates) from an independent extension the paper did not test</li>
</ul>
</td>
</tr>
<tr>
<td nowrap="nowrap">26.09</td>
<td>
<a href="https://github.com/dhsama51/ragorigin-reproduction"><b>RAGOrigin Edge Case Reproduction — Reproduction & Extension</b></a><br/>
[Python, Qwen2.5-1.5B-Instruct, Llama-3.2-1B-Instruct, FAISS] Replicated, on a low-cost GPU with lightweight models, the attribution-scope-narrowing algorithm and Responsibility-Score threshold from <i>"Who Taught the Lie? Responsibility Attribution for Poisoned Knowledge in RAG"</i> (RAGOrigin, IEEE S&P'26), cross-checking against the authors' official implementation and correcting three discrepancies found in the process.
<ul>
<li>Found that forcing early termination causes a deeply-hidden poisoned text (22 segments in) to go <b>entirely undetected in 5/5 cases</b>, since it never enters the final attribution scope</li>
<li>Constructed an adaptive termination-forcing attack under the paper's strong-attacker assumption that <b>evaded detection in 20/20 cases</b> (5 questions × 4 payload depths, ranks 200–2000), regardless of how deep the real payload was hidden</li>
<li>Showed a second weakness of the same termination condition (stop once Match and No-match segment counts are equal): when no poison sits in the top-K — as could happen when re-running attribution after the top-K poisons are removed — a single poison at rank 2K+1 <b>kept scope narrowing from terminating</b> (5/5 hit the 30-iteration cap), so it was still included only after scanning 150 texts</li>
<li>Swapped the judgment LLM between self-judging (Qwen2.5-1.5B, also the generation and proxy LLM) and a separate judge (Llama-3.2-1B) and showed that final detection accuracy stayed identical (DACC = 1.00) while the average number of iterations rose from 2.40 to 4.00 — isolating an efficiency effect of judgment strictness from a detection-accuracy effect</li>
</ul>
</td>
</tr>
</tbody>
</table>

---

## 📄 Recent Security Paper Analysis

<table width="100%">
<thead>
<tr>
<th align="left" width="12%">Date</th>
<th align="left" width="26%">Paper</th>
<th align="left" width="52%">Focus</th>
<th align="left" width="10%">Link</th>
</tr>
</thead>
<tbody>
<tr>
<td nowrap="nowrap">26.10</td>
<td><b>Who Taught the Lie? Responsibility Attribution for Poisoned Knowledge in RAG</b> (IEEE S&P'26)</td>
<td>RAGOrigin: black-box tracing of poisoned texts behind a RAG misgeneration from only the reported (question, wrong answer) — adaptive attribution scope plus a combined retrieval/generation responsibility score; identified edge cases in its scope-termination rule (Eq. 4) that motivated a follow-up reproduction</td>
<td><a href="https://github.com/dhsama51/Security-Paper-Review/blob/main/analysis_Who_Taught_the_Lie.pdf">Link</a></td>
</tr>
<tr>
<td nowrap="nowrap">26.09</td>
<td><b>Opossum Attack</b> (USENIX Sec'26)</td>
<td>Application-layer desynchronization from the coexistence of implicit and opportunistic TLS; analyzed four resulting exploit classes and an IPv4-wide exposure scan</td>
<td><a href="https://github.com/dhsama51/ISS-Lab/blob/main/Security%20Paper%20Review/analysis_opossum_attack_2026.pdf">Link</a></td>
</tr>
<tr>
<td nowrap="nowrap">26.09</td>
<td><b>Adversarial Hubness in Multi-Modal Retrieval</b> (IEEE S&P'26)</td>
<td>Analyzed how an intentionally-crafted "adversarial hub" can dominate nearest-neighbor retrieval for thousands of unrelated queries at once — the paper that motivated the reproduction study above</td>
<td><a href="https://github.com/dhsama51/ISS-Lab/blob/main/Security%20Paper%20Review/analysis_adversarial_hubness_2026.pdf">Link</a></td>
</tr>
<tr>
<td nowrap="nowrap">26.08</td>
<td><b>DNS Cache Poisoning Like it's 2006</b> (USENIX Sec'26)</td>
<td>Recovering BIND 9's Xoshiro128** PRNG state from observable TXID/RRset-order leakage to defeat both TXID and UDP-port randomization</td>
<td><a href="https://github.com/dhsama51/ISS-Lab/blob/main/Security%20Paper%20Review/analysis_dns_cache_poisoning_2026.pdf">Link</a></td>
</tr>
</tbody>
</table>

Ongoing habit of reading and presenting recent IEEE S&P / USENIX Security papers to sharpen the same empirical-vulnerability mindset before applying it to AI systems. Full slide deck for each paper: <a href="https://github.com/dhsama51/ISS-Lab">ISS-Lab</a>

---

## 🤖 Selected Projects

<table width="100%">
<thead>
<tr>
<th align="left" width="16%">Period</th>
<th align="left" width="27%">Project / Activity</th>
<th align="left" width="20%">Affiliation</th>
<th align="left" width="37%">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td nowrap="nowrap">26.03 ~ 26.06</td>
<td><a href="https://github.com/dhsama51/Software/tree/main/26-1%20Multimodal%20AI"><b>Multimodal AI & Vision-Language Model Study</b></a></td>
<td>멀티모달인공지능</td>
<td>[Python, PyTorch] Implemented image-text retrieval with triplet loss, trained an image-captioning model, and ran CLIP zero-shot classification experiments across prompt templates.</td>
</tr>
<tr>
<td nowrap="nowrap">26.01 ~ 26.05</td>
<td><a href="https://github.com/dhsama51/26-1_Capstone_Reinforcement_Learning_Agent_in_Handmade_Card_Game"><b>Call of the King</b></a></td>
<td>Capstone Design</td>
<td>[Python, PyTorch] Designed a custom PvP card game and developed a PPO-based RL agent for automated balancing; when training plateaued, redesigned the state representation with a Transformer to better capture card–board relationships. Not directly related to current interests, but reflects the define-a-problem → design-a-model → improve-through-experiments cycle central to my research approach.</td>
</tr>
<tr>
<td nowrap="nowrap">25.11</td>
<td><a href="https://github.com/dhsama51/Software/tree/main/25-2%20Information%20and%20System%20Security"><b>Encrypted Traffic Analysis</b></a></td>
<td>정보보호와시스템보안 프로젝트</td>
<td>[Python] Analyzed encrypted traffic for website fingerprinting using a Random Forest–XGBoost soft-voting ensemble — an early exposure to combining ML with security analysis.</td>
</tr>
<tr>
<td nowrap="nowrap">25.07 ~ 25.11</td>
<td><a href="https://github.com/dhsama51/MobiSec/blob/main/Validation%20of%20Traceability%20Attacks%20in%20NAS%20Registration%20Procedure.pdf"><b>5G NAS Traceability Attack Validation</b></a></td>
<td>MobiSec Undergraduate Intern</td>
<td>[5G, Open-Source Testbed] Reproduced a published traceability attack and experimentally examined whether its assumptions held in the tested environment. Published as a poster paper at MobiSec'25.</td>
</tr>
<tr>
<td nowrap="nowrap">25.07 ~ 25.08</td>
<td><a href="https://github.com/dhsama51/Information_Security_Cryptography_and_Mathematics/blob/main/25-2%20Kookmin%20Crypto%20Festival/%EC%9D%B4%EB%8F%99%ED%9B%88%20%ED%8F%AC%EC%8A%A4%ED%84%B0%20OpenSSL%20CVE-2015-1793%20TLS%20%EC%9D%B8%EC%A6%9D%EC%84%9C%20%EA%B2%80%EC%A6%9D%20%EC%9A%B0%ED%9A%8C%20%EA%B3%B5%EA%B2%A9%20%EC%9E%AC%ED%98%84.pdf"><b>OpenSSL CVE-2015-1793 Reproduction</b></a></td>
<td>MobiSec Undergraduate Intern</td>
<td>[OpenSSL, TLS/PKI] Analyzed and reproduced a certificate-chain validation bypass and compared vulnerable and corrected validation behavior. Awarded Excellence Prize at Kookmin Crypto Festival 2025.</td>
</tr>
<tr>
<td nowrap="nowrap">24.10 ~ 24.12</td>
<td><a href="https://github.com/dhsama51/Information_Security_Cryptography_and_Mathematics/tree/main/24-2%20Security%20Protocol"><b>miniTLS & Padding Oracle Attack</b></a></td>
<td>Security Protocols</td>
<td>[Python] Implemented a simplified TLS-like protocol and reproduced a padding oracle attack caused by distinguishable server responses.</td>
</tr>
</tbody>
</table>

---

## 🧩 Security & Systems Background

<table width="100%">
<thead>
<tr>
<th align="left" width="16%">Period</th>
<th align="left" width="27%">Project / Activity</th>
<th align="left" width="20%">Affiliation</th>
<th align="left" width="37%">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td nowrap="nowrap">26.03 ~ 26.04</td>
<td><b>CKKS Performance Analysis</b></td>
<td>CSE Undergraduate Intern</td>
<td>[C, C++] Analyzed CKKS operation performance using SEAL and SEAL-Embedded.</td>
</tr>
<tr>
<td nowrap="nowrap">26.01 ~ 26.02</td>
<td><a href="https://github.com/dhsama51/CSE"><b>Cryptographic Arithmetic Implementation</b></a></td>
<td>CSE Undergraduate Intern</td>
<td>[C] Implemented LEA-128/192/256, 256-bit P-256 field arithmetic, elliptic-curve point operations, and multiple scalar-multiplication algorithms.</td>
</tr>
<tr>
<td nowrap="nowrap">22.09 ~ 24.03</td>
<td><b>육군 정보보호병</b></td>
<td>Republic of Korea Army</td>
<td>Managed Linux server security and infrastructure operations.</td>
</tr>
<tr>
<td nowrap="nowrap">21.04 ~ 21.09</td>
<td><b>Cryptographic Implementation Study</b></td>
<td>Academic Club</td>
<td>[C] Implemented AES-128 and studied differential cryptanalysis on a toy cipher.</td>
</tr>
</tbody>
</table>

---

## 📜 Certifications

<table width="100%">
<thead>
<tr>
<th align="left" width="18%">Date</th>
<th align="left" width="55%">Certification</th>
<th align="left" width="27%">Note</th>
</tr>
</thead>
<tbody>
<tr>
<td nowrap="nowrap">26.08.28</td>
<td nowrap="nowrap"><b>정보보안기사</b></td>
<td>-</td>
</tr>
<tr>
<td nowrap="nowrap">26.09.11</td>
<td nowrap="nowrap"><b>정보처리기사</b></td>
<td>-</td>
</tr>
<tr>
<td nowrap="nowrap">23.12.01</td>
<td nowrap="nowrap"><b>리눅스마스터 1급</b></td>
<td>-</td>
</tr>
<tr>
<td nowrap="nowrap">22.06.24</td>
<td nowrap="nowrap"><b>SQL 개발자(SQLD)</b></td>
<td>-</td>
</tr>
</tbody>
</table>

---

## 🏆 Awards

<table width="100%">
<thead>
<tr>
<th align="left" width="15%">Year</th>
<th align="left" width="35%">Award</th>
<th align="left" width="50%">Description</th>
</tr>
</thead>
<tbody>
<tr>
<td nowrap="nowrap">2025</td>
<td nowrap="nowrap"><b>국민암호페스티벌 우수상</b></td>
<td>TLS CVE-2015-1793 certificate chain validation bypass reproduction</td>
</tr>
</tbody>
</table>

---

## 📝 Publications & Posters

<table width="100%">
<thead>
<tr>
<th align="left" width="12%">Year</th>
<th align="left" width="18%">Venue</th>
<th align="left" width="18%">Type</th>
<th align="left" width="42%">Title / Topic</th>
<th align="left" width="10%">Link</th>
</tr>
</thead>
<tbody>
<tr>
<td nowrap="nowrap">2025</td>
<td><b>MobiSec</b></td>
<td>Poster Paper</td>
<td>Validation of Traceability Attacks in NAS Registration Procedure</td>
<td><a href="https://github.com/dhsama51/MobiSec/blob/main/Validation%20of%20Traceability%20Attacks%20in%20NAS%20Registration%20Procedure.pdf">Link</a></td>
</tr>
<tr>
<td nowrap="nowrap">2025</td>
<td><b>국민암호페스티벌</b></td>
<td>Poster</td>
<td>OpenSSL CVE-2015-1793: TLS 인증서 검증 우회 공격 재현</td>
<td><a href="https://github.com/dhsama51/Information_Security_Cryptography_and_Mathematics/blob/main/25-2%20Kookmin%20Crypto%20Festival/%EC%9D%B4%EB%8F%99%ED%9B%88%20%ED%8F%AC%EC%8A%A4%ED%84%B0%20OpenSSL%20CVE-2015-1793%20TLS%20%EC%9D%B8%EC%A6%9D%EC%84%9C%20%EA%B2%80%EC%A6%9D%20%EC%9A%B0%ED%9A%8C%20%EA%B3%B5%EA%B2%A9%20%EC%9E%AC%ED%98%84.pdf">Link</a></td>
</tr>
</tbody>
</table>

---

## 💻 Stacks & Tools

<div align="center">

<img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
<img src="https://img.shields.io/badge/PyTorch-EE4C2C?style=for-the-badge&logo=pytorch&logoColor=white"/>
<br/>
<img src="https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=C&logoColor=black"/>
<img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white"/>
<img src="https://img.shields.io/badge/Linux-FCC624?style=for-the-badge&logo=linux&logoColor=black"/>
<img src="https://img.shields.io/badge/MySQL-4479A1?style=for-the-badge&logo=mysql&logoColor=white"/>

</div>

---

## 🌎 Language

<table width="100%">
<thead>
<tr>
<th align="left" width="25%">Date</th>
<th align="left" width="35%">Test</th>
<th align="left" width="40%">Score</th>
</tr>
</thead>
<tbody>
<tr>
<td nowrap="nowrap">25.11.18</td>
<td><b>TOEIC</b></td>
<td>830</td>
</tr>
<tr>
<td nowrap="nowrap">26.09.30</td>
<td><b>TEPS</b></td>
<td>360</td>
</tr>
</tbody>
</table>
