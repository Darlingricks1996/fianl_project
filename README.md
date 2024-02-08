import os
import subprocess

def clone_repository(repository_url):
os.makedirs("project_directory", exist_ok=True)
os.chdir("project_directory")
subprocess.check_call(["git", "clone", repository_url])

clone_repository("https://github.com/ibm-developer-skills-network/oaqjp-final-project-emb-ai.git")

def analyze_emotions(text):
natural_language_understanding = NaturalLanguageUnderstandingV1(
version='2024-02-07',
username='darlingricks',
password='School@123')

response = natural_language_understanding.analyze(
text=text,
features=Features(emotion=EmotionOptions())).get_result()

return response['emotion']['document']['emotion']

feedback_text = "This product is amazing!"
emotions = analyze_emotions(feedback_text)
print(emotions)

def format_output(emotions):
formatted_output = ""
for emotion, score in emotions.items():
formatted_output += f"{emotion.capitalize()}: {score}\n"
return formatted_output

formatted_output = format_output(emotions)
print(formatted_output)

import unittest

class EmotionDetectionTests(unittest.TestCase):
def test_analyze_emotions(self):
feedback_text = "This product is amazing!"
emotions = analyze_emotions(feedback_text)
self.assertEqual(emotions['joy'], 0.9)

def test_format_output(self):
emotions = {'joy': 0.9, 'sadness': 0.1}
formatted_output = format_output(emotions)
self.assertIn("Joy: 0.9", formatted_output)
self.assertIn("Sadness: 0.1", formatted_output)

if __name__ == '__main__':
unittest.main()
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/analyze', methods=['POST'])
def analyze():
feedback_text = request.json['text']
emotions = analyze_emotions(feedback_text)
formatted_output = format_output(emotions)
return jsonify({'result': formatted_output})

if __name__ == '__main__':
app.run()
def analyze_emotions(text):
try:
# Your existing code here
except Exception as e:
print(f"An error occurred: {e}")
return {}

@app.route('/analyze', methods=['POST'])
def analyze():
try:
feedback_text = request.json['text']
emotions = analyze_emotions(feedback_text)
formatted_output = format_output(emotions)
return jsonify({'result': formatted_output})
except Exception as e:
return jsonify({'error': str(e)})

pip install flake8
flake8 your_code.py


