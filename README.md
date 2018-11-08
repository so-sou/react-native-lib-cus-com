# react-native-lib-cus-com
react-native 自定义辅助组件库，完美适配各种机型和屏幕大小；
完美的网路请求，带加载条，可上传、下载文件;
等等多种ui,可自定义删除;可节省应用级软件的开发时间

###  安装组件：
npm i --save react-native-lib-cus-com

###  注意：
1.所有源码中的方法有注释，可自行查看；<BR/>
2.各组件的详细调用方法，可进入相应的组件文件查看，里面所有的方法/函数都有注释；<BR/>
3.以下“使用”的说明只有简单的说明(且都不写参数，直接复制使用，可能会报错)，具体说明，请参照“注意”第2点

### 安装依赖,必须安装
npm i --save react-native-root-siblings <BR/>
### 安装依赖,选择安装（别忘了根据相应库进行react-native link ...）
<b>npm i --save react-native-root-toast //若不安装，请求接口等报错没有提示</b> <BR/>
npm i --save react-native-view-shot <BR/>
npm i --save react-native-sqlite-storage <BR/>
npm i --save react-native-fs <BR/>
npm i --save react-native-device-info <BR/>
npm i --save react-native-doc-viewer <BR/><BR/>
<b>
这是一套：npm i --save jcore-react-native  <BR/>
npm i --save jpush-react-native <BR/><BR/>
</b>
<b>/** react-native-update 发布热更新报错 将node_modules\react-native-update\local-cli\lib\bundle.js <BR/>
 的439行种的metro-bundler改成metro可成功运行！ <BR/>
 报错版本0.52+(0.52以上版本报错) <BR/>
 **/ <BR/>
npm i --save react-native-update</b> <BR/>
npm i --save react-native-image-marker <BR/>
npm i --save react-native-storage <BR/>
npm i --save react-native-image-crop-picker <BR/>
npm i --save react-native-image-picker <BR/>
npm i --save react-native-picker <BR/>
npm i --save react-native-spinkit <BR/>
npm i --save react-native-talkingdata <BR/>
<b>/** 本库自带react-navigation@1.5.11，若想使用最新版则按“选择安装依赖的初始化”初始化
 **/ <BR/>
npm i --save react-navigation</b> <BR/>
npm i --save react-native-orientation <BR/><BR/>
<b>/**
    * react-native-smart-barcode 二维码库中将react的PropTypes换成
    * import PropTypes  from 'prop-types';
    * PropTypes已经从react中单独提取出来
    * android 需要修改 RCTCapturePackage中的List的继承去掉
    * **/<BR/>
npm i --save react-native-smart-barcode</b> <BR/>
npm i --save react_native_linear_gradient</b> <BR/>
npm i --save react_native_svg</b> <BR/>
npm i --save victory_native</b> <BR/>


### “可选依赖”的初始化 (看下列例子)
```
import {ComponentConstructor} from "react-native-lib-cus-com";

ComponentConstructor({
react_native_root_toast:require("react-native-root-toast"),
react_native_fs:require("react-native-fs")
});

//就是将组件名中的"-"换成"_",传入ComponentConstructor（组件构造器）即可。
```

### 使用api (方法参数，进入源文件查看，里面详细注解)：
##### StyleSheetAdapt 样式表创建，适配各种机型、各种屏幕 与StyleSheet用法一致
```
import {StyleSheetAdapt} from "react-native-lib-cus-com";
import React, {Component} from 'react';
import {View} from 'react-native';

StyleSheetAdapt.designSize = {width:768,height:1024};//页面设计大小
const styles = StyleSheetAdapt.create({

    testStyle2:{
        width:100,
        height:200,
    },
    testStyle:{
        transform:[
            {rotateX:'180deg'}
        ],
    },
});//创建样式表单
//StyleSheetAdapt.styleJsonAdaptConvert();//样式属性json中的值适配


export default class Test extends BaseComponent<Props> {

    constructor(props) {
        super(props);

    }

    alert(){
        //与react-native 中的Alert用法一致
        Alert.alert();
    }

    componentWillMount(){

    }

    componentDidMount() {
    }




    render() {

        const {resultEstimateData,noticesData,resultFinishProgress,
            tripListData,customerObj,isNews,pictures,path,dataSize,picture} = this.state;

        return (
             <ViewTitle>
                            <View style={styles.testStyle}></View>
                            <View style={StyleSheetAdapt.testStyle2}></View>
                            <View style={StyleSheetAdapt.styleJsonAdaptConvert({
                                width:100,
                                height:200,
                            })}></View>
                        </ViewTitle>
        );
    }
}


```

