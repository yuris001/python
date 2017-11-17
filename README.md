

### pyenv インストール
本体
```
git clone https://github.com/yyuu/pyenv.git ~/.pyenv
```

環境設定(CentOS)
Ubuntuの場合は .bashrc らしい?
```
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bash_profile
echo 'export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bash_profile
echo 'eval "$(pyenv init -)"' >> ~/.bash_profile
```

source で適用かな

### pyenv virtual インストール
本体
```
git clone https://github.com/yyuu/pyenv-virtualenv.git ~/.pyenv/plugins/pyenv-virtualenv
```

環境設定(CentOS)
```
echo ‘eval “$(pyenv virtualenv-init -)”’ >> ~/.bash_profile
```

source で適用かな

使い方
```
$ pyenv virtualenv 3.5.1 projectA
$ pyenv virtualenv 3.5.1 projectB
このコマンドを実行すると ~/.pyenv/versions/projectA, ~/.pyenv/versions/projectB というディレクトリが作成され、pyenv の環境として指定できるようになります。
```

---

### PyPi への登録

.pypircの作成
```
[distutils]
index-servers =
    pypi
    pypitest

[pypi]
#repository: https://upload.pypi.org/legacy/ これはいらないのかな。
username: hoge
password: fuga

[pypitest]
repository: https://test.pypi.org/legacy/
username: hoge
password: fuga
```

ディレクトリ構成
```
root/

　├ hello/

　│　├ __init__.py

　│　└ hello.py

　└ setup.py
```
hello.py の中身
```
def hello():
    print("Hello, world!")

if __name__ == '__main__':
    hello()
```


setup.py の中身
```
from setuptools import setup

#setup(
#    name='hello',
#    version='0.0.1',
#    packages=['hello'],
#    entry_points={
#        'console_scripts': [
#            'hello=hello.hello:hello',
#        ],
#    },
#)

setup(
    name='orenohello',
    version='0.2.0',
    description='A sample Python project',
    long_description='This is a sample to say Hello!',
    url='https://github.com/yuris001/orenohello',
    author='ore',
    author_email='hoge.fuga@test.test',
    license='MIT',
    classifiers=[
    'Development Status :: 3 - Alpha',
    'Intended Audience :: Education',
    'Topic :: Education',
    'License :: OSI Approved :: MIT License',
    'Programming Language :: Python :: 3.5',
    ],
    keywords='sample setuptools development',
    packages=['hello'],
    entry_points={
        'console_scripts': [
            'hello=hello.hello:hello',
        ],
    },
)
```

アップロードさせる
```
python setup.py sdist upload -r pypitest

や

python setup.py sdist upload -r pypi これだめかな。

twine upload dist/*

を実行する
```
