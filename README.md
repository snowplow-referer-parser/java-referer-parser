# referer-parser

This is the Java implementation of [referer-parser][referer-parser], the library for extracting attribution data from referer (sic) URLs.

The implementation uses the shared 'database' of known referers found in [`referers.yml`][referers-yml].

## Usage:

Use referer-parser in Java like this:

```java
import com.snowplowanalytics.refererparser.Parser;

...

String refererUrl = "http://www.google.com/search?q=gateway+oracle+cards+denise+linn&hl=en&client=safari";
String pageUrl    = "http://www.psychicbazaar.com/shop"; // Our current URL

Parser refererParser = new Parser();
Referer r = refererParser.parse(refererUrl, pageUrl);

System.out.println(r.medium);     // => "search"
System.out.println(r.source);     // => "Google"
System.out.println(r.term);       // => "gateway oracle cards denise linn"
```


### Installation

Add the following code into your `HOME/.m2/settings.xml` to be able to use this repository:

```xml
<settings>
  <profiles>
    <profile>
      <!-- ... -->
      <repositories>
        <repository>
          <id>com.snowplowanalytics</id>
          <name>SnowPlow Analytics</name>
          <url>http://maven.snplow.com/releases</url>
          <releases>
            <enabled>true</enabled>
          </releases>
          <snapshots>
            <enabled>true</enabled>
          </snapshots>
        </repository>
      </repositories>
    </profile>
  </profiles>
</settings>
```

Then add into your project's `pom.xml`:

```xml
<dependency>
    <groupId>com.snowplowanalytics</groupId>
    <artifactId>referer-parser_2.11</artifactId>
    <version>0.3.0</version>
</dependency>
```


## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## Copyright and license

Licensed under the [Apache License, Version 2.0][license] (the "License");
you may not use this software except in compliance with the License.

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.


[referer-parser]: https://github.com/snowplow/referer-parser
[referers-yml]: https://github.com/snowplow/referer-parser/blob/master/referers.yml
