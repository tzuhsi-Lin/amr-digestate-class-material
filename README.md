# Demo Dataset for R Programming Class: Antimicrobial Resistance Associated with Different Fertilizer Source

## Overview
[data](data) 資料夾內 .csv 檔為中央大學環工所林居慶老師團隊執行前環保署計畫「[商業有機肥料與沼渣沼液作為環境抗生素抗藥性發展的潛在來源探究](https://www.grb.gov.tw/search/planDetail?id=13380871)」所得之部份研究數據，僅供王孫崇老師「R 之系統生物應用」課堂教學使用。

## About this Research Project
除了人體醫療之外，抗生素 (antibiotics) 在畜牧產業也被廣泛應用，而無法完全被動物消化系統所吸收的抗生素也隨著「禽畜糞肥農用」途徑進入到土壤環境。
在抗生素的選擇壓力下，容易使得環境微生物產生突變，或透過水平基因轉移獲得抗生素抗性基因 (antibiotic resistance genes, ARGs)，讓抗藥性 (antimicrobial resistance, AMR) 問題變得更為嚴峻。

在將禽畜糞作為肥料重新利用之前，需經過一定的前處理，除了傳統的堆肥工法之外，前環保署 (現為環境部) 以及前農委會 (現為農業部) 自民國 104 年起大力推行「厭氧消化」工法，鼓勵農友將禽畜糞尿透過厭氧消化轉製為「沼液沼渣 (biogas residue)」作為肥料使用。
沼液沼渣的再利用不僅避免禽畜糞尿被排入環境水體，也節省農友施肥開支，創造新的產業價值。
然而若以公衛角度切入，禽畜糞被視為 ARGs 熱點，做為肥料施用潛藏著讓環境中 ARGs、抗藥性菌傳播的可能性。

為了讓相關疑慮得以釐清，本研究分為二階段進行：

1. **階段一 (Stage I)：** 採集具代表性的市售堆肥以及沼液沼渣樣本，檢測其中 (ARGs) 含量，並比較不同組別樣本 (市售堆肥 vs. 沼液沼渣)(不同動物來源) 的 ARGs 豐度 (abundance)。
2. **階段二 (Stage II)：** 製備實驗室規模縮模系統 (microcosm)，將市售堆肥、沼液沼渣、超純水 (對照組) 分別添加到土壤中，檢測在經過 30 天的培養之後，土壤中的 ARGs 豐度變化。

本計畫已結束，相關結果曾在 2023 年環工年會發表，此為[研討會簡報](https://drive.google.com/file/d/16I_Sj5RspPw_ez7N76SKzfut2cUBJRZX/view?usp=sharing)供參。

## Data Description
本節為各數據表格之簡要說明。

### Stage I Experiment
[Stage.I_data.csv](data/20220917_Stage.I_data.csv) 為階段一之檢測結果，以下為各欄數據說明：

* sample_id：樣品編號，BR 表示沼液沼渣 (biogas residue)；CS 表示市售堆肥樣品 (compost sample)
* species：各肥料的主要原料 (動物)
  * SW：swine (豬糞)
  * CA：cattle (牛糞)
  * PO：poultry (雞糞)
  * MM：mixed manure (混合糞肥)
  * LM：low manure (禽畜糞含量 < 50%)
  * NM：non manure (不含禽畜糞)
* Target genes (目標基因)：
  * Reference gene (參考基因)：16S rRNA gene
  * ARGs：
    * 四環素 (tetracycline) 抗性基因：*tetA*, *tetM*, *tetO*, *tetW*
    * 磺胺類藥物 (sulfonamide) 抗性基因：*sul1*, *sul2*
    * β-內醯胺 (β-lactam) 抗性基因：*bla*<sub>CTX-M</sub>, *bla*<sub>SHV</sub>, *bla*<sub>TEM</sub>
    * MLSB 抗性基因：*ermB*, *ermF*
  * Mobile genetic element (MGE)(移動性遺傳元件)：*intI1*
* Gene quantification (基因量化單位)：
  * Absolute abundance (**AA**)(絕對豐度)：gene copy/mL-biogas residue
  * Relative abundance (**RA**)(相對豐度)：gene copy/16S rRNA gene copy
* Chemical properties
  * 水質參數：pH、EC (電導度)、COD (化學需氧量)、TN (總氮)、TP (總磷)
  * 重金屬：Cu (銅)、Zn (鋅)
  * 抗生素濃度：
    * TET (四環素)：CTC、OTC、TC
    * SF (磺胺類藥物)：SDZ、SMZ、SMX、SP


### Stage II Experiment
[Stage.II_Tech.rep_data.csv](data/20220917_Stage.II_Tech.rep_data.csv) 為階段二之檢測結果，表格中 sample id、species、目標基因以及量化單位表示方法與 Stage I 實驗數據相同，以下為 Stage II 實驗數據表格新增之數據欄位說明：

* replicate_no：第二階段實驗中，每一土壤樣品、每一取樣時間均執行三重複，replicate_no 即標示為第幾重複之數據
* time：取樣時間，T0 為第 0 天；T30 為第 30 天


[Stage.II_Bio.rep_data.csv](data/20220917_Stage.II_Bio.rep_data.csv) 同樣為階段二之數據，但已將三重複之測值取平均。另外此表格還新增了反應動力學參數，以下為新增之數據欄位說明：

* Chan.ratio：change ratio，表示目標基因豐度的變化率
* Red.ratio：reduction ratio，表示目標基因豐度的削減率
* *k* ：反應速率常數 (first-order kinetics)
* T<sub>half</sub>：目標基因之半衰期


## References

1. 鄭念媛. 不同料源製成之市售堆肥其抗生素抗性基因含量調查. mastersthesis, 國立中央大學, 桃園縣, 2022. https://hdl.handle.net/11296/bncg6u.
2. 林子晞. 沼液沼渣的施用促成農地土壤抗生素抗性基因增殖的可能性探討. mastersthesis, 國立中央大學, 桃園縣, 2023. https://hdl.handle.net/11296/35jd58.
3. 李杰穎. 季節效應對沼液沼渣中抗生素抗性基因豐度之影響, 國立中央大學, 桃園縣, 2023. https://hdl.handle.net/11296/uu5hu5.
4. 陳宥丞. 不同肥料引入的抗生素抗性基因在實際農業土壤中的宿命, 國立中央大學, 桃園縣, 2023. https://hdl.handle.net/11296/ce3b83.
