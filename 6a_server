"""
Server module for Emotion Detection web application.

This module uses Flask to deploy a web interface that allows users to input
text and receive emotion analysis results using the Watson NLP API.

Routes:
- "/" : Renders the main HTML page.
- "/emotionDetector" : Processes user input and returns emotion analysis.
"""


from flask import Flask, render_template, request
from EmotionDetection.emotion_detection import emotion_detector

app = Flask("Emotion Detector")

@app.route("/emotionDetector")
def emotion_analyzer():
    """
    Handle GET request for emotion analysis.

    Retrieves input text from the request, sends it to the emotion_detector
    function, and returns a formatted string containing emotion scores and
    the dominant emotion.

    Returns:
        str: Formatted response with emotion scores and dominant emotion.
    """    
    text_to_analyze = request.args.get("textToAnalyze")

    response = emotion_detector(text_to_analyze)

    anger = response["anger"]
    disgust = response["disgust"]
    fear = response["fear"]
    joy = response["joy"]
    sadness = response["sadness"]
    dominant_emotion = response["dominant_emotion"]

    return (
        "For the given statement, the system response is "
        f"'anger': {anger}, "
        f"'disgust': {disgust}, "
        f"'fear': {fear}, "
        f"'joy': {joy} and "
        f"'sadness': {sadness}. "
        f"The dominant emotion is {dominant_emotion}."
    )


@app.route("/")
def render_index_page():
    """
    Render the main web interface.

    Returns:
        str: Rendered HTML page (index.html).
    """
    return render_template("index.html")


if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)