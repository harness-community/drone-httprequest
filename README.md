A plugin to http request plugin for Drone.

# Building

Build the plugin binary:

```text
scripts/build.sh
```

Build the plugin image:

```text
docker build -t local/httprequest -f docker/Dockerfile .
```

# Testing

Execute the plugin from your current working directory:

```text
Simple GET request
docker run --rm \
-e PLUGIN_URL='https://httpbin.org/get' \
-e PLUGIN_HTTP_METHOD='GET' \
-e PLUGIN_HEADERS='Content-Type:application/json' \
-e PLUGIN_TIMEOUT='30' \
  -w /drone/src  -v $(pwd):/drone/src local/httprequest


GET request with response logged in to a file
docker run --rm \
-e PLUGIN_URL='https://httpbin.org/get' \
-e PLUGIN_HTTP_METHOD='GET' \
-e PLUGIN_HEADERS='Content-Type:application/json' \
-e PLUGIN_TIMEOUT='30' \
-e PLUGIN_OUTPUT_FILE='/tmp/output_6008.txt' \
  -w /drone/src  -v $(pwd):/drone/src local/httprequest


GET request with proxy usage
docker run --rm \
-e PLUGIN_URL='https://httpbin.org/get' \
-e PLUGIN_HTTP_METHOD='GET' \
-e PLUGIN_HEADERS='Content-Type:application/json' \
-e PLUGIN_TIMEOUT='30' \
-e PLUGIN_IGNORE_SSL='true' \
-e PLUGIN_PROXY='http://localhost:8888' \
  -w /drone/src  -v $(pwd):/drone/src local/httprequest

Simple POST request
docker run --rm \
-e PLUGIN_URL='https://httpbin.org/post' \
-e PLUGIN_HTTP_METHOD='POST' \
-e PLUGIN_HEADERS='Content-Type:application/json' \
-e PLUGIN_REQUEST_BODY='{"name":"drone"}' \
-e PLUGIN_TIMEOUT='30' \
  -w /drone/src  -v $(pwd):/drone/src local/drone_http_request_plugin  
```
