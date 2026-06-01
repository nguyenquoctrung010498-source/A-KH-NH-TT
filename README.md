<!DOCTYPE html>
<html lang="vi">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Trình Tự Chuẩn Bị Hồ Sơ Đầu Tư</title>
<style>
  @import url('https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@300;400;500;600;700&family=Space+Mono:wght@400;700&display=swap');

  :root {
    --bg: #0d1117;
    --surface: #161b22;
    --surface2: #1c2128;
    --border: #30363d;
    --accent: #1f6feb;
    --accent-glow: rgba(31,111,235,0.25);
    --green: #238636;
    --green-light: #3fb950;
    --red: #da3633;
    --red-light: #f85149;
    --yellow: #9e6a03;
    --yellow-light: #d29922;
    --text: #e6edf3;
    --text-muted: #8b949e;
    --connector: #58a6ff;
  }

  * { margin: 0; padding: 0; box-sizing: border-box; }

  body {
    background: var(--bg);
    font-family: 'Be Vietnam Pro', sans-serif;
    color: var(--text);
    min-height: 100vh;
    padding: 40px 20px 60px;
    overflow-x: hidden;
  }

  /* Grid background */
  body::before {
    content: '';
    position: fixed;
    inset: 0;
    background-image:
      linear-gradient(rgba(31,111,235,0.04) 1px, transparent 1px),
      linear-gradient(90deg, rgba(31,111,235,0.04) 1px, transparent 1px);
    background-size: 40px 40px;
    pointer-events: none;
    z-index: 0;
  }

  .wrapper {
    position: relative;
    z-index: 1;
    max-width: 760px;
    margin: 0 auto;
  }

  header {
    text-align: center;
    margin-bottom: 48px;
  }

  header .label {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    letter-spacing: 3px;
    color: var(--accent);
    text-transform: uppercase;
    margin-bottom: 12px;
  }

  header h1 {
    font-size: 26px;
    font-weight: 700;
    line-height: 1.3;
    color: var(--text);
  }

  header h1 span {
    color: var(--connector);
  }

  header p {
    margin-top: 10px;
    font-size: 13px;
    color: var(--text-muted);
  }

  /* FLOW */
  .flow {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 0;
  }

  /* START / END terminals */
  .terminal {
    display: flex;
    align-items: center;
    justify-content: center;
    width: 140px;
    height: 44px;
    border-radius: 22px;
    font-family: 'Space Mono', monospace;
    font-size: 12px;
    font-weight: 700;
    letter-spacing: 1px;
    text-transform: uppercase;
    border: 2px solid var(--border);
    background: var(--surface2);
    color: var(--text-muted);
    position: relative;
    z-index: 2;
  }

  .terminal.start {
    border-color: var(--green);
    color: var(--green-light);
    background: rgba(35,134,54,0.1);
    box-shadow: 0 0 20px rgba(35,134,54,0.2);
  }

  .terminal.end {
    border-color: var(--red);
    color: var(--red-light);
    background: rgba(218,54,51,0.1);
    box-shadow: 0 0 20px rgba(218,54,51,0.2);
  }

  /* Vertical connector */
  .connector {
    width: 2px;
    height: 32px;
    background: linear-gradient(to bottom, var(--border), var(--connector));
    position: relative;
    z-index: 1;
  }

  .connector::after {
    content: '';
    position: absolute;
    bottom: -6px;
    left: 50%;
    transform: translateX(-50%);
    border-left: 6px solid transparent;
    border-right: 6px solid transparent;
    border-top: 8px solid var(--connector);
  }

  /* Step node */
  .step-node {
    width: 100%;
    max-width: 560px;
    background: var(--surface);
    border: 1px solid var(--border);
    border-radius: 10px;
    overflow: hidden;
    position: relative;
    transition: border-color 0.2s, box-shadow 0.2s;
    cursor: default;
    animation: fadeSlide 0.4s ease both;
  }

  .step-node:hover {
    border-color: var(--accent);
    box-shadow: 0 0 24px var(--accent-glow);
  }

  @keyframes fadeSlide {
    from { opacity: 0; transform: translateY(10px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  .step-node:nth-child(1) { animation-delay: 0.05s; }
  .step-node:nth-child(2) { animation-delay: 0.10s; }
  .step-node:nth-child(3) { animation-delay: 0.15s; }
  .step-node:nth-child(4) { animation-delay: 0.20s; }
  .step-node:nth-child(5) { animation-delay: 0.25s; }
  .step-node:nth-child(6) { animation-delay: 0.30s; }
  .step-node:nth-child(7) { animation-delay: 0.35s; }

  .step-header {
    display: flex;
    align-items: center;
    gap: 14px;
    padding: 14px 18px;
    background: var(--surface2);
    border-bottom: 1px solid var(--border);
  }

  .step-num {
    font-family: 'Space Mono', monospace;
    font-size: 11px;
    font-weight: 700;
    color: var(--accent);
    background: rgba(31,111,235,0.12);
    border: 1px solid rgba(31,111,235,0.3);
    border-radius: 6px;
    padding: 3px 8px;
    white-space: nowrap;
    flex-shrink: 0;
  }

  .step-title {
    font-size: 14px;
    font-weight: 600;
    color: var(--text);
    line-height: 1.3;
  }

  .step-subtitle {
    font-size: 11px;
    color: var(--text-muted);
    font-style: italic;
    margin-top: 1px;
  }

  .step-body {
    padding: 14px 18px;
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 12px;
  }

  .meta-block {
    background: rgba(255,255,255,0.02);
    border: 1px solid rgba(255,255,255,0.06);
    border-radius: 7px;
    padding: 10px 12px;
  }

  .meta-label {
    font-family: 'Space Mono', monospace;
    font-size: 9px;
    letter-spacing: 1.5px;
    text-transform: uppercase;
    color: var(--text-muted);
    margin-bottom: 5px;
  }

  .meta-text {
    font-size: 12px;
    color: var(--text);
    line-height: 1.5;
  }

  /* Decision diamond */
  .decision-wrap {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100%;
    max-width: 560px;
    position: relative;
    animation: fadeSlide 0.4s ease both;
  }

  .diamond-outer {
    position: relative;
    width: 100%;
    display: flex;
    justify-content: center;
  }

  .diamond {
    background: var(--surface2);
    border: 1px solid var(--yellow-light);
    border-radius: 8px;
    padding: 14px 24px;
    font-size: 13px;
    font-weight: 600;
    color: var(--yellow-light);
    text-align: center;
    box-shadow: 0 0 20px rgba(210,153,34,0.15);
    position: relative;
    width: auto;
    max-width: 420px;
    display: flex;
    align-items: center;
    gap: 10px;
  }

  .diamond-icon {
    font-size: 16px;
    flex-shrink: 0;
  }

  /* Outcome branches */
  .branches {
    display: flex;
    width: 100%;
    justify-content: space-between;
    align-items: flex-start;
    margin-top: 0;
    position: relative;
    padding: 0 20px;
  }

  .branch {
    display: flex;
    flex-direction: column;
    align-items: center;
    flex: 1;
    position: relative;
  }

  .branch-line-v {
    width: 2px;
    height: 28px;
    background: linear-gradient(to bottom, var(--border), currentColor);
    position: relative;
  }

  .branch-line-v::after {
    content: '';
    position: absolute;
    bottom: -6px;
    left: 50%;
    transform: translateX(-50%);
    border-left: 5px solid transparent;
    border-right: 5px solid transparent;
    border-top: 7px solid currentColor;
  }

  .branch.yes .branch-line-v { color: var(--green-light); }
  .branch.no  .branch-line-v { color: var(--red-light); }

  .branch-tag {
    font-family: 'Space Mono', monospace;
    font-size: 10px;
    font-weight: 700;
    padding: 3px 10px;
    border-radius: 4px;
    margin-bottom: 6px;
    margin-top: 6px;
  }

  .branch.yes .branch-tag {
    background: rgba(35,134,54,0.15);
    border: 1px solid var(--green);
    color: var(--green-light);
  }

  .branch.no .branch-tag {
    background: rgba(218,54,51,0.12);
    border: 1px solid var(--red);
    color: var(--red-light);
  }

  /* Side action box (for "No" branch) */
  .side-action {
    background: var(--surface);
    border: 1px dashed var(--red);
    border-radius: 8px;
    padding: 10px 14px;
    font-size: 12px;
    color: var(--red-light);
    text-align: center;
    width: 100%;
    max-width: 190px;
    line-height: 1.4;
  }

  /* Horizontal divider between branches */
  .h-bridge {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    height: 2px;
    width: calc(50% - 40px);
    background: var(--border);
  }

  /* Legend */
  .legend {
    margin-top: 40px;
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    gap: 16px;
  }

  .legend-item {
    display: flex;
    align-items: center;
    gap: 7px;
    font-size: 11px;
    color: var(--text-muted);
  }

  .legend-box {
    width: 24px;
    height: 14px;
    border-radius: 3px;
  }

  .legend-box.process { background: var(--surface2); border: 1px solid var(--accent); }
  .legend-box.decision { background: var(--surface2); border: 1px solid var(--yellow-light); }
  .legend-box.yes-path { background: rgba(35,134,54,0.3); border: 1px solid var(--green); }
  .legend-box.no-path { background: rgba(218,54,51,0.2); border: 1px dashed var(--red); }
</style>
</head>
<body>
<div class="wrapper">
  <header>
    <div class="label">Quy trình pháp lý đầu tư</div>
    <h1>Trình Tự Chuẩn Bị <span>Hồ Sơ Đầu Tư</span></h1>
    <p>7 bước từ thành lập pháp nhân đến hoàn thiện hồ sơ xin chủ trương</p>
  </header>

  <div class="flow">

    <!-- START -->
    <div class="terminal start">▶ BẮT ĐẦU</div>

    <div class="connector"></div>

    <!-- STEP 1 -->
    <div class="step-node">
      <div class="step-header">
        <div class="step-num">BƯỚC 01</div>
        <div>
          <div class="step-title">Thành lập pháp nhân</div>
          <div class="step-subtitle">Đăng ký kinh doanh công ty</div>
        </div>
      </div>
      <div class="step-body">
        <div class="meta-block">
          <div class="meta-label">Mục đích</div>
          <div class="meta-text">Có chủ thể pháp lý độc lập để đứng tên hồ sơ và giao dịch với cơ quan nhà nước</div>
        </div>
        <div class="meta-block">
          <div class="meta-label">Hành động</div>
          <div class="meta-text">Đăng ký thành lập doanh nghiệp tại Sở Kế hoạch và Đầu tư</div>
        </div>
      </div>
    </div>

    <div class="connector"></div>

    <!-- STEP 2 -->
    <div class="step-node">
      <div class="step-header">
        <div class="step-num">BƯỚC 02</div>
        <div>
          <div class="step-title">Khảo sát địa điểm & kiểm tra quy hoạch</div>
          <div class="step-subtitle">Đối chiếu vị trí khu đất với các loại quy hoạch</div>
        </div>
      </div>
      <div class="step-body">
        <div class="meta-block">
          <div class="meta-label">Mục đích</div>
          <div class="meta-text">Đảm bảo khu đất không vi phạm quy định cấm và phù hợp định hướng phát triển địa phương</div>
        </div>
        <div class="meta-block">
          <div class="meta-label">Đối chiếu với</div>
          <div class="meta-text">Quy hoạch chung TP · Quy hoạch sử dụng đất · Quy hoạch phân khu xã/phường</div>
        </div>
      </div>
    </div>

    <div class="connector"></div>

    <!-- DECISION 1: Quy hoạch -->
    <div class="decision-wrap">
      <div class="diamond-outer">
        <div class="diamond">
          <span class="diamond-icon">◆</span>
          Quy hoạch có phù hợp?
        </div>
      </div>
      <div class="branches">
        <!-- YES branch -->
        <div class="branch yes" style="align-items: center;">
          <div class="branch-tag">✓ CÓ</div>
          <div class="branch-line-v" style="color: var(--green-light);"></div>
        </div>
        <!-- NO branch -->
        <div class="branch no" style="align-items: center;">
          <div class="branch-tag">✗ KHÔNG</div>
          <div class="side-action">Tìm vị trí khác<br>hoặc xin điều chỉnh<br>quy hoạch → Quay lại B2</div>
        </div>
      </div>
    </div>

    <!-- STEP 3 -->
    <div class="step-node">
      <div class="step-header">
        <div class="step-num">BƯỚC 03</div>
        <div>
          <div class="step-title">Khảo sát chi tiết đất đai</div>
          <div class="step-subtitle">Đo đạc trích lục hiện trạng, nguồn gốc đất</div>
        </div>
      </div>
      <div class="step-body">
        <div class="meta-block">
          <div class="meta-label">Mục đích</div>
          <div class="meta-text">Xác định chính xác ranh giới, diện tích và tình trạng pháp lý khu đất</div>
        </div>
        <div class="meta-block">
          <div class="meta-label">Hành động</div>
          <div class="meta-text">Thuê đơn vị đo đạc có phép lập Trích lục bản đồ · Xác nhận nguồn gốc sử dụng đất với địa phương</div>
        </div>
      </div>
    </div>

    <div class="connector"></div>

    <!-- STEP 4 -->
    <div class="step-node">
      <div class="step-header">
        <div class="step-num">BƯỚC 04</div>
        <div>
          <div class="step-title">Thiết lập dự án</div>
          <div class="step-subtitle">Xác định mục tiêu, quy mô, công nghệ, tổng vốn</div>
        </div>
      </div>
      <div class="step-body">
        <div class="meta-block">
          <div class="meta-label">Mục đích</div>
          <div class="meta-text">Hình thành bộ khung cốt lõi của Đề xuất dự án đầu tư</div>
        </div>
        <div class="meta-block">
          <div class="meta-label">Hành động</div>
          <div class="meta-text">Xác định quy mô xây dựng · Lựa chọn máy móc & công nghệ · Khái toán Tổng vốn đầu tư</div>
        </div>
      </div>
    </div>

    <div class="connector"></div>

    <!-- STEP 5 -->
    <div class="step-node">
      <div class="step-header">
        <div class="step-num">BƯỚC 05</div>
        <div>
          <div class="step-title">Đánh giá sơ bộ tác động môi trường</div>
          <div class="step-subtitle">ĐTM sơ bộ theo Luật BVMT 2020</div>
        </div>
      </div>
      <div class="step-body">
        <div class="meta-block">
          <div class="meta-label">Mục đích</div>
          <div class="meta-text">Phân tích các yếu tố môi trường bị ảnh hưởng bởi quy trình công nghệ và quy mô dự án</div>
        </div>
        <div class="meta-block">
          <div class="meta-label">Hành động</div>
          <div class="meta-text">Lập báo cáo ĐTM sơ bộ để nộp kèm hồ sơ xin chủ trương đầu tư</div>
        </div>
      </div>
    </div>

    <div class="connector"></div>

    <!-- DECISION 2: ĐTM -->
    <div class="decision-wrap">
      <div class="diamond-outer">
        <div class="diamond">
          <span class="diamond-icon">◆</span>
          Đạt tiêu chuẩn ĐTM?
        </div>
      </div>
      <div class="branches">
        <div class="branch yes" style="align-items: center;">
          <div class="branch-tag">✓ ĐẠT</div>
          <div class="branch-line-v" style="color: var(--green-light);"></div>
        </div>
        <div class="branch no" style="align-items: center;">
          <div class="branch-tag">✗ KHÔNG ĐẠT</div>
          <div class="side-action">Điều chỉnh công nghệ / quy mô → Quay lại B4</div>
        </div>
      </div>
    </div>

    <!-- STEP 6 -->
    <div class="step-node">
      <div class="step-header">
        <div class="step-num">BƯỚC 06</div>
        <div>
          <div class="step-title">Chứng minh năng lực tài chính</div>
          <div class="step-subtitle">BCTC 2 năm + Cam kết tín dụng ngân hàng</div>
        </div>
      </div>
      <div class="step-body">
        <div class="meta-block">
          <div class="meta-label">Mục đích</div>
          <div class="meta-text">Khẳng định công ty có đủ năng lực tài chính để thực hiện toàn bộ dự án</div>
        </div>
        <div class="meta-block">
          <div class="meta-label">Hành động</div>
          <div class="meta-text">Chuẩn bị BCTC 2 năm gần nhất · Xin cam kết cung cấp tín dụng/vốn vay từ ngân hàng</div>
        </div>
      </div>
    </div>

    <div class="connector"></div>

    <!-- DECISION 3: Vốn -->
    <div class="decision-wrap">
      <div class="diamond-outer">
        <div class="diamond">
          <span class="diamond-icon">◆</span>
          Vốn + Tín dụng ≥ Tổng vốn đầu tư?
        </div>
      </div>
      <div class="branches">
        <div class="branch yes" style="align-items: center;">
          <div class="branch-tag">✓ ĐỦ</div>
          <div class="branch-line-v" style="color: var(--green-light);"></div>
        </div>
        <div class="branch no" style="align-items: center;">
          <div class="branch-tag">✗ THIẾU</div>
          <div class="side-action">Bổ sung tài sản đảm bảo / Đổi ngân hàng → Quay lại B6</div>
        </div>
      </div>
    </div>

    <!-- STEP 7 -->
    <div class="step-node">
      <div class="step-header">
        <div class="step-num">BƯỚC 07</div>
        <div>
          <div class="step-title">Tổng hợp thành bộ hồ sơ hoàn chỉnh</div>
          <div class="step-subtitle">Nộp hồ sơ xin chủ trương đầu tư</div>
        </div>
      </div>
      <div class="step-body">
        <div class="meta-block">
          <div class="meta-label">Đầu vào</div>
          <div class="meta-text">Kết quả từ B1–B6: pháp nhân · bản đồ · quy mô · ĐTM · tài chính</div>
        </div>
        <div class="meta-block">
          <div class="meta-label">Đầu ra</div>
          <div class="meta-text">Bộ hồ sơ đề xuất dự án đầu tư đầy đủ pháp lý để nộp cơ quan thẩm quyền</div>
        </div>
      </div>
    </div>

    <div class="connector" style="background: linear-gradient(to bottom, var(--border), var(--green));"></div>
    <div class="connector" style="background: linear-gradient(to bottom, var(--border), var(--green)); height:0;"></div>

    <!-- END -->
    <div class="terminal end">■ KẾT THÚC</div>

  </div><!-- /flow -->

  <!-- Legend -->
  <div class="legend">
    <div class="legend-item">
      <div class="legend-box process"></div>
      Bước xử lý
    </div>
    <div class="legend-item">
      <div class="legend-box decision"></div>
      Cổng quyết định
    </div>
    <div class="legend-item">
      <div class="legend-box yes-path"></div>
      Luồng thuận (Có / Đạt / Đủ)
    </div>
    <div class="legend-item">
      <div class="legend-box no-path"></div>
      Luồng ngược (Không / Không đạt)
    </div>
  </div>

</div><!-- /wrapper -->
</body>
</html>
