
# ATHENA Developing Guide
---

## 1. 개요(Overview)

### 1.1. Introduction
[ATHENA](https://www.playchat.ai/developer/)는 머니브레인에서 개발한 챗봇 플랫폼으로서, Dialog Graph를 중심으로 챗봇을 직접 개발하고, 배포할 수 있는 툴입니다.


### 1.2. Tutorial

## 2. 시작해보기(Getting Started)

### 2.1. Make ChatBot
챗봇을 개발하기 위해서는, 일단 챗봇을 신규등록해야합니다.  
왼쪽 사이드바의 "챗봇관리 > 챗봇 리스트" 메뉴에서 신규등록 버튼을 클릭하여 챗봇을 등록합니다.  

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/botlist.png?raw=true)

봇 생성 페이지에서 봇 아이디, 봇 이름, 봇 설명, 대화파일, 템플릿을 입력하면 새로운 봇이 생성됩니다.  

- 봇아이디 : 영문자로 입력. unique한 값이며, 봇의 directory name.
- 봇이름 : 자유롭게 입력. 중복입력 가능. 실제로 다른 사람들에게 보이는 값.
- 설명 : 봇에 대한 간략한 설명.
- 대화파일 : Dialog Set 파일 등록. [4. Dialogset](#dialogset) 참조.

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/botcreate.png?raw=true)

봇 생성을 한 후에는, 오른쪽 위 선택창에서 봇을 선택해주세요. (봇이 보이지 않을 시, 새로 고침 후에 다시 시도해주세요.)  

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/botselect.png?raw=true)

## 3. 자연어 이해(NLU)
ATHENA에는 머니브레인의 자체 NLU모듈이 탑재되어있습니다. 사용자가 입력한 문장은 NLU모듈을 통해 분석되고, 결과값으로 Entity와 Intent를 받아옵니다. 개발자는 Entity와 Intent를 Dialog의 Input으로 설정하여 대화를 발생시킬수 있습니다. 또한 Entity를 Parameter로 사용하여, Task를 개발할 수 있습니다.

### 3.1. <a name="entity"></a>개체명(Entity)
Entity는 자연어 입력에서 필요한 parameter를 추출하는 강력한 도구입니다. 특정 봇에서 정의된 Entity는 봇의 기능에 따라 달라집니다. 즉, 모든 개념에 대하여 Entity를 설정할 필요는 없습니다.  
Entity를 새로 만들기 위해서는 왼쪽 사이드바의 "자연어 이해(NLU) > 개체명 분석(Entity)" 메뉴에서 신규등록 버튼을 클릭합니다.  

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/entitylist.png?raw=true)  

Entity 생성 페이지에서 엔터티명, 내용을 입력하면 새로운 Entity가 생성됩니다.  

- 엔터티 : 엔터티명. 이후 이 값을 대표명으로 사용하게 됩니다.
- 내용 추가 : Entity에 속하는 내용을 입력하고 추가버튼 혹은 enter를 누르면, 내용이 목록에 추가됩니다.

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/entitycreate.png?raw=true)


### 3.2. <a name="intent"></a>의도(Intent)
Intent는 입력한 문장들을 토대로 의도를 분석하는 도구입니다. Input으로 사용하기 위해 쓰이며, 봇의 Dialog 구조에 따라 필요한 Intent를 생성하여 사용합니다.  
Intent를 새로 만들기 위해서는 왼쪽 사이드바의 "자연어 이해(NLU) > 의도 분석(Intent)" 메뉴에서 신규등록 버튼을 클릭합니다.  

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/intentlist.png?raw=true)  

Intent 생성 페이지에서 인텐트명, 내용을 입력하면 새로운 Intent가 생성됩니다.  

- 인텐트 : 인텐트명. 이후 이 값을 대표명으로 사용하게 됩니다.
- 내용 추가 : Intent의 의미를 가지는 문장을 입력하고 추가버튼 혹은 enter를 누르면, 문장이 목록에 추가됩니다.

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/intentcreate.png?raw=true)
## <a name="dialogset"></a>4. DialogSet
대화셋(DialogSet)은 딥러닝을 통한 챗봇 개발을 할 수 있게 하는 도구입니다. 봇은 그래프와 대화셋 두가지 방법으로 구성될 수 있고, 함께 사용하는 것도 가능합니다. 대화셋은 '질문:답변 = 1:1' 방식으로 작성되어야 하며, 사용자의 입력 문장과 가장 유사도가 높은 질문을 찾아 답변을 출력하는 Retreival방식의 모델을 사용합니다. 그래프와 대화셋을 같이 사용하였을 경우에는, 그래프가 답변에서 우선순위를 가집니다.  
DialogSet을 새로 등록하기 위해서는 왼쪽 사이드바의 "대화 관리 > 대화셋 관리" 메뉴에서 신규등록 버튼을 클릭합니다.  

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/dialoglist.png?raw=true)

대화셋 등록 페이지에서 Title, Type, 공개여부, 파일을 입력하면 새로운 대화셋이 등록됩니다.

