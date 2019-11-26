---
layout: post
title:  "OS X에서 Launche daemon 추가하기"
date:   2019-11-26 11:30:00 +0900
categories: jekyll update
---
OS X에서 주기적인 작업 처리를 실행하는데 crontab을 사용하는 것은 권한 설정 등의 불편한 점이 있어
Launch Daemon을 사용하는 것이 좋다.

Scenario : 사용자 계정에서 300초 마다 ~/Startup/Script/run.sh를 실행하도록 launch daemon 추가 및 실행

{% highlight bash %}
$ cd ~/Library/LaunchAgents
$ cat > com.muskcat.shellscript.plist << EOF
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
    <dict>
        <key>Label</key>
        <string>com.muskcat.shellscript</string>
        <key>ProgramArguments</key>
        <array>
            <string>/Users/muskcat/Startup/Script/run.sh</string>
        </array>
        <key>Nice</key>
        <integer>1</integer>
        <key>StartInterval</key>
        <integer>300</integer>
        <key>RunAtLoad</key>
        <true/>
        <key>StandardErrorPath</key>
        <string>/Users/muskcat/Startup/Script/process.err</string>
        <key>StandardOutPath</key>
        <string>/Users/muskcat/Startup/Script/process.log</string>
    </dict>
</plist>
EOF
$ cd ~/
$ launchctl load ~/Library/LaunchAgents/com.muskcat.shellscript.plist
$ launchctl list | grep muskcat
$ launchctl unload ~/Library/LaunchAgents/com.muskcat.shellscript.plist
{% endhighlight %}
