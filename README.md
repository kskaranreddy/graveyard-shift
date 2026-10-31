# 🎃 Graveyard Shift

A Halloween-themed gamified productivity web app built for **Hack-to-Ween 2026** (AWS Student Builder Group, IIT Jodhpur).

Every unfinished task is a restless spirit. Summon it, aim a candle-lit Séance Timer at it, and banish it to the cemetery.

## Features
- **Haunted List:** tasks as spirits (Poltergeist, Zombie, Demon, Nightmare Boss) with realms, search and filters
- **Séance Focus Altar:** 5/15/25/45 minute timer with a melting animated candle and rune progress ring
- **Boss battles:** big tasks have HP; each completed séance deals damage
- **XP and ranks:** Novice Medium up to Grand Necromancer, plus a daily witching streak
- **Grimoire:** unlockable achievements
- **Cemetery Yard:** banished tasks become tombstones with epitaphs; resurrect or export as JSON
- **Curse of Silence:** fullscreen zen focus mode
- **Atmosphere:** 4 haunted themes, procedural Web Audio sound effects and ambient soundscapes (no audio files), fog particles, bats, spiderwebs
- **Persistence:** everything saves in the browser (localStorage)

## AWS integration (live)
The app syncs to a small serverless backend deployed with one CloudFormation template (`template.yaml`):
- **AWS Lambda** (Python 3.12, Function URL): `GET/PUT /state` and `POST /speak`
- **Amazon DynamoDB**: one item per user holding spirits, graves, XP and streak
- **Amazon Polly**: voices the banish incantation, returned as mp3 through Lambda
- **Amazon CloudWatch Logs**: structured event logs from the Lambda function
- **AWS CloudFormation**: infrastructure as code

The app is offline-first: without a backend URL it runs entirely in the browser using localStorage and browser speech.

### Deploy the backend
1. In the AWS Console choose the region your account allows (for example **ap-southeast-2, Sydney**), open **CloudFormation → Create stack → With new resources**.
2. Upload `template.yaml`, name the stack `graveyard-shift`, tick the IAM acknowledgement, and create it.
3. When the stack is `CREATE_COMPLETE`, open **Outputs** and copy `FunctionUrl`.
4. Open the app, go to the **AWS Cloud** tab, paste the URL, and click **Connect**.
5. Optional: put the URL in `window.GS_AWS_URL` near the top of `index.html` so every visitor is connected automatically.
6. Delete the stack after judging to avoid any charges.

## Tech
Plain HTML, CSS and JavaScript in one file. No build step, no dependencies.

## Run locally
Open `index.html` in a modern browser.

## Third-party resources
- Fonts via Google Fonts: Creepster, Pirata One, Plus Jakarta Sans, Special Elite (SIL Open Font License)
- Emoji: system emoji set
