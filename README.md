## ❓ 코드 사용방법
python IDLE에 코드를 붙여넣은 후, **Run-Run module** 하여 코드를 실행
<br/><br/>
## 📹 Video Editor for HBT (GPU-accelerated)
400 * 400 px로 영상 crop, 60분으로 trim을 함. 컴퓨터에 GPU가 있어야 빠른 속도로 실행가능함.
 ### 사용방법
> - 비디오를 선택
> - crop할 위치에 맞추어 초록색 네모를 옮겨줌
> - trim을 시작할 영상시간을 프롬프트에 입력
> - **ffmpeg.exe** (검은 창)이 사라질 때까지 기다림  

<br/>

## 🟢 ROI extractor for HBT
ROI인 원형 well의 정보를 가져올 수 있음.
### 사용방법
>- 비디오를 선택 (코드가 비디오의 첫 번째 프레임을 불러옴)
>- ROI의 중심에서부터 드래그하여 원형 ROI를 지정
>- **q**를 눌러서 종료
>- print statement에서 ROI 중심 <ins> (x,y)좌표와 반지름(r) </ins> 정보를 확인  

<br/>

## 📊 Ethogram maker for HBT
SLEAP에서 추출한 pose estimation data(.csv)를 활용하여 Checking behavior를 한 시점과 횟수를 보여주는 Ethogram과 excel 파일을 생성함.
### 사용방법
>- SLEAP에서 얻은 csv파일을 선택
>- **ROI extractor for HBT**에서 얻은 ROI 정보(x,y,r)를 순서대로 입력
>- Ethogram이 저장될 위치와 파일명을 입력 (png 형태로 저장됨)
>- excel 파일이 저장될 위치와 파일명을 입력


## Rotate Video
영상 회전시키기 (A-SOiD 분석에 필요), GPU 사용
### 사용방법
>- ffmpeg 설치 : pip install ffmpeg-python

## A-SOiD
Anaconda prompt 실행 후 코드 실행

## SLEAP
Anaconda prompt 실행 후 아래 코드 실행<br/><br/>
F:<br/>
cd sleap<br/>
conda activate sleap<br/>
sleap-label<br/><br/>

## Video ffmpeg re-encoding
비디오 그대로 SLEAP이 처리를 못함. 아래 코드로 re-encoding한 비디오를 사용. IDLE 말고 Conda prompt에서 사용<br/>
>- ffmpeg -y -i "input.mp4" -c:v libx264 -pix_fmt yuv420p -preset superfast -crf 23 "output.mp4"<br/>
<br/>
GPU 가속 사용 시<br/>
>- ffmpeg -y -hwaccel cuda -i "input.mp4" -c:v h264_nvenc -preset fast -crf 23 "output.mp4"<br/>

## Video resize
FHD 비디오는 현 GPU로 처리가 힘듦. 가로 세로 각 1/3로 줄이는 코드 <br/>
