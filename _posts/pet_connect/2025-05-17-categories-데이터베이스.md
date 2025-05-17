---
title: "데이터베이스를 어떤 방식으로 만들어야 할까?"
excerpt: "데이터베이스.."

categories:
  - pet_connect
tags:
  - [tag1, tag2]

permalink: /pet_connect/데이터베이스 1

toc: true
toc_sticky: true

date: 2025-05-17
last_modified_at: 2025-05-17
---

# 필요한 엔티티 목록 (1차 정리)

| 엔티티 | 설명 |
| --- | --- |
| **User** | 보호자 계정 정보 |
| **Pet** | 반려동물 정보 |
| **Match** | 교배 매칭 신청 및 상태 |
| **ChatRoom** | 채팅방 정보 |
| **ChatMessage** | 채팅 메시지 기록 |
| **Post** | 커뮤니티 게시글 |
| **Comment** | 커뮤니티 댓글 |
| **Report** | 신고 정보 |
| **Notification** | 실시간 알림 |
| **Location** | 위치 정보 (사용자/동물 기준) |
| **Admin** | 관리자 계정 (선택적) |
| Black List Token | 블랙리스트 토큰 |

---

# 📦 각 엔티티에 포함될 주요 속성 예시

### 1. `User`

- id (PK)
- username
- password
- email
- nickname
- phone
- profile_image_url
- is_admin (boolean)
- created_at / updated_at

### 2. `Pet`

- id (PK)
- owner_id (FK → User)
- name
- species (e.g., dog, cat)
- breed
- gender
- birth_date
- is_neutered
- personality (text)
- photo_url
- location_id (FK → Location)
- created_at / updated_at

### 3. `Match`

- id (PK)
- pet_id (FK → Pet)
- target_pet_id (FK → Pet)
- status (대기/수락/거절/완료 등)
- created_at / updated_at

### 4. `ChatRoom`

- id (PK)
- match_id (FK → Match)
- created_at

### 5. `ChatMessage`

- id (PK)
- chatroom_id (FK → ChatRoom)
- sender_id (FK → User)
- message
- sent_at

### 6. `Post`

- id (PK)
- author_id (FK → User)
- title
- content
- category (잡담/질문/정보 등)
- created_at / updated_at

### 7. `Comment`

- id (PK)
- post_id (FK → Post)
- author_id (FK → User)
- content
- created_at / updated_at

### 8. `Report`

- id (PK)
- reporter_id (FK → User)
- target_type (user/post/comment/chat)
- target_id
- reason
- status (처리중/처리완료)
- created_at

### 9. `Notification`

- id (PK)
- user_id (FK → User)
- type (매칭요청, 메시지도착 등)
- content
- is_read (boolean)
- created_at

### 10. `Location`

- id (PK)
- latitude
- longitude
- city
- district

작성중..