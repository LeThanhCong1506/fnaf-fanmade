# 🍕 Pizzarella: The Last Shift

> **"Không chỉ là sinh tồn. Đó là một cuộc đi săn sự thật."**

**Pizzarella: The Last Shift** là một tựa game kinh dị sinh tồn góc nhìn thứ nhất (FPS Horror) được phát triển bằng Unity. Khác với lối chơi thụ động truyền thống (ngồi một chỗ check camera), game buộc người chơi phải di chuyển, giải đố và khám phá bí ẩn cốt truyện thông qua cơ chế **Environmental Storytelling**.

---

## 📖 Giới thiệu (Overview)

Bạn vào vai nhân viên bảo vệ đêm mới tại nhà hàng **Pizzarella**. Bề ngoài, nhiệm vụ của bạn rất đơn giản: Nghe điện thoại chỉ dẫn của quản lý, tiết kiệm điện và sống sót đến 6 giờ sáng.

Tuy nhiên, những cuộn băng (Tapes) bị bỏ lại bởi người bảo vệ cũ tên John sẽ hé lộ một sự thật kinh hoàng. Lũ Animatronic không bị lỗi, chúng đang săn mồi. Và nhiệm vụ của bạn sẽ thay đổi từ **"Sống sót"** sang **"Thiêu rụi tất cả"**.

---

## ✨ Tính năng nổi bật (Key Features)

* **🕵️ Scavenger Hunt Gameplay:** Hệ thống nhiệm vụ theo chuỗi (Chain Reaction). Manh mối từ cuộn băng A sẽ dẫn đến vị trí cuộn băng B, ép người chơi rời khỏi vùng an toàn.
* **🧠 Deceptive UI (Giao diện đánh lừa):** Hệ thống UI được lập trình để "nói dối" người chơi. Nhiệm vụ hiển thị là "Survive until 6 AM", nhưng thực chất game ngầm theo dõi số lượng vật phẩm thu thập để kích hoạt *Secret Ending*.
* **📞 Interactive Tutorial:** Hệ thống hướng dẫn thông minh. NPC (Phone Guy) sẽ dừng hội thoại và chờ đợi cho đến khi người chơi thực hiện đúng thao tác (Mở Camera, Đóng cửa) mới nói tiếp.
* **🤖 Smart AI:** Kẻ địch (Animatronics) sử dụng **NavMesh** để tìm đường và có cơ chế "Giờ thức dậy" (Revival Hour) riêng biệt cho từng màn chơi, tăng dần độ khó.
* **🎙️ AI Voice Acting:** Lồng tiếng nhân vật được tạo bởi công nghệ **ElevenLabs v3**, mang lại trải nghiệm âm thanh sống động và ám ảnh.

---

## 🛠️ Kiến trúc Kỹ thuật (Technical Architecture)

Dự án áp dụng các Design Pattern và kỹ thuật tối ưu trong Unity:

### 1. Data-Driven Design (ScriptableObjects)

Thay vì Hardcode dữ liệu vào script, toàn bộ dữ liệu game được quản lý bằng **ScriptableObjects**:

* `TapeItemSO`: Lưu trữ dữ liệu từng cuộn băng (Audio, Subtitle, ID).
* `LevelDataSO`: Cấu hình độ khó cho từng đêm (Giờ Enemy thức dậy, số lượng băng cần tìm).
* `ItemDataSO`: Dữ liệu vật phẩm Inventory.

### 2. Observer Pattern (Event System)

Sử dụng C# Actions để xử lý sự kiện, giảm sự phụ thuộc (Decoupling) và tối ưu hiệu năng (tránh dùng `Update` liên tục):

* Khi nhặt đồ -> `InventoryManager` bắn sự kiện `OnInventoryChanged`.
* UI (`MissionUI`) lắng nghe và tự cập nhật trạng thái nhiệm vụ.

### 3. Singleton Pattern

Sử dụng cho các lớp quản lý cốt lõi để đảm bảo truy cập toàn cục dễ dàng:

* `GameManager`
* `InventoryManager`
* `UIManager`

---

## 🎮 Điều khiển (Controls)

| Phím | Hành động |
| --- | --- |
| **W, A, S, D** | Di chuyển |
| **Chuột** | Xoay Camera |
| **E / Chuột Trái** | Tương tác (Mở cửa, Nhặt đồ) |
| **Chuột Phải** | Bật/Tắt Đèn pin |
| **I / Tab** | Mở túi đồ (Inventory) |
| **Esc** | Tạm dừng (Pause) |

---

## 📂 Cấu trúc thư mục (Project Structure)

```
Assets/
├── Scripts/
│   ├── Core/           # Chứa các Manager, Interface, Data (ScriptableObjects)
│   ├── GameLogic/      # Logic Gameplay (Player, Enemy, Interactions)
│   ├── UI/             # Logic hiển thị (Screens, Popups, Widgets)
│   └── Editor/         # Các công cụ hỗ trợ Editor
├── Resources/
│   └── Data/           # Nơi chứa các file ScriptableObject (Levels, Tapes...)
└── ...

```

---

## 🚀 Hướng phát triển (Roadmap)

* [x] Hoàn thiện Core Gameplay (Inventory, AI cơ bản, Tape System).
* [x] Tích hợp Deceptive UI và Secret Ending.
* [ ] **Multiplayer Mode (Tương lai):** Phát triển chế độ **Asymmetric PvP (1vs4)** sử dụng **Photon PUN 2**. Một người chơi điều khiển Animatronic săn đuổi 4 người chơi khác.
* [ ] Cải thiện AI: Thêm hành vi phối hợp nhóm (Flanking) cho Enemy.

---

## 👨‍💻 Tác giả (Credits)

* **Developer:** Lê Thành Công

---

*Cảm ơn bạn đã quan tâm đến dự án! Nếu thấy thú vị, hãy để lại một ⭐️ nhé!*
