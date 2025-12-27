`grep`（Global Regular Expression Print）是 Linux/Unix 中用于**在文件或输入流中搜索匹配指定模式的行**的强大文本搜索工具。它支持正则表达式，广泛用于日志分析、代码查找、数据过滤等场景。

以下是 `grep` 常用参数（选项）的详细介绍：

---

## 🔑 基本语法
```bash
grep [选项] '模式' 文件...
```

---

## 📌 常用参数详解

| 参数 | 说明 |
|------|------|
| `-i` | **忽略大小写**<br>例：`grep -i "error" log.txt` → 匹配 error、ERROR、Error 等 |
| `-v` | **反向匹配**（显示不匹配的行）<br>例：`grep -v "^#" config.conf` → 过滤掉注释行 |
| `-n` | **显示行号**<br>例：`grep -n "main" script.py` → 显示匹配行及其行号 |
| `-c` | **只输出匹配行的数量**（count）<br>例：`grep -c "success" access.log` |
| `-l` | **只列出包含匹配内容的文件名**（多个文件时）<br>例：`grep -l "TODO" *.md` |
| `-L` | **列出不包含匹配内容的文件名**（与 `-l` 相反） |

---

## 🔍 搜索范围控制

| 参数 | 说明 |
|------|------|
| `-r` 或 `--recursive` | **递归搜索子目录**<br>例：`grep -r "password" /etc/` |
| `-R` | 类似 `-r`，但会跟随符号链接（symbolic links） |
| `--include="*.ext"` | 递归时**只搜索特定类型文件**<br>例：`grep -r --include="*.py" "def" .` |
| `--exclude="file"` | 递归时**排除某些文件**<br>例：`grep -r --exclude="*.log" "error" .` |
| `--exclude-dir=dir` | 递归时**跳过指定目录**<br>例：`grep -r --exclude-dir=.git "TODO" .` |

---

## 🧩 正则与匹配模式

| 参数 | 说明 |
|------|------|
| `-E` 或 `--extended-regexp` | 使用**扩展正则表达式**（等价于 `egrep`）<br>例：`grep -E "error|warning" log.txt` |
| `-F` 或 `--fixed-strings` | 将模式视为**普通字符串**（禁用正则，等价于 `fgrep`）<br>例：`grep -F "[ERROR]" log.txt`（避免 `[` 被当作正则字符） |
| `-w` | **整词匹配**（word boundary）<br>例：`grep -w "cat" file` → 匹配 "cat"，但不匹配 "category" |
| `-x` | **整行完全匹配**<br>例：`grep -x "127.0.0.1" hosts` → 只匹配整行就是该 IP 的行 |

---

## 🖨️ 输出格式控制

| 参数 | 说明 |
|------|------|
| `-A N` | 显示匹配行**之后 N 行**（After）<br>例：`grep -A 2 "Exception" app.log` |
| `-B N` | 显示匹配行**之前 N 行**（Before） |
| `-C N` 或 `--context=N` | 显示匹配行**前后各 N 行**（Context）<br>例：`grep -C 3 "segfault" dmesg` |
| `--color=auto` | **高亮匹配内容**（大多数系统默认已启用） |

---

## 🛠️ 其他实用选项

| 参数 | 说明 |
|------|------|
| `-q` | **静默模式**（quiet），不输出内容，仅通过退出状态判断是否匹配（常用于脚本）<br>例：`if grep -q "running" status.txt; then ...` |
| `-s` | **不显示错误信息**（如“文件不存在”） |
| `-H` | **显示文件名**（当搜索多个文件时，默认开启；单文件时可用 `-H` 强制显示） |
| `-h` | **不显示文件名**（多文件搜索时隐藏来源文件） |

---

## ✅ 经典使用示例

```bash
# 1. 忽略大小写搜索
grep -i "login" /var/log/auth.log

# 2. 递归搜索所有 Python 文件中的函数定义
grep -r --include="*.py" "^def " .

# 3. 查找包含 "ERROR" 的行，并显示前后 2 行上下文
grep -C 2 "ERROR" app.log

# 4. 统计某关键词出现次数
grep -c "404" access.log

# 5. 找出哪些 .md 文件包含 "TODO"
grep -l "TODO" *.md

# 6. 过滤空行和注释（#开头）
grep -v "^#\|^$" config.conf
```

---

## 💡 小贴士

- `grep` 默认使用**基本正则表达式（BRE）**，复杂模式建议用 `-E`。
- 想要更强大的功能？试试 `ripgrep`（`rg`）或 `ack`，速度更快、默认递归、对代码友好。
- 在管道中常用：`ps aux | grep nginx`

---

掌握这些参数，你就能高效地在海量文本中精准定位所需信息！🔍