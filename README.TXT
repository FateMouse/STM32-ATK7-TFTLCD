实验器材:
	MiniSTM32F103开发板V3版本
	
实验目的:
	学习ATK-7寸TFTLCD电容触摸屏模块的使用（注意：是V1版本的7寸屏，CPLD+GT811方案）.

硬件资源:	
	1,DS0(连接在PA8),DS1(连接在PD2) 
	2,串口1(波特率:9600,PA9/PA10连接在板载USB转串口芯片CH340上面)
	3,ALIENTEK 7寸TFTLCD模块(CPLD+GT811方案,通过GPIO驱动,连接关系见lcd.h)
	4,SD卡,通过SPI1连接 
	5,W25Q64(SPI FLASH芯片,连接在SPI1上)
	6,按键KEY0(PC5)/KEY1(PA15)/KEY_UP(PA0,也称之为WK_UP)  
		
实验现象:
	1，电容触摸屏测试—通过按KEY0按键进入此项测试。进入测试后，可以在屏幕上实现触摸画线，最多支持5点触
	摸。同时该程序带触摸力度检测，按下的面积大，画出来的线就比较粗，反之则比较细。通过按屏幕右上角的
	"RST"可以实现清屏。

	2，图片显示测试—通过按KEY1按键进入此项测试。此项测试需要一个SD卡，并且在SD卡根目录放一个PICTURE文
	件夹，里面放一些图片文件(bmp/jpeg/gif等)，然后程序检测到图片后，就开始在LCD模块上PICTURE文件夹里面
	的图片。通过KEY0/KEY1可以切换下一张/上一张图片，通过按WK_UP按键，可以暂停/继续自动播放(DS1用于指示
	是否处于暂停状态)。

	3，液晶自测试—通过按WK_UP按键进入此项测试。此项测试又分为4个测试小项:速度测试/镜像测试/缓存测试/背
	光测试。速度测试类似ucGUI的测试效果，测试结果将显示在LCD上(像素/秒);镜像测试，展示液晶的4个显示效果
	:正常/上下调转/左右调转/上下左右都调转;缓存测试，用于测试LCD模块的8页显存，每页显示一种颜色;背光测
	试，用于测试模块的背光控制功能，背光将从暗到亮变化。


注意事项:
	1,7寸屏需要比较大电流,USB供电可能不足,请用外部电源供电(5V电源，接VOUT2即可).
	2,本例程在LCD_Init函数里面(在ILI93xx.c),用到了printf,如果不初始化串口1,将导致液晶无法显示!! 
	3,LCD模块在开发板的LCD接口上面，必须靠右插 
	4,不要把1820和PA0的跳线帽跳上,否则可能导致按键"不灵". 
	5,该实验图片显示测试须自备SD卡一个，并在SD卡根目录新建PICTURE文件夹，然后放入一些图片，支持的图片格式有：BMP/JPG/JPEG/GIF。     
	6,该实验不支持MiniSTM32 V3.0之前的板子，请注意！！如果您是用的V3.0之前的板子，请用老版本的代码。
	7,本例程详细说明，见光盘：9，增值资料\1，ALIENTEK 产品资料\3，ATK-7' TFTLCD电容触摸屏模块\ATK-7' TFTLCD 模块使用说明(战舰V2&Mini V3)_AN1410.pdf
				

					正点原子@ALIENTEK
					2014-4-1
					广州市星翼电子科技有限公司
					电话：020-38271790
					传真：020-36773971
					购买：http://shop62103354.taobao.com
					http://shop62057469.taobao.com
					公司网站：www.alientek.com
					技术论坛：www.openedv.com