##### Http 网路请求
```
import {Http} from "react-native-lib-cus-com";
Http.post();//基于 fetch 封装的 POST请求
Http.get();//基于 fetch 封装的 Get请求
Http.requestAjax();//基于 ajax 封装的 网络请求
Http.urlFile = "";//上传文件 接口
Http.upLoadFileToService();//上传文件 react-native-fs
Http.downloadFile();//下载文件 react-native-fs
```

##### Tools 工具类，提供各种功能
```
import {Tools} from "react-native-lib-cus-com";
Tools.getStyle();//得到样式属性的json对象
Tools.replaceStr();//替换指定位置的字符串 字符串替换处理操作
Tools.getLocation();//获取地理位置
Tools.toast();//toast消息提示
Tools.openDoc();//打开文档(文件)
Tools.pickMonth();//选择年月（弹出年月ui选择框）
Tools.timeFormatConvert();//时间格式转化
Tools.isNumber();//判断是否是数字
Tools.getTimeByRank();//获取本周周一和周日的时间戳 对象；获取本月的月初的时间戳和月底的时间戳 对象
Tools.getDistanceByGps();//计算两点经纬度的距离
Tools.captureViewScreen();//截屏 截取UI的图片
Tools.toSpecifiedPageInPush = (result)=>{};//打开推送回调函数（如：跳转入指定页面）;直接赋值方法
```

##### Alert对话框
```
import {Alert} from "react-native-lib-cus-com";
Alert.alert();//显示对话框
Alert.hide();//关闭对话框
```

##### CaptureImage 截屏或截UI图 基于react-native-view-shot
```
import {CaptureImage} from "react-native-lib-cus-com";
CaptureImage.captureViewScreen();//截屏 截取UI的图片
```

##### DbMgr 数据库操作 基于react-native-sqlite-storage
```
import {DbMgr} from "react-native-lib-cus-com";
DbMgr.DB_TABLE_LIST = [];//创建表列表 此必须先调用
DbMgr.executeSql();//执行sql
还有很多方法，请查看文件里的注释
```

##### HotUpdate 热更新，提供热更新各种方法 基于react-native-update
```
安装、配置好react-native-update后

/**
 发布热更新报错 将node_modules\react-native-update\local-cli\lib\bundle.js
 的439行种的metro-bundler改成metro可成功运行！
 报错版本0.52+(0.52以上版本报错)
 **/


/**
 * HotUpdate 热更新，提供热更新各种方法
 * 元信息：{
updateList:[],//更新app id集合（app id集合）//不传更新全部
updateNoList:[],//不更新app id集合（app id集合）//传了的账户则不更新
code:777,//777、立刻更新；888、立刻强制更新；999、立刻静默更新
reboot:555,//666、强制使用更新；555、用户决定是否使用更新;333、下次启用更新 默认是555
}
 发布时，因react-native-update只接受字符串，所以元信息应是json的字符串，
 如：{"updateList":[]}
 * **/
import {HotUpdate} from "react-native-lib-cus-com";

/**
appkey 可采用以下方式获取：
import _updateConfig from '项目名/update';
const {appKey} = _updateConfig[Platform.OS];
**/
HotUpdate.appKey = null;//react-native-update的key
HotUpdate.appID = null;//当前给app指定（分配）的id
HotUpdate.updateFirst = true;//app第一次启动是否强制更新，默认true更新

这些设置完后即可，提示会根据元信息的情况提示
```

##### IamgeWaterMark 设置图片水印 基于react-native-image-marker
```
import {IamgeWaterMark} from "react-native-lib-cus-com";
IamgeWaterMark.markText();//设置水印文本
```

