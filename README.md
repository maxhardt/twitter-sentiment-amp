# Twitter Sentiment Analysis with Cloudera Machine Learning (CML)

Automated deployment with [Cloudera AMP](https://docs.cloudera.com/machine-learning/cloud/applied-ml-prototypes/topics/ml-amp-project-spec.html) and project specification defined in [./.project-metadata.yaml](./.project-metadata.yaml):

```yml
name: Twitter sentiment analysis
short_summary: Deployment of pre-trained model for sentiment analysis of Tweets.
description: Deployment of pre-trained model for sentiment analysis of Tweets.
author: Cloudera Inc.
date: '2023-01-17'
specification_version: "0.1"
prototype_version: "1.0"

runtimes:
  - editor: JupyterLab
    kernel: Python 3.9
    edition: Standard

tasks:

  - type: create_model
    short_summary: model create step
    name: Twitter sentiment analysis model
    entity_label: twitter-sentiment
    default_resources:
      cpu: 2
      memory: 8

  - type: build_model
    short_summary: model build step
    entity_label: twitter-sentiment
    examples:
      - request:
          created_at: "2023-01-11T15:05:45.000Z"
          id: "1613190434120949761"
          text: "I love hackathons!"
        response: 
          created_at: "2023-01-11T15:05:45.000Z"
          id: "1613190434120949761"
          text: "I love hackathons!"
          negative: 0.0042450143955647945
          neutral: 0.011172760277986526
          positive: 0.984582245349884
          label: "positive"
    target_file_path: inference.py
    target_function_name: predict
    kernel: python3

  - type: deploy_model
    short_summary: model deployment step
    entity_label: twitter-sentiment
