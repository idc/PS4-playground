# ps4-entrypoint-176
Payload executing for PS4 firmware 1.76.

Intended to be used with payloads developed using [ps4-payload-sdk](https://github.com/idc/ps4-payload-sdk). Not required, as long as the payload is well-formed (should be compatible with [original PS4-SDK](https://github.com/CTurt/PS4-SDK/tree/master/libPS4)).

Payload binary should be two 1MB sections. First 1MB section should be readable/executable data, second 1MB section should be readable/writeable data. It is OK if the binary is truncated. Sending more than 2MB of data is likely to corrupt memory and cause issues.

This fork makes several changes to the original PS4-playground to increase stability of running payload binaries and removes everything unrelated to this functionality.

## Setup
A live demo can be tried [here](http://idc.github.io/ps4-entrypoint-176/).

You should clone the repo and upload it your own server if you wish to make changes:

    git clone https://github.com/idc/ps4-payload-sdk.git

You can also download a zip of the latest source [here](https://github.com/idc/ps4-entrypoint-176/archive/gh-pages.zip).

### Code Execution
Click "Go", and wait for the text "Stage: Waiting for payload..." to appear.

Send the desired binary over TCP to your PS4 on port 9023; you can use any standard networking tool to do this, or my custom Windows tool, [WiFi-Loader](https://github.com/CTurt/WiFi-Loader)

If you're on Linux, the easiest way is probably to use `netcat`:

    nc -w 3 192.168.0.7 9023 < *.bin

After you have sent the binary, it will be executed automatically.
