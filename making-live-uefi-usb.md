# Live USB with UEFI enabled

1. find your device and export it
```
export LIVE_DEVICE=/dev/sdX
```

2. create GPT table and {UEFI,DATA} partitions

```
parted ${LIVE_DEVICE}
```

3. create mountpoints
```

```
