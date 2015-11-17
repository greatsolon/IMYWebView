# IMYWebView
UIWebView seamless switching to WKWebView <br>
无缝切换 UIWebView 为 WKWebView  

##要求


* ARC only

##使用方法

直接把你项目中的 'UIWebView' 名称替换为 'IMYWebView'

##在原框架基础上，添加了`js回调oc`的相关方法，用法如下
```
/**
 *  iOS8下 本地注册js方法，让服务端调用
 */
- (void)addJsMethodIniOS8
{
    WYScriptMessageHandlerLeakAvoider *leakAvoider = [[WYScriptMessageHandlerLeakAvoider alloc] initWithDelegate:self];
    [_co_webView addScriptMessageHandler:leakAvoider name:@"closeMe"];
}
```
在当前类`self`的`dealloc`里面调用下面的方法：

```
/**
 *  iOS8下 注销 本地注册的js方法
 */
- (void)removeJsMethodIniOS8
{
    [_co_webView removeScriptMessageHandlerForName:@"closeMe"];
}
```
