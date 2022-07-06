# TJUPT Auto Attendance / 北洋园PT自动签到
[北洋园PT](https://www.tjupt.org/)的签到图片来自 [豆瓣电影](https://movie.douban.com/) 的海报，因此可通过查询豆瓣的方式实现自动签到。

## 用法
### GitHub Actions
1. Fork此项目，在顶部“Settings”标签中找到“Actions”→“General”→“Actions permissions”，选择“Allow all actions and reusable workflows”，然后在顶部“Actions”标签中选择“I understand my workflows, go ahead and enable them”。
2. 在顶部“Settings”标签中找到“Secrets”→“Actions”，使用“New repository secret”新建两个秘钥：
  - “USERNAME”，填写用户名；
  - “PASSWORD”，填写密码。
3. 此时GitHub Actions已启用，将会在北京时间每天00:00（UTC 16:00）开始执行（由于GitHub Actions自身限制，执行时间可能会推迟15分钟左右）。
4. 也可选择手动执行，在顶部“Actions”标签中选择“Auto Attendance”→“Run workflow”→“Run workflow”。

### 本地执行
1. 将本项目Clone到本地，将“config”文件夹下的“config.template.ini”复制一份为“config.ini”，然后修改“config.ini”中的用户名和密码。
2. 安装依赖项：在本项目根目录下执行`pip install -r requirements.txt`。
3. 在本项目根目录下执行`python main.py`。
4. 如需自动运行，可设置定时任务，例如Ubuntu下可使用Cron：

```cron
0 0 * * * cd /home/username/TjuptAutoAttendance && python3 main.py >> /home/username/TjuptAutoAttendance/out.log 2>&1
```