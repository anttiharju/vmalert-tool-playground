# vmalert-tool-playground

1. Install vmalert-tool from https://github.com/VictoriaMetrics/VictoriaMetrics/releases/download/v1.125.1/vmutils-darwin-arm64-v1.125.1.tar.gz
2. Understand it from https://docs.victoriametrics.com/victoriametrics/vmalert-tool/
3. Run the example:

```sh
vmalert-tool unittest --files=./unittest/testdata/test.yaml -external.label=cluster=prod
```

See what issues vmalert-tool catches:

```sh
vmalert-tool unittest --files=./unittest/testdata1/test.yaml -external.label=cluster=prod
vmalert-tool unittest --files=./unittest/testdata2/test.yaml -external.label=cluster=prod
```
