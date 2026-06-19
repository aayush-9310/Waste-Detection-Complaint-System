# Waste Detection & Complaint System

A full-stack web application that uses machine learning to classify waste from images and educate users about sustainable disposal practices.

## Overview

Waste management is an essential aspect of environmental responsibility, influencing ecosystems, resource use, and public health. This project brings machine learning into everyday decisions about waste disposal and reuse.

Users can either upload an image from their device and manually enter the location, or capture a photo directly using the device camera with location automatically captured through the browser. A pretrained deep learning model analyzes the image to predict its waste category and assign a severity level — **LOW** or **HIGH**.

- **LOW severity** → the app displays disposal tips and DIY reuse suggestions for individual action.
- **HIGH severity** → the user is directed to the Complaints Module to report the waste at a specific location.

User can also track all his/her complaints progress.

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React, TypeScript |
| Backend | Node.js, Express, MongoDB |
| ML Service | Python, Flask, MobileNetV2 |

## Dataset

The dataset used to train the waste classification model was collected from **Roboflow**, an open-source computer vision dataset platform.

- **Source**: Roboflow Universe
- **Categories**: paper, plastic, metal, glass, organic, trash, battery, shoes, wood (9 classes)
- **Format**: Labeled image dataset, preprocessed and resized for MobileNetV2 input
- **Usage**: Used to train and validate the MobileNetV2-based classification model for waste category and severity prediction

## Workflow

1. User uploads a waste image from their device (with manual location entry) or captures a photo using the device camera (with location auto-captured via browser geolocation)
2. Image is sent to the Flask ML service for inference
3. MobileNetV2 model predicts the waste category and assigns a severity level (LOW or HIGH)
4. Result is returned to the frontend and displayed to the user
5. If severity is **LOW** → disposal tips and DIY reuse suggestions are shown
6. If severity is **HIGH** → user is redirected to the Complaints Module
7. Complaint (with image and location) is submitted and stored in MongoDB via the backend API
8. Stored complaint data becomes available for review, enabling community-level and data-driven waste management action

## Architecture

The system follows a modular three-tier architecture:

1. **Frontend (React + TypeScript)** — handles image upload/capture, geolocation, and the user interface.
2. **Backend (Node.js + Express + MongoDB)** — handles authentication, complaint storage, and notifications.
3. **ML Service (Python + Flask)** — runs a MobileNetV2-based model that classifies waste into nine categories and predicts severity.


## Outcomes

- Achieved ~93% classification accuracy across nine waste categories (paper, plastic, metal, glass, organic, trash, battery, shoes, wood), with real-time prediction
- Severity-based guidance directs users to DIY disposal tips (LOW severity) or complaint submission (HIGH severity)
- Complaints Module enables community-level reporting, with location data stored in MongoDB for potential use in waste management decisions
- Demo Mode and Live Mode (with automatic geolocation) make the app accessible for both testing and real-world use
- Modular three-tier architecture provides a scalable foundation for future enhancements like mobile support and expanded waste categories

## Limitations & Future Work

The model has certain limitations in generalizing across diverse real-world images. Future improvements could include expanding the training dataset, adding mobile app support, and integrating location-based disposal guidance.
