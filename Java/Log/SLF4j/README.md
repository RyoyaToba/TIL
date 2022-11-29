## [SLF4j](https://www.slf4j.org/download.html)

SLF4jを利用するには、外部jarを導入する必要がある。

HelloWorldをログ出力するSampleコードは以下

```Java
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

public class HelloWorld {

  public static void main(String[] args) {
    Logger logger = LoggerFactory.getLogger(HelloWorld.class);
    logger.info("Hello World");
  }
}
```