##### JPush 极光推送类，提供极光推送的各种方法 可看JPush文件源码注释
```
本库未直接导出，若想使用，使用自行导出；
需要安装:
npm i --save jcore-react-native
npm i --save jpush-react-native
```

##### LocalStorage 持久化本地存储 基于react-native-storage
```
import {LocalStorage} from "react-native-lib-cus-com";
LocalStorage.save();//使用key来保存单个数据（key-only）。这些数据一般是全局独有的，需要谨慎单独处理的数据
LocalStorage.get();//读取单个数据
LocalStorage.saves();//使用key来保存批量数据（key-only）。这些数据一般是全局独有的，需要谨慎单独处理的数据
LocalStorage.gets();//读取批量数据
```

##### Media 媒体类，处理摄像头使用和相册的使用 相册文件操作 基于react-native-image-crop-picker和react-native-image-picker
```
import {Media} from "react-native-lib-cus-com";
Media.pickImage();//选择图片 react-native-image-crop-picker
Media.takeImage();//拍照 react-native-image-crop-picker
Media.pickVideo();//选择视频 react-native-image-crop-picker
Media.takeVideo();//拍摄视频 react-native-image-picker
```

##### MenuBottomApi 底部弹出菜单API
```
import {MenuBottomApi} from "react-native-lib-cus-com";
MenuBottomApi.show();//显示底部菜单
MenuBottomApi.hide();//隐藏底部菜单
```

##### PickerCustome 自定义滑动选择   基于react-native-picker
```
import {PickerCustome} from "react-native-lib-cus-com";
PickerCustome.pick();//选择框 底部
PickerCustome.pickMonth();//选择年月
```

##### ProgressApi 加载指示器（加载条）  基于react-native-spinkit
```
import {ProgressApi} from "react-native-lib-cus-com";
ProgressApi.show();//显示加载指示器
ProgressApi.hide();//隐藏菊花加载指示器
```

##### ProgressPerApi 显示进度的进度条
```
import {ProgressPerApi} from "react-native-lib-cus-com";
ProgressPerApi.show();//显示进度条
ProgressPerApi.hide();//隐藏进度条
```

##### TalkingData 使用talkingdata app统计分析 可看TalkingData源文件注释
```
本库未直接导出，若想使用，使用自行导出；
需要安装:
npm i --save react-native-talkingdata
```

##### Theme 主题集合 颜色、宽度，及一些默认配置
```
import {Theme} from "react-native-lib-cus-com";
主题配色，宽高，弧度，在这个库中的一些ui使用到这里的默认配置，特别是样式
```

### 使用UI (ui属性，可调用方法参数，进入源文件自行查看，里面详细注解)：
##### BaseComponent 用于继承导航属性;这个组件中的方法都是"静态和动态"两种调用方式
```
import React, {Component} from 'react';
import {
   Text,
} from 'react-native'
import {
    StyleSheetAdapt,
    ViewTitle,
    BaseComponent,
    BarcodeView,
    Tools,
} from "react-native-lib-cus-com";
export default class Test extends BaseComponent<Props> {

    constructor(props) {
        super(props);
let param = Tools.userConfig.userCutAccount && Tools.userConfig.userCutAccount.length > 0
            ? {
                headerLeft:<ImageChange icon={require("images/role.png")}
                                        onPressIn={()=>PageSearchRole.show(this)}
                                        style={styles.hLeft}/>
            }
            : {
                headerLeft:false
            };

        this.setParams(param);
    }
    render() {
        return (
            <ViewTitle>
                <BarcodeView ref={c=>this.barcodeView}
                    style={styles.testStyle}/>
                <Text onPress={()=>this.barcodeView.startScan()}>
                    开始扫码
                </Text>
            </ViewTitle>
        );
    }
}
const styles = StyleSheetAdapt.create({

    testStyle2:{
        width:100,
        height:200,
    },
    testStyle:{
        transform:[
            {rotateX:'180deg'}
        ],
    },
});

BaseComponent.setScreenOrientations();//设置屏幕 静态
this.setScreenOrientations();//设置屏幕 动态
BaseComponent.getOrientation();//获取屏幕方向 静态
this.getOrientation();//获取屏幕方向 动态
BaseComponent.addOrientationListener();//监听屏幕方向变化
this.goPage();//跳转页面
this.goBack();//返回已进入的页面
this.setParams();//设置参数改变导航栏
this.getPageParams();//获取页面跳转传递的参数
```

