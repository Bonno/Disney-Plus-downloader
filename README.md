# Disney-Plus-subtitles-downloader

## Quick start
1. Install python 3.10.0, be sure to add python to PATH while installing it

   1. Optional create a python virtual environment
   `python3 -m venv venv`

2. Run pip install -r requirements.txt

3. Copy dsnp.cfg.sample to dsnp.cfg with notepad and add your settings

4. Call `./disneyplus` with the url of the video detail page

## Widevine CDM
This repo doesn't come with a widevine cdm. You have to use your own license keys for decoding the content. Here is a good starting place for that quest:
[https://forum.videohelp.com/threads/404994-Decryption-and-the-Temple-of-Doom
](https://forum.videohelp.com/threads/404994-Decryption-and-the-Temple-of-Doom)
### Widevine Descriptor file (wvd)
Pywidevine can use a descriptor file instead of single key files. You can create this file with the following command
`pywidevine create-device -k /path/to/your/device_private_key  -c /path/to/your/device_client_id_blob -t ANDROID -l3 -o ./`

### Extra information

`disneyplus.py --nv --na --keep --url https://www.disneyplus.com/es-es/series/loki/6pARMvILBGzF -s 1 -e 1 --slang eng --flang eng`

Change eng to the language you need to download the subtitles in.

To download the subtitles in multiple languages use

`disneyplus.py --nv --na --keep --url https://www.disneyplus.com/es-es/series/loki/6pARMvILBGzF -s 1 -e 1 --slang eng spa jpn --flang eng`

Language codes

[pydisney/disneyplus_muxer.py#L105-L190](https://github.com/Bonno/Disney-Plus-downloader/blob/main/pydisney/disneyplus_muxer.py#L105-L190)

For downloading the subtitles of all the seasons use

`disneyplus.py --nv --na --all-season --keep --url https://www.disneyplus.com/es-es/series/the-mandalorian/3jLIGMDYINqD -s 1 -e 1 --slang eng --flang eng`
`disneyplus.py --nv --na --all-season --keep --url https://www.disneyplus.com/es-es/series/the-mandalorian/3jLIGMDYINqD -s 2 -e 1 --slang eng --flang eng`

Replace US in these lines with your country code, for example for France replace "region/US" with "region/NL".

[pydisney/disneyplus_api.py#L22-L26
](https://github.com/Bonno/Disney-Plus-downloader/blob/main/pydisney/disneyplus_api.py#L22-L26)

If you changed the country IP using a VPN delete the file token.ini before starting to download the subtitles, 
and change the country code in disneyplus_api.py.

This script may not work with some TV shows.