- Title : 대화셋명. 이후 이 값을 대표명으로 사용하게 됩니다.
- Type : 대화셋 파일의 유형. 현재 ATHENA에서는 csv, 카카오톡 백업파일, smi 세가지 유형의 파일을 사용할 수 있습니다.  
\* 참고 : csv 파일의 형식은 '행 수는 제한 없음, 열 수는 2열, 1열은 질문, 2열은 답변'입니다.
- File : 파일을 등록합니다. Type에서 선택한 형식의 파일 등록.
- Content : 대화셋에 대한 설명을 입력.

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/dialogcreate.png?raw=true)

대화셋을 등록한 이후에는, 관리자페이지에서 내용을 수정할 수 있습니다. 대화셋 리스트에서 수정하고자 하는 대화셋의 '대화 관리'버튼을 클릭하여 내용을 수정할 수 있습니다.

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/dialogedit.png?raw=true)

## 5. 챗봇 개발(Developing)
ATHENA는 대화를 그래프 형식의 UI로 만들어, 사용자가 쉽게 편집하고, 개발할 수 있는 툴을 제공합니다. 그래프는 \*.graph.js 형태의 파일로 저장되고, Task는 \*.js의 파일 형태로 저장됩니다.

### 5.1. Graph
그래프를 사용하기 위해서는 오른쪽 위 선택창에서 봇을 선택한 후, 왼쪽 사이드바 중 "챗봇 개발"을 클릭합니다. 네모난 박스가 input-task-output 구조를 가진 하나의 Dialog입니다. 상단 메뉴바의 "detailed"를 클릭하면, 확장된 형태의 Dialog box를 볼 수 있습니다. Dialog간의 관계는 선으로 표현되며, Children 관계는 회색선, Call 관계는 주황색 선으로 표현됩니다.

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/graph1.png?raw=true)

완성 그래프 예시

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/graph2.png?raw=true)

#### 5.1.1. Add & Delete
그래프에서 Child Dialog를 추가하기 위해서는 Parent Dialog의 +버튼을 클릭합니다. (단축키 : Insert)

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/graph3.png?raw=true)

Dialog를 삭제하기 위해서는 삭제하고자 하는 Dialog를 선택하고 x버튼을 클릭합니다. (단축키 : Del)

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/graph4.png?raw=true)

#### 5.1.2. Edit
Dialog를 수정하기 위해서는, 수정하고자 하는 Dialog를 선택하고, 수정버튼 (+의 왼쪽 버튼)을 클릭합니다. (단축키 : Enter)  

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/graph5.png?raw=true)

Dialog는 Input-Task-Output구조로 이루어져 있습니다.  

- Name : Dialog 이름. 이 후 이 값을 대표명으로 사용하게 됩니다.
- Input : [5.1.2.1. Input](#input) 참조.
- Task : [5.1.2.2. Task](#task) 참조.
- Output : [5.1.2.3. Output](#output) 참조.

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/graph6.png?raw=true)

##### <a name="input"></a>5.1.2.1. Input
Input은 자연어 처리된 사용자 입력에서 Dialog를 발동시키기 위한 것을 선택하는 도구입니다. Input에는 Text, Regexp, Type, If, Intent, Entity 6가지를 입력할 수 있습니다.  

- Text : 단순 keyword를 입력할 수 있습니다. 버튼 아래에 자연어 처리된 preview를 볼 수 있으며, 사용자가 keyword가 포함된 문장을 입력할 시, 발동됩니다. (keyword 사이에 띄어쓰기를 할 시, AND 조건으로 처리됩니다.)
- Regexp : Regular Expression을 입력할 수 있습니다. 사용자가 regexp에 match되는 문장을 입력할 시, 발동됩니다.
- Type : 주소, 핸드폰 번호, 자동차 번호, 날짜, 시간 등을 인식하는 Type을 선택할 수 있습니다.
- If : (Task를 사용할 때 사용됩니다.) Javascript의 if 조건문과 동일하게 사용됩니다. 결과값이 True일 시, 발동됩니다.
- Entity : 등록한 Entity를 선택할 수 있습니다. [3.1 Entity](#entity) 참조
- Intent : 등록한 Intent를 선택할 수 있습니다. [3.2 Intent](#intent) 참조

Input의 AND조건은 다음과 같이 입력합니다.

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/graph7.png?raw=true)

Input의 OR조건은 다음과 같이 입력합니다.

![image](https://github.com/VictorJeon/dev-guide/blob/master/images/graph8.png?raw=true)

##### <a name="task"></a>5.1.2.1. Task
Task는 Dialog에서 function을 수행하기 위한 도구입니다. Dialog에서 발동할 Task를 선택할 수 있습니다. 자세한 사항은 [5.2 Task](#task)를 참조하시기 바랍니다.

##### <a name="output"></a>5.1.2.1. Output

#### 5.1.3. Shortcut

### <a name="task"></a>5.2. Task

### 5.2.1. Params

### 5.2.2. Action

## 6. 운영 관리(Management)

## 7. 분석(Analytics)













