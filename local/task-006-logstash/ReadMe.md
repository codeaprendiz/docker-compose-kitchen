## Logstash docker-compose

- input from file
- filter logs using grok filter (allowed everything)
- output to stdout

```bash
$ docker-compose up
.
.
.
logstash-sandbox    | {"level":"INFO","loggerName":"logstash.agent","timeMillis":1594974961328,"thread":"Api Webserver","logEvent":{"message":"Successfully started Logstash API endpoint","port":9600}}
logstash-sandbox    | /usr/share/logstash/vendor/bundle/jruby/2.5.0/gems/awesome_print-1.7.0/lib/awesome_print/formatters/base_formatter.rb:31: warning: constant ::Fixnum is deprecated
logstash-sandbox    | {
logstash-sandbox    |           "ident" => "-",
logstash-sandbox    |         "request" => "/xampp/status.php",
logstash-sandbox    |        "clientip" => "127.0.0.1",
logstash-sandbox    |        "@version" => "1",
logstash-sandbox    |        "response" => "200",
logstash-sandbox    |         "message" => "127.0.0.1 - - [11/Dec/2013:00:01:45 -0800] \"GET /xampp/status.php HTTP/1.1\" 200 3891 \"http://cadenza/xampp/navi.php\" \"Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:25.0) Gecko/20100101 Firefox/25.0\"",
logstash-sandbox    |            "auth" => "-",
logstash-sandbox    |            "path" => "/tmp/access.log",
logstash-sandbox    |           "bytes" => "3891",
logstash-sandbox    |      "@timestamp" => 2013-12-11T08:01:45.000Z,
logstash-sandbox    |            "verb" => "GET",
logstash-sandbox    |            "host" => "8ab5d2b292ee",
logstash-sandbox    |       "timestamp" => "11/Dec/2013:00:01:45 -0800",
logstash-sandbox    |        "referrer" => "\"http://cadenza/xampp/navi.php\"",
logstash-sandbox    |     "httpversion" => "1.1",
logstash-sandbox    |           "agent" => "\"Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:25.0) Gecko/20100101 Firefox/25.0\""
logstash-sandbox    | }
logstash-sandbox    | {
logstash-sandbox    |           "ident" => "-",
logstash-sandbox    |         "request" => "/xampp/status.php",
logstash-sandbox    |        "clientip" => "127.0.0.1",
logstash-sandbox    |        "@version" => "1",
logstash-sandbox    |        "response" => "200",
logstash-sandbox    |         "message" => "127.0.0.1 - - [11/Dec/2013:00:01:45 -0800] \"GET /xampp/status.php HTTP/1.1\" 200 3891 \"http://cadenza/xampp/navi.php\" \"Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:25.0) Gecko/20100101 Firefox/25.0\"",
logstash-sandbox    |            "auth" => "-",
logstash-sandbox    |            "path" => "/tmp/access.log",
logstash-sandbox    |           "bytes" => "3891",
logstash-sandbox    |      "@timestamp" => 2013-12-11T08:01:45.000Z,
logstash-sandbox    |            "verb" => "GET",
logstash-sandbox    |            "host" => "8ab5d2b292ee",
logstash-sandbox    |       "timestamp" => "11/Dec/2013:00:01:45 -0800",
logstash-sandbox    |        "referrer" => "\"http://cadenza/xampp/navi.php\"",
logstash-sandbox    |     "httpversion" => "1.1",
logstash-sandbox    |           "agent" => "\"Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:25.0) Gecko/20100101 Firefox/25.0\""
logstash-sandbox    | }
.
.
.
```