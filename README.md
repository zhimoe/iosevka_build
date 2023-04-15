# iosevka_build
iosevka是目前最流行的可编程开源字体。有以下特色：
1. 字符全，作者更新频率非常高，不停地在补充字符（对强迫症用户其实有点不友好哈哈）
2. 有严格半宽和常规宽度两个版本。HalfWidth的编程字体不多，目前比较流行的就三个：iosevka，pragmata pro, ubuntu mono.
3. 可编程，iosevka是完全可编程的,你可以组合自己想要的字符外观构建自己的版本。
4. 风格多选，在可编程的基础上，参考其他流行字体的特色，iosekva官方给出了十几种风格版本，当然效果和原版还是差别比较大的，例如和Fira Code相比。

## Usage
### 使用dockerhub的镜像构建
1. 在[typeof.net/Iosevka/customizer](https://typeof.net/Iosevka/customizer)配置你想要的字体外观，将下面的build config放在`private-build-plans.toml`文件中。
2. 在`private-build-plans.toml`目录下通过docker构建
```shell
docker run -it -v $(pwd):/build zhimoe/iosevka_build ttf::iosevka
```
注意：最后的ttf:参数表示只构建ttf版本，可以去掉同时构建ttf,otf和woff文件。 最后的iosevka是`private-build-plans.toml`的[buildPlans.iosevka] name。

### 使用本地Dockerfile构建
也可以修改本仓库中的Dockerfile后自己构建镜像：
```shell
# 构建docker镜像，在Dockerfile目录下
docker build -t iosevka_build .

# 构建iosevka字体
docker run -it -v $(pwd):/build iosevka_build ttf::iosevka
```

## Customized glyphs
修改了`g` `0` `2` 三个字符外观