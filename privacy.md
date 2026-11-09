---
title: VAANI Privacy Policy
---

[हिन्दी में पढ़ें](privacy-hi)

# VAANI Privacy Policy

*Version 1.02, November 2026. Applies to the Android app VAANI (वाणी), "Pro Recorder & Editor".*

**In short: VAANI does not collect, send or sell any information about you. Your recordings stay on your phone.**

## What the app does with your data

- **Recordings, imported files and texts.** Your recordings, the files you import, their edits and the texts made from them
  (speech to text) are stored on your phone only, in the app's own folder (Android/data/ssc.vaani.recorder). That folder is
  removed when you uninstall the app. VAANI has no account, no cloud and no server of its own. Nothing is uploaded. VAANI does
  not encrypt these files itself; the phone's own lock and storage encryption protect them.
- **Microphone.** The microphone is used only while you record. Recording keeps running with the screen off through a
  notification that you can see; it stops when you press Stop.
- **AI features** (noise cancelling, Studio voice, Studio Max, speech to text) run **on your phone**. Your audio
  is not sent anywhere to be processed.
- **Internet.** The only use of the internet is to download an AI model when you ask for one (for example speech to text). The
  files come from GitHub or Hugging Face. Those sites can see that your phone downloaded a file (as any website can see a visit,
  for example your IP address). VAANI sends no recording, no text and no identifier with the request.
- **VAANI Pro (Google Play).** In the Play Store version, the purchase of VAANI Pro is made and handled by Google Play. VAANI only
  asks Google Play whether this account has bought Pro; it never sees your card, bank or UPI details. Google's own privacy policy
  applies to the purchase. To keep Pro from being faked, the app keeps the Pro status on your phone sealed with a key of the phone's
  own Android Keystore and checks that it is the app that was published; none of this leaves the phone.
- **Notification access ("Do not disturb")** is used only if you switch on *Mute calls while recording*; it lets the app silence
  incoming call sounds during a recording. VAANI does not read your notifications, calls or messages.
- **No ads, no analytics, no tracking, no advertising ID.**
- **Crash report.** If the app closes by itself, the error text is saved in a small file on your phone. It is shown to you
  the next time the app opens, with a Copy button. It leaves the phone only if you copy it and send it yourself.
- **Settings** (theme, language, formats, and whether Pro was bought or the free trial was started) are kept on your phone.

## Sharing and saving outside the app

VAANI shares nothing by itself. When you press *Share* or *Export*, the file goes to the app you choose, and that app's own
policy applies from there. When you use *Save to Music/Recordings*, the file is copied to your phone's shared Music folder, where
other apps that you have allowed to read audio files can see it. Delete such copies yourself when you no longer want them.

## Recording other people

In many countries and places you need the consent of the people you record, and some uses of a recording (publishing it, using it
against someone) can break privacy or other laws even if the recording itself was allowed. You are responsible for recording and
using voices lawfully, and for telling people when the law or good manners ask you to. Do not use VAANI to record people
secretly, to make a person's voice say what they did not say, or to harm anyone.

## Children

VAANI is not directed at children and collects no personal information from anybody.

## Your control

Delete a recording in the app, or delete the app: its private files go with it. Files you saved or exported to your own
folders stay until you delete them. Because VAANI keeps no data about you on any server, there is nothing for us to access, correct
or delete on your behalf; everything is in your hands on your phone.

## Changes and contact

If this policy changes, the new text will be in this file and in the app's next update (Settings > About > Privacy policy).
Contact: open an issue at https://github.com/sandeepsp121/vaani-public/issues, or write to the email address given on VAANI's page in Google Play.

This policy is written to match the app's real behaviour (see `NOTICE.md` for the third-party parts it uses, and the permissions
in `app/src/main/AndroidManifest.xml`). Because the app does not process personal data on any server, it is meant to agree with
India's Digital Personal Data Protection Act, 2023, and with the privacy rules of Google Play.
