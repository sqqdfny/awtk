## fscript\_t
### 概述
一个简易的函数式脚本引擎。
用法请参考：https://github.com/zlgopen/awtk/blob/master/docs/fscript.md
----------------------------------
### 函数
<p id="fscript_t_methods">

| 函数名称 | 说明 | 
| -------- | ------------ | 
| <a href="#fscript_t_fscript_create">fscript\_create</a> | 创建引擎对象。 |
| <a href="#fscript_t_fscript_destroy">fscript\_destroy</a> | 销毁引擎对象。 |
| <a href="#fscript_t_fscript_eval">fscript\_eval</a> | 执行一段脚本。 |
| <a href="#fscript_t_fscript_exec">fscript\_exec</a> |  |
| <a href="#fscript_t_fscript_global_deinit">fscript\_global\_deinit</a> | 全局释放。 |
| <a href="#fscript_t_fscript_global_init">fscript\_global\_init</a> | 全局初始化。 |
| <a href="#fscript_t_fscript_register_func">fscript\_register\_func</a> | 注册全局自定义函数。 |
### 属性
<p id="fscript_t_properties">

| 属性名称 | 类型 | 说明 | 
| -------- | ----- | ------------ | 
| <a href="#fscript_t_fast_vars">fast\_vars</a> | value\_t* | 快速访问变量。在脚本可以用a/b/c/d来访问，需要优化时使用。 |
| <a href="#fscript_t_obj">obj</a> | object\_t* | 脚本执行上下文。 |
| <a href="#fscript_t_str">str</a> | str\_t | C语言实现函数可以使用这个变量，可以有效避免内存分配。 |
#### fscript\_create 函数
-----------------------

* 函数功能：

> <p id="fscript_t_fscript_create">创建引擎对象。

* 函数原型：

```
fscript_t* fscript_create (object_t* obj, const char* script);
```

* 参数说明：

| 参数 | 类型 | 说明 |
| -------- | ----- | --------- |
| 返回值 | fscript\_t* | 返回fscript对象。 |
| obj | object\_t* | 脚本执行上下文。 |
| script | const char* | 脚本代码。 |
#### fscript\_destroy 函数
-----------------------

* 函数功能：

> <p id="fscript_t_fscript_destroy">销毁引擎对象。

* 函数原型：

```
ret_t fscript_destroy (fscript_t* fscript);
```

* 参数说明：

| 参数 | 类型 | 说明 |
| -------- | ----- | --------- |
| 返回值 | ret\_t | 返回RET\_OK表示成功，否则表示失败。 |
| fscript | fscript\_t* | 脚本引擎对象。 |
#### fscript\_eval 函数
-----------------------

* 函数功能：

> <p id="fscript_t_fscript_eval">执行一段脚本。

* 函数原型：

```
ret_t fscript_eval (object_t* obj, const char* script, value_t* result);
```

* 参数说明：

| 参数 | 类型 | 说明 |
| -------- | ----- | --------- |
| 返回值 | ret\_t | 返回RET\_OK表示成功，否则表示失败。 |
| obj | object\_t* | 脚本执行上下文。 |
| script | const char* | 脚本代码。 |
| result | value\_t* | 执行结果(调用者需要用value\_reset函数清除result)。 |
#### fscript\_exec 函数
-----------------------

* 函数功能：

> <p id="fscript_t_fscript_exec">

* 函数原型：

```
ret_t fscript_exec (fscript_t* fscript, value_t* result);
```

* 参数说明：

| 参数 | 类型 | 说明 |
| -------- | ----- | --------- |
| 返回值 | ret\_t | 返回RET\_OK表示成功，否则表示失败。 |
| fscript | fscript\_t* | 脚本引擎对象。 |
| result | value\_t* | 执行结果(调用者需要用value\_reset函数清除result)。 |
#### fscript\_global\_deinit 函数
-----------------------

* 函数功能：

> <p id="fscript_t_fscript_global_deinit">全局释放。

* 函数原型：

```
ret_t fscript_global_deinit ();
```

* 参数说明：

| 参数 | 类型 | 说明 |
| -------- | ----- | --------- |
| 返回值 | ret\_t | 返回RET\_OK表示成功，否则表示失败。 |
#### fscript\_global\_init 函数
-----------------------

* 函数功能：

> <p id="fscript_t_fscript_global_init">全局初始化。

* 函数原型：

```
ret_t fscript_global_init ();
```

* 参数说明：

| 参数 | 类型 | 说明 |
| -------- | ----- | --------- |
| 返回值 | ret\_t | 返回RET\_OK表示成功，否则表示失败。 |
#### fscript\_register\_func 函数
-----------------------

* 函数功能：

> <p id="fscript_t_fscript_register_func">注册全局自定义函数。

* 函数原型：

```
ret_t fscript_register_func (const char* name, fscript_func_t* func);
```

* 参数说明：

| 参数 | 类型 | 说明 |
| -------- | ----- | --------- |
| 返回值 | ret\_t | 返回RET\_OK表示成功，否则表示失败。 |
| name | const char* | 函数名(无需加函数前缀)。 |
| func | fscript\_func\_t* | 函数指针。 |
#### fast\_vars 属性
-----------------------
> <p id="fscript_t_fast_vars">快速访问变量。在脚本可以用a/b/c/d来访问，需要优化时使用。

* 类型：value\_t*

| 特性 | 是否支持 |
| -------- | ----- |
| 可直接读取 | 是 |
| 可直接修改 | 否 |
#### obj 属性
-----------------------
> <p id="fscript_t_obj">脚本执行上下文。

* 类型：object\_t*

| 特性 | 是否支持 |
| -------- | ----- |
| 可直接读取 | 是 |
| 可直接修改 | 否 |
#### str 属性
-----------------------
> <p id="fscript_t_str">C语言实现函数可以使用这个变量，可以有效避免内存分配。

* 类型：str\_t

| 特性 | 是否支持 |
| -------- | ----- |
| 可直接读取 | 是 |
| 可直接修改 | 否 |
