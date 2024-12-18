# 🎬 공학도서관 오리지널 컨텐츠

# 📸 라즈베리파이 타임랩스 카메라 만들기

## 📝 프로젝트 소개
이 프로젝트는 라즈베리파이와 카메라 모듈을 활용하여 자동으로 타임랩스 영상을 촬영하는 장치를 만드는 과정을 설명합니다. 주기적으로 사진을 촬영하고 이를 동영상으로 만들어 시간의 흐름을 담아낼 수 있습니다.

## 📚 사전학습
이 프로젝트를 시작하기 전에 아래 내용을 먼저 공부하고 오시면 좋아요.

- 라즈베리파이 기초
  - 라즈베리파이 OS 설치하기
  - 리눅스 기본 명령어 익히기
  - 터미널 사용법 알아보기

- 리눅스 명령어
  - 기본 파일 조작 명령어 이해하기
  - crontab 사용법 알아보기
  - 쉘 스크립트 작성법 익히기

- 카메라 활용하기
  - 라즈베리파이 카메라 설정방법
  - raspistill 명령어 이해하기
  - FFmpeg 사용법 알아보기

## 🎯 성취 목표
- 라즈베리파이 카메라 모듈을 연결하고 설정할 수 있다.
- 기본적인 사진 촬영과 저장을 할 수 있다.
- 타임랩스 촬영 스크립트를 작성할 수 있다.
- 촬영한 사진들을 동영상으로 변환할 수 있다.
- crontab으로 자동 촬영을 설정할 수 있다.

## 🛠 준비물
- 라즈베리파이 4
- 라즈베리파이 카메라 모듈
- SD 카드
- 모니터
- HDMI 케이블
- 키보드/마우스
- 전원 어댑터

## 📋 하드웨어 연결 방법
1. 라즈베리파이 카메라 연결
   - 카메라 슬롯의 커넥터 열기
   - 은색 단자가 보이도록 케이블 삽입
   - 커넥터 닫아서 고정

2. 주변기기 연결
   - HDMI 케이블로 모니터 연결
   - USB 키보드/마우스 연결
   - 전원 어댑터 연결

## 💾 실습 코드
| 파일명 | 설명 |
|--------|------|
| [timelapse.sh](./src/timelapse.sh) | 타임랩스 촬영 스크립트 |


## 📋 실습 명령어
### 기본 터미널 명령어
| 명령어 | 설명 | 비고 |
|--------|------|------|
| `Ctrl + Shift + +` | 터미널 글자 크기 키우기 | 보기 편하게 확대 |
| `Ctrl + -` | 터미널 글자 크기 줄이기 | 축소 필요할 때 사용 |
| `clear` | 터미널 화면 내용 지우기 | 깔끔한 작업 환경 만들기 |

### 카메라 제어 명령어
| 명령어 | 설명 | 비고 |
|--------|------|------|
| `rpicam-hello` | 카메라 기본 촬영 실행 | 카메라 테스트용 |
| `rpicam-hello --timeout 0` | 카메라 미리보기 화면 계속 유지 | Ctrl+C로 종료 |
| `rpicam-still --output test.jpg` | 사진 한 장 촬영하여 test.jpg로 저장 | 기본 해상도 사용 |
| `rpicam-still --timeout 30000 --timelapse 2000 -o timelapse/image%04d.jpg` | 30초 동안 2초 간격으로 타임랩스 촬영 | %04d는 0001부터 순차적으로 증가 |

### 타임랩스 관련 명령어
| 명령어 | 설명 | 비고 |
|--------|------|------|
| `mkdir timelapse` | 타임랩스 저장할 폴더 생성 | |
| `sudo apt install ffmpeg` | 동영상 변환용 FFmpeg 설치 | |
| `ffmpeg -r 10 -i timelapse/image%04d.jpg -s 1920x1080 output.mp4` | 타임랩스 사진을 동영상으로 변환 | -r: 프레임 속도(fps)<br>-s: 해상도 |
| `vlc output.mp4 --loop` | 생성된 동영상 반복 재생 | VLC 플레이어 사용 |

## 🚀 시작하기
1. 라즈베리 카메라 모듈 연결하기
   - 케이블 커넥터의 슬롯을 엽니다
   - 은색 단자가 아래를 향하도록 케이블을 삽입합니다
   - 갈색 커넥터를 밀어서 단단히 고정합니다

