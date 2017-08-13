
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


