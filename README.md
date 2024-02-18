# GitHubPoster

- **[Apple Health](#AppleHealth)**


## 下载

## pip 安装

```
pip3 install -U 'github_poster[all]'
```

## 安装(Python3.6+)

```
pip3 install -r requirements.txt
```

## 使用

生成的 svg 在 `OUT_FOLDER` 内, 用 type 命名（暂时）

不同类型按下方指定的使用方式：

- `--year 2022`: 可以指定年份(默认)或年份区间 `--year 2012-2022`
- `--track-color=#f4cccc`: 指定基础颜色
- `--special-number1 10 -- special_number2 20`: 可以指定特殊颜色，默认自动生成不同颜色需要的 number（特殊颜色）
- `--special-color1 pink --special-color2 '#33C6A4'`: 指定特殊颜色
- `--with-animation`: 可以增加动画  (加入 GOGOGO 动画)
- `--animation-time 14`: 可以控制动画时间（默认是 10s）, 配合 `--with-animation` 使用
- `--with-skyline`: 可以增加 Skyline  (默认生成的为 to_year)
- `--skyline-with-name`: 将用户名打印在 Skyline 上, 配合 `--with-skyline` 使用
- `--is-circular`: 支持 circular svg 配合动画
- `--without-type-name`: 支持隐藏标题中生成类型的名称


### AppleHealth
<details>
<summary>Make <code> Apple Health </code> GitHub poster</summary>

Apple Health 里有丰富的数据，此 loader 暂时只支持 Apple Watch Activity 里的三大项，即 Move，Exercise，Stand。但理论上任何 Apple Health 里的数据都能支持。

Loader 支持两种模式: 

increment 模式（默认）适用于每日更新，可利用 Shortcut 每日自动触发，参考 https://github.com/yihong0618/iBeats
<br>
```
python3 -m github_poster AppleHealthData --date <date-str> --value <value> --apple_health_record_type <move, exercise, stand> --me "your name"
or
github_poster AppleHealthData --appple_health_date <date-str> --apple_health_value <value> --apple_health_record_type <move, exercise, stand> --me "your name"
```

backfill 模式适用于一次性导入所有数据。
打开 Health App, 点击右上方头像，选择 Export All Health Data, 将所得压缩包拷贝到 `IN-FOLDER` 后解压，会得到一个 `apple_health_export` 文件夹。之后运行:
<br>
```
python3 -m github_poster AppleHealthData --apple_health_mode backfill --year 2015-2021 --apple_health_record_type <move, exercise, stand> --me "your name"
or
github_poster AppleHealthData --apple_health_mode backfill --year 2015-2021 --apple_health_record_type <move, exercise, stand> --me "your name"
```

</details>

