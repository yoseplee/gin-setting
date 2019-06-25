# gin-setting
setting up a web framework based on golang named gin

## prerequisite
* 1. go programming language
* 2. dep(package manager for golang)

## 1. installation
* 1. install go programming language(macos)
    * 1.  ``` $ brew install go ```
* 2. setting up $GOPATH and $GOROOT
    * 1. modify bash_profile. you may create.
        * ``` $ vim ~/.bash_profile ``` 
    * 2. $GOROOT(path where the exec files exists)
        * ```export GOROOT=/usr/local/Cellar/go/1.12.6/libexec```
        * NOTE: the path above fully relies on brew installed case. if you downloaded from other case, you might change path
    * 3. $GOPATH(path where your go projectes exist)
        * ```export GOPATH=$HOME/goProject```
        * NOTE: the path above means go project directory. unlike any other programming language, you should init and run 'gin', a web framework under GOPATH/src.
* 3. install dep(macos)
    * ``` $ brew install dep ```

## 2. run the server in the minimum setting
* 1. move to $GOPATH/src directory(you may create src directory)
    * ```$ dep init```
    * Gopkg.toml, Gopkg.lock are created
* 2. add dependency 'gin' into Gopkg.toml
    * ``` [[constraint]] ```
    * ``` name = "github.com/gin-gonic/gin"```
    * ``` version = "1.4.0"```
* 3. create main.go (from official github README.md, https://github.com/gin-gonic/gin)
```go
package main

import "github.com/gin-gonic/gin"

func main() {
    r := gin.Default()
    r.GET("/ping", func(c *gin.Context) {
        c.JSON(200, gin.H {
            "message": "pong",
        })
    })
    r.Run() //listen and serve on 0.0.0.0:8000
}
```
* 4. ``` $ dep ensure ```    
* 5. install dependency: ``` $ dep ensure ```
* 6. run server: ``` $ go run main.go ```
* 7. test with curl ``` curl -i http://localhost:8080/ping ```
