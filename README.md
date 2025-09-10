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
```

```sh
vmalert-tool unittest --files=./unittest/testdata2/test.yaml -external.label=cluster=prod
```

See what issues vmalert-tool does not catch:

```sh
vmalert-tool unittest --files=./unittest/testdata3/test.yaml -external.label=cluster=prod
```

These are things you can likely catch with https://www.conftest.dev

---

testdata1-3 are issues that can be caught without having the people who define alerts ~~define any mock data~~ _this is unclear for the moment, if defining tests is required for validations, that's perfectly fine_.

If one is willing to have people write simple expectations for what alerts _should_ look like, there's opportunity for much more:

```sh
vmalert-tool unittest --files=./unittest/testdata4/test.yaml -external.label=cluster=prod
```

These may seem minor, but if you let botched manifest get deployed, the people who _now expect to have an alert working_ are blissfully assuming they get notified of issues, will only find out when the issue has become a major one so that a human is contacting them. Therefore catching simple typos etc. is very valuable, they're more common than one might think.
