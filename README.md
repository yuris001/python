

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