##### ViewTitle 视频播放组件 ui控件  导航框控件 头部有导航栏（可设置有无） 左边带返回按钮（可设置有无） 中间有title文本（可设置有无） 右边带菜单按钮（可设置有无） 底部带按钮（可设置有无） 可设置是否可滚动 一般用于作为页面的基础框View
   ```
import {ViewTitle} from "react-native-lib-cus-com";
```

##### VideoView 视频播放组件 ui控件
```
import {VideoView} from "react-native-lib-cus-com";
```

##### VideoList 视频播放组控件，支持水平或竖直方向排布 ui控件
```
import {VideoList} from "react-native-lib-cus-com";
```

##### WebViewCus 浏览器（可设置成弹框出现，也可与页面合并兼容）的组件 ui控件（WebView） 支持html和uri（网页地址），并自动适配页面大小
```
import {WebViewCus} from "react-native-lib-cus-com";
```

##### DatePicker 日期选择组件
```
import {DatePicker} from "react-native-lib-cus-com";
```

##### ViewCtrl View的升级版 增加左右滑动事件
```
import {ViewCtrl} from "react-native-lib-cus-com";
```

##### DropdownBox 下拉框 支持单选和多选 基础组件
```
import {DropdownBox} from "react-native-lib-cus-com";
```

##### PickDropdown 下拉框 有下拉图表等，更加符合应用场景（基于DropdownBox）
```
import {PickDropdown} from "react-native-lib-cus-com";
```

##### PickDropdownMonth 月份下拉框 （基于PickDropdown）
```
import {PickDropdownMonth} from "react-native-lib-cus-com";
```

##### Progress 进度加载条
```
import {Progress} from "react-native-lib-cus-com";
```

##### ProgressPer  进度条 显示进度
```
import {ProgressPer} from "react-native-lib-cus-com";
```

##### Question  答题ui，支持单选、多选、问答；主要应用场景是调查问卷累等等
```
import {Question} from "react-native-lib-cus-com";
```

##### QuestionList  答题集合（列表）ui （基于Question）
```
import {QuestionList} from "react-native-lib-cus-com";
```

##### FlatListView 列表加载，可上下拉、分页、懒加载UI,有加载提示动画和提示信息 （加载更多）
```
import {FlatListView} from "react-native-lib-cus-com";
```

##### ImageBg 背景图组件
```
import {ImageBg} from "react-native-lib-cus-com";
```

##### ButtonChange 点击按钮
```
import {ButtonChange} from "react-native-lib-cus-com";
```

##### ButtonTime 时间选择按钮控件 可选择时间显示 并回传时间
```
import {ButtonTime} from "react-native-lib-cus-com";
```

##### ImageView 查看大图
```
import {ImageView} from "react-native-lib-cus-com";
```

##### ImageList 图片列表（水平或竖直）可以查看图片，成行排列 每张图片下部可以有提示文字 默认可滚动 （基于ImageView）
```
import {ImageList} from "react-native-lib-cus-com";
```

##### BarcodeView 二维码及条形码扫描组件
```
import React, {Component} from 'react';
import {
   Text,
} from 'react-native'
import {
    StyleSheetAdapt,
    ViewTitle,
    BaseComponent,
    BarcodeView,
} from "react-native-lib-cus-com";

type Props = {};
export default class Test extends BaseComponent<Props> {

    constructor(props) {
        super(props);

    }
    render() {
        return (
            <ViewTitle>
                <BarcodeView ref={c=>this.barcodeView}
                    style={styles.testStyle}/>
                <Text onPress={()=>this.barcodeView.startScan()}>
                    开始扫码
                </Text>
            </ViewTitle>
        );
    }
}
const styles = StyleSheetAdapt.create({

    testStyle2:{
        width:100,
        height:200,
    },
    testStyle:{
        transform:[
            {rotateX:'180deg'}
        ],
    },
});
```

##### MenuBottom 底部菜单ui
```
import {MenuBottom} from "react-native-lib-cus-com";
<MenuBottom ref={c=>this.menuBottom=c}
btnList={["btn1","btn2"]}
onPress={item=>{}}
/>
this.menuBottom.show(true);
```

