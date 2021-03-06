MPS converts audio/video files to different bitrates and resolutions for smooth playback on various devices with different bandwidth options. It has the following features:

## Audio/Video Transcoding
Transcoding is an offline task that converts the source audio/video bitstream to another one. It changes parameters of the source bitstream, such as container format, resolution, and bitrate, to adapt it to different devices and network conditions. The following benefits can be achieved with transcoding:
- Compatibility with more devices: A source video can be transcoded to various formats (e.g., MP4) that are compatible with more types of devices for smooth playback.
- Adaption to different bandwidth options: A source video can be transcoded and output in various definitions such as LD, SD, HD, and FHD, and end users can select the most appropriate bitrate for their network conditions.
- Improvement in playback efficiency: The moov atom can be moved from the end of an MP4 file to its beginning, so that the player can play back a video before the entire video is downloaded.
- Reduced bandwidth consumption: With a more advanced codec (e.g., H.265), the bitrate of a video can be substantially reduced while retaining the original quality, which helps reduce the bandwidth consumption.


The target specification of an output video after transcoding is subject to parameters such as container format, resolution, and bitrate, which can be customized as shown below:

<table>
    <tr>
        <th style="width:18%">
            Category
        </th>
        <th style="width:22%">
            Parameter
        </th>
        <th>
            Description
        </th>
    </tr>
    <tr>
        <td rowspan=4>
            Muxing
        </td>
    </tr>
    <tr>
        <td>
            Container format
        </td>
        <td>
			The following video and audio container formats are supported:
            <li>Video: MP4, TS, HLS, and FLV</li>
            <li>Audio: MP3, M4A, FLAC, and OGG</li>
        </td>
    </tr>
    <tr>
        <td>
            Video stream deletion
        </td>
        <td>
            If this parameter is enabled, the output video after transcoding will contain only the audio stream with the video stream discarded
        </td>
    </tr>
    <tr>
        <td>
            Audio stream deletion
        </td>
        <td>
            If this parameter is enabled, the output video after transcoding will contain only the video stream with the audio stream discarded
        </td>
    </tr>
    <tr>
        <td rowspan=7>
            Video encoding
        </td>
        <td>
            Codec
        </td>
        <td>
            H.264 and H.265 are supported
        </td>
    </tr>
    <tr>
        <td>
            Bitrate
        </td>
        <td>
            Supported bitrate range: 10–35 Mbps
        </td>
    </tr>
    <tr>
        <td>
            Frame rate
        </td>
        <td>
            Supported frame rate range: 1–60 fps; common values: 24, 25, and 30 fps
        </td>
    </tr>
    <tr>
        <td>
            Resolution
        </td>
        <td>
            <li>Supported width range: 128–4,096 px</li>
            <li>Supported height range: 128–4,096 px</li>
        </td>
    </tr>
    <tr>
        <td>
            GOP (short for group of pictures) length
        </td>
        <td>
            Supported GOP length range: 1–10s
        </td>
    </tr>
    <tr>
        <td>
            Profile
        </td>
        <td>
            <li>When the video codec is H.264, the `Baseline`, `Main`, and `High` profiles are supported</li>
            <li>When the video codec is H.265, only the `Main` profile is supported</li>
        </td>
    </tr>
    <tr>
        <td>
            Color space
        </td>
        <td>
            YUV420P is supported
        </td>
    </tr>
    <tr>
        <td rowspan=4>
            Audio encoding
        </td>
        <td>
            Codec
        </td>
        <td>
            MP3, AAC, AC3, and FLAC are supported
        </td>
    </tr>
    <tr>
        <td>
            Sample rate
        </td>
        <td>
            The following audio sample rates are supported:
            <li>34,000 Hz</li>
            <li>44,100 Hz</li>
            <li>48,000 Hz</li>
        </td>
    </tr>
    <tr>
        <td>
            Bitrate
        </td>
        <td>
            Supported bitrate range: 26–256 Kbps, including the following values:
            <li>48 Kbps</li>
            <li>64 Kbps</li>
            <li>128 Kbps</li>
        </td>
    </tr>
    <tr>
        <td>
            Channel
        </td>
        <td>
        	<li>Mono</li>
			    <li>Dual</li>
			    <li>Stereo</li>
        </td>
    </tr>
</table>



## Watermarking
Watermarking is an offline task that adds an image at the specified position of the video during video transcoding or screencapturing. MPS supports the following types of watermarks:
- Static image watermark: This refers to an image watermark in PNG format, for example, a copyright owner's or TV station's logo, which is generally used to indicate the video copyright ownership.
- Animated image watermark: This refers to an image watermark in APNG format, which can be animated.

MPS can add multiple watermarks to a video or screenshot whose size and position can be customized individually.


