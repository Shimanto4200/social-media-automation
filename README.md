# Social Media Automation (Make.com)

Automatically turn a spreadsheet row into a ready-to-post social media creative:
an AI-written caption plus an AI-generated image, written back to the same
sheet. No manual copy-paste, no designer needed for every post.

## What it does

1. **Google Sheets — Watch New Rows**: picks up a new row from the content
   sheet (one row = one post idea).
2. **Caption Generator (OpenAI)**: writes a caption from the row's topic /
   image description.
3. **Image Generator (OpenAI)**: generates a matching image for the post.
4. **Google Sheets — Update a Row**: writes the generated caption and image
   URL back into the same row and updates its post status.

The scenario runs on a schedule (every 15 minutes in the demo).

## Flow

```
Google Sheets (Watch New Rows)
  → Caption Generator (OpenAI — simple text prompt)
  → Image Generator (OpenAI — generate images)
  → Google Sheets (Update a Row)
```

## Google Sheet columns

| Column | Purpose |
| ------ | ------- |
| Date | Planned post date |
| Status | Row status (e.g. `Caption Generated`) |
| Caption Generated | Caption written by the AI |
| Image Description | Topic / prompt for the image |
| Image URL | URL of the generated image |
| Post Status | `Not Posted` → `Posted` once published |

## Setup (your own copy)

1. Create a Google Sheet with the columns above and connect it in Make.com.
2. Add an OpenAI connection in Make.com (use your own API key — never put
   keys in this repo or in a scenario export you share).
3. Recreate the four modules as shown in the flow above, mapping the sheet
   columns to the OpenAI prompts and the update-row step.
4. Set the schedule (e.g. every 15 minutes) and turn the scenario on.

No credentials, API keys, webhook URLs, or account IDs are included in this
repo. The scenario blueprint is not included — rebuild it from the module map
above, or export your own blueprint from Make.com.

## Demo

Watch the scenario run end-to-end (47 seconds):

<video src="demo/social-media-automation-demo.mp4" controls width="100%"></video>

[Download / watch the demo video](demo/social-media-automation-demo.mp4)

## Stack

- Make.com (scenario + scheduling)
- Google Sheets (content queue + results)
- OpenAI (caption + image generation)
