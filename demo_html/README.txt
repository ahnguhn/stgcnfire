model_test/demo_html — 데모 페이지 (2026-11-08: 프로젝트의 유일한 데모 페이지, {demo_html} = {base}\model_test\demo_html)
  성능 시연:  model_test> python make_demo_html_dem.py   (상위 5 · 하위 5 · 랜덤 5, 실행할 때마다 requests · results 를 비우고 새로 생성)
  보기:    이 폴더의 index.html 을 브라우저로 열기 (열려 있으면 [⟳ 다시 불러오기])
  공간정보 building\ 갱신: code\demo_data_builder> python make_demo_html.py --space-only (이 폴더로 바로 씀)
  infer.py · 웹 서비스(?save=1) · make_request.py 결과도 이 폴더 requests\ · results\ 에 들어온다 (make_demo_html_dem.py 를 돌리면 비워짐)

demo_html — 화재 확산 추론 데모 (단일 파일 index.html, 외부 라이브러리 없음, 3D/2D)

폴더
  index.html                         데모 페이지 (더블클릭으로 열기)
  building\space_data.json  + .js    공간정보   code\demo_data_builder> python make_demo_html.py --space-only
  requests\<id>.json  + _bundle.js   추론 입력  model_test> python make_request.py --id <id> --ignition <구획ID> --wind 6 --dir 225 --rh 60
  results\<id>_result.json + _bundle.js  추론 출력  code\inference> python infer.py --input ..\..\model_test\demo_html\requests\ --output ..\..\model_test\demo_html\results\
                                                     (make_request.py 에 --run 을 붙이면 입력 저장과 추론을 한 번에)
자동 불러오기
  index.html 을 열면 building · requests · results 의 데이터를 자동으로 읽는다. 새 결과를 만든 뒤 [⟳ 다시 불러오기] 를 누르면 다시 읽는다
  (보고 있던 시나리오 · 시점 · 선택 구획 유지).
  브라우저는 file:// 에서 폴더 목록을 읽지 못하므로 각 폴더의 .js 묶음(space_data.js · _bundle.js)을 읽는다.
  묶음은 make_request.py · infer.py · make_demo_html.py 가 파일을 쓸 때 자동 갱신된다.
  JSON 을 손으로 넣거나 지웠으면:  code\inference> python demo_bundle.py
  묶음 없이 보려면 [폴더 직접 선택] 으로 demo_html 폴더를 고르거나 JSON 파일을 창에 끌어다 놓는다.
화면
  왼쪽   시나리오 목록 (requests ↔ results, request_id 로 짝) · 불러오기 기록
  가운데 지도 — 3D(기본: 드래그 회전 · Shift/우클릭 드래그 이동 · 휠 확대 · 보이는 층 '~n층' 으로 위층 숨김) / 2D(층별 평면)
         모드: 시간별 확산(슬라이더 5분 × 12 · ▶ 재생) · 도달시각 · 60분 확률, 호실 클릭 → 확률 곡선에 추가
  오른쪽 요청 내용(발화 · 이미 연소 · 풍속 · 풍향 · 습도, 적용값) · 확산 요약(구획 · 층 · 건물 표) · 착화 확률 곡선
공간정보 · 모델을 다시 만들면(04 → train → predict/graph) building\space_data.json 도 다시 만들고 결과 JSON 도 새 모델로 다시 돌린다.
requests · results 의 '예시_라벨Y기반_…' 2건은 모델 출력이 아니라 학습 라벨로 만든 예시 — 실제 결과가 생기면 지운 뒤 demo_bundle.py 실행.
