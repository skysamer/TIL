## ๐ก component-scan ๊ฐ์
component-scan์ด๋, bean์ผ๋ก ๋ฑ๋ก ๋  ์ค๋น๋ฅผ ๋ง์น ํด๋์ค๋ค์ ์ค์บํ์ฌ, bean์ผ๋ก ๋ฑ๋กํด์ฃผ๋ ๊ฒ์ด๋ค.
@Contorller, @Service, @Repository, @Component ์ด๋ธํ์ด์์ ๋ถ์ธ ํด๋์ค๋ค์ด ๋น์ผ๋ก ๋ฑ๋ก ๋  ์ค๋น๊ฐ ๋๋ค.

component-scan์ ๊ธฐ๋ณธ์ ์ผ๋ก @Component ์ด๋ธํ์ด์์ bean ๋ฑ๋ก ๋์์ผ๋ก ํฌํจํ๋ค.
@Controller๋ @Service ์ด๋ธํ์ด์์ @Component๋ฅผ ํฌํจํ๊ณ  ์๊ธฐ ๋๋ฌธ์ ์ด ์ด๋ธํ์ด์๋ ์๋์ผ๋ก ์ธ์๋๋ค.

<br>
---

## ๐ก ์ฌ์ฉ๋ฐฉ๋ฒ
component-scan์ ์ฌ์ฉํ๋ ๋ฐฉ๋ฒ์ xml ํ์ผ์ ์ค์ ํ๋ ๋ฐฉ๋ฒ๊ณผ, ์๋ฐํ์ผ์์์ ์ค์ ํ๋ ๋ฐฉ๋ฒ์ด ์๋ค.

~~~xml
<context:component-scan base-package="com.ex.domain"/> 
~~~
๋ค์๊ณผ ๊ฐ์ด xml ํ์ผ์ ์ค์ ํ๊ณ , base package๋ฅผ ์ ์ด์ฃผ๋ฉด ํด๋์ค๋ค์ ์ค์บํ์ฌ ๋น์ผ๋ก ๋ฑ๋กํ๋ค.
๋ฑ๋ก๋ ํจํค์ง๋ฅผ ํฌํจํ์ฌ ํ์์ ํจํค์ง์์ ์๋ ํด๋์ค๋ค์ด ๋ชจ๋ ๋ฑ๋ก๋๋ค.

ํน์ ํ ๊ฐ์ฒด๋ง ๋น์ผ๋ก ๋ฑ๋กํ์ฌ ์ฌ์ฉํ๊ณ  ์ถ๋ค๋ฉด **include-filter**๋ **exclude-filter**๋ฅผ ํตํด ์ค์ ํ  ์ ์๋ค.

~~~xml
<context:component-scan base-package="com.ex.domain">
    <context:exclude-filter type="annotation" 
        expression="org.springframework.stereotype.Controller"/>
</context:component-scan>
~~~

<br>
---

## ๐ก ๋์๊ณผ์ 
component-scan ์ค์ ์ ํ์ฑํ๋ค
base-package์ ์ค์ ํ ํจํค์ง๋ฅผ ๊ธฐ์ค์ผ๋ก
componentScanAnnotationParser๊ฐ ์ค์บํ๊ธฐ ์ํ ์ค์ ์ ํ์ฑํ๋ค.

                         โฌ
                          
base-package ์ค์ ์ ๋ฐํ์ผ๋ก ๋ชจ๋  ํด๋์ค๋ฅผ ๋ก๋ฉํ๋ค

                         โฌ
                          
ClassLoader๊ฐ ๋ก๋ฉํ ํด๋์ค๋ค์ BeanDefinition์ผ๋ก ์ ์ํ๋ค.

                         โฌ

์ ์๋ฅผ ํ ๋๋ก ๋น์ ์์ฑํ๋ค.

<br>
---
