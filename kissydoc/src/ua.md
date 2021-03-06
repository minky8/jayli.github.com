<style>
h3 {
	color:blue;
}
</style>

# UA

> 判断浏览器类型、版本、外壳等信息，引入种子文件后，通过`KISSY.UA`来访问`UserAgent`相关属性

此处的外壳表示广义的外壳，即 IE, Firefox, Chrome, Opera, Safari 等浏览器都属于外壳。可以利用此标识符直接识别浏览器类型。 可以首先使用 UA.shell 返回的标识符判断当前浏览器类型，若需浏览器具体版本信息，可以再通过 `UA[UA.shell]` 取出版本号。 

* UA.core 返回字符串，目前支持 trident, webkit, gecko, presto 四大浏览器内核. 
* UA.shell 返回字符串，比如 firefox, opera, chrome, ie, safari 
* UA.mobile 返回字符串，目前支持 apple, nokia, android, opera mini/mobile 等设备/浏览器的探测.

通过 KISSY.UA, 你可以获取浏览器等用户代理信息. 属性值遵循以下规则：

* 表示当前引擎或浏览器的版本. 版本号 1.2.3.4 会转换为数值 1.234 
* 如果不是当前引擎或浏览器, 返回 0 
* 如果当前引擎或浏览器的版本号无法准确判定, 返回 0.1

通过 KISSY.UA 的属性，你可以获取浏览器等用户代理的信息。属性值遵循以下规则：

- 表示当前引擎或浏览器的版本。版本号 1.2.3.4 会转换为数值 1.234
- 如果不是当前引擎或浏览器，返回 0 或者 undefined
- 如果当前浏览器版本号无法准确判定，均返回 0.1


	KISSY.use('ua',function(S,UA){
		alert(UA); // UA可以使用了
	});

-------------------------------------


### trident  `<static>`

{Number} - trident 的版本号。IE 浏览器 8 系列以下都无法准确探测 Trident 内核的版本号。

### webkit  `<static>`

{Number} - webkit 的版本号。

### gecko  `<static>`

{Number} - gecko 的版本号。

### presto  `<static>`

{Number} - presto 的版本号。

### chrome  `<static>`

{Number} - chrome 的版本号。

### safari  `<static>`

{Number} - safari 的版本号。

### firefox  `<static>`

{Number} - firefox 的版本号。

### ie  `<static>`

{Number} - ie 的版本号。

### opera  `<static>`

{Number} - opera 的版本号。

### mobile  `<static>`

{String} - mobile 的标志符。 若无法探测或非移动设备浏览器，将返回空字符串。

### core  `<static>`

{String} - core 的标志符。此标识符表示浏览器的内核标识。若浏览器内核不是 trident, webkit, gecko, presto 将返回空字符串。

### shell  `<static>`

{String} - shell 的标志符。此标识符表示用户所用浏览器的外壳标识。

### os  `<static>`

{String} - 操作系统标志符。例如 windows android ios linux

### ipad  `<static>`

{Number} - ipad ios 版本号。例如 5.0

### iphone  `<static>`

{Number} - iphone ios 版本号。例如 5.0

### ipod  `<static>`

{Number} - ipod ios 版本号。例如 5.0

### ios  `<static>`

{Number} - ios 版本号。例如 5.0

### android  `<static>`

{Number} - android 版本号。例如 5.0

----------------------------------------------------

## examples

### 判断浏览器类型

	KISSY.use('ua',function(S,UA){
		if(UA.chrome > 0){
			alert('Your browser is chrome');
		}else if(UA.safari > 0){
			alert('Your browser is safari');
		}else if(UA.opera > 0){
			alert('Your browser is opera');
		}else if(UA.firefox > 0){
			alert('Your browser is firefox');
		}else if(UA.ie > 0){
			alert('Your browser is ie');
		}else{
			alert('Your browser is unknown');
		}
	});

## 判断操作系统类型

	KISSY.use('ua',function(S,UA){
        if(UA.os == 'windows'){
            alert('Your os is Windows');
        }else if(UA.os == 'Linux'){
            alert('Your os is Linux');
        }else if(UA.os == 'ios'){
            alert('Your os is ios and version is' + UA.ios);
            if(UA.ipad > 0){
                alert('Your device is iPad');
            }else if(UA.iphone > 0){
                alert('Your device is iPhone');
            }else if(UA.ipod > 0){
                alert('Your device is iPod')
            }
        }else if(UA.os == 'android'){
            alert('Your os is Android');
        }
    });

### 判断mobile类型

	KISSY.use('ua',function(S,UA){
        if(UA.mobile == 'apple'){
            alert('Your device is Apple');
        }else if(UA.mobile == 'nokia'){
            alert('Your device is Nokia');
        }else if(UA.mobile == 'android'){
            alert('Your device is Android');
        }else if(UA.mobile == 'opera mini' || UA.mobile == 'opera mobi'){
            alert('Your browser is opera mobile');
        }
    }); 

### 判断浏览器外壳

	KISSY.use('ua',function(S,UA){
        if(UA.shell == 'chrome'){
            alert('Your browser is chrome and the version is' + UA[UA.shell]);
        }else if(UA.shell == 'se360'){
            alert('Your browser is 360浏览器');
        }else if(UA.shell == 'tt'){
            alert('Your browser is 腾讯TT浏览器');
        }else if(UA.shell == 'maxthon'){
            alert('Your browser is 遨游浏览器');
        }
    });