2. 라즈베리파이4 부팅하기
   - 모니터에 HDMI 케이블을 연결합니다
   - 전원 케이블을 연결해 부팅합니다
   - 파란색 바탕화면이 나타날 때까지 기다립니다

3. 카메라 테스트하기
   - 터미널을 실행합니다
   - `Ctrl + Shift + +`로 글자 크기를 키웁니다
   - `rpicam-hello` 명령어로 카메라를 테스트합니다
   - `rpicam-hello --timeout 0`로 미리보기를 계속 유지합니다
   - `Ctrl + C`로 미리보기를 종료합니다

4. 사진 촬영하기
   - `rpicam-still --output test.jpg` 명령어로 사진을 촬영합니다
   - 파일 탐색기로 촬영된 사진을 확인합니다
   - 이미지 뷰어로 사진을 열어봅니다

5. 타임랩스 촬영 준비하기
   - `mkdir timelapse` 명령어로 저장 폴더를 만듭니다
   - `clear` 명령어로 터미널 화면을 깨끗이 합니다

6. 타임랩스 촬영하기
   - `rpicam-still --timeout 30000 --timelapse 2000 -o timelapse/image%04d.jpg` 명령어로 30초 동안 2초 간격으로 촬영합니다
   - 촬영이 끝날 때까지 기다립니다
   - 파일 탐색기에서 촬영된 사진들을 확인합니다

7. FFmpeg 설치하기
   - `sudo apt install ffmpeg` 명령어로 FFmpeg를 설치합니다
   - 설치가 완료될 때까지 기다립니다

8. 동영상 만들기
   - `ffmpeg -r 10 -i timelapse/image%04d.jpg -s 1920x1080 output.mp4` 명령어로 동영상을 만듭니다
   - 변환이 완료될 때까지 기다립니다

9. 동영상 확인하기
   - `vlc output.mp4` 명령어로 동영상을 재생합니다
   - `vlc output.mp4 --loop` 명령어로 반복 재생할 수 있습니다

## 🔍 문제해결
- 카메라가 인식되지 않아요
  - 케이블이 올바른 방향으로 연결되었는지 확인해보세요.
  - 은색 단자가 아래를 향하도록 다시 연결해보세요.
  - 갈색 커넥터가 단단히 고정되었는지 확인해보세요.

- 카메라 화면이 안 나와요
  - 터미널에서 명령어를 정확히 입력했는지 확인해보세요.
  - `rpicam-hello` 명령어로 다시 테스트해보세요.
  - 케이블이 느슨하지 않은지 살펴보세요.

- 사진이 저장되지 않아요
  - `timelapse` 폴더가 제대로 만들어졌는지 확인해보세요.
  - 저장 경로를 정확히 입력했는지 다시 한번 보세요.
  - 디스크 공간이 충분한지 확인해보세요.

- 동영상 변환이 안 돼요
  - FFmpeg가 제대로 설치되었는지 확인해보세요.
  - 촬영된 사진들의 이름이 순서대로 있는지 확인해보세요.
  - 명령어에 오타가 없는지 다시 확인해보세요.

## 🌟 이렇게 업그레이드 해볼 수 있어요
- 자동 촬영 시스템 만들기
  매일 일정 시간에 자동으로 촬영되도록 만들 수 있어요.

- 웹에서 확인하기
  촬영된 사진을 웹 브라우저에서 바로 볼 수 있게 만들 수 있어요.

- 더 멋진 타임랩스 만들기
  - 일몰부터 일출까지 하늘의 변화를 담아보세요.
  - 식물이 자라나는 모습을 기록해보세요.
  - 구름의 움직임을 포착해보세요.

## 📚 참고 자료
- [라즈베리파이 카메라 문서](https://www.raspberrypi.com/documentation/accessories/camera.html)
- [FFmpeg 사용 가이드](https://www.ffmpeg.org/documentation.html)
- [라즈베리파이 공식 포럼](https://forums.raspberrypi.com)

> **주의사항**: 
> - 모든 명령어는 터미널에서 실행해야 해요.
> - 카메라 모듈은 정전기에 민감하니 조심히 다루세요.
> - 촬영하기 전에 충분한 저장 공간을 확보하세요.
> - 오랜 시간 촬영할 때는 전원 공급이 안정적인지 확인하세요.

