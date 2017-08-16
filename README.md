### 短链接生成算法

> usage
```
import "ShortUrlGenerator"

result, err := ShortUrlGenerator.Transform("www.baidu.com")
if err != nil {
     fmt.Println(err)
     return
}

```
>algorithm
1. 将原长链接进行md5校验和计算，生成32位字符串
2. 将32位字符串每8位划分一段，得到4段子串。将每个字串（16进制形式）转化为整型数值，与0x3FFFFFFF按位与运算，生成一个30位的数值
3. 将上述生成的30位数值按5位为单位依次提取，得到的数值与0x0000003D按位与，获取一个0-61的整型数值，作为从字符数组中提取字符的索引。得到6个字符就生成了一个短链
4. 4段字串共可以生成4个短链
