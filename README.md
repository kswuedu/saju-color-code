[Index.html] 
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>사주&amp;컬러코드 | 정통 만세력 &amp; 기질 컬러 · 궁합 심층 리포트</title>
  <style>
    :root {
      --bg: #f8fafc;
      --card: #ffffff;
      --text-main: #0f172a;
      --text-body: #334155;
      --text-sub: #64748b;
      --border: #e2e8f0;
      --wood: #2e8b57;
      --fire: #e05252;
      --earth: #d99b26;
      --metal: #64748b;
      --water: #2563eb;
    }
    * { box-sizing: border-box; margin: 0; padding: 0; }
    body {
      font-family: -apple-system, BlinkMacSystemFont, "Pretendard", "Apple SD Gothic Neo", "Malgun Gothic", sans-serif;
      background-color: var(--bg);
      color: var(--text-main);
      line-height: 1.65;
      padding: 20px 14px 48px;
      -webkit-font-smoothing: antialiased;
    }
    .container { max-width: 900px; margin: 0 auto; }

    /* 헤더 */
    header { text-align: center; margin-bottom: 22px; }
    header h1 {
      font-size: clamp(1.55rem, 3.5vw, 1.95rem);
      font-weight: 800;
      color: #0f172a;
      letter-spacing: -0.025em;
    }
    header p { color: var(--text-sub); font-size: 0.93rem; margin-top: 5px; }

    /* 상단 모드 전환 탭 */
    .mode-tabs {
      display: flex;
      background: #e2e8f0;
      padding: 4px;
      border-radius: 14px;
      margin-bottom: 20px;
      gap: 4px;
    }
    .tab-btn {
      flex: 1;
      padding: 12px 10px;
      border: none;
      border-radius: 10px;
      font-size: 0.94rem;
      font-weight: 700;
      color: #475569;
      background: transparent;
      cursor: pointer;
      transition: all 0.2s ease;
    }
    .tab-btn.active {
      background: #ffffff;
      color: #0f172a;
      box-shadow: 0 2px 8px rgba(15, 23, 42, 0.08);
    }

    /* 카드 공통 */
    .card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 18px;
      padding: 24px;
      margin-bottom: 18px;
      box-shadow: 0 2px 12px rgba(15, 23, 42, 0.03);
    }
    .section-title {
      font-size: 1.08rem;
      font-weight: 700;
      margin-bottom: 16px;
      color: #0f172a;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 8px;
    }

    /* 입력 폼 */
    .form-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(205px, 1fr));
      gap: 16px;
    }
    .form-group { display: flex; flex-direction: column; gap: 6px; }
    label { font-size: 0.84rem; font-weight: 600; color: #475569; }
    input[type="text"], input[type="date"], input[type="time"] {
      width: 100%;
      padding: 11px 12px;
      border: 1px solid #cbd5e1;
      border-radius: 10px;
      font-size: 0.95rem;
      background: #ffffff;
      color: var(--text-main);
      transition: border-color 0.15s;
    }
    input:focus { outline: none; border-color: #2563eb; }
    input:disabled { background: #f1f5f9; color: #94a3b8; cursor: not-allowed; }
    .inline-options {
      display: flex;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
      margin-top: 3px;
      font-size: 0.86rem;
    }
    .inline-options label {
      display: flex;
      align-items: center;
      gap: 5px;
      font-weight: 500;
      cursor: pointer;
      padding: 2px 0;
    }
    .solar-time-bar {
      margin-top: 14px;
      padding-top: 12px;
      border-top: 1px dashed var(--border);
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 8px;
      font-size: 0.85rem;
      color: #475569;
    }
    .btn-submit {
      width: 100%;
      margin-top: 18px;
      padding: 15px;
      background: #0f172a;
      color: #ffffff;
      border: none;
      border-radius: 12px;
      font-size: 1rem;
      font-weight: 700;
      cursor: pointer;
      transition: background 0.2s, transform 0.1s;
    }
    .btn-submit:hover { background: #1e293b; }
    .btn-submit:active { transform: scale(0.995); }

    /* 궁합 2인 입력 분리 박스 */
    .couple-input-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(310px, 1fr));
      gap: 16px;
    }
    .person-box {
      border: 1px solid var(--border);
      border-radius: 14px;
      padding: 18px;
      background: #f8fafc;
    }
    .person-box h3 {
      font-size: 0.98rem;
      font-weight: 800;
      margin-bottom: 12px;
      color: #0f172a;
    }

    /* 알림 메시지 박스 */
    .toast-msg {
      display: none;
      padding: 12px 16px;
      background: #fef2f2;
      border: 1px solid #fecaca;
      color: #b91c1c;
      border-radius: 10px;
      font-size: 0.88rem;
      font-weight: 600;
      margin-top: 12px;
    }
    .toast-info {
      display: none;
      padding: 11px 15px;
      background: #eff6ff;
      border: 1px solid #bfdbfe;
      color: #1e40af;
      border-radius: 10px;
      font-size: 0.86rem;
      font-weight: 600;
      margin-bottom: 12px;
    }

    /* 액션 툴바 */
    .action-bar {
      display: flex;
      justify-content: flex-end;
      flex-wrap: wrap;
      gap: 8px;
      margin-bottom: 14px;
    }
    .btn-action {
      background: #ffffff;
      color: #0f172a;
      border: 1px solid #cbd5e1;
      padding: 10px 15px;
      border-radius: 10px;
      font-size: 0.85rem;
      font-weight: 700;
      cursor: pointer;
      transition: all 0.15s;
    }
    .btn-action:hover { background: #f1f5f9; }
    .btn-action:disabled { opacity: 0.6; cursor: wait; }
    .btn-primary-pdf {
      background: #0f172a;
      color: #ffffff;
      border-color: #0f172a;
    }
    .btn-primary-pdf:hover { background: #1e293b; }
    .btn-png {
      background: #2563eb;
      color: #ffffff;
      border-color: #2563eb;
    }
    .btn-png:hover { background: #1d4ed8; }

    /* 리포트 공통 */
    .capture-zone { background: var(--bg); padding: 4px; border-radius: 16px; }
    .badge-row { display: flex; flex-wrap: wrap; gap: 8px; margin-bottom: 10px; }
    .badge {
      display: inline-block;
      padding: 4px 11px;
      border-radius: 999px;
      font-size: 0.78rem;
      font-weight: 700;
      background: #f1f5f9;
      color: #334155;
    }
    .badge-animal { background: #eff6ff; color: #1d4ed8; }
    .persona-title {
      font-size: clamp(1.2rem, 3vw, 1.42rem);
      font-weight: 800;
      margin-bottom: 6px;
      color: #0f172a;
      letter-spacing: -0.02em;
    }
    .meta-info { font-size: 0.85rem; color: var(--text-sub); margin-bottom: 16px; }

    /* 컬러 카드 & 라이프스타일 오감 테라피 가이드 */
    .color-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 14px;
      margin-top: 12px;
    }
    .color-box {
      display: flex;
      align-items: center;
      gap: 14px;
      padding: 14px;
      border-radius: 14px;
      border: 1px solid var(--border);
      background: #f8fafc;
    }
    .swatch {
      width: 58px;
      height: 58px;
      border-radius: 12px;
      flex-shrink: 0;
      border: 1px solid rgba(15, 23, 42, 0.12);
      box-shadow: inset 0 2px 4px rgba(255,255,255,0.25);
    }
    .color-info h4 { font-size: 0.79rem; color: var(--text-sub); font-weight: 600; }
    .color-info p { font-size: 1rem; font-weight: 800; color: #0f172a; margin-top: 1px; }
    .color-info span { font-size: 0.8rem; color: #475569; display: block; margin-top: 2px; line-height: 1.4; }

    .therapy-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
      gap: 14px;
      margin-top: 14px;
    }
    .therapy-card {
      padding: 16px 18px;
      border-radius: 14px;
      border: 1px solid var(--border);
      background: #ffffff;
    }
    .therapy-card-header {
      display: flex;
      align-items: center;
      gap: 8px;
      margin-bottom: 10px;
      padding-bottom: 8px;
      border-bottom: 1px solid #f1f5f9;
    }
    .mini-dot {
      width: 14px;
      height: 14px;
      border-radius: 50%;
      border: 1px solid rgba(0,0,0,0.12);
      flex-shrink: 0;
    }
    .therapy-card-header h5 {
      font-size: 0.92rem;
      font-weight: 800;
      color: #0f172a;
    }
    .therapy-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 8px;
      font-size: 0.86rem;
      color: var(--text-body);
    }
    .therapy-list li strong {
      color: #0f172a;
      font-weight: 700;
    }

    /* 사주명식 테이블 */
    .table-wrap { width: 100%; overflow-x: auto; }
    .pillars-table { width: 100%; border-collapse: collapse; text-align: center; table-layout: fixed; min-width: 340px; }
    .pillars-table th {
      background: #f1f5f9;
      padding: 10px 6px;
      font-size: 0.82rem;
      color: #475569;
      border: 1px solid var(--border);
    }
    .pillars-table td {
      padding: 11px 6px;
      border: 1px solid var(--border);
      vertical-align: middle;
    }
    .hanja-char { font-size: 1.85rem; font-weight: 800; display: block; line-height: 1.15; }
    .kor-char { font-size: 0.8rem; font-weight: 600; color: var(--text-sub); }
    .sipseong-tag {
      font-size: 0.78rem;
      font-weight: 700;
      color: #334155;
      background: #f8fafc;
      border: 1px solid #e2e8f0;
      padding: 3px 8px;
      border-radius: 6px;
      display: inline-block;
    }

    .c-목 { color: var(--wood); }
    .c-화 { color: var(--fire); }
    .c-토 { color: var(--earth); }
    .c-금 { color: var(--metal); }
    .c-수 { color: var(--water); }

    /* 대운 & 세운 */
    .daeun-scroll {
      display: grid;
      grid-template-columns: repeat(8, minmax(74px, 1fr));
      gap: 6px;
      text-align: center;
      overflow-x: auto;
      padding-bottom: 4px;
    }
    .daeun-cell {
      border: 1px solid var(--border);
      border-radius: 10px;
      padding: 10px 4px;
      background: #f8fafc;
    }
    .daeun-cell.active-daeun {
      border: 2px solid #2563eb;
      background: #eff6ff;
    }
    .daeun-age { font-size: 0.76rem; font-weight: 700; color: #475569; margin-bottom: 4px; }
    .daeun-ganji { font-size: 1.15rem; font-weight: 800; line-height: 1.25; }
    .daeun-sip { font-size: 0.72rem; color: #64748b; margin-top: 4px; }
    .seun-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(310px, 1fr));
      gap: 14px;
      margin-top: 16px;
    }
    .seun-box {
      padding: 18px;
      border-radius: 14px;
      background: #fffbeb;
      border: 1px solid #fde68a;
      font-size: 0.9rem;
      color: #451a03;
      line-height: 1.65;
    }
    .seun-box.seun-2027 {
      background: #fef2f2;
      border: 1px solid #fecaca;
      color: #450a0a;
    }
    .seun-header {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 6px;
      margin-bottom: 10px;
      padding-bottom: 8px;
      border-bottom: 1px solid rgba(0, 0, 0, 0.08);
    }
    .seun-header h4 { font-size: 1rem; font-weight: 800; }
    .seun-badge {
      font-size: 0.76rem;
      font-weight: 700;
      padding: 3px 9px;
      border-radius: 999px;
      background: rgba(255, 255, 255, 0.85);
    }
    .seun-list {
      list-style: none;
      display: flex;
      flex-direction: column;
      gap: 8px;
    }
    .seun-list li strong { font-weight: 700; }

    /* 최종 종합 요약 카드 */
    .final-summary-card {
      border: 2px solid #0f172a;
      background: linear-gradient(180deg, #ffffff 0%, #f8fafc 100%);
    }
    .summary-kv-table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 12px;
      font-size: 0.89rem;
    }
    .summary-kv-table th, .summary-kv-table td {
      border: 1px solid var(--border);
      padding: 10px 12px;
      text-align: left;
      vertical-align: top;
    }
    .summary-kv-table th {
      width: 26%;
      background: #f1f5f9;
      font-weight: 700;
      color: #0f172a;
    }
    .summary-kv-table td { color: var(--text-body); background: #ffffff; }
    .pdf-cta-bar {
      margin-top: 20px;
      padding: 18px;
      border-radius: 14px;
      background: #f1f5f9;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 12px;
    }
    .pdf-cta-bar p { font-size: 0.9rem; font-weight: 600; color: #0f172a; }

    .brand-watermark {
      text-align: center;
      font-size: 0.78rem;
      font-weight: 600;
      color: var(--text-sub);
      padding: 12px 0 4px;
      letter-spacing: 0.02em;
    }

    /* 오행 막대 그래프 */
    .ohaeng-row { display: flex; align-items: center; gap: 12px; margin-bottom: 10px; }
    .ohaeng-label { width: 68px; font-size: 0.88rem; font-weight: 700; }
    .bar-bg { flex: 1; height: 14px; background: #f1f5f9; border-radius: 999px; overflow: hidden; }
    .bar-fill { height: 100%; border-radius: 999px; transition: width 0.5s ease; }
    .ohaeng-pct { width: 52px; text-align: right; font-size: 0.85rem; font-weight: 700; }
    .ohaeng-summary-box {
      margin-top: 14px;
      padding: 13px 16px;
      background: #f8fafc;
      border-radius: 10px;
      font-size: 0.9rem;
      border-left: 4px solid #0f172a;
      color: var(--text-body);
    }

    /* 10대 상세 분석 */
    .analysis-grid { display: grid; grid-template-columns: 1fr; gap: 12px; }
    .analysis-item {
      padding: 18px;
      border: 1px solid var(--border);
      border-radius: 14px;
      background: #ffffff;
    }
    .analysis-item h3 { font-size: 0.98rem; font-weight: 700; color: #0f172a; margin-bottom: 7px; }
    .analysis-item p { font-size: 0.92rem; color: var(--text-body); white-space: pre-line; }

    /* 궁합 결과 전용 스타일 */
    .score-hero {
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-wrap: wrap;
      gap: 16px;
      padding: 20px;
      background: linear-gradient(135deg, #f8fafc 0%, #eff6ff 100%);
      border-radius: 14px;
      border: 1px solid #dbeafe;
      margin-bottom: 16px;
    }
    .score-circle {
      width: 96px;
      height: 96px;
      border-radius: 50%;
      background: #0f172a;
      color: #ffffff;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: center;
      flex-shrink: 0;
      box-shadow: 0 6px 16px rgba(15, 23, 42, 0.16);
    }
    .score-num { font-size: 1.75rem; font-weight: 800; line-height: 1; }
    .score-unit { font-size: 0.74rem; opacity: 0.85; margin-top: 3px; }
    .sub-scores {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(190px, 1fr));
      gap: 12px;
      margin-bottom: 16px;
    }
    .sub-score-card {
      padding: 14px;
      border: 1px solid var(--border);
      border-radius: 12px;
      background: #ffffff;
      text-align: center;
    }
    .sub-score-card h4 { font-size: 0.81rem; color: var(--text-sub); }
    .sub-score-card .val { font-size: 1.28rem; font-weight: 800; color: #0f172a; margin: 4px 0; }
    .sub-score-card span { font-size: 0.78rem; color: #2563eb; font-weight: 600; }

    @media print {
      .mode-tabs, #single-input-card, #compat-input-card, .action-bar, .pdf-cta-bar, .toast-info { display: none !important; }
      body { background: #ffffff !important; padding: 0 !important; -webkit-print-color-adjust: exact; print-color-adjust: exact; }
      .container { max-width: 100% !important; margin: 0 !important; }
      .capture-zone { background: #ffffff !important; padding: 0 !important; }
      .card, .analysis-item, .seun-box, .color-box, .therapy-card, .score-hero {
        box-shadow: none !important;
        break-inside: avoid;
        page-break-inside: avoid;
        -webkit-print-color-adjust: exact;
        print-color-adjust: exact;
      }
      .daeun-scroll, .table-wrap { overflow: visible !important; }
    }
  </style>
</head>
<body>

<div class="container">
  <header>
    <h1>사주&amp;컬러코드</h1>
    <p>정통 만세력 4기둥과 나만의 기질 컬러로 읽어내는 인생 설계 &amp; 시너지 리포트</p>
  </header>

  <!-- 상단 모드 전환 탭 -->
  <div class="mode-tabs">
    <button class="tab-btn active" id="tab-single" onclick="switchTab('single')">개인 사주 &amp; 기질 컬러 분석</button>
    <button class="tab-btn" id="tab-compat" onclick="switchTab('compat')">두 사람 궁합 &amp; 컬러 시너지</button>
  </div>

  <!-- =====================================================================
       [탭 1] 개인 사주 & 기질 컬러 분석
       ===================================================================== -->
  <div id="view-single">
    <div class="card" id="single-input-card">
      <div class="section-title">출생 정보 입력</div>
      <div class="form-grid">
        <div class="form-group">
          <label for="userName">이름</label>
          <input type="text" id="userName" placeholder="예: 김지민" value="김지민" />
        </div>
        <div class="form-group">
          <label>성별 (대운 순·역행 기준)</label>
          <div class="inline-options" style="padding-top: 6px;">
            <label><input type="radio" name="gender" value="여" checked /> 여성</label>
            <label><input type="radio" name="gender" value="남" /> 남성</label>
          </div>
        </div>
        <div class="form-group">
          <label for="birthDate">생년월일</label>
          <input type="date" id="birthDate" value="1992-08-14" />
          <div class="inline-options">
            <label><input type="radio" name="calType" value="solar" checked onchange="toggleLeap('calType', 'leapLabel', 'isLeap')" /> 양력</label>
            <label><input type="radio" name="calType" value="lunar" onchange="toggleLeap('calType', 'leapLabel', 'isLeap')" /> 음력</label>
            <label id="leapLabel" style="display:none; color:#2563eb;"><input type="checkbox" id="isLeap" /> 윤달</label>
          </div>
        </div>
        <div class="form-group">
          <label for="birthTime">태어난 시간</label>
          <input type="time" id="birthTime" value="10:30" />
          <div class="inline-options">
            <label><input type="checkbox" id="unknownTime" onchange="toggleTime('unknownTime', 'birthTime')" /> 시간 모름 (삼주 분석)</label>
          </div>
        </div>
      </div>

      <div class="solar-time-bar">
        <label style="display:flex; align-items:center; gap:6px; cursor:pointer;">
          <input type="checkbox" id="useTrueSolarSingle" checked /> 진태양시 보정 (-30분 적용 · 한국 표준시 경도 보정)
        </label>
        <span>1900~2100년 내장 천문 절입일 정밀 계산</span>
      </div>

      <div id="singleErrorMsg" class="toast-msg"></div>
      <button class="btn-submit" onclick="runSingleAnalysis(true)">내 사주명식 &amp; 기질 컬러 분석하기</button>
    </div>

    <div id="single-report-area" style="display:none;">
      <div class="action-bar">
        <button class="btn-action" id="printBtnSingle" onclick="safePrintReport('single-capture', 'singleInfoMsg')">리포트 인쇄</button>
        <button class="btn-action btn-png" id="pngBtnSingle" onclick="downloadNativePNG('single-capture', 'pngBtnSingle', 'singleInfoMsg')">고화질 PNG 저장</button>
        <button class="btn-action btn-primary-pdf" id="pdfBtnSingle" onclick="downloadNativePDF('single-capture', 'pdfBtnSingle', 'singleInfoMsg')">PDF 파일 다운로드</button>
      </div>
      <div id="singleInfoMsg" class="toast-info"></div>

      <div id="single-capture" class="capture-zone">
        <!-- 종합 요약 & 기질 컬러 + 오감 테라피 가이드 -->
        <div class="card">
          <div class="badge-row">
            <span class="badge" id="hashBadge">명식 코드</span>
            <span class="badge badge-animal" id="animalBadge">60갑자 물상</span>
          </div>
          <div class="persona-title" id="personaTitle">분석 결과 타이틀</div>
          <div class="meta-info" id="metaInfo">기준 정보</div>
          <p id="overallSummary" style="font-size: 0.95rem; color: #1e293b; margin-bottom: 16px;"></p>

          <div class="color-grid">
            <div class="color-box">
              <div class="swatch" id="tempSwatch"></div>
              <div class="color-info">
                <h4>타고난 본질 컬러 (일간 기준)</h4>
                <p id="tempColorName">-</p>
                <span id="tempColorKeyword">-</span>
              </div>
            </div>
            <div class="color-box">
              <div class="swatch" id="balSwatch"></div>
              <div class="color-info">
                <h4>에너지 보완 컬러 (개운 컬러)</h4>
                <p id="balColorName">-</p>
                <span id="balColorDesc">-</span>
              </div>
            </div>
          </div>

          <!-- 패션·공간·아로마 오감 테라피 가이드 -->
          <div class="therapy-grid" id="therapyGuideGrid"></div>
        </div>

        <!-- 사주명식 4기둥 -->
        <div class="card">
          <div class="section-title">사주명식 (四柱命式 · 4개의 기둥)</div>
          <div class="table-wrap">
            <table class="pillars-table">
              <thead>
                <tr>
                  <th>구분</th>
                  <th>시주 (말년·자녀)</th>
                  <th>일주 (나·배우자)</th>
                  <th>월주 (청년·사회)</th>
                  <th>년주 (초년·조상)</th>
                </tr>
              </thead>
              <tbody id="pillarsBody"></tbody>
            </table>
          </div>
        </div>

        <!-- 10년 대운 및 2026~2027 세운 -->
        <div class="card">
          <div class="section-title">
            <span>10년 대운(大運) 흐름 및 2026 병오년 · 2027 정미년 세운 심층 분석</span>
            <span id="daeunDirectionBadge" style="font-size:0.82rem; color:#2563eb; font-weight:700;"></span>
          </div>
          <div class="daeun-scroll" id="daeunTimeline"></div>
          <div class="seun-grid">
            <div class="seun-box" id="seun2026Box"></div>
            <div class="seun-box seun-2027" id="seun2027Box"></div>
          </div>
        </div>

        <!-- 오행 분포 -->
        <div class="card">
          <div class="section-title">오행(五行) 에너지 분포 및 과다·부족 분석</div>
          <div id="ohaengBars"></div>
          <div class="ohaeng-summary-box" id="ohaengSummaryText"></div>
        </div>

        <!-- 10대 상세 분석 -->
        <div class="card">
          <div class="section-title">심층 기질 및 운세 종합 리포트 (10대 핵심 영역)</div>
          <div class="analysis-grid" id="detailGrid"></div>
        </div>

        <!-- 최종 종합 요약 리포트 (One-Page Summary) -->
        <div class="card final-summary-card" id="finalSummarySection">
          <div class="section-title">
            <span>최종 종합 정리 (One-Page Summary)</span>
            <span class="badge badge-animal" id="finalSummaryBadge">핵심 마스터 시트</span>
          </div>
          <p id="finalSummaryLead" style="font-size:0.93rem; color:#1e293b; margin-bottom:10px;"></p>
          <table class="summary-kv-table">
            <tbody id="finalSummaryTableBody"></tbody>
          </table>
        </div>

        <div class="brand-watermark">사주&amp;컬러코드 (SAJU &amp; COLOR CODE) · 정통 만세력 &amp; 기질 컬러 분석 리포트</div>
      </div>

      <div class="pdf-cta-bar">
        <p>사주&amp;컬러코드 전체 분석 리포트와 최종 종합 정리를 소장용 PDF 문서로 저장하세요.</p>
        <div style="display:flex; gap:8px; flex-wrap:wrap;">
          <button class="btn-action" onclick="safePrintReport('single-capture', 'singleInfoMsg')">리포트 인쇄</button>
          <button class="btn-action btn-primary-pdf" id="pdfBtnSingleBottom" onclick="downloadNativePDF('single-capture', 'pdfBtnSingleBottom', 'singleInfoMsg')">PDF 파일 다운로드</button>
        </div>
      </div>
    </div>
  </div>

  <!-- =====================================================================
       [탭 2] 두 사람 궁합 & 컬러 시너지
       ===================================================================== -->
  <div id="view-compat" style="display:none;">
    <div class="card" id="compat-input-card">
      <div class="section-title">두 사람의 출생 정보 입력</div>
      <div class="couple-input-grid">
        <div class="person-box">
          <h3>첫 번째 사람 (나)</h3>
          <div class="form-grid">
            <div class="form-group">
              <label>이름</label>
              <input type="text" id="p1Name" value="김지민" />
            </div>
            <div class="form-group">
              <label>성별</label>
              <div class="inline-options" style="padding-top:6px;">
                <label><input type="radio" name="p1Gender" value="여" checked /> 여성</label>
                <label><input type="radio" name="p1Gender" value="남" /> 남성</label>
              </div>
            </div>
            <div class="form-group">
              <label>생년월일</label>
              <input type="date" id="p1Date" value="1992-08-14" />
              <div class="inline-options">
                <label><input type="radio" name="p1Cal" value="solar" checked onchange="toggleLeap('p1Cal', 'p1LeapLbl', 'p1Leap')" /> 양력</label>
                <label><input type="radio" name="p1Cal" value="lunar" onchange="toggleLeap('p1Cal', 'p1LeapLbl', 'p1Leap')" /> 음력</label>
                <label id="p1LeapLbl" style="display:none; color:#2563eb;"><input type="checkbox" id="p1Leap" /> 윤달</label>
              </div>
            </div>
            <div class="form-group">
              <label>태어난 시간</label>
              <input type="time" id="p1Time" value="10:30" />
              <div class="inline-options">
                <label><input type="checkbox" id="p1Unknown" onchange="toggleTime('p1Unknown', 'p1Time')" /> 시간 모름</label>
              </div>
            </div>
          </div>
        </div>

        <div class="person-box">
          <h3>두 번째 사람 (상대방)</h3>
          <div class="form-grid">
            <div class="form-group">
              <label>이름</label>
              <input type="text" id="p2Name" value="이현우" />
            </div>
            <div class="form-group">
              <label>성별</label>
              <div class="inline-options" style="padding-top:6px;">
                <label><input type="radio" name="p2Gender" value="여" /> 여성</label>
                <label><input type="radio" name="p2Gender" value="남" checked /> 남성</label>
              </div>
            </div>
            <div class="form-group">
              <label>생년월일</label>
              <input type="date" id="p2Date" value="1990-03-22" />
              <div class="inline-options">
                <label><input type="radio" name="p2Cal" value="solar" checked onchange="toggleLeap('p2Cal', 'p2LeapLbl', 'p2Leap')" /> 양력</label>
                <label><input type="radio" name="p2Cal" value="lunar" onchange="toggleLeap('p2Cal', 'p2LeapLbl', 'p2Leap')" /> 음력</label>
                <label id="p2LeapLbl" style="display:none; color:#2563eb;"><input type="checkbox" id="p2Leap" /> 윤달</label>
              </div>
            </div>
            <div class="form-group">
              <label>태어난 시간</label>
              <input type="time" id="p2Time" value="15:20" />
              <div class="inline-options">
                <label><input type="checkbox" id="p2Unknown" onchange="toggleTime('p2Unknown', 'p2Time')" /> 시간 모름</label>
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="solar-time-bar">
        <label style="display:flex; align-items:center; gap:6px; cursor:pointer;">
          <input type="checkbox" id="useTrueSolarCompat" checked /> 진태양시 보정 (-30분 적용)
        </label>
        <span>일간 천간합 · 일지 육합/삼합/충 · 오행 용신 상호 보완 분석</span>
      </div>

      <div id="compatErrorMsg" class="toast-msg"></div>
      <button class="btn-submit" onclick="runCompatAnalysis(true)">두 사람 궁합 점수 &amp; 컬러 시너지 분석하기</button>
    </div>

    <div id="compat-report-area" style="display:none;">
      <div class="action-bar">
        <button class="btn-action" onclick="safePrintReport('compat-capture', 'compatInfoMsg')">궁합 리포트 인쇄</button>
        <button class="btn-action btn-png" id="pngBtnCompat" onclick="downloadNativePNG('compat-capture', 'pngBtnCompat', 'compatInfoMsg')">고화질 PNG 저장</button>
        <button class="btn-action btn-primary-pdf" id="pdfBtnCompat" onclick="downloadNativePDF('compat-capture', 'pdfBtnCompat', 'compatInfoMsg')">궁합 PDF 다운로드</button>
      </div>
      <div id="compatInfoMsg" class="toast-info"></div>

      <div id="compat-capture" class="capture-zone">
        <div class="card">
          <div class="score-hero">
            <div style="flex:1; min-width: 240px;">
              <span class="badge badge-animal" id="compatPairBadge">일주 조합</span>
              <div class="persona-title" id="compatHeadline" style="margin-top:6px;">두 사람의 궁합 요약</div>
              <p id="compatSubSummary" style="font-size:0.92rem; color:#334155;"></p>
            </div>
            <div class="score-circle">
              <span class="score-num" id="totalCompatScore">0</span>
              <span class="score-unit">종합 시너지</span>
            </div>
          </div>

          <div class="sub-scores">
            <div class="sub-score-card">
              <h4>1. 일간 천간합 (정신·가치관)</h4>
              <div class="val" id="ganScoreVal">-</div>
              <span id="ganRelLabel">-</span>
            </div>
            <div class="sub-score-card">
              <h4>2. 일지 지지합 (속마음·현실)</h4>
              <div class="val" id="jiScoreVal">-</div>
              <span id="jiRelLabel">-</span>
            </div>
            <div class="sub-score-card">
              <h4>3. 오행 상호 보완 (에너지 균형)</h4>
              <div class="val" id="ohScoreVal">-</div>
              <span id="ohRelLabel">-</span>
            </div>
          </div>

          <div class="color-grid">
            <div class="color-box">
              <div class="swatch" id="cSwatch1"></div>
              <div class="color-info">
                <h4 id="cTitle1">첫 번째 사람 본질 컬러</h4>
                <p id="cName1">-</p>
                <span id="cDesc1">-</span>
              </div>
            </div>
            <div class="color-box">
              <div class="swatch" id="cSwatch2"></div>
              <div class="color-info">
                <h4 id="cTitle2">두 번째 사람 본질 컬러</h4>
                <p id="cName2">-</p>
                <span id="cDesc2">-</span>
              </div>
            </div>
          </div>
        </div>

        <div class="card">
          <div class="section-title">두 사람 사주명식 핵심 대조</div>
          <div class="table-wrap">
            <table class="pillars-table">
              <thead>
                <tr>
                  <th>구분</th>
                  <th id="thP1">첫 번째 사람</th>
                  <th id="thP2">두 번째 사람</th>
                </tr>
              </thead>
              <tbody id="compatCompareBody"></tbody>
            </table>
          </div>
        </div>

        <div class="card">
          <div class="section-title">심층 관계 및 시너지 코칭 리포트</div>
          <div class="analysis-grid" id="compatDetailGrid"></div>
        </div>

        <div class="card final-summary-card">
          <div class="section-title">
            <span>두 사람 궁합 &amp; 시너지 최종 종합 정리</span>
            <span class="badge badge-animal" id="compatFinalBadge">커플·파트너 마스터 시트</span>
          </div>
          <table class="summary-kv-table">
            <tbody id="compatFinalSummaryBody"></tbody>
          </table>
        </div>

        <div class="brand-watermark">사주&amp;컬러코드 (SAJU &amp; COLOR CODE) · 두 사람 궁합 &amp; 컬러 시너지 리포트</div>
      </div>

      <div class="pdf-cta-bar">
        <p>사주&amp;컬러코드 두 사람의 궁합 점수 및 시너지 코칭 리포트를 PDF로 소장하세요.</p>
        <div style="display:flex; gap:8px; flex-wrap:wrap;">
          <button class="btn-action" onclick="safePrintReport('compat-capture', 'compatInfoMsg')">궁합 리포트 인쇄</button>
          <button class="btn-action btn-primary-pdf" id="pdfBtnCompatBottom" onclick="downloadNativePDF('compat-capture', 'pdfBtnCompatBottom', 'compatInfoMsg')">궁합 PDF 다운로드</button>
        </div>
      </div>
    </div>
  </div>
</div>

<script>
// ============================================================================
// [A] 완전 내장형 한국 음양력 변환 엔진 (1900~2100년)
// ============================================================================
const LUNAR_INFO = [
  0x04bd8,0x04ae0,0x0a570,0x054d5,0x0d260,0x0d950,0x16554,0x056a0,0x09ad0,0x055d2,
  0x04ae0,0x0a5b6,0x0a4d0,0x0d250,0x1d255,0x0b540,0x0d6a0,0x0ada2,0x095b0,0x14977,
  0x04970,0x0a4b0,0x0b4b5,0x06a50,0x06d40,0x1ab54,0x02b60,0x09570,0x052f2,0x04970,
  0x06566,0x0d4a0,0x0ea50,0x06e95,0x05ad0,0x02b60,0x186e3,0x092e0,0x1c8d7,0x0c950,
  0x0d4a0,0x1d8a6,0x0b550,0x056a0,0x1a5b4,0x025d0,0x092d0,0x0d2b2,0x0a950,0x0b557,
  0x06ca0,0x0b550,0x15355,0x04da0,0x0a5b0,0x14573,0x052b0,0x0a9a8,0x0e950,0x06aa0,
  0x0aea6,0x0ab50,0x04b60,0x0aae4,0x0a570,0x05260,0x0f263,0x0d950,0x05b57,0x056a0,
  0x096d0,0x04dd5,0x04ad0,0x0a4d0,0x0d4d4,0x0d250,0x0d558,0x0b540,0x0b6a0,0x195a6,
  0x095b0,0x049b0,0x0a974,0x0a4b0,0x0b27a,0x06a50,0x06d40,0x0af46,0x0ab60,0x09570,
  0x04af5,0x04970,0x064b0,0x074a3,0x0ea50,0x06b58,0x05ac0,0x0ab60,0x096d5,0x092e0,
  0x0c960,0x0d954,0x0d4a0,0x0da50,0x07552,0x056a0,0x0abb7,0x025d0,0x092d0,0x0cab5,
  0x0a950,0x0b4a0,0x0baa4,0x0ad50,0x055d9,0x04ba0,0x0a5b0,0x15176,0x052b0,0x0a930,
  0x07954,0x06aa0,0x0ad50,0x05b52,0x04b60,0x0a6e6,0x0a4e0,0x0d260,0x0ea65,0x0d530,
  0x05aa0,0x076a3,0x096d0,0x04afb,0x04ad0,0x0a4d0,0x1d0b6,0x0d250,0x0d520,0x0dd45,
  0x0b5a0,0x056d0,0x055b2,0x049b0,0x0a577,0x0a4b0,0x0aa50,0x1b255,0x06d20,0x0ada0,
  0x14b63,0x09370,0x049f8,0x04970,0x064b0,0x168a6,0x0ea50,0x06b20,0x1a6c4,0x0aae0,
  0x092e0,0x0d2e3,0x0c960,0x0d557,0x0d4a0,0x0da50,0x05d55,0x056a0,0x0a6d0,0x055d4,
  0x052d0,0x0a9b8,0x0a950,0x0b4a0,0x0b6a6,0x0ad50,0x055a0,0x0aba4,0x0a5b0,0x052b0,
  0x0b273,0x06930,0x07337,0x06aa0,0x0ad50,0x14b55,0x04b60,0x0a570,0x054e4,0x0d160,
  0x0e968,0x0d520,0x0daa0,0x16aa6,0x056d0,0x04ae0,0x0a9d4,0x0a2d0,0x0d150,0x0f252,
  0x0d520
];

function getLunarLeapMonth(y) { return LUNAR_INFO[y - 1900] & 0xf; }
function getLunarLeapDays(y) {
  if (getLunarLeapMonth(y)) return (LUNAR_INFO[y - 1900] & 0x10000) ? 30 : 29;
  return 0;
}
function getLunarMonthDays(y, m) { return (LUNAR_INFO[y - 1900] & (0x10000 >> m)) ? 30 : 29; }
function getLunarYearDays(y) {
  let sum = 348;
  for (let i = 0x8000; i > 0x8; i >>= 1) sum += (LUNAR_INFO[y - 1900] & i) ? 1 : 0;
  return sum + getLunarLeapDays(y);
}

function convertLunarToSolar(lYear, lMonth, lDay, isLeap) {
  if (lYear < 1900 || lYear > 2100 || lMonth < 1 || lMonth > 12 || lDay < 1 || lDay > 30) return null;
  const leapMonth = getLunarLeapMonth(lYear);
  if (isLeap && leapMonth !== lMonth) return null;
  const maxDays = isLeap ? getLunarLeapDays(lYear) : getLunarMonthDays(lYear, lMonth);
  if (lDay > maxDays) return null;

  let offset = 0;
  for (let i = 1900; i < lYear; i++) offset += getLunarYearDays(i);
  for (let m = 1; m < lMonth; m++) {
    offset += getLunarMonthDays(lYear, m);
    if (leapMonth > 0 && leapMonth === m) offset += getLunarLeapDays(lYear);
  }
  if (isLeap) offset += getLunarMonthDays(lYear, lMonth);
  offset += (lDay - 1);

  const baseUTC = Date.UTC(1900, 0, 31);
  const resDate = new Date(baseUTC + offset * 24 * 60 * 60 * 1000);
  return {
    year: resDate.getUTCFullYear(),
    month: resDate.getUTCMonth() + 1,
    day: resDate.getUTCDate()
  };
}

// ============================================================================
// [B] 천문 태양 황경(24절기) 정밀 계산 엔진
// ============================================================================
function getSolarLongitudeKST(dateObjKST) {
  const utcMs = dateObjKST.getTime() - 9 * 60 * 60 * 1000;
  const jd = utcMs / 86400000.0 + 2440587.5;
  const T = (jd - 2451545.0) / 36525.0;

  let L0 = 280.46646 + 36000.76983 * T + 0.0003032 * T * T;
  let M = 357.52911 + 35999.05029 * T - 0.0001537 * T * T;
  const Mrad = (M * Math.PI) / 180.0;

  const C =
    (1.914602 - 0.004817 * T - 0.000014 * T * T) * Math.sin(Mrad) +
    (0.019993 - 0.000101 * T) * Math.sin(2 * Mrad) +
    0.000289 * Math.sin(3 * Mrad);

  const trueLon = L0 + C;
  const omega = 125.04 - 1934.136 * T;
  const appLon = trueLon - 0.00569 - 0.00478 * Math.sin((omega * Math.PI) / 180.0);

  return ((appLon % 360) + 360) % 360;
}

// ============================================================================
// [C] 명리 기초 상수 및 10대 본질 컬러 · 5대 개운 컬러 오감 테라피 DB
// ============================================================================
const CHEONGAN = ["갑", "을", "병", "정", "무", "기", "경", "신", "임", "계"];
const CHEONGAN_HANJA = ["甲", "乙", "丙", "丁", "戊", "己", "庚", "辛", "壬", "癸"];
const JIJI = ["자", "축", "인", "묘", "진", "사", "오", "미", "신", "유", "술", "해"];
const JIJI_HANJA = ["子", "丑", "寅", "卯", "辰", "巳", "午", "未", "申", "酉", "戌", "亥"];

const GAN_OHAENG = ["목", "목", "화", "화", "토", "토", "금", "금", "수", "수"];
const GAN_YINYANG = [1, 0, 1, 0, 1, 0, 1, 0, 1, 0];
const JI_OHAENG = ["수", "토", "목", "목", "토", "화", "화", "토", "금", "금", "토", "수"];
const JI_MAIN_GAN = [9, 5, 0, 1, 4, 2, 3, 5, 6, 7, 4, 8];

const GAN_COLOR_PREFIX = ["푸른", "푸른", "붉은", "붉은", "황금", "황금", "하얀", "하얀", "검은", "검은"];
const JI_ANIMAL_NAME = ["쥐", "소", "호랑이", "토끼", "용", "뱀", "말", "양", "원숭이", "닭", "개", "돼지"];

const TWELVE_UNSEONG_NAMES = ["장생", "목욕", "관대", "건록", "제왕", "쇠", "병", "사", "묘", "절", "태", "양"];
const JANGSAENG_JI = [11, 6, 2, 9, 2, 9, 5, 0, 8, 3];

const TEMPERAMENT_COLORS = {
  "갑": {
    name: "딥 포레스트 그린",
    hex: "#1B4D3E",
    keyword: "개척 · 직진 · 성장의 리더십",
    persona: "거침없이 뻗어 올라가는 푸른 거목",
    fashion: "구조적인 테일러드 재킷이나 딥 그린 니트·스카프 포인트, 세로 스트라이프 셔츠로 단단한 리더십과 신뢰감을 극대화하세요.",
    interior: "천연 원목 가구와 잎이 큰 관엽식물(몬스테라·여인초)을 업무 공간 좌측에 배치하면 기획력과 직관적 추진력이 살아납니다.",
    aroma: "시더우드 · 파인 니들 · 로즈마리 (울창한 숲속을 걷는 듯한 우디 허브 노트가 머리의 열기를 식히고 결단력을 높여줍니다.)"
  },
  "을": {
    name: "파스텔 민트 그린",
    hex: "#68B984",
    keyword: "유연 · 적응 · 끈질긴 생명력",
    persona: "바람에도 꺾이지 않고 피어나는 들꽃",
    fashion: "부드럽게 흐르는 실크·린넨 블라우스, 민트·세이지 그린 카디건에 곡선형 실버 주얼리를 매치하면 특유의 친화력이 빛납니다.",
    interior: "라탄·패브릭 소재의 라운드 테이블과 창가의 행잉 플랜트, 은은한 간접 조명으로 부드럽고 창의적인 소통 공간을 연출하세요.",
    aroma: "버가못 · 페퍼민트 · 네롤리 (상쾌한 시트러스와 허브 노트가 눈치와 긴장으로 지친 신경을 이완하고 유연한 영감을 불어넣습니다.)"
  },
  "병": {
    name: "선셋 오렌지",
    hex: "#FF6B35",
    keyword: "열정 · 확산 · 밝은 에너지",
    persona: "세상을 환하게 비추는 한낮의 태양",
    fashion: "생동감 있는 테라코타·오렌지 포인트 백이나 넥타이, 화사한 아이보리 톤 상의로 카리스마와 밝은 에너지를 돋보이게 하세요.",
    interior: "채광이 잘 드는 거실에 따뜻한 2700K 전구색 스탠드 조명과 기하학 패턴의 아트 포스터를 두면 긍정 에너지가 확산됩니다.",
    aroma: "스위트 오렌지 · 시나몬 · 프랑킨센스 (태양의 온기를 담은 시트러스 스파이시 노트가 표현력과 무대 위 존재감을 극대화합니다.)"
  },
  "정": {
    name: "코랄 버건디",
    hex: "#C83E4D",
    keyword: "섬세 · 집중 · 따뜻한 통찰",
    persona: "어둠 속에서 길을 밝히는 은은한 촛불",
    fashion: "벨벳·캐시미어 소재의 코랄 핑크나 딥 버건디 포인트, 섬세한 디테일이 살아있는 시계·안경테가 지적인 매력을 배가합니다.",
    interior: "서재나 침실 한켠에 아로마 캔들, 무드 램프, 짙은 우드 책장을 배치해 오롯이 나에게 몰입할 수 있는 아지트를 만드세요.",
    aroma: "다마스크 로즈 · 샌달우드 · 일랑일랑 (깊고 관능적인 플로럴 우디 노트가 예민해진 감수성을 다독이고 내면의 집중력을 높입니다.)"
  },
  "무": {
    name: "웜 테라코타",
    hex: "#C68B59",
    keyword: "포용 · 신뢰 · 묵직한 중심",
    persona: "변함없이 자리를 지키는 웅장한 태산",
    fashion: "카멜·테라코타 트렌치코트, 스웨이드 로퍼, 묵직한 가죽 브리프케이스 등 클래식하고 안정감 있는 톤온톤 스타일링이 최적입니다.",
    interior: "도자기 오브제, 테라코타 화분, 묵직한 패브릭 소파와 러그를 거실 중앙에 배치하면 가정과 일터의 중심운이 단단해집니다.",
    aroma: "베티버 · 패출리 · 시더우드 (대지의 뿌리를 닮은 얼시(Earthy) 우디 노트가 흔들리지 않는 평정심과 묵직한 신뢰감을 지켜줍니다.)"
  },
  "기": {
    name: "샌드 머스타드",
    hex: "#E0B44A",
    keyword: "실속 · 배려 · 다재다능함",
    persona: "만물을 길러내는 비옥한 대지",
    fashion: "따뜻한 샌드 베이지·머스타드 니트 베스트, 실용적인 포켓 디테일 재킷, 오가닉 코튼 소재로 온화하고 유능한 인상을 완성하세요.",
    interior: "주방과 다이닝 공간을 깔끔하게 정돈하고 옐로우·크림 톤 식기나 리넨 커튼을 활용하면 재물과 인복이 자연스럽게 모입니다.",
    aroma: "카모마일 · 만다린 · 클라리세이지 (포근하고 달콤한 허브 노트가 타인을 배려하느라 소진된 에너지를 따뜻하게 충전해 줍니다.)"
  },
  "경": {
    name: "퓨어 실버 화이트",
    hex: "#CBD5E1",
    keyword: "결단 · 원칙 · 강직한 추진력",
    persona: "단단하게 제련된 원석과 강철",
    fashion: "각이 살아있는 크리습 화이트 셔츠, 차콜·실버 그레이 수트, 메탈 스트랩 시계로 군더더기 없는 프로페셔널함을 강조하세요.",
    interior: "불필요한 잡동사니를 비운 미니멀 인테리어에 스테인리스·유리·대리석 소재의 데스크 소품을 두면 결단력과 실행력이 날카로워집니다.",
    aroma: "유칼립투스 · 주니퍼베리 · 사이프러스 (청량하고 선명한 상록수 노트가 복잡한 고민을 단칼에 정리하고 명쾌한 판단을 돕습니다.)"
  },
  "신": {
    name: "아이스 펄 블루",
    hex: "#A5D8FF",
    keyword: "예리함 · 세련됨 · 완벽주의",
    persona: "맑고 투명하게 빛나는 보석",
    fashion: "아이스 블루·펄 화이트 셔츠, 미세한 광택이 도는 울 슬랙스, 심플한 플래티넘·진주 액세서리가 고유의 품위와 세련미를 살립니다.",
    interior: "화이트 톤 벽면에 크리스탈·실버 프레임 거울과 정돈된 수납함을 배치해 시야를 맑고 투명하게 유지하는 것이 핵심입니다.",
    aroma: "화이트 티 · 네롤리 · 레몬 버베나 (맑고 투명한 시트러스 티 노트가 완벽주의로 인한 긴장을 녹이고 섬세한 직관을 깨워줍니다.)"
  },
  "임": {
    name: "미드나잇 네이비",
    hex: "#1E3A8A",
    keyword: "지혜 · 유연성 · 넓은 스케일",
    persona: "모든 것을 품고 흐르는 깊은 바다",
    fashion: "깊이감 있는 미드나잇 네이비 코트, 여유로운 와이드 핏 팬츠, 유려하게 흐르는 트렌치 스타일로 지적인 카리스마를 연출하세요.",
    interior: "서재나 침실에 딥 블루·네이비 침구나 커튼을 사용하고, 작은 수반이나 가습기로 수분감을 유지하면 지혜와 재물 흐름이 트입니다.",
    aroma: "블랙페퍼 · 프랑킨센스 · 마린 미스트 (깊고 신비로운 발삼·스파이시 노트가 방대한 아이디어를 하나로 응집시키는 통찰력을 줍니다.)"
  },
  "계": {
    name: "미스티 라벤더",
    hex: "#9B89B3",
    keyword: "직관 · 감수성 · 스며드는 치유",
    persona: "대지를 적시는 고요한 봄비와 샘물",
    fashion: "은은한 라벤더·더스티 블루 니트, 부드러운 모달·캐시미어 머플러, 투명한 원석 주얼리로 섬세하고 감각적인 아우라를 표현하세요.",
    interior: "침실 조도를 낮추고 라벤더·그레이 톤의 포근한 패브릭과 아로마 디퓨저를 배치하면 수면의 질과 직관적 영감이 높아집니다.",
    aroma: "트루 라벤더 · 클라리세이지 · 벤조인 (고요하고 포근한 플로럴 발삼 노트가 감정의 파도를 잠재우고 깊은 숙면과 치유를 선사합니다.)"
  }
};

const BALANCE_COLORS = {
  "목": {
    name: "보태니컬 그린",
    hex: "#2E8B57",
    desc: "새로운 시작과 추진력, 창의적 에너지를 채워줍니다.",
    fashion: "그린 계열 양말·머플러·카드지갑이나 식물 패턴 스카프를 착용해 정체된 일상에 새로운 돌파구와 기획 에너지를 불어넣으세요.",
    interior: "현관이나 책상 위에 싱그러운 수경재배 식물이나 초록색 데스크 매트를 두면 막혀 있던 시작운과 학업·사업운이 열립니다.",
    aroma: "로즈마리 · 페퍼민트 · 버가못 (청량한 그린 허브 향기가 무기력함을 깨우고 새로운 도전을 실행할 생기를 채워줍니다.)"
  },
  "화": {
    name: "테라 로즈 레드",
    hex: "#E05252",
    desc: "표현력과 열정, 사회적 활기를 끌어올려 줍니다.",
    fashion: "버건디·로즈 레드 립 포인트, 붉은 스티치 가죽 소품이나 웜톤 액세서리를 매치하면 대인관계 호감도와 발표·영업운이 상승합니다.",
    interior: "남쪽 방향이나 거실에 따뜻한 캔들 워머, 붉은빛이 감도는 쿠션·아트워크를 배치해 식어 있던 열정과 활기를 점화하세요.",
    aroma: "스위트 오렌지 · 제라늄 · 시나몬 (따뜻하고 생동감 넘치는 향기가 내면의 위축감을 걷어내고 자신감 있는 표현력을 끌어냅니다.)"
  },
  "토": {
    name: "크림 베이지 & 옐로우",
    hex: "#E6C773",
    desc: "마음의 안정감과 중심을 잡고 실행력을 높여줍니다.",
    fashion: "크림 베이지·오트밀 니트, 옐로우 골드 주얼리, 단단한 스퀘어 쉐입 가방을 활용해 흔들리는 마음을 잡고 신뢰감을 높이세요.",
    interior: "거실 중앙에 베이지 톤 러그나 도자기 화병을 두고 조명을 따뜻하게 맞추면 불안감이 줄어들고 재물이 머무는 안정감이 생깁니다.",
    aroma: "베티버 · 샌달우드 · 만다린 (차분하고 포근한 대지의 향기가 산만한 생각을 가라앉히고 현실적인 실행력을 단단히 고정해 줍니다.)"
  },
  "금": {
    name: "크리스탈 화이트 & 골드",
    hex: "#E2E8F0",
    desc: "명확한 결단력과 맺고 끊음의 에너지를 보강합니다.",
    fashion: "깨끗한 화이트 셔츠, 골드·실버 메탈 시계나 안경테를 착용하면 우유부단함을 끊어내고 명확한 판단력과 카리스마가 살아납니다.",
    interior: "책상 위 서류와 케이블을 깔끔히 정리하고 화이트·메탈 트레이나 둥근 시계를 배치하면 일의 마무리 능력과 결실운이 강해집니다.",
    aroma: "유칼립투스 · 사이프러스 · 레몬 (맑고 예리한 시트러스 우디 노트가 감정적 미련을 정리하고 핵심에 집중하게 돕습니다.)"
  },
  "수": {
    name: "딥 오션 블루",
    hex: "#2563EB",
    desc: "깊은 사고력과 유연함, 내면의 지혜를 채워줍니다.",
    fashion: "딥 블루·네이비 셔츠나 데님, 물결무늬 실크 스카프, 진주·아쿠아마린 포인트를 활용해 과열된 스트레스를 식히고 유연성을 높이세요.",
    interior: "침실이나 휴식 공간에 블루 계열 쿠션·침구를 배치하고, 유리 물병을 책상 옆에 두어 수분과 차분한 사색의 에너지를 보충하세요.",
    aroma: "라벤더 · 프랑킨센스 · 카모마일 (깊고 고요한 수분감의 허브 노트가 조급함과 화기를 잠재우고 지혜로운 통찰력을 채워줍니다.)"
  }
};

const ILJI_INNER_TRAIT = {
  "자": "지혜롭고 속마음을 쉽게 드러내지 않는 전략가적 면모가 있으며, 조용한 환경에서 아이디어가 샘솟습니다.",
  "축": "묵묵히 자기 자리를 지키는 끈기와 성실함이 강하며, 한번 마음을 먹으면 끝까지 해내는 저력이 있습니다.",
  "인": "새로운 일을 기획하고 시작하는 추진력이 뛰어나며, 어디서든 주도권을 쥐고 역동적으로 움직이려는 성향이 강합니다.",
  "묘": "섬세한 감수성과 뛰어난 눈치, 미적 감각을 갖추고 있으며 사람들과 부드럽게 어울리는 친화력이 돋보입니다.",
  "진": "스케일이 크고 이상이 높으며, 변화를 두려워하지 않고 큰 판을 움직이려는 진취적인 에너지를 품고 있습니다.",
  "사": "두뇌 회전이 빠르고 언변과 표현력이 뛰어나며, 목표를 포착하면 예리하게 파고드는 집중력이 있습니다.",
  "오": "화려하고 열정적이며 솔직한 매력이 넘치고, 주변 사람들에게 밝은 에너지를 전파하는 카리스마가 있습니다.",
  "미": "온화하고 배려심이 깊지만 내면에는 단단한 고집과 실속을 챙기는 현실 감각이 자리 잡고 있습니다.",
  "신": "다재다능하고 임기응변이 뛰어나며, 상황을 객관적이고 냉철하게 분석하여 해결책을 찾아내는 능력이 탁월합니다.",
  "유": "깔끔하고 완벽주의적인 성향이 강하며, 자신의 분야에서는 타협 없는 프로페셔널함을 보여주는 장인 기질이 있습니다.",
  "술": "의리와 신의를 목숨처럼 여기며, 책임감이 강해 주변 사람들로부터 든든한 버팀목으로 신뢰받습니다.",
  "해": "포용력이 넓고 통찰력과 직관이 뛰어나며, 학문이나 예술·철학 등 깊이 있는 분야를 탐구하는 지혜가 있습니다."
};

const ILJI_SIPSEONG_MOD = {
  "비견": "배우자와 친구처럼 대등하고 독립적인 관계를 추구하며, 스스로 주인이 되는 구조에서 성취감이 큽니다.",
  "겁재": "승부욕과 추진력이 강해 경쟁이 치열한 환경에서 오히려 능력을 발휘하며, 재물은 고정 자산으로 묶어두는 것이 유리합니다.",
  "식신": "타고난 복록과 창의적 전문성이 있어 좋아하는 일을 꾸준히 파고들면 자연스럽게 의식주와 재물이 풍요로워집니다.",
  "상관": "기존의 틀을 깨는 혁신적인 아이디어와 언변이 무기이며, 자유로운 환경에서 재능을 표현할 때 크게 성공합니다.",
  "편재": "넓은 무대와 사업적 수완을 갖추어 큰돈의 흐름을 읽는 감각이 뛰어나며, 활동 반경을 넓힐수록 재물운이 상승합니다.",
  "정재": "성실하고 계획적인 자산 관리 능력이 탁월하며, 안정적인 시스템 속에서 차곡차곡 확실한 부와 신뢰를 쌓아갑니다.",
  "편관": "강한 책임감과 카리스마로 어려운 과제를 해결하는 해결사 기질이 있으며, 조직의 핵심 리더나 전문직에서 빛납니다.",
  "정관": "원칙과 명예를 중시하는 반듯한 성품으로 사회적 신뢰가 높으며, 안정적인 조직이나 전문 분야에서 탄탄대로를 걷습니다.",
  "편인": "남다른 직관력과 독창적인 통찰력을 지녀 기획·연구·IT·심리·예술 등 특수 전문 영역에서 대체 불가능한 존재가 됩니다.",
  "정인": "학구열이 높고 따뜻한 포용력과 문서운(자격·부동산)을 타고나, 주변의 도움과 인정을 받으며 품위 있게 성장합니다."
};

const ILGAN_DB = {
  "갑": {
    temperament: "목표가 정해지면 뒤돌아보지 않고 직진하는 개척자형 기질입니다. 자존심과 주체성이 매우 강해 남의 지시를 수동적으로 따르기보다 스스로 판을 짜고 주도권을 쥘 때 가장 큰 생명력을 발휘합니다. 속마음이 투명하고 불의를 보면 참지 못하는 대장부 기질이 있으며, 새로운 환경을 두려워하지 않고 맨 앞에서 길을 여는 리더의 본성을 타고났습니다.",
    strength: "위기 상황에서도 쉽게 꺾이지 않는 압도적인 추진력과 기획력, 아무것도 없는 맨땅에서 새로운 구조를 일궈내는 돌파력이 최고의 무기입니다. 한 번 책임지기로 마음먹은 일은 끝까지 밀어붙이는 우직한 성실성을 갖추고 있습니다.",
    weakness: "융통성이 부족해 큰 바람에 부러지기 쉽고, 한 번 고집을 피우면 주변의 합리적인 조언조차 귀를 닫아 독단적으로 흐를 위험이 있습니다. 사소한 디테일이나 감정적인 배려를 놓쳐 가까운 사람에게 서운함을 줄 수 있습니다.",
    coaching: "때로는 '굽힐 줄 아는 유연함(을목의 지혜)'을 의식적으로 훈련하세요. 100% 완벽한 계획이 세워질 때까지 기다리기보다 70% 수준에서 먼저 실행한 뒤 현장에서 수정하는 방식이 훨씬 유리합니다.",
    externalView: "첫인상은 당당하고 스케일이 크며 믿음직스러운 리더처럼 보입니다. 속내를 숨기지 못해 솔직하고 뒤끝 없는 사람으로 평가받지만, 가까운 사이에서는 의외로 순수하고 여린 면모가 드러나 반전 매력을 줍니다.",
    compatibility: "나를 부드럽게 감싸주고 현실적인 살림과 디테일을 조율해 주는 기토(己土) 성향의 사람과 최고의 합(갑기합토)을 이룹니다. 또한 내 에너지를 꽃피워주는 병화(丙火)나 뿌리를 적셔주는 계수(癸水) 성향의 파트너와 함께할 때 시너지가 극대화됩니다.",
    wealth: "단기적인 시세 차익이나 투기성 재테크보다는 자신의 이름값, 전문 라이선스, 사업적 지분을 키워 큰 판을 움직일 때 묵직한 재물이 따릅니다. 현금을 손에 쥐고 있으면 쓰임새가 커지므로 부동산·우량 장기 자산 형태로 묶어두는 전략이 필수입니다.",
    love: "좋아하면 계산하지 않고 적극적으로 표현하는 직진형 연애를 합니다. 자존심을 세워주고 능력과 비전을 존중해 주는 연인에게는 한없이 헌신하지만, 사사건건 통제하려 들거나 자존심을 긁으면 빠르게 마음이 식습니다.",
    career: "신규 사업 기획, 스타트업 창업, 프로젝트 총괄(PM), 건축·인테리어, 교육·코칭 리더, 조직 경영 등 스스로 의사결정권을 쥐고 비전을 제시하는 직무가 천직입니다.",
    health: "오행상 목(木)에 해당하므로 간 기능, 눈의 피로, 목·어깨·근육의 만성 긴장에 유의해야 합니다. 스트레스가 쌓이면 편두통이나 상열감으로 나타나기 쉬우므로 주 3회 이상 가벼운 유산소 운동과 스트레칭으로 기운을 순환시키세요."
  },
  "을": {
    temperament: "어떤 척박한 환경에서도 살아남는 강인한 적응력과 유연한 처세술을 지닌 기질입니다. 겉으로는 바람에 흔들리는 들꽃처럼 부드럽고 온화해 보이지만, 내면에는 명확한 목표 의식과 현실적인 실리를 챙기는 강단 있는 생존 본능이 자리 잡고 있습니다. 사람과 환경을 자연스럽게 연결하는 네트워킹 능력이 탁월합니다.",
    strength: "상황 변화에 대한 눈치와 판단력이 빠르고, 갈등을 부드럽게 봉합하는 협상·조율 능력이 뛰어납니다. 한 번 뿌리를 내리면 끝까지 버텨내는 끈기와 지구력으로 결국 원하는 목표를 손에 넣습니다.",
    weakness: "주변 사람의 시선과 평가를 지나치게 의식해 에너지를 소모하거나, 결정적인 순간에 혼자 책임지는 것을 두려워해 결단을 미루는 경향이 나타날 수 있습니다.",
    coaching: "타인의 기대에 맞추느라 정작 자신의 욕구를 억누르지 않도록 '건강하게 거절하는 연습'이 필요합니다. 막연한 불안감이 올라올 때는 머릿속 고민을 종이에 적어 우선순위를 정하고 실행하세요.",
    externalView: "친근하고 배려심이 깊으며 대화가 잘 통하는 세련된 사람으로 보입니다. 모난 구석이 없어 어디서든 환영받으며, 부드러운 카리스마로 주변에 사람과 정보가 자연스럽게 모여듭니다.",
    compatibility: "나의 재능을 정교하게 다듬어주고 명확한 방향을 제시해 주는 경금(庚金) 성향의 사람과 강한 운명적 끌림(을경합금)이 있습니다. 결단력 있는 실행가 파트너와 짝을 이루면 기획과 실행이 완벽히 맞물립니다.",
    wealth: "혼자 고독하게 일하기보다 인맥, 정보력, 트렌드 감각을 활용한 비즈니스, 중개·에이전시, 컨설팅, 온라인 커머스 분야에서 꾸준하고 알찬 현금 흐름을 만들어냅니다.",
    love: "다정다감하고 세심하게 상대의 기분을 살피는 로맨틱한 연애를 합니다. 정서적 교감과 대화가 무엇보다 중요하며, 흔들리는 마음을 든든하게 잡아줄 수 있는 듬직하고 일관성 있는 상대에게 깊이 끌립니다.",
    career: "마케팅·브랜딩, 홍보·PR, 외교·협상, 공간·시각 디자인, 심리상담·코칭, 인사(HR), 프리랜서 전문직 등 유연한 소통과 감각이 빛나는 분야가 최적입니다.",
    health: "신경계 예민함, 스트레스성 소화기(위장) 트러블, 관절 및 말초 혈액순환 관리에 신경 써야 합니다. 규칙적인 수면 리듬을 유지하고 햇볕을 쬐며 걷는 산책이 최고의 보약입니다."
  },
  "병": {
    temperament: "한낮의 태양처럼 밝고 열정적이며 숨김이 없는 투명한 기질입니다. 호기심이 왕성하고 표현력이 풍부해 어디를 가나 어두운 분위기를 환하게 밝히는 에너지 발전소 역할을 합니다. 예의와 명분을 중시하며, 한번 마음을 열면 조건 없이 베푸는 호탕함과 추진력을 지녔습니다.",
    strength: "탁월한 전달력과 프레젠테이션 능력, 침체된 조직과 분위기를 단숨에 반전시키는 긍정 에너지, 아이디어를 즉시 행동으로 옮기는 빠른 실행력이 최고의 강점입니다.",
    weakness: "감정 기복이 빠르고 흥미가 식으면 뒷심이 약해져 용두사미가 될 위험이 있습니다. 솔직하고 직설적인 화법으로 인해 본의 아니게 상대방에게 상처를 줄 수 있으므로 말의 온도를 조절해야 합니다.",
    coaching: "열정이 과열되어 스스로 지치기 전에 의식적으로 한 박자 멈춰 서는 '냉각 루틴'을 만드세요. 시작하는 에너지는 타의 추종을 불허하므로, 마무리를 함께 챙겨줄 꼼꼼한 체크리스트나 실무 파트너를 두는 것이 성공의 핵심입니다.",
    externalView: "에너지가 넘치고 화려하며 솔직 담백한 사람으로 비칩니다. 뒤끝이 없고 명랑해 주변 사람들에게 활력을 주지만, 때로는 다소 성급하거나 자기주장이 강해 보일 수 있습니다.",
    compatibility: "나의 뜨거운 열정을 차분하게 식혀주고 세련되게 빛내주는 신금(辛金) 성향의 사람과 찰떡궁합(병신합수)을 이룹니다. 차분하고 디테일에 강한 파트너가 내 에너지를 고부가가치 성과로 바꾸어 줍니다.",
    wealth: "작은 돈을 아끼며 모으기보다 판을 키우고 회전시키는 감각이 뛰어납니다. 대중을 상대로 하는 분야, 방송·미디어, 교육·강연, IT 트렌드 및 마케팅 분야에서 큰 수익을 창출합니다.",
    love: "금방 사랑에 빠지고 뜨겁게 애정을 표현하는 정열적인 로맨티스트입니다. 함께 새로운 장소를 여행하고 지적·감각적 경험을 공유할 수 있는 센스 있는 연인과 오랫동안 행복한 관계를 유지합니다.",
    career: "강사·교육자, 방송·유튜브 크리에이터, 영업·비즈니스 개발, 공연·엔터테인먼트, 스타트업 창업 등 자신을 무대 위에 드러내고 대중과 소통하는 직업이 천직입니다.",
    health: "오행상 화(火)의 기운이 강하므로 심혈관계, 시력, 열감으로 인한 피부 트러블이나 불면증에 주의해야 합니다. 과도한 카페인 섭취를 줄이고 충분한 수분 보충으로 열기를 진정시키세요."
  },
  "정": {
    temperament: "어둠을 밝히는 촛불이나 용광로처럼 은은하지만 한곳에 집중하면 놀라운 몰입력을 발휘하는 섬세한 기질입니다. 감수성이 풍부하고 통찰력이 예리해 겉으로 드러나지 않는 이면의 본질과 사람의 심리를 정확히 꿰뚫어 봅니다. 내면에 뜨거운 열정과 헌신적인 사랑을 품고 있습니다.",
    strength: "깊이 있는 탐구력과 분석력, 타인의 아픔을 세심하게 살피는 배려심, 특정 전문 분야를 끝까지 파고들어 독보적인 경지에 오르는 장인 정신과 직관력이 뛰어납니다.",
    weakness: "생각과 걱정이 너무 많아 시작 전부터 에너지를 소모하거나, 마음속에 서운함을 차곡차곡 쌓아두었다가 한계점에 다다르면 한 번에 폭발시켜 관계를 단절하는 경향이 있습니다.",
    coaching: "머릿속을 맴도는 복잡한 생각과 감정을 글쓰기나 메모로 시각화하여 밖으로 비워내는 습관이 좋습니다. 완벽주의 기준을 100%에서 80%로 낮추면 실행 속도와 삶의 만족도가 배가 됩니다.",
    externalView: "차분하고 지적인 분위기를 풍기며, 속이 깊고 예의 바른 사람으로 보입니다. 첫인상은 다소 조용해 보일 수 있으나 가까이 지낼수록 진가와 따뜻한 온기가 드러나는 매력적인 스타일입니다.",
    compatibility: "넓은 포용력으로 나의 섬세함을 든든하게 받아주는 임수(壬水) 성향의 사람과 깊은 인연(정임합목)을 맺습니다. 또한 나의 불꽃이 꺼지지 않게 땔감이 되어주는 갑목(甲木) 성향과도 훌륭한 조화를 이룹니다.",
    wealth: "단순 노동보다는 전문 기술, 지적 재산권, 연구·분석, 정밀 자산 관리 등 치밀한 계산과 희소성 있는 전문성이 필요한 영역에서 알짜배기 부를 단단하게 축적합니다.",
    love: "한 사람에게 깊이 몰입하고 헌신하는 순정파입니다. 화려한 겉모습보다 내면의 깊은 대화가 통하고 정서적 안정감과 신뢰를 주는 상대에게 마음의 문을 활짝 엽니다.",
    career: "연구원, 데이터 애널리스트, 심리상담가, 작가·콘텐츠 기획자, 의료·약학, IT 개발 및 정밀 예술·공예 분야가 탁월합니다.",
    health: "심장 두근거림, 신경성 소화불량, 안구 건조증, 말초 혈액순환에 유의하세요. 저녁 시간의 명상이나 따뜻한 반신욕이 긴장된 신경을 이완하고 에너지를 회복하는 데 큰 도움이 됩니다."
  },
  "무": {
    temperament: "웅장한 태산처럼 묵직하고 신용을 목숨처럼 여기는 신뢰의 아이콘입니다. 포용력이 넓어 다양한 사람들의 비밀과 고민을 들어주는 대나무 숲 역할을 자주 맡습니다. 스케일이 크고 중재 능력이 뛰어나 어떤 조직에서든 흔들리지 않는 중심축을 잡아줍니다.",
    strength: "위기 상황에서도 당황하지 않는 배포와 안정감, 이해관계가 얽힌 사람들을 하나로 묶는 중재력, 한 번 시작한 일을 묵묵히 완수하는 우직한 지구력이 강점입니다.",
    weakness: "변화를 싫어해 보수적이고 고집이 셀 수 있으며, 돌다리를 너무 오래 두드리느라 행동으로 옮기는 시동이 늦어져 좋은 타이밍을 놓칠 수 있습니다.",
    coaching: "완벽한 조건이 갖춰지기를 기다리기보다 작은 실험부터 즉시 실행하는 '민첩함'을 더하세요. 낯선 분야의 배움이나 여행은 고여 있는 흙의 에너지를 순환시켜 새로운 기회를 불러옵니다.",
    externalView: "듬직하고 비밀을 끝까지 지켜줄 것 같은 믿음직한 사람으로 보입니다. 말과 행동에 무게감이 있어 나이에 비해 성숙하고 포용력이 넓다는 인상을 줍니다.",
    compatibility: "나의 묵직함에 생기와 촉촉한 아이디어를 불어넣어 주는 계수(癸水) 성향의 사람과 이상적인 조화(무계합화)를 이룹니다. 섬세하고 기발한 파트너가 내 현실 감각과 결합하면 큰 성취를 이룹니다.",
    wealth: "부동산, 건축, 인프라, 중개, 우량 장기 가치 투자 등 묵직하고 안정적인 자산 증식에 천부적인 감각이 있습니다. 단기 변동성에 흔들리지 않고 시간을 내 편으로 만들 때 큰 부를 거머쥡니다.",
    love: "한번 내 사람이라고 생각하면 끝까지 책임지고 지켜주는 든든한 연애를 합니다. 다만 감정 표현이 투박하고 무뚝뚝할 수 있으므로 의식적으로 고마움과 애정을 말로 표현하는 노력이 관계를 더욱 빛나게 합니다.",
    career: "부동산·금융 자산 관리, 조직 관리·경영, 공공기관, 법률·중재 컨설팅, 플랫폼 운영 등 사람과 자원을 안전하게 모으고 관리하는 분야가 잘 맞습니다.",
    health: "오행상 토(土)에 해당하므로 위장·비장 등 소화기 계통과 체중 관리에 신경 써야 합니다. 스트레스성 폭식이나 야식을 피하고 하체 근력을 키우는 규칙적인 운동이 필수입니다."
  },
  "기": {
    temperament: "만물을 길러내는 비옥한 텃밭처럼 실속 있고 다재다능하며 현실 감각이 뛰어난 기질입니다. 겉으로 자신을 화려하게 과시하기보다 내실과 실리를 챙기며, 주변 사람을 세심하게 보살피는 따뜻한 포용력과 어머니 같은 배려심을 지녔습니다.",
    strength: "현실적인 문제 해결 능력, 새로운 지식을 빠르게 자기 것으로 만드는 학습·흡수력, 어떤 성향의 사람과도 무난하게 어울리는 유연한 친화력이 최고의 강점입니다.",
    weakness: "속마음을 잘 드러내지 않아 주변에서 알기 어렵다는 오해를 살 수 있으며, 사소한 일에 마음을 쓰느라 우유부단해져 결단력이 약해질 수 있습니다.",
    coaching: "모든 사람을 다 챙기려다 정작 본인의 에너지와 우선순위를 놓치지 마세요. 핵심 목표 1~2가지에 시간과 자원을 집중하는 '선택과 집중' 전략이 필요합니다.",
    externalView: "온화하고 소탈하며 실무 능력이 뛰어난 사람으로 평가받습니다. 권위적이지 않고 편하게 다가갈 수 있는 좋은 이웃이자 든든한 실무 파트너 같은 인상을 줍니다.",
    compatibility: "나에게 명확한 비전과 큰 무대를 열어주는 갑목(甲木) 성향의 사람과 최고의 파트너십(갑기합토)을 발휘합니다. 추진력 있는 리더의 곁에서 내실을 다질 때 가장 큰 보상을 얻습니다.",
    wealth: "알뜰하고 치밀한 자산 관리와 실속 있는 수익 파이프라인 구축에 능합니다. 교육·콘텐츠, 프랜차이즈, 생활 밀착형 비즈니스, 적립식 장기 투자에서 꾸준하고 단단하게 재산을 불립니다.",
    love: "현실적이고 안정적인 연애를 추구하며, 상대의 화려한 말보다 생활 습관과 성실함을 중요하게 봅니다. 소소한 일상을 함께 나누고 서로의 편이 되어주는 따뜻한 관계에서 깊은 행복을 느낍니다.",
    career: "교육·강사, 세무·회계, 인사·총무, 요리·웰니스, 콘텐츠 기획, 고객 관리(CS) 등 세심한 디테일과 배려가 필요한 직무가 최적입니다.",
    health: "소화기(위·장), 피부 알레르기, 당 대사 관리에 주의하세요. 규칙적인 식사 시간을 지키고 식이섬유가 풍부한 자연식 위주의 식단이 건강과 컨디션을 지켜줍니다."
  },
  "경": {
    temperament: "제련되지 않은 거대한 원석이자 강철처럼 결단력과 추진력이 압도적인 기질입니다. 옳고 그름이 명확하며 의리와 원칙을 목숨처럼 중시합니다. 불필요한 군더더기나 변명을 싫어하고 문제의 핵심을 정확히 찌르는 카리스마와 개혁 정신을 지녔습니다.",
    strength: "강력한 실행력, 위기 상황에서의 냉철한 돌파 능력, 사사로운 감정에 치우치지 않는 공정한 판단력, 목표를 향한 무서운 집중력이 최고의 무기입니다.",
    weakness: "타협을 모르고 직설적인 화법을 구사해 주변과 마찰을 빚기 쉬우며, 자신과 타인에게 지나치게 엄격한 잣대를 들이대어 스스로를 고립시킬 수 있습니다.",
    coaching: "단단한 강철이 세상을 이롭게 하는 명검이 되려면 공감과 경청이라는 부드러운 연마 과정이 필요합니다. 상대의 감정을 먼저 인정해 주는 화법을 익히면 리더로서의 영향력이 배가 됩니다.",
    externalView: "카리스마 있고 프로페셔널하며 맺고 끊음이 확실한 사람으로 보입니다. 첫인상은 다소 차갑고 강해 보일 수 있으나, 실제로는 한 번 맺은 인연을 끝까지 지키는 의리파입니다.",
    compatibility: "나의 단단함을 부드럽게 녹여주고 유연한 처세와 지혜를 더해주는 을목(乙木) 성향의 사람과 강한 운명적 인연(을경합금)을 이룹니다.",
    wealth: "결단력과 속도감이 필요한 투자, 금융, IT·엔지니어링, 제조·유통, 전문직 라이선스를 통해 큰 규모의 자산을 형성합니다. 원칙을 세운 시스템 투자가 유리합니다.",
    love: "밀당이나 애매한 태도를 싫어하고 솔직 담백한 연애를 선호합니다. 한 번 신뢰를 주면 변치 않고 든든하게 지켜주지만, 거짓말이나 무책임한 태도는 단호하게 선을 긋습니다.",
    career: "엔지니어, 금융·투자 전문가, 법률·수사, 의료(외과·치과계), 경영 전략, 스포츠·군경 등 명확한 성과와 원칙이 중요한 분야가 천직입니다.",
    health: "오행상 금(金)에 해당하므로 폐·호흡기, 대장 기능, 피부 건조증, 치아 및 뼈·관절 건강에 유의하세요. 맑은 공기를 마시는 유산소 운동과 충분한 보습 관리가 중요합니다."
  },
  "신": {
    temperament: "정교하게 세공된 보석이나 예리한 칼날처럼 섬세하고 세련되며 자존심이 강한 기질입니다. 미적 감각과 디테일 포착 능력이 타의 추종을 불허하며, 자신만의 확고한 기준과 취향을 가지고 있습니다. 깔끔하고 군더더기 없는 완벽한 일 처리를 선호합니다.",
    strength: "초정밀 분석력, 탁월한 심미안과 트렌드 감각, 상황의 본질을 꿰뚫는 예리한 직관, 높은 완성도를 추구하는 프로페셔널 의식이 강점입니다.",
    weakness: "예민하고 까다로워 스스로 스트레스를 많이 받으며, 한 번 마음이 상하거나 실망하면 냉정하게 돌아서는 단호함 때문에 인간관계의 폭이 좁아질 수 있습니다.",
    coaching: "자신에게 들이대는 완벽주의의 잣대를 조금 느슨하게 풀어주세요. 타인의 실수나 빈틈을 너그럽게 허용하는 여유를 가질 때 본연의 보석 같은 가치가 더욱 눈부시게 빛납니다.",
    externalView: "세련되고 지적이며 빈틈없는 전문가의 인상을 줍니다. 깔끔한 외모와 정제된 말투로 호감을 얻으며, 함부로 대할 수 없는 고유의 품위와 아우라가 느껴집니다.",
    compatibility: "나의 차가운 완벽주의를 따뜻하게 비춰주고 생기와 활력을 불어넣는 병화(丙火) 성향의 사람과 최고의 조화(병신합수)를 이룹니다. 밝고 긍정적인 파트너가 내 긴장을 녹여줍니다.",
    wealth: "고부가가치 전문직, 뷰티·패션, 디자인, 정밀 분석, 금융 자산 운용 등 남들이 쉽게 흉내 낼 수 없는 희소성과 퀄리티로 승부하는 분야에서 큰 부를 얻습니다.",
    love: "자신의 취향과 지적 수준이 맞는 센스 있는 상대에게 끌립니다. 세심한 배려와 매너를 중시하며, 서로의 개인 영역과 프라이버시를 존중하는 세련된 연애를 원합니다.",
    career: "디자이너, 뷰티·패션 디렉터, 애널리스트, 연구원, IT 기획·QA, 아나운서·방송인, 럭셔리 브랜드 비즈니스 등이 잘 맞습니다.",
    health: "호흡기(기관지·비염), 피부 예민함, 신경성 편두통에 주의해야 합니다. 실내 습도 조절과 따뜻한 물 마시기, 아로마·명상 등 신경 이완 루틴이 필수입니다."
  },
  "임": {
    temperament: "깊고 넓은 바다나 도도히 흐르는 큰 강물처럼 지혜롭고 스케일이 크며 유연한 사고를 지닌 기질입니다. 임기응변과 통찰력이 뛰어나 어떤 위기 상황에서도 기발한 해법을 찾아냅니다. 속내를 쉽게 드러내지 않는 깊이가 있으며 자유로운 영혼의 소유자입니다.",
    strength: "탁월한 지혜와 학습·응용 능력, 거시적인 안목, 어떤 틀이나 고정관념에도 갇히지 않는 창의성과 포용력이 최고의 강점입니다.",
    weakness: "생각이 너무 방대해 실행이 늦어지거나, 흥미가 떨어지면 쉽게 방향을 바꾸어 마무리가 약해지고 산만해질 수 있습니다.",
    coaching: "넓게 펼쳐진 아이디어를 하나로 모으는 명확한 마감 기한(데드라인)을 설정하고 하나씩 완수하는 습관이 성공의 열쇠입니다.",
    externalView: "지적이고 여유로우며 속을 알 수 없는 매력적인 사람으로 보입니다. 격식에 얽매이지 않고 누구와도 유연하게 어울리는 친화력과 카리스마를 동시에 지녔습니다.",
    compatibility: "나의 넓은 생각에 따뜻한 온기와 집중력을 더해주는 정화(丁火) 성향의 사람과 운명적인 시너지(정임합목)를 냅니다. 또한 물길을 잡아주는 무토(戊土) 성향과도 훌륭한 파트너가 됩니다.",
    wealth: "유통, 무역, IT·플랫폼, 지식 비즈니스, 해외 관련 사업 등 사람과 자본이 크게 흐르는 길목에서 스케일 큰 재물을 만집니다.",
    love: "구속받거나 집착하는 연애를 싫어하며 친구처럼 대화가 잘 통하는 자유로운 관계를 선호합니다. 지적 호기심을 자극하고 배울 점이 있는 매력적인 상대에게 깊이 빠집니다.",
    career: "무역·물류, IT·AI 서비스 기획, 경영 컨설턴트, 전략 기획, 연구·학술, 여행·미디어 등 변화와 흐름을 읽는 분야가 천직입니다.",
    health: "오행상 수(水)에 해당하므로 신장·방광 등 비뇨기 계통, 혈액순환, 부종, 하체 냉증에 유의해야 합니다. 반신욕이나 족욕으로 하체를 따뜻하게 유지하고 짠 음식을 줄이세요."
  },
  "계": {
    temperament: "대지를 적시는 고요한 봄비나 맑은 샘물처럼 섬세하고 직관적이며 타인의 감정에 깊이 공감하는 기질입니다. 두뇌 회전이 빠르고 아이디어가 샘솟으며, 겉으로 소리 내지 않고 조용히 스며들어 사람들의 마음을 움직이는 치유와 설득의 힘을 지녔습니다.",
    strength: "뛰어난 직관력과 공감 능력, 참신한 기획력, 세밀한 관찰력과 어떤 환경에도 스며드는 유연한 적응력이 최고의 무기입니다.",
    weakness: "감수성이 풍부한 만큼 사소한 말에도 상처를 잘 받고 기분에 따라 에너지가 출렁이며, 현실적인 추진력이나 체력이 다소 약해질 수 있습니다.",
    coaching: "감정의 파도에 휩쓸리지 않도록 객관적인 데이터와 규칙적인 일상 루틴으로 생활을 단단히 고정하세요. 머릿속 아이디어를 즉시 메모하고 작은 행동으로 옮기는 훈련이 중요합니다.",
    externalView: "차분하고 다정하며 감성적인 사람으로 보입니다. 비밀을 털어놓고 싶게 만드는 편안하고 치유적인 아우라가 있어 주변에 고민 상담을 청하는 사람이 많습니다.",
    compatibility: "나의 감수성을 든든하게 받아주고 현실적인 뼈대를 세워주는 무토(戊土) 성향의 사람과 완벽한 합(무계합화)을 이룹니다. 묵직하고 일관성 있는 파트너가 최고의 안식처가 됩니다.",
    wealth: "아이디어, 콘텐츠, 심리·상담, 교육, 온라인 비즈니스 등 초기 자본이 적게 들고 지혜와 감각을 활용하는 분야에서 알찬 수익을 창출합니다.",
    love: "정서적 교감과 섬세한 배려가 무엇보다 중요한 연애를 합니다. 말하지 않아도 눈빛과 마음을 알아주는 다정하고 든든한 상대에게 온 마음을 다해 헌신합니다.",
    career: "심리상담·코칭, 작가·콘텐츠 크리에이터, 브랜드·서비스 기획, 교육, 예술·디자인, 데이터 및 트렌드 리서치 분야가 최적입니다.",
    health: "신장 기능, 수면 장애(불면), 수족냉증, 만성 피로에 주의해야 합니다. 무리한 밤샘 작업을 피하고 충분한 숙면과 가벼운 근력 운동으로 기초 체력을 다지세요."
  }
};

const SEUN_YEAR_DETAIL = {
  "비견": {
    theme: "주체성 확립 · 독립적 도약",
    flow: "나와 같은 오행의 에너지가 강하게 들어와 자존감과 독립심이 높아집니다. 남에게 의지하기보다 스스로 판을 짜고 주도권을 쥘 때 성과가 커집니다.",
    action: "개인 브랜딩, 단독 프로젝트 런칭, 전문 영역 확장에 최적의 시기입니다. 다만 동업이나 공동 투자는 의견 충돌이 생기기 쉬우니 역할과 지분을 명확히 나누세요.",
    caution: "고집이 세져 주변의 조언을 놓칠 수 있으니 유연한 소통을 유지하세요."
  },
  "겁재": {
    theme: "활동 반경 확장 · 전략적 자산 방어",
    flow: "경쟁심과 승부욕이 불타오르며 새로운 인맥과 외부 활동이 폭발적으로 늘어납니다. 치열한 경쟁 속에서 오히려 내 실력을 입증할 기회가 찾아옵니다.",
    action: "네트워킹을 통한 비즈니스 기회 포착과 공격적인 역량 개발에 유리합니다. 수익이 들어오는 만큼 지출도 커지므로 선저축·후지출 시스템을 반드시 가동하세요.",
    caution: "충동적인 투자, 보증, 지인 간의 금전 거래는 절대 피해야 합니다."
  },
  "식신": {
    theme: "전문성 발휘 · 의식주 풍요와 결실",
    flow: "나의 재능과 전문성이 자연스럽게 세상에 드러나며 일상의 여유와 풍요가 따르는 길운입니다. 그동안 묵묵히 준비해 온 작업물이 인정받습니다.",
    action: "콘텐츠 제작, 연구 개발, 자격증 취득, 새로운 서비스 출시에 최고의 타이밍입니다. 좋아하는 분야를 깊이 파고들수록 자연스럽게 재물운으로 연결됩니다.",
    caution: "안일함에 빠져 마무리를 미루지 않도록 일정 관리를 꼼꼼히 하세요."
  },
  "상관": {
    theme: "혁신적 돌파 · 표현력과 변화의 물결",
    flow: "기존의 낡은 틀을 깨고 새로운 방식으로 도약하려는 에너지가 강해집니다. 언변과 창의력이 빛을 발하며 직무 전환이나 새로운 도전의 기회가 열립니다.",
    action: "프레젠테이션, 마케팅, 창업, 예술·기획 분야에서 압도적인 존재감을 드러낼 수 있습니다. 아이디어를 즉시 실행에 옮겨 시장의 반응을 확인하세요.",
    caution: "직설적인 말투로 인한 구설이나 윗사람과의 마찰만 조심하면 크게 도약합니다."
  },
  "편재": {
    theme: "무대 확장 · 역동적 재물과 사업 기회",
    flow: "활동 무대가 넓어지고 다양한 경로에서 수익과 사업적 기회가 찾아오는 역동적인 시기입니다. 큰돈의 흐름을 읽는 감각과 추진력이 살아납니다.",
    action: "신규 거래처 개척, 부업·N잡 확장, 유통·영업 활동에서 기대 이상의 성과를 거둘 수 있습니다. 여러 기회 중 핵심 2가지에 선택과 집중을 하세요.",
    caution: "무리한 사업 확장이나 과로로 인한 체력 저하를 경계해야 합니다."
  },
  "정재": {
    theme: "안정적 축적 · 성실한 노력의 확실한 보상",
    flow: "땀 흘려 노력한 만큼 정직하고 안정적인 대가가 돌아오는 탄탄한 재물운의 해입니다. 삶의 질서가 잡히고 신용도가 크게 상승합니다.",
    action: "급여·매출의 안정적 증대, 장기 저축, 부동산·우량 자산 계약 및 문서 정리에 매우 유리합니다. 보수적이고 계획적인 자산 배분이 빛을 발합니다.",
    caution: "지나친 완벽주의나 소심함으로 찾아온 좋은 기회를 망설이지 마세요."
  },
  "편관": {
    theme: "책임감과 돌파 · 리더십 및 지위 상승",
    flow: "사회적 역할과 책임이 커지며 어려운 과제를 해결해 명예를 높이는 시기입니다. 압박감이 따르는 환경일수록 오히려 숨겨진 카리스마가 발휘됩니다.",
    action: "중책 맡기, 승진 심사, 조직 개편의 핵심 리더 역할, 난이도 높은 프로젝트 완수를 통해 조직 내 입지를 확고히 굳힐 수 있습니다.",
    caution: "과도한 스트레스와 과로를 피하고 규칙적인 운동으로 긴장을 풀어주세요."
  },
  "정관": {
    theme: "명예와 인정 · 반듯한 성취와 안정",
    flow: "승진, 합격, 사회적 평판 상승 등 반듯한 명예운과 조직운이 활짝 열리는 해입니다. 원칙과 신뢰를 바탕으로 주변의 두터운 인정을 받습니다.",
    action: "시험·자격 합격, 이직 및 승진, 공식 계약 체결, 안정적인 커리어 확장에 최적의 시기입니다. 정공법으로 차분히 나아가면 원하는 자리를 얻습니다.",
    caution: "체면이나 형식에 얽매여 유연성을 잃지 않도록 균형을 잡으세요."
  },
  "편인": {
    theme: "직관과 통찰 · 특수 전문성과 내면의 도약",
    flow: "생각이 깊어지고 남들이 보지 못하는 이면을 꿰뚫는 직관력과 기획력이 예리해집니다. 특수 전문 분야나 학문·예술적 몰입에 강한 에너지를 발휘합니다.",
    action: "중장기 전략 수립, IT·데이터·심리·기획 분야 심화 학습, 독창적인 아이디어 특허 및 브랜드 기획에 탁월한 성과를 냅니다.",
    caution: "생각이 너무 많아 실행이 늦어지거나 고립되지 않도록 소통 창구를 열어두세요."
  },
  "정인": {
    theme: "귀인의 도움 · 문서운과 내실의 완성",
    flow: "윗사람이나 귀인의 따뜻한 지원이 따르고, 학업·자격·계약 등 문서운이 순조롭게 풀리는 복된 시기입니다. 조급함을 내려놓을수록 좋은 기회가 제 발로 찾아옵니다.",
    action: "부동산·주요 계약 체결, 학위·자격 취득, 브랜드 신뢰도 구축 및 내실 다지기에 집중하세요. 배움에 투자한 시간과 비용이 몇 배의 가치로 돌아옵니다.",
    caution: "주변의 도움에 안주해 스스로 움직이는 실행력이 느슨해지지 않도록 주의하세요."
  }
};

// ============================================================================
// [D] UI 제어 및 공통 만세력 코어 엔진
// ============================================================================
function showMsg(boxId, text) {
  const el = document.getElementById(boxId);
  if (!el) return;
  if (!text) {
    el.style.display = "none";
    el.textContent = "";
    return;
  }
  el.textContent = text;
  el.style.display = "block";
}

function switchTab(mode) {
  document.getElementById("tab-single").classList.toggle("active", mode === "single");
  document.getElementById("tab-compat").classList.toggle("active", mode === "compat");
  document.getElementById("view-single").style.display = mode === "single" ? "block" : "none";
  document.getElementById("view-compat").style.display = mode === "compat" ? "block" : "none";
}

function toggleLeap(radioName, labelId, checkId) {
  const isLunar = document.querySelector(`input[name="${radioName}"]:checked`).value === "lunar";
  document.getElementById(labelId).style.display = isLunar ? "flex" : "none";
  if (!isLunar) document.getElementById(checkId).checked = false;
}

function toggleTime(checkId, timeId) {
  document.getElementById(timeId).disabled = document.getElementById(checkId).checked;
}

function getSipseong(dayGanIdx, targetGanIdx) {
  const sameYinYang = GAN_YINYANG[dayGanIdx] === GAN_YINYANG[targetGanIdx];
  const dayOh = Math.floor(dayGanIdx / 2);
  const targetOh = Math.floor(targetGanIdx / 2);
  const diff = (targetOh - dayOh + 5) % 5;

  if (diff === 0) return sameYinYang ? "비견" : "겁재";
  if (diff === 1) return sameYinYang ? "식신" : "상관";
  if (diff === 2) return sameYinYang ? "편재" : "정재";
  if (diff === 3) return sameYinYang ? "편관" : "정관";
  if (diff === 4) return sameYinYang ? "편인" : "정인";
  return "";
}

function get12Unseong(dayGanIdx, jiIdx) {
  const isYang = GAN_YINYANG[dayGanIdx] === 1;
  const startJi = JANGSAENG_JI[dayGanIdx];
  const offset = isYang ? (jiIdx - startJi + 12) % 12 : (startJi - jiIdx + 12) % 12;
  return TWELVE_UNSEONG_NAMES[offset];
}

function calculateDaeunNumber(trueSolarDate, isForward) {
  const stepMs = (isForward ? 1 : -1) * 60 * 60 * 1000;
  const startLon = getSolarLongitudeKST(trueSolarDate);
  const startSector = Math.floor(((startLon - 315 + 360) % 360) / 30);

  let probe = new Date(trueSolarDate.getTime());
  for (let i = 0; i < 1200; i++) {
    probe = new Date(probe.getTime() + stepMs);
    const lon = getSolarLongitudeKST(probe);
    const sector = Math.floor(((lon - 315 + 360) % 360) / 30);
    if (sector !== startSector) {
      const diffDays = Math.abs(probe.getTime() - trueSolarDate.getTime()) / (24 * 60 * 60 * 1000);
      return Math.max(1, Math.min(10, Math.round(diffDays / 3)));
    }
  }
  return 5;
}

function computePersonSaju({ name, gender, calType, isLeap, birthDateVal, unknownTime, birthTimeVal, useTrueSolar }) {
  let [inYear, inMonth, inDay] = birthDateVal.split("-").map(Number);
  let [inHour, inMin] = unknownTime ? [12, 0] : (birthTimeVal || "12:00").split(":").map(Number);

  let solarY = inYear, solarM = inMonth, solarD = inDay;
  if (calType === "lunar") {
    const solar = convertLunarToSolar(inYear, inMonth, inDay, isLeap);
    if (!solar) return null;
    solarY = solar.year;
    solarM = solar.month;
    solarD = solar.day;
  }

  const rawDate = new Date(Date.UTC(solarY, solarM - 1, solarD, inHour, inMin));
  const offsetMin = useTrueSolar ? 30 : 0;
  const trueSolarDate = new Date(rawDate.getTime() - offsetMin * 60 * 1000);

  const lon = getSolarLongitudeKST(trueSolarDate);
  let sajuYear = trueSolarDate.getUTCFullYear();
  const tsMonth = trueSolarDate.getUTCMonth() + 1;
  if (tsMonth <= 2 && lon >= 270 && lon < 315) sajuYear -= 1;

  const adjustedLon = (lon - 315 + 360) % 360;
  const monthOrder = Math.floor(adjustedLon / 30);

  const yearGanIdx = (sajuYear - 4 + 10000) % 10;
  const yearJiIdx = (sajuYear - 4 + 12000) % 12;

  const monthJiIdx = (monthOrder + 2) % 12;
  const firstMonthGan = ((yearGanIdx % 5) * 2 + 2) % 10;
  const monthGanIdx = (firstMonthGan + monthOrder) % 10;

  const baseUTC = Date.UTC(1900, 0, 1);
  const targetDayUTC = Date.UTC(
    trueSolarDate.getUTCFullYear(),
    trueSolarDate.getUTCMonth(),
    trueSolarDate.getUTCDate()
  );
  const diffDays = Math.floor((targetDayUTC - baseUTC) / (24 * 60 * 60 * 1000));
  const dayGanIdx = (0 + diffDays + 100000) % 10;
  const dayJiIdx = (10 + diffDays + 120000) % 12;

  let hourPillar = null;
  if (!unknownTime) {
    const tsHour = trueSolarDate.getUTCHours();
    const hourJiIdx = Math.floor((tsHour + 1) / 2) % 12;
    const firstHourGan = ((dayGanIdx % 5) * 2) % 10;
    const hourGanIdx = (firstHourGan + hourJiIdx) % 10;
    hourPillar = { ganIdx: hourGanIdx, jiIdx: hourJiIdx };
  }

  const pillars = {
    year: { ganIdx: yearGanIdx, jiIdx: yearJiIdx },
    month: { ganIdx: monthGanIdx, jiIdx: monthJiIdx },
    day: { ganIdx: dayGanIdx, jiIdx: dayJiIdx },
    hour: hourPillar
  };

  const isYangYear = GAN_YINYANG[yearGanIdx] === 1;
  const isMale = gender === "남";
  const isForward = (isYangYear && isMale) || (!isYangYear && !isMale);
  const daeunStartAge = calculateDaeunNumber(trueSolarDate, isForward);

  const daeunList = [];
  for (let i = 1; i <= 8; i++) {
    const step = isForward ? i : -i;
    daeunList.push({
      age: daeunStartAge + (i - 1) * 10,
      ganIdx: (monthGanIdx + step + 100) % 10,
      jiIdx: (monthJiIdx + step + 120) % 12
    });
  }

  const scores = { "목": 0, "화": 0, "토": 0, "금": 0, "수": 0 };
  ["year", "month", "day", "hour"].forEach(key => {
    const p = pillars[key];
    if (!p) return;
    scores[GAN_OHAENG[p.ganIdx]] += 1.0;
    scores[JI_OHAENG[p.jiIdx]] += (key === "month" ? 2.5 : 1.0);
  });

  const totalScore = Object.values(scores).reduce((a, b) => a + b, 0);
  const ratios = {};
  Object.keys(scores).forEach(k => {
    ratios[k] = Number(((scores[k] / totalScore) * 100).toFixed(1));
  });

  const excessList = Object.keys(ratios).filter(k => ratios[k] >= 35);
  const lackingList = Object.keys(ratios).filter(k => ratios[k] <= 10);
  const weakestOhaeng = Object.keys(ratios).reduce((a, b) => ratios[a] < ratios[b] ? a : b);
  const strongestOhaeng = Object.keys(ratios).reduce((a, b) => ratios[a] > ratios[b] ? a : b);
  const currentKoreanAge = 2026 - solarY + 1;

  return {
    name, gender, solarY, solarM, solarD, trueSolarDate, unknownTime, useTrueSolar,
    pillars, dayGanIdx, ratios, excessList, lackingList, weakestOhaeng, strongestOhaeng,
    isForward, daeunList, currentKoreanAge
  };
}

// ============================================================================
// [E] 탭 1 실행: 개인 사주 & 기질 컬러 리포트
// ============================================================================
function runSingleAnalysis(shouldScroll = true) {
  showMsg("singleErrorMsg", "");
  showMsg("singleInfoMsg", "");
  const birthDateVal = document.getElementById("birthDate").value;
  if (!birthDateVal) {
    showMsg("singleErrorMsg", "생년월일을 입력해 주세요.");
    return;
  }

  const data = computePersonSaju({
    name: document.getElementById("userName").value.trim() || "사용자",
    gender: document.querySelector('input[name="gender"]:checked').value,
    calType: document.querySelector('input[name="calType"]:checked').value,
    isLeap: document.getElementById("isLeap").checked,
    birthDateVal,
    unknownTime: document.getElementById("unknownTime").checked,
    birthTimeVal: document.getElementById("birthTime").value,
    useTrueSolar: document.getElementById("useTrueSolarSingle").checked
  });

  if (!data) {
    showMsg("singleErrorMsg", "유효하지 않은 음력 날짜(1900~2100년 범위 및 윤달 여부)입니다. 날짜를 다시 확인해 주세요.");
    return;
  }

  const { name, gender, solarY, solarM, solarD, trueSolarDate, unknownTime, useTrueSolar,
          pillars, dayGanIdx, ratios, excessList, lackingList, weakestOhaeng, strongestOhaeng,
          isForward, daeunList, currentKoreanAge } = data;

  const dayGan = CHEONGAN[dayGanIdx];
  const dayJiIdx = pillars.day.jiIdx;
  const dayJi = JIJI[dayJiIdx];
  const iljuName = `${dayGan}${dayJi}일주`;
  const animalSymbol = `${GAN_COLOR_PREFIX[dayGanIdx]} ${JI_ANIMAL_NAME[dayJiIdx]}`;
  const iljiSipseong = getSipseong(dayGanIdx, JI_MAIN_GAN[dayJiIdx]);

  const tempColor = TEMPERAMENT_COLORS[dayGan];
  const balColor = BALANCE_COLORS[weakestOhaeng];
  const db = ILGAN_DB[dayGan];

  const pStr = ["year", "month", "day", "hour"].map(k => {
    const p = pillars[k];
    return p ? `${CHEONGAN[p.ganIdx]}${JIJI[p.jiIdx]}` : "미상";
  }).join("_");

  document.getElementById("hashBadge").textContent = `명식 코드: ${pStr}`;
  document.getElementById("animalBadge").textContent = `60갑자 물상: ${animalSymbol} (${iljuName})`;
  document.getElementById("personaTitle").textContent = `${name}님은 "${tempColor.persona}, ${iljuName}"입니다.`;

  const hh = String(trueSolarDate.getUTCHours()).padStart(2, "0");
  const mm = String(trueSolarDate.getUTCMinutes()).padStart(2, "0");
  const timeDisplay = unknownTime
    ? "시간 미상 (삼주 기반 정밀 분석)"
    : (useTrueSolar ? `진태양시 보정 ${hh}:${mm}` : `한국 표준시 ${hh}:${mm}`);

  document.getElementById("metaInfo").textContent =
    `양력 ${solarY}년 ${solarM}월 ${solarD}일 · ${gender}성 (2026년 기준 ${currentKoreanAge}세) · ${timeDisplay}`;

  document.getElementById("overallSummary").textContent =
    `${name}님은 '${tempColor.name}(${dayGan}일간)'의 본질 에너지를 지닌 '${animalSymbol}' 상으로, 내면에는 ${ILJI_INNER_TRAIT[dayJi]} 전체 오행 중 '${strongestOhaeng}' 기운이 주도적이며 '${weakestOhaeng}' 기운을 보완할 때 삶의 균형이 극대화됩니다.`;

  document.getElementById("tempSwatch").style.backgroundColor = tempColor.hex;
  document.getElementById("tempColorName").textContent = tempColor.name;
  document.getElementById("tempColorKeyword").textContent = tempColor.keyword;

  document.getElementById("balSwatch").style.backgroundColor = balColor.hex;
  document.getElementById("balColorName").textContent = `${balColor.name} (${weakestOhaeng} 기운 보충)`;
  document.getElementById("balColorDesc").textContent = balColor.desc;

  document.getElementById("therapyGuideGrid").innerHTML = `
    <div class="therapy-card">
      <div class="therapy-card-header">
        <span class="mini-dot" style="background:${tempColor.hex};"></span>
        <h5>본질 컬러 라이프스타일 가이드 (${tempColor.name})</h5>
      </div>
      <ul class="therapy-list">
        <li><strong>패션 포인트:</strong> ${tempColor.fashion}</li>
        <li><strong>공간 인테리어:</strong> ${tempColor.interior}</li>
        <li><strong>추천 아로마 노트:</strong> ${tempColor.aroma}</li>
      </ul>
    </div>
    <div class="therapy-card">
      <div class="therapy-card-header">
        <span class="mini-dot" style="background:${balColor.hex};"></span>
        <h5>개운 컬러 에너지 충전 가이드 (${balColor.name})</h5>
      </div>
      <ul class="therapy-list">
        <li><strong>패션 포인트:</strong> ${balColor.fashion}</li>
        <li><strong>공간 인테리어:</strong> ${balColor.interior}</li>
        <li><strong>추천 아로마 노트:</strong> ${balColor.aroma}</li>
      </ul>
    </div>
  `;

  const order = ["hour", "day", "month", "year"];
  let rowGanSipseong = `<tr><td><strong>천간 십성</strong></td>`;
  let rowGanChar = `<tr><td><strong>천간 (天干)</strong></td>`;
  let rowJiChar = `<tr><td><strong>지지 (地支)</strong></td>`;
  let rowJiSipseong = `<tr><td><strong>지지 십성</strong></td>`;
  let row12Unseong = `<tr><td><strong>12운성</strong></td>`;

  order.forEach(key => {
    const p = pillars[key];
    if (!p) {
      rowGanSipseong += `<td><span class="sipseong-tag">미상</span></td>`;
      rowGanChar += `<td style="color:#94a3b8;">-<br><span class="kor-char">시간 미상</span></td>`;
      rowJiChar += `<td style="color:#94a3b8;">-<br><span class="kor-char">시간 미상</span></td>`;
      rowJiSipseong += `<td><span class="sipseong-tag">미상</span></td>`;
      row12Unseong += `<td>-</td>`;
      return;
    }
    const gOh = GAN_OHAENG[p.ganIdx];
    const jOh = JI_OHAENG[p.jiIdx];
    const gSip = key === "day" ? "본원(일간)" : getSipseong(dayGanIdx, p.ganIdx);
    const jSip = getSipseong(dayGanIdx, JI_MAIN_GAN[p.jiIdx]);
    const unseong = get12Unseong(dayGanIdx, p.jiIdx);

    rowGanSipseong += `<td><span class="sipseong-tag">${gSip}</span></td>`;
    rowGanChar += `<td><span class="hanja-char c-${gOh}">${CHEONGAN_HANJA[p.ganIdx]}</span><span class="kor-char">${CHEONGAN[p.ganIdx]} (${gOh})</span></td>`;
    rowJiChar += `<td><span class="hanja-char c-${jOh}">${JIJI_HANJA[p.jiIdx]}</span><span class="kor-char">${JIJI[p.jiIdx]} (${jOh})</span></td>`;
    rowJiSipseong += `<td><span class="sipseong-tag">${jSip}</span></td>`;
    row12Unseong += `<td style="font-size:0.84rem; font-weight:600;">${unseong}</td>`;
  });

  document.getElementById("pillarsBody").innerHTML =
    rowGanSipseong + "</tr>" +
    rowGanChar + "</tr>" +
    rowJiChar + "</tr>" +
    rowJiSipseong + "</tr>" +
    row12Unseong + "</tr>";

  document.getElementById("daeunDirectionBadge").textContent =
    `${isForward ? "순행(順行)" : "역행(逆行)"} · ${daeunList[0].age}세 대운수`;

  let daeunHTML = "";
  let activeDaeunObj = daeunList[0];
  daeunList.forEach((d, idx) => {
    const nextAge = idx < daeunList.length - 1 ? daeunList[idx + 1].age : d.age + 10;
    const isCurrent = currentKoreanAge >= d.age && currentKoreanAge < nextAge;
    if (isCurrent) activeDaeunObj = d;

    const gOh = GAN_OHAENG[d.ganIdx];
    const jOh = JI_OHAENG[d.jiIdx];
    const gSip = getSipseong(dayGanIdx, d.ganIdx);
    const jSip = getSipseong(dayGanIdx, JI_MAIN_GAN[d.jiIdx]);

    daeunHTML += `
      <div class="daeun-cell ${isCurrent ? "active-daeun" : ""}">
        <div class="daeun-age">${d.age}세${isCurrent ? " (현재)" : ""}</div>
        <div class="daeun-ganji">
          <span class="c-${gOh}">${CHEONGAN_HANJA[d.ganIdx]}</span><span class="c-${jOh}">${JIJI_HANJA[d.jiIdx]}</span>
          <div style="font-size:0.78rem; color:#334155;">${CHEONGAN[d.ganIdx]}${JIJI[d.jiIdx]}</div>
        </div>
        <div class="daeun-sip">${gSip}·${jSip}</div>
      </div>
    `;
  });
  document.getElementById("daeunTimeline").innerHTML = daeunHTML;

  const seun2026GanSip = getSipseong(dayGanIdx, 2);
  const seun2026JiSip = getSipseong(dayGanIdx, JI_MAIN_GAN[6]);
  const s26 = SEUN_YEAR_DETAIL[seun2026GanSip];

  const seun2027GanSip = getSipseong(dayGanIdx, 3);
  const seun2027JiSip = getSipseong(dayGanIdx, JI_MAIN_GAN[7]);
  const s27 = SEUN_YEAR_DETAIL[seun2027GanSip];

  const curDaeunStr = `${CHEONGAN[activeDaeunObj.ganIdx]}${JIJI[activeDaeunObj.jiIdx]}대운(${activeDaeunObj.age}세~)`;

  document.getElementById("seun2026Box").innerHTML = `
    <div class="seun-header">
      <h4>2026년 병오년 (丙午年 · 붉은 말)</h4>
      <span class="seun-badge">${seun2026GanSip} · ${seun2026JiSip}운</span>
    </div>
    <ul class="seun-list">
      <li><strong>핵심 테마:</strong> ${s26.theme} (현재 ${curDaeunStr} 흐름과 결합)</li>
      <li><strong>전반적 흐름:</strong> ${s26.flow}</li>
      <li><strong>재물·커리어 전략:</strong> ${s26.action}</li>
      <li><strong>주의할 변수:</strong> ${s26.caution}</li>
    </ul>
  `;

  document.getElementById("seun2027Box").innerHTML = `
    <div class="seun-header">
      <h4>2027년 정미년 (丁未年 · 붉은 양)</h4>
      <span class="seun-badge">${seun2027GanSip} · ${seun2027JiSip}운</span>
    </div>
    <ul class="seun-list">
      <li><strong>핵심 테마:</strong> ${s27.theme} (2026년의 열기를 결실로 다듬는 해)</li>
      <li><strong>전반적 흐름:</strong> ${s27.flow}</li>
      <li><strong>재물·커리어 전략:</strong> ${s27.action}</li>
      <li><strong>주의할 변수:</strong> ${s27.caution}</li>
    </ul>
  `;

  const ohaengMeta = [
    { key: "목", label: "목 (木)", color: "var(--wood)" },
    { key: "화", label: "화 (火)", color: "var(--fire)" },
    { key: "토", label: "토 (土)", color: "var(--earth)" },
    { key: "금", label: "금 (金)", color: "var(--metal)" },
    { key: "수", label: "수 (水)", color: "var(--water)" }
  ];

  document.getElementById("ohaengBars").innerHTML = ohaengMeta.map(item => `
    <div class="ohaeng-row">
      <div class="ohaeng-label c-${item.key}">${item.label}</div>
      <div class="bar-bg"><div class="bar-fill" style="width:${ratios[item.key]}%; background:${item.color};"></div></div>
      <div class="ohaeng-pct">${ratios[item.key]}%</div>
    </div>
  `).join("");

  const excessText = excessList.length > 0 ? `<strong>${excessList.join(", ")}</strong> 기운이 강하게 발달해 있으며` : "특정 오행으로의 극단적 치우침 없이 고른 편이며";
  const lackingText = lackingList.length > 0 ? `<strong>${lackingList.join(", ")}</strong> 기운이 부족(10% 이하)합니다.` : `상대적으로 <strong>${weakestOhaeng}</strong> 기운을 보강하면 더욱 좋습니다.`;
  document.getElementById("ohaengSummaryText").innerHTML =
    `계절(월지) 가중치를 반영한 결과, ${excessText} ${lackingText} 부족한 <strong>${weakestOhaeng}</strong> 기운을 채우기 위해 <strong>${balColor.name}</strong> 계열의 컬러와 소품을 가까이 두는 것을 권장합니다.`;

  const details = [
    { title: `1. 타고난 기질 및 성향 (${iljuName} · ${animalSymbol})`, content: `${db.temperament}\n\n[일지 '${dayJi}' 심층 내면 성향] ${ILJI_INNER_TRAIT[dayJi]}` },
    { title: "2. 핵심 강점과 무기", content: db.strength },
    { title: "3. 보완점 및 리스크 관리 패턴", content: db.weakness },
    { title: "4. 맞춤 성장 코칭 및 컬러 루틴", content: `${db.coaching}\n\n[오행 밸런스 처방] 현재 명식에서 가장 시급히 보충해야 할 '${weakestOhaeng}' 에너지를 채우기 위해 '${balColor.name}' 컬러의 소품·패션·데스크 아이템을 일상적으로 활용하고, 과다하게 발달한 '${strongestOhaeng}' 에너지는 운동·창작·아웃풋 활동으로 건설적으로 순환시키세요.` },
    { title: "5. 남들이 보는 나 (외적 이미지와 첫인상)", content: db.externalView },
    { title: "6. 인간관계 및 합이 잘 맞는 사람", content: db.compatibility },
    { title: "7. 재물운 및 자산 증식 전략", content: `${db.wealth}\n\n[일주 성취·재물 작동 원리] ${ILJI_SIPSEONG_MOD[iljiSipseong]}` },
    { title: "8. 연애운 및 이상적인 파트너십", content: db.love },
    { title: "9. 직업운 및 최적의 적성 분야", content: db.career },
    { title: "10. 건강운 및 체질 에너지 관리법", content: db.health }
  ];

  document.getElementById("detailGrid").innerHTML = details.map(d => `
    <div class="analysis-item">
      <h3>${d.title}</h3>
      <p>${d.content}</p>
    </div>
  `).join("");

  const pillarSummaryStr = ["year", "month", "day", "hour"].map(k => {
    const labelMap = { year: "년주", month: "월주", day: "일주", hour: "시주" };
    const p = pillars[k];
    return `${labelMap[k]}: ${p ? CHEONGAN[p.ganIdx] + JIJI[p.jiIdx] + "(" + CHEONGAN_HANJA[p.ganIdx] + JIJI_HANJA[p.jiIdx] + ")" : "미상"}`;
  }).join(" / ");

  const ohaengRatioStr = ohaengMeta.map(m => `${m.key} ${ratios[m.key]}%`).join(" · ");

  document.getElementById("finalSummaryBadge").textContent = `${name}님 마스터 요약표`;
  document.getElementById("finalSummaryLead").textContent =
    `${name}님은 '${tempColor.persona}(${iljuName} · ${animalSymbol})'의 기질을 타고났으며, 본질 컬러인 '${tempColor.name}'의 강점을 살리면서 개운 컬러인 '${balColor.name}'으로 부족한 '${weakestOhaeng}' 에너지를 채울 때 최고의 운세 흐름을 만듭니다.`;

  document.getElementById("finalSummaryTableBody").innerHTML = `
    <tr><th>기본 명식 (4기둥)</th><td>${pillarSummaryStr}</td></tr>
    <tr><th>기질 &amp; 개운 컬러</th><td><strong>본질 컬러:</strong> ${tempColor.name} (${tempColor.keyword})<br><strong>보완 컬러:</strong> ${balColor.name} (${weakestOhaeng} 기운 보충)</td></tr>
    <tr><th>오감 테라피 포인트</th><td><strong>패션:</strong> ${tempColor.fashion}<br><strong>향기 노트:</strong> ${tempColor.aroma}</td></tr>
    <tr><th>오행 에너지 밸런스</th><td>${ohaengRatioStr}<br>→ <strong>주도 기운:</strong> ${strongestOhaeng} (${ratios[strongestOhaeng]}%) / <strong>보완 필요:</strong> ${weakestOhaeng} (${ratios[weakestOhaeng]}%)</td></tr>
    <tr><th>핵심 강점 &amp; 코칭</th><td>${db.strength} → <em>${s26.theme}</em> 방향으로 실행력을 집중하세요.</td></tr>
    <tr><th>재물 · 직업 핵심</th><td><strong>적성:</strong> ${db.career}<br><strong>재물 전략:</strong> ${ILJI_SIPSEONG_MOD[iljiSipseong]}</td></tr>
    <tr><th>연애 · 궁합 포인트</th><td>${db.compatibility}</td></tr>
    <tr><th>건강 관리 핵심</th><td>${db.health}</td></tr>
    <tr><th>2026 병오년 전략</th><td><strong>[${seun2026GanSip}·${seun2026JiSip}운]</strong> ${s26.theme} — ${s26.action}</td></tr>
    <tr><th>2027 정미년 전략</th><td><strong>[${seun2027GanSip}·${seun2027JiSip}운]</strong> ${s27.theme} — ${s27.action}</td></tr>
  `;

  document.getElementById("single-report-area").style.display = "block";
  if (shouldScroll) {
    document.getElementById("single-report-area").scrollIntoView({ behavior: "smooth" });
  }
}

// ============================================================================
// [F] 탭 2 실행: 두 사람 궁합 점수 & 컬러 시너지 계산 엔진
// ============================================================================
function evaluateCheonganCompat(g1, g2) {
  if (Math.abs(g1 - g2) === 5) {
    return {
      score: 98,
      label: "천간합 (天干合 · 운명적 끌림)",
      desc: `${CHEONGAN[g1]}일간과 ${CHEONGAN[g2]}일간이 만나 하나의 새로운 기운으로 융합되는 최상의 정신적 합입니다. 서로의 부족한 사고방식을 본능적으로 채워주며 가치관의 결이 자연스럽게 맞아떨어집니다.`
    };
  }
  const oh1 = Math.floor(g1 / 2);
  const oh2 = Math.floor(g2 / 2);
  const diff = (oh2 - oh1 + 5) % 5;

  if (diff === 1 || diff === 4) {
    const giver = diff === 1 ? CHEONGAN[g1] : CHEONGAN[g2];
    const receiver = diff === 1 ? CHEONGAN[g2] : CHEONGAN[g1];
    return {
      score: 88,
      label: "상생 관계 (相生 · 아낌없는 지원)",
      desc: `${giver}의 에너지가 ${receiver}의 성장을 자연스럽게 밀어주는 상생 구조입니다. 대화가 막힘없이 흐르고 함께 있을수록 서로의 잠재력이 살아나는 건강한 파트너십입니다.`
    };
  }
  if (diff === 0) {
    return {
      score: 82,
      label: "비화 관계 (比和 · 친구 같은 동반자)",
      desc: `같은 오행(${GAN_OHAENG[g1]})의 성향을 공유해 설명하지 않아도 서로의 감정과 행동 패턴을 잘 이해합니다. 친구처럼 편안하지만, 고집을 부릴 때는 한 발씩 양보하는 지혜가 필요합니다.`
    };
  }
  return {
    score: 72,
    label: "상극 자극 (相剋 · 다름에서 오는 성장)",
    desc: `서로 다른 기질(${GAN_OHAENG[g1]} vs ${GAN_OHAENG[g2]})이 만나 처음에는 강한 호기심과 긴장감을 동시에 느낍니다. 내 방식을 강요하기보다 '다름의 역할 분담'을 명확히 하면 서로의 약점을 보완하는 단단한 팀이 됩니다.`
  };
}

function evaluateJijiCompat(j1, j2) {
  const yukHapPairs = [[0,1], [2,11], [3,10], [4,9], [5,8], [6,7]];
  const isYukHap = yukHapPairs.some(([a, b]) => (j1 === a && j2 === b) || (j1 === b && j2 === a));
  if (isYukHap) {
    return {
      score: 96,
      label: "일지 육합 (六合 · 찰떡 속궁합·생활 호흡)",
      desc: `배우자 궁인 일지(${JIJI[j1]}·${JIJI[j2]})가 육합으로 단단히 결속되어 일상생활의 리듬과 정서적 안정감이 매우 뛰어납니다. 함께 있을 때 마음이 가장 편안해지는 인연입니다.`
    };
  }

  const samHapGroups = [[8,0,4], [11,3,7], [2,6,10], [5,9,1]];
  const isSamHap = j1 !== j2 && samHapGroups.some(grp => grp.includes(j1) && grp.includes(j2));
  if (isSamHap) {
    return {
      score: 92,
      label: "일지 삼합 (三合 · 공동 목표와 시너지)",
      desc: `두 사람의 일지(${JIJI[j1]}·${JIJI[j2]})가 같은 목표를 향해 힘을 합치는 삼합의 기운을 띱니다. 연애는 물론 함께 일하거나 미래를 설계할 때 추진력이 배가 됩니다.`
    };
  }

  if (Math.abs(j1 - j2) === 6) {
    return {
      score: 68,
      label: "일지 충 (沖 · 역동적 변화와 조율 필요)",
      desc: `일지(${JIJI[j1]}·${JIJI[j2]})가 정면으로 마주 보는 충 관계로, 첫눈에 강렬하게 끌리지만 생활 습관이나 감정 표현 방식에서 부딪힘이 생길 수 있습니다. 서로의 개인 시간을 존중할 때 갈등이 예방됩니다.`
    };
  }

  return {
    score: 80,
    label: "안정적 조화 (無難 · 무리 없는 일상 호흡)",
    desc: `일지(${JIJI[j1]}·${JIJI[j2]}) 사이에 큰 충돌 없이 서로의 영역을 자연스럽게 존중하는 안정적인 흐름입니다. 함께 취미나 루틴을 만들어갈수록 유대감이 깊어집니다.`
  };
}

function evaluateOhaengSynergy(p1, p2) {
  const p2SupplyForP1 = p2.ratios[p1.weakestOhaeng] || 0;
  const p1SupplyForP2 = p1.ratios[p2.weakestOhaeng] || 0;
  const avgSupply = (p2SupplyForP1 + p1SupplyForP2) / 2;

  const rawScore = Math.min(99, Math.max(65, Math.round(65 + avgSupply * 1.1)));

  let label = "균형 보완형";
  if (rawScore >= 90) label = "최상의 용신 보완 (상호 충전)";
  else if (rawScore >= 80) label = "우수한 에너지 밸런스";

  const desc = `${p1.name}님에게 가장 필요한 '${p1.weakestOhaeng}' 기운을 ${p2.name}님이 ${p2SupplyForP1}% 보유하고 있으며, 반대로 ${p2.name}님에게 부족한 '${p2.weakestOhaeng}' 기운을 ${p1.name}님이 ${p1SupplyForP2}% 채워줍니다. 두 사람이 함께하면 각자 혼자일 때보다 오행의 빈틈이 메워져 심리적 안정감과 현실적 실행력이 함께 올라갑니다.`;

  return { score: rawScore, label, desc };
}

function runCompatAnalysis(shouldScroll = true) {
  showMsg("compatErrorMsg", "");
  showMsg("compatInfoMsg", "");
  const d1Val = document.getElementById("p1Date").value;
  const d2Val = document.getElementById("p2Date").value;
  if (!d1Val || !d2Val) {
    showMsg("compatErrorMsg", "두 사람의 생년월일을 모두 입력해 주세요.");
    return;
  }

  const useTrueSolar = document.getElementById("useTrueSolarCompat").checked;
  const p1 = computePersonSaju({
    name: document.getElementById("p1Name").value.trim() || "첫 번째 사람",
    gender: document.querySelector('input[name="p1Gender"]:checked').value,
    calType: document.querySelector('input[name="p1Cal"]:checked').value,
    isLeap: document.getElementById("p1Leap").checked,
    birthDateVal: d1Val,
    unknownTime: document.getElementById("p1Unknown").checked,
    birthTimeVal: document.getElementById("p1Time").value,
    useTrueSolar
  });

  const p2 = computePersonSaju({
    name: document.getElementById("p2Name").value.trim() || "두 번째 사람",
    gender: document.querySelector('input[name="p2Gender"]:checked').value,
    calType: document.querySelector('input[name="p2Cal"]:checked').value,
    isLeap: document.getElementById("p2Leap").checked,
    birthDateVal: d2Val,
    unknownTime: document.getElementById("p2Unknown").checked,
    birthTimeVal: document.getElementById("p2Time").value,
    useTrueSolar
  });

  if (!p1 || !p2) {
    showMsg("compatErrorMsg", "음력 날짜 입력이 올바르지 않습니다. 연·월·일 및 윤달 여부를 확인해 주세요.");
    return;
  }

  const ganRes = evaluateCheonganCompat(p1.dayGanIdx, p2.dayGanIdx);
  const jiRes = evaluateJijiCompat(p1.pillars.day.jiIdx, p2.pillars.day.jiIdx);
  const ohRes = evaluateOhaengSynergy(p1, p2);

  const totalScore = Math.round(ganRes.score * 0.35 + jiRes.score * 0.35 + ohRes.score * 0.30);

  const p1Ilju = `${CHEONGAN[p1.dayGanIdx]}${JIJI[p1.pillars.day.jiIdx]}일주`;
  const p2Ilju = `${CHEONGAN[p2.dayGanIdx]}${JIJI[p2.pillars.day.jiIdx]}일주`;
  const p1Animal = `${GAN_COLOR_PREFIX[p1.dayGanIdx]} ${JI_ANIMAL_NAME[p1.pillars.day.jiIdx]}`;
  const p2Animal = `${GAN_COLOR_PREFIX[p2.dayGanIdx]} ${JI_ANIMAL_NAME[p2.pillars.day.jiIdx]}`;

  document.getElementById("compatPairBadge").textContent = `${p1.name}(${p1Ilju}) × ${p2.name}(${p2Ilju})`;
  document.getElementById("compatHeadline").textContent =
    `${p1.name}님과 ${p2.name}님의 종합 시너지는 ${totalScore}점입니다.`;
  document.getElementById("compatSubSummary").textContent =
    `'${p1Animal}' 기질과 '${p2Animal}' 기질의 만남으로, 정신적 교감(${ganRes.score}점)과 현실 호흡(${jiRes.score}점), 에너지 상호 보완(${ohRes.score}점)이 어우러진 관계입니다.`;
  document.getElementById("totalCompatScore").textContent = `${totalScore}점`;

  document.getElementById("ganScoreVal").textContent = `${ganRes.score}점`;
  document.getElementById("ganRelLabel").textContent = ganRes.label;
  document.getElementById("jiScoreVal").textContent = `${jiRes.score}점`;
  document.getElementById("jiRelLabel").textContent = jiRes.label;
  document.getElementById("ohScoreVal").textContent = `${ohRes.score}점`;
  document.getElementById("ohRelLabel").textContent = ohRes.label;

  const c1 = TEMPERAMENT_COLORS[CHEONGAN[p1.dayGanIdx]];
  const c2 = TEMPERAMENT_COLORS[CHEONGAN[p2.dayGanIdx]];
  document.getElementById("cSwatch1").style.backgroundColor = c1.hex;
  document.getElementById("cTitle1").textContent = `${p1.name}님의 본질 컬러`;
  document.getElementById("cName1").textContent = c1.name;
  document.getElementById("cDesc1").textContent = `${c1.keyword} (부족 오행: ${p1.weakestOhaeng})`;

  document.getElementById("cSwatch2").style.backgroundColor = c2.hex;
  document.getElementById("cTitle2").textContent = `${p2.name}님의 본질 컬러`;
  document.getElementById("cName2").textContent = c2.name;
  document.getElementById("cDesc2").textContent = `${c2.keyword} (부족 오행: ${p2.weakestOhaeng})`;

  document.getElementById("thP1").textContent = `${p1.name} (${p1.gender})`;
  document.getElementById("thP2").textContent = `${p2.name} (${p2.gender})`;

  const fmtP = (p) => p ? `${CHEONGAN_HANJA[p.ganIdx]}${JIJI_HANJA[p.jiIdx]} (${CHEONGAN[p.ganIdx]}${JIJI[p.jiIdx]})` : "시간 미상";
  document.getElementById("compatCompareBody").innerHTML = `
    <tr><td><strong>일주 (본질·배우자궁)</strong></td><td><strong>${fmtP(p1.pillars.day)}</strong></td><td><strong>${fmtP(p2.pillars.day)}</strong></td></tr>
    <tr><td><strong>월주 (사회성·환경)</strong></td><td>${fmtP(p1.pillars.month)}</td><td>${fmtP(p2.pillars.month)}</td></tr>
    <tr><td><strong>년주 (초년·가풍)</strong></td><td>${fmtP(p1.pillars.year)}</td><td>${fmtP(p2.pillars.year)}</td></tr>
    <tr><td><strong>시주 (말년·내면)</strong></td><td>${fmtP(p1.pillars.hour)}</td><td>${fmtP(p2.pillars.hour)}</td></tr>
    <tr><td><strong>가장 강한 오행</strong></td><td>${p1.strongestOhaeng} (${p1.ratios[p1.strongestOhaeng]}%)</td><td>${p2.strongestOhaeng} (${p2.ratios[p2.strongestOhaeng]}%)</td></tr>
    <tr><td><strong>보완 필요 오행</strong></td><td>${p1.weakestOhaeng} (${p1.ratios[p1.weakestOhaeng]}%)</td><td>${p2.weakestOhaeng} (${p2.ratios[p2.weakestOhaeng]}%)</td></tr>
  `;

  const compatDetails = [
    {
      title: "1. 정신적 교감 및 가치관 호흡 (천간 분석)",
      content: `${ganRes.desc}\n\n[대화 및 의사소통 팁] ${p1.name}님은 '${c1.keyword}'의 관점으로 사안을 바라보고, ${p2.name}님은 '${c2.keyword}'의 방식으로 반응합니다. 중요한 결정을 내릴 때는 서로의 핵심 키워드를 먼저 인정해 주는 대화가 신뢰를 두 배로 높입니다.`
    },
    {
      title: "2. 일상생활 및 속마음 케미스트리 (일지 분석)",
      content: `${jiRes.desc}\n\n[갈등 예방 및 조율법] ${p1.name}님의 내면은 ${ILJI_INNER_TRAIT[JIJI[p1.pillars.day.jiIdx]]} 반면 ${p2.name}님의 내면은 ${ILJI_INNER_TRAIT[JIJI[p2.pillars.day.jiIdx]]} 서로의 휴식 방식과 감정 정리 속도가 다름을 이해하면 사소한 오해가 눈 녹듯 사라집니다.`
    },
    {
      title: "3. 부족한 에너지를 채워주는 오행 시너지",
      content: ohRes.desc
    },
    {
      title: "4. 두 사람의 컬러 테라피 & 2026~2027년 협업·데이트 가이드",
      content: `${p1.name}님의 '${c1.name}' 에너지와 ${p2.name}님의 '${c2.name}' 에너지가 만났습니다. 두 사람 모두에게 시너지를 주는 공통 개운 컬러는 '${BALANCE_COLORS[p1.weakestOhaeng].name}'와 '${BALANCE_COLORS[p2.weakestOhaeng].name}'입니다.\n\n[2026 병오년 · 2027 정미년 관계 흐름] 화(火)·토(土) 에너지가 강해지는 2026~2027년에는 두 사람이 함께 새로운 공동 목표(여행, 재테크 계획, 공동 프로젝트)를 세워 추진할 때 결속력이 크게 강해집니다. 감정이 뜨거워질 때는 물(수·水)의 여유를 상징하는 조용한 카페나 물가 산책 데이트가 최고의 윤활유가 됩니다.`
    }
  ];

  document.getElementById("compatDetailGrid").innerHTML = compatDetails.map(d => `
    <div class="analysis-item">
      <h3>${d.title}</h3>
      <p>${d.content}</p>
    </div>
  `).join("");

  document.getElementById("compatFinalBadge").textContent = `${p1.name} × ${p2.name} 마스터 요약`;
  document.getElementById("compatFinalSummaryBody").innerHTML = `
    <tr><th>두 사람 일주 조합</th><td>${p1.name} (${p1Ilju} · ${p1Animal}) × ${p2.name} (${p2Ilju} · ${p2Animal})</td></tr>
    <tr><th>종합 시너지 점수</th><td><strong>${totalScore}점</strong> (천간 교감 ${ganRes.score}점 · 일지 호흡 ${jiRes.score}점 · 오행 보완 ${ohRes.score}점)</td></tr>
    <tr><th>본질 컬러 매칭</th><td>${p1.name}: <strong>${c1.name}</strong> / ${p2.name}: <strong>${c2.name}</strong></td></tr>
    <tr><th>공통 행운 컬러</th><td>${BALANCE_COLORS[p1.weakestOhaeng].name} (${p1.weakestOhaeng} 보충) &amp; ${BALANCE_COLORS[p2.weakestOhaeng].name} (${p2.weakestOhaeng} 보충)</td></tr>
    <tr><th>핵심 시너지 요약</th><td>${ganRes.label} + ${jiRes.label} 구조로, 서로의 부족한 오행을 자연스럽게 채워주는 건설적인 파트너십입니다.</td></tr>
  `;

  document.getElementById("compat-report-area").style.display = "block";
  if (shouldScroll) {
    document.getElementById("compat-report-area").scrollIntoView({ behavior: "smooth" });
  }
}

// ============================================================================
// [G] 순수 자바스크립트 내장 고해상도 DOM -> Canvas -> PDF 1.4 바이너리 & PNG 생성 엔진
//     (외부 CDN 차단 및 iframe 샌드박스 인쇄 제한 완벽 해결)
// ============================================================================
function getExportFileName(captureId, ext) {
  if (captureId === "single-capture") {
    const uName = (document.getElementById("userName").value.trim() || "사용자").replace(/\s+/g, "_");
    return `사주&컬러코드_${uName}_리포트.${ext}`;
  }
  const n1 = (document.getElementById("p1Name").value.trim() || "나").replace(/\s+/g, "_");
  const n2 = (document.getElementById("p2Name").value.trim() || "상대방").replace(/\s+/g, "_");
  return `사주&컬러코드_궁합_${n1}_${n2}_리포트.${ext}`;
}

// DOM 요소를 SVG foreignObject로 직렬화하여 고배율 Canvas로 변환
async function renderElementToCanvas(captureId) {
  const sourceEl = document.getElementById(captureId);
  const clone = sourceEl.cloneNode(true);
  clone.style.width = "820px";
  clone.style.padding = "20px";
  clone.style.background = "#ffffff";
  clone.style.margin = "0";

  // 인라인 스타일 강제 적용 (SVG foreignObject 렌더링 정확도 보장)
  const styleBlock = document.createElement("style");
  let allCss = "";
  for (const sheet of document.styleSheets) {
    try {
      for (const rule of sheet.cssRules) {
        allCss += rule.cssText + "\n";
      }
    } catch (e) {}
  }
  styleBlock.textContent = allCss + `
    * { box-sizing: border-box; }
    body { margin: 0; padding: 0; background: #ffffff; font-family: -apple-system, BlinkMacSystemFont, "Pretendard", "Malgun Gothic", sans-serif; }
    .card { box-shadow: none !important; border: 1px solid #cbd5e1 !important; background: #ffffff !important; }
    .daeun-scroll, .table-wrap { overflow: visible !important; }
  `;

  // 정확한 높이 측정을 위해 화면 밖 임시 호스트에 잠깐 부착
  const measureHost = document.createElement("div");
  measureHost.style.position = "fixed";
  measureHost.style.left = "-9999px";
  measureHost.style.top = "0";
  measureHost.style.width = "820px";
  measureHost.style.background = "#ffffff";
  measureHost.appendChild(clone);
  document.body.appendChild(measureHost);

  const width = 820;
  const height = Math.ceil(clone.scrollHeight) + 24;
  document.body.removeChild(measureHost);

  const wrapper = document.createElement("div");
  wrapper.setAttribute("xmlns", "http://www.w3.org/1999/xhtml");
  wrapper.style.width = width + "px";
  wrapper.style.height = height + "px";
  wrapper.style.background = "#ffffff";
  wrapper.appendChild(styleBlock);
  wrapper.appendChild(clone);

  const serializedHTML = new XMLSerializer().serializeToString(wrapper);
  const svgStr = `
    <svg xmlns="http://www.w3.org/2000/svg" width="${width}" height="${height}">
      <foreignObject width="100%" height="100%">
        ${serializedHTML}
      </foreignObject>
    </svg>
  `;

  const svgDataUrl = "data:image/svg+xml;charset=utf-8," + encodeURIComponent(svgStr);

  return new Promise((resolve, reject) => {
    const img = new Image();
    img.onload = () => {
      const scale = 1.8;
      const canvas = document.createElement("canvas");
      canvas.width = Math.floor(width * scale);
      canvas.height = Math.floor(height * scale);
      const ctx = canvas.getContext("2d");
      ctx.fillStyle = "#ffffff";
      ctx.fillRect(0, 0, canvas.width, canvas.height);
      ctx.scale(scale, scale);
      ctx.drawImage(img, 0, 0);
      resolve(canvas);
    };
    img.onerror = (err) => reject(err);
    img.src = svgDataUrl;
  });
}

// 여러 페이지(A4 비율)로 분할된 JPEG 배열로부터 순수 PDF 1.4 바이너리 Uint8Array 생성
function buildMultiPagePdfBinary(jpegPages) {
  const encoder = new TextEncoder();
  const chunks = [];
  let byteLength = 0;

  function pushStr(str) {
    const bytes = encoder.encode(str);
    chunks.push(bytes);
    byteLength += bytes.length;
  }
  function pushBytes(uint8) {
    chunks.push(uint8);
    byteLength += uint8.length;
  }

  const offsets = [0]; // obj 0 placeholder
  function startObj(objNum) {
    offsets[objNum] = byteLength;
    pushStr(`${objNum} 0 obj\n`);
  }
  function endObj() {
    pushStr(`endobj\n`);
  }

  pushStr("%PDF-1.4\n%\xE2\xE3\xCF\xD3\n");

  // Obj 1: Catalog, Obj 2: Pages
  const pageCount = jpegPages.length;
  const pageObjNums = [];
  for (let i = 0; i < pageCount; i++) {
    pageObjNums.push(3 + i * 3);
  }

  startObj(1);
  pushStr(`<< /Type /Catalog /Pages 2 0 R >>\n`);
  endObj();

  startObj(2);
  pushStr(`<< /Type /Pages /Kids [${pageObjNums.map(n => `${n} 0 R`).join(" ")}] /Count ${pageCount} >>\n`);
  endObj();

  // 각 페이지마다 Page Obj(3+3i), Content Stream Obj(4+3i), Image XObject Obj(5+3i) 생성
  const a4W = 595.28;
  const a4H = 841.89;

  for (let i = 0; i < pageCount; i++) {
    const p = jpegPages[i];
    const pageObj = 3 + i * 3;
    const contentObj = 4 + i * 3;
    const imgObj = 5 + i * 3;

    const drawW = a4W - 36; // 좌우 18pt 여백
    const drawH = (p.height / p.width) * drawW;
    const posX = 18;
    const posY = a4H - 18 - drawH;

    startObj(pageObj);
    pushStr(`<< /Type /Page /Parent 2 0 R /MediaBox [0 0 ${a4W} ${a4H}] /Resources << /XObject << /Im${i} ${imgObj} 0 R >> >> /Contents ${contentObj} 0 R >>\n`);
    endObj();

    const contentStream = `q\n${drawW.toFixed(2)} 0 0 ${drawH.toFixed(2)} ${posX.toFixed(2)} ${posY.toFixed(2)} cm\n/Im${i} Do\nQ\n`;
    startObj(contentObj);
    pushStr(`<< /Length ${contentStream.length} >>\nstream\n${contentStream}endstream\n`);
    endObj();

    startObj(imgObj);
    pushStr(`<< /Type /XObject /Subtype /Image /Width ${p.width} /Height ${p.height} /ColorSpace /DeviceRGB /BitsPerComponent 8 /Filter /DCTDecode /Length ${p.bytes.length} >>\nstream\n`);
    pushBytes(p.bytes);
    pushStr(`\nendstream\n`);
    endObj();
  }

  const xrefOffset = byteLength;
  const totalObjs = 3 + pageCount * 3;
  pushStr(`xref\n0 ${totalObjs}\n`);
  pushStr(`0000000000 65535 f \n`);
  for (let objNum = 1; objNum < totalObjs; objNum++) {
    const offStr = String(offsets[objNum]).padStart(10, "0");
    pushStr(`${offStr} 00000 n \n`);
  }

  pushStr(`trailer\n<< /Size ${totalObjs} /Root 1 0 R >>\nstartxref\n${xrefOffset}\n%%EOF`);

  const merged = new Uint8Array(byteLength);
  let cursor = 0;
  for (const c of chunks) {
    merged.set(c, cursor);
    cursor += c.length;
  }
  return merged;
}

function dataUrlToUint8Array(dataUrl) {
  const base64 = dataUrl.split(",")[1];
  const binStr = atob(base64);
  const len = binStr.length;
  const bytes = new Uint8Array(len);
  for (let i = 0; i < len; i++) bytes[i] = binStr.charCodeAt(i);
  return bytes;
}

function triggerBlobDownload(blob, filename) {
  const url = URL.createObjectURL(blob);
  const a = document.createElement("a");
  a.href = url;
  a.download = filename;
  a.style.display = "none";
  document.body.appendChild(a);
  a.click();
  setTimeout(() => {
    document.body.removeChild(a);
    URL.revokeObjectURL(url);
  }, 1500);
}

async function downloadNativePDF(captureId, btnId, infoBoxId) {
  const btn = document.getElementById(btnId);
  const origText = btn ? btn.textContent : "";
  if (btn) {
    btn.textContent = "PDF 문서 생성 중...";
    btn.disabled = true;
  }
  showMsg(infoBoxId, "고해상도 다중 페이지 PDF 문서를 생성하고 있습니다. 잠시만 기다려 주세요...");

  try {
    const fullCanvas = await renderElementToCanvas(captureId);
    // A4 비율(595.28 : 841.89)에 맞춘 1페이지 슬라이스 높이 계산
    const pageSliceHeight = Math.floor(fullCanvas.width * (805.89 / 559.28));
    const jpegPages = [];

    for (let y = 0; y < fullCanvas.height; y += pageSliceHeight) {
      const sliceH = Math.min(pageSliceHeight, fullCanvas.height - y);
      const pageCanvas = document.createElement("canvas");
      pageCanvas.width = fullCanvas.width;
      pageCanvas.height = sliceH;
      const pCtx = pageCanvas.getContext("2d");
      pCtx.fillStyle = "#ffffff";
      pCtx.fillRect(0, 0, pageCanvas.width, pageCanvas.height);
      pCtx.drawImage(fullCanvas, 0, y, fullCanvas.width, sliceH, 0, 0, fullCanvas.width, sliceH);

      const jpegUrl = pageCanvas.toDataURL("image/jpeg", 0.92);
      jpegPages.push({
        width: pageCanvas.width,
        height: pageCanvas.height,
        bytes: dataUrlToUint8Array(jpegUrl)
      });
    }

    const pdfBytes = buildMultiPagePdfBinary(jpegPages);
    const pdfBlob = new Blob([pdfBytes], { type: "application/pdf" });
    const filename = getExportFileName(captureId, "pdf");
    triggerBlobDownload(pdfBlob, filename);

    showMsg(infoBoxId, `PDF 저장 완료: '${filename}' (${jpegPages.length}페이지) 파일이 다운로드 폴더에 저장되었습니다.`);
  } catch (err) {
    showMsg(infoBoxId, "미리보기 보안 환경에서 SVG 캡처가 제한되어 브라우저 인쇄 창을 호출합니다. 대상 프린터를 'PDF로 저장'으로 선택해 주세요.");
    try { window.print(); } catch (e) {}
  } finally {
    if (btn) {
      btn.textContent = origText;
      btn.disabled = false;
    }
  }
}

async function downloadNativePNG(captureId, btnId, infoBoxId) {
  const btn = document.getElementById(btnId);
  const origText = btn ? btn.textContent : "";
  if (btn) {
    btn.textContent = "PNG 이미지 생성 중...";
    btn.disabled = true;
  }
  showMsg(infoBoxId, "고화질 리포트 PNG 이미지를 생성하고 있습니다...");

  try {
    const fullCanvas = await renderElementToCanvas(captureId);
    const filename = getExportFileName(captureId, "png");
    fullCanvas.toBlob((blob) => {
      if (blob) {
        triggerBlobDownload(blob, filename);
        showMsg(infoBoxId, `PNG 저장 완료: '${filename}' 이미지가 다운로드 폴더에 저장되었습니다.`);
      }
      if (btn) {
        btn.textContent = origText;
        btn.disabled = false;
      }
    }, "image/png");
  } catch (err) {
    showMsg(infoBoxId, "PNG 변환이 제한된 환경입니다. 우측 'PDF 파일 다운로드' 버튼을 이용해 주세요.");
    if (btn) {
      btn.textContent = origText;
      btn.disabled = false;
    }
  }
}

function safePrintReport(captureId, infoBoxId) {
  showMsg(infoBoxId, "인쇄 대화상자를 호출합니다. 미리보기 환경에서 인쇄창이 열리지 않을 경우 자동으로 PDF 파일 다운로드를 실행합니다.");
  let beforePrintFired = false;
  const onBeforePrint = () => { beforePrintFired = true; };
  window.addEventListener("beforeprint", onBeforePrint, { once: true });

  try {
    window.print();
  } catch (e) {}

  // iframe 샌드박스에서 window.print()가 무시되는 경우 600ms 후 자동 PDF 다운로드 폴백
  setTimeout(() => {
    window.removeEventListener("beforeprint", onBeforePrint);
    if (!beforePrintFired) {
      downloadNativePDF(captureId, null, infoBoxId);
    }
  }, 600);
}

window.addEventListener("DOMContentLoaded", () => {
  runSingleAnalysis(false);
});
</script>
</body>
</html>