The target specification of a watermark is subject to parameters such as watermark type, width, height, and position which can be customized as shown below:

| Parameter                     | Description                                                         |
| ------------------------ | ------------------------------------------------------------ |
| Type         | Static or animated image watermark                           |
| Position     | Relative position of a watermark in the video                                 |
| ImageSize    | Size of a watermark in the video                                |
| ImageContent | Binary content of a watermark                                 |




## Screencapturing

Screencapturing is an offline task that captures a screenshot of a video at a certain point in time. MPS provides the following types of screenshots:
- Time point screenshot: MPS can capture screenshots of a video at the specified set of points in time.
- Sampled screenshot: MPS can capture a set of screenshots of a video at the specified time interval.
- Image sprite: MPS can capture a set of screenshots of a video at the specified time interval and stitch them together to generate a large image (i.e., image sprite).


The target specification of a screenshot is subject to parameters such as screenshot file format, width, and height, which can be customized as shown below:

### Time point screenshot


| Parameter | Description |
| -------------------- | ------------------------------------------------------------ |
| Format       | Output format of a screenshot file. Currently, only JPG is supported                         |
| Width        | Screenshot width. Value range: 128–4,096 px                             |
| Height     | Screenshot height. Value range: 128–4,096 px                             |
| FillType | Filling refers to the way of processing a screenshot when its aspect ratio is different from that of the source video. Generally, the following filling types are supported: <li>Stretch: The screenshot is stretched to match the aspect ratio of the source video, which may make the screenshot "shorter" or "longer" </li><li>Fill with black: This option retains the aspect ratio of the source video for the screenshot and fill the unmatched area with black color blocks </li><li>Fill with white: This option retains the aspect ratio of the source video for the screenshot and fill the unmatched area with white color blocks </li><li>Gaussian blur: This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with Gaussian blur </li> |


### Sampled screenshot


| Parameter                     | Description                                                         |
| ---------------------- | ------------------------------------------------------------ |
| Format       | Output format of a screenshot file. Currently, only JPG is supported                         |
| Width        | Screenshot width. Value range: 128–4,096 px                             |
| Height     | Screenshot height. Value range: 128–4,096 px                             |
| SampleType | The following two types are supported: <li>Sample by percent: If this type is selected and `Interval` is set to `5%` for example, 20 screenshots will be generated </li><li>Sample by time: If this type is selected and `Interval` is set to `10s` for example, the number of generated screenshots will depend on the video length </li> |
| Interval   | Sampling interval. <li>If the sampling type is by percent, this parameter will be a percent value </li><li>If the sampling type is by time, this parameter will be a second value </li> |
| FillType | Filling refers to the way of processing a screenshot when its aspect ratio is different from that of the source video. Generally, the following filling types are supported: <li>Stretch: The screenshot is stretched to match the aspect ratio of the source video, which may make the screenshot "shorter" or "longer" </li><li>Fill with black: This option retains the aspect ratio of the source video for the screenshot and fill the unmatched area with black color blocks </li><li>Fill with white: This option retains the aspect ratio of the source video for the screenshot and fill the unmatched area with white color blocks </li><li>Gaussian blur: This option retains the aspect ratio of the source video for the screenshot and fills the unmatched area with Gaussian blur </li> |


### Image sprite

| Parameter                     | Description                                                         |
| ---------------------- | ------------------------------------------ |
| Format       | Output format of an image sprite file. Currently, only JPG is supported                         |
| Width      | Sub-image width of an image sprite                       |
| Height   | Sub-image height of an image sprite                       |
| Rows       | Number of rows of sub-images in an image sprite                 |
| Columns    | Number of columns of sub-images in an image sprite                  |
| SampleType | Sampling type of sub-images. Currently, only sampling by time is supported |
| Interval   | Time interval for capturing a screenshot as a sub-image     |

>
>- The value of `Width` * `Columns` should be between 128 and 4,096 px (i.e., the range of the image sprite width).
>- The value of `Height` * `Rows` should be between 128 and 4,096 px (i.e., the range of the image sprite height).



## Animated image generating
Animated image generating is an offline task that converts a video to an animated image such as in GIF or WEBP format. An animated image is a seamless cycle of continuous frames, which can deliver an animation effect with a small file size.


The target specification of an animated image is subject to parameters such as animated image format, width, height, and frame rate, which can be customized as shown below:

| Parameter                     | Description                                                         |
| ---------------- | -------------------------------------------- |
| Format   | Output format of an animated image file. Currently, only GIF and WEBP are supported |
| Width        | Animated image width. Value range: 128–4,096 px                             |
| Height     | Animated image height. Value range: 128–4,096 px                             |
| FPS      | Supported frame rate range: 1–60 fps                  |

