## R包安装方式
1. 在github.com上下载xx-master.zip
2. 安装
```
remotes::install_local("xx-master.zip", upgrade=F, dependencies=T)
```
另：也可以将zip文件解压成文件夹XX-master，输入命令
```
install.packages("xx-master", repos=NULL, type="source")
```

附：4种R包安装方式
1. 直接安装
```
install.packages('xxx')
```
2. 找到下载地址，然后安装
```
url <- "http://cran.r-proiect.org/src/contrib/Archive/gridExtra/gridExtra 0.9.1.tar.gz"
install.packages(url, repos=NULL, type="source")
```
3. 下载到本地，然后安装
```
dowmload,file("http://bioconductor .org/packages/release/bioc/src/contrib/BiocInstaller 1.20,1.tar.gz","BiocInstaller 1.20.1.tar.gz")
##也可以选择其他方式下载
install.packages("BiocInstaller 1.20.1,tar,gz", repos = NULL)
```
4. Linux命令行安装
```
sudo R CMD INSTALI package.tar.gz
```
