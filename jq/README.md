## JQ Cheatsheet

Data:

```json
{
  "images": [
    {
      "creation_date": "2019-01-03T14:52:34.514699+00:00",
      "default_bootscript": {
        "kernel": "http://169.254.10.254/kernel/arm64/1.2.1",
        "initrd": "http://169.254.42.254/initrd/initrd-Linux-arm64-v3.14.6.gz",
        "architecture": "arm64",
        "title": "arm64 1.2.1"
      },
      "arch": "arm64",
      "id": "x6cevb6f-fe18-475f-4b92-x8ce51f92051",
      "name": "ubuntu xenial"
    },
    {
      "creation_date": "2019-01-03T14:52:34.514699+00:00",
      "default_bootscript": {
        "kernel": "http://169.254.10.254/kernel/arm64/1.2.2",
        "initrd": "http://169.254.10.254/initrd/initrd-Linux-arm64-v3.14.6.gz",
        "architecture": "arm64",
        "title": "arm64 1.2.2"
      },
      "arch": "arm64",
      "id": "x3ce2buf-fe58-47bf-8b52-c8cv51nn2050",
      "name": "alpine"
    },
    {
      "creation_date": "2019-01-03T14:52:34.514699+00:00",
      "default_bootscript": {
        "kernel": "http://169.254.10.254/kernel/arm64/1.2.1",
        "initrd": "http://169.254.10.254/initrd/initrd-Linux-arm64-v3.14.6.gz",
        "architecture": "arm64",
        "title": "amd64 1.2.1"
      },
      "arch": "arm64",
      "id": "x3cf2bbf-fe08-947f-8bf2-c8ce51f92050",
      "name": "ubuntu xenial"
    }
  ]
}
```

Return the data under the image array:

```bash
$ cat data.json | jq '.images[]'

  {
    "creation_date": "2019-01-03T14:52:34.514699+00:00",
    "default_bootscript": {
      "kernel": "http://169.254.10.254/kernel/arm64/1.2.1",
      "initrd": "http://169.254.42.254/initrd/initrd-Linux-arm64-v3.14.6.gz",
      "architecture": "arm64",
      "title": "arm64 1.2.1"
    },
    "arch": "arm64",
    "id": "x6cevb6f-fe18-475f-4b92-x8ce51f92051",
    "name": "ubuntu xenial"
  }
  {
 ...
```

Return only data relevant with arch: amd64:

```bash
$ cat data.json | jq '.images[] | select(.arch == "amd64")'
{
  "creation_date": "2019-01-03T14:52:34.514699+00:00",
  "default_bootscript": {
    "kernel": "http://169.254.10.254/kernel/amd64/1.2.1",
    "initrd": "http://169.254.10.254/initrd/initrd-Linux-amd64-v3.14.6.gz",
    "architecture": "amd64",
    "title": "amd64 1.2.1"
  },
  "arch": "amd64",
  "id": "x3cf2bbf-fe08-947f-8bf2-c8ce51f92050",
  "name": "ubuntu xenial"
}
```

Only return the id value from our query:

```bash
$ cat data.json | jq '.images[] | select(.arch == "amd64") | .id'
"x3cf2bbf-fe08-947f-8bf2-c8ce51f92050"
```

