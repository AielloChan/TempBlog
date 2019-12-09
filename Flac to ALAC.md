# 将 Flac 文件转换为 iTunes 能够使用的 Apple lossless 文件

命令行直接使用 ffmpeg 转换

```shell
ffmpeg -i Awake.flac -acodec alac -vcodec copy Awake.m4a
```

只需要将 `-acodec alac` 传递给命令行就能够实现转换，如果你的音乐文件是带封面的，可以加上 `-vcodec copy` 这个选项，会顺带把封面等信息复制过来😃

如果你的文件比较多，那可以选择批量转换，如下

```shell
for f in ./*.flac; do ffmpeg -i $f -acodec alac -vcodec copy ${f%flac}m4a; done
```
上面的命令会将当前文件夹里面的所有 `flac` 结尾的文件都转换为 ALAC 并且将其后缀名改为 `m4a`
