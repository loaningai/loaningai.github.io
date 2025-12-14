<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Loaning.ai - 아티클 읽기</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.4.0/css/all.min.css">
    <style>
        /* 기본 스타일 */
        * {
            box-sizing: border-box;
            margin: 0;
            padding: 0;
            font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;
        }

        body {
            background-color: #f9f9f9;
            color: #333;
            line-height: 1.6;
        }

        /* 헤더 */
        header {
            background: white;
            padding: 15px 40px;
            border-bottom: 1px solid #eee;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .logo {
            font-size: 20px;
            font-weight: bold;
            color: #00a86b;
            display: flex;
            align-items: center;
            gap: 5px;
        }

        /* 아티클 컨테이너 */
        .article-wrapper {
            max-width: 720px;
            margin: 40px auto;
            background: white;
            padding: 40px;
            border-radius: 8px;
            box-shadow: 0 2px 10px rgba(0,0,0,0.05);
            position: relative; /* 게이트 위치 기준점 */
            /* 중요: 초기 높이 제한 및 넘치는 텍스트 숨김 */
            max-height: 800px; 
            overflow: hidden;
            transition: max-height 0.5s ease;
        }

        /* 아티클 내용 스타일 */
        .article-header img {
            width: 100%;
            border-radius: 8px;
            margin-bottom: 20px;
        }

        h1 {
            font-size: 28px;
            margin-bottom: 10px;
            line-height: 1.4;
            color: #222;
        }

        .author-info {
            color: #666;
            font-size: 14px;
            margin-bottom: 30px;
            display: flex;
            gap: 10px;
        }

        .content-body p {
            margin-bottom: 20px;
            font-size: 16px;
            color: #444;
        }

        /* --- 콘텐츠 게이트 (이메일 입력창) 스타일 --- */
        .content-gate {
            position: absolute;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 400px; /* 그라데이션 영역 높이 */
            /* 위쪽은 투명, 아래쪽은 흰색으로 변하는 그라데이션 (Blur 효과) */
            background: linear-gradient(to bottom, rgba(255,255,255,0) 0%, rgba(255,255,255,0.9) 30%, #ffffff 100%);
            display: flex;
            flex-direction: column;
            justify-content: flex-end; /* 내용을 아래로 정렬 */
            align-items: center;
            padding-bottom: 60px;
            z-index: 10;
        }

        .gate-box {
            background-color: #f0fdf4; /* 연한 녹색 배경 */
            border: 1px solid #00a86b;
            border-radius: 12px;
            padding: 30px;
            width: 90%;
            max-width: 500px;
            text-align: center;
            box-shadow: 0 10px 25px rgba(0, 168, 107, 0.15);
        }

        .gate-title {
            font-size: 20px;
            font-weight: 700;
            color: #00a86b;
            margin-bottom: 10px;
        }

        .gate-desc {
            font-size: 14px;
            color: #555;
            margin-bottom: 20px;
        }

        /* 이메일 폼 스타일 */
        .email-form {
            display: flex;
            gap: 10px;
        }

        .email-input {
            flex: 1;
            padding: 12px;
            border: 1px solid #ddd;
            border-radius: 6px;
            outline: none;
        }
        
        .email-input:focus {
            border-color: #00a86b;
        }

        .submit-btn {
            padding: 12px 20px;
            background-color: #00a86b;
            color: white;
            border: none;
            border-radius: 6px;
            font-weight: bold;
            cursor: pointer;
            white-space: nowrap;
        }

        .submit-btn:hover {
            background-color: #008f5b;
        }

        /* 잠금 해제 시 적용할 클래스 */
        .unlocked {
            max-height: none; /* 높이 제한 해제 */
            overflow: visible;
        }
        
        .hidden {
            display: none !important;
        }

    </style>
</head>
<body>

    <header>
        <div class="logo"><i class="fas fa-home"></i> Loaning.ai</div>
        <div style="font-size:14px; color:#666;">Blog</div>
    </header>

    <div class="article-wrapper" id="articleWrapper">
        <div class="article-header">
            <div style="background-color:#e0e0e0; height:200px; width:100%; border-radius:8px; display:flex; align-items:center; justify-content:center; color:#888; margin-bottom:20px;">
                <i class="fas fa-image" style="font-size:40px;"></i>
            </div>
            <h1>같은 피드백, 왜 누구에게는 통하고 누구에게는 안 통할까? | 팀원을 움직이는 피드백의 과학</h1>
            <div class="author-info">
                <span>저자 김봉준</span> | <span>리더십/매니지먼트</span>
            </div>
        </div>

        <div class="content-body">
            <p>
                많은 리더들이 팀원에게 피드백을 줄 때 고민에 빠집니다. "이 말을 하면 상처받지 않을까?" 혹은 "지난번에도 말했는데 왜 안 고쳐질까?" 같은 고민들이죠. 
                피드백은 조직의 성장을 위해 필수적인 요소이지만, 잘못 전달된 피드백은 오히려 독이 될 수 있습니다.
            </p>
            <p>
                하지만 많은 사람들이 이 부분을 간과합니다. 지시가 필요한 팀원에게 위임하고, 위임이 필요한 팀원에게 지시합니다. 
                그리고 팀원들의 원치 않는 반응에 당혹스러워합니다. 이것은 팀원들도 마찬가지입니다. 
                자신은 지시가 필요한데 위임을 원한다고 착각하거나, 반대로 위임이 필요한데 지시를 기대하는 경우도 있습니다.
            </p>
            <p>
                지시와 위임, 어떤 방식으로 운영할 것인가에 대한 명확한 기준이 없다면 조직은 방향을 잃기 쉽습니다.
                효과적인 피드백을 위해서는 먼저 상대방의 '준비 상태(Readiness)'를 파악해야 합니다.
            </p>
            <p>
                상황적 리더십 이론에 따르면, 구성원의 역량과 의욕에 따라 4가지 단계로 나눌 수 있습니다. 
                첫째, 역량은 낮지만 의욕이 높은 단계. 둘째, 역량도 낮고 의욕도 떨어진 단계. 셋째, 역량은 높지만 의욕이 불안정한 단계. 
                마지막으로 역량과 의욕이 모두 높은 단계입니다.
            </p>
            <p>
                각 단계별로 리더가 취해야 할 행동은 완전히 다릅니다. 초심자에게는 구체적인 지시가 필요하지만, 
                숙련자에게 시시콜콜한 지시는 간섭으로 느껴질 뿐입니다.
            </p>
            <p>
                그렇다면 우리 팀원들은 현재 어떤 상태일까요? 그리고 나는 그들에게 적절한 피드백을 주고 있을까요?
                지금부터 구체적인 진단 방법과 해결책을 하나씩 살펴보겠습니다. 이를 통해 당신은...
            </p>
        </div>

        <div class="content-gate" id="contentGate">
            <div class="gate-box">
                <div class="gate-title">
                    <i class="fas fa-lock-open"></i> 전체 내용을 읽고 싶으신가요?
                </div>
                <div class="gate-desc">
                    이메일을 입력하시면 나머지 전문을 <br>무료로 바로 확인하실 수 있습니다.
                </div>
                
                <form class="email-form" onsubmit="unlockContent(event)">
                    <input type="email" class="email-input" placeholder="이메일 주소 입력" required>
                    <button type="submit" class="submit-btn">계속 읽기</button>
                </form>
            </div>
        </div>

    </div>

    <script>
        function unlockContent(event) {
            event.preventDefault(); // 폼 제출 시 새로고침 방지

            // 1. 게이트(입력창+그라데이션) 숨기기
            const gate = document.getElementById('contentGate');
            gate.classList.add('hidden');

            // 2. 아티클 컨테이너의 높이 제한 풀기
            const wrapper = document.getElementById('articleWrapper');
            wrapper.classList.add('unlocked');

            // (선택사항) 사용자에게 알림
            alert("확인되었습니다. 전체 내용을 확인하세요!");
        }
    </script>

</body>
</html>
