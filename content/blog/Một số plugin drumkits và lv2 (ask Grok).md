---
title: Một số plugin drumkits và lv2 (ask Grok)
description: Hướng dẫn chi tiết để cài đặt và sử dụng AppImage trên Linux Mint (hoặc bất kỳ distro dựa trên Ubuntu/Debian nào)
tags:
  - Zrythm
dateCreated: 2025-12-21
---



cài đặt appimage mint

Dưới đây là hướng dẫn chi tiết để **cài đặt và sử dụng AppImage** trên **Linux Mint** (hoặc bất kỳ distro dựa trên Ubuntu/Debian nào):

### 1. Cách đơn giản nhất (khuyến nghị cho hầu hết người dùng)

1. **Tải file AppImage về máy** Ví dụ: bạn tải được file tên Kdenlive.AppImage hoặc Obsidian.AppImage,...
    
2. **Cho file quyền thực thi** Có 2 cách:
    
    - **Cách 1 - dùng chuột** (dễ nhất) Nhấp chuột phải vào file AppImage → **Properties** → tab **Permissions** → tick vào ô **Allow executing file as program** → Close.
    - **Cách 2 - dùng terminal**
        
        ```Bash
        chmod +x Tên_file.AppImage
        ```
        
        Ví dụ:
        
        ``` Bash
        chmod +x Kdenlive-24.08.2-x86_64.AppImage
        ```
        
3. **Chạy AppImage**
    
    - Nhấp đúp vào file → chương trình sẽ chạy ngay.
    - Hoặc từ terminal:
        
        
        
        ```Bash
        ./Tên_file.AppImage
        ```
        

### 2. Tích hợp AppImage vào menu (tạo shortcut)

Sau khi chạy lần đầu, bạn thường muốn nó xuất hiện trong menu ứng dụng như phần mềm bình thường.

**Cách 1 - Dùng AppImageLauncher (khuyên dùng)**

AppImageLauncher là công cụ rất tiện lợi trên Linux Mint/Ubuntu.



```Bash
# Cài AppImageLauncher (có sẵn trong repository của Linux Mint)
sudo apt update
sudo apt install appimagelauncher
```

Sau khi cài xong:

- Khi bạn nhấp đúp lần đầu vào AppImage → AppImageLauncher sẽ hỏi: → Chọn **Integrate and run** → nó sẽ tự động tạo shortcut trong menu và thêm vào /home/tên_người_dùng/.local/share/applications/

**Cách 2 - Tự tạo shortcut thủ công**

Nếu không muốn dùng AppImageLauncher:

1. Tạo file .desktop Ví dụ: kdenlive.desktop
    
    
    
    ```Bash
    nano ~/.local/share/applications/kdenlive.desktop
    ```
    
    Dán nội dung sau (thay đổi đường dẫn cho đúng):
    
    
    
    ```ini
    [Desktop Entry]
    Name=Kdenlive
    Exec=/home/tên_người_dùng/Downloads/Kdenlive-24.08.2-x86_64.AppImage
    Type=Application
    Icon=kdenlive
    Terminal=false
    Categories=AudioVideo;Video;
    ```
    
2. Cho file quyền thực thi:
    
    
    
    ```Bash
    chmod +x ~/.local/share/applications/kdenlive.desktop
    ```
    

### 3. Một số mẹo hữu ích

- **Di chuyển AppImage ra thư mục cố định** Nên để trong /opt/ hoặc thư mục ~/Applications/ để dễ quản lý.
    
    Ví dụ:
    
    
    
    ```Bash
    mkdir -p ~/Applications
    mv Kdenlive*.AppImage ~/Applications/
    ```
    
- **Cập nhật AppImage** Hầu hết AppImage mới hỗ trợ tự cập nhật khi chạy:
    
    - Mở AppImage → vào menu **Help → Check for updates**
- **Xóa AppImage đã tích hợp** Nếu dùng AppImageLauncher → nhấp chuột phải vào shortcut trong menu → **Remove integration**
    

Chúc bạn cài đặt thành công! Nếu bạn đang cố chạy AppImage cụ thể nào mà bị lỗi, cứ gửi tên file hoặc thông báo lỗi mình hỗ trợ tiếp nhé!

có bộ trống nào có thể load sample như hydrogen nhưng là lv2 không?

