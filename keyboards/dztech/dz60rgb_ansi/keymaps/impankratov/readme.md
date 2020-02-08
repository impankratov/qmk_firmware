# impankratov keymap instructions

Some info:
https://www.reddit.com/r/MechanicalKeyboards/comments/bcvcoa/compiled_list_of_dz60rgb_issuesproblems/

## Creating the impankratov dz60rgb firmware file

1. While in the `qmk_firmware` directory, issue the following command

    ```
    make git-submodule
    ```

    This will download the chibi-os submoduled needed to create firmware for ARM based boards such as the dz60rgb. 

2. While in the `qmk_firmware` directory, issue the followng command

    ```
    env CFLAGS="-Wno-error=deprecated" make dztech/dz60rgb_ansi/v1:impankratov
    ```

    This will result in a file called `dztech_dz60rgb_ansi_v1_impankratov.bin` that you can flash onto your board using QMK Toolbox. 

3. Use dfu-util to flash the firmware:
```
sudo dfu-util -D ./.build/dztech_dz60rgb_ansi_v1_impankratov.bin -R -d 0483:df11 -a 0 -s 0x08000000:leave 
```
