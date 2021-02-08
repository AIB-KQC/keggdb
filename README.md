# keggdb
#安装Y叔的包，
#安装创建KEGG数据库的包的包
remotes::install_github("YuLab-SMU/createKEGGdb")
#创建自己的物种的包create_kegg_db，会自动创建名称为KEGG.db_1.0.tar,gz的包。物种名称的简写，在
createKEGGdb::create_kegg_db('zma')

#安装这个包(默认的包的路径在当前工作目录，根据实际情况修改路径)
install.packages("~/KEGG.db_1.0.tar.gz",repos=NULL,type="source")

测试
library(KEGG.db)
library(clusterProfiler)
data(geneList,package="DOSE")
head(geneList)
gene <- names(geneList)[abs(geneList) > 2]
head(gene)
kk <- enrichKEGG(gene= gene,organism= 'zma',pvalueCutoff = 0.05,qvalueCutoff = 0.05,use_internal_data =T)
#当使用本地的KEGG.db数据库时，use_internal_data设置为T,使用在线数据库时设置为F.
head(kk)
nrow(kk)
