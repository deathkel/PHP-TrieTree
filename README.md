# PHP-TrieTree
## 这是一个支持中英文混合的PHP的字典树

> 本字典树是在https://github.com/AbelZhou/PHP-TrieTree的基础上做了进一步的修改，本想将个人的优化更新push到该仓库，但作者由于客观原因不方便merge我的更改，故重新开了仓库。
> 测试的词库引用了Abel的，谢谢Abel
> 本人的进一步更改有的是出于自己的需求，不代表一定比原作者的好，各位同学可以对比阅读后按需加载

## 示例
```php
<?php
require "../src/TrieTree.php";


$testArr = array("张三","张四","王五","张大宝","张三四","张氏家族","王二麻子");

$tree = new \Keyword\TrieTree();

foreach ($testArr as $str){
    $tree->append($str);
}

$res = $tree->getTree();

var_dump($res);

$res = $tree->search("有一个叫张三的哥们");
var_dump($res);

$res = $tree->search("我叫李四喜");
var_dump($res);

//删除
$res = $tree->delete("张三");

//删除整棵树 连带“张三”和张三下的“张三四”一并删除
$tree->delete("张三",true);
```

## 使用场景
- 敏感词过滤
- 内链建设

## 性能
test目录下有个1.5w左右的敏感词。
mac下检索耗时2~5毫秒左右
这些敏感词来自网络，不是很全。

