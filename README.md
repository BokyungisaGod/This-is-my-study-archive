📜: Paper link
🧑🏻‍💻: Developer blog & Github link & HuggingFace
🗞️: News
🤪: Interesting

---

# My study archive 2024

## 🎄 December
<details>
  <summary>1st week</summary>

- 📜 [Harvard, Stanford, MIT, Databricks, CMU] [Scaling Laws for Precision](https://arxiv.org/pdf/2411.04330)
  - 낮은 정밀도(Low precision)로 학습과 추론을 수행할 때의 영향을 연구했으며, 이를 예측하는 새로운 스케일링 법칙 제시
    - 학습 시: 낮은 정밀도는 모델의 유효 파라미터 수를 감소시키는 효과가 있음을 발견
    - 추론 시: 데이터가 많아질수록 양자화로 인한 성능 저하가 커져서, 오히려 추가 사전학습이 해로울 수 있음
  - 특히 대규모 모델의 경우 저정밀도 훈련이 계산 효율성 측면에서 최적일 수 있다는 점 제시
  - 1.7B 파라미터 규모의 모델과 26B 토큰 데이터셋으로 검증하여, 학습과 추론 시의 정밀도 변화에 따른 성능 저하를 예측하는 통합된 수식 제시
    <details>
      <summary>중요 개념</summary>
      
    - precision(정밀도): 숫자를 얼마나 정확하게 표현하는지의 정도
    - scaling laws(스케일링 법칙): 모델의 크기와 성능 관계를 설명하는 규칙
    - quantization(양자화): 데이터를 더 작은 비트로 압축하는 과정
    </details>
  
- 🧑🏻‍💻 https://chanmuzi.tistory.com/479
  - NLP, LLM 위주의 인공지능 최신 논문/뉴스 follow-up 팁

- 📜 [RAPID RESPONSE: MITIGATING LLM JAILBREAKS WITH A FEW EXAMPLES](https://arxiv.org/abs/2411.07494)
  - LLM의 안전성 확보를 위해, 완벽한 방어가 아닌 신속 대응 기법에 초점을 맞춤
  - 소수의 공격 사례만으로도 유사한 형태의 전체 공격 유형을 차단하는 방법 제시
  → 이를 평가하기 위한 'RapidResponseBench' 벤치마크 개발
    <details>
      <summary>'<b>탈옥 확산(jailbreak proliferation)</b>' 기반의 5가지 방어 기법 평가</summary>
      
    - 관찰된 공격 사례를 바탕으로 자동으로 유사한 jailbreak를 생성하여 방어에 활용
    - 가장 효과적인 방법: 생성된 jailbreak를 차단하도록 입력 분류기를 미세조정
    - 단 하나의 공격 사례만으로도 동일 유형 공격은 1/240, 새로운 유형 공격은 1/15로 성공률 감소
    </details>
  
  - 추가 연구를 통해 방어 효과에 영향을 미치는 핵심 요소 파악
    <details>
      <summary>중요 역할</summary>
  
    - 확산 모델의 품질:  생성된 탈옥 사례의 다양성과 적합성
    - 생성된 탈옥 사례 수: 더 많은 사례가 더 강력한 방어로 이어짐
    </details>
    
- 🗞️ [Introducing Motif: A High-Performance Open-Source Korean LLM by Moreh](https://moreh.io/blog/introducing-motif-a-high-performance-open-source-korean-llm-by-moreh-241202)
  - Moreh에서 한국어 성능이 뛰어난 초거대 언어 모델(LLM) 'Llama3-Motif-102B'을 오픈소스로 공개
    - 한국어 성능 강화를 위해 LlamaPro와 Masked Structure Growth(MSG) 등 최신 학습 기법을 활용해 개발
  - KMMLU 벤치마크에서 GPT-4를 능가하는 성적을 기록하였으며, Hugging Face와 GitHub에서 접근 가능
  - Llama 3 기반으로 MoAI 플랫폼을 활용하여 개발되었으며, 효율적 GPU 관리 및 모델 최적화 가능
  - 향상된 한국어 처리 능력과 영어 성능을 동시에 제공
  - [테스트 해보기](https://model-hub.moreh.io/text)

- 📜 [IST, ETH] [GPTQ: ACCURATE POST-TRAINING QUANTIZATION FOR GENERATIVE PRE-TRAINED TRANSFORMERS](https://arxiv.org/abs/2210.17323)
  - 기존 GPT 모델의 한계 : 모델 크기가 방대하여 추론에 많은 GPU가 필요해 실용성이 떨어짐
  - GPTQ: GPT모델의 높은 컴퓨팅 및 저장 비용 문제를 해결하기 위한 새로운 양자화 방법
    <details>
        <summary>주요 특징</summary>
      
      - 원샷 가중치 양자화: 한 번의 과정을 통해 모델의 가중치를 효율적으로 압축
      - 1750억 개 파라미터를 가진 GPT 모델을 약 4시간 만에 양자화 가능
      - 가중치당 비트 폭을 3~4비트로 줄여도 성능 저하가 거의 없음
      - 기존 양자화 기법 대비 2배 이상 효율적
    </details>
    <details>
        <summary>주요 성과 및 추론 속도 향상</summary>
      
      - 1750억 개 파라미터 모델도 단일 GPU로 처리 가능
      - FP16 대비 추론 속도
        - 고급 GPU(NVIDIA A100): 3.25배,
        - 비용 효율적인 GPU(NVIDIA A6000): 4.5배 빨라짐
      - 극한 양자화에서도 정확도 유지
        - 가중치를 2비트 또는 3진수로 줄여도 합리적인 성능 유지 
    </details>
  - [Github](https://github.com/IST-DASLab/gptq)

- 🗞️ [Google DeepMind] [Genie 2: A large-scale foundation world model](https://deepmind.google/discover/blog/genie-2-a-large-scale-foundation-world-model/)
  - Genie 2: 이미지 하나만으로 다양한 3D 환경을 생성하는 기반 세계 모델
    - 사람 또는 AI 에이전트가 키보드와 마우스로 조작하며 상호 작용할 수 있는 무한한 가상 환경을 제공
    - 물리 효과, 캐릭터 애니메이션, 객체 상호 작용 등을 모델링하여 현실적인 가상 세계를 생성하며, 실제 이미지를 기반으로 한 환경 생성도 가능
    - AI 에이전트 훈련 및 평가에 유용한 다양한 환경을 빠르게 제작하는 데 활용

- 📜 [KU, KAIST] [CheckEval: Robust Evaluation Framework using Large Language Model via Checklist](https://arxiv.org/abs/2403.18771)
  - CheckEval: LLM을 활용한 새로운 평가 프레임워크로, 기존 평가 방법의 문제점(모호한 평가 기준, 불일치)을 개선하기 위해 설계
    <details>
        <summary>해결 방법</summary>
          
      - 평가 기준을 세부적인 하위 측면으로 나눔
      - 각 측면별로 Boolean 질문 체크리스트를 만들어 평가 과정을 단순화
      - 해석 가능성 높임, 특정 평가 항목에 초점 → 결과의 견고성, 신뢰성 강화
    </details>

    <details>
        <summary>주요 성과</summary>
          
      - SummEval 벤치마크를 활용한 집중 사례 연구 → CheckEval: 인간의 판단과 높은 상관관계를 보임
      - IAA(Inter-Annotator Agreement)가 매우 높음
      - 객관적이고 유연하며 정밀한 평가에 효과적임을 입증
    </details>

    <details>
        <summary>중요 개념</summary>
      
      - CheckEval: 평가의 명확성과 일관성을 높이기 위해 설계된 LLM 기반 평가 프레임워크
      - Inter-Annotator Agreement (IAA): 평가자 간의 일치도를 측정하는 지표
      - SummEval : 요약에 대한 다양한 평가 방법을 비교하는 벤치마크 데이터셋
    </details>

- 📜 [Google] [PaliGemma 2: A Family of Versatile VLMs for Transfer](https://arxiv.org/abs/2412.03555)
  - PaliGemma 2: 기존 PaliGemma 모델을 기반으로 업그레이드된 VLM으로, Gemma 2 언어 모델 계열의 개선된 기능을 통합한 모델
  - Gemma 2 언어 모델 계열(2B ~ 27B 파라미터)과 SigLIP-So400m 비전 인코더 통합

    <details>
        <summary>3가지 해상도(224px², 448px², 896px²)에서 다단계 훈련</summary>
      
      - 전이 학습 능력 강화, 세부 조정 가능
      - 학습률, 작업 유형, 모델 크기, 해상도 등 전이 성능 영향 요소 분석
    </details>

    <details>
        <summary>작업 범위 확장</summary>
    
      - OCR 관련 작업: 테이블 구조, 분자 구조, 악보 인식
      - 세밀한 장기 캡션 생성, 방사선 보고서 작성
      - 다양한 전이 작업에서 최첨단 성능(SOTA) 달성
    </details>

    <details>
        <summary>중요 개념</summary>
  
      - Vision-Language Model (VLM): 이미지를 처리하는 비전 모델과 텍스트를 이해하는 언어 모델을 결합한 AI 모델
      - 전이 학습(Transfer Learning): 이미 학습된 모델을 새로운 작업에 적응시키는 방법
    </details>

  - [HuggingFace](https://huggingface.co/papers/2412.03555), [Kaggle](https://www.kaggle.com/models/google/paligemma-2)
</details>
  
<details>
  <summary>2nd week</summary>

- 🧑🏻‍💻 [NVIDIA] [Content Moderation and Safety Checks with NVIDIA NeMo Guardrails](https://developer.nvidia.com/blog/content-moderation-and-safety-checks-with-nvidia-nemo-guardrails/)
  - RAG application: 실시간으로 외부 데이터를 검색하고 LLM을 활용하여 동적인 콘텐츠를 생성
    - 안전하고 신뢰할 수 있는 응답을 보장하기 위해 content moderation 필수적
  - NVIDIA NeMo Guardrails: LLM의 입력 및 출력을 관리하는 toolkit/microservice

     <details>
         <summary>주요 기능</summary>
       
       - LlamaGuard
          - 입력/출력에서 부적절한 콘텐츠 감지
       - AlignScore
          - 응답의 사실 검증(검색 데이터와 생성된 결과 비교)

       - 기타 기능: 식별 정보(PII) 검출, 허위 정보 방지, 탈옥 감지 등
    </details>

    <details>
        <summary>적용 방법</summary>

      - NeMo Guardrails를 설치
      - RAG 애플리케이션과 연동
      - LlamaGuard 및 AlignScore 모델을 설정
      - NeMo Guardrails의 구성 파일(config.yml)에 통합
      - 보안 레이어를 구성하고 샘플 쿼리로 테스트
    </details>

- 🤪 [ElevenLabs](https://www.talktosanta.io/)

- 🤪 [Microsoft] [MicrosoftDesigner](https://designer.microsoft.com/design)

- 🧑🏻‍💻 [Docling] [Docling](https://ds4sd.github.io/docling/)
  - PDF, DOCX, PPTX 등 다양한 문서 형식을 읽어 Markdown 및 JSON 형식으로 변환하는 도구
  - 페이지 레이아웃, 읽기 순서, 표 구조 등을 포함한 고급 PDF 문서 이해 기능과 🦙 LlamaIndex, 🦜🔗 LangChain과의 쉬운 통합 제공
  - OCR 지원, CLI 제공 등 사용 편의성을 높였으며, 추후 방정식 및 코드 추출, 메타데이터 추출 기능 추가 예정
  - [2023년 최신판 OCR 8가지 API 비교평가 테스트](https://devocean.sk.com/blog/techBoardDetail.do?ID=165524&boardType=techBlog)
    - 다양한 OCR 서비스의 성능 및 속도를 비교 분석한 결과, Google Cloud Vision, Azure Document Intelligence, Upstage, Naver Clova 순으로 우수한 속도를 보임

- 🤪 [DVC] [DVC](https://dvc.org/)
  - DVC(Data Version Control): GitOps 원칙에 기반하여 대규모 데이터의 버전 관리 및 ML 모델링 프로세스의 재현 가능한 워크플로우 구축을 지원하는 오픈소스 플랫폼
  - [Github](https://github.com/iterative/dvc)

- 🧑🏻‍💻 [HuggingFace] [meta-llama/Llama-3.3-70B-Instruct](https://huggingface.co/meta-llama/Llama-3.3-70B-Instruct)
  - Meta Llama 3.3: Meta가 개발한 70B 파라미터 규모의 다국어 지원 LLM으로, 사전 학습과 명령어 조정을 통해 다국어 대화, 자연어 생성, 코딩 지원 등 다양한 사용 사례에 최적화
    <details>
        <summary>모델 아키텍처</summary>

      - 트랜스포머 기반: 최적화된 트랜스포머 아키텍처를 활용한 자동 회귀 모델
      - 명령어 조정: 감독 미세 조정(SFT)과 인간 피드백 기반 강화 학습(RLHF)을 통해 사용자의 도움 및 안전성 선호도에 맞게 조정됨
    </details>

    <details>
        <summary>벤치마크</summary>
    
      - MMLU(CoT): 86.0% 정확도
      - HumanEval: 88.4% 성공률
      - MATH(CoT): 77.0% 정확도
      - MGSM: 91.1% 정확도
    </details>

- 🧑🏻‍💻 [Upstage] [Solar Cookbook](https://github.com/UpstageAI/solar-prompt-cookbook)
  - Solar에 대한 프롬프트 A-Z를 담아, 누구나 더 쉽게 다룰 수 있도록 돕는 Cookbook
    - 프롬프트 엔지니어링의 기본 구조부터 복잡한 프롬프트 체이닝, 환각 해결법까지..
  - Small-Scale Model에 대한 Prompt Engineering의 insight 공유

  - [Solar_Prompt_Guide](https://github.com/studydev/Solar_Prompt_Guide)
    - Upstage Cookbook의 Prompt를 빠르게 실습할 수 있게 만들어놓은 환경
    - Upstage github repo를 fork 하여, GitHub의 CodeSpace 기반(가상 개발 컨테이너 환경)으로 필요한 몇 가지 환경 변수를 추가한 repo를 만들어놓음

- 📜 [Arcee, Florida, USA] [Arcee’s MergeKit: A Toolkit for Merging Large Language Models](https://arxiv.org/abs/2403.13257)
  <details>
      <summary>문제 상황</summary>
    
    - 특정 작업을 위해 사전 학습된 모델을 미세 조정하는 전이 학습의 발전으로 인해 수많은 작업별 특화 모델이 개발되었지만, 이들은 일반적으로 개별 작업에만 특화되어 있어 서로의 강점을 활용하지 못함
  </details>

  - MergeKit: 다수의 오픈소스 언어 모델을 효율적으로 통합하는 오픈소스 도구
    - 추가 학습 없이 모델의 성능과 다양성을 향상시키는 모델 병합 전략 지원
    - 다양한 하드웨어에서 사용 가능한 확장성 있는 프레임워크 제공
    - 이미 오픈소스 커뮤니티에서 수천 개의 모델 병합에 활용되어 Open LLM Leaderboard 상위권의 강력한 모델들을 생성하는 데 기여

  - [Github](https://github.com/arcee-ai/mergekit)

- 🧑🏻‍💻 [Amazon] [Amazon Nova and our commitment to responsible AI](https://www.amazon.science/blog/amazon-nova-and-our-commitment-to-responsible-ai)
  - Amazon Nova → Amazon에서 만든 책임감 있는 AI 개발을 위해 8가지 핵심 원칙(개인정보 보호 및 보안, 안전, 공정성, 정확성 및 견고성, 설명 가능성, 제어 가능성, 거버넌스, 투명성 등)을 바탕으로 한 새로운 멀티 모달 기반 모델
  - 이들을 제어하기 위해 SFT와 RLHF을 모두 사용하여 모델을 정렬
    - SFT → 여러 언어로 단일 및 다중 턴 훈련 데모
    - RLHF → 이전 평가의 예를 포함하여 인간의 선호도 데이터를 수집

  - 모델 개발 전 과정에서 자동화된 방법과 인간 피드백을 활용하여 편향성 평가 및 완화, 정확성 및 견고성 향상을 위한 다양한 테스트 및 벤치마크 진행, 적대적 공격에 대한 방어 및 워터마킹 기술 적용
  - 📜 [Amazon Nova Family 기술 보고서] [The Amazon Nova Family of Models: Technical Report and Model Card](https://assets.amazon.science/b0/2b/e74dd4f84f188701fd06792670e7/the-amazon-nova-family-of-models-technical-report-and-model-card.pdf)

- 🧑🏻‍💻 [Google] [python-genai](https://github.com/googleapis/python-genai)
  - Google Gen AI Python SDK: Google의 생성형 모델을 Python 애플리케이션에 통합할 수 있는 인터페이스 제공
  - 현재는 초기 출시 단계! API가 변경될 수 있으므로 프로덕션 환경에서는 사용하지 않는 것이 좋음
  - 텍스트 생성, 이미지 생성, 임베딩 등 다양한 기능 제공 및 비동기 처리 및 토큰 계산 기능 지원

- 📜 [NCSOFT] [VARCO-VISION: Expanding Frontiers in Korean Vision-Language Models](https://arxiv.org/pdf/2411.19103)
  - VARCO-VISION: 한국어와 영어를 모두 다룰 수 있는 이미지-텍스트 작업을 위해 설계된 오픈소스 VLM
    - 기존 모델의 지식을 유지하면서 시각적 정보와 언어 정보를 효과적으로 통합할 수 있도록 새로운 단계별 학습 전략 채택
  - 📊 5개의 한국어 평가 데이터셋 공개 → 4개의 폐쇄형 벤치마크, 1개의 개방형 벤치마크

    <details>
        <summary>주요 성과</summary>

      - 유사 크기의 모델과 비교해 이중언어 이미지-텍스트 이해 및 생성 능력에서 뛰어난 성능 입증
      - 다양한 기능 지원
        - Grounding: 이미지 내 객체 인식 및 위치 추적
        - Referring: 특정 객체를 지칭하는 작업
        - OCR: 이미지에서 텍스트를 추출하는 작업
    </details>

  - 🧑🏻‍💻 [HuggingFace][NCSOFT/VARCO-VISION-14B-HF](https://huggingface.co/NCSOFT/VARCO-VISION-14B-HF)

- 🧑🏻‍💻 [Google] [The next chapter of the Gemini era for developers](https://developers.googleblog.com/en/the-next-chapter-of-the-gemini-era-for-developers/)
  - Gemini 2.0 Flash: 개발자의 workflow를 개선하는 코딩 에이전트와 몰입적이고 대화형 애플리케이션 제작을 지원하는 AI플랫폼
    - 멀티모달 출력: 텍스트, 오디오, 이미지 통합 생성
    - 실시간 스트리밍 API: 오디오, 비디오 입력 지원
    - 도구 통합: Google 검색, 코드 실행 기능 지원 및 외부 도구와 연동 가능
    - AI 코드 에이전트: Jules로 자동화된 버그 수정 및 코드 작성
  - 현재는 실험 단계로 Gemini API를 통해 Google AI Studio 및 Vertex AI에서 사용 가능(내년 초 정식 출시)

- 🧑🏻‍💻 [NVIDIA] [LLaMA-Mesh:Unifying 3D Mesh Generation with Language Models](https://research.nvidia.com/labs/toronto-ai/LLaMA-Mesh/?linkId=100000318302360)
  - LLaMA-Mesh: 텍스트를 기반으로 사전 학습된 LLM의 기능을 확장하여 3D Mesh를 생성할 수 있는 통합 모델

    <details>
        <summary>장점</summary>
      
      - 튜토리얼 같은 텍스트 소스에서 파생된 LLM에 내재된 공간적 지식 활용 가능
      - 대화형 3D 생성 및 Mesh 이해 가능
    </details>
    <details>
        <summary>SFT 데이터셋 구성</summary>

      - 텍스트 프롬프트로 3D Mesh 생성
      - 텍스트와 3D Mesh를 혼합한 출력 생성
      - 3D Mesh를 이해하고 해석
    </details>

  - 📜 [Tsinghua Univ., NVIDIA] [LLaMA-Mesh: Unifying 3D Mesh Generation with Language Models](https://arxiv.org/abs/2411.09595)
</details>

<details>
  <summary>3rd week</summary>

- 📜 [FAIR at Meta, 2UC San Diego] [Training Large Language Models to Reason in a Continuous Latent Space](https://arxiv.org/abs/2412.06769)
  - LLM → 언어 공간이 항상 최적의 추론 방식을 제공하지는 않음
  - Coconut(Chain of Continuous Thought): 자연어 대신 제약 없는 잠재 공간에서 LLM 추론의 가능성을 탐구하기 위해 제시한 새로운 패러다임
    - 마지막 은닉 상태를 단어로 디코딩하지 않고, 다음 입력 임베딩으로 직접 활용해 추론 효율을 높임
    - 연속적 사고 → 단일 경로에 의존X, 여러 대안의 다음 추론 단계를 인코딩해 BFS 기반 문제 해결 가능
   
- 📜 [Maryland Univ., OpenAI] [The Prompt Report: A Systematic Survey of Prompting Techniques](https://arxiv.org/pdf/2406.06608)
  - 프롬프트 → GenAI 시스템과의 상호작용을 위한 주요 도구, 연구 초기 단계로 인해 용어와 개념이 혼재되어 있음
  - 목적: 프롬프트 기술의 분류 체계 구축, 주요 용어 정리 및 사용 사례 분석
    <details>
        <summary>성과</summary>

      - 어휘: 33개의 주요 프롬프트 관련 용어 정의
      - 텍스트 전용 프롬프트 기술의 분류 체계: 58가지
      - 다른 양식의 프롬프트 기술: 40가지
      - 자연어 prefix-prompting 관련 메타 분석 제시
    </details>

- 🗞️ [Google] [구글, 텍스트 프롬프트 없이 이미지 생성하는 '위스크' 공개](https://www.aitimes.com/news/articleView.html?idxno=166297)
  - 위스크(Whisk) → Google이 공개한 이미지 생성 AI
    <details>
          <summary>작동 방식</summary>

      - 구글의 이미지 생성 모델 Imagen 3 기반
      - 텍스트 프롬프트 대신 3가지 이미지(주제 이미지, 장면 이미지, 스타일 이미지)를 결합하여 새로운 이미지 생성
      - 입력 이미지를 바탕으로 자동 생성된 텍스트 캡션을 활용해 이미지 생성
    </details>
  - [Whisk](https://labs.google/fx/tools/whisk/unsupported-country)

- 🗞️ [Google] [Veo 2](https://deepmind.google/technologies/veo/veo-2/)
   - Veo 2: Google DeepMind에서 개발한 최첨단 비디오 생성 모델
   - 메타의 MovieGenBench 데이터셋 기반
   - 🗞️ ["구글의 비오 2, 소라에 압승"...테스터 비교 영상 속속 등장](https://www.aitimes.com/news/articleView.html?idxno=166379)

- 📜 [NYU] [Self-Reflection Outcome is Sensitive to Prompt Construction](https://arxiv.org/abs/2406.10400)
    - LLMs → zero-shot 및 few-shot 추론 능력을 보여줌 → Self-Reflection으로 개선 가능함을 제안
      - LLM 스스로 초기 응답의 실수를 식별하고 수정하게끔

      <details>
          <summary>주요 발견</summary>
        
        - 기존 Self-reflection 연구에서 사용된 대부분의 프롬프트는 편향을 포함 → LLM이 정답을 불필요하게 수정하도록 유도
        - 보수적인 프롬프트 설계를 통해 Self-Reflection의 정확도 향상을 입증
      </details>
  - [Github](https://github.com/Michael98Liu/mixture-of-prompts)
