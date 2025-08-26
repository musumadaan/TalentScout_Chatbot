# TalentScout_Chatbot

The TalentScout Hiring Assistant is an AI-powered recruitment chatbot designed to automate the initial candidate screening process for technology roles.
It uses Streamlit for the web interface, the OpenRouter API (openrouter/auto model) for natural language responses, and VADER Sentiment Analysis to detect the tone of the candidate’s answers.

## Capabilities:
1.) Greets the candidate and explains the process.

2.) Sequentially collects 7 key candidate details:

  2.1.) Full Name
  
  2.2.) Desired Position(s)
  
  2.3.) Email Address
  
  2.4.) Phone Number
  
  2.5.) Years of Experience
  
  2.6.) Current Location
  
  2.7.) Tech Stack
  
3.) Generates exactly 3 tailored technical questions based on the tech stack.

4.) Analyzes sentiment for each user message and adapts tone accordingly.

5.) Saves the conversation in anonymized format and provides a download option.

6.) Styled with a black & purple theme and branded with the TS logo (https://www.shutterstock.com/image-vector/gradient-3d-connected-alphabet-letter-ts-2491875927).

## Installations:
1.) Clone the repository.

2.) Create the virtual environment inside Talentscout_chatbot folder.

3.) Check the python interpreter and set it to 3.8.10.

4.) Install the dependencies by using pip install -r requirements.txt.

5.) Create .env file to add the api key, site_url, logo and model.

6.) Add the logo image in PNG inside the talentscout_chatbot folder.

7.) Run the application by using streamlit run app.py.

## Usage Guide:
1.) The assistant greets you and explains the process.

2.) The bot asks one field at a time. Some fields (e.g., email, phone) require valid formats.

3.) Once all 7 fields are filled, the bot generates 3 intermediate-level technical questions tailored to your stack.

4.) After each answer, a badge shows your sentiment (Positive/Neutral/Negative) and score.

5.) The bot thanks you and ends the session.

6.) Click Save Conversation (Simulated), then download candidate_data.txt (with anonymized details).

## Technical Details:
### Libraries Used:
1.) Python 3.8.10

2.) Streamlit - UI Framework

3.) dotenv - Environment Variable Management

4.) vaderSentiment - Sentiment Analysis. 

### Model Details:
1.) Provider: OpenRouter

2.) Model: openrouter/auto (auto-selects optimal model for each request)

### Architecture Details:
1.) Sequential field collection — Ensures all required candidate details are captured before moving to questions.

2.) Regex-based validation — For emails, phone numbers, and years of experience.

3.) Sentiment integration — VADER chosen for its simplicity, lightweight nature, and good performance on conversational text.

4.) Local file save + download — Avoids server persistence concerns; GDPR-friendly.

5.) Custom styling — Black background, white text, purple theme for buttons and accents, branded logo.

## Prompt Design:
### System Prompt:
1.) The assistant’s role (Hiring Assistant for TalentScout).

2.) Required steps: greeting, 7-field collection, technical question generation.

3.) Rules: exactly 3 intermediate technical questions, relevant to tech stack, concise answers, no off-topic conversation.

### User Prompt:
Code Snippet: When generating technical questions, the assistant is prompted.
Tech stack: {tech_stack}
Return EXACTLY {n} intermediate technical questions that assess practical skill.
Respond ONLY with a JSON array of strings.

Thus, it ensures no extra text or numbering with relevant questions which are technically diverse and of appropriate difficulty.

## Challenges & Solutions:
1.) Premature Ending:

Issue: The bot sometimes ended the interview after the first answer if multiple fields were inferred too early.

Solution: Enforced strict sequential field-by-field flow. Even if multiple fields are extracted, the bot still prompts for each in order.

2.) Sentiment Accuracy:

Issue: Sarcasm and neutral wording could skew sentiment classification.

Solution: Tuned thresholds in VADER (compound >= 0.30 for Positive, <= -0.30 for Negative) and used sentiment only for tone, not decision-making.

### Detailed Project Description:
(With the DEMO Video and Deployed Link):
https://docs.google.com/document/d/139pSGvtqXPtYYNHCPwWavt4Xodjo6w3s1MYgRFuoKQw/edit?usp=sharing









