# 碩論演示
## 大綱
  [研究背景與概述](#reaserch_backround)  
  [Python套件說明](#python_package) (###施工中###)  
  [FRBR與FRAD實體關係模型簡介](#FRBR_instruction)

<a name="reaserch_backround"/>

## 研究背景與概述
### 研究概述
  * 論文名稱

    >[小說讀者資訊尋找心智模型與FRBR之比較研究](https://etds.lib.tku.edu.tw/ETDS/Home/Detail/U0002-2307202123134400 "淡江碩博士論文系統")（2023/8開放全文）
  
  * 研究目的
  
      >瞭解小說讀者集體心智模型與書目紀錄功能要件（Functional Requirements for Bibliographic Records, FRBR）及權威需求功能要件（Functional Requirements for Authority Data, FRAD）等兩種實體關係模型之異同
  
  * 研究問題
  
      >讀者的資訊尋找心智模型包含哪些資料項目、值與關聯？又可對照至FRBR與FRAD的實際情形如何？

### 資料收集
  * 線上問卷（surveycake）
  * 半結構式訪談
  * 手機錄音、拍照

### 資料分析
  * EXCEL（問卷）、PPT（概念圖）
  * 新增：Python Graphviz套件
  * 新增：Python RDFlib套件

<a name="python_package"/>

## Python套件與概念圖JSON格式說明(###施工中###)
### Python套件說明
  * Grapviz
  
    >用於概念圖資料重繪的視覺化，但操作略複雜，未實際用於論文中，改以PPT手動重繪
    >
  
  ![範例](https://github.com/jerryyehself/Python-thesis/blob/main/example.png?raw=true "Graphviz示例")
  
### 概念圖JSON格式
  * 因涉及受訪者個資，無法將檔案釋出，格式如下：
  
    ```
    "受訪者編碼":
    {
      "資料元素":
      [
        {
          "概念圖編號":[0,0,0], ###一位受訪者共繪製三張概念圖，資料元素若出現於圖中則標示為1
          "資料元素出現次序": "1", ###可能同時出現，故部分數字重複，無法確定出現次序的標示為[]
          "資料元素內容（值）": "Hogwarts Express", ###受訪者自書上取出之資料元素的內容
          "資料元素屬性": "書中特定交通工具", ###受訪者認為資料元素為書本的什麼屬性
          "知識本體說明": ["所屬知識實體之屬性標籤", "所屬知識實體"],
          "本研究歸類": "角色相關資訊",
          "本研究歸納類目": "故事內容",
        },
        {
           ...  ###圖中其餘多個資料元素
        }
      ],
      "實體間關係":
      [
        {
          "主詞資料元素": "元素於概念圖元素陣列中的索引位置",  ###以"atr圖編號_元素編號"標示
          "元素間關係屬性說明":
          [
            {
              "概念圖編號": [0,0,0],
              "受詞資料元素": "元素於概念圖元素陣列中的索引位置",
              "關係線條呈現": "", ###分為虛線與實線，實線為空值，虛線為"dashed"
              "關係方向呈現": "", ###分為無向、單向與雙向，單向為空值（即主詞經述語指向受詞），雙向"both"，無向為"none"
              "述詞內容": "[認識]描述、想像",
              "知識本體說明" ["", ""]  ###同元素知識本體說明，但本研究最後未使用
             },
             {
                ...N個受詞  ###主詞資料元素指向的其他受詞資料元素，主詞可一對多受詞
             }
           ],
        },
        {
            ...  ##其餘主詞資料元素，包括如前示的元素關係與受詞描述
        }
      ]
    },
    ...  ###其餘資料受訪者概念圖資料
    ```
  * 實際範例
  
    ```
    "RR_01":
    {       
        "data_elements":
        [
            {
                "in_graph":[1,0,0],
                "element_number": "1",
                "element_content": "Hogwarts Express",
                "element_attribute": "書中特定交通工具",
                "in_ontology": ["frbrer:P3049(f)", "Object(fictional)"],
                "element_code": "角色相關資訊",
                "element_class": "故事內容"
            },  
            ...
        ],
        "relationships":
        [
            {                   
                "subject_element": "atr0_3",
                "relationship_attribute":
                [
                    {
                        "in_graph":[1,0,0],
                        "object_element": "atr0_5",
                        "relationship_edge_line": "",
                        "relationship_edge_direct": "",
                        "predicate":"[認識]描述、想像",
                        "in_ontology": ["", ""]
                    },
                    ...
                ]
            }
        ]           
    },
    ...
    ```
<a name="FRBR_instruction"/>

## FRBR與FRAD實體關係模型簡介</h2>
### FRBR
  * 資料實體  
  
    >由於用於書目資料，故也稱為 __書目實體__ 。書目實體共分為三組，分別為：
    
    * 第一組書目實體（Group 1）
    
      >作品（Work）、內容版本（Expression）、載體版本（Manifestation）、單件（Item）
      
    * 第二組書目實體（Group 2）
      
      >個人（Person）、團體（Corporate Body）
    
    * 第三組書目實體（Group 3）
    
      >主題（Subject）、物件（Object）、事件（Event）、地點（Place）
    
  * 實體關係
  
    >三組書目實體第一組實體的關係，包括：
    * 第一組四種實體間關係
    
      >作品至單件間的抽象至具體實例的雙向關係（有/被實現、有/被具體化、有/被實例），關係圖請參見[IFLA FRBR最終報告書]圖3.1（頁14）
    
    * 第一組實體與第二組實體間關係
      
      >個人或團體與第一組實體間的雙向關係，包括（被）創作、（被）實現、（被）製作、（被）擁有，關係圖請參見[IFLA FRBR最終報告書]圖3.2（頁15）
    
    * 第一組實體與第三組實體間關係
      
      >有主題，而第一組實體及第二組實體亦可以作品的主題關係與第一組實體關聯，關係圖請參見[IFLA FRBR最終報告書]圖3.3（頁16）
    
    [IFLA FRBR最終報告書]: https://repository.ifla.org/bitstream/123456789/811/2/ifla-functional-requirements-for-bibliographic-records-frbr.pdf
    
 ### FRAD
  * 模型簡述
  
    >使用FRBR個資料實體及實體關係，並擴充FRBR第一組實體與第二組實體間關係，並加入名稱、識別碼、控制詞彙與檢索點等要素</li>
  
  * 實體關係
    
    >關係圖請參見[IFLA FRAD報告書](https://www.ifla.org/wp-content/uploads/2019/05/assets/cataloguing/frad/frad_2013.pdf)圖2（頁7)                                                                                                                                        
  ### IFLA FRBR與FRAD知識本體
  
   * [FRBR知識本體](https://www.iflastandards.info/fr/frbr/frbrer.html)
   * [FRAD知識本體](https://www.iflastandards.info/fr/frad.html)
