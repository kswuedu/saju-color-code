
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>사주&컬러코드 — 정통 만세력 · 기질 컬러 · 궁합 리포트</title>
  <style>
    :root {
      --bg: #f8fafc;
      --card: #ffffff;
      --text-main: #1e293b;
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
      font-family: -apple-system, BlinkMacSystemFont, "Pretendard", "Malgun Gothic", sans-serif;
      background-color: var(--bg);
      color: var(--text-main);
      line-height: 1.65;
      padding: 24px 16px;
    }
    .container { max-width: 920px; margin: 0 auto; }
    header { text-align: center; margin-bottom: 20px; }
    header h1 { font-size: 1.85rem; font-weight: 800; color: #0f172a; letter-spacing: -0.02em; }
    header p { color: var(--text-sub); font-size: 0.95rem; margin-top: 4px; }

    /* 상단 모드 전환 탭 */
    .mode-tabs {
      display: flex;
      background: #e2e8f0;
      padding: 4px;
      border-radius: 14px;
      margin-bottom: 20px;
      gap: 4px;
      flex-wrap: wrap;
    }
    .tab-btn {
      flex: 1;
      min-width: 140px;
      padding: 12px 10px;
      border: none;
      border-radius: 10px;
      font-size: 0.92rem;
      font-weight: 700;
      color: #475569;
      background: transparent;
      cursor: pointer;
      transition: all 0.2s;
    }
    .tab-btn.active {
      background: #ffffff;
      color: #0f172a;
      box-shadow: 0 2px 6px rgba(15, 23, 42, 0.08);
    }

    .card {
      background: var(--card);
      border: 1px solid var(--border);
      border-radius: 16px;
      padding: 24px;
      margin-bottom: 18px;
      box-shadow: 0 2px 10px rgba(15, 23, 42, 0.03);
    }
    .section-title {
      font-size: 1.1rem;
      font-weight: 700;
      margin-bottom: 14px;
      color: #0f172a;
      display: flex;
      align-items: center;
      justify-content: space-between;
      flex-
