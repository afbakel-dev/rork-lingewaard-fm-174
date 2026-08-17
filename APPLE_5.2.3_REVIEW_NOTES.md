# Apple Guideline 5.2.3 — how to get Lingewaard FM approved

Apple rejected under **5.2.3 Legal: Intellectual Property — Audio/Video Downloading**.

This is NOT a code bug. The app contains no download, record, save or export function —
it only plays a live HTTP stream. Apple flags this guideline when the reviewer cannot
verify that the developer account is authorised to broadcast the audio it streams.

The account is `bibabroadcast` (Biba Broadcast) while the app is named "Lingewaard FM".
That mismatch is almost certainly what triggered it. It is resolved with paperwork in the
App Review notes, plus a reply to the Resolution Center.

---

## Step 1 — Paste this into App Review Information → Notes

> Lingewaard FM is a licensed Dutch local radio station (www.lingewaardfm.nl).
> This app is the station's own official app, published by Biba Broadcast, which
> operates the station.
>
> The app does NOT download, record, cache, export or share any audio. It only plays
> the station's own live broadcast stream over HTTP:
> https://totaal-streaming.de/listen/lingewaardfm_nl/radio.mp3
>
> There is no download button, no offline playback, no file storage and no
> third-party media in the app. Audio is played only while the user is listening
> live, exactly as with an FM receiver.
>
> All music broadcast by Lingewaard FM is licensed through the Dutch collecting
> societies Buma/Stemra and Sena. A written authorisation confirming that Biba
> Broadcast owns and operates Lingewaard FM and holds the rights to distribute
> the stream is attached / available on request.
>
> No login is required to test the app. Press the play button on the main screen
> to start the live stream.

## Step 2 — Attach the authorisation

Use `APPLE_5.2.3_AUTHORISATION_LETTER.md` — fill in your details, print, sign, scan to PDF.
Attach it in the Resolution Center reply (Apple accepts attachments there).

If you also hold the Buma/Stemra and/or Sena licence certificates for Lingewaard FM,
attach those PDFs too. That is the single strongest piece of evidence for 5.2.3.

## Step 3 — Reply in the Resolution Center

Reply in the same thread as the rejection (do not just resubmit silently), with the
letter attached and the Step 1 text repeated. Then submit the new build.

---

## Code changes made in this commit (supporting evidence)

1. Added a visible rights notice on the player screen:
   "Officiële app van Lingewaard FM. Uitzending onder licentie van Buma/Stemra en Sena.
    Alleen live luisteren — opnemen of downloaden is niet mogelijk."
   This tells the reviewer directly, inside the app, that the stream is licensed and
   that no downloading is possible.

2. Fixed the "now playing" metadata endpoint — it was pointing at the .mp3 stream URL
   instead of the AzuraCast JSON API, so track titles never loaded:
   old: https://totaal-streaming.de/listen/lingewaardfm_nl/radio.mp3
   new: https://totaal-streaming.de/api/nowplaying/lingewaardfm_nl

## Also check in App Store Connect

- App name / subtitle must not contain any other station's or brand's name.
- Screenshots must show only Lingewaard FM branding.
- The "Copyright" field should read: Lingewaard FM / Biba Broadcast.
- Support URL and Privacy Policy URL must both point at lingewaardfm.nl and must load.
