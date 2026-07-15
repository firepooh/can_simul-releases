# can_simul — Releases

ESP32-C3 기반 차량 진단 CAN 시뮬레이터(OBD-II / WWH-OBD / J1939)의 **배포용 저장소**입니다.
소스 코드는 비공개이며, 이 저장소는 빌드된 펌웨어 바이너리 배포만 담당합니다.

> ⚠️ Lab use only. 실차 CAN 버스에 연결하지 말 것.

## 다운로드

[**Releases**](../../releases) 페이지에서 최신 버전을 받으세요. 각 릴리스에는 두 가지 파일이 있습니다.

| 파일 | 설명 |
| ---- | ---- |
| `can_simul-esp32c3-vX.Y.Z-merged.bin` | 부트로더+파티션+앱을 합친 **단일 이미지**. 0x0 부터 한 번에 플래시 |
| `can_simul-esp32c3-vX.Y.Z-all.zip` | 개별 바이너리 전체 세트(app, elf, bootloader, partition, flasher_args) |

## 플래시 방법

[esptool](https://github.com/espressif/esptool) 로 단일 이미지를 플래시합니다. (`<PORT>` 는 보드 COM 포트)

```bash
esptool --chip esp32c3 -p <PORT> write_flash 0x0 can_simul-esp32c3-vX.Y.Z-merged.bin
```

- 하드웨어: ESP32-C3 Super Mini / CAN 트랜시버 TWAI TX=GPIO4, RX=GPIO3 / 콘솔=USB Serial-JTAG
- 콘솔 접속: 임의의 시리얼 터미널로 115200 8N1 접속 후 `help` 입력
