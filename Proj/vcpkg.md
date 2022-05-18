### 安装

vcpkg国内镜像使用方法 - 知乎
[https://zhuanlan.zhihu.com/p/383683670](https://zhuanlan.zhihu.com/p/383683670)

感谢作者提供的源：
**[http://106.15.181.5/](http://106.15.181.5/)** 

--- 

VCPKG安装BOOST
要下载的包很多，而且由于众所周知的网络问题，
下载过程中，屡屡失败，

索性写个Python爬虫，
将所有的BOOST包爬取下来，
然后放至  `vcpkg\downloads`   文件夹中

然后再执行命令: `vcpkg install boost`
它会检测本地的包，若存在，就不会下载，并继续安装

  ---      

**python 代码：**

```py
import requests
from bs4 import BeautifulSoup
url = 'http://106.15.181.5/'
res = requests.get(url)
soup = BeautifulSoup(res.text, 'html.parser')
listTr = soup.find_all('tr')

urlList = []
for i in listTr:
    url1 = i.find('a')['href']
    if url1.startswith('/boostorg') and url1.endswith('.tar.gz'):
        urlList.append(url1)

for j in urlList:
    data = requests.get(url + j).content
    with open(j[1:], 'wb') as f:
        f.write(data)
        print(f'{j[1:]} 下载成功')

print('\n任务完成')
```

---

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210708114227341.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1bGlueHg=,size_16,color_FFFFFF,t_70#pic_center)

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210708120439226.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3l1bGlueHg=,size_16,color_FFFFFF,t_70#pic_center)

现提供爬取到的网址，若版本更新（2021.07），可自行修改替换：

```
http://106.15.181.5/boost-1.75.0-boostcpp.jam
http://106.15.181.5/boostorg-accumulators-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-algorithm-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-algorithm-boost-1.75.0.tar.gz.6240.part
http://106.15.181.5/boostorg-align-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-any-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-array-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-asio-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-assert-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-assign-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-atomic-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-beast-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-bimap-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-bind-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-build-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-callable_traits-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-chrono-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-circular_buffer-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-compatibility-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-compute-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-concept_check-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-config-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-container_hash-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-container-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-context-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-contract-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-conversion-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-convert-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-core-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-coroutine-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-coroutine2-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-crc-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-date_time-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-detail-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-dll-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-dynamic_bitset-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-endian-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-exception-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-fiber-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-filesystem-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-flyweight-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-foreach-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-format-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-function_types-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-function-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-functional-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-fusion-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-geometry-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-gil-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-graph_parallel-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-graph-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-hana-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-heap-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-histogram-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-hof-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-icl-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-integer-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-interprocess-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-interval-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-intrusive-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-io-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-iostreams-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-iterator-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-json-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-lambda-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-leaf-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-lexical_cast-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-local_function-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-locale-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-lockfree-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-log-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-logic-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-math-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-math-boost-1.75.0.tar.gz.6035.part
http://106.15.181.5/boostorg-metaparse-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-move-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-mp11-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-mpl-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-msm-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-multi_array-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-multi_index-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-multiprecision-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-nowide-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-numeric_conversion-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-odeint-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-optional-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-outcome-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-parameter_python-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-parameter-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-pfr-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-phoenix-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-poly_collection-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-polygon-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-pool-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-predef-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-preprocessor-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-process-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-program_options-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-property_map-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-property_tree-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-proto-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-ptr_container-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-python-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-qvm-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-random-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-range-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-ratio-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-rational-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-regex-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-safe_numerics-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-scope_exit-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-serialization-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-signals2-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-smart_ptr-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-sort-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-spirit-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-stacktrace-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-statechart-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-static_assert-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-static_string-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-stl_interfaces-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-system-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-test-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-thread-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-throw_exception-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-timer-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-tokenizer-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-tti-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-tuple-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-type_erasure-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-type_index-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-type_traits-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-typeof-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-ublas-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-units-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-unordered-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-unordered-boost-1.75.0.tar.gz.4854.part
http://106.15.181.5/boostorg-utility-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-uuid-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-variant-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-variant2-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-vmd-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-wave-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-winapi-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-xpressive-boost-1.75.0.tar.gz
http://106.15.181.5/boostorg-yap-boost-1.75.0.tar.gz
```

--------------

如:
现要安装boost, VCPKG提示的为 1.78版,
将上述一系列的网址 1.75 替换 为 1.78
然后用 Motrix 等下载工具,批量下载完成

![Motrix 下载 BOOST](https://img-blog.csdnimg.cn/0d6916416fbe473ba1925f622964235f.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAeXVsaW54eA==,size_20,color_FFFFFF,t_70,g_se,x_16)
![Motrix 下载 BOOST2](https://img-blog.csdnimg.cn/3207dccaee7e4a74afa292e1f1edfcdc.png?x-oss-process=image/watermark,type_d3F5LXplbmhlaQ,shadow_50,text_Q1NETiBAeXVsaW54eA==,size_20,color_FFFFFF,t_70,g_se,x_16)

---

Linux下:
也可将上述地址前加个 wget , 保存为 .ssh 文件, 并添加 x 的权限,
调用 .ssh 进行下载

```
x@x:~/install/vcpkg/downloads$ vim boostDownload.sh 
x@x:~/install/vcpkg/downloads$ chmod +x boostDownload.sh 
x@x:~/install/vcpkg/downloads$ ./boostDownload.sh 
```

---

**同理，OpenCV等其它库，**
**均下载离线文件，然后放至 vcpkg\downloads**
**然后再 vcpkg install XXX 即可**
