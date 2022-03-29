# wework-sdk

企业微信-会话内容存档 java SDK    
本包只提供最原始的sdk调用接口,需要您需要解密等操作,请参考以下相关集成包


本包的多版本,不同的系统使用不同的包,并且使用不同的动态库
- [wework-sdk](https://github.com/aa24615/wework-win) linux版
- [wework-sdk-win](https://github.com/aa24615/wework-win) win版

### 相关集成包

- [wework-message](https://github.com/aa24615/wework-message) 获取聊天记录,解密,下载媒体文件
- [wework-msgaudit](https://github.com/aa24615/wework-msgaudit) 带web管理 支持多企业 入库mysql


### 把动态库拷贝到系统

linux系统
```shell
cp ./lib/WeWorkFinanceSdk.so /usr/lib/WeWorkFinanceSdk.so
```

win系统

```shell
//请把lib下四个文件拷贝到C盘 C:\Windows\System32\

libcrypto-1_1-x64.dll
libcurl-x64.dll
libssl-1_1-x64.dll
WeWorkFinanceSdk.dll
```


### 调用示例

```java

import com.tencent.wework.Finance;
import java.io.*;


public class sdkdemo {
    public static void main(String[] args){
        long sdk = Finance.NewSdk();
        System.out.println(Finance.Init(sdk,  "wwd08coe7d775abaaa","zJ6k0naVVQ--gt9PUSSEvs03zW_nlDVmjAkPOTAfrew"));
        String priKey =
                "-----BEGIN RSA PRIVATE KEY-----\n" +
                        "MIIEowIBAAKCAQEAjzJfnYgy8gI/UdR9OMzMh2/Svtz6ynPJdgqWX0qCm7361g04\n" +
                        "Sz/g+aJGtqu8jRJNg3rxQhezoy5mc+//QDyL6sM0auASS+eWx2igxVahLhJEWef3\n" +
                        "2woMrb+OHs6nJf2jBcfA494KvgkxSYXU84vl8UCHwUI839SLBSLWofb8ccFEmy9W\n" +
                        "VSWY7EIUVV8pO8sLZ9uVWK1IrHHSrcGkx4SF913RDIxCTExj7bLqxNRklzWZgi3m\n" +
                        "bYoIsTG6dmsGkmxagGPEtuVOI2UjpjQw1WyrN+6o+2+qpOIuoHKF5vGrPbQBL1jU\n" +
                        "nshGs3MnwTWdxVOe+bw8a+VAqxpD5DlfdKamgQIDAQABAoIBAGNRbe3mPGeMVXyd\n" +
                        "I6kUqrs5PPNyc2OdwVpk53z6QfJhZyu1iZjvmkuqWN9z59f0nNyXlePgapDAqwC4\n" +
                        "sdJM7EKM17tU5HvPCc4O7ItSlYJN2yh8cnVy1+5ekOUfMeFwtPRaYpfpNowt9ghn\n" +
                        "kZbGLlsRBddt6KjaUv3h9vnpQ5hlhU53slh+Zsdrsselpy0sTCF0ulVQgioZ6lzg\n" +
                        "/Y61xCGxRWqq71UT/7EOZwIoD3NmLRZLE6vxm8uBrFvZZ5/jw9Z//8S+vgtRUgGj\n" +
                        "/5v55ftTG+EOsaz2Zvt+jghkaEAchcyy5LyUv09Ir9eOYfjNAgeCk9dQv6E+2BiR\n" +
                        "SvcUJEECgYEA5CvcoSpV66qC1T99/JqmqyTjORZ4ZKBJY9vos4uxNYfCbbhNJLDY\n" +
                        "QAbCC234nBuKQ+3cVKkWtjBwfNp90mEmIoN6sYv+SdtVe2ofhJEqLMTiGyZPi2Iv\n" +
                        "+vvRpFmiAUfWXqFzBy+3HSoTkRqbCytUIT7NXZZ3YwKbbIhyzABTzSkCgYEAoKlf\n" +
                        "Gsn4rQEfmitAGJpuiSahih6KV3K+S9olnPbwd04YOw4u5UmouhyC7N0z2K8AO6zo\n" +
                        "IkzCQtWQS1B1uaPE/stG7I/iy0CI6q46nSly5pajBBGQc+Y5ixRf23hEjGgca556\n" +
                        "1pDyMs0Nb0J2AGDcr8olrbT1KwBvg8oWHOlA4ZkCgYAmC+pONXD+SwBl7qBjbqY8\n" +
                        "A3qgGk8Y+GFEdXbn+XMjKfARu5mhdJuakYXpwfyiizUS/qaut0NCPfGD4Cr62Zgy\n" +
                        "SRo8YMuWJSyr15ZJ1KrjrDDHtiutYkH959+dOBT7ga8NOH6lxB8Ujd+VYopX4nG0\n" +
                        "2XQFFwHxUI36GwaJXcSbgQKBgEe4VERZNTHF9p2UASD6j62aGTLXP1qaVmj2ESRo\n" +
                        "+B/KNPbn9fdVUoUChU/Hz4VDWg9JuLbXHUFIpQl5+ZPNj/tOM3MXKF8jh/t7m57d\n" +
                        "CfX1+P+v95RFihqUFdabcb5cG5PPQ3bVbclP0FeCi7rPgrTWwMsypN91alKivAxb\n" +
                        "9CLBAoGBALfb5SEupOoyIUetiWhOc1vlmP+71rJEXUEYwm0CMmfKZRW+I1A8qTE+\n" +
                        "DVT6iUMVt6jj8L/YiMzjUh8y8HLcp4mlldzdfyjssZg6v2hABJcnID6o3DcTXA8k\n" +
                        "8uMmaZZ0qY4oUzwgZa7bf/C//3mKlRUMoBYOT/LAksZlySIBXoST\n" +
                        "-----END RSA PRIVATE KEY-----\n";

        long ret = 0;

        if (args[0].equals("1")) {
            int seq = Integer.parseInt(args[1]);
            int limit = Integer.parseInt(args[2]);
            long slice = Finance.NewSlice();
            ret = Finance.GetChatData(sdk, seq, limit, args[3], args[4], Integer.parseInt(args[5]), slice);
            if (ret != 0) {
                System.out.println("getchatdata ret " + ret);
                return;
            }
            System.out.println("getchatdata :" + Finance.GetContentFromSlice(slice));
            Finance.FreeSlice(slice);
        } else if (args[0].equals("2")) {

            String indexbuf = "";
            while(true){
                long media_data = Finance.NewMediaData();
                ret = Finance.GetMediaData(sdk, indexbuf, args[1], args[2], args[3], Integer.parseInt(args[4]), media_data);
                System.out.println("getmediadata ret:" + ret);
                if(ret!=0){
                    return;
                }
                System.out.printf("getmediadata outindex len:%d, data_len:%d, is_finis:%d\n",Finance.GetIndexLen(media_data),Finance.GetDataLen(media_data), Finance.IsMediaDataFinish(media_data));
                try {
                    FileOutputStream outputStream  =new FileOutputStream(new File("/home/qspace/upload/media_data"),true);
                    outputStream.write(Finance.GetData(media_data));
                    outputStream.close();
                } catch (Exception e) {
                    e.printStackTrace();
                }

                if(Finance.IsMediaDataFinish(media_data) == 1)
                {
                    // need free media_data
                    Finance.FreeMediaData(media_data);
                    break;
                }
                else
                {
                    indexbuf = Finance.GetOutIndexBuf(media_data);

                    // need free media_data
                    Finance.FreeMediaData(media_data);
                }
            }
        }else if (args[0].equals("3")) {
            // notice!
            // // use prikey to decrpyt get args[1] by do it yourself

            long msg = Finance.NewSlice();
            ret = Finance.DecryptData(sdk,args[1] ,args[2], msg);
            if (ret != 0) {
                System.out.println("getchatdata ret " + ret);
                return;
            }
            System.out.println("decrypt ret:" + ret + " msg:" + Finance.GetContentFromSlice(msg));
            Finance.FreeSlice(msg);
        }
        else {
            System.out.println("wrong args " + args[0]);
        }
        Finance.DestroySdk(sdk);
    }
}
```


###  参与贡献

1. fork 当前库到你的名下
2. 在你的本地修改完成审阅过后提交到你的仓库
3. 提交 PR 并描述你的修改，等待合并


###  License

[MIT license](https://opensource.org/licenses/MIT)


