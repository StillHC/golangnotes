
# day 1


MacOS 默认安装路径 ：/usr/local/go
version : go version

complier:

go build xxx

go run xxx.go

GOPAHT :
<pre><code> 
function setgopath() {
currpath=`pwd`
gopath=${currpath%/src*}
if [[ $currpath != $gopath ]];then
    if [[ $gopath != $GOPATH ]];then
        export GOPATH=$gopath
        echo '$GOPATH:'$GOPATH
    fi
fi
}
setgopath

function cd_and_setgopath() {
cd $1
setgopath
}
alias cd='cd_and_setgopath'

</code> </pre>
配置生效：
source ~/.zshrc

## 测试单元 ：
引入测试包
<code>
import "testing"
func Test_funcName(t *testing.T){
     //v := funcName()
    if v != xx {
       t.Errorf("xxx failed .... %v", v)
       }
}
</code>

### 单元测试命令；
   go test xxx
   
## 打印日志 
   fmt 包中的Printf() 和 Println() 使用。
   
# 顺序编程

## 变量声明 
var varName vartype 
<code>
var v1 int 
var v2 string 
var v3 [10]int 
var v4 []int //数组切片

var v5 struct {
    f int 
}

var v6 *int //pointer

var v7 map[string]int 
var v8 func (a int)int // function 

var (
     v1 int
     v2 string
)

</code>

##  变量初始化 

<code>
var v1 int = 10
var v2 = 10
v3 := 10
</code>

注意：“ := ” 不能在声明过后再使用


## 变量赋值 
支持多重赋值
<code>
i, j = j, i

</code>

匿名变量 
<code>
func GetName() (fristName, lastName, nickName string){
    return "May", "Chan", "Chibi Maruko"
}
// 调用

_, _, nickName := GetName()

</code>

## 常量定义 
常量可以限定类型，也可以不限定。

const Pi float64 = 3.141592654

const Zero = 0.0

const u, v float32 = 0, 3

## 预定义常量 
Go 语言预定义了true false iota 

iota 在每一个const 关键字出现被重置为0
然后在下一个const 出现之前 没出现一次iota 代表数字增加1

const (
 c0 = iota //0
 c1        //1
 c2        //2
)

## 枚举 

const ( 
  Sumday = iota
  Monday 
  Tuesday
  ...
  numberOfDays //对于其他引用该包。为包内私有 大写字母开头的常量在包外可见。
)


## 类型

布尔 ：bool 
整型 ： int8 byte, int16, int, uint, uintprt 
浮点型： float32 float64 
复数：complex64 complex 128
字符串：string
字符：runne
错误类型 error
指针：pointer
数组： array 
切片：slice 
字典 ：map
通道：chan
结构体：struct
接口：interface 

布尔类型 不支持自动或者强制类型转换

整型 ： int, uint 平台相关 
uintprt :同指针

int 和int32 是两个不同的类型， 不会自动转换， 需要强制转换

int32(a)

两个不同类型的整型不能直接比较 。但是变量可以和字面常量进行比较。


## 位运算

x << y 左移 124 <<2 //496
x >> y 右移 124 >>2 //31
x^y   亦或 124^2 //126
x&y 与   124&2 //0

x|y 或 124|2 //126

^x 取反  ^2 //-3


## 浮点型比较 

不能直接使用 == 比较两个浮点数 

推荐使用 math 包

<code>
import "math"

func IsEqual(f1, f2, p float64) bool {
   return math.Fdim(f1, f2) <p
}
</code>


## 复数

var v1 complex64
v1 = 3.2 + 12i
v2 := complex(3.2, 12)

