# can_simul — Releases

ESP32-C3 기반 차량 진단 CAN 시뮬레이터(OBD-II / WWH-OBD / J1939)의 **배포용 저장소**입니다.
소스 코드는 비공개이며, 이 저장소는 빌드된 펌웨어 바이너리 배포만 담당합니다.

> ⚠️ Lab use only. 실차 CAN 버스에 연결하지 말 것.

## 플래시 방법 (웹 플래셔)

별도 프로그램 설치 없이 **브라우저에서 바로** 플래시합니다.

👉 **웹 플래셔: <https://firepooh.github.io/can_simul-releases/>**

> 데스크톱 **Chrome / Edge** 필요 (Web Serial 지원). USB 케이블로 보드를 PC 에 연결하세요.

![can_simul Web Flasher](img/flasher-main.jpg)

1. 위 주소를 Chrome / Edge 로 엽니다.
2. **펌웨어 버전** 드롭다운에서 버전을 고릅니다 (기본: 최신).
   필요하면 바로 아래 **직접 다운로드** 링크로 `.bin` 파일만 받을 수도 있습니다.
3. **1. 연결 (Connect)** 클릭 → 포트 선택 창에서 보드 포트
   (예: `USB JTAG/serial debug unit`) 선택 → 연결.
4. 로그에 `Chip is ESP32-C3 …` / `[OK] 연결됨` 이 뜨면 정상 연결입니다.
5. **2. 플래시 (Flash 0x0)** 클릭 → 진행률 100% 후 `[OK] 플래시 완료` → 보드 자동 리셋.

- **Baud** 기본값은 460800. 연결이 불안정하면 115200 으로 낮춰보세요.
- 칩 전체를 지우려면 **Erase Flash** 버튼을 사용합니다.

## 하드웨어 / 콘솔

- 하드웨어: ESP32-C3 Super Mini / CAN 트랜시버 TWAI TX=GPIO4, RX=GPIO3 / 콘솔=USB Serial-JTAG
- 콘솔 접속: 임의의 시리얼 터미널로 115200 8N1 접속 후 `help` 입력
- 버전별 명령어 등 상세 사용법은 각 [Releases](../../releases) 페이지 본문(운용자 매뉴얼)을 참고하세요.

## 수동 다운로드 / 플래시 (선택)

[Releases](../../releases) 페이지에서 파일을 직접 받을 수 있습니다.

| 파일 | 설명 |
| ---- | ---- |
| `can_simul-esp32c3-vX.Y.Z-merged.bin` | 부트로더+파티션+앱을 합친 **단일 이미지**. 0x0 부터 한 번에 플래시 |
| `can_simul-esp32c3-vX.Y.Z-all.zip` | 개별 바이너리 전체 세트(app, elf, bootloader, partition, flasher_args) |

[esptool](https://github.com/espressif/esptool) 로 수동 플래시:

```bash
esptool --chip esp32c3 -p <PORT> write_flash 0x0 can_simul-esp32c3-vX.Y.Z-merged.bin
```
