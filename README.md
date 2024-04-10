[![GitHub release (latest by date including pre-releases)](https://img.shields.io/github/v/release/nfa-vfxim/tk-multi-reviewsubmission?include_prereleases)](https://github.com/nfa-vfxim/tk-multi-reviewsubmission) 
[![GitHub issues](https://img.shields.io/github/issues/nfa-vfxim/tk-multi-reviewsubmission)](https://github.com/nfa-vfxim/tk-multi-reviewsubmission/issues) 


# Review Submission <img src="icon_256.png" alt="Icon" height="24"/>

Provides functionality to submit media to Shotgun for review.

## Requirements

| ShotGrid version | Core version | Engine version |
|------------------|--------------|----------------|
| -                | v0.19.5      | -              |

## Configuration

### Strings

| Name                 | Description                                                | Default value |
|----------------------|------------------------------------------------------------|---------------|
| `display_name`       | Specify the name that should be used in menus and the main |               |
| `new_version_status` | The value to use for a new Version's status.               | rev           |


### Booleans

| Name                | Description                                                                                                                                                                      | Default value |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `upload_to_shotgun` | Should the movie being created be uploaded to Shotgun as a version or just kept on disk? Disabling this as well as the store_on_disk option effectively disables the whole tool. | True          |
| `store_on_disk`     | Should the movie being created be kept on disk? Disabling this as well as the upload_to_shotgun option will effectively disable the whole tool.                                  | True          |


### Templates

| Name                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                              | Default value | Fields |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|--------|
| `movie_path_template` | Template defining the output location of the movie file on the the file system. For this template you can use all the fields defined in the template passed to the render_and_submit fields. In addition to these you can use the special fields width and height, which contain the resolution of the movie. If the store_on_disk setting is false, this setting will still be required but will be used as a temporary location for processing before the file is uploaded to Shotgun. |               |        |


### Integers

| Name                     | Description                                                                                                                                                                                                 | Default value |
|--------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `movie_width`            | The width of the rendered movie file                                                                                                                                                                        | 1920          |
| `movie_height`           | The height of the rendered movie file                                                                                                                                                                       | 1080          |
| `version_number_padding` | This value will be used to pad the version number in the slate and various movie burnins. This will not affect version number padding in the movie filename. See movie_path_template. Use 1 for no padding. | 3             |


### Config paths

| Name         | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                   | Default value |
|--------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| `slate_logo` | This is the path to an image to use on the slate such as a company logo. The supplied image will be reformated into a 400 pixel box and the lower left corner of the logo will be aligned 100 pixels to the right and 100 pixels above the lower left corner of the slate. You can use an image with an alpha channel if you want to add transparency. Currently any image format supported by Nuke is adequate. If this setting is an empty string, no logo will be applied. |               |


### Hooks

| Name                | Description                                                   | Default value                                               |
|---------------------|---------------------------------------------------------------|-------------------------------------------------------------|
| `render_media_hook` | Implements how media get generated while this app is running. | {self}/render_media.py:{self}/{engine_name}/render_media.py |
| `submitter_hook`    | Implements how media get sent to Shotgun                      | {self}/submitter_sgtk.py                                    |


