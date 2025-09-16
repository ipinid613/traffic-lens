# Traffic Lens: 실시간 교통 CCTV 뷰어

OpenCV를 활용하여 천안시 공공 CCTV 영상을 실시간으로 확인하고, 원하는 장면을 녹화 및 필터링하는 프로그램

<br>

### 실행 결과 예시
 <p align="center" width="100%">
  <img src="https://github.com/ipinid613/traffic-lens/blob/master/videos/%EC%8B%9C%EC%B2%AD_%EC%82%AC%EA%B1%B0%EB%A6%AC_output_20250916193803.gif" width="32%">
  <img src="https://github.com/ipinid613/traffic-lens/blob/master/videos/%EC%8B%9C%EC%B2%AD_%EC%82%AC%EA%B1%B0%EB%A6%AC_output_20250916193803.gif" width="32%">
  <img src="https://github.com/ipinid613/traffic-lens/blob/master/videos/%EC%98%88%EC%88%A0%EC%9D%98_%EC%A0%84%EB%8B%B9_output_20250916193825.gif" width="32%">
</p>

<br>

## 주요 기능

-   **실시간 스트리밍**: 지정된 RTSP 주소의 CCTV 영상을 실시간으로 재생, 촬영 위치/타임스탬프 표시
-   **카메라 선택**: 여러 관측 지점 중 원하는 카메라를 선택하는 기능
-   **실시간 필터**: 그레이스케일, 블러, 엣지 검출 등 6가지 필터를 실시간으로 적용
-   **영상 녹화**: 스페이스바를 이용해 원하는 구간을 동영상 파일(.avi)로 저장, 촬영 위치/타임스탬프 및 필터까지 적용된 상태에서 녹화 가능(실용성 업그레이드)

<br>

## 관측 지점 정보

본 프로젝트는 천안시에서 제공하는 공공데이터 CCTV 영상 중 아래 3개 지점을 사용

| 관측 지점 | 설치 위치 주소 | RTSP 주소 |
| :--- | :--- | :--- |
| **불당현대 사거리** | 충청남도 천안시 서북구 불당동 722 | `rtsp://210.99.70.120:1935/live/cctv048.stream` |
| **시청 사거리** | 충청남도 천안시 서북구 불당동 19-7 | `rtsp://210.99.70.120:1935/live/cctv045.stream` |
| **예술의 전당** | 충청남도 천안시 동남구 목천읍 운전리 산4-3 | `rtsp://210.99.70.120:1935/live/cctv036.stream` |

<br>

## 프로젝트 구성

-   `traffic-lens.ipynb`
    -   초기 개발 버전 (AI 지원 없이 **직접** 작성)
-   `traffic-lens_clean-code.ipynb`
    -   코드 구조 개선 및 리팩토링 버전 (AI 지원 활용)
-   **참고**: 두 노트북의 기능은 동일하며, 코드 스타일 및 구조만 다름

<br>

## 설치 및 실행 방법 (`uv` 사용)

1.  **`uv` 설치**
    -   `uv`가 설치되어 있지 않다면, [공식 설치 가이드](https://github.com/astral-sh/uv#installation)를 참고하여 먼저 설치

2.  **프로젝트 설정**
    ```bash
    # 저장소 복제
    git clone https://github.com/ipinid613/traffic-lens.git
    cd traffic-lens

    # 가상 환경 생성 및 의존성 동기화
    uv sync
    ```

3.  **Jupyter Notebook 실행**
    -   VS Code 등의 에디터에서 `traffic-lens_clean-code.ipynb` 파일 실행
    -   또는 터미널에서 Jupyter 실행
        ```bash
        jupyter notebook
        ```

<br>

### (선택) `requirements.txt`가 필요한 경우

`pip`를 사용해야 하는 환경이라면, `uv`로 `requirements.txt` 파일을 생성할 수 있음

```bash
# requirements.txt 파일 생성
uv pip freeze > requirements.txt

# pip로 의존성 설치
pip install -r requirements.txt
```

<br>

## 사용법 (키보드 입력)

-   `ESC`: 프로그램 종료
-   `Space`: 녹화 시작 / 중지
-   `1`~`6`: 실시간 필터 변경
    -   `1`: 필터 없음
    -   `2`: 그레이스케일
    -   `3`: 가우시안 블러
    -   `4`: 엣지 검출 (Canny)
    -   `5`: 세피아
    -   `6`: 좌우 반전
