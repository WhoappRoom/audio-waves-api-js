# audio-waves-api-js

Audio Waves API Documentation
=============================

*   [Introduction](#introduction)
*   [Endpoints](#endpoints)
*   [Get All Audios](#get-all-audios)
*   [Get Audio by ID](#get-audio-by-id)
*   [Examples](#examples)

Introduction
------------

Welcome to the Audio Waves API documentation. This API allows you to retrieve audio files in the Audio Waves application.

Visit the [Audio Waves web app](https://audio-waves.vercel.app) to see the application in action.

Endpoints
---------
*     https://audio-waves-api-js.vercel.app
*   [GET /audios/api](#get-all-audios): Retrieve all audio files.
*   [GET /audios/api/{audioId}](#get-audio-by-id): Retrieve a specific audio file by ID.

Get All Audios
--------------

Retrieve a list of all audio files.

    GET /audios/api

### Example Request

    fetch('https://audio-waves-api-js.vercel.app/audios/api')
      .then(response => response.json())
      .then(data => console.log(data))
      .catch(error => console.error('Error:', error));

### Example Response

    [
      {
        "id": "123",
        "name": "Sample Audio",
        "orginal": "Original Sample Audio",
        "time": "2024-07-20T12:00:00Z",
        "url": "https://example.com/audio.mp3",
        "userImage": "https://example.com/user.jpg",
        "userName": "Axmed aadan",
        "countPlays": 124
      }
    ]

Get Audio by ID
---------------

Retrieve details of a specific audio file by its ID.

    GET /audios/api/{audioId}

### Example Request

    fetch('https://audio-waves-api-js.vercel.app/audios/api/SM2k7D1KnvUuQa32A2cO')
      .then(response => response.json())
      .then(data => console.log(data))
      .catch(error => console.error('Error:', error));

### Example Response

    {
      "id": "123",
      "name": "Sample Audio",
      "orginal": "Original Sample Audio",
      "time": "2024-07-20T12:00:00Z",
      "url": "https://example.com/audio.mp3",
      "userImage": "https://example.com/user.jpg",
      "userName": "Axmed aadan",
      "countPlays": 124
    }

Examples
--------

### Example: Fetching All Audios and Displaying Them

The following example demonstrates how to fetch all audio files and display them using HTML and JavaScript:

    <!DOCTYPE html>
    <html>
    <head>
      <title>Audio Waves Example</title>
    </head>
    <body>
      <h1>Audio Files</h1>
      <div id="audio-list"></div>
    
      <script>
        fetch('https://audio-waves-api-js.vercel.app/audios/api')
        .then(response => response.json())
        .then(data => {
          const audioList = document.getElementById('audio-list');
          data.forEach(audio => {
            const audioContainer = document.createElement('div');
            audioContainer.innerHTML = `
              <h3>${audio.name || audio.orginal}</h3>
              <audio controls src="${audio.url}"></audio>
              <p>Uploaded on: ${audio.time}</p>
              <p>Counts : ${audio.countPlays}</p>
              <p>Uploaded by: <img src="${audio.userImage}" alt="User Image" width="50" /> ${audio.userName}</p>
            `;
            audioList.appendChild(audioContainer);
          });
        })
        .catch(error => console.error('Error:', error));
      </script>
    </body>
    </html>

### Example: Fetching a Specific Audio by ID

The following example demonstrates how to fetch a specific audio file by its ID and display it:

    <!DOCTYPE html>
    <html>
    <head>
      <title>Audio Waves Example</title>
    </head>
    <body>
      <h1>Audio File</h1>
      <div id="audio-details"></div>
    
      <script>
        const audioId = 'SM2k7D1KnvUuQa32A2cO';  // Replace with the audio ID
        fetch(`https://audio-waves-api-js.vercel.app/audios/api/${audioId}`)
        .then(response => response.json())
        .then(audio => {
          const audioDetails = document.getElementById('audio-details');
          audioDetails.innerHTML = `
            <h3>${audio.name || audio.orginal}</h3>
            <audio controls src="${audio.url}"></audio>
            <p>Uploaded on: ${audio.time}</p>
            <p>Counts : ${audio.countPlays}</p>
            <p>Uploaded by: <img src="${audio.userImage}" alt="User Image" width="50" /> ${audio.userName}</p>
          `;
        })
        .catch(error => console.error('Error:', error));
      </script>
    </body>
    </html>

Visit more of our web apps:

[My Coder Seven](https://mycoderseven.site) | [Small Pencil](https://small-pencil.website)
