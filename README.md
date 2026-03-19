# Wild Nieuw-West — A Murder Mystery Party Game

A companion app for hosting real-life Cluedo-style murder mystery parties. Players select characters with secret roles (Murderer, Detective, Innocent), receive room-based social tasks every 20 minutes, and report murders during "lights out" rounds.

## Setup

### 1. Create Google Sheet

1. Go to [Google Sheets](https://sheets.google.com) and create a new spreadsheet
2. Name it "Wild Nieuw-West Games"
3. Copy the Sheet ID from the URL: `https://docs.google.com/spreadsheets/d/SHEET_ID_HERE/edit`

### 2. Deploy Backend (Google Apps Script)

1. Go to [Google Apps Script](https://script.google.com) and create a new project
2. Copy the contents of `wild-nieuw-west-backend.gs` into the editor
3. Replace `YOUR_GOOGLE_SHEET_ID_HERE` with your Sheet ID
4. Click **Deploy > New Deployment**
5. Select **Web app** as the type
6. Set "Execute as" to **Me**
7. Set "Who has access" to **Anyone**
8. Click **Deploy** and copy the Web App URL

### 3. Configure Frontend

1. Open `index.html`
2. Find `const API_URL = 'YOUR_APPS_SCRIPT_URL_HERE';`
3. Replace with your deployed Apps Script URL

### 4. Deploy to GitHub Pages

```bash
cd wild-nieuw-west
git init
git add index.html README.md wild-nieuw-west-backend.gs
git commit -m "Initial commit"
gh repo create wild-nieuw-west --public --source=. --push
```

Then enable GitHub Pages in repo Settings > Pages > Source: main branch.

Live at: `https://YOUR_USERNAME.github.io/wild-nieuw-west/`

## How to Play

1. **Host** opens the app and taps "Host a Party"
2. **Host** enters their name, picks a character, and shares the game code or QR
3. **Guests** join with the code and pick available characters
4. **Host** starts the party when everyone has joined
5. Everyone sees their **secret role** and first **room task**
6. Every 20 minutes, a new task sends players to different rooms
7. During **"Lights Out"** rounds, murderers tap victims on the shoulder
8. Murdered players tap "I Have Been Murdered!" on their phone
9. **Discuss and vote** to arrest suspects
10. **Murderers win** at 6 kills; **Innocents win** by arresting all murderers

## Roles

- **Murderer** (2): Secretly eliminate guests. Need 6 kills to win.
- **Detective** (2): Interrogate suspects. 2 interrogation chances.
- **Innocent** (12): Survive and help catch the murderers.

## Characters

Characters are pre-defined in the backend and can be easily customized by editing the `CHARACTERS` array in `wild-nieuw-west-backend.gs`.

## Rooms

Balcony, Living Room, Kitchen, Hall, Big Bathroom, Laundry Room, Gustavo's Bedroom, Jakob's Bedroom.

## Tech Stack

- **Frontend**: Single HTML file (HTML + CSS + JS)
- **Backend**: Google Apps Script
- **Database**: Google Sheets
- **Hosting**: GitHub Pages
- **Style**: Art Nouveau Noir
