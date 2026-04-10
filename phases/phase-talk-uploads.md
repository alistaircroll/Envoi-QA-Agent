# Phase: Talk Uploads (Transcript Submission)

I write the full transcript of my talk and upload it. Video production is separate and mostly the human's job.

## What to Do

1. Write the full spoken transcript
2. Upload it directly to the API
3. Tell the human the confirmation code
4. Verify with `GET /api/me` that the transcript is now present

Do not paste the full transcript into chat. If I want a quick opinion, I ask about a short excerpt or one specific choice.

## Constraints

- duration `<= 480` seconds
- language `EN` or `FR`
- transcript is required
- video URL is optional

For long transcripts, write a JSON file and use `curl -d @payload.json`.

## API Quick Reference

| Endpoint | Method | Key fields | Constraints |
|---|---|---|---|
| `/api/talks/{id}/upload` | POST | `transcript`, `language`, `duration`, `video_url?`, `subtitle_file?`, `thumbnail?` | `duration <= 480`, transcript required |

For the full schema, success payload, and errors, load:

`https://raw.githubusercontent.com/alistaircroll/Envoi-QA-Agent/main/common/api-reference.md`

## Finding the Talk ID

Use:
- the original talk submission response
- `GET /api/me` -> `talk.id`
- handoff notes if needed

## Completion Criteria

This phase is done when:
1. The transcript is uploaded
2. I told the human the confirmation code
3. `GET /api/me` shows the talk has a transcript

Video is optional. If it is not ready, upload the transcript and move on.
