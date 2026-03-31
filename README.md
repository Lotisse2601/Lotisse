#主題

<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <style>
        :root {
            /* 醫用金屬與冷光色調 */
            --metal-bg: #1a1d21; /* 深色髮絲紋金屬背景底色 */
            --panel-steel: #e0e6ed; /* 拉絲不鏽鋼面板顏色 */
            --medical-cyan: #00ffff; /* 手術儀器冷藍光 */
            --medical-cyan-dim: rgba(0, 255, 255, 0.3);
            --blood-red: #ff3333; /* 警告/生命跡象紅色 */
            --text-dark: #121418;
            --text-light: #dbe2e9;
        }

        body {
            background-color: var(--metal-bg);
            /* 添加微小的金屬髮絲紋背景 */
            background-image: repeating-radial-gradient(circle at center, #23272d 0px, #1a1d21 1px, #23272d 2px);
            background-size: 4px 4px;
            color: var(--text-light);
            font-family: 'Inter', sans-serif, "Microsoft JhengHei";
            margin: 0;
            padding: 30px;
            line-height: 1.8;
            letter-spacing: 0.03em;
        }

        /* 主標題：金屬銘版風格 */
        .main-title {
            font-size: 2.8em;
            font-weight: 900;
            margin-bottom: 30px;
            color: var(--panel-steel);
            text-transform: uppercase;
            letter-spacing: 0.1em;
            text-align: center;
            /* 金屬蝕刻與發光效果 */
            text-shadow: -1px -1px 1px rgba(255,255,255,0.3), 1px 1px 1px rgba(0,0,0,0.8), 0 0 10px var(--medical-cyan);
            border-bottom: 3px solid var(--panel-steel);
            padding-bottom: 15px;
            position: relative;
        }
        
        /* 標題裝飾：模擬鉚釘 */
        .main-title::before, .main-title::after {
            content: '';
            position: absolute;
            bottom: -8px;
            width: 10px;
            height: 10px;
            background: #aaa;
            border-radius: 50%;
            box-shadow: inset -1px -1px 2px #000, 1px 1px 2px rgba(255,255,255,0.5);
        }
        .main-title::before { left: 10px; }
        .main-title::after { right: 10px; }

        .intro-section {
            margin-bottom: 40px;
            font-size: 1em;
            color: #b0bac5;
            padding: 20px;
            background: rgba(0, 0, 0, 0.2);
            border-left: 4px solid var(--medical-cyan-dim);
        }

        /* 互動式摺疊區塊：手術箱/儀器面板風格 */
        details {
            margin-bottom: 15px;
            background: linear-gradient(145deg, #2a2f36, #1e2227); /* 金屬立體感漸層 */
            border: 1px solid #444;
            box-shadow: 3px 3px 6px rgba(0,0,0,0.5), inset 1px 1px 1px rgba(255,255,255,0.1);
            transition: all 0.3s ease;
        }

        details[open] {
            border: 1px solid var(--medical-cyan);
            box-shadow: 0 0 15px var(--medical-cyan-dim), 3px 3px 6px rgba(0,0,0,0.5);
        }

        summary {
            cursor: pointer;
            padding: 15px 20px;
            font-weight: bold;
            font-size: 1.2em;
            color: var(--panel-steel);
            list-style: none;
            display: flex;
            align-items: center;
            outline: none;
            text-shadow: 1px 1px 2px rgba(0,0,0,0.8);
            position: relative;
        }

        summary::-webkit-details-marker { display: none; }
        
        /* 銳利的手術刀型箭頭 */
        summary::before {
            content: "";
            display: inline-block;
            width: 0;
            height: 0;
            border-style: solid;
            border-width: 8px 0 8px 14px;
            border-color: transparent transparent transparent var(--panel-steel);
            margin-right: 15px;
            transform: rotate(0deg);
            transition: transform 0.2s, border-color 0.2s;
            filter: drop-shadow(0 0 2px var(--medical-cyan));
        }

        details[open] summary::before {
            transform: rotate(90deg);
            border-color: transparent transparent transparent var(--medical-cyan);
        }
        
        /* 模擬儀器指示燈 */
        summary::after {
            content: '';
            position: absolute;
            right: 20px;
            width: 12px;
            height: 12px;
            background-color: #333; /* 關閉狀態 */
            border-radius: 50%;
            box-shadow: inset 0 0 3px #000;
            transition: background-color 0.3s, box-shadow 0.3s;
        }
        
        details[open] summary::after {
            background-color: var(--medical-cyan); /* 激活狀態 */
            box-shadow: 0 0 10px var(--medical-cyan), inset 0 0 3px #fff;
        }

        .content-inner {
            padding: 10px 30px 25px 50px;
            font-size: 1em;
            color: #d0dbe5;
            border-top: 1px solid #444;
        }

        /* 數據面板：儀器螢幕風格 */
        .data-panel {
            margin-top: 20px;
            background: rgba(0, 0, 0, 0.5);
            border: 2px solid #555;
            padding: 15px;
            font-family: 'Courier New', monospace; /* 保持數據的科技感 */
            box-shadow: inset 0 0 10px #000;
        }

        .data-panel::before {
            content: 'BIOMETRIC DATA MONITOR';
            font-size: 0.7em;
            color: #777;
            display: block;
            margin-bottom: 10px;
            border-bottom: 1px solid #333;
        }

        .data-row {
            display: flex;
            justify-content: space-between;
            margin-bottom: 8px;
            border-bottom: 1px dashed #333;
        }

        .highlight {
            color: var(--medical-cyan);
            font-weight: bold;
            text-shadow: 0 0 5px var(--medical-cyan-dim);
        }

        .danger {
            color: var(--blood-red);
            font-weight: bold;
            text-shadow: 0 0 5px rgba(255, 51, 51, 0.5);
            animation: pulse 2s infinite;
        }
        
        @keyframes pulse {
            0% { opacity: 1; }
            50% { opacity: 0.6; }
            100% { opacity: 1; }
        }

        .footer-tag {
            margin-top: 50px;
            font-size: 0.8em;
            text-align: right;
            color: #555;
            border-top: 1px solid #333;
            padding-top: 10px;
            font-family: monospace;
        }
    </style>
</head>
<body>

    <div class="main-title">妄二虛間</div>

    <div class="intro-section">
        <p>繁華之城的野心，數百萬生命流逝<br>
        一場數百年的實驗，使生存成為奢望、自由成為妄想</p>
        <p>赤色長河與刀鋒爭鬥，一步步牽線成為強權手下的傀儡</p>
        <p>沒有終點的壽命，是生命的蛻變也是一生的枷鎖</p>
    </div>

    <details>
        <summary>人類基因改造計畫</summary>
        <div class="content-inner">
            <p>此計畫於希恩在位653年時被帝國內各個貴族聯合壓迫下宣告結束，死亡人數超過180萬人。</p>
            <p>因此計畫為各個未知區域的探索帶來巨大貢獻，所以希恩仍然是統治帝國的權力者。此計畫被迫害的人在接受巨額賠償金之後大多隱居在各處，或者隱姓埋名繼續擔任雇傭兵。</p>
            <p>希恩內部高層在無法控制洛緹絲後曾試圖說服她入駐皇家，但遭其拒絕並被其殺害不少過往行為極度殘忍的部分高層。</p>
        </div>
    </details>

    <details>
        <summary>[syn 實驗所]</summary>
        <div class="content-inner">
            <p>希恩統治帝國200多年時內部高層經會議決定後建立，並在五大區各個地方都設有分部。</p>
            <p>雇傭大量傭兵尋找年齡7-10歲的孩子並將其帶走到實驗所中控制進行藥物注射，400多年來實驗總人數高達200萬人。</p>
            
            <div class="data-panel">
                <div class="data-row"><span>FIRST BATCH SUBJECTS</span><span class="highlight">10,000</span></div>
                <div class="data-row"><span>SURVIVAL RATE (INJECTION)</span><span class="danger">~ 0.84%</span></div>
                <div class="data-row"><span>PHYSIOLOGICALLY INTACT</span><span class="highlight">1</span></div>
                <div class="data-row"><span>TOTAL SUBJECTS (CUMULATIVE)</span><span class="highlight">2,000,000</span></div>
            </div>
        </div>
    </details>

    <div class="footer-tag">
        MED_OS v2.1 // SUBJECT_STATUS: MONITORING // VOID_E2
    </div>

</body>
</html>


<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <style>
        :root {
            /* 醫用金屬與冷藍光色調 */
            --metal-bg: #1a1d21;
            --panel-steel: #e0e6ed;
            --medical-cyan: #00ffff;
            --medical-cyan-dim: rgba(0, 255, 255, 0.3);
            --text-light: #dbe2e9;
            --box-bg: rgba(45, 52, 60, 0.6);
        }

        body {
            background-color: var(--metal-bg);
            background-image: repeating-radial-gradient(circle at center, #23272d 0px, #1a1d21 1px, #23272d 2px);
            background-size: 4px 4px;
            color: var(--text-light);
            font-family: 'Inter', sans-serif, "Microsoft JhengHei";
            margin: 0;
            padding: 30px;
            line-height: 1.8;
            letter-spacing: 0.03em;
        }

        /* 區域標題：金屬銘版風格 */
        .header-section {
            border-left: 5px solid var(--medical-cyan);
            padding-left: 20px;
            margin-bottom: 40px;
            background: linear-gradient(90deg, rgba(0, 255, 255, 0.05), transparent);
        }

        .region-name {
            font-size: 2.2em;
            font-weight: 900;
            margin: 0 0 15px 0;
            color: var(--panel-steel);
            text-transform: uppercase;
            text-shadow: 0 0 10px var(--medical-cyan-dim);
        }

        .region-desc {
            font-size: 1em;
            color: #b0bac5;
        }

        /* 陣營摺疊塊 */
        details {
            margin-bottom: 15px;
            background: linear-gradient(145deg, #2a2f36, #1e2227);
            border: 1px solid #444;
            box-shadow: 3px 3px 6px rgba(0,0,0,0.5);
            transition: all 0.3s ease;
        }

        details[open] {
            border: 1px solid var(--medical-cyan);
            box-shadow: 0 0 15px var(--medical-cyan-dim);
        }

        summary {
            cursor: pointer;
            padding: 15px 20px;
            font-weight: bold;
            font-size: 1.2em;
            color: var(--panel-steel);
            list-style: none;
            display: flex;
            align-items: center;
            outline: none;
        }

        summary::-webkit-details-marker { display: none; }
        summary::before {
            content: "";
            display: inline-block;
            width: 0;
            height: 0;
            border-style: solid;
            border-width: 8px 0 8px 14px;
            border-color: transparent transparent transparent var(--panel-steel);
            margin-right: 15px;
            transform: rotate(0deg);
            transition: transform 0.2s;
        }

        details[open] summary::before {
            transform: rotate(90deg);
            border-color: transparent transparent transparent var(--medical-cyan);
        }

        .content-inner {
            padding: 10px 30px 25px 50px;
            border-top: 1px solid #444;
            background: var(--metal-bg);
        }

        /* 家族/單位標題 */
        .unit-label {
            color: var(--medical-cyan);
            font-weight: bold;
            font-size: 1.1em;
            margin-top: 25px;
            margin-bottom: 10px;
            display: block;
            border-bottom: 1px solid var(--medical-cyan-dim);
            width: fit-content;
            padding-right: 30px;
        }

        /* 內容數據盒 */
        .data-box {
            background: var(--box-bg);
            border: 1px solid rgba(255, 255, 255, 0.1);
            padding: 15px 20px;
            margin: 10px 0;
            box-shadow: inset 0 0 10px rgba(0,0,0,0.5);
        }

        .data-box ul {
            list-style: none;
            padding: 0;
            margin: 0;
        }

        .data-box li {
            margin-bottom: 5px;
            color: #dbe2e9;
        }

        p {
            margin: 12px 0;
            color: #b0bac5;
        }

        .divider {
            height: 1px;
            background: linear-gradient(90deg, var(--medical-cyan-dim), transparent);
            margin: 30px 0 10px 0;
        }

        .footer-tag {
            margin-top: 50px;
            font-size: 0.8em;
            text-align: right;
            color: #555;
            font-family: monospace;
        }
    </style>
</head>
<body>

    <div class="header-section">
        <div class="region-name">【聖彌可帝國 (西區)】</div>
        <div class="region-desc">
            冰冷的機械聲與忙碌的腳步，沒有人情味的社會只剩科技與時間的搏鬥在資源荒涼的世代不斷找尋新科技，自給自足的代價是強權的壓迫
        </div>
    </div>

    <details>
        <summary>中立派</summary>
        <div class="content-inner">
            <span class="unit-label">[希恩家族（皇家）]</span>
            <div class="data-box">
                <ul>
                    <li>1. 繼位長達六百多年</li>
                    <li>2. 主張公正執法、帝國發展為第一優先</li>
                    <li>3. 具三大非家族勢力支持</li>
                    <li>4. 除帝國境內的人民外都是「劣種」</li>
                    <li>5. 位於帝國西南部</li>
                </ul>
            </div>
            <p>於在位二百多年時開始啟動「人類基因改造計畫」，在此期間不斷在帝國外的地區尋找幼年孩子進行藥物實驗</p>
            <p>在位五百多年時計畫敗露但因各家利益牽扯導致帝國主權仍然掌握在手中</p>

            <div class="divider"></div>
            <span class="unit-label">[希爾曼家族（子爵）]</span>
            <p>(原為希爾文家族，後因內部爭鬥改名)</p>
            <div class="data-box">
                <ul>
                    <li>1. 原為希爾文，經聖殿提拔取得爵位</li>
                    <li>2. 主張能力至上、無情</li>
                    <li>3. 表面無站隊，但暗裡會配合皇家行動</li>
                    <li>4. 男權家族</li>
                </ul>
            </div>
            <p>希恩在位四百多年時因族內內訌產生權力挑戰，當代家主變挑戰成功後飲毒自殺。而希爾文家族也不復存在，由希爾曼家族接續</p>

            <div class="divider"></div>
            <span class="unit-label">[聖希維爾軍團]</span>
            <div class="data-box">
                <ul>
                    <li>1. 駐守於西區南部邊疆</li>
                    <li>2. 主張團結、紀律</li>
                    <li>3. 與邊境地帶的勢力有交易往來</li>
                    <li>4. 軍令至上</li>
                </ul>
            </div>
            <p>聖彌可最著名的就職方向，高福利及不受貴族控制的地位使每年都有無數平民爭奪名額。當然每年也有貴族會將自己部分子弟送入盼望他們能成為自己未來的助力</p>
            <p>具有挑戰制度，每十年舉行一次大會，輪替萬夫長以下軍職，以上則二十年輪替一次統帥等高層則是五十年輪替一次</p>
            <p>在役期間可對比自己高的軍職發起挑戰兩次不限時間，兩次皆失敗則失去下次挑戰大會的名額並且具有重大功勞也不予升軍職最低服役時間為二十年，十年後可自行決定是否留於軍中</p>

            <div class="divider"></div>
            <span class="unit-label">[奧雷伊索聖殿]</span>
            <div class="data-box">
                <ul>
                    <li>1. 富可敵國</li>
                    <li>2. 主張平等、清心寡慾</li>
                    <li>3. 帝國最高權力</li>
                    <li>4. 主神至上</li>
                </ul>
            </div>
            <p>聖彌可帝國主心骨，平時不管事因此會扶持家族以確保在控管範圍內聖殿每五年選拔新人選進入其中靜修，只選擇有緣之人（錢緣未盡者也可再續前緣）</p>
            <p>完成修業者可在聖殿範圍內獲得一穩定職業，也可決定離開聖殿。未完成者則永久失去進入聖殿的機會</p>
        </div>
    </details>

    <details>
        <summary>激進派</summary>
        <div class="content-inner">
            <span class="unit-label">[艾德里克家族（伯爵）]</span>
            <div class="data-box">
                <ul>
                    <li>1. 從商貴族，位高權重</li>
                    <li>2. 主張利益至上、金錢主義</li>
                    <li>3. 曾提出「將平民改造成機械人以獲取永久勞動力」的荒謬想法</li>
                </ul>
            </div>
            <p>不受聖殿待見，但因每年繳納高額貢獻金使其爵位尚存，但也因此無法晉升公爵</p>

            <div class="divider"></div>
            <span class="unit-label">[瓦拉家族（伯爵）]</span>
            <div class="data-box">
                <ul>
                    <li>1. 科技著名</li>
                    <li>2. 主張知識&數據才是真理</li>
                    <li>3. 受軍團喜愛</li>
                    <li>4. 厭惡聖殿</li>
                </ul>
            </div>
            <p>為了希恩研究中的數據而私下達成了某種協議。看不慣聖殿以神為信仰的行為但礙於權力表面仍然尊敬</p>

            <div class="divider"></div>
            <span class="unit-label">[貝拉維塔家族（子爵）]</span>
            <div class="data-box">
                <ul>
                    <li>1. 因族中出了一位奧雷伊索副主教從而榮獲爵位</li>
                    <li>2. 主張信仰至上</li>
                    <li>3. 厭惡瓦拉，與艾德里克交好</li>
                    <li>4. 未完成奧雷伊索修業者一律處死</li>
                </ul>
            </div>
            <p>希恩在位三百多年時第486代副主教米德．貝爾維塔因平民出身，為了將自己姓氏留存於世向聖殿申請了爵位並於兩年後成功通過。也立下了以信仰為中心的一切家規</p>

            <div class="divider"></div>
            <span class="unit-label">[彭布曼家族（男爵）]</span>
            <div class="data-box">
                <ul>
                    <li>1. 瓦拉扶持獲得爵位，因聖殿在其中阻擾導致無法晉升更高位貴族</li>
                    <li>2. 主張韜光養晦、謙卑</li>
                    <li>3. 背後培養兩隊未知力量駐守於孟凡倫特</li>
                    <li>4. 厭惡瓦拉</li>
                </ul>
            </div>
            <p>認為因為瓦拉家族的扶持才導致家族受聖殿厭惡並無法提升地位，只能成為瓦拉的附庸。暗地中在各個家族裡都安排了探子探查消息，也創建了情報網匿名出售消息</p>
        </div>
    </details>

    <details>
        <summary>保守派</summary>
        <div class="content-inner">
            <span class="unit-label">[孟思萊德家族（公爵）]</span>
            <div class="data-box">
                <ul>
                    <li>1. 老牌貴族</li>
                    <li>2. 主張忠誠、淡泊名利</li>
                    <li>3. 受聖殿喜愛</li>
                    <li>4. 盲目追隨者處死</li>
                </ul>
            </div>
            <p>原是聖殿想扶持成皇家的貴族，因當時高層們一致認為不適合才換希恩上位公爵地位為一代代皇家慢慢升上來的，盡忠職守無野心，使孟思萊德幾乎是每代皇家並需要取得支持的家族</p>

            <div class="divider"></div>
            <span class="unit-label">[貝里安家族（男爵）]</span>
            <div class="data-box">
                <ul>
                    <li>1. 姓氏前身為世代奴隸，由孟思萊德提拔獲得爵位</li>
                    <li>2. 主張血統其次，榮譽至上</li>
                    <li>3. 歧視一切靠家世而不努力的貴族子弟</li>
                    <li>4. 會定期收養孤兒或年幼奴隸培養成族內力量</li>
                </ul>
            </div>
            <p>配戴貝里安姓氏者大多與其血統並無太大關係，通常為被收養者經培養後授予其姓氏每代貝里安家主由對帝國有最高奉獻者繼承</p>

            <div class="divider"></div>
            <span class="unit-label">[法羅拉斯家族（子爵）]</span>
            <div class="data-box">
                <ul>
                    <li>1. 貿易起家</li>
                    <li>2. 主張秩序、規律，注重體面與禮統</li>
                    <li>3. 對外以高尚名聲著名</li>
                    <li>4. 有繁瑣的禮節條款學習手冊</li>
                </ul>
            </div>
            <p>因駐地位置靠海使其在貿易方面具有不小的成就，並在帝國中有一定佔比的重要性，因此被皇家重視距離學院遙遠而在駐地內有專設一所學院以應付多數子弟的學習需求</p>

            <div class="divider"></div>
            <span class="unit-label">[柯尼斯學院]</span>
            <div class="data-box">
                <p>為窮苦人家專門設立的學院，由孟思萊德和貝里安合作協辦。學費、住宿全免，課業優異者甚至有獎學金輔助完成學業的排名前5%可獲得得到聖殿實習或者進軍團擔任文職的機會</p>
            </div>
            <p>因學生多為勤勉之人，使帝國每年優秀人才增加許多，皇家和聖殿也會定期到當地親自挑選合適的人才</p>
        </div>
    </details>

    <div class="footer-tag">
        MED_OS v2.4 // REGION: WEST_SECTOR // SYSTEM_STATUS: MONITORING
    </div>

</body>
</html>


<!DOCTYPE html>
<html lang="zh-TW">
<head>
    <meta charset="UTF-8">
    <style>
        :root {
            --metal-bg: #1a1d21;
            --panel-steel: #e0e6ed;
            --medical-cyan: #00ffff;
            --medical-cyan-dim: rgba(0, 255, 255, 0.3);
            --text-light: #dbe2e9;
            --poison-green-bg: rgba(35, 45, 35, 0.6); /* 暗綠色調模擬萬毒之地感 */
            --box-border: rgba(0, 255, 255, 0.1);
        }

        body {
            background-color: var(--metal-bg);
            background-image: repeating-radial-gradient(circle at center, #23272d 0px, #1a1d21 1px, #23272d 2px);
            background-size: 4px 4px;
            color: var(--text-light);
            font-family: 'Inter', sans-serif, "Microsoft JhengHei";
            margin: 0;
            padding: 30px;
            line-height: 1.8;
            letter-spacing: 0.03em;
        }

        /* 頂部標題與介紹：萬毒之地 */
        .header-section {
            border-left: 5px solid #4ade80; /* 萬毒之地採用毒素綠色標示 */
            padding-left: 20px;
            margin-bottom: 40px;
            background: linear-gradient(90deg, rgba(74, 222, 128, 0.05), transparent);
        }

        .region-name {
            font-size: 2.2em;
            font-weight: 900;
            margin: 0 0 15px 0;
            color: var(--panel-steel);
            text-transform: uppercase;
            text-shadow: 0 0 10px rgba(74, 222, 128, 0.3);
        }

        .region-desc {
            font-size: 1em;
            color: #b0bac5;
        }

        /* 互動式摺疊塊 */
        details {
            margin-bottom: 15px;
            background: linear-gradient(145deg, #2a2f36, #1e2227);
            border: 1px solid #444;
            box-shadow: 3px 3px 6px rgba(0,0,0,0.5);
            transition: all 0.3s ease;
        }

        details[open] {
            border: 1px solid var(--medical-cyan);
            box-shadow: 0 0 15px var(--medical-cyan-dim);
        }

        summary {
            cursor: pointer;
            padding: 15px 20px;
            font-weight: bold;
            font-size: 1.2em;
            color: var(--panel-steel);
            list-style: none;
            display: flex;
            align-items: center;
            outline: none;
        }

        summary::-webkit-details-marker { display: none; }
        summary::before {
            content: "";
            display: inline-block;
            width: 0;
            height: 0;
            border-style: solid;
            border-width: 8px 0 8px 14px;
            border-color: transparent transparent transparent var(--panel-steel);
            margin-right: 15px;
            transform: rotate(0deg);
            transition: transform 0.2s;
        }

        details[open] summary::before {
            transform: rotate(90deg);
            border-color: transparent transparent transparent var(--medical-cyan);
        }

        .content-inner {
            padding: 10px 30px 25px 50px;
            border-top: 1px solid #444;
            background: var(--metal-bg);
        }

        /* 勢力標題 */
        .force-label {
            color: #4ade80; /* 綠色字體 */
            font-weight: bold;
            font-size: 1.1em;
            margin-top: 25px;
            margin-bottom: 10px;
            display: block;
            border-bottom: 1px solid rgba(74, 222, 128, 0.2);
            width: fit-content;
            padding-right: 30px;
        }

        /* 內容數據盒 */
        .data-box {
            background: var(--poison-green-bg);
            border: 1px solid var(--box-border);
            padding: 15px 20px;
            margin: 10px 0;
            box-shadow: inset 0 0 10px rgba(0,0,0,0.5);
            font-size: 0.95em;
        }

        p {
            margin: 12px 0;
            color: #b0bac5;
        }

        .divider {
            height: 1px;
            background: linear-gradient(90deg, rgba(74, 222, 128, 0.2), transparent);
            margin: 30px 0 10px 0;
        }

        .footer-tag {
            margin-top: 50px;
            font-size: 0.8em;
            text-align: right;
            color: #555;
            font-family: monospace;
        }
    </style>
</head>
<body>

    <div class="header-section">
        <div class="region-name">【萬毒之地（中區）】</div>
        <div class="region-desc">
            人為的污染與資源的消耗，人們長時以面具抵擋空氣中未知的毒素，依賴外地糧食與水源少部分人因禍得福免疫毒素成為一方霸主，將重心放在工業上以求得更高權力的支持
        </div>
    </div>

    <details>
        <summary>萬毒城</summary>
        <div class="content-inner">
            <span class="force-label">[法蘭]</span>
            <div class="data-box">
                萬毒城之首，歷代家主因實力高強且據說與帝國內人物有關係從而繼位至今<br>
                城內擁有可以不被毒素干擾的儀器，因此人流密集度高每五年舉辦一次全城的清剿活動，以定期清理萬毒山脈中的魔物<br>
                但從二百年前便不再舉辦，轉為定期委託的方式清理，據說是當時城主在大會期間長子和其隨從皆隕落，悲痛之下頒下的公告
            </div>

            <div class="divider"></div>
            <span class="force-label">[梅倫]</span>
            <div class="data-box">
                外地移居，非中區本地勢力，但依靠高明的制工與防毒技術在城中奪得一席之位
            </div>

            <div class="divider"></div>
            <span class="force-label">[薩摩金]</span>
            <div class="data-box">
                主業是海上貿易，與帝國和雪紗城部分地區皆有交易來往<br>
                暗中與奎金達成交易合作，定期搶奪法蘭冒險隊隊伍並分贓
            </div>

            <div class="divider"></div>
            <span class="force-label">[洛笙]</span>
            <div class="data-box">
                表面是萬毒城中最龐大傭兵團，除了傭兵委託之外也會進行城中交易往來<br>
                暗地裡有名為“夜夢”的殺手組織，用特殊的委託渠道才能知道這個組織，業務範圍涵蓋除南區之外的範圍
            </div>

            <div class="divider"></div>
            <span class="force-label">[奎雷那]</span>
            <div class="data-box">
                負責控制流民地帶暴動，與雪紗城有奴隸交易，在無人管控的區域中是地頭蛇的存在
            </div>
        </div>
    </details>

    <details>
        <summary>墨樹林沼澤帶</summary>
        <div class="content-inner">
            <div class="data-box">
                沼澤帶毒，當地土壤是煉藥的極好材料，生物大多攻擊性高且免疫毒物，同樣其血液作為藥劑時具有極強的藥效<br><br>
                就學期間七年，若未在時間內完成學業，最多延後三年，若十年內未完成則成為學院內雜役，就算是貴族也無法避免
            </div>
        </div>
    </details>

    <details>
        <summary>紫青岩礦山</summary>
        <div class="content-inner">
            <div class="data-box">
                盛產紫青岩，可用於製造武器、能量炮，甚至可以當成燃料，是聖彌可中大量需要的物品
            </div>
            <p style="color: #4ade80;">目前由瓦拉家族和聖希維爾軍團掌控</p>
        </div>
    </details>

    <details>
        <summary>成可尼爾水域</summary>
        <div class="content-inner">
            <span class="force-label">[密坦達灣]</span>
            <div class="data-box">
                因萬毒山脈的地形遮擋使寂冰之喉中的極端寒風不會影響到灣內，因此建造許多碼頭和漁業<br><br>
                靠近聖彌可帝國的邊界地帶目前由貝爾維塔和法羅拉斯家族掌控，其餘為萬毒城掌控區塊
            </div>
        </div>
    </details>

    <details>
        <summary>萬毒山脈</summary>
        <div class="content-inner">
            <span class="force-label">[羅布倫村]</span>
            <div class="data-box">
                位於萬毒山脈西邊山腳，因接近軍團轄地因而安全受到保障，當地以農業自給自足為主
            </div>

            <div class="divider"></div>
            <span class="force-label">[奎金]</span>
            <div class="data-box">
                定點於萬毒山脈南邊高緯度斷崖附近一處山洞中，對山中地貌極為熟悉，因定點隱密沒人知道他們真正的大本營在何處
            </div>

            <div class="divider"></div>
            <span class="force-label">[米拉爾]</span>
            <div class="data-box">
                一群非人類種族，定居在萬毒山脈山腳下一處山洞中，平時靠法蘭發布的委託和挖礦、鍛造交易維生<br>
                喜好燉湯和山泉水，因其廚藝高超因此不少法蘭人會僱用他們當廚師
            </div>
        </div>
    </details>

    <div class="footer-tag">
        MED_OS v2.4 // REGION: CENTRAL_TOXIC_ZONE // SYSTEM_STATUS: MONITORING
    </div>

</body>
</html>

