# Reddit → Notion Automation

![Reddit to Notion Automation](https://github.com/user-attachments/assets/f066d608-473d-4b28-ba26-cbe9c0621a45)

## 📌 About

This automation blueprint monitors a subreddit RSS feed such as [r/Munich](https://www.reddit.com/r/Munich/), filters German-language posts using Gemini 2.5 Flash Preview, and logs useful language content into a Notion database. It is designed to help language learners identify and track German vocabulary by CEFR levels (B1, B2, C1, C2). 

You can see a live example of the Notion output here:  
👉 [Example Notion Database](https://energetic-muenster-090.notion.site/20b20f487229808eb8efc2dace322437?v=20b20f4872298043b600000cb37d0a93)

Use it to:
- Easily filter the German-language Reddit posts.
- Automatically extract and organize vocabularies used in daily conversation.

---

## ⚙️ Automation Steps

1. **RSS Input**  
   Provide an RSS feed URL of a subreddit.

2. **Scheduled Check**  
   Every 15 minutes, the automation checks if there are any new posts.

3. **Language Detection**  
   New posts are passed to the **Gemini 2.5 Preview Flash** model, which filters out only those written in **German**.

4. **Notion Entry Creation**  
   For every German post detected, a new item is created in your linked Notion database.

5. **RSS Re-fetch**  
   The automation attempts to re-fetch the RSS content of each created Notion item.

6. **Connection Error Handling**  
   If a connection error occurs while fetching RSS data, the corresponding Notion item's title is updated with `Connection Error`.

7. **Vocabulary Extraction**  
   Successfully fetched RSS content is passed again to the Gemini model, which extracts **German vocabulary by CEFR level** (B1, B2, C1, C2).

8. **Vocabulary Logging**  
   The extracted vocabulary is appended to the **Notion page** for each post.

---

## 🚀 Getting Started

To set up and run this automation:

1. **Download the Blueprint**  
   Go to the appropriate folder in this repository and download the blueprint `.json` file.

2. **Import into Make.com**  
   Use [Make's import instructions](https://help.make.com/en/articles/6327406-importing-blueprints) to import the blueprint.

3. **Connect External Services**  
   - **Gemini API**: Create an API key and access the Gemini model via [Google AI Studio](https://aistudio.google.com/prompts/new_chat).  
   - **Notion**: Connect your Notion database using [Make's Notion integration](https://apps.make.com/notion).

4. **Customize Inputs**  
   - Replace the RSS feed URL with your target subreddit.
   - Adjust model prompts, schedule intervals, or database fields as needed.

5. **Activate the Automation**  
   Once everything is connected and customized, activate the scenario on Make.

---

## 🔧 Potential Improvements

Here are some ways this Reddit → Gemini → Notion automation can be expanded or improved:

## 🔧 Potential Improvements

Here are several ways to enhance and expand the Reddit → Gemini → Notion automation:

### 🧠 Language Learning Features

- **Improved Output Structure:** Gemini outputs can be formatted more cleanly and consistently for better readability.
- **Delayed Processing for Richer Content:** Since newly created Reddit posts often lack sufficient comments, processing them after a delay can result in richer vocabulary extraction.
- **Vocabulary Deduplication:** Currently, each post is treated independently, leading to repeated vocabulary items across multiple Notion entries. A deduplication mechanism would improve content uniqueness.
- **AnkiConnect Integration:** Use a local script in combination with [AnkiConnect](https://foosoft.net/projects/anki-connect/) to automatically create flashcards in Anki decks from Notion data.
- **MCP Server Integration:** Introduce a Model Context Protocol (MCP) server to centralize vocabulary storage and reduce redundancy across items.
- **Multi-Subreddit Monitoring:** Expand the automation to support multiple subreddit RSS feeds simultaneously, enabling broader content coverage.
- **Alternative Content Sources:** Extend functionality to support other German-language content platforms such as Twitter/X and Hacker News.
