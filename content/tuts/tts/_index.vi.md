---
title: Chuyển Văn bản thành Giọng nói
weight: 1
prev: /tts
next: /tts/kokoro
sidebar:
  open: true
---

## Bảng xếp hạng

Mô hình AI chuyển Văn bản thành Giọng nói

Bảng xếp hạng các API chuyển văn bản thành giọng nói được so sánh bên dưới bằng cách sử dụng dữ liệu của bên thứ ba từ bảng xếp hạng [Artificial Analysis leaderboard](https://artificialanalysis.ai/text-to-speech/leaderboard) (tính đến tháng 4 năm 2026), các chỉ số độ tin cậy trong sản xuất và tính linh hoạt trong triển khai, bao gồm các tiêu chuẩn về độ trễ, phạm vi ngôn ngữ và các tùy chọn tích hợp.

Inworld AI TTS-1.5 Max xếp hạng #1 với điểm ELO là 1.208 dựa trên hàng nghìn so sánh sở thích của người dùng ẩn danh, với độ trễ P90 dưới 250ms.

| Hạng | Công ty | Model | ELO | Giá API |
| :-- | :-- | :-- | :-- | :-- |
| #1  | Inworld | Inworld TTS 1.5 Max  | 1,208 | $50 /1M chars |
| #2  | Google  | Gemini 3.1 Flash TTS | 1,204 | $36.6 /1M chars |
| #3  | ElevenLabs | Eleven v3 | 1,179 | $100 /1M chars |
| #4  | MiniMax | Speech 2.8 HD | 1,165 | $100 /1M chars |
| #5  | StepFun | Step TTS 2 (Mar 2026) | 1,153 | $50 /1M chars |
| #6  | Fish Audio | Fish Audio S2 Pro (Open Weights) | 1,130 | $15 /1M chars |
| #7  | Microsoft Azure | Azure HD 2.5 | 1,116 | $22 /1M chars |
| #8  | StepFun | Step Audio EditX (Open Weights) | 1,101 | N/A |
| #9  | OpenAI | TTS-1 | 1,101 | $15 /1M chars |
| #10 | Cartesia | Sonic 3 | 1,069 | $39 /1M chars |
| #11 | NVIDIA | Magpie-Multilingual 357M (Open Weights) | 1,063 | N/A |
| #12 | Google | Studio | 1,062 | $160 /1M chars |
| #13 | Speechify | SIMBA 1.6 | 1,058 | $10 /1M chars |
| #14 | Kokoro | Kokoro 82M v1.0 (Open Weights) | 1,056 | $0.7 /1M chars |
| #15 | Amazon | Polly Generative | 1,055 | $30.0 /1M chars |
| #16 | async | AsyncFlow V2, async | 1,051 | $8.3 /1M chars |
| #17 | Maya Research | Maya1 (Open Weights) | 1,051 | N/A |
| #18 | Mistral | Voxtral TTS (Open Weights) | 1,044 | $16 /1M chars |
| #19 | Hume AI | Octave 2 | 1,044 | $87.5 /1M chars |
| #20 | Google | Chirp 3: HD | 1,041 | $30 /1M chars |
| #21 | Resemble AI | Chatterbox HD | 1,036 | $40 /1M chars |
| #22 | Google | Journey | 1,029 | $16 0 /1M chars |
| #23 | Microsoft Azure | MAI-Voice-1 | 1,024 | N/A |
| #24 | Xiaomi | MiMo-V2-TTS | 1,021 | N/A |
| #25 | Smallest.ai | Lightning v3.1 | 1,015 | $25 /1M chars |
| #26 | Resemble AI | Chatterbox (Open Weights) | 1,007 | $25 /1M chars |
| #27 | Zyphra | Zonos-v0.1 (Open Weights) | 1,000 | $20 /1M chars |
| #28 | Rime | Arcana v3 | 975 | $40 /1M chars |
| #29 | LMNT | LMNT | 967 | $49 /1M chars |
| #30 | Murf AI | Murf Speech Gen 2 | 956 | $100 /1M chars |
| #31 | OpenVoice | OpenVoice v2 (Open Weights) | 951 | $8.3 /1M chars |
| #32 | Neuphonic | Neuphonic TTS | 938 | $20.8 /1M chars |
| #33 | Alibaba | Qwen3 TTS | 936 | N/A |
| #34 | Coqui | XTTS v2 (Open Weights) | 885 | $40.4 /1M chars |
| #35 | StyleTTS  | StyleTTS 2 (Open Weights) | 880 | $2.8 /1M chars |
| #36 | MetaVoice | MetaVoice v1 | 767 | N/A |

Độ trễ dưới 200ms hiện nay đã có thể đạt được nhờ các kiến ​​trúc mạng thần kinh hiện đại, và việc sao chép giọng nói không cần huấn luyện từ đoạn âm thanh dài 3-15 giây đã trở thành tính năng tiêu chuẩn chứ không còn là tính năng cao cấp nữa.

## Top 27 mô hình AI TTS theo xếp hạng theo ELO

{{< youtube D8_wft9Bd84 >}}


## 1. Inworld AI TTS

**Tổng quan nhanh**
Inworld giữ vị trí số 1 trên bảng xếp hạng Giọng nói Phân tích Nhân tạo với mô hình TTS 1.5 Max (ELO 1.238). Trên bảng xếp hạng HuggingFace TTS riêng biệt, Inworld TTS đứng ở vị trí số 2 (ELO 1.578). Mô hình TTS-1 Max thế hệ trước cũng nằm trong top 5.

Giá thành tạo giọng nói của Inworld khá cạnh tranh so với các lựa chọn thay thế (xem bảng giá) đối với mô hình hàng đầu. Cùng một dung lượng trên các đối thủ cạnh tranh xếp hạng cao hơn có giá từ 6.000 đến 20.600 đô la tùy thuộc vào nhà cung cấp.

Về mặt kỹ thuật, Inworld sử dụng hai kích thước mô hình: một mô hình nhẹ hơn với 1 tỷ tham số (Mini) được tối ưu hóa cho tốc độ, và một mô hình lớn hơn với 8 tỷ tham số (Max) được tối ưu hóa cho chất lượng. Cả hai đều truyền phát âm thanh qua WebSocket hoặc truyền phát ngay lập tức khi được tổng hợp, không có bước đệm. Trong môi trường sản xuất, điều đó có nghĩa là độ trễ đầu cuối dưới 130ms đối với Mini và dưới 250ms đối với Max, được đo bằng P90 toàn diện bao gồm cả chi phí mạng.

Chất lượng cao (xếp hạng 1 về chất lượng), giá cả cạnh tranh (xem giá cả) và tốc độ tạo nhanh (dưới 250ms) khiến Inworld trở thành lựa chọn mạnh mẽ cho các nhà phát triển xây dựng ứng dụng tạo giọng nói AI.

**Phù hợp cho**:
Các tác nhân AI đàm thoại yêu cầu hội thoại đa lượt tự nhiên, các nền tảng học ngôn ngữ cần giọng nói đa ngôn ngữ biểu cảm ở quy mô người tiêu dùng và các nhà phát triển yêu cầu chất lượng hàng đầu với chi phí thấp nhất trên mỗi ký tự.

**Ưu điểm:**
- Xếp hạng #1 về Phân tích Nhân tạo (TTS 1.5 Max, ELO 1.238), xếp hạng chất lượng độc lập cao nhất trong số các mô hình TTS
- Giá cả cạnh tranh trên mỗi ký tự. Giá thành thấp hơn đáng kể so với các giải pháp thay thế có chất lượng tương đương hoặc cao hơn
- Độ trễ đầu cuối P90 dưới 250ms (Tối đa), dưới 130ms (Tối thiểu), được công bố dưới dạng số liệu toàn bộ hệ thống, không chỉ suy luận
- Sao chép giọng nói miễn phí từ 5-15 giây âm thanh
- Hệ thống xử lý giọng nói hoàn chỉnh với API thời gian thực, cung cấp khả năng điều phối và quan sát LLM tích hợp
- Triển khai hoàn toàn tại chỗ cho các doanh nghiệp cần chủ quyền dữ liệu, kết hợp với định tuyến không phụ thuộc vào mô hình trên hàng trăm LLM
- Chứng nhận SOC2 Loại II, GDPR, HIPAA với BAA, chế độ Không lưu trữ dữ liệu
- Thẻ cảm xúc đánh dấu âm thanh ([vui vẻ], [buồn bã], [thì thầm]) và phi ngôn ngữ ([ho], [thở dài], [thở])

**Nhược điểm**:
- Hỗ trợ 15 ngôn ngữ. Nếu bạn cần phạm vi ngôn ngữ rộng hơn hiện nay, đây là một thiếu sót thực sự. Các thị trường thương mại chính (tiếng Anh, tiếng Tây Ban Nha, tiếng Pháp, tiếng Hàn, tiếng Trung, tiếng Nhật, tiếng Đức, và nhiều hơn nữa) đã được hỗ trợ, nhưng các giọng địa phương và ngôn ngữ ít phổ biến hơn hiện chưa có.

- Sản phẩm TTS ra mắt tháng 6 năm 2025. Chưa đầy một năm kinh nghiệm sản xuất so với các nhà cung cấp lâu năm có lịch sử triển khai nhiều năm.

**Giá cả**
- Xem bảng giá để biết mức giá TTS hiện tại
- Sao chép giọng nói không cần huấn luyện: Miễn phí
- Gói miễn phí: 2 triệu ký tự cho người dùng mới
- Cài đặt tại chỗ: Giá doanh nghiệp tùy chỉnh

**Ý kiến ​​người dùng**:
Talkpal AI, một nền tảng học ngôn ngữ với hơn 5 triệu người dùng, đã tích hợp Inworld TTS cho toàn bộ người dùng của họ. Thử nghiệm A/B cho thấy giảm 40% chi phí, tăng 7% mức độ sử dụng tính năng và tăng 4% tỷ lệ giữ chân người dùng trong vòng bốn tuần. Bible Chat đã mở rộng các tính năng giọng nói AI cho hàng triệu người dùng đồng thời giảm chi phí hơn 90% so với nhà cung cấp TTS trước đây của họ.


## 2. Google Cloud Text-to-Speech

**Phù hợp nhất cho**: Các doanh nghiệp toàn cầu yêu cầu phạm vi ngôn ngữ rộng và tích hợp cơ sở hạ tầng GCP.

**Ưu điểm**:
- Hơn 380 giọng nói trên hơn 75 ngôn ngữ cung cấp phạm vi phủ sóng toàn cầu vượt trội cho các ứng dụng đa ngôn ngữ
- Tích hợp trực tiếp GCP với Compute Engine, Cloud Storage và BigQuery giúp giảm độ phức tạp của cơ sở hạ tầng
- Hỗ trợ SSML cho phép tùy chỉnh tạm dừng, phát âm và định dạng ngày/giờ
- 1 triệu ký tự miễn phí hàng tháng cho giọng nói tiêu chuẩn hỗ trợ thử nghiệm phát triển
- Mô hình Gemini 3.1 với khả năng điều khiển dựa trên lời nhắc và hội thoại đa người nói

**Nhược điểm**:
- Khả năng biểu cảm cảm xúc hạn chế, một số giọng nói nghe có vẻ robot so với các nhà cung cấp chuyên biệt
- Thiết lập GCP phức tạp yêu cầu kích hoạt thanh toán, tài khoản dịch vụ và quản lý khóa JSON
- Tốc độ giảm mạnh được báo cáo với giọng nói Chirp3-HD, trong đó 5 phút âm thanh mất hơn 10 phút để tạo ra

**Giá cả**: Gemini 3.1 Flash TTS có giá 0,50 đô la cho mỗi triệu mã thông báo đầu vào và 10,00 đô la cho mỗi triệu mã thông báo đầu ra âm thanh. Chirp 3 HD có giá 30 đô la cho mỗi triệu ký tự sau khi được sử dụng miễn phí 1 triệu ký tự. WaveNet có giá 4 đô la cho mỗi triệu ký tự sau khi sử dụng miễn phí 4 triệu ký tự.

## 3. ElevenLabs

**Phù hợp cho**: Lồng tiếng, sách nói và tạo nội dung yêu cầu giọng kể trau chuốt, giàu cảm xúc.

**Ưu điểm**:
- Thư viện giọng nói phong phú với hơn 10.000 giọng nói được cộng đồng chia sẻ, cung cấp nhiều lựa chọn nhân vật đa dạng
- Eleven v3 mở rộng hỗ trợ ngôn ngữ lên 74 ngôn ngữ
- Độ trễ Flash v2.5 khoảng 75ms trên 32 ngôn ngữ cho các ứng dụng thời gian thực
- Nền tảng AI đàm thoại với độ trễ dưới 100ms và tự động phát hiện ngôn ngữ
- Sao chép giọng nói chuyên nghiệp từ 30 phút âm thanh tạo ra bản sao gần như hoàn hảo

**Nhược điểm**:
- Giá cao hơn so với một số đối thủ cạnh tranh có xếp hạng chất lượng tương đương hoặc cao hơn
- Giá cả phức tạp dựa trên tín dụng với chi phí biến động và phí LLM ẩn khiến việc lập ngân sách khó dự đoán
- Flash v2.5 đánh đổi khả năng biểu cảm lấy tốc độ, đòi hỏi sự thỏa hiệp giữa độ trễ và phạm vi cảm xúc

**Giá cả**: Giá API đa ngôn ngữ v2/v3 bắt đầu từ 120 đô la Mỹ cho mỗi triệu ký tự. Các mô hình Flash/Turbo có giá khởi điểm từ 60 đô la mỗi triệu ký tự. Có các gói đăng ký với chiết khấu theo số lượng. Xem [bảng giá ElevenLabs](https://elevenlabs.io/pricing) để biết giá hiện tại.


## 4. MiniMax Speech

**Phù hợp cho**: Các nhà phát triển nhạy cảm về chi phí cần chất lượng hàng đầu với khả năng sao chép giọng nói nhanh chóng.

**Ưu điểm**:
- Nhiều mô hình nằm trong top 10, với một số mô hình giọng nói được xếp hạng cao nhất trên Artificial Analysis tính đến tháng 4 năm 2026
- Giá cả cạnh tranh ở mức 60 đô la Mỹ/triệu ký tự cho phiên bản Turbo và 100 đô la Mỹ/triệu ký tự cho phiên bản HD
- Phản hồi dưới 2 giây cho các đầu vào thông thường với thông lượng hàng nghìn ký tự mỗi giây
- Hỗ trợ 32 ngôn ngữ với kiến ​​trúc Transformer tự hồi quy cộng với Flow-VAE để sao chép không cần dữ liệu đầu vào
- Sao chép giọng nói từ 10 giây âm thanh tạo ra các mô hình giọng nói tùy chỉnh nhanh chóng

**Nhược điểm**:
- Độ phức tạp của API theo khu vực yêu cầu phải khớp máy chủ API và khóa theo khu vực, gây ra lỗi Khóa API không hợp lệ trong quá trình thiết lập
- Phiên bản tiếng Trung có những hạn chế về tính năng sao chép giọng nói, hạn chế chức năng dựa trên khu vực
- Sự phân mảnh phiên bản mô hình trên Speech-02, Speech-2.5, Speech-2.6 và Speech-2.8 gây nhầm lẫn khi lựa chọn

**Giá cả**:
- Speech-02-Turbo có giá 60 đô la Mỹ/triệu ký tự. Phần mềm Speech-02-HD có giá 100 đô la cho mỗi triệu ký tự. Sao chép giọng nói có giá 3 đô la cho mỗi giọng nói.


## 9. OpenAI TTS-1

**Phù hợp cho**: Các nhà phát triển ưu tiên tích hợp hệ sinh thái OpenAI thống nhất và tùy chỉnh giọng nói dựa trên hướng dẫn.

**Ưu điểm**:
- Xếp hạng chất lượng cao, nằm trong nhóm hàng đầu về Phân tích Nhân tạo dựa trên hàng nghìn mẫu người dùng ẩn danh (tính đến tháng 4 năm 2026)
- Hướng dẫn ngôn ngữ tự nhiên thông qua gpt-4o-mini-tts cho phép các nhà phát triển tùy chỉnh kiểu giọng nói mà không cần chuyên môn về SSML
- Khả năng chuyển đổi giọng nói thành giọng nói thông qua gpt-realtime mang lại thời gian hội thoại tự nhiên với độ trễ tối thiểu
- Hỗ trợ hơn 50 ngôn ngữ với 13 giọng nói tích hợp sẵn bao gồm alloy, echo, fable, onyx, nova và shimmer
- Hỗ trợ phát trực tuyến với mã hóa truyền tải khối cho phép phát lại ngay lập tức trước khi quá trình tạo hoàn tất

**Nhược điểm**:
- Công cụ giọng nói vẫn đang trong giai đoạn xem trước sau hơn một năm, với tính năng sao chép 15 giây không khả dụng đối với hầu hết các nhà phát triển
- Độ chính xác phát âm thấp hơn ở mức 77,30% so với 81,97% của ElevenLabs, với độ chính xác ngữ điệu là 45,83% so với 64,57%
- Giọng nói được tối ưu hóa cho tiếng Anh có thể ảnh hưởng đến chất lượng đối với các ứng dụng không phải tiếng Anh mặc dù hỗ trợ đa ngôn ngữ

**Giá cả**: TTS-1 có giá 15 đô la cho mỗi triệu ký tự. TTS-1-HD có giá 30 đô la cho mỗi triệu ký tự. gpt-4o-mini-tts sử dụng giá dựa trên token với mức 0,60 đô la cho mỗi triệu token đầu vào cộng với 12 đô la cho mỗi triệu token đầu ra âm thanh.


## 10. Cartesia Sonic

**Phù hợp cho**: Trí tuệ nhân tạo đàm thoại thời gian thực và trung tâm liên lạc yêu cầu độ trễ dưới 100ms để mang lại trải nghiệm sống động.

**Ưu điểm**:
- TTFB 40ms với Sonic Turbo, thời gian phản hồi byte đầu tiên nhanh nhất được công bố trong số các API TTS thương mại
- Kiến trúc Mô hình Không gian Trạng thái cho phép mở rộng tuyến tính so với chi phí biến đổi bậc hai
- Điều chỉnh cảm xúc và tốc độ với thẻ SSML để tinh chỉnh giọng nói
- Sao chép giọng nói tức thì từ 3 giây âm thanh so với yêu cầu 30 giây của ElevenLabs
- Sonic 3 được đánh giá 4.7 và được ưa chuộng hơn ElevenLabs Flash V2 với tỷ lệ 61.4% so với 38.6% trong các thử nghiệm nội bộ

**Nhược điểm**:
- Chỉ hỗ trợ 15 ngôn ngữ so với hơn 40 ngôn ngữ được quảng cáo, hạn chế hỗ trợ ứng dụng đa ngôn ngữ
- Giới hạn 500 ký tự mỗi yêu cầu với Sonic Turbo yêu cầu chia nhỏ nội dung dài hơn
- Chủ yếu là nhà cung cấp TTS và STT với Line để điều phối hội thoại, nhưng ít tích hợp hơn so với các giải pháp toàn diện

**Giá cả**: Gói Pro có giá 5 đô la mỗi tháng với 100.000 tín dụng. Gói Khởi nghiệp có giá 49 đô la mỗi tháng với 1,25 triệu tín dụng. Tính năng chuyển văn bản thành giọng nói (TTS) có giá 1 tín dụng cho mỗi ký tự.


## 14. Kokoro 82M

**Phù hợp cho**: Các nhóm có ngân sách hạn chế nhưng thoải mái với việc tự lưu trữ, muốn có chất lượng tốt với chi phí tối thiểu, hoặc các nhà phát triển cần toàn quyền kiểm soát mô hình để tinh chỉnh tùy chỉnh và triển khai tại biên.

**Ưu điểm**:
- Mã nguồn mở theo giấy phép Apache 2.0
- Khoảng 0,70 USD/1 triệu ký tự (chi phí tính toán tự lưu trữ), là lựa chọn rẻ nhất hiện nay
- 82 triệu tham số chạy trên CPU tầm trung mà không cần GPU
- Vượt trội hơn OpenAI TTS-1 HD về phân tích giọng nói nhân tạo mặc dù rẻ hơn hơn 100 lần

**Nhược điểm**:
- Chỉ hỗ trợ tự lưu trữ, không có API được quản lý hoặc hỗ trợ doanh nghiệp
- Hiện tại hỗ trợ 6 ngôn ngữ (tiếng Anh, tiếng Pháp, tiếng Hàn, tiếng Nhật, tiếng Quan thoại, tiếng Anh Anh)

- Chất lượng tổng thể thấp hơn so với các tùy chọn thương mại trong top 10

**Giá cả**:
Khoảng 0,70 USD/1 triệu ký tự dựa trên chi phí tính toán tự lưu trữ. Không có phí đăng ký hoặc phí API.


<!--more-->

{{< cards >}}
  {{< card link="kokoro" title="Kokoro 82M v1.0" icon="book-open" >}}
  {{< card link="miniconda" title="Miniconda" icon="book-open" >}}
{{< /cards >}}