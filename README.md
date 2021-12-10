
<h2>研究背景與概述</h2>
<h3>研究概述</h3>
  <ul>
    <li><b>論文名稱</b>：<a href="https://etds.lib.tku.edu.tw/ETDS/Home/Detail/U0002-2307202123134400">小說讀者資訊尋找心智模型與FRBR之比較研究</a>（2023/8開放全文）</li>
    <li><b>研究目的</b>：瞭解小說讀者集體心智模型與書目紀錄功能要件（Functional Requirements for Bibliographic Records, FRBR）及權威需求功能要件（Functional Requirements for Authority Data, FRAD）等兩種實體關係模型之異同</li>
    <li><b>研究問題</b>：讀者的資訊尋找心智模型包含哪些資料項目、值與關聯？又可對照至FRBR與FRAD的實際情形如何？
</li>
  </ul>
<h3>資料收集</h3>
  <ul>
    <li>線上問卷(surveycake)</li>
    <li>半結構式訪談</li>
    <li>手機錄音、拍照</li>
  </ul>

<h3>資料分析</h3>
  <ul>
    <li>EXCEL、PPT</li>
    <li>新增：Python Graphviz套件</li>
    <li>新增：Python RDFlib套件</li>
  </ul>
<h2>概念圖JSON檔與Python套件說明</h2>
<h3>Python套件說明</h3>
  <p>
  <span>Grapviz概念圖範例</span>
  <br>
  <img src="https://github.com/jerryyehself/Python-thesis/blob/main/example.png?raw=true" width=50%></img>
  </p>

<h2>FRBR與FRAD實體關係模型簡介</h2>
<h3>FRBR</h3>
  <ul>
    <li><b>資料實體</b>：共分為三組
      <ul>
        <li>第一組書目實體（Group 1）：作品（Work）、內容版本（Expression）、載體版本（Manifestation）、單件（Item）</li>
        <li>第二組書目實體（Group 2）：個人（Person）、團體（Corporate Body）</li>
        <li>第三組書目實體（Group 3）：主題（Subject）、物件（Object）、事件（Event）、地點（Place）</li>
      </ul>
    </li>
    <li><b>實體關係</b>：
      <ul>
        <li>第一組四種實體間關係：作品至單件間的抽象至具體實例的雙向關係（有/被實現、有/被具體化、有/被實例），關係圖請參見<a href="https://repository.ifla.org/bitstream/123456789/811/2/ifla-functional-requirements-for-bibliographic-records-frbr.pdf">IFLA原始報告書</a>圖3.1（頁14）</li>
        <li>第一組實體與第二組實體間關係：個人或團體與第一組實體間的雙向關係，包括（被）創作、（被）實現、（被）製作、（被）擁有，關係圖請參見<a href="https://repository.ifla.org/bitstream/123456789/811/2/ifla-functional-requirements-for-bibliographic-records-frbr.pdf">IFLA原始報告書</a>圖3.2（頁15）</li>
        <li>第一組實體與第三組實體間關係：有主題，而第一組實體及第二組實體亦可以作品的主題關係與第一組實體關聯，關係圖請參見<a href="https://repository.ifla.org/bitstream/123456789/811/2/ifla-functional-requirements-for-bibliographic-records-frbr.pdf">IFLA原始報告書</a>圖3.3（頁16）</li>
      </ul>
    </li>
</ul>
  <h3>FRAD</h3>
    <ul>
      <li><b>用途</b>：使用FRBR個資料實體及實體關係，並擴充FRBR第一組實體與第二組實體間關係，並加入名稱、識別碼、控制詞彙與檢索點等要素</li>
      <li><b>實體關係</b>：關係圖請參見<a href="https://www.ifla.org/wp-content/uploads/2019/05/assets/cataloguing/frad/frad_2013.pdf">IFLA原始報告書</a>圖2（頁7）<li>
    </ul>                                                                                                                                                
  <h3>知識本體</h3>
      <ul>
        <li><a href="https://www.iflastandards.info/fr/frbr/frbrer.html">FRBR知識本體</a></li>
        <li><a href="https://www.iflastandards.info/fr/frad.html">FRAD知識本體</a></li>
      </ul>
