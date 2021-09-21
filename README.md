# Demo repo

1. A git commit to this repo triggers in parallel:
   - a job on a windows host
   - a job on a linux host
2. Also, a user is able to trigger the same workflow and have options to specify:
   - platform: windows, linux or both.
   - git branch or tag
3. Windows or linux job outputs hardware parameters in the unified format:
    ```
    Host name:
    OS version:
    CPU cores:
    RAM:
    HDD size: for C:\ or /
    HDD disk usage: for C:\ or /
    ```
4. System parameters from p.3 are published as a job artifact.