Có, có một số **plugin LV2** hỗ trợ load sample/drumkit (tương tự Hydrogen), và chúng được thiết kế để dùng trong DAW (như Ardour, Carla, Reaper, Qtractor,...) với MIDI input. Dưới đây là các lựa chọn tốt nhất hiện nay (dựa trên cộng đồng Linux Audio năm 2025):

### 1. **Drumlabooh** (Khuyến nghị mạnh nhất – hiện đại nhất)

- **Đặc điểm**:
    - Load trực tiếp Hydrogen drumkit (hỗ trợ đầy đủ layer, velocity).
    - Hỗ trợ thêm SFZ và format riêng của nó.
    - Có mixer built-in, multi-out (lên đến 36 channel), FX (LP/HP filter, Analog warmth), auto hihat choke, round-robin, layers (tối đa 127 layer/instrument).
    - Giao diện đẹp, hỗ trợ hình ảnh drumkit.
- **Hỗ trợ**: LV2 + VST3 (Linux & Windows).
- **Link**: [https://psemiletov.github.io/drumlabooh/](https://psemiletov.github.io/drumlabooh/?referrer=grok.com)
- **Cài đặt trên Linux Mint**:
    
    
    
    ```Bash
    sudo apt install git cmake build-essential libasound2-dev libfreetype6-dev libx11-dev libxcomposite-dev libxcursor-dev libxext-dev libxinerama-dev libxrandr-dev libxrender-dev libfontconfig1-dev libjack-jackd2-dev libgl1-mesa-dev libglu1-mesa-dev
    git clone https://github.com/psemiletov/drumlabooh.git
    cd drumlabooh
    mkdir build && cd build
    cmake .. -DCMAKE_INSTALL_PREFIX=/usr
    make -j$(nproc)
    sudo make install
    ```
    
    Sau đó load trong Carla hoặc Ardour như LV2 plugin.

### 2. **Drumrox** (Fork của DrMr, đơn giản hơn)

- Load Hydrogen kit (hỗ trợ format mới nhất).
- Giao diện GTK, multi-out.
- Tương tự DrMr nhưng fix nhiều bug cũ.
- **Link**: [https://psemiletov.github.io/drumrox/](https://psemiletov.github.io/drumrox/?referrer=grok.com)
- Thường có sẵn trong repo hoặc build từ source tương tự Drumlabooh.

### 3. **DrMr** (Cũ nhưng vẫn dùng tốt)

- Load Hydrogen kit (layer, velocity).
- Có UI GTK để chọn kit, chỉnh gain/pan.
- Multi-out, save state tốt.
- **Link**: [https://github.com/nicklan/drmr](https://github.com/nicklan/drmr?referrer=grok.com) (hoặc fork falkTX/drmr)
- Nhiều distro có sẵn (apt install drmr-lv2).

### 4. **Fabla** (Đơn giản, load sample thủ công)

- LV2 drum sampler, load sample riêng lẻ (không load Hydrogen kit trực tiếp).
- Có sẵn một số kit (bao gồm sample từ Hydrogen).
- **Link**: [http://openavproductions.com/fabla/](http://openavproductions.com/fabla/?referrer=grok.com)
- Thường có trong repo (apt install fabla).

### 5. **x42-avldrums** (Kit cố định, rất chất lượng)

- Load kit AVL (Black Pearl, Red Zeppelin,...).
- 5 velocity layers, multi-out.
- Không load Hydrogen kit, nhưng sound rất tốt.
- **Link**: [https://x42-plugins.com/x42/x42-avldrums](https://x42-plugins.com/x42/x42-avldrums?referrer=grok.com)
- Cài: sudo apt install x42-plugins

### 6. **drumkv1** (Old-school, load sample)

- LV2 drum sampler, load sample thủ công (không Hydrogen).
- **Link**: [https://drumkv1.sourceforge.io/](https://drumkv1.sourceforge.io/?referrer=grok.com)

**Tóm lại**:

- Nếu bạn muốn **gần giống Hydrogen nhất** (load kit trực tiếp, layer, velocity) → **Drumlabooh** là lựa chọn tốt nhất hiện tại.
- Nếu dùng Ardour/Carla → thử Drumlabooh hoặc Drumrox.

Bạn dùng DAW nào (Ardour, Carla,...)? Nếu cần hướng dẫn build/cài cụ thể cho Mint, mình hỗ trợ thêm nhé!

1,3 giây

![Web page favicon](https://imgs.search.brave.com/xxsA4YxzaR0cl-DBsH9-lpv2gsif3KMYgM87p26bs_o/rs:fit:32:32:1:0/g:ce/aHR0cDovL2Zhdmlj/b25zLnNlYXJjaC5i/cmF2ZS5jb20vaWNv/bnMvYWQyNWM1NjA5/ZjZmZjNlYzI2MDNk/N2VkNmJhYjE2MzZl/MDY5ZTMxMDUzZmY1/NmU3NWIzNWVmMjk0/NTBjMjJjZi9naXRo/dWIuY29tLw)

![Web page favicon](https://imgs.search.brave.com/IGf6CQXoFSGI8dYw-A5oN3ftJ8RFtgAlFM8T9yFDPjc/rs:fit:32:32:1:0/g:ce/aHR0cDovL2Zhdmlj/b25zLnNlYXJjaC5i/cmF2ZS5jb20vaWNv/bnMvODRiNjBhZmIw/MTYwNTNmNjNhYjc2/MDExODQ0YzM5ODBj/YThjMTM4ODZjYTlk/ZjkzMDNiMjE1MzNl/MGIwMWQ2Ni9saW51/eC1hdWRpby1kZXYu/bGludXhhdWRpby5u/YXJraXZlLmNvbS8)

![Web page favicon](https://imgs.search.brave.com/Ka3AeES8OY8Dn-ZtlzFoYz6f0ri9SCKtSmCJagw7gs8/rs:fit:32:32:1:0/g:ce/aHR0cDovL2Zhdmlj/b25zLnNlYXJjaC5i/cmF2ZS5jb20vaWNv/bnMvMjdlZjk4ZjI2/YmM4OGQ1YmFjYjg5/ZGYzMjlhMzA2ODYy/MTNmODFiMmJiMmRm/Yjg5YWMxMzc5MmZk/NjM5ZTQyZS9vcGVu/aHViLm5ldC8)

75 sources

dùng zrythm, nó tự động load lv2 không?

Có! **Zrythm** hỗ trợ **tự động load LV2 plugin** rất tốt, và đây là một trong những điểm mạnh của nó so với một số DAW khác.

### Cách Zrythm load LV2

1. **Tự động quét LV2** Khi bạn mở Zrythm lần đầu (hoặc sau khi cài plugin mới), nó sẽ **tự động quét** các thư mục LV2 chuẩn:
    
    - /usr/lib/lv2/
    - /usr/lib64/lv2/
    - /usr/local/lib/lv2/
    - ~/.lv2/
    - ~/.local/share/lv2/
    
    → Nếu bạn cài plugin LV2 bằng sudo apt install hoặc build từ source (với make install), Zrythm sẽ tự nhận diện.
    
2. **Chỉ cần refresh plugin** Nếu bạn vừa cài plugin mà Zrythm chưa thấy:
    
    - Vào **Edit → Preferences → Plugins** → nhấn nút **Scan for new plugins** (hoặc **Rescan**).
    - Hoặc restart Zrythm là nó quét lại.
3. **Thêm plugin vào project**
    
    - Nhấn **+** ở track mới → chọn **Instrument** → tìm plugin LV2 (như Drumlabooh, Drumrox, x42-avldrums,...) trong danh sách.
    - Zrythm hiển thị rõ ràng **LV2** bên cạnh tên plugin, và có filter để lọc theo loại (Drum, Sampler, Synth,...).

### Lưu ý khi dùng Zrythm với drum plugin LV2

- **Drumlabooh**, **Drumrox**, **DrMr**, **x42-avldrums** đều hoạt động tốt trong Zrythm.
- Nếu plugin có **multi-output** (như Drumlabooh hoặc x42-avldrums), Zrythm hỗ trợ **routing riêng từng channel** (ví dụ: kick ra bus 1, snare ra bus 2,...).
- Zrythm cũng hỗ trợ **MIDI patterns** để lập trình beat rất dễ, tương tự Hydrogen.

### Kiểm tra plugin đã load chưa

- Vào **Window → Plugin Browser** → tab **Instruments** hoặc **Drums**.
- Nếu thấy plugin như **Drumlabooh** hoặc **x42 AVL Drums**, là đã OK.

Nếu bạn đang dùng **Linux Mint** và muốn thử **Drumlabooh** (tốt nhất cho Hydrogen-like), cứ làm theo hướng dẫn build mình gửi trước đó. Sau khi build xong, chạy Zrythm → Rescan plugin → sẽ thấy ngay.

Bạn đã thử cài plugin nào chưa, hay cần mình hướng dẫn chi tiết build Drumlabooh cho Zrythm?

1,6 giây

có bộ plugin nào mạnh như wave cho zrythm mint không?

Có, trong **Zrythm** trên **Linux Mint** (và Linux nói chung), bạn không có **plugin LV2** nào "mạnh như Waves" (vì Waves là bundle thương mại cao cấp, chuyên nghiệp, với sound signature đặc trưng như CLA-2A, SSL, H-Delay, API,...). Tuy nhiên, có nhiều bộ **LV2 plugin miễn phí/mở nguồn** chất lượng cao, chuyên nghiệp, được cộng đồng Linux Audio dùng thay thế rất tốt cho Waves.

Dưới đây là các bộ **LV2 mạnh nhất** (2025) cho mixing/mastering trong Zrythm:

### 1. **Calf Studio Gear** (Bộ tốt nhất, gần Waves nhất)

- **Tại sao mạnh?** Đây là suite LV2 **hoàn chỉnh nhất** cho Linux: compressor, multiband compressor, limiter, EQ parametric, de-esser, gate, reverb, delay, exciter, stereo tools,... Nhiều người so sánh sound của Calf compressor/multiband với Waves CLA series hoặc SSL (clean, musical, không bị distort khi đẩy mạnh). Multiband compressor/limiter rất pro cho mastering.
- **Cài trên Linux Mint**:
    
    
    
    ```Bash
    sudo apt update
    sudo apt install calf-plugins
    ```
    
- **Trong Zrythm**: Tự động load sau rescan → dùng cho track/instrument/master bus.

### 2. **x42-plugins** (Rất mạnh, clean & transparent)

- **Tại sao mạnh?** Compressor (darc.lv2 - inspired by zita-dc1, rất clean), limiter (dpl.lv2 - look-ahead peak limiter), EQ parametric (fil4.lv2), matrix mixer, meters pro,... Sound transparent, ít màu, giống Waves API/SSL clean series. Limiter dpl.lv2 thay thế tốt cho Waves L2/L3.
- **Cài**:
    
    
    
    ```Bash
    sudo apt install x42-plugins
    ```
    
- **Khuyến nghị**: Dùng x42-compressor + x42-limiter + fil4 EQ cho chain master.

### 3. **LSP-plugins** (Bộ LV2 lớn nhất, cực kỳ mạnh)

- **Tại sao mạnh?** Hơn 300 plugin: compressor (mono/stereo/multiband), EQ parametric/dynamic, limiter, gate, de-esser, maximizer, tape saturation, reverb,... Compressor/limiter/multiband của LSP rất pro, sound sạch, transparent, được dùng trong mixing/mastering pro. Có dynamic EQ, sidechain compressor giống Waves F6.
- **Cài**:
    
    
    
    ```Bash
    sudo apt install lsp-plugins-lv2
    ```
    
- **Trong Zrythm**: Tìm "LSP Compressor Stereo" hoặc "LSP Multiband Compressor".

### 4. **ZamAudio** (Compressor & Multiband hay nhất)

- **Tại sao mạnh?** ZamComp, ZaMultiComp (multiband compressor), ZaMaximizer,... sound rất musical, punchy, thay thế tốt Waves SSL G Compressor hoặc multiband.
- **Cài**:
    
    
    
    ```Bash
    sudo apt install zam-plugins
    ```
    

### 5. **Infamous Plugins** (Thêm màu analog)

- Distortion, waveshaper, tape emulation,... thay thế Waves J37 hoặc Abbey Road.
- **Cài**: Build từ GitHub[github.com](https://github.com/ssj71/infamousPlugins) hoặc dùng repo nếu có.

### 6. **Zrythm's own ZPlugins** (Đi kèm Zrythm)

- EQ, compressor, limiter, reverb,... cơ bản nhưng chất lượng cao.
- Cài: Khi cài Zrythm, nó tự bundle.

### Tóm tắt so sánh với Waves (thay thế gần nhất)

|Waves Plugin|LV2 Thay Thế Tốt Nhất|Bộ Plugin|
|---|---|---|
|CLA-2A / CLA-76|Calf Compressor, x42-darc, LSP Compressor|Calf, x42, LSP|
|SSL G Compressor|ZamComp, x42-darc|ZamAudio, x42|
|API / SSL EQ|Calf 8-band EQ, x42-fil4, LSP Parametric EQ|Calf, x42, LSP|
|F6 Dynamic EQ|LSP Dynamic EQ (rất mạnh)|LSP-plugins|
|L2/L3 Limiter|x42-dpl, Calf Limiter, LSP Limiter|x42, Calf, LSP|
|Multiband|Calf Multiband Compressor/Limiter|Calf|
|Tape Saturation|Infamous Tape, ChowTapeModel (nếu có LV2 port)|Infamous|

**Khuyến nghị cho Zrythm trên Mint**: Bắt đầu với **Calf + x42 + LSP** (cài hết bằng apt). Sau đó rescan plugin trong Zrythm (Edit → Preferences → Plugins → Rescan). Chain master: LSP Compressor → Calf Multiband Compressor → x42 Limiter + Meter.

Nếu bạn cần sound "màu" analog hơn (như CLA series), thử thêm **Infamous** hoặc **Chow** plugins (có LV2).

Bạn muốn chain cụ thể cho vocal/mastering hay cần hướng dẫn build plugin nào? Mình hỗ trợ tiếp! 🎛️

1,2 giây

![Web page favicon](https://imgs.search.brave.com/xxsA4YxzaR0cl-DBsH9-lpv2gsif3KMYgM87p26bs_o/rs:fit:32:32:1:0/g:ce/aHR0cDovL2Zhdmlj/b25zLnNlYXJjaC5i/cmF2ZS5jb20vaWNv/bnMvYWQyNWM1NjA5/ZjZmZjNlYzI2MDNk/N2VkNmJhYjE2MzZl/MDY5ZTMxMDUzZmY1/NmU3NWIzNWVmMjk0/NTBjMjJjZi9naXRo/dWIuY29tLw)

![Web page favicon](https://imgs.search.brave.com/nN2tIjHApHKwiDHgH-ojxlkhPm0-KE-J9-nWF5rgpSQ/rs:fit:32:32:1:0/g:ce/aHR0cDovL2Zhdmlj/b25zLnNlYXJjaC5i/cmF2ZS5jb20vaWNv/bnMvMmQ1MGZiOGUw/M2Q1N2U4NjEwYmQy/ODQ3MzQyMjUzOWEy/MDU1NDQ2ZGZlYmUz/YWRmM2M0NzNhMTMz/YTVmMzZkYy93d3cu/bG9vcGVybWFuLmNv/bS8)

![Web page favicon](https://imgs.search.brave.com/2Jc5hqFpbJGNZ3zerbDfTaduqBO0nkoLwGgND62r62s/rs:fit:32:32:1:0/g:ce/aHR0cDovL2Zhdmlj/b25zLnNlYXJjaC5i/cmF2ZS5jb20vaWNv/bnMvY2Q1ZjQ1Y2Fj/YzEwMDJiZDI0YWFj/YzIyNjMyOGI3MWRm/YWE0YTEzOGNkYTBl/YWJlOTI0YTg0ZmVm/YTkzMzU3NC9tYW51/YWwuenJ5dGhtLm9y/Zy8)

65 sources

dùng dumlahnoo sao để lấy kit từ hydrogen được?

Có, **Drumlabooh** hỗ trợ load **Hydrogen drumkit** trực tiếp (định dạng .h2drumkit hoặc thư mục chứa drumkit.xml + samples), và đây là một trong những tính năng chính của nó (tương thích tốt với Hydrogen kit format hiện đại).

### Cách load Hydrogen kit vào Drumlabooh (trong Zrythm)

1. **Đảm bảo kit Hydrogen đã có sẵn** Hydrogen kit thường nằm ở:
    
    - ~/.hydrogen/data/drumkits/ (user kits)
    - /usr/share/hydrogen/data/drumkits/ (system kits)
    - Hoặc thư mục bạn tự copy (ví dụ: ~/Drumkits/).
    
    Nếu bạn dùng kit từ Hydrogen, chỉ cần giữ nguyên cấu trúc: thư mục kit chứa drumkit.xml và các file sample (.wav/.ogg).
    
2. **Load trong Drumlabooh GUI**
    
    - Trong Zrythm: Thêm track Instrument → Load Drumlabooh (LV2).
    - Mở plugin GUI (nhấp đúp vào plugin).
    - Ở phần **Kit selector** (thường là dropdown hoặc button "Load kit" ở top):
        - Chọn **Hydrogen** (hoặc nó tự detect).
        - Duyệt đến thư mục kit → chọn thư mục chứa drumkit.xml (hoặc file .h2drumkit nếu có).
        - Load → Plugin sẽ đọc XML, load samples, và hiển thị instruments (tối đa 36 slots, hỗ trợ layers lên đến 16 từ Hydrogen, auto hihat choke,...).
3. **Nếu không thấy kit trong list**
    
    - Drumlabooh scan các thư mục chuẩn của Hydrogen + một số custom.
    - Để thêm thư mục custom: Tạo thư mục ~/drum_dirs/ (hoặc ~/.drumlabooh/drum_dirs/) → copy kit Hydrogen vào đó (ví dụ: ~/drum_dirs/MyHydrogenKit/).
        - Restart Zrythm hoặc reload plugin → kit sẽ xuất hiện trong selector (có "magic" scan như dev nói).
    - Hoặc build/install với -DINSTALLKITS=OFF nếu bạn không muốn kit default (nhưng vẫn load manual được).
4. **Mẹo dùng Hydrogen kit tốt hơn trong Drumlabooh**
    
    - **MIDI mapping**: Đặt "MIDI map mode" trong GUI thành **"Kit"** (nếu kit có note mapping trong XML) → giữ nguyên mapping từ Hydrogen (thường GM standard).
    - Nếu mapping bị lệch → dùng **"Auto"** và chỉnh "Base MIDI note" (default 36).
    - Kit load xong, bạn thấy log ở GUI (kit type: Hydrogen, RAM used, load time) – nếu lỗi, check log để fix (thường do sample path sai).
5. **Nếu gặp vấn đề**
    
    - Đảm bảo dùng phiên bản **Drumlabooh mới nhất** (hiện 12.0.0 hoặc cao hơn, fix nhiều bug Hydrogen loader).
    - Nếu kit cũ (Hydrogen <1.0), thử convert bằng Hydrogen trước (load → save lại).
    - Check DAW compatibility wiki: [https://github.com/psemiletov/drumlabooh/wiki/DAW-Compatibility](https://github.com/psemiletov/drumlabooh/wiki/DAW-Compatibility?referrer=grok.com) (Zrythm hỗ trợ tốt LV2).

Bạn thử load kit nào cụ thể chưa? Nếu gặp lỗi (ví dụ: "failed to load samples" hoặc crash), gửi tên kit/log mình check giúp! 🎶

1,9 giây

![Web page favicon](https://imgs.search.brave.com/xxsA4YxzaR0cl-DBsH9-lpv2gsif3KMYgM87p26bs_o/rs:fit:32:32:1:0/g:ce/aHR0cDovL2Zhdmlj/b25zLnNlYXJjaC5i/cmF2ZS5jb20vaWNv/bnMvYWQyNWM1NjA5/ZjZmZjNlYzI2MDNk/N2VkNmJhYjE2MzZl/MDY5ZTMxMDUzZmY1/NmU3NWIzNWVmMjk0/NTBjMjJjZi9naXRo/dWIuY29tLw)

![Web page favicon](https://imgs.search.brave.com/xxsA4YxzaR0cl-DBsH9-lpv2gsif3KMYgM87p26bs_o/rs:fit:32:32:1:0/g:ce/aHR0cDovL2Zhdmlj/b25zLnNlYXJjaC5i/cmF2ZS5jb20vaWNv/bnMvYWQyNWM1NjA5/ZjZmZjNlYzI2MDNk/N2VkNmJhYjE2MzZl/MDY5ZTMxMDUzZmY1/NmU3NWIzNWVmMjk0/NTBjMjJjZi9naXRo/dWIuY29tLw)

![Web page favicon](https://imgs.search.brave.com/xxsA4YxzaR0cl-DBsH9-lpv2gsif3KMYgM87p26bs_o/rs:fit:32:32:1:0/g:ce/aHR0cDovL2Zhdmlj/b25zLnNlYXJjaC5i/cmF2ZS5jb20vaWNv/bnMvYWQyNWM1NjA5/ZjZmZjNlYzI2MDNk/N2VkNmJhYjE2MzZl/MDY5ZTMxMDUzZmY1/NmU3NWIzNWVmMjk0/NTBjMjJjZi9naXRo/dWIuY29tLw)

55 sources

# Are you satisfied with Grok's answer?

  

## Nâng cấp lên SuperGrok

Hướng dẫn cài đặt AppImage trên Linux Mint - Grok

---
Shen2H X Scorprien: from ashses