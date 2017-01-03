Run it like this:

mkdir /mnt/mp3
mount --bind /mnt/mp3 /mnt/mp3
mount --make-shared /mnt/mp3

docker run --rm -t -i --cap-add mknod --cap-add sys_admin --device=/dev/fuse \
    -v /path/to/flac/:/input \
    -v /mnt/mp3:/output \
    dartagan/mp3fs -f /input /output
