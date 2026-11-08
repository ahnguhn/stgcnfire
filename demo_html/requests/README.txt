추론 입력 JSON 폴더 (model_test/demo_html) — model_test\make_demo_html_dem.py 가 실행할 때마다 비우고
<set_id>_top_NN.json (예측 상위) · _low_NN.json (예측 하위) · _rand_NN.json (랜덤) 과 <set_id>_목록.csv 를 새로 만든다.
형식: {"request_id": "demo_top_01", "ignition_nodes": ["B45-F1-U03"], "burning_nodes": [], "weather": {"wind_speed_ms": 6, "wind_dir_deg": 225, "rh_pct": 60}, "pick": {...}}