##### SlideMenuDrawer   侧滑菜单 控件
```
import {SlideMenuDrawer} from "react-native-lib-cus-com";
```

##### SwiperImage 图片轮播图
```
import {SwiperImage} from "react-native-lib-cus-com";
```

##### SwiperNotice 公告轮播 图片和一些文本信息
```
import {SwiperNotice} from "react-native-lib-cus-com";
```

##### TextChange 按钮 可使用API改变文本
```
import {TextChange} from "react-native-lib-cus-com";
```

##### TextDoubleIcon 双文本并且右边有个图标 控件
```
import {TextDoubleIcon} from "react-native-lib-cus-com";
```

##### TextInputIcon 左边带图标的输入框 控件
```
import {TextInputIcon} from "react-native-lib-cus-com";
```

##### TextInputLabel 带文字label 的输入框的输入框 控件
```
import {TextInputLabel} from "react-native-lib-cus-com";
```

##### TextIcon 左边带图标的文本 控件
```
import {TextIcon} from "react-native-lib-cus-com";
```

##### TextIconBg 圆进程可以放底图 中间可放进度百分比 控件
```
import {TextIconBg} from "react-native-lib-cus-com";
```

##### TitleRow 左边具有按钮logo的UI 右边具有按钮 中间具有按钮UI控件
```
import {TitleRow} from "react-native-lib-cus-com";
```

##### TitleBlock 左边具有竖杠 中间上部具有大文本紧挨着右边具有较小本 大文本下边有小文本
```
import {TitleBlock} from "react-native-lib-cus-com";
```

##### TitleBlockList TitleBlock的列表
```
import {TitleBlockList} from "react-native-lib-cus-com";
```

##### ModalTextInput  弹出输入内容框，如反馈评价等；（有一个评分输入，和一个评语输入）
```
import {ModalTextInput} from "react-native-lib-cus-com";
```

##### ModalTextInputS  弹出输入内容框，如反馈评价等；（一个评语输入）
```
import {ModalTextInputS} from "react-native-lib-cus-com";
```

##### ModalTextInputS 行选择，默认垂直(或水平)显示选项选择,(单选或多选)
```
import {ModalTextInputS} from "react-native-lib-cus-com";
```

##### ScrollSelectOptions  左边具有标题的提示的UI 右边具有标识或UI的 UI控件
```
import {ScrollSelectOptions} from "react-native-lib-cus-com";
```

##### ScrollViewRowList  分组的带图片的ui 上部有title的文本，下边是主体有图片，图片下边有文本 支持一行多个或竖直多个
```
import {ScrollViewRowList} from "react-native-lib-cus-com";
```

##### ItemRowSwitch 具有ItemRowTitle提示的下拉展示控件框 直接封装有打开文件
```
import {ItemRowSwitch} from "react-native-lib-cus-com";
```

##### ItemRowTableSwitch 具有ItemRowTitle提示的下拉展示控件框
```
import {ItemRowTableSwitch} from "react-native-lib-cus-com";
```

##### ImageBrower 图片浏览UI，可以多个图片 缩略图和大图皆支持
```
import {ImageBrower} from "react-native-lib-cus-com";
```

##### CheckBox 选择框 此库里只有本人写的源码，还未测试导出，有意者可自行修改导出
```
```

##### Charts 图表
```
import {Charts} from "react-native-lib-cus-com";
<Charts.BarHorizontal /> //水平渐变柱状图 双层颜色变化
<Charts.BarHorizontal2 /> //水平渐变柱状图2 左右有文字提示 中间相对比变化的进度对比条
<Charts.BarHorizontal3 /> //水平渐变柱状图3 可有多条BarHorizontal2
<Charts.BarCircleGradient /> //圆形渐变图
<Charts.BarCircleChart /> //圆形加载图 4圆 中间有显示文本（Native实现）
<Charts.Chart /> //echarts图表 图形类型：柱状图，饼图，饼图
<Charts.BarCharts /> //柱状图（Native实现）
```

