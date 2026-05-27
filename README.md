# AnswerMark

A full-featured cross-platform social platform built with Flutter and Firebase. 
AnswerMark enables community interaction through posts, comments, private messaging, 
and social connections — with real-time updates, transparent content ranking, 
and a fully moderated environment.

## Features

- **Secure Authentication** — Email/password login with email verification, 
  password reset, and account suspension enforcement
- **Post Feed** — Real-time feed with anonymous posting, sponsored content, 
  and like/dislike reactions
- **Fair Comment Ranking** — Deterministic score-based ranking with guaranteed 
  24-hour visibility for new comments and permanent visibility for top-10 scoring comments
- **Nested Comments** — Threaded replies with upvote/downvote voting
- **Private Messaging** — Friend-only messaging with real-time delivery and read receipts
- **Friends System** — Send, accept, and decline friend requests; block users
- **Notifications** — Real-time notifications for comments, messages, 
  friend requests, and admin actions
- **Admin Dashboard** — User management, content moderation, sponsored post 
  control, and tamper-evident audit logging
- **User Profiles** — Editable display name, bio, and profile picture
- **User Search** — Real-time prefix-based user discovery

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | Flutter (Dart) |
| Authentication | Firebase Auth |
| Database | Cloud Firestore |
| Storage | Firebase Storage |
| State Management | Provider |
| Navigation | go_router |

## Getting Started

### Prerequisites
- Flutter SDK 3.x
- A Firebase project with Auth and Firestore enabled

### Setup

1. **Clone the repository**
```bash
   git clone https://github.com/yourusername/answermark.git
   cd answermark
```

2. **Install dependencies**
```bash
   flutter pub get
```

3. **Connect to Firebase**
```bash
   dart pub global activate flutterfire_cli
   flutterfire configure
```

4. **Deploy Firestore security rules**
```bash
   firebase deploy --only firestore:rules
```

5. **Run the app**
```bash
   flutter run
```

### Making yourself an admin
After registering, go to Firebase Console → Firestore → users → your document 
and set `isAdmin: true`.

## Firestore Collections

| Collection | Description |
|-----------|-------------|
| `users` | User profiles, friend lists, block lists |
| `posts` | Feed posts with reactions and comment counts |
| `comments` | Flat comments with parent references for nesting |
| `conversations` | Message thread metadata |
| `conversations/{id}/messages` | Individual messages |
| `friendRequests` | Pending and resolved friend requests |
| `notifications` | Per-user notification documents |
| `adminLogs` | Immutable admin action audit trail |

## Security

Access control is enforced at the database layer through Firestore security rules, 
independent of application code. Key rules include:
- All reads require authentication
- Posts and comments can only be edited or deleted by their author or an admin
- Messages are only accessible to conversation participants
- Admin logs are read/write restricted to admin users only

## Future Work

- End-to-end encrypted messaging
- Push notifications via Firebase Cloud Messaging
- User-facing content reporting interface
- Collaborative filtering recommendations
- Moderator role with limited admin privileges
- Migration to PostgreSQL for production scaling

## License

MIT
