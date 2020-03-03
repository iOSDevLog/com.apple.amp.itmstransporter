# Transporter
---

解决使用 Transporter 上传 **ipa** 到 App Store 时，有时间会卡住或者非常慢。

## 使用

1. 下载 `Release` 下面的 `zip` 包，或者 `git clone https://github.com/iOSDevLog/com.apple.amp.itmstransporter`
1. 替换`~/Library/Caches/com.apple.amp.itmstransporter`

## 原因

Transporter 安装上第一次打开后，会在硬盘目录：`~/Library/Caches/com.apple.amp.itmstransporter` 目录下下载一些缓存文件，这些缓存文件没有下载完，或者下载失败没下载完时，使用Transporter去提交应用这个页面就会卡住或者这个页面很慢。

## 解决方案

终端运行命令

```bash
/Applications/Transporter.app/Contents/itms/bin/iTMSTransporter
```

查看 `~/Library/Caches/com.apple.amp.itmstransporter` 变化

如果有报错信息 `https://...jar`，把 `jar` 文件下载下来，放入 `~/Library/Caches/com.apple.amp.itmstransporter/obr/2.2.0/`

再次运行

`/Applications/Transporter.app/Contents/itms/bin/iTMSTransporter`

```bash
[2020-03-03 12:28:39 CST] <main>  INFO: Configuring logging...
[2020-03-03 12:28:39 CST] <main>  INFO: Logging level set to eXtreme
[2020-03-03 12:28:39 CST] <main>  INFO: Transporter is searching for new software components.
[2020-03-03 12:28:39 CST] <main>  INFO: INFO: using cached repository.xml file.
[2020-03-03 12:28:40 CST] <main>  INFO: Update check complete.
[2020-03-03 12:28:41 CST] <main> DEBUG: Attempting refresh of configuration data from https://contentdelivery.itunes.apple.com/transporter/Defaults.properties
[2020-03-03 12:28:41 CST] <main> DEBUG: Configuration refresh successful.
[2020-03-03 12:28:41 CST] <main> DEBUG: Saving configuration to local path: /Users/iosdevlog/Library/Caches/com.apple.amp.itmstransporter/Defaults.properties
usage: iTMSTransporter [-help <arg> | -info | -m <arg> | -version]   [-o <arg>] [-v
       <arg>]  [-WONoPause <arg>] [-Xmx4096m]
iTMSTransporter : iTunes Store Transporter 2.0.0
 -help <arg>        Show this help.  If a mode value is specified, show help specific
                    to that mode.
 -info              The -info option should be used by itself and returns the
                    copyright notice and acknowledgements.
 -m <arg>           The -m option specifies the tool's mode.  The valid values are:
                    verify, upload, provider, diagnostic, lookupMetadata,
                    createArtist, lookupArtist, status, statusAll,
                    createMetadataTicket, queryTickets, generateSchema, transferTest,
                    downloadMetadataGuides, listReports, requestReport
 -o <arg>           The -o option specifies the directory and filename you want to use
                    to log output information.  By default, Transporter logs output
                    information to standard out. If you specify a filename,
                    Transporter logs the output to the specified file, as well as to
                    standard out.
 -v <arg>           The -v option specifies the level of logging.  The five values
                    are: off, detailed, informational, critical, eXtreme.
 -version           The -version option should be used by itself and returns the
                    version of the tool.
 -WONoPause <arg>   The -WONoPause option is only valid on Windows and its value can
                    be 'true' or 'false'.  If an error occurs during script execution,
                    the process idles because the message 'Press any key...' is
                    displayed on the console and the system awaits a keypress. To
                    avoid this behavior, set this property to true
 -Xmx4096m          Specifies that you want to change the Java Virtual Machine's (JVM)
                    allocated memory by increasing the JVM heap size.  By default,
                    Transporter uses a 2048MB heap size. You can use the -Xmx4096m
                    option to specify a 4-gigabyte (GB) heap size. Apple recommends,
                    if needed, increasing the heap size to 4096MB by specifying the
                    -Xmx4096m (or -Xmx4g) option and adjusting as needed.
[2020-03-03 12:28:41 CST] <main> DBG-X: Returning 0
```

出现以上结果说明正常
