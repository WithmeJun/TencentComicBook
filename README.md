# TencentComicBook

腾讯漫画、哔哩哔哩漫画、有妖气漫画爬虫

## 本项目特点

- [x] 漫画批量下载
- [x] 分目录按章节保存
- [x] 支持腾讯漫画、哔哩哔哩漫画、有妖气漫画
- [x] 支持登录
- [x] 支持生成pdf
- [x] 支持发送到邮箱
- [x] 集成api，方便调用 [API-README](API-README.md)


## 使用步骤
```sh
# clone项目
git clone git@github.com:lossme/TencentComicBook.git
# 切换工作目录
cd TencentComicBook
# 安装依赖
python3 -m pip install requirements.txt
# 查看帮助
python3 -m onepiece --help
```

## 常规使用

默认从腾讯漫画下载，注意不同站点的comicid区别

- 下载海贼王最新一集: `python3 -m onepiece`
- 下载漫画 id=505430 最新一集: `python3 -m onepiece --comicid=505430`
- 下载漫画 id=505430 所有章节: `python3 -m onepiece --comicid=505430 --all`
- 下载漫画 id=505430 第800集: `python3 -m onepiece --comicid=505430 --chapter=800`
- 下载漫画 id=505430 倒数第二集: `python3 -m onepiece --comicid=505430 --chapter=-2`
- 下载漫画 id=505430 1到5集,7集，9到10集: `python3 -m onepiece --comicid=505430 --chapter=1-5,7,9-10`
- 下载漫画 id=505430 并生成pdf文件: `python3 -m onepiece --comicid=505430 --pdf`
- 下载漫画 id=505430 并推送到邮箱: `python3 -m onepiece --comicid=505430 --pdf --mail`
- 从鼠绘漫画下载: `python3 -m onepiece --site=ishuhui --comicid=1 --chapter=1-5`
- 从哔哩哔哩漫画下载: `python3 -m onepiece --site=bilibili --comicid=mc24742 --chapter=1-5`
- 从有妖气漫画下载: `python3 -m onepiece --site=u17 --comicid=195 --chapter=-1`

若不清楚或不记得comicid，可以使用名字来搜索，按照提示输入comicid

- `python3 -m onepiece --site=qq --name=海贼 --chapter=1-5`
- `python3 -m onepiece --site=bilibili --name=海贼 --chapter=-1`
- `python3 -m onepiece --site=u17 --name=雏蜂 --chapter=-1`

**注意**: 发送到邮箱需预先配置好信息

复制`config.ini.example`并命名为`config.ini`，并根据实际情况修改`config.ini`的参数

#### 关于登录

限于本人能力有限，登录懒得搞，只好祭出selenium这个大杀器

1. 安装selenium: `python3 -m pip install selenium`
2. 安装chrome浏览器，或其它浏览器
3. [下载chromedriver](https://chromedriver.chromium.org/downloads)，或其它浏览器的driver
4. 登录，并将cookies保存在本地（保存登录状态，存着下次用）
```sh
python3 -m onepiece --site=qq --comicid=505430 --chapter=-1 \
  --login \
  --driver-path="driver路径" \
  --driver-type="Chrome" \
  --session-path=".cache/session.pickle"
```


**免责声明**：本项目仅供学习交流之用，请勿用于非法用途。
