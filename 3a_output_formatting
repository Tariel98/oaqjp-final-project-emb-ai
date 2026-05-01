import requests
import json

def emotion_detector(text_to_analyze):

    url = "https://sn-watson-emotion.labs.skills.network/v1/watson.runtime.nlp.v1/NlpService/EmotionPredict"


    headers =  {"grpc-metadata-mm-model-id": "emotion_aggregated-workflow_lang_en_stock"}
    input_json = { "raw_document": { "text": text_to_analyze } }

    response = requests.post(url, json=input_json, headers=headers)
    formated_output = json.loads(response.text)

    anger_score = formated_output["emotionPredictions"][0]["emotion"]["anger"]
    disgust_score = formated_output["emotionPredictions"][0]["emotion"]["disgust"]
    fear_score = formated_output["emotionPredictions"][0]["emotion"]["fear"]
    joy_score = formated_output["emotionPredictions"][0]["emotion"]["joy"]
    sadness_score = formated_output["emotionPredictions"][0]["emotion"]["sadness"]

    score_mapping = {
        anger_score : 'anger',
        disgust_score: 'digust',
        fear_score : 'fear',
        joy_score : 'joy',
        sadness_score: 'sadness'
    }

    dominant_emotion = score_mapping.get(max(list(score_mapping.keys())))

    result = {
    'anger': anger_score,
    'disgust': disgust_score,
    'fear': fear_score,
    'joy': joy_score,
    'sadness': sadness_score,
    'dominant_emotion': dominant_emotion
    }   

    return result

