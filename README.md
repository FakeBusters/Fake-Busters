# Fake-Busters
Final project for a Bachelor's degree in Software Engineering at Shenkar
FakeBusters is a comprehensive system designed to automate the detection of sock-puppet accounts on social networks. Sock-puppet accounts are multiple user accounts operated by the same individual or group to spread misinformation and orchestrate influence campaigns. The FakeBusters system integrates advanced content and network analysis techniques to provide a scalable, accurate approach to identifying these malicious accounts.

## Table of Contents
- [Introduction](#introduction)
- [Features](#features)
- [Architecture](#architecture)
- [Installation](#installation)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)

## Introduction

Sock-puppets are a significant threat to the integrity of online discourse, and traditional detection methods are labor-intensive and lack scalability. FakeBusters addresses this challenge by leveraging a novel system built upon an enhanced Latent Personal Analysis (LPA) algorithm and advanced network analysis techniques. The system provides analysts with tools to detect sock-puppets effectively by analyzing both the content and the network structure of user profiles on social media.

## Features

- **Content Analysis**: Uses the Latent Personal Analysis (LPA) algorithm to assign unique content signatures to users and measure the similarity between them, identifying potential sock-puppetry.
- **Network Analysis**: Constructs and analyzes social network graphs to detect patterns and connections indicative of coordinated sock-puppet behavior.
- **Scalability**: Optimized for large-scale data processing, enabling efficient analysis of vast social media datasets.
- **User-Friendly Interface**: Provides a web-based interface for easy data input, analysis, and result visualization.
- **Integration with AWS**: Utilizes AWS S3, Lambda, and EC2 services for scalable and reliable processing.

## Architecture

The architecture of FakeBusters is designed to handle large-scale data processing and provide accurate analysis results efficiently. The system is composed of several key components:

- **Client**: Built using React.js, the client application communicates with the backend servers through a REST API, providing an intuitive interface for users to interact with the system.
- **Backend Services**: 
  - **LPA Service**: A Node.js server handles the LPA algorithm processing. The heavy computations are offloaded to an AWS EC2 instance to ensure performance and reliability.
  - **Network Analysis Service**: A Flask server running Python's NetworkX package performs the social network analysis.
- **Data Storage**: 
  - **MongoDB**: Stores user data and calculation results, providing a scalable and flexible database solution.
  - **AWS S3 Buckets**: Used for storing large input files and processing results.
- **Processing Workflow**: 
  - Uploaded files are processed and stored in the Frequency Bucket on AWS S3.
  - The LPA analysis is triggered via a Lambda function, which processes the data and stores the results in another S3 bucket.
  - Once processing is complete, the results are sent back to the client, and the user is notified via a server-sent event (SSE).

## Installation

To install and run the FakeBusters system locally, follow these steps:

1. **Clone the repository**:
    ```bash
    git clone https://github.com/FakeBusters/Fake-Busters.git
    ```

2. **Navigate to the project directory**:
    ```bash
    cd Fake-Busters
    ```

3. **Install dependencies for the client and server**:
    ```bash
    cd client
    npm install
    cd ../server
    npm install
    ```

4. **Set up the environment variables**:
    - Create an `.env` file in both the `client` and `server` directories with the necessary environment variables for MongoDB, AWS, etc.

5. **Run the servers**:
    - For the client:
      ```bash
      cd client
      npm start
      ```
    - For the server:
      ```bash
      cd server
      npm start
      ```

## Usage

Once the system is running, you can interact with it via the web interface. Users can upload datasets, configure preprocessing options, and initiate both content and network analyses. The results are displayed in the interface, where potential sock-puppets are flagged for further investigation.

## Project Structure

- **client/**: Contains the React.js frontend code.
- **server/**: Contains the Node.js backend code for handling LPA analysis.
- **network-analysis/**: Contains the Flask server code for network analysis using NetworkX.
- **scripts/**: Utility scripts for setting up and managing the project.

