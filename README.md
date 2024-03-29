## Available Features

- [x] Download videos with watermark
- [x] Download videos without watermark
- [x] Download video thumbnail
- [x] Download audio from video
- [x] Download audio cover from video
- [x] Get details/info about a video
- [x] Download all videos published by a user with watermark
- [x] Download all videos published by a user without watermark
- [x] Download user profile picture

## Installation

TikTool is just a tool for my other projects and is still unreleased, but contributions to the project are highly appreciated.
Install the module using the following command to test it out and help us develop the project further.

```bash
pip install "git+https://github.com/simonfarah/TikTool.git#egg=TikTool"
```

## Usage

- ### Video Related Functions

    #### Main setup
    ```python
    from TikTool import Video

    video = Video("https://www.tiktok.com/@tiktok/video/xxxxxxxxxx")

    # all link formats are accepted
    ```

    #### Download video with or without watermark
    ```python
    # download video with watermark
    video.downloadVideo(watermark=True, path="video.mp4")

    # download video without watermark
    video.downloadVideo(watermark=False, path="C:/Users/user/Desktop/video.mp4")

    # if the watermark parameter was not passed,
    # it will be set to True by default

    # if the path parameter was not passed,
    # you will find the downloaded video in the following path :
    # "./download/the_video_id/"
    ```
    Extra checks : this function will return `True` if the video was downloaded successfully and `False` if the video does not exist, is private or if the video was not downloaded.

    #### Download video thumbnail
    ```python
    # download video thumbnail
    video.downloadThumbnail(path="thumbnail.jpeg")

    # if the path parameter was not passed,
    # you will find the downloaded thumbnail in the following path :
    # "./download/the_video_id/"
    ```
    Extra checks : this function will return `True` if the thumbnail was downloaded successfully and `False` if the video does not exist, is private or if the thumbnail was not downloaded.

    #### Download audio from video
    ```python
    # download audio from video
    video.downloadAudio(path="audio.mp3")

    # if the path parameter was not passed,
    # you will find the downloaded audio in the following path :
    # "./download/the_video_id/"
    ```
    Extra checks : this function will return `True` if the audio was downloaded successfully and `False` if the video does not exist, is private or if the audio was not downloaded.

    #### Download audio cover from video
    ```python
    # download audio cover from video
    video.downloadAudioCover(path="audio-cover.jpeg")

    # if the path parameter was not passed,
    # you will find the downloaded audio cover in the following path :
    # "./download/the_video_id/"
    ```
    Extra checks : this function will return `True` if the audio cover was downloaded successfully and `False` if the video does not exist, is private or if the audio cover was not downloaded.

    #### Get video details/info
    ```python
    # get global details about video
    video.getDetails()
    ```
    Extra checks : this function will return `None` if the video does not exist or is private. Response structure (`object`) :
    ```python
    {
        "shares": {
            "total": TOTAL_SHARES,
            "shares_via_whatsapp": TOTAL_SHARES_VIA_WHATSAPP
        },
        "views_count": VIDEO_VIEWS_COUNT,
        "downloads_count": VIDEO_DOWNLOADS_COUNT,
        "likes_count": VIDEO_LIKES_COUNT,
        "comments_count": VIDEO_COMMENTS_COUNT,
        "download": {
            "wm": [LIST OF DOWNLOAD LINKS - WITH WATERMARK],
            "no-wm": [LIST OF DOWNLOAD LINKS - WITHOUT WATERMARK]
        },
        "music": {
            "name": MUSIC_NAME,
            "owner_username": MUSIC_OWNER_USERNAME,
            "owner_name": MUSIC_OWNER_NAME,
            "download_link": MUSIC_DOWNLOAD_LINK,
            "cover_image": MUSIC_COVER_IMAGE_DOWNLOAD_LINK
        },
        "hashtags": [LIST OF HASHTAGS]
    }
    ```

- ### User Related Funtions

    #### Main setup
    ```python
    from TikTool import User

    user = User("username")
    ```

    #### Download user published videos with or without watermark
    ```python
    # download all the user published videos (with watermark)
    user.downloadAllVideos(watermark=True)

    # download all the user published videos (without watermark)
    user.downloadAllVideos(watermark=False)

    # if the watermark parameter was not passed,
    # it will be set to True by default

    # you will find the downloaded videos in the following path :
    # "./download/username/"
    ```
    Extra checks : this function will return `True` if the videos were downloaded successfully and `False` if the user does not exist, is a private account or if the videos were not downloaded.


    #### Download the user profile picture
    ```python
    # download the user profile picture
    user.downloadProfilePicture(path="profile.jpeg")

    # if the path parameter was not passed,
    # you will find the downloaded profile picture in the following path :
    # "./download/username/"
    ```
    Extra checks : this function will return `True` if the profile picture was downloaded successfully and `False` if the user does not exist, is a private account or if the profile picture was not downloaded.