##### ImageViewWatermark  固定图片水印模版UI 水印在左下角
```
import {ImageViewWatermark} from "react-native-lib-cus-com";
ImageViewWatermark.show();//显示图片，有参数
或
<ImageViewWatermark ref={c=>this.waterMark=c} />
this.waterMark.show();//显示图片，有参数
```

##### GuideImageHint 任务头部水平提示导航栏
```
import {GuideImageHint} from "react-native-lib-cus-com";
```

##### ItemRowBuyCar 购物车行元素UI,右，有勾选框、图片、文本、数量输入UI；
```
import {ItemRowBuyCar} from "react-native-lib-cus-com";
```

##### ItemRowGoods 商品行组件 水平行，从左到右内容分别是，左边一张图片，中间有可支持5行竖直的文本行，其次是商品价格 最右边一个按钮（如加入购物车）
```
import {ItemRowGoods} from "react-native-lib-cus-com";
```

##### ItemRowGoods 商品行组件 水平行，从左到右内容分别是，左边一张图片，中间有可支持5行竖直的文本行，其次是商品价格 最右边一个按钮（如加入购物车）
```
import {ItemRowGoods} from "react-native-lib-cus-com";
```

##### ItemRowGoodsPromotion 促销活动Item；一张图片，图片左下角和右下角分别有一个按钮
```
import {ItemRowGoodsPromotion} from "react-native-lib-cus-com";
```

##### ItemRowGuideApplyType 行选择组件，分成两部分，左边支持文本和选择框，右边是文本
```
import {ItemRowGuideApplyType} from "react-native-lib-cus-com";
```

##### ItemRowTripApply 出差样式UI，左边文本提示文字，右边可以是：下拉框，输入框，文本
```
import {ItemRowTripApply} from "react-native-lib-cus-com";
```

##### ItemRowGuideTripApply 行单元格，一行内可支持1到7个单元格，可组合成表格。
```
import {ItemRowGuideTripApply} from "react-native-lib-cus-com";
```

##### ItemRowTripTask 行组件，上部是左边是title，右边是状态；像QQ一样单行可以侧滑，侧滑显示按钮
```
import {ItemRowTripTask} from "react-native-lib-cus-com";
```

##### ItemRowReciew 多个ui平分一行 水平
```
import {ItemRowReciew} from "react-native-lib-cus-com";
```

##### BarHorizontalTitleSection 条形进度块，上部有对比条提示，左边有对比的title，主体是对比条若干
```
import {BarHorizontalTitleSection} from "react-native-lib-cus-com";
```

##### ChartCircleProgress 4圆进度显示Chart 中间提示进度数据 最外层时间进度，跨度1月最小单位；天 (主页业绩进度例子，左边圆圈进度)
```
import {ChartCircleProgress} from "react-native-lib-cus-com";
```

##### ChartCircleProgressList  是ChartCircleProgress列表 有title （基于 ChartCircleProgress）
```
import {ChartCircleProgressList} from "react-native-lib-cus-com";
```

##### ResultProgressBlock  业务进度块 类似于进度对比表，有显示的基本内容，还有条状的对比图
```
import {ResultProgressBlock} from "react-native-lib-cus-com";
```

##### SearchDDDIpt  搜索组件 四个下拉框 一个输入框 一个搜索按钮
```
import {SearchDDDIpt} from "react-native-lib-cus-com";
```

##### SearchDropIpt  搜索组件 四个下拉框 一个输入框 一个搜索按钮
```
import {SearchDropIpt} from "react-native-lib-cus-com";
```

##### SearchIpt  具有 输入框(或下拉框)--按钮 的搜索条件的UI
```
import {SearchIpt} from "react-native-lib-cus-com";
```

##### TitleBlockTarget 目标幕模块 上部有header文本 中间有TitleBlockList 下边有TitleBlock文本提示(下左)和BarHorizontalTitleSection（对比进程 下右）
```
import {TitleBlockTarget} from "react-native-lib-cus-com";
```

##### TitleBlockTargetArea 区域模块 上部有header文本 中间有ResultProgressBlock（业绩进度模块） 下边有TitleBlock文本提示(下左)和BarHorizontalTitleSection（对比进程 下右）
```
import {TitleBlockTargetArea} from "react-native-lib-cus-com";
```