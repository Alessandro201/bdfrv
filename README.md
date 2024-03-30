# bdfrv
Bulk Downloader For Reddit Viewer

Bdfrv is a web interface written in RUST for the Reddit posts downloaded with [Bulk Downloader For Reddit](https://github.com/aliparlakci/bulk-downloader-for-reddit).

# Features
- Perform full-text-search of posts, comments, subreddits, and users
- Find similar media in other posts
- Sort subreddits by new, top, posts author, random, and posts with unique media.
- Random feed of all posts
- Save posts, comments, subreddits, and users in a favourite section
- Given that the program starts a local server, the interface is accessible by all devices connected to the local network like a home wifi (the interface is password protected) 

# Requirements
- [ffmpeg](https://ffmpeg.org//download.html) to generate thumbnails of the videos
- .... to generate video hashes
- .... to generate image hashes

# Installation
Download the latest [release](https://github.com/Alessandro201/bdfrv/release) or clone the repository and build it from source. In the latter case, ensure you have [RUST](https://www.rust-lang.org/tools/install) and [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) installed and then type:

```bash
git pull https://github.com/Alessandro201/bdfrv
cd bdfrv
cargo build -r
```
The binary will be `target/release/bdfrv` for Linux or `target/release/bdfrv.exe` for Windows.

# How to use
You should first download some Reddit posts with Bulk Downloader For Reddit. I suggested to use the `clone` command to download both posts, comments, and media. To ensure consistency in the folder structure and file names, I also suggest to set `--time-format`, `--file-scheme`, and for users `--folder-scheme` as shown in the examples below:

To download subreddits:
```bash
bdfr clone --time-format "%Y-%m-%dT%H%M%S" --file-scheme "{{DATE}}_{{POSTID}}_{{REDDITOR}}_{{TITLE}}" --subreddit [SUBREDDIT] ./reddit
```

To download a post:
```bash
bdfr clone --time-format "%Y-%m-%dT%H%M%S" --file-scheme "{{DATE}}_{{POSTID}}_{{REDDITOR}}_{{TITLE}}" --link [LINK] ./reddit
```

To download users:
```bash
bdfr clone --time-format "%Y-%m-%dT%H%M%S" --folder-scheme "u_{{REDDITOR}}" --file-scheme "{{DATE}}_{{POSTID}}_{{REDDITOR}}_{{TITLE}}" --all-comments --submitted --user [USER] ./reddit_user 
```

Once you have downloaded the posts you first need to let BDFRV process and load them into a local database. The command will also generate thumbnails of the videos using :
```
bdfrv process --generate-thumbnails --db .\archive.db .\reddit\ .\reddit_user\
```
