- распаковать архив gst-rtsp-server1.0_1.14u1804.tgz в удобное место
- в скрипте rtsp-run указать:
   wd - абсолютный путь к папке, из которой будут проигрываться ролики в формате m4v
   streamer - абсолютный путь к вещателю из архива gst-rtsp-server1.0_1.14u1804.tgz
- chmod +x rtsp-run
- запустить rtsp-run. URL видеопотока будет rtsp://<ip-addr>:200<N>/test, где N - от 1 до количества роликов в $wd

для автозапуска:
- создать systemd-unit с содержимым как в rtsp-streamer.service (cp rtsp-streamer.service /etc/systemd/system/rtsp-streamer.service)
- исправить в /etc/systemd/system/rtsp-streamer.service путь в ExecStart
- активировать юнит systemctl enable rtsp-streamer.service
- теперь управлять вещателем можно через "service rtsp-streamer start/stop" или через "systemctl start/stop"