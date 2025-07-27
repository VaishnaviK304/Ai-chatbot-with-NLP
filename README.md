# Ai-chatbot-with-NLP
# 📦 Install required libraries
!pip install textblob -q
!python -m textblob.download_corpora

# 📚 Import libraries
from textblob import TextBlob
import random
from IPython.display import display, Markdown

# 🎭 Define emotion-based responses
emotions = {
    "positive": {
        "quotes": [
            "🌟 'Keep your face always toward the sunshine—and shadows will fall behind you.' – Walt Whitman",
            "🎶 Here's a happy tune: 'Happy' by Pharrell Williams",
            "😄 You radiate joy! The world needs more of that."
        ]
    },
    "negative": {
        "quotes": [
            "🌧️ 'Even the darkest night will end and the sun will rise.' – Victor Hugo",
            "🎧 Mood match: 'Fix You' by Coldplay",
            "💙 You’re not alone. I’m here to listen."
        ]
    },
    "neutral": {
        "quotes": [
            "🍃 'Life is a balance of holding on and letting go.' – Rumi",
            "🎼 Try: 'Weightless' by Marconi Union",
            "🤔 It's okay to just exist. Let's reflect together."
        ]
    }
}

# 🧠 Define the main chatbot logic
def emotion_mirror_bot():
    display(Markdown("**🪞 Welcome to the Emotion Mirror Bot**"))
    display(Markdown("Tell me how you’re feeling. Type `stop` to end the session."))

    while True:
        user_input = input("You: ")
        
        if user_input.lower() in ["stop", "exit", "bye"]:
            display(Markdown("🪞 *Reflection complete.* Take care of your heart. ❤️"))
            break

        # Analyze sentiment
        blob = TextBlob(user_input)
        polarity = blob.sentiment.polarity

        # Determine emotion category
        if polarity > 0.2:
            mood = "positive"
        elif polarity < -0.2:
            mood = "negative"
        else:
            mood = "neutral"

        # Choose a random mood-matching response
        response = random.choice(emotions[mood]["quotes"])
        display(Markdown(f"**🪞 Emotion Mirror:** I sense you are feeling *{mood}*."))
        display(Markdown(f"**💡 Reflection:** {response}"))

# 🚀 Run the chatbot
emotion_mirror_bot()
