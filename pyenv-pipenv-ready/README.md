pyenv-pipenv环境准备
===================


[TOC]


### 一、准备pip.conf

- 把pip.conf复制到当前用户的家目录下和全局


### 二、安装pipenv

- pip install pipenv

### 三、安装pyenv


```python
git clone https://github.com/pyenv/pyenv.git /opt/.pyenv

vim /etc/profile
# 添加下面的行

export PATH
export PYENV_ROOT="/opt/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
if command -v pyenv 1>/dev/null 2>&1; then
  eval "$(pyenv init -)"
fi

```


### 四、默认安装python3.6


```python
pyenv install 3.6.0

```


### 五、pipenv 使用python3


```python
cd floader; pipenv --three; pipenv shell

```


### 六、参考


[pyenv官方github](https://github.com/pyenv/pyenv)

[pipenv官方github](https://github.com/pypa/pipenv)


[pyenv rehash problem](https://www.gsymy.com/2016/08/25/pyenv_rehash_problem.html